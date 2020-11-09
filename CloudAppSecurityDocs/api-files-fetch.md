---
title: 'Fetch: API de archivos'
description: En este artículo se describe la solicitud de captura en la API de archivos de Cloud App Security.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 03/27/2020
ms.topic: reference
ms.collection: M365-security-compliance
ms.service: cloud-app-security
ms.suite: ems
ms.openlocfilehash: 5127f1e09fc5cd34ce0a45fd05ed1714e94cd94a
ms.sourcegitcommit: 288f3011c0ce0e5f2d8cbaa9057a63be044465f7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/09/2020
ms.locfileid: "94375079"
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

| Parámetro | Descripción |
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
