---
title: Enumerar API de enriquecimiento de datos
description: En este artículo se describe la solicitud de lista de la API de enriquecimiento de datos de Cloud App Security.
ms.date: 12/13/2020
ms.topic: reference
ms.openlocfilehash: a817431dc7788900294b8f6fde26beb326a21d87
ms.sourcegitcommit: 90df07ce9cd64fd9c46fb6563f0249079204e174
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/04/2021
ms.locfileid: "97859231"
---
# <a name="list---data-enrichment-api"></a>Enumerar API de enriquecimiento de datos

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Ejecute la solicitud GET o POST para capturar una lista de intervalos IP que coinciden con los filtros especificados.

## <a name="http-request"></a>Solicitud HTTP

```rest
GET /api/v1/subnet/
```

```rest
POST /api/v1/subnet/
```

## <a name="request-body-parameters"></a>Parámetros del cuerpo de la solicitud

| Parámetro | Description |
| --- | --- |
| filters | Filtre los objetos con todos los filtros de búsqueda de la solicitud; consulte [filtros de intervalo IP](api-data-enrichment.md#filters) para obtener más detalles. |
| sortDirection | Dirección de ordenación. Los valores posibles son: `asc` y `desc` |
| sortField | Campos usados para ordenar intervalos IP. Los valores posibles son:<br />- **categoría**: la categoría del intervalo IP<br />- **Tags**: etiquetas del intervalo IP<br />- **nombre**: el nombre del intervalo de direcciones IP |
| skip | Omite el número de registros especificado. |
| limit | Número máximo de registros devueltos por la solicitud |

## <a name="example"></a>Ejemplo

### <a name="request"></a>Solicitud

Este es un ejemplo de la solicitud.

```rest
curl -XPOST -H "Authorization:Token <your_token_key>" "https://<tenant_id>.<tenant_region>.contoso.com/api/v1/subnet/" -d '{
  "filters": {
    // some filters
  },
  "skip": 5,
  "limit": 10
  ...
}'
```

### <a name="response"></a>Response

Devuelve una lista de intervalos IP en formato JSON. Para obtener información sobre los campos de respuesta, vea [propiedades](api-data-enrichment.md#properties).

```json
{
  "total": 1 // total number of records
  "hasNext": false // whether there is more data to show or not.
  "data": [
    {
      // returned records
      "_id": "5fd767259cd24bb563567d7c",
      "name": "range name",
      "subnets": [
        {
          "mask": 112,
          "address": "0000:0000:0000:0000:0000:ffff:c5c6:0000",
          "originalString": "197.198.192.20/16"
        }
      ],
      "location": {
        "name": "United States",
        "latitude": 39.5035514831543,
        "longitude": -99.01830291748047,
        "countryCode": "US",
        "countryName": "United States"
      },
      "organization": "isp name",
      "tags": [
        {
          "_id": "5ce2aaf42207ad108c76fa3a",
          "id": "000000290000000000000000",
          "target": 1,
          "type": 2,
          "name": "Contoso",
          "nameTemplate": {
            "template": "SAGE_BUILTIN_TAG_CONTOSO_NAME"
          },
          "description": "IP addresses used by Contoso",
          "descriptionTemplate": {
            "template": "SAGE_BUILTIN_TAG_CONTOSO_DESCRIPTION"
          },
          "visibility": 0,
          "status": 0,
          "_tid": 113348336
        }
      ],
      "category": 5,
      "lastModified": 1607952165309.8032,
      "_tid": 113348336
    }
  ]
}
```

[!INCLUDE [Open support ticket](includes/support.md)]
