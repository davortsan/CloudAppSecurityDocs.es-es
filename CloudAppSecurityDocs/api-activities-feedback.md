---
title: 'Comentarios: API de actividades'
description: En este artículo se describe la solicitud de comentarios en la API de actividades de Cloud App Security.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 03/27/2020
ms.topic: reference
ms.collection: M365-security-compliance
ms.service: cloud-app-security
ms.suite: ems
ms.openlocfilehash: cd6f32c85d0202264a951533a29c26d068337917
ms.sourcegitcommit: 6e47d0348283d105614d81db4e7737fc837ed20b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/20/2020
ms.locfileid: "88657606"
---
# <a name="feedback-on-activity---activities-api"></a>Comentarios sobre la actividad: API de actividades

*Se aplica a: Microsoft Cloud App Security*

Ejecute la solicitud POST para enviar comentarios sobre la actividad que coincide con la clave principal especificada.

## <a name="http-request"></a>Solicitud HTTP

```rest
POST /api/v1/activities/<pk>/feedback
```

## <a name="request-url-parameters"></a>Parámetros de URL de solicitud

| Parámetro | Descripción |
| --- | --- |
| pk | Identificador de la actividad. |

## <a name="request-body-parameters"></a>Parámetros del cuerpo de la solicitud

| Parámetro | Descripción |
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
