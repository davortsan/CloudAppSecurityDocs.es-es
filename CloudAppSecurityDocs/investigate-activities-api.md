---
title: Investigar actividades mediante la API-Cloud App Security
description: En este artículo se proporciona información sobre cómo usar la API de para investigar la actividad del usuario en Cloud App Security.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 03/26/2019
ms.topic: how-to
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 7eabf167dacf06a51a8c78951a89923a5c8d01bd
ms.sourcegitcommit: 575f2b2efa9ca4477d7e60271d21e225ef2c38ea
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/22/2020
ms.locfileid: "90879393"
---
# <a name="investigate-activities-using-the-api"></a>Investigación de actividades mediante la API

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Microsoft Cloud App Security proporciona una API de REST totalmente compatible para que pueda interactuar con el servicio mediante programación.

Puede usar el Microsoft Cloud App Security API para investigar las actividades realizadas por los usuarios en las aplicaciones en la nube conectadas.

El modo de API de Cloud App Security actividades está optimizado para el análisis y la recuperación de grandes cantidades de datos (más de 5.000 actividades). El análisis de la API consulta los datos de la actividad varias veces hasta que se han examinado todos los resultados.

> [!NOTE]
> En el caso de grandes cantidades de actividades y de implementaciones a gran escala, se recomienda usar el [agente Siem](siem.md) para el análisis de actividades.

**Para usar la API de examen de actividad:**

1. Ejecute la consulta en los datos.
1. Si hay más registros de los que se pueden mostrar en un solo examen, obtendrá un comando devuelto con `nextQueryFilters` que debe ejecutar. Obtendrá este comando cada vez que digitalice hasta que la consulta devuelva todos los resultados.

**Parámetros del cuerpo**de la solicitud:

- "filtros": los objetos de filtro con todos los filtros de búsqueda de la solicitud, vea [filtros de actividad](activity-filters.md) para obtener más información. Para evitar que las solicitudes se limiten, asegúrese de incluir una limitación en la consulta, por ejemplo, consultar las actividades del último día o filtrar por una aplicación determinada.
- "isScan": booleano. Habilita el modo de exploración.
- "sortDirection": la dirección de ordenación, los valores posibles son "ASC" y "DESC"
- "sortField": campos que se usan para ordenar las actividades. Los valores posibles son:
  - Fecha: la fecha en la que se produjo la actividad (este es el valor predeterminado).
  - creado: marca de tiempo en la que se guardó la actividad.
- "Limit": entero. En modo de exploración, entre 500 y 5000 (el valor predeterminado es 500). Controla el número de iteraciones utilizadas para examinar todos los datos.

**Parámetros de respuesta**:

- "Data": los datos devueltos. Contendrá hasta "limitar" el número de registros de cada iteración. Si hay más registros para extraer (hasNext = true), se quitarán los últimos registros para asegurarse de que todos los datos se muestran una sola vez.
- "hasNext": booleano. Indica si se necesita otra iteración en los datos.
- "nextQueryFilters": si se necesita otra iteración, contiene la consulta JSON consecutiva que se va a ejecutar. Úselo como el parámetro "filters" en la siguiente solicitud.

En el siguiente ejemplo de Python se obtienen todas las actividades del último día de Exchange Online.

``` python
import requests
import json
ACTIVITIES_URL = 'https://<your_tenant>.portal.cloudappsecurity.com/api/v1/activities/'

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
