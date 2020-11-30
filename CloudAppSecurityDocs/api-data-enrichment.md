---
title: 'Creación de un intervalo de direcciones IP: API de enriquecimiento de datos'
description: En este artículo se describe la solicitud de creación de un intervalo de direcciones IP en la API de enriquecimiento de datos de Cloud App Security.
ms.date: 03/27/2020
ms.topic: reference
ms.openlocfilehash: ec84185e0523b8b9f9f172e1940302656f10316b
ms.sourcegitcommit: d87372b47ca98e942c2bf94032a6a61902627d69
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/30/2020
ms.locfileid: "96314518"
---
# <a name="create-ip-address-range---data-enrichment-api"></a>Creación de un intervalo de direcciones IP: API de enriquecimiento de datos

[!INCLUDE [Banner for top of topics](includes/banner.md)]

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
