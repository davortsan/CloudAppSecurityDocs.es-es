---
title: 'Eliminar intervalo de direcciones IP: API de enriquecimiento de datos'
description: En este artículo se describe la solicitud de eliminación de intervalo de direcciones IP en la API de enriquecimiento de datos de Cloud App Security.
ms.date: 12/13/2020
ms.topic: reference
ms.openlocfilehash: 0cda04381501283526c77240debd7cfbe4f672fc
ms.sourcegitcommit: 90df07ce9cd64fd9c46fb6563f0249079204e174
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/04/2021
ms.locfileid: "97859240"
---
# <a name="delete-ip-address-range---data-enrichment-api"></a>Eliminar intervalo de direcciones IP: API de enriquecimiento de datos

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Ejecute la solicitud de eliminación para eliminar un intervalo de direcciones IP.

## <a name="http-request"></a>Solicitud HTTP

```rest
DELETE /api/v1/subnet/<ip_range_id>/
```

## <a name="example"></a>Ejemplo

### <a name="request"></a>Solicitud

Este es un ejemplo de la solicitud.

```rest
curl -X DELETE -H "Authorization:Token <your_token_key>" "https://<tenant_id>.<tenant_region>.contoso.com/api/v1/subnet/<ip_range_id>/"
```

[!INCLUDE [Open support ticket](includes/support.md)]
