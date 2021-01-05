---
title: Administrar intervalos de direcciones IP mediante la API
description: En este artículo se proporciona información sobre cómo usar la API de para administrar los intervalos de direcciones IP en Cloud App Security.
ms.date: 01/04/2021
ms.topic: how-to
ms.openlocfilehash: 4351649e023128cbb7635c366e3ab5449956c144
ms.sourcegitcommit: 90df07ce9cd64fd9c46fb6563f0249079204e174
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/04/2021
ms.locfileid: "97859239"
---
# <a name="manage-ip-address-ranges-using-the-api"></a>Administrar intervalos de direcciones IP mediante la API

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Puede usar las API de enriquecimiento de datos para administrar los intervalos de direcciones IP.

## <a name="to-use-the-manage-ip-address-ranges-script"></a>Para usar el script administrar intervalos de direcciones IP

1. Cree un archivo CSV con los siguientes campos previstos: nombre, IP_Address_Ranges, categoría, etiqueta (ID.) y Override_ISP_Name.

1. Actualice los valores de las siguientes variables de script: **OPTION_DELETE_ENABLED**, **IP_RANGES_BASE_URL**, **CSV_ABSOLUTE_PATH**, **YOUR_TOKEN**

    > [!IMPORTANT]
    > Si establece **OPTION_DELETE_ENABLED** en **true**, el script eliminará los intervalos de direcciones IP que se hayan definido en el inquilino, pero que no existan en los archivos CSV. Si usa esta opción, asegúrese de que el archivo CSV define todos los intervalos de direcciones IP que desea en el inquilino.

1. Ejecute el script para crear nuevos registros y actualizar las reglas existentes con el nombre coincidente.

## <a name="request-body-parameters"></a>Parámetros del cuerpo de la solicitud

- "filtros": los objetos de filtro con todos los filtros de búsqueda de la solicitud, consulte [filtros de enriquecimiento de datos](api-data-enrichment.md#filters) para obtener más información. Para evitar que se limiten las solicitudes, asegúrese de incluir una limitación en la consulta.
- "Limit": entero. En modo de exploración, entre 500 y 5000 (el valor predeterminado es 500). Controla el número de iteraciones utilizadas para examinar todos los datos.

## <a name="response-parameters"></a>Parámetros de respuesta

- "Data": los datos devueltos. Contendrá hasta "limitar" el número de registros de cada iteración. Si hay más registros para extraer (hasNext = true), se quitarán los últimos registros para asegurarse de que todos los datos se muestran una sola vez.
- "hasNext": booleano. Indica si se necesita otra iteración en los datos.
- "nextQueryFilters": si se necesita otra iteración, contiene la consulta JSON consecutiva que se va a ejecutar. Úselo como el parámetro "filters" en la siguiente solicitud.

En el siguiente ejemplo de Python se usa el contenido de un archivo CSV para administrar (crear, actualizar o eliminar) intervalos de direcciones IP en el entorno de Cloud App Security.

```python
import csv
import requests
import json

OPTION_DELETE_ENABLED = False
IP_RANGES_BASE_URL = 'https://<tenant_id>.<tenant_region>.contoso.com/api/v1/subnet/'
IP_RANGES_UPDATE_SUFFIX = 'update_rule/'
IP_RANGES_CREATE_SUFFIX = 'create_rule/'
CSV_ABSOLUTE_PATH = 'rules.csv'
YOUR_TOKEN = '<your_token>'
HEADERS = {
  'Authorization': 'Token {}'.format(YOUR_TOKEN),
}

# Get all records.
def get_records():
  list_request_data = {
    # Optionally, edit to match your filters
    'filters': {},
    "skip": 0,
    "limit": 20
  }
  records = []
  has_next = True
  while has_next:
    content = json.loads(requests.post(IP_RANGES_BASE_URL, json=list_request_data, headers=HEADERS).content)
    response_data = content.get('data', [])
    records += response_data
    has_next = content.get('hasNext', False)
    list_request_data["skip"] += len(response_data)
  return records

# Rule fields are compared to the CSV row.
def rule_matching(record, ip_address_ranges, category, tag, isp_name, ):
  rule_exists_conditions = [sorted([subnet.get('originalString', False) for subnet in record.get('subnets', [])]) !=
                            sorted(ip_address_ranges.split(' ')),
                            str(record.get('category', False)) != category,
                            len(record.get('tags', [])) != len(tag.split(' ')) and
                            (len(record.get('tags', [])) != 0 and len(tag) == 1),
                            bool(record.get('organization', False)) != bool(isp_name) or
                            (record.get('organization', False) is not None and not isp_name)]
  if any(rule_exists_conditions):
    return False
  for tag in record.get('tags', []):
    tag_id = tag.get('id')
    if tag_id and tag_id not in tag.split(' '):
      return False
  return True

def create_update_rule(name, ip_address_ranges, category, tag, isp_name, records, request_data):
  for record in records:
    # Records are compared by name(unique).
    # This can be changed to id (to update the name), it will include adding id to the CSV and changing row shape.
    if record["name"] == name:
      # request_data["_tid"] = record["_tid"]
      if not rule_matching(record, ip_address_ranges, category, tag, isp_name):
        # Update existing rule
        json.loads(
          requests.post(f"{IP_RANGES_BASE_URL}{record['_id']}/{IP_RANGES_UPDATE_SUFFIX}", json=request_data, headers=HEADERS).content)
        return record
      else:
        # The exact same rule exists. no need for change.
        return record
  # Create new rule.
  requests.post(f"{IP_RANGES_BASE_URL}{IP_RANGES_CREATE_SUFFIX}", json=request_data, headers=HEADERS)

# Request data creation.
def create_request_data(name, ip_address_ranges, category, tag, isp_name):
  request_data = {"name": name, "subnets": ip_address_ranges.split(' '), "category": category,
                  "tags": tag.split(' ') if tag else ''}
  if isp_name:
    request_data["overrideOrganization"] = True
    request_data["organization"] = isp_name
  return request_data

def main():
  # CSV fields are: Name,IP_Address_Ranges,Category,Tag(id),Override_ISP_Name
  # Multiple values (eg: multiple subnets) will be space-separated. (eg: value1 value2)
  records = get_records()
  with open(CSV_ABSOLUTE_PATH, newline='\n') as your_file:
    reader = csv.reader(your_file, delimiter=',')
    for row in reader:
      name, ip_address_ranges, category, tag, isp_name = row
      request_data = create_request_data(name, ip_address_ranges, category, tag, isp_name)
      if records:
        # Existing records were retrieved from your tenant
        record = create_update_rule(name, ip_address_ranges, category, tag, isp_name, records, request_data)
        record_id = record['_id']
      else:
        # No existing records were retrieved from your tenant
        record_id = json.loads(requests.post(f"{IP_RANGES_BASE_URL}{IP_RANGES_CREATE_SUFFIX}", json=request_data, headers=HEADERS).content)
      if OPTION_DELETE_ENABLED:
        # Remove CSV file record from tenant records.
        if record_id:
          for record in records:
            if record['_id'] == record_id:
              records.remove(record)
  if OPTION_DELETE_ENABLED:
    # Delete remaining tenant records, i.e. records that aren't in the CSV file.
    for record in records:
      requests.delete(f"{IP_RANGES_BASE_URL}{record['_id']}/", headers=HEADERS)
  
if __name__ == '__main__':
  main()
```

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Actividades diarias para proteger el entorno de nube](daily-activities-to-protect-your-cloud-environment.md)

[!INCLUDE [Open support ticket](includes/support.md)]
