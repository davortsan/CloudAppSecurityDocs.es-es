---
title: 'Marcar como no leída: API de alertas'
description: En este artículo se describe la solicitud marcar como no leída en la API de alertas de Cloud App Security.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 03/27/2020
ms.topic: reference
ms.collection: M365-security-compliance
ms.service: cloud-app-security
ms.suite: ems
ms.openlocfilehash: 262163c5063e856957477166c6989a9bc5ae8e72
ms.sourcegitcommit: 6e47d0348283d105614d81db4e7737fc837ed20b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/20/2020
ms.locfileid: "88657816"
---
# <a name="mark-as-unread---alerts-api"></a>Marcar como no leída: API de alertas

*Se aplica a: Microsoft Cloud App Security*

Ejecute la solicitud POST para marcar la alerta que coincide con la clave principal especificada como no leída.

## <a name="http-request"></a>Solicitud HTTP

```rest
POST /api/v1/alerts/<pk>/unread/
```

## <a name="request-url-parameters"></a>Parámetros de URL de solicitud

| Parámetro | Descripción |
| --- | --- |
| pk | El ID. de la alerta |

## <a name="example"></a>Ejemplo

### <a name="request"></a>Solicitud

Este es un ejemplo de la solicitud.

```rest
curl -XPOST -H "Authorization:Token <your_token_key>" "https://<tenant_id>.<tenant_region>.contoso.com/api/v1/alerts/<pk>/unread/"
```

[!INCLUDE [Open support ticket](includes/support.md)]
