---
title: Cierre de la API de alertas benignas
description: En este artículo se describe el cierre masivo de una alerta como solicitud benigna en la API de alertas de Cloud App Security.
ms.date: 10/20/2020
ms.topic: reference
ms.openlocfilehash: cf137f0476b588e66493fabde7bfae354cf41f15
ms.sourcegitcommit: d87372b47ca98e942c2bf94032a6a61902627d69
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/30/2020
ms.locfileid: "96314671"
---
# <a name="close-benign---alerts-api"></a>Cierre de la API de alertas benignas

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Ejecute la solicitud POST para cerrar varias alertas que coinciden con los filtros especificados como benignas (una alerta sobre una actividad sospechosa pero no malintencionada, como una prueba de penetración u otra acción sospechosa autorizada).

## <a name="http-request"></a>Solicitud HTTP

```rest
POST /api/v1/alerts/close_benign/
```

## <a name="request-body-parameters"></a>Parámetros del cuerpo de la solicitud

| Parámetro | Description |
| --- | --- |
| filters | Filtre los objetos con todos los filtros de búsqueda de la solicitud; consulte [filtros de alerta](api-alerts.md#filters) para obtener más detalles. |
| comment | Un Comentario sobre por qué se descartan las alertas |
| reasonId | Razón por la que se cierran las alertas como benignas. Proporcionar un motivo ayuda a mejorar la precisión de la detección a lo largo del tiempo. Los valores posibles son:<br /><br />**2**: la gravedad real es menor<br />**4**: otros<br />**5**: confirmado con el usuario final<br />**6**: desencadenado por la prueba |
| sendFeedback | Un valor booleano que indica que se proporciona información sobre esta alerta. Valor predeterminado: false |
| feedbackText | El texto de los comentarios |
| allowContact | Un valor booleano que indica que se proporciona consentimiento para ponerse en contacto con el usuario. Valor predeterminado: false |
| contactEmail | La dirección de correo electrónico del usuario. |

## <a name="example"></a>Ejemplo

### <a name="request"></a>Solicitud

Este es un ejemplo de la solicitud.

```rest
curl -XPOST -H "Authorization:Token <your_token_key>" "https://<tenant_id>.<tenant_region>.contoso.com/api/v1/alerts/close_benign/" -d '{
  "filters": {
    "id": {
      "eq": [
        "55af7415f8a0a7a29eef2e1f",
        "55af741cf8a0a7a29eef2e20"
        "5f8d70bfc1ffb25b0a541c7d"
      ]
    }
  },
  "comment": "Irrelevant",
  "reasonId": 5,
  "sendFeedback": true,
  "feedbackText": "Feedback text",
  "allowContact": true,
  "contactEmail": " user@contoso.com"
}'
```

[!INCLUDE [Open support ticket](includes/support.md)]
