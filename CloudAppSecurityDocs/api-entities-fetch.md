---
title: 'Fetch: API de entidades'
description: En este artículo se describe la solicitud de captura en la API de entidades de Cloud App Security.
ms.date: 03/27/2020
ms.topic: reference
ms.openlocfilehash: 34db1003dd3ac23f7bc4d5f14100b6c1ff4f6a2e
ms.sourcegitcommit: d87372b47ca98e942c2bf94032a6a61902627d69
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/30/2020
ms.locfileid: "96314280"
---
# <a name="fetch---entities-api"></a>Fetch: API de entidades

[!INCLUDE [Banner for top of topics](includes/banner.md)]

> [!NOTE]
> Esta solicitud no está disponible para Office 365 Cloud App Security.

Ejecute la solicitud GET para capturar la entidad que coincide con la clave principal especificada.

## <a name="http-request"></a>Solicitud HTTP

```rest
GET /api/v1/entities/<pk>/
```

## <a name="request-url-parameters"></a>Parámetros de URL de solicitud

| Parámetro | Description |
| --- | --- |
| pk | Un diccionario con el identificador de entidad, SaaS e información de instancia codificado como una cadena Base64. Por ejemplo: `{"id":"3fa9f28b-eb0e-463a-ba7b-8089fe9991e2","saas":11161,"inst":0}` codificado como una cadena Base64. |

## <a name="example"></a>Ejemplo

### <a name="request"></a>Solicitud

Este es un ejemplo de la solicitud.

```rest
curl -XPOST -H "Authorization:Token <your_token_key>" "https://<tenant_id>.<tenant_region>.contoso.com/api/v1/entities/<pk>/"
```

### <a name="response"></a>Response

Devuelve la entidad especificada en formato JSON.

```json
{
  // entity record
}
```

[!INCLUDE [Open support ticket](includes/support.md)]
