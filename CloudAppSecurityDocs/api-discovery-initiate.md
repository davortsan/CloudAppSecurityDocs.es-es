---
title: 'Inicio de la carga de archivos: API de Cloud Discovery'
description: En este artículo se describe la solicitud de upload_url en la API de Cloud Discovery de Cloud App Security.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 10/21/2020
ms.topic: reference
ms.collection: M365-security-compliance
ms.service: cloud-app-security
ms.suite: ems
ms.openlocfilehash: e9ce97ebd5a9bb3e57b6ed6d0a54d91ad54d6039
ms.sourcegitcommit: ce4c0c03292c75a515938433951bdb78270d75a3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/21/2020
ms.locfileid: "92333594"
---
# <a name="initiate-file-upload---cloud-discovery-api"></a>Inicio de la carga de archivos: API de Cloud Discovery

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Ejecute la solicitud GET para iniciar el proceso de carga. Esta llamada, la primera de las tres, devuelve una dirección URL que se usará más adelante para realizar la solicitud de carga (PUT).

## <a name="http-request"></a>Solicitud HTTP

```rest
GET /api/v1/discovery/upload_url/
```

## <a name="request-url-parameters"></a>Parámetros de URL de solicitud

| Parámetro | Description |
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
- CUSTOM_PARSER
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
>
> - Cuando se usa un analizador personalizado, Cloud App Security usará el analizador personalizado asociado al origen de datos seleccionado.
> - Si no encuentra el formato de archivo, realice una carga manual mediante el portal.

## <a name="response-parameters"></a>Parámetros de respuesta

| Parámetro | Descripción |
| --- | --- |
| url | La dirección URL de destino que llevará a cabo la carga Cloud Discovery. |
| provider | "Azure" o "AWS", una indicación de si la carga es el destino de almacenamiento de Windows Azure Storage y AWS S3. |

## <a name="example"></a>Ejemplo

### <a name="request"></a>Solicitud

Este es un ejemplo de la solicitud.

```rest
curl -XGET -H "Authorization:Token <your_token_key>" "https://<tenant_id>.<tenant_region>.contoso.com/api/v1/discovery/upload_url/?filename=my_discovery_file.txt&source=LOG_3COM"
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
