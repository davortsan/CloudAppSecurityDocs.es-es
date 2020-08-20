---
title: Marcar como API de lectura/alertas
description: En este artículo se describe la solicitud marcar como lectura en la API de alertas de Cloud App Security.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 03/27/2020
ms.topic: reference
ms.collection: M365-security-compliance
ms.service: cloud-app-security
ms.suite: ems
ms.openlocfilehash: 61a8c7edb0533d4b7c6cf2228ef7a83c54541bd7
ms.sourcegitcommit: 6e47d0348283d105614d81db4e7737fc837ed20b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/20/2020
ms.locfileid: "88657867"
---
# <a name="mark-as-read---alerts-api"></a>Marcar como API de lectura/alertas

*Se aplica a: Microsoft Cloud App Security*

Ejecute la solicitud POST para marcar la alerta que coincide con la clave principal especificada como leída.

## <a name="http-request"></a>Solicitud HTTP

```rest
POST /api/v1/alerts/<pk>/read/
```

## <a name="request-url-parameters"></a>Parámetros de URL de solicitud

| Parámetro | Descripción |
| --- | --- |
| pk | El ID. de la alerta |

## <a name="example"></a>Ejemplo

### <a name="request"></a>Solicitud

Este es un ejemplo de la solicitud.

```rest
curl -XPOST -H "Authorization:Token <your_token_key>" "https://<tenant_id>.<tenant_region>.contoso.com/api/v1/alerts/<pk>/read/"
```

[!INCLUDE [Open support ticket](includes/support.md)]
