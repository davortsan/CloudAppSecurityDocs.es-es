---
title: 'Actualización del intervalo de direcciones IP: API de enriquecimiento de datos'
description: En este artículo se describe la solicitud de actualización del intervalo de direcciones IP en la API de enriquecimiento de datos de Cloud App Security.
ms.date: 12/13/2020
ms.topic: reference
ms.openlocfilehash: 7a9b2b14165388daab5f498a028057d7130e644b
ms.sourcegitcommit: 90df07ce9cd64fd9c46fb6563f0249079204e174
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/04/2021
ms.locfileid: "97859232"
---
# <a name="update-ip-address-range---data-enrichment-api"></a>Actualización del intervalo de direcciones IP: API de enriquecimiento de datos

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Ejecute la solicitud POST para actualizar un intervalo de direcciones IP existente.

## <a name="http-request"></a>Solicitud HTTP

```rest
POST /api/v1/subnet/<ip_range_id>/update_rule/
```

## <a name="request-body-parameters"></a>Parámetros del cuerpo de la solicitud

| Parámetro | Descripción |
| --- | --- |
| name | Nombre único del intervalo. |
| category | Identificador de la categoría de intervalo. Proporcionar una categoría le ayuda a reconocer fácilmente las actividades de las direcciones IP interesantes. Los valores posibles son:<br /><br />**1**: empresa<br />**2**: administración<br />**3**: arriesgado<br />**4**: VPN<br />**5**: proveedor de la nube<br />**6**: otros |
| subredes | Una matriz de máscaras como cadenas (IPv4/IPv6) |
| Organización (opcional) | El ISP registrado |
| etiquetas (opcional) | Una matriz de objetos nuevos o existentes, incluidos el nombre de etiqueta, el identificador, la descripción, la plantilla de nombre y el identificador de inquilino. |

## <a name="example"></a>Ejemplo

### <a name="request"></a>Solicitud

Este es un ejemplo de la solicitud.

```rest
curl -XPOST -H "Authorization:Token <your_token_key>" "https://<tenant_id>.<tenant_region>.contoso.com/api/v1/subnet/<ip_range_id>/update_rule/" -d '{
  "name":"range name",
  "category":5,
  "organization":"Microsoft",
  "subnets":[
    "192.168.1.0/24",
    "192.168.2.0/16"
  ],
  "tags":[
    "existing tag"
  ]
}'
```

[!INCLUDE [Open support ticket](includes/support.md)]
