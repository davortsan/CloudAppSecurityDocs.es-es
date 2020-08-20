---
title: 'Fetch: API de alertas'
description: En este artículo se describe la solicitud de captura en la API de alertas de Cloud App Security.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 03/27/2020
ms.topic: reference
ms.collection: M365-security-compliance
ms.service: cloud-app-security
ms.suite: ems
ms.openlocfilehash: 9d61d4456674632aab09875b6c534593947856cc
ms.sourcegitcommit: 6e47d0348283d105614d81db4e7737fc837ed20b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/20/2020
ms.locfileid: "88657340"
---
# <a name="fetch---alerts-api"></a>Fetch: API de alertas

*Se aplica a: Microsoft Cloud App Security*

Ejecute la solicitud GET para capturar la alerta que coincide con la clave principal especificada.

## <a name="http-request"></a>Solicitud HTTP

```rest
GET /api/v1/alerts/<pk>/
```

## <a name="request-url-parameters"></a>Parámetros de URL de solicitud

| Parámetro | Descripción |
| --- | --- |
| pk | El ID. de la alerta |

## <a name="example"></a>Ejemplo

### <a name="request"></a>Solicitud

Este es un ejemplo de la solicitud.

```rest
curl -XPOST -H "Authorization:Token <your_token_key>" "https://<tenant_id>.<tenant_region>.contoso.com/api/v1/alerts/<pk>/"
```

### <a name="response"></a>Response

Devuelve la alerta especificada en formato JSON.

```json
{
  // alert record
}
```

[!INCLUDE [Open support ticket](includes/support.md)]
