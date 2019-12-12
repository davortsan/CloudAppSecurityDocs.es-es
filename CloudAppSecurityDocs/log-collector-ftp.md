---
title: Configuración de FTP del recopilador de registros
description: En este artículo se describe el proceso para modificar la configuración de Docker de Cloud Discovery para Cloud App Security.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 8/7/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: aba19263cafbc1d91a4a650d4cb67e9e748947db
ms.sourcegitcommit: 6eff466c7a6817b14a60d8c3b2c201c7ae4c2e2c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "74719914"
---
# <a name="log-collector-ftp-configuration"></a>Configuración de FTP del recopilador de registros

*Se aplica a: Microsoft Cloud App Security*

En este artículo se describe cómo modificar la configuración de Docker de Cloud Discovery para Cloud App Security.

## <a name="docker-deployment"></a>Implementación de Docker

Es posible que deba modificar la configuración de Docker de Cloud Discovery para Cloud App Security.

### <a name="changing-the-ftp-password"></a>Cambio de la contraseña FTP

1. Conéctese al host del recopilador de registros.

2. Ejecute `docker exec -it <collector name> pure-pw passwd <ftp user>`:

    1. Escriba la nueva contraseña.
    2. Vuelva a escribir la nueva contraseña para confirmarla.

3. Ejecute `docker exec -it <collector name> pure-pw mkdb` para aplicar el cambio.

    ![cambio de la contraseña ftp](media/ftp-connect.png)

### <a name="customize-certificate-files"></a>Personalización de archivos de certificado

Siga este procedimiento para personalizar los archivos de certificado que utiliza para las conexiones seguras con el Docker de Cloud Discovery.

1. Abra un cliente FTP y conéctese al recopilador de registros.

    ![Conexión al cliente FTP](media/ftp-connect.png)

2. Navegue al directorio `ssl_update`.
3. Cargue los nuevos archivos de certificado en el directorio `ssl_update` (los nombres son obligatorios).

    ![Cambio de la contraseña FTP](media/new-certs.png)

    - **Para FTP:** se requiere un solo archivo. El archivo tiene los datos de la clave y del certificado, en ese orden, y se denomina **pure-ftpd.pem**.
    - **Para Syslog:** se necesitan tres archivos: **ca.pem**, **server-key.pem y **server-cert.pem**. Si falta alguno de ellos, la actualización no se llevará a cabo.

4. En una ejecución de terminal: `docker exec -t <collector name> update_certs`. El comando generará una salida similar a la que se ve en la captura de pantalla que se muestra a continuación.

    ![Cambio de la contraseña FTP](media/update-certs.png)

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Implementar Cloud Discovery](set-up-cloud-discovery.md)

[!INCLUDE [Open support ticket](includes/support.md)]
