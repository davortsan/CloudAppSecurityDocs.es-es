---
title: Investigar las actividades mediante la API, Cloud App Security | Microsoft Docs
description: En este artículo se proporciona información sobre cómo usar la API para investigar la actividad del usuario en Cloud App Security.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: barbkess
ms.date: 03/26/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 0f2f971d-10e3-496d-8004-96d9fad71cae
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: a4d91f196cb8d2bab51a2688c07f0654317765f3
ms.sourcegitcommit: fe4cd2174f6dc83811a2d484f079e8dfbac5d082
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/26/2019
ms.locfileid: "58476457"
---
# <a name="investigate-activities-using-the-api"></a>Investigar las actividades mediante la API

*Se aplica a: Microsoft Cloud App Security*

Microsoft Cloud App Security proporciona una API de REST totalmente compatible para permitirle interactuar mediante programación con el servicio.

Puede usar las API de Microsoft Cloud App Security para investigar las actividades realizadas por los usuarios en las aplicaciones conectadas en la nube. 

El modo de API de las actividades de Cloud App Security está optimizado para la detección y recuperación de grandes cantidades de datos (más de 5.000 actividades). La API de analizar los datos de actividad de consultas repetidamente hasta que se han examinado todos los resultados. 

> [!NOTE] 
> Para grandes cantidades de actividades y las implementaciones a gran escala, se recomienda que utilice el [agente SIEM](siem.md) para el análisis de actividad.

**Para usar la API de detección de actividad:**

1. Ejecutar la consulta de los datos.
1. Si hay más registros que pueden enumerarse en un solo recorrido, obtendrá un comando devuelto con `nextQueryFilters` que debe ejecutar. Obtendrá este comando cada vez que digitalice hasta que la consulta ha devuelto todos los resultados.
 
 
**Parámetros de cuerpo de solicitud**:
- "filtros": Filtro de los objetos que tienen todos los filtros de búsqueda para la solicitud, consulte [filtros de actividad](activity-filters.md) para obtener más información. Para evitar que las solicitudes de estar limitado, asegúrese de incluir una limitación en la consulta, por ejemplo, las actividades del último día de la consulta o filtrar por una aplicación determinada.
- “isScan”: Valor booleano. Habilita el modo de exploración.
- “sortDirection”: La dirección de ordenación, los valores posibles son "asc" y "desc" 
- “sortField”: Campos utilizados para ordenar las actividades. Los valores posibles son: 
    - Date: la fecha cuando, a continuación, se produjo la actividad (este es el valor predeterminado).
    - creado: la marca de tiempo cuando se guardó la actividad.
- "límite": Número entero. En el modo de análisis, entre 500 y 5000 (valor predeterminado es 500). Controla el número de iteraciones usadas para la exploración de todos los datos. 

**Parámetros de respuesta**:
- "datos": los datos devueltos. Contendrá "límite" número máximo de registros de cada iteración. Si hay más registros que se pueden extraer (hasNext = true), la última que se van a quitar algunos registros para asegurarse de que todos los datos de una sola vez.
- "hasNext": Valor booleano. Indica si se necesita otra iteración en los datos.
- “nextQueryFilters”: Si se necesita otra iteración, contiene la consulta JSON consecutiva que se ejecutará. Utilícelo como el parámetro "filtros" en la siguiente solicitud.

En el siguiente ejemplo de Python Obtiene todas las actividades desde el último día de Exchange Online.

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
        
 
## <a name="next-steps"></a>Pasos siguientes
[Actividades diarias para proteger el entorno de nube](daily-activities-to-protect-your-cloud-environment.md)   

[Los clientes Premier también pueden crear una solicitud de soporte técnico directamente en el portal Premier.](https://premier.microsoft.com/)  
  
