---
title: Habilitación del recopilador de registros tras un proxy en Cloud App Security | Microsoft Docs
description: En este artículo se proporciona información sobre cómo habilitar el recopilador de registros de Cloud Discovery en Cloud App Security Discovery desde detrás de un servidor proxy.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 9/1/2019
ms.topic: conceptual
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 6bde2a6c-60cc-4a7d-9e83-e8b81ac229b0
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 894f3051bf6a0b46c1c9ff51e9452931882e82ff
ms.sourcegitcommit: 8ed1a81e3e27c4fd0e1e131a7c8527fbb264b9fe
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/07/2019
ms.locfileid: "54059994"
---
# <a name="enable-the-log-collector-behind-a-proxy"></a>Habilitación del recopilador de registros tras un proxy

Después de configurar el recopilador de registros, si está ejecutando detrás de un proxy, es posible que el recopilador de registros tenga problemas para enviar datos a Cloud App Security. Esto puede deberse a que el recopilador de registros no confía en la entidad emisora de certificados raíz del proxy y no puede conectarse a Microsoft Cloud App Security para recuperar su configuración o cargar los registros recibidos.

>[!NOTE] 
> Para más información sobre cómo cambiar los certificados utilizados por el recopilador de registros para Syslog o FTP, y para resolver problemas de conectividad desde los firewalls y los proxys al recopilador de registros, consulte [Solución de problemas de implementación de Cloud Discovery para Microsoft Cloud App Security](troubleshoot-docker.md).
>

## <a name="set-up-the-log-collector-behind-a-proxy"></a>Configuración del recopilador de registros tras un proxy

Asegúrese de que ha realizado los pasos necesarios para ejecutar Docker en una máquina Windows o Linux y de que ha descargado correctamente la imagen de Docker de Cloud App Security en la máquina. Para más información, consulte [Configuración de la carga de registros automática para informes continuos](discovery-docker.md).

### <a name="validate-docker-log-collector-container-creation"></a>Validación de la creación del contenedor del recopilador de registros de Docker

En el shell, compruebe que el contenedor se ha creado y se está ejecutando con el comando siguiente:

    bash
    docker ps


![docker ps](./media/docker-1.png "docker ps")

### <a name="copy-proxy-root-ca-certificate-to-the-container"></a>Copia del certificado de entidad de certificación raíz del proxy en el contenedor

Desde la máquina virtual, copie el certificado de entidad de certificación en el contenedor de Cloud App Security. En el ejemplo siguiente, el contenedor se denomina *Ubuntu LogCollector* y el certificado de entidad de certificación se denomina *Proxy-CA.crt*.
Ejecute el comando en el host Ubuntu y copie el certificado en una carpeta del contenedor en ejecución:

    bash
    docker cp Proxy-CA.crt Ubuntu-LogCollector:/var/adallom/ftp/discovery


### <a name="set-the-configuration-to-work-with-the-ca-certificate"></a>Establecimiento de la configuración para que funcione con el certificado de entidad de certificación

1. Vaya al contenedor mediante el comando siguiente. Bash se abrirá en el contenedor del recopilador de registros:

        bash
        docker exec -it Ubuntu-LogCollector /bin/bash

2. Desde el bash dentro del contenedor, vaya al directorio jre de Java. Para evitar un error de ruta de acceso relacionado con la versión, utilice este comando:

       bash
       cd 'find /opt/jdk/*/jre -iname bin'

3. Importe el certificado raíz, que copió anteriormente, desde la carpeta *discovery* en el almacén de claves de Java y defina una contraseña. La contraseña predeterminada es "changeit":

       bash
       ./keytool --import --noprompt --trustcacerts --alias SelfSignedCert --file /var/adallom/ftp/discovery/Proxy-CA.crt --keystore ../lib/security/cacerts --storepass changeit


4. Valide que el certificado se importó correctamente en el almacén de claves de la entidad de certificación, mediante el siguiente comando para buscar el alias que ha proporcionado durante la importación (*SelfSignedCert*):

       bash
       ./keytool --list --keystore ../lib/security/cacerts | grep self


![keytool](./media/docker-2.png "keytool")

Debería ver el certificado de entidad de certificación de proxy importado.

### <a name="set-the-log-collector-to-run-with-the-new-configuration"></a>Establecimiento del recopilador de registros para que se ejecute con la nueva configuración

El contenedor ya está listo. 

Ejecute el comando **collector_config** mediante el token de la API que utilizó durante la creación del recopilador de registros:

![Token de API](./media/docker-3.png "API token")

Al ejecutar el comando, especifique su propio token de API:

      bash
      collector_config abcd1234abcd1234abcd1234abcd1234 ${CONSOLE} ${COLLECTOR}


![Actualización de la configuración](./media/docker-4.png "Configuration update")

El recopilador de registros ahora puede comunicarse con Cloud App Security. Después de enviarle los datos, el estado cambiará de **Correcto**a **Conectado** en el portal de Cloud App Security.

![Estado](./media/docker-5.png "Status")

>[!NOTE]
> Si tiene que actualizar la configuración del recopilador de registros para, por ejemplo, agregar o eliminar un origen de datos, normalmente tiene que **eliminar** el contenedor y volver a realizar los pasos anteriores. Para evitar esto, puede volver a ejecutar la herramienta *collector_config* con el nuevo token de la API generado en el portal de Cloud App Security.



 
  
## <a name="next-steps"></a>Pasos siguientes 
[Directivas de actividad de usuario](user-activity-policies.md)   

[Los clientes Premier también pueden crear una solicitud de soporte técnico directamente en el portal Premier.](https://premier.microsoft.com/)  
  
  