---
title: API List-Alerts
description: En este artículo se describe la solicitud de lista en la API de alertas de Cloud App Security.
ms.date: 03/27/2020
ms.topic: reference
ms.openlocfilehash: 3c3dec04dff5369120decdfc6142d0517eca4e2a
ms.sourcegitcommit: 90df07ce9cd64fd9c46fb6563f0249079204e174
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/04/2021
ms.locfileid: "97859044"
---
# <a name="list---alerts-api"></a>API List-Alerts

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Ejecute la solicitud GET o POST para capturar una lista de alertas que coinciden con los filtros especificados.

## <a name="http-request"></a>Solicitud HTTP

```rest
GET /api/v1/alerts/
```

```rest
POST /api/v1/alerts/
```

## <a name="request-body-parameters"></a>Parámetros del cuerpo de la solicitud

| Parámetro | Description |
| --- | --- |
| filters | Filtre los objetos con todos los filtros de búsqueda de la solicitud; consulte [filtros de alerta](api-alerts.md#filters) para obtener más detalles. |
| sortDirection | Dirección de ordenación. Los valores posibles son: `asc` y `desc` |
| sortField | Campos usados para ordenar las alertas. Los valores posibles son:<br />- **fecha**: fecha en la que se creó la alerta.<br />- **gravedad**: la gravedad de la alerta |
| skip | Omite el número de registros especificado. |
| limit | Número máximo de registros devueltos por la solicitud |

## <a name="example"></a>Ejemplo

### <a name="request"></a>Solicitud

Este es un ejemplo de la solicitud.

```rest
curl -XPOST -H "Authorization:Token <your_token_key>" "https://<tenant_id>.<tenant_region>.contoso.com/api/v1/alerts/" -d '{
  "filters": {
    // some filters
  },
  "skip": 5,
  "limit": 10
  ...
}'
```

### <a name="response"></a>Response

Devuelve una lista de alertas en formato JSON.

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
