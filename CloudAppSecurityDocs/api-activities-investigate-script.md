---
title: Investigación de actividades mediante la API
description: En este artículo se proporciona información sobre cómo usar la API de para investigar la actividad del usuario en Cloud App Security.
ms.date: 12/22/2020
ms.topic: how-to
ms.openlocfilehash: 799e248ed69626b301d9281c43c14053b6ff03cf
ms.sourcegitcommit: 90df07ce9cd64fd9c46fb6563f0249079204e174
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/04/2021
ms.locfileid: "97859225"
---
# <a name="investigate-activities-using-the-api"></a>Investigación de actividades mediante la API

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Puede usar las API de actividades para investigar las actividades realizadas por los usuarios en las aplicaciones en la nube conectadas.

El modo de API de actividades está optimizado para el análisis y la recuperación de grandes cantidades de datos (más de 5.000 actividades). El análisis de la API consulta los datos de la actividad varias veces hasta que se han examinado todos los resultados.

> [!NOTE]
> En el caso de grandes cantidades de actividades y de implementaciones a gran escala, se recomienda usar el [agente Siem](siem.md) para el análisis de actividades.

## <a name="to-use-the-activity-scan-script"></a>Para usar el script de análisis de actividad

1. Ejecute la consulta en los datos.
1. Si hay más registros de los que se pueden mostrar en un solo examen, obtendrá un comando devuelto con `nextQueryFilters` que debe ejecutar. Obtendrá este comando cada vez que digitalice hasta que la consulta devuelva todos los resultados.

## <a name="request-body-parameters"></a>Parámetros del cuerpo de la solicitud

- "filtros": los objetos de filtro con todos los filtros de búsqueda de la solicitud, vea [filtros de actividad](activity-filters-queries.md) para obtener más información. Para evitar que las solicitudes se limiten, asegúrese de incluir una limitación en la consulta, por ejemplo, consultar las actividades del último día o filtrar por una aplicación determinada.
- "isScan": booleano. Habilita el modo de exploración.
- "sortDirection": la dirección de ordenación, los valores posibles son "ASC" y "DESC"
- "sortField": campos que se usan para ordenar las actividades. Los valores posibles son:
  - Fecha: la fecha en la que se produjo la actividad (este es el valor predeterminado).
  - creado: marca de tiempo en la que se guardó la actividad.
- "Limit": entero. En modo de exploración, entre 500 y 5000 (el valor predeterminado es 500). Controla el número de iteraciones utilizadas para examinar todos los datos.

## <a name="response-parameters"></a>Parámetros de respuesta

- "Data": los datos devueltos. Contendrá hasta "limitar" el número de registros de cada iteración. Si hay más registros para extraer (hasNext = true), se quitarán los últimos registros para asegurarse de que todos los datos se muestran una sola vez.
- "hasNext": booleano. Indica si se necesita otra iteración en los datos.
- "nextQueryFilters": si se necesita otra iteración, contiene la consulta JSON consecutiva que se va a ejecutar. Úselo como el parámetro "filters" en la siguiente solicitud.

En el siguiente ejemplo de Python se obtienen todas las actividades del último día de Exchange Online.

``` python
import requests
import json
ACTIVITIES_URL = 'https://<your_tenant>.<tenant_region>.contoso.com/api/v1/activities/'

your_token = '<your_token>'
headers = {
'Authorization': 'Token {}'.format(your_token),
}

filters = {
  # optionally, edit to match your filters
  'date': {'gte_ndays': 1},
  'service': {'eq': [20893]}
}
request_data = {
  'filters': filters,
  'isScan': True
}

records = []
has_next = True
while has_next:
    content = json.loads(requests.post(ACTIVITIES_URL, json=request_data, headers=headers).content)
    response_data = content.get('data', [])
    records += response_data
    print('Got {} more records'.format(len(response_data)))
    has_next = content.get('hasNext', False)
    request_data['filters'] = content.get('nextQueryFilters')

print('Got {} records in total'.format(len(records)))
```

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Actividades diarias para proteger el entorno de nube](daily-activities-to-protect-your-cloud-environment.md)

[!INCLUDE [Open support ticket](includes/support.md)]
