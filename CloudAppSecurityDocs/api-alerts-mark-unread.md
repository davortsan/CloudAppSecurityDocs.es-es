---
title: 'Marcar como no leída: API de alertas'
description: En este artículo se describe la solicitud marcar como no leída en la API de alertas de Cloud App Security.
ms.date: 03/27/2020
ms.topic: reference
ms.openlocfilehash: 5fb1a23183d0077a945fdfb1cb8637151921e509
ms.sourcegitcommit: d87372b47ca98e942c2bf94032a6a61902627d69
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/30/2020
ms.locfileid: "96314569"
---
# <a name="mark-as-unread---alerts-api"></a>Marcar como no leída: API de alertas

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Ejecute la solicitud POST para marcar la alerta que coincide con la clave principal especificada como no leída.

## <a name="http-request"></a>Solicitud HTTP

```rest
POST /api/v1/alerts/<pk>/unread/
```

## <a name="request-url-parameters"></a>Parámetros de URL de solicitud

| Parámetro | Description |
| --- | --- |
| pk | El ID. de la alerta |

## <a name="example"></a>Ejemplo

### <a name="request"></a>Solicitud

Este es un ejemplo de la solicitud.

```rest
curl -XPOST -H "Authorization:Token <your_token_key>" "https://<tenant_id>.<tenant_region>.contoso.com/api/v1/alerts/<pk>/unread/"
```

[!INCLUDE [Open support ticket](includes/support.md)]
