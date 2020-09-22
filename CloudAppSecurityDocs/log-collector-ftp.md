---
title: Configuración de FTP del recopilador de registros
description: En este artículo se describe el proceso para modificar la configuración de Docker de Cloud Discovery para Cloud App Security.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 8/7/2019
ms.topic: how-to
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: a53ebad2900fe14a570b048f285d56b620bf4135
ms.sourcegitcommit: 575f2b2efa9ca4477d7e60271d21e225ef2c38ea
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/22/2020
ms.locfileid: "90879325"
---
# <a name="log-collector-ftp-configuration"></a>Configuración de FTP del recopilador de registros

[!INCLUDE [Banner for top of topics](includes/banner.md)]

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

2. Vaya al directorio `ssl_update`.
3. Cargue los nuevos archivos de certificado en el directorio `ssl_update` (los nombres son obligatorios).

    ![Cargar archivos de certificado](media/new-certs.png)

    - **Para FTP:** se requiere un solo archivo. El archivo tiene los datos de la clave y del certificado, en ese orden, y se denomina **pure-ftpd.pem**.
    - **Para syslog:** Se necesitan tres archivos: **CA. pem**, * * Server-Key. PEM y **Server-cert. pem**. Si falta alguno de ellos, la actualización no se llevará a cabo.

4. En una ejecución de terminal: `docker exec -t <collector name> update_certs`. El comando generará una salida similar a la que se ve en la captura de pantalla que se muestra a continuación.

    ![Actualizar archivos de certificado](media/update-certs.png)

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Implementación de Cloud Discovery](set-up-cloud-discovery.md)

[!INCLUDE [Open support ticket](includes/support.md)]
