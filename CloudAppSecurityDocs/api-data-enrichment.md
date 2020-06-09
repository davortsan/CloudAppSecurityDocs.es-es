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
ms.openlocfilehash: 790389f16409b5554fe44e0b20d2f584b0fd0fe5
ms.sourcegitcommit: 286f8d5d940d1bb9a09daa3070ac4fc3768208f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/08/2020
ms.locfileid: "84505414"
---
# <a name="create-ip-address-range---data-enrichment-api"></a>Creación de un intervalo de direcciones IP: API de enriquecimiento de datos

*Se aplica a: Microsoft Cloud App Security*

Ejecute la solicitud POST para agregar un nuevo intervalo de direcciones IP.

## <a name="http-request"></a>Solicitud HTTP

```rest
POST /cas/api/subnet/
```

## <a name="request-body-parameters"></a>Parámetros del cuerpo de la solicitud

| Parámetro | Descripción |
| --- | --- |
| category | Identificador de la categoría de rango |
| subnetMasks | Una matriz de máscaras como cadenas (IPv4/IPv6) |
| Organización (opcional) | El ISP registrado |
| etiquetas (opcional) | Una matriz de etiquetas (objetos con la propiedad "Text" establecida con el nombre de etiqueta): nuevo o existente |

Actualmente se admiten las siguientes categorías:

| Category | Identificador |
| --- | -- |
| Corporativos | 1 |
| Administrativo | 2 |
| Riesgo | 3 |
| VPN | 4 |
| Proveedor de nube | 5 |
| Otros | 6 |

## <a name="example"></a>Ejemplo

### <a name="request"></a>Solicitud

Este es un ejemplo de la solicitud.

```rest
curl -XPOST -H "Authorization:<your_token_key>" "https://<tenant_id>.<tenant_region>.contoso.com/cas/api/subnet/create_rule/" -d '{
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
