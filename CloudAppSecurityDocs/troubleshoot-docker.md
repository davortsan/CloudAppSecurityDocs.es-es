---
title: "Solución de problemas de implementación de Docker para Cloud Discovery | Microsoft Docs"
description: "En este tema se describe el proceso para modificar la configuración de Docker de Cloud Discovery para Cloud App Security."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 1/15/2018
ms.topic: get-started-article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: 776e834f-3c20-4d5f-9fab-4c5b975edb06
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: b994661f0f875db100a0aa2eb293b88e637b89cb
ms.sourcegitcommit: 458e936e1ac548eda37e9bf955b439199bbdd018
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/16/2018
---
# <a name="troubleshooting-the-cloud-app-security-cloud-discovery-docker"></a>Solución de problemas de Docker de Cloud Discovery para Cloud App Security

## <a name="changing-the-ftp-password"></a>Cambio de la contraseña FTP


1. Conéctese al host del recopilador de registros.

2.  Ejecute `docker exec -it <collector name> pure-pw passwd <ftp user>`

    1. Escriba la nueva contraseña.
    2. Vuelva a escribir la nueva contraseña para confirmarla.
 
3.  Ejecute `docker exec -it <collector name> pure-pw mkdb` para aplicar el cambio.


  ![cambio de la contraseña ftp](./media/ftp-connect.png)

## <a name="customize-certificate-files"></a>Personalización de archivos de certificado

Siga este procedimiento para personalizar los archivos de certificado que utiliza para las conexiones seguras con el Docker de Cloud Discovery.

1.  Abra un cliente FTP y conéctese al recopilador de registros.

  ![Conexión al cliente FTP](./media/ftp-connect.png)

2.  Navegue al directorio `ssl_update`.
3.  Cargue los nuevos archivos de certificado en el directorio `ssl_update` (los nombres son obligatorios).

    ![Cambio de la contraseña FTP](./media/new-certs.png)

    1.  Para FTP: solo se requiere un archivo que contenga los datos de clave y certificado, en ese orden, denominado **puro ftpd.pem**.
    
    2.  Para Syslog: se necesitan tres archivos: **ca.pem**, **server key.pem** y **server-cert.pem**. Si falta alguno de los archivos, la actualización no se llevará a cabo.

4.  En una ejecución de terminal: `docker exec -t <collector name> update_certs`. Esto debería producir una salida similar a la que se ve en la pantalla siguiente.

    ![Cambio de la contraseña FTP](./media/update-certs.png)

## <a name="see-also"></a>Consulte también
[Implementar Cloud Discovery](set-up-cloud-discovery.md)

[Los clientes Premier también pueden elegir Cloud App Security directamente desde el Portal Premier](https://premier.microsoft.com/)

