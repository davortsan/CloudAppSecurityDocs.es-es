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
ms.openlocfilehash: 78f41250805255f9a17a9dcd62aade52274091a1
ms.sourcegitcommit: 6e47d0348283d105614d81db4e7737fc837ed20b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/20/2020
ms.locfileid: "88657699"
---
# <a name="fetch---files-api"></a>Fetch: API de archivos

*Se aplica a: Microsoft Cloud App Security*

> [!NOTE]
> Esta solicitud no está disponible para Office 365 Cloud App Security.

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
