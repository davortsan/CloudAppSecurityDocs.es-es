---
title: "Solución de problemas de implementación de Docker para Cloud Discovery | Microsoft Docs"
description: "En este tema se describe el proceso para modificar la configuración de Docker de Cloud Discovery para Cloud App Security."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 29/11/2017
ms.topic: get-started-article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: 776e834f-3c20-4d5f-9fab-4c5b975edb06
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: e40eae71a84f3e2cc0ca2814c4a8f16b25a6b380
ms.sourcegitcommit: f4ec7f2cb81c9d83bb7f406ddcca91ab07790a98
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/28/2017
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
[Para obtener soporte técnico, visite la página de soporte técnico asistido de Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)  
[Los clientes Premier también pueden elegir Cloud App Security directamente desde el Portal Premier](https://premier.microsoft.com/)
