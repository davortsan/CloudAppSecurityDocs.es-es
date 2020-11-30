---
title: 'Comentarios: API de actividades'
description: En este artículo se describe la solicitud de comentarios en la API de actividades de Cloud App Security.
ms.date: 03/27/2020
ms.topic: reference
ms.openlocfilehash: f21dbee6d43236710f6a5846962c8444c52cddc7
ms.sourcegitcommit: d87372b47ca98e942c2bf94032a6a61902627d69
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/30/2020
ms.locfileid: "96314739"
---
# <a name="feedback-on-activity---activities-api"></a>Comentarios sobre la actividad: API de actividades

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Ejecute la solicitud POST para enviar comentarios sobre la actividad que coincide con la clave principal especificada.

## <a name="http-request"></a>Solicitud HTTP

```rest
POST /api/v1/activities/<pk>/feedback
```

## <a name="request-url-parameters"></a>Parámetros de URL de solicitud

| Parámetro | Description |
| --- | --- |
| pk | Identificador de la actividad. |

## <a name="request-body-parameters"></a>Parámetros del cuerpo de la solicitud

| Parámetro | Description |
| --- | --- |
| feedback | Los comentarios de la actividad |

## <a name="example"></a>Ejemplo

### <a name="request"></a>Solicitud

Este es un ejemplo de la solicitud.

```rest
curl -XPOST -H "Authorization:Token <your_token_key>" "https://<tenant_id>.<tenant_region>.contoso.com/api/v1/activities/<pk>/feedback" -d '{
  "feedbackValue": "0",
  "feedbackText": "Irrelevant",
  "allowContact": false,
  "contactEmail": "some.contact.address"
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
