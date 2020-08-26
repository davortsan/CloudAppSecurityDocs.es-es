---
title: Generar script de bloque Cloud Discovery API
description: En este artículo se describe la solicitud de discovery_block_scripts en la API de Cloud Discovery de Cloud App Security.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 03/27/2020
ms.topic: reference
ms.collection: M365-security-compliance
ms.service: cloud-app-security
ms.suite: ems
ms.openlocfilehash: 3a1d9ef4412ddecf2117722b6c060a9f86023814
ms.sourcegitcommit: 04811ae308bcc3cd25b18c5e2379ca92920d9e60
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/26/2020
ms.locfileid: "88876551"
---
# <a name="generate-block-script---cloud-discovery-api"></a>Generar script de bloque Cloud Discovery API

*Se aplica a: Microsoft Cloud App Security*

> [!NOTE]
> Esta solicitud no está disponible para Office 365 Cloud App Security.

Ejecute la solicitud GET para obtener un script de bloque para el dispositivo de red.

## <a name="http-request"></a>Solicitud HTTP

```rest
GET /api/discovery_block_scripts/
```

## <a name="request-url-parameters"></a>Parámetros de URL de solicitud

| Parámetro | Descripción |
| --- | --- |
| format | El formato del dispositivo de red. |

Actualmente se admiten los siguientes formatos:

| Dispositivo | Formato |
| --- | --- |
| BlueCoat ProxySG | 102 |
| Cisco ASA | 104 |
| Fortinet FortiGate | 108 |
| Juniper SRX | 129 |
| Palo Alto | 112 |
| Websense | 135 |
| Zscaler | 120 |

> [!NOTE]
> Si no encuentra el dispositivo, genere un script de bloque manualmente mediante el portal.

## <a name="response"></a>Respuesta

Esta solicitud devuelve el script de bloque como texto.

## <a name="example"></a>Ejemplo

### <a name="request"></a>Solicitud

Este es un ejemplo de la solicitud.

```rest
curl -XGET -H "Authorization:Token <your_token_key>" "https://<tenant_id>.<tenant_region>.contoso.com/api/discovery_block_scripts/?format=102&type=banned"
```

### <a name="response"></a>Respuesta

```text
url.domain=application.com deny
url.domain=application.be deny
url.domain=application.co deny
```

[!INCLUDE [Open support ticket](includes/support.md)]
