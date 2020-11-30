---
title: 'Fetch: API de archivos'
description: En este artículo se describe la solicitud de captura en la API de archivos de Cloud App Security.
ms.date: 03/27/2020
ms.topic: reference
ms.openlocfilehash: 7d3faf9630edf3e277b481d5f8bcea87898e67cd
ms.sourcegitcommit: d87372b47ca98e942c2bf94032a6a61902627d69
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/30/2020
ms.locfileid: "96314059"
---
# <a name="fetch---files-api"></a>Fetch: API de archivos

[!INCLUDE [Banner for top of topics](includes/banner.md)]

> [!NOTE]
>
> - Esta API estará en desuso pronto. Microsoft Cloud App Security está desarrollando una nueva solución para identificar y actuar sobre los archivos que infringen las directivas.
> - Esta API no está disponible para Office 365 Cloud App Security.

Ejecute la solicitud GET para capturar el archivo que coincide con la clave principal especificada.

## <a name="http-request"></a>Solicitud HTTP

```rest
GET /api/v1/files/<pk>/
```

## <a name="request-url-parameters"></a>Parámetros de URL de solicitud

| Parámetro | Description |
| --- | --- |
| pk | Identificador del archivo. |

## <a name="example"></a>Ejemplo

### <a name="request"></a>Solicitud

Este es un ejemplo de la solicitud.

```rest
curl -XPOST -H "Authorization:Token <your_token_key>" "https://<tenant_id>.<tenant_region>.contoso.com/api/v1/files/<pk>/"
```

### <a name="response"></a>Response

Devuelve el archivo especificado.

[!INCLUDE [Open support ticket](includes/support.md)]
