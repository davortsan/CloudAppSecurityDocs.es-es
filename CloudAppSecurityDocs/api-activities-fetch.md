---
title: 'Fetch: API de actividades'
description: En este artículo se describe la solicitud de captura en la API de actividades de Cloud App Security.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 03/27/2020
ms.topic: reference
ms.collection: M365-security-compliance
ms.service: cloud-app-security
ms.suite: ems
ms.openlocfilehash: 151edb2f763f55fa21f10b8b869703a31406dffb
ms.sourcegitcommit: 6e47d0348283d105614d81db4e7737fc837ed20b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/20/2020
ms.locfileid: "88657680"
---
# <a name="fetch---activities-api"></a>Fetch: API de actividades

*Se aplica a: Microsoft Cloud App Security*

Ejecute la solicitud GET para capturar la actividad que coincide con la clave principal especificada.

## <a name="http-request"></a>Solicitud HTTP

```rest
GET /api/v1/activities/<pk>/
```

## <a name="request-url-parameters"></a>Parámetros de URL de solicitud

| Parámetro | Descripción |
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
