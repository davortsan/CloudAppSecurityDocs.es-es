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
ms.openlocfilehash: e7904bcd421d5c2132c1202d2b644a2ee9f52599
ms.sourcegitcommit: 575f2b2efa9ca4477d7e60271d21e225ef2c38ea
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/22/2020
ms.locfileid: "90879974"
---
# <a name="bulk-resolve---alerts-api"></a>Resolución en masa: API de alertas

[!INCLUDE [Banner for top of topics](includes/banner.md)]

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
curl -XPOST -H "Authorization:Token <your_token_key>" "https://<tenant_id>.<tenant_region>.contoso.com/api/v1/alerts/resolve" -d '{
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
