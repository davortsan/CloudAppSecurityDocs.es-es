---
title: 'Fetch: API de actividades'
description: En este artículo se describe la solicitud de captura en la API de actividades de Cloud App Security.
ms.date: 03/27/2020
ms.topic: reference
ms.openlocfilehash: dc26c22748aa2a03e7a59208b691c6a3a92527d6
ms.sourcegitcommit: d87372b47ca98e942c2bf94032a6a61902627d69
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/30/2020
ms.locfileid: "96314722"
---
# <a name="fetch---activities-api"></a>Fetch: API de actividades

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Ejecute la solicitud GET para capturar la actividad que coincide con la clave principal especificada.

## <a name="http-request"></a>Solicitud HTTP

```rest
GET /api/v1/activities/<pk>/
```

## <a name="request-url-parameters"></a>Parámetros de URL de solicitud

| Parámetro | Description |
| --- | --- |
| pk | Identificador de la actividad. |

## <a name="example"></a>Ejemplo

### <a name="request"></a>Solicitud

Este es un ejemplo de la solicitud.

```rest
curl -XPOST -H "Authorization:Token <your_token_key>" "https://<tenant_id>.<tenant_region>.contoso.com/api/v1/activities/<pk>/"
```

### <a name="response"></a>Response

Devuelve la actividad especificada en formato JSON.

```json
{
  // activity record
}
```

[!INCLUDE [Open support ticket](includes/support.md)]
