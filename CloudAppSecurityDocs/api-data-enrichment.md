---
title: 'Creación de un intervalo de direcciones IP: API de enriquecimiento de datos'
description: En este artículo se describe la solicitud de creación de un intervalo de direcciones IP en la API de enriquecimiento de datos de Cloud App Security.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 03/27/2020
ms.topic: reference
ms.collection: M365-security-compliance
ms.service: cloud-app-security
ms.suite: ems
ms.openlocfilehash: 8739566fb2bd9413651c9f1e14257e62e6f4589e
ms.sourcegitcommit: c114a9e04589e1a3e0b5350862b3e6daf18e3d30
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/20/2020
ms.locfileid: "88658871"
---
# <a name="create-ip-address-range---data-enrichment-api"></a>Creación de un intervalo de direcciones IP: API de enriquecimiento de datos

*Se aplica a: Microsoft Cloud App Security*

Ejecute la solicitud POST para agregar un nuevo intervalo de direcciones IP.

## <a name="http-request"></a>Solicitud HTTP

```rest
POST /api/v1/subnet/
```

## <a name="request-body-parameters"></a>Parámetros del cuerpo de la solicitud

| Parámetro | Descripción |
| --- | --- |
| category | Identificador de la categoría de rango |
| subredes | Una matriz de máscaras como cadenas (IPv4/IPv6) |
| Organización (opcional) | El ISP registrado |
| etiquetas (opcional) | Una matriz de etiquetas (objetos con la propiedad "Text" establecida con el nombre de etiqueta): nuevo o existente |

Actualmente se admiten las siguientes categorías:

| Category | Identificador |
| --- | -- |
| Corporativos | 1 |
| Administrativa | 2 |
| Riesgo | 3 |
| VPN | 4 |
| Proveedor de servicios en la nube | 5 |
| Otros | 6 |

## <a name="example"></a>Ejemplo

### <a name="request"></a>Solicitud

Este es un ejemplo de la solicitud.

```rest
curl -XPOST -H "Authorization:Token <your_token_key>" "https://<tenant_id>.<tenant_region>.contoso.com/api/v1/subnet/create_rule/" -d '{
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

### <a name="response"></a>Response

Devuelve el identificador del nuevo intervalo como una cadena.

[!INCLUDE [Open support ticket](includes/support.md)]
