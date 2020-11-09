---
title: API de lista de archivos
description: En este artículo se describe la solicitud de lista de la API de archivos de Cloud App Security.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 03/27/2020
ms.topic: reference
ms.collection: M365-security-compliance
ms.service: cloud-app-security
ms.suite: ems
ms.openlocfilehash: 4cfe5e15964be0a4add19f11b571254235e1a72c
ms.sourcegitcommit: 288f3011c0ce0e5f2d8cbaa9057a63be044465f7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/09/2020
ms.locfileid: "94375047"
---
# <a name="list---files-api"></a>API de lista de archivos

[!INCLUDE [Banner for top of topics](includes/banner.md)]

> [!NOTE]
>
> - Esta API estará en desuso pronto. Microsoft Cloud App Security está desarrollando una nueva solución para identificar y actuar sobre los archivos que infringen las directivas.
> - Este punto de conexión puede agotar el tiempo de espera al filtrar y paginar colecciones de gran tamaño.
> - Esta API no está disponible para Office 365 Cloud App Security.

Ejecute la solicitud GET o POST para capturar una lista de archivos que coinciden con los filtros especificados.

## <a name="http-request"></a>Solicitud HTTP

```rest
GET /api/v1/files/
```

```rest
POST /api/v1/files/
```

## <a name="request-body-parameters"></a>Parámetros del cuerpo de la solicitud

| Parámetro | Descripción |
| --- | --- |
| filters | Filtre los objetos con todos los filtros de búsqueda de la solicitud; consulte [filtros de archivo](api-files.md#filters) para obtener más detalles. |
| skip | Omite el número de registros especificado. |
| limit | Número máximo de registros devueltos por la solicitud |

## <a name="example"></a>Ejemplo

### <a name="request"></a>Solicitud

Este es un ejemplo de la solicitud.

```rest
curl -XPOST -H "Authorization:Token <your_token_key>" "https://<tenant_id>.<tenant_region>.contoso.com/api/v1/files/" -d '{
  "filters": {
    // some filters
  },
  "skip": 5,
  "limit": 10
  ...
}'
```

### <a name="response"></a>Response

Devuelve una lista de archivos en formato JSON.

```json
{
  "total": 5 // total number of records
  "hasNext": true // whether there is more data to show or not.
  "data": [
    // returned records
  ]
}
```

[!INCLUDE [Open support ticket](includes/support.md)]
