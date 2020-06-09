---
title: 'Inicio de la carga de archivos: API de Cloud Discovery'
description: En este artículo se describe la solicitud de upload_url en la API de Cloud Discovery de Cloud App Security.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 03/27/2020
ms.topic: reference
ms.collection: M365-security-compliance
ms.service: cloud-app-security
ms.suite: ems
ms.openlocfilehash: 6259161ecaa02a7820d97aafc5b7efb98c988c07
ms.sourcegitcommit: 286f8d5d940d1bb9a09daa3070ac4fc3768208f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/08/2020
ms.locfileid: "84505394"
---
# <a name="initiate-file-upload---cloud-discovery-api"></a>Inicio de la carga de archivos: API de Cloud Discovery

*Se aplica a: Microsoft Cloud App Security*

Ejecute la solicitud GET para iniciar el proceso de carga. Esta llamada, la primera de las tres, devuelve una dirección URL que se usará más adelante para realizar la solicitud de carga (PUT).

## <a name="http-request"></a>Solicitud HTTP

```rest
GET /api/v1/discovery/upload_url/
```

## <a name="request-url-parameters"></a>Parámetros de URL de solicitud

| Parámetro | Descripción |
| --- |--- |
| filename | Nombre del archivo que desea cargar para el procesamiento de Cloud Discovery |
| source | El tipo de archivo de registro de Cloud Discovery que se va a cargar. |

Actualmente se admiten los siguientes tipos de origen:

- BARRACUDA
- BLUECOAT
- CHECKPOINT
- CHECKPOINT_CEF_SYSLOG
- CHECKPOINT_SMART_VIEW_TRACKER
- CHECKPOINT_XML
- CISCO_ASA
- CISCO_ASA_FIREPOWER
- CISCO_FIREPOWER_V6_SYSLOG
- CISCO_FWSM
- CISCO_IRONPORT_PROXY
- CISCO_IRONPORT_WSA_II
- CISCO_SCAN_SAFE
- CLAVISTER
- CORRATA
- FORCEPOINT
- FORCEPOINT_LEEF
- FORTIGATE
- GENERIC_CEF
- GENERIC_LEEF
- GENERIC_W3C
- I_FILTER
- IBOSS
- JUNIPER_SRX
- JUNIPER_SRX_SD
- JUNIPER_SRX_WELF
- JUNIPER_SSG
- MACHINE_ZONE_MERAKI
- MCAFEE_SWG
- MICROSOFT_ISA_W3C
- PALO_ALTO
- PALO_ALTO_LEEF
- SONICWALL_SYSLOG
- SOPHOS_CYBEROAM
- SOPHOS_SG
- SOPHOS_XG
- SQUID
- SQUID_NATIVE
- STORMSHIELD
- WEBSENSE_SIEM_CEF
- WEBSENSE_V7_5
- ZSCALER
- ZSCALER_CEF
- ZSCALER_QRADAR

> [!NOTE]
> Si no encuentra el formato de archivo, realice una carga manual mediante el portal.

## <a name="response-parameters"></a>Parámetros de respuesta

| Parámetro | Descripción |
| --- | --- |
| url | La dirección URL de destino que llevará a cabo la carga Cloud Discovery. |
| provider | "Azure" o "AWS", una indicación de si la carga es el destino de almacenamiento de Windows Azure Storage y AWS S3. |

## <a name="example"></a>Ejemplo

### <a name="request"></a>Solicitud

Este es un ejemplo de la solicitud.

```rest
curl -XGET -H "Authorization:<your_token_key>" "https://<tenant_id>.<tenant_region>.contoso.com/api/v1/discovery/upload_url/?filename=my_discovery_file.txt&source=LOG_3COM"
```

### <a name="response"></a>Response

Este es un ejemplo de la respuesta JSON.

```json
{
  "url": "https://<initiate_file_upload_response_url>",
  "provider": "azure"
}
```

[!INCLUDE [Open support ticket](includes/support.md)]
