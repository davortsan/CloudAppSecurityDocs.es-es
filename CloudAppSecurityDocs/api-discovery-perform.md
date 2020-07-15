---
title: Realización de la API de Cloud Discovery de carga de archivos
description: En este artículo se describe la solicitud realizar carga de archivos en la API Cloud Discovery de Cloud App Security.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 03/27/2020
ms.topic: reference
ms.collection: M365-security-compliance
ms.service: cloud-app-security
ms.suite: ems
ms.openlocfilehash: b187b8cfa7b9df0610523baeb02410b76bcf00f4
ms.sourcegitcommit: 286f8d5d940d1bb9a09daa3070ac4fc3768208f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/08/2020
ms.locfileid: "84505384"
---
# <a name="perform-file-upload---cloud-discovery-api"></a>Realización de la API de Cloud Discovery de carga de archivos

*Se aplica a: Microsoft Cloud App Security*

Cargue el contenido del archivo realizando una solicitud HTTP PUT. Se le pedirá que use la dirección URL devuelta por la solicitud de [carga de archivo de inicio](api-discovery-initiate.md) .

Azure y AWS tienen distintos encabezados y limitaciones al cargar archivos en la dirección URL de destino.

> [!NOTE]
>
> - Puede cargar archivos individuales de hasta 5 GB. Si necesita cargar archivos de mayor tamaño, divida los datos de Cloud Discovery en varios fragmentos.
> - Si no sabe qué entorno está ejecutando, Compruebe la solicitud de [Inicio de carga de archivo](api-discovery-initiate.md) , que devuelve esta información.

## <a name="http-request"></a>Solicitud HTTP

```rest
PUT https://<initiate_file_upload_response_url>
```

> [!NOTE]
>
> Para Azure:
> - Si el archivo tiene menos de 64 MB, agregue el encabezado "x-MS-BLOB-Type: BlockBlob" a la solicitud.
> - Si el tamaño del archivo es superior a 64 MB, cárguelo en fragmentos. la forma más fácil de hacerlo es usar el [SDK de Azure](https://azure.microsoft.com/downloads/).

## <a name="example"></a>Ejemplo

### <a name="request"></a>Solicitud

Este es un ejemplo de la solicitud de Azure.

```rest
curl --request PUT --upload-file <file_to_upload> -H "x-ms-blob-type: BlockBlob" "https://<initiate_file_upload_response_url>"
```

Este es un ejemplo de la solicitud del SDK de Java de Azure.

```java
File fileReference = new File("file.name");
// Create a blob using the URI that contains the shared access signature.
CloudBlockBlob sasBlob = new CloudBlockBlob(uri);

// Upload the file to the blob.
sasBlob.upload(new FileInputStream(fileReference), fileReference.length());
```

[!INCLUDE [Open support ticket](includes/support.md)]