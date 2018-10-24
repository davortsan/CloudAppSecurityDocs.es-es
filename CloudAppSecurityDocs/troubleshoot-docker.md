---
title: Solución de problemas de implementación de Docker para Cloud Discovery | Microsoft Docs
description: En este tema se describe el proceso para modificar la configuración de Docker de Cloud Discovery para Cloud App Security.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 10/07/2018
ms.topic: conceptual
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 776e834f-3c20-4d5f-9fab-4c5b975edb06
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: f53eca16b08b72798e2b3b0ababcad7ae676765d
ms.sourcegitcommit: 53a1c990ff06674c26563a9ebcb1979818c3c063
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/09/2018
ms.locfileid: "48881778"
---
*Se aplica a: Microsoft Cloud App Security*

# <a name="troubleshooting-the-microsoft-cloud-app-security-cloud-discovery-deployment"></a>Solución de problemas de implementación de Cloud Discovery para Microsoft Cloud App Security

## <a name="windows-defender-atp-integration"></a>Integración con ATP de Windows Defender
Si integra ATP de Windows Defender con Cloud App Security y no ve los resultados de la integración (no hay ningún informe de **usuarios del punto de conexión de Win10**), asegúrese de que las máquinas que está conectando son de Windows 10 versión 1809 o posterior y de esperar las dos horas necesarias que tardan los datos en estar accesibles.

## <a name="docker-deployment"></a>Implementación de Docker

### <a name="changing-the-ftp-password"></a>Cambio de la contraseña FTP


1. Conéctese al host del recopilador de registros.

2.  Ejecute `docker exec -it <collector name> pure-pw passwd <ftp user>`

    1. Escriba la nueva contraseña.
    2. Vuelva a escribir la nueva contraseña para confirmarla.
 
3.  Ejecute `docker exec -it <collector name> pure-pw mkdb` para aplicar el cambio.


  ![cambio de la contraseña ftp](./media/ftp-connect.png)

### <a name="customize-certificate-files"></a>Personalización de archivos de certificado

Siga este procedimiento para personalizar los archivos de certificado que utiliza para las conexiones seguras con el Docker de Cloud Discovery.

1. Abra un cliente FTP y conéctese al recopilador de registros.

   ![Conexión al cliente FTP](./media/ftp-connect.png)

2. Navegue al directorio `ssl_update`.
3. Cargue los nuevos archivos de certificado en el directorio `ssl_update` (los nombres son obligatorios).

   ![Cambio de la contraseña FTP](./media/new-certs.png)

   1.  Para FTP: solo se requiere un archivo que contenga los datos de clave y certificado, en ese orden, denominado **puro ftpd.pem**.
    
   2.  Para Syslog: se necesitan tres archivos: **ca.pem**, **server key.pem** y **server-cert.pem**. Si falta alguno de los archivos, la actualización no se llevará a cabo.

4. En una ejecución de terminal: `docker exec -t <collector name> update_certs`. Esto debería producir una salida similar a la que se ve en la pantalla siguiente.

   ![Cambio de la contraseña FTP](./media/update-certs.png)

## <a name="see-also"></a>Consulte también
[Implementar Cloud Discovery](set-up-cloud-discovery.md)

[Los clientes Premier también pueden elegir Cloud App Security directamente desde el Portal Premier](https://premier.microsoft.com/)

