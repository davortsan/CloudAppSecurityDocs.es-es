---
title: 'Habilitar el recopilador de registros detrás de un proxy: Cloud App Security | Microsoft Docs'
description: En este artículo se proporciona información sobre cómo habilitar el recopilador de registros de Cloud Discovery de Cloud App Security desde detrás de un proxy.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 8/6/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 2b6d888c90a3e21ee98002372c16484f6a471610
ms.sourcegitcommit: d340917143d37ded0dd342a277a1b6ad267f9a7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/26/2020
ms.locfileid: "77618451"
---
# <a name="enable-the-log-collector-behind-a-proxy"></a>Habilitación del recopilador de registros detrás de un proxy

Después de configurar el compilador de registros, si se ejecuta detrás de un proxy, el recopilador de registros podría tener problemas para enviar datos a Cloud App Security. Esto puede ocurrir porque el recopilador de registros no confía en la entidad de certificación raíz del proxy y no puede conectarse a Microsoft Cloud App Security para recuperar su configuración o cargar los registros recibidos.

>[!NOTE]
> Para obtener información sobre cómo cambiar los certificados utilizados por el compilador de registros para syslog o FTP, y para resolver problemas de conectividad de los firewalls y servidores proxy en el compilador de registros, consulte registro de la [configuración de FTP del recopilador de registros](log-collector-ftp.md).
>

## <a name="set-up-the-log-collector-behind-a-proxy"></a>Configurar el recopilador de registros detrás de un proxy

Asegúrese de que ha realizado los pasos necesarios. para ello, ejecute Docker en un equipo Windows o Linux y descargue correctamente la Cloud App Security imagen de Docker en la máquina. Para obtener más información, consulte [configurar la carga de registros automática para informes continuos](discovery-docker.md).

### <a name="validate-docker-log-collector-container-creation"></a>Validar la creación de contenedores del recopilador de registros de Docker

En el Shell, compruebe que el contenedor se ha creado y se está ejecutando con el siguiente comando:

```bash
docker ps
```

![Docker PS](media/docker-1.png)

### <a name="copy-proxy-root-ca-certificate-to-the-container"></a>Copiar el certificado de CA raíz del proxy en el contenedor

Desde la máquina virtual, copie el certificado de CA en el contenedor de Cloud App Security. En el ejemplo siguiente, el contenedor se denomina *Ubuntu-LogCollector* y el certificado de CA se denomina *proxy-CA. CRT*.
Ejecute el comando en el host de Ubuntu. Copia el certificado en una carpeta en el contenedor en ejecución:

```bash
docker cp Proxy-CA.crt Ubuntu-LogCollector:/var/adallom/ftp/discovery
```

### <a name="set-the-configuration-to-work-with-the-ca-certificate"></a>Establecer la configuración para que funcione con el certificado de CA

1. Vaya al contenedor con el siguiente comando. Se abrirá bash en el contenedor del recopilador de registros:

    ```bash
    docker exec -it Ubuntu-LogCollector /bin/bash
    ```

2. Desde Bash dentro del contenedor, vaya a la carpeta Java *JRE* . Para evitar un error de ruta de acceso relacionada con la versión, use este comando:

    ```bash
    cd "$(find /opt/jdk/*/jre -name "bin" -printf '%h' -quit)"
    ```

3. Importe el certificado raíz que copió anteriormente, desde la carpeta de *detección* al almacén de claves de Java y defina una contraseña. La contraseña predeterminada es "changeit". Para obtener información sobre cómo cambiar la contraseña, consulte [cambio de la contraseña del almacén de claves de Java](#how-to-change-the-java-keystore-password).

    ```bash
    ./keytool --import --noprompt --trustcacerts --alias SelfSignedCert --file /var/adallom/ftp/discovery/Proxy-CA.crt --keystore ../lib/security/cacerts --storepass <password>
    ```

4. Compruebe que el certificado se ha importado correctamente en el almacén de claves de CA mediante el siguiente comando para buscar el alias que proporcionó durante la importación (*SelfSignedCert*):

    ```bash
    ./keytool --list --keystore ../lib/security/cacerts | grep self
    ```

    ![keytool](media/docker-2.png "keytool")

Debería ver el certificado de la entidad de certificación del proxy importado.

### <a name="set-the-log-collector-to-run-with-the-new-configuration"></a>Establecimiento del recopilador de registros para que se ejecute con la nueva configuración

El contenedor ya está listo.

Ejecute el comando **collector_config** mediante el token de API que usó durante la creación del recopilador de registros:

![Token de API](media/docker-3.png "Token de API")

Al ejecutar el comando, especifique su propio token de API:

```bash
collector_config abcd1234abcd1234abcd1234abcd1234 ${CONSOLE} ${COLLECTOR}
```

![Actualización de la configuración](media/docker-4.png "Actualización de la configuración")

Ahora, el recopilador de registros puede comunicarse con Cloud App Security. Después de enviar datos a él, el estado cambiará de **correcto** a **conectado** en el portal de Cloud App Security.

![Estado](media/docker-5.png "Estado")

>[!NOTE]
> Si tiene que actualizar la configuración del recopilador de registros, para agregar o quitar un origen de datos, por ejemplo, tiene que **eliminar** el contenedor y volver a realizar los pasos anteriores. Para evitar esto, puede volver a ejecutar la herramienta de *collector_config* con el nuevo token de API generado en el portal de Cloud App Security.

## <a name="how-to-change-the-java-keystore-password"></a>Cómo cambiar la contraseña del almacén de claves de Java

1. Detenga el servidor Java KeyStore.
1. Abra un shell de Bash dentro del contenedor y vaya a la carpeta *AppData/conf* .
1. Cambie la contraseña del almacén de claves del servidor mediante este comando:

    ```bash
    keytool -storepasswd -new newStorePassword -keystore server.keystore
    -storepass changeit
    ```

    > [!NOTE]
    > La contraseña predeterminada del servidor es *changeit*.

1. Cambie la contraseña del certificado con este comando:

    ```bash
    keytool -keypasswd -alias server -keypass changeit -new newKeyPassword -keystore server.keystore -storepass newStorePassword
    ```

    > [!NOTE]
    > El alias de servidor predeterminado es *Server*.

1. En un editor de texto, abra el archivo *Server-install\conf\server\secured-installed.Properties* y, a continuación, agregue las siguientes líneas de código y, a continuación, guarde los cambios:
    1. Especifique la nueva contraseña del almacén de claves de Java para el servidor: `server.keystore.password=newStorePassword`
    1. Especifique la nueva contraseña de certificado para el servidor: `server.key.password=newKeyPassword`
1. Inicie el servidor.

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Directivas de actividad de usuario](user-activity-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]
