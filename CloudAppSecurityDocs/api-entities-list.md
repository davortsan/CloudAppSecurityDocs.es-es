---
title: List-entidades API
description: En este artículo se describe la solicitud de lista en la API de entidades de Cloud App Security.
ms.date: 03/27/2020
ms.topic: reference
ms.openlocfilehash: a93fa00db40720d8b8bf31a8494ce949402bca0b
ms.sourcegitcommit: 90df07ce9cd64fd9c46fb6563f0249079204e174
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/04/2021
ms.locfileid: "97858993"
---
# <a name="list---entities-api"></a>List-entidades API

[!INCLUDE [Banner for top of topics](includes/banner.md)]

> [!NOTE]
> Esta solicitud no está disponible para Office 365 Cloud App Security.

Ejecute la solicitud GET o POST para capturar una lista de entidades que coinciden con los filtros especificados.

## <a name="http-request"></a>Solicitud HTTP

```rest
GET /api/v1/entities/
```

```rest
POST /api/v1/entities/
```

## <a name="request-body-parameters"></a>Parámetros del cuerpo de la solicitud

| Parámetro | Description |
| --- | --- |
| filters | Filtre los objetos con todos los filtros de búsqueda de la solicitud; consulte [filtros de entidad](api-entities.md#filters) para obtener más detalles. |
| sortDirection | Dirección de ordenación. Los valores posibles son: `asc` y `desc` |
| sortField | Campos usados para ordenar entidades. Los valores posibles son:<br />- **fecha**: fecha en la que se creó la entidad.<br />- **gravedad**: la gravedad de la entidad |
| skip | Omite el número de registros especificado. |
| limit | Número máximo de registros devueltos por la solicitud |

## <a name="example"></a>Ejemplo

### <a name="request"></a>Solicitud

Este es un ejemplo de la solicitud.

```rest
curl -XPOST -H "Authorization:Token <your_token_key>" "https://<tenant_id>.<tenant_region>.contoso.com/api/v1/entities/" -d '{
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
