---
title: Marcar como API de lectura/alertas
description: En este artículo se describe la solicitud marcar como lectura en la API de alertas de Cloud App Security.
ms.date: 03/27/2020
ms.topic: reference
ms.openlocfilehash: ecf314300e59371fc6cddaeddc0ab4b78efbaaa0
ms.sourcegitcommit: d87372b47ca98e942c2bf94032a6a61902627d69
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/30/2020
ms.locfileid: "96314603"
---
# <a name="mark-as-read---alerts-api"></a>Marcar como API de lectura/alertas

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Ejecute la solicitud POST para marcar la alerta que coincide con la clave principal especificada como leída.

## <a name="http-request"></a>Solicitud HTTP

```rest
POST /api/v1/alerts/<pk>/read/
```

## <a name="request-url-parameters"></a>Parámetros de URL de solicitud

| Parámetro | Description |
| --- | --- |
| pk | El ID. de la alerta |

## <a name="example"></a>Ejemplo

### <a name="request"></a>Solicitud

Este es un ejemplo de la solicitud.

```rest
curl -XPOST -H "Authorization:Token <your_token_key>" "https://<tenant_id>.<tenant_region>.contoso.com/api/v1/alerts/<pk>/read/"
```

[!INCLUDE [Open support ticket](includes/support.md)]
