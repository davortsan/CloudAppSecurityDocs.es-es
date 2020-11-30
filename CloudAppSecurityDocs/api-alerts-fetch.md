---
title: 'Fetch: API de alertas'
description: En este artículo se describe la solicitud de captura en la API de alertas de Cloud App Security.
ms.date: 03/27/2020
ms.topic: reference
ms.openlocfilehash: 8332805803dc05d991ef153b8402afb39b7b0cc1
ms.sourcegitcommit: d87372b47ca98e942c2bf94032a6a61902627d69
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/30/2020
ms.locfileid: "96314620"
---
# <a name="fetch---alerts-api"></a>Fetch: API de alertas

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Ejecute la solicitud GET para capturar la alerta que coincide con la clave principal especificada.

## <a name="http-request"></a>Solicitud HTTP

```rest
GET /api/v1/alerts/<pk>/
```

## <a name="request-url-parameters"></a>Parámetros de URL de solicitud

| Parámetro | Description |
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
