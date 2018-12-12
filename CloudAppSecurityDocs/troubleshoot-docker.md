---
title: Solución de problemas de implementación de Docker para Cloud Discovery | Microsoft Docs
description: En este artículo se describe el proceso para modificar la configuración de Docker de Cloud Discovery para Cloud App Security.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 12/9/2018
ms.topic: conceptual
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 776e834f-3c20-4d5f-9fab-4c5b975edb06
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 69ff240426b86a254128e241c66c59fff1a10c36
ms.sourcegitcommit: c497253a7ab63973bb806607e5f15dece91640be
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/10/2018
ms.locfileid: "53123002"
---
# <a name="troubleshooting-the-microsoft-cloud-app-security-cloud-discovery-deployment"></a>Solución de problemas de implementación de Cloud Discovery para Microsoft Cloud App Security

*Se aplica a: Microsoft Cloud App Security*

En este artículo se describe cómo modificar la configuración de Docker de Cloud Discovery para Cloud App Security.

## <a name="windows-defender-atp-integration"></a>Integración con ATP de Windows Defender

Si ha integrado ATP de Windows Defender con Cloud App Security y no ve los resultados de la integración (no hay ningún informe de **usuarios del punto de conexión de Win10**), debe asegurarse de que las máquinas que conecta son de Windows 10, versión 1809 o posterior. Además, tendrá que esperar dos horas para poder acceder a los datos.

## <a name="docker-deployment"></a>Implementación de Docker

Es posible que deba modificar la configuración de Docker de Cloud Discovery para Cloud App Security. 

### <a name="changing-the-ftp-password"></a>Cambio de la contraseña FTP

1. Conéctese al host del recopilador de registros.

2. Ejecute `docker exec -it <collector name> pure-pw passwd <ftp user>`

    1. Escriba la nueva contraseña.
    2. Vuelva a escribir la nueva contraseña para confirmarla.
 
3. Ejecute `docker exec -it <collector name> pure-pw mkdb` para aplicar el cambio.

  ![cambio de la contraseña ftp](./media/ftp-connect.png)

### <a name="customize-certificate-files"></a>Personalización de archivos de certificado

Siga este procedimiento para personalizar los archivos de certificado que utiliza para las conexiones seguras con el Docker de Cloud Discovery.

1. Abra un cliente FTP y conéctese al recopilador de registros.

   ![Conexión al cliente FTP](./media/ftp-connect.png)

2. Navegue al directorio `ssl_update`.
3. Cargue los nuevos archivos de certificado en el directorio `ssl_update` (los nombres son obligatorios).

   ![Cambio de la contraseña FTP](./media/new-certs.png)

    - **Para FTP:** se requiere un solo archivo. El archivo tiene los datos de la clave y del certificado, en ese orden, y se denomina **pure-ftpd.pem**.
    - **Para Syslog:** se necesitan tres archivos: **ca.pem**, **server-key.pem y **server-cert.pem**. Si falta alguno de ellos, la actualización no se llevará a cabo.

4. En una ejecución de terminal: `docker exec -t <collector name> update_certs`. El comando generará una salida similar a la que se ve en la captura de pantalla que se muestra a continuación.

   ![Cambio de la contraseña FTP](./media/update-certs.png)

## <a name="next-steps"></a>Pasos siguientes

[Implementar Cloud Discovery](set-up-cloud-discovery.md)

[Los clientes Premier también pueden elegir Cloud App Security directamente desde el Portal Premier](https://premier.microsoft.com/)
