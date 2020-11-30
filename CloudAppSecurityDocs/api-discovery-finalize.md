---
title: 'Finalización de la carga de archivos: API de Cloud Discovery'
description: En este artículo se describe la solicitud de done_upload en la API de Cloud Discovery de Cloud App Security.
ms.date: 03/27/2020
ms.topic: reference
ms.openlocfilehash: 52adeb1b0a9f858a5c4251ff9a79cb4a24656a14
ms.sourcegitcommit: d87372b47ca98e942c2bf94032a6a61902627d69
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/30/2020
ms.locfileid: "96314484"
---
# <a name="finalize-file-upload---cloud-discovery-api"></a>Finalización de la carga de archivos: API de Cloud Discovery

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Una vez completada correctamente la carga del contenido del archivo, notifíquelo para comenzar el procesamiento del archivo.

## <a name="http-request"></a>Solicitud HTTP

```rest
POST /api/v1/discovery/done_upload/
```

## <a name="request-body-parameters"></a>Parámetros del cuerpo de la solicitud

| Parámetro | Description |
| --- | --- |
| uploadUrl | La dirección URL que se devolvió en la llamada inicial que solicita la carga de archivos. |
| inputStreamName | Nombre del origen de datos desde el que entran los datos (representa el dispositivo). |
| uploadAsSnapshot | Cargue los datos como un informe de instantáneas en lugar de cargarlos en un informe continuo. Si se establece este parámetro, el informe se creará con el nombre especificado en inputStreamName. |

## <a name="example"></a>Ejemplo

### <a name="request"></a>Solicitud

Este es un ejemplo de la solicitud.

```rest
curl -XPOST -H "Authorization:Token <your_token_key>" "https://<tenant_id>.<tenant_region>.contoso.com/api/v1/discovery/done_upload/" -d "uploadUrl=<initiate_file_upload_response_url>"
```

[!INCLUDE [Open support ticket](includes/support.md)]
