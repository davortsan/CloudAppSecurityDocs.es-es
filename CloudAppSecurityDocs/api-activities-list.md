---
title: List-Activities API
description: En este artículo se describe la solicitud de lista en la API de actividades de Cloud App Security.
ms.date: 03/27/2020
ms.topic: reference
ms.openlocfilehash: d36f18f3cc19b726ce84ae75b4a19427a78dba17
ms.sourcegitcommit: d87372b47ca98e942c2bf94032a6a61902627d69
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/30/2020
ms.locfileid: "96314705"
---
# <a name="list---activities-api"></a>List-Activities API

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Ejecute la solicitud GET o POST para obtener una lista de las actividades que coinciden con los filtros especificados.

## <a name="http-request"></a>Solicitud HTTP

```rest
GET /api/v1/activities/
```

```rest
POST /api/v1/activities/
```

## <a name="request-body-parameters"></a>Parámetros del cuerpo de la solicitud

| Parámetro | Description |
| --- | --- |
| filters | Filtre los objetos con todos los filtros de búsqueda de la solicitud; consulte [filtros de actividad](api-activities.md#filters) para obtener más detalles. |
| sortDirection | Dirección de ordenación. Los valores posibles son: `asc` y `desc` |
| sortField | Campos usados para ordenar las actividades. Los valores posibles son:<br /><br />**Date**: la fecha en la que se produjo la actividad.<br /><br />**creado**: marca de tiempo en la que se guardó la actividad |
| skip | Omite el número de registros especificado. |
| limit | Número máximo de registros devueltos por la solicitud |

## <a name="example"></a>Ejemplo

### <a name="request"></a>Solicitud

Este es un ejemplo de la solicitud.

```rest
curl -XPOST -H "Authorization:Token <your_token_key>" "https://<tenant_id>.<tenant_region>.contoso.com/api/v1/activities/" -d '{
  "filters": {
    // some filters
  },
  "skip": 5,
  "limit": 10
  ...
}'
```

### <a name="response"></a>Response

Devuelve una lista de actividades en formato JSON.

```json
{
  "total": 5 // total number of records
  "hasNext": true // whether there is more data to show or not.
  "data": [
    // returned records
  ]
}
```

[!INCLUDE [Open support ticket](includes/support.md)]
