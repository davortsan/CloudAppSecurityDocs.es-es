---
title: 'Cierre de falsos positivos: API de alertas'
description: En este artículo se describe cómo cerrar en bloque una alerta como una solicitud falsa positiva en la API de alertas de Cloud App Security.
ms.date: 10/20/2020
ms.topic: reference
ms.openlocfilehash: 309e0fc4b7c89ab4f24ace1dd0b790b73a66bf6f
ms.sourcegitcommit: d87372b47ca98e942c2bf94032a6a61902627d69
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/30/2020
ms.locfileid: "96314654"
---
# <a name="close-false-positive---alerts-api"></a>Cierre de falsos positivos: API de alertas

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Ejecute la solicitud POST para cerrar varias alertas que coincidan con los filtros especificados como falsos positivos (una alerta sobre una actividad no malintencionada).

## <a name="http-request"></a>Solicitud HTTP

```rest
POST /api/v1/alerts/close_false_positive/
```

## <a name="request-body-parameters"></a>Parámetros del cuerpo de la solicitud

| Parámetro | Description |
| --- | --- |
| filters | Filtre los objetos con todos los filtros de búsqueda de la solicitud; consulte [filtros de alerta](api-alerts.md#filters) para obtener más detalles. |
| comment | Un Comentario sobre por qué se descartan las alertas |
| reasonId | Razón por la que se cierran las alertas como falso positivo. Proporcionar un motivo ayuda a mejorar la precisión de la detección a lo largo del tiempo. Los valores posibles son:<br /><br />**0**: no es de interés<br />**1**: demasiadas alertas similares<br />**3**: la alerta no es precisa<br />**4**: otros |
| sendFeedback | Un valor booleano que indica que se proporciona información sobre esta alerta. Valor predeterminado: false |
| feedbackText | El texto de los comentarios |
| allowContact | Un valor booleano que indica que se proporciona consentimiento para ponerse en contacto con el usuario. Valor predeterminado: false |
| contactEmail | La dirección de correo electrónico del usuario. |

## <a name="example"></a>Ejemplo

### <a name="request"></a>Solicitud

Este es un ejemplo de la solicitud.

```rest
curl -XPOST -H "Authorization:Token <your_token_key>" "https://<tenant_id>.<tenant_region>.contoso.com/api/v1/alerts/close_false_positive/" -d '{
  "filters": {
    "id": {
      "eq": [
        "55af7415f8a0a7a29eef2e1f",
        "55af741cf8a0a7a29eef2e20",
        "5f8d70bfc1ffb25b0a541c7d"
      ]
    }
  },
  "comment": "Irrelevant",
  "reasonId": 0,
  "sendFeedback": true,
  "feedbackText": "Feedback text",
  "allowContact": true,
  "contactEmail": " user@contoso.com"
}'
```

[!INCLUDE [Open support ticket](includes/support.md)]
