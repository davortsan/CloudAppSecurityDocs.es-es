---
title: 'Finalización de la carga de archivos: API de Cloud Discovery'
description: En este artículo se describe la solicitud de done_upload en la API de Cloud Discovery de Cloud App Security.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 03/27/2020
ms.topic: reference
ms.collection: M365-security-compliance
ms.service: cloud-app-security
ms.suite: ems
ms.openlocfilehash: 7013a7b079f39a88bc95d583622e2591a7c5a2af
ms.sourcegitcommit: 286f8d5d940d1bb9a09daa3070ac4fc3768208f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/08/2020
ms.locfileid: "84505404"
---
# <a name="finalize-file-upload---cloud-discovery-api"></a>Finalización de la carga de archivos: API de Cloud Discovery

*Se aplica a: Microsoft Cloud App Security*

Una vez completada correctamente la carga del contenido del archivo, notifíquelo para comenzar el procesamiento del archivo.

## <a name="http-request"></a>Solicitud HTTP

```rest
POST /api/v1/discovery/done_upload/
```

## <a name="request-body-parameters"></a>Parámetros del cuerpo de la solicitud

| Parámetro | Descripción |
| --- | --- |
| uploadUrl | La dirección URL que se devolvió en la llamada inicial que solicita la carga de archivos. |
| inputStreamName | Nombre del origen de datos desde el que entran los datos (representa el dispositivo). |
| uploadAsSnapshot | Cargue los datos como un informe de instantáneas en lugar de cargarlos en un informe continuo. Si se establece este parámetro, el informe se creará con el nombre especificado en inputStreamName. |

## <a name="example"></a>Ejemplo

### <a name="request"></a>Solicitud

Este es un ejemplo de la solicitud.

```rest
curl -XPOST -H "Authorization:<your_token_key>" "https://<tenant_id>.<tenant_region>.contoso.com/api/v1/discovery/done_upload/" -d "uploadUrl=<initiate_file_upload_response_url>"
```

[!INCLUDE [Open support ticket](includes/support.md)]
