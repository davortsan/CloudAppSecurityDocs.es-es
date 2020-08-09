---
title: 'Descartar: API de alertas'
description: En este artículo se describe la solicitud de descartar en la API de alertas de Cloud App Security.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 03/27/2020
ms.topic: reference
ms.collection: M365-security-compliance
ms.service: cloud-app-security
ms.suite: ems
ms.openlocfilehash: cebdc20f52b295106a2147f9438990504819e857
ms.sourcegitcommit: 4450119e1c7e2c54357dca955621327f9c343422
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2020
ms.locfileid: "88027030"
---
# <a name="dismiss---alerts-api"></a>Descartar: API de alertas

*Se aplica a: Microsoft Cloud App Security*

Ejecute la solicitud POST para descartar la alerta que coincide con la clave principal especificada.

## <a name="http-request"></a>Solicitud HTTP

```rest
POST /api/v1/alerts/<pk>/dismiss/
```

## <a name="request-url-parameters"></a>Parámetros de URL de solicitud

| Parámetro | Descripción |
| --- | --- |
| pk | El ID. de la alerta |

## <a name="request-body-parameters"></a>Parámetros del cuerpo de la solicitud

| Parámetro | Descripción |
| --- | --- |
| comment | Comentario sobre por qué se descartó la alerta |

## <a name="example"></a>Ejemplo

### <a name="request"></a>Solicitud

Este es un ejemplo de la solicitud.

```rest
curl -XPOST -H "Authorization:<your_token_key>" "https://<tenant_id>.<tenant_region>.contoso.com/api/v1/alerts/<pk>/dismiss/" -d '{
  "comment": "Irrelevant"
}'
```

[!INCLUDE [Open support ticket](includes/support.md)]
