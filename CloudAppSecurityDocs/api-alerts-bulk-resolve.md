---
title: 'Resolución en masa: API de alertas'
description: En este artículo se describe la solicitud de resolución masiva en la API de alertas de Cloud App Security.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 03/27/2020
ms.topic: reference
ms.collection: M365-security-compliance
ms.service: cloud-app-security
ms.suite: ems
ms.openlocfilehash: 11d1cc9651a48042f9b7b7223e36da35b389fed4
ms.sourcegitcommit: 286f8d5d940d1bb9a09daa3070ac4fc3768208f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/08/2020
ms.locfileid: "84505564"
---
# <a name="bulk-resolve---alerts-api"></a>Resolución en masa: API de alertas

*Se aplica a: Microsoft Cloud App Security*

Ejecute la solicitud POST para resolver varias alertas que coinciden con los filtros especificados.

## <a name="http-request"></a>Solicitud HTTP

```rest
POST /api/v1/alerts/resolve/
```

## <a name="request-body-parameters"></a>Parámetros del cuerpo de la solicitud

| Parámetro | Descripción |
| --- | --- |
| filters | Filtre los objetos con todos los filtros de búsqueda de la solicitud; consulte [filtros de alerta](api-alerts.md#filters) para obtener más detalles. |
| comment | Comentario sobre por qué se resuelven las alertas |

## <a name="example"></a>Ejemplo

### <a name="request"></a>Solicitud

Este es un ejemplo de la solicitud.

```rest
curl -XPOST -H "Authorization:<your_token_key>" "https://<tenant_id>.<tenant_region>.contoso.com/api/v1/alerts/resolve" -d '{
  "comment": "Irrelevant",
  "filters": {
    "id": {
      "eq": [
        "55af7415f8a0a7a29eef2e1f",
        "55af741cf8a0a7a29eef2e20"
      ]
    }
  }
}'
```

[!INCLUDE [Open support ticket](includes/support.md)]