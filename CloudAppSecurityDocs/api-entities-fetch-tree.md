---
title: 'Captura de árbol de entidades: API de entidades'
description: En este artículo se describe la solicitud de captura del árbol de entidades en la API de entidades de Cloud App Security.
ms.date: 03/27/2020
ms.topic: reference
ms.openlocfilehash: 70e01ffa31ddfe13434c0a1705f2af98b43de6b5
ms.sourcegitcommit: d87372b47ca98e942c2bf94032a6a61902627d69
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/30/2020
ms.locfileid: "96314297"
---
# <a name="fetch-entity-tree---entities-api"></a>Captura de árbol de entidades: API de entidades

[!INCLUDE [Banner for top of topics](includes/banner.md)]

> [!NOTE]
> Esta solicitud no está disponible para Office 365 Cloud App Security.

Ejecute la solicitud GET para recuperar todas las entidades relacionadas con la entidad que coincide con la clave principal especificada. Si la entidad es un usuario, captura todas las cuentas asociadas al usuario. Si la entidad es una cuenta, captura el elemento primario y los elementos del mismo nivel de la entidad.

## <a name="http-request"></a>Solicitud HTTP

```rest
GET /api/v1/entities/<pk>/retrieve_tree/
```

## <a name="request-url-parameters"></a>Parámetros de URL de solicitud

| Parámetro | Description |
| --- | --- |
| pk | Identificador de la entidad. |

## <a name="example"></a>Ejemplo

### <a name="request"></a>Solicitud

Este es un ejemplo de la solicitud.

```rest
curl -XPOST -H "Authorization:Token <your_token_key>" "https://<tenant_id>.<tenant_region>.contoso.com/api/v1/entities/<pk>/retrieve_tree/"
```

### <a name="response"></a>Response

Devuelve el árbol de entidades especificado en formato JSON.

```json
{
  // entity tree record
}
```

[!INCLUDE [Open support ticket](includes/support.md)]
