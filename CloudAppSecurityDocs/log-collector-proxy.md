---
title: 'Habilitación del recopilador de registros detrás de un proxy: Cloud App Security'
description: En este artículo se proporciona información sobre cómo habilitar el recopilador de registros de Cloud Discovery en Cloud App Security Discovery desde detrás de un servidor proxy.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 8/6/2019
ms.topic: how-to
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 665d7435399c37a1d9683f004b0996f9ea5d263f
ms.sourcegitcommit: 29a8e66c665f51d831516924ae4d9d8047b39276
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2020
ms.locfileid: "88781708"
---
# <a name="enable-the-log-collector-behind-a-proxy"></a>Habilitación del recopilador de registros tras un proxy

Después de configurar el recopilador de registros, si está ejecutando detrás de un proxy, es posible que el recopilador de registros tenga problemas para enviar datos a Cloud App Security. Esto puede deberse a que el recopilador de registros no confía en la entidad emisora de certificados raíz del proxy y no puede conectarse a Microsoft Cloud App Security para recuperar su configuración o cargar los registros recibidos.

>[!NOTE]
> Para obtener información sobre cómo cambiar los certificados utilizados por el compilador de registros para syslog o FTP, y para resolver problemas de conectividad de los firewalls y servidores proxy en el compilador de registros, consulte registro de la [configuración de FTP del recopilador de registros](log-collector-ftp.md).
>

## <a name="set-up-the-log-collector-behind-a-proxy"></a>Configuración del recopilador de registros tras un proxy

Asegúrese de que ha realizado los pasos necesarios para ejecutar Docker en una máquina Windows o Linux y de que ha descargado correctamente la imagen de Docker de Cloud App Security en la máquina. Para más información, consulte [Configuración de la carga de registros automática para informes continuos](discovery-docker.md).

### <a name="validate-docker-log-collector-container-creation"></a>Validación de la creación del contenedor del recopilador de registros de Docker

En el shell, compruebe que el contenedor se ha creado y se está ejecutando con el comando siguiente:

```bash
docker ps
```

![docker ps](media/docker-1.png)

### <a name="copy-proxy-root-ca-certificate-to-the-container"></a>Copia del certificado de entidad de certificación raíz del proxy en el contenedor

Desde la máquina virtual, copie el certificado de entidad de certificación en el contenedor de Cloud App Security. En el ejemplo siguiente, el contenedor se denomina *Ubuntu LogCollector* y el certificado de entidad de certificación se denomina *Proxy-CA.crt*.
Ejecute el comando en el host de Ubuntu y copie el certificado en una carpeta del contenedor en ejecución:

```bash
docker cp Proxy-CA.crt Ubuntu-LogCollector:/var/adallom/ftp/discovery
```

### <a name="set-the-configuration-to-work-with-the-ca-certificate"></a>Establecimiento de la configuración para que funcione con el certificado de entidad de certificación

1. Vaya al contenedor mediante el comando siguiente. Bash se abrirá en el contenedor del recopilador de registros:

    ```bash
    docker exec -it Ubuntu-LogCollector /bin/bash
    ```

2. Desde Bash dentro del contenedor, vaya a la carpeta Java *JRE* . Para evitar un error de ruta de acceso relacionado con la versión, utilice este comando:

    ```bash
    cd "$(find /opt/jdk/*/jre -name "bin" -printf '%h' -quit)"
    ```

3. Importe el certificado raíz que copió anteriormente, desde la carpeta de *detección* al almacén de claves de Java y defina una contraseña. La contraseña predeterminada es "changeit". Para obtener información sobre cómo cambiar la contraseña, consulte [cambio de la contraseña del almacén de claves de Java](#how-to-change-the-java-keystore-password).

    ```bash
    ./keytool --import --noprompt --trustcacerts --alias SelfSignedCert --file /var/adallom/ftp/discovery/Proxy-CA.crt --keystore ../lib/security/cacerts --storepass <password>
    ```

4. Valide que el certificado se importó correctamente en el almacén de claves de la entidad de certificación, mediante el siguiente comando para buscar el alias que ha proporcionado durante la importación (*SelfSignedCert*):

    ```bash
    ./keytool --list --keystore ../lib/security/cacerts | grep self
    ```

    ![keytool](media/docker-2.png "keytool")

Debería ver el certificado de entidad de certificación de proxy importado.

### <a name="set-the-log-collector-to-run-with-the-new-configuration"></a>Establecimiento del recopilador de registros para que se ejecute con la nueva configuración

El contenedor ya está listo.

Ejecute el comando **collector_config** mediante el token de la API que utilizó durante la creación del recopilador de registros:

![Token de API](media/docker-3.png "Token de API")

Al ejecutar el comando, especifique su propio token de API:

```bash
collector_config abcd1234abcd1234abcd1234abcd1234 ${CONSOLE} ${COLLECTOR}
```

![Actualización de la configuración](media/docker-4.png "Actualización de la configuración")

El recopilador de registros ahora puede comunicarse con Cloud App Security. Después de enviarle los datos, el estado cambiará de **Correcto**a **Conectado** en el portal de Cloud App Security.

![Estado](media/docker-5.png "Estado")

>[!NOTE]
> Si tiene que actualizar la configuración del recopilador de registros para, por ejemplo, agregar o eliminar un origen de datos, normalmente tiene que **eliminar** el contenedor y volver a realizar los pasos anteriores. Para evitar esto, puede volver a ejecutar la herramienta *collector_config* con el nuevo token de la API generado en el portal de Cloud App Security.

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
    1. Especifique la nueva contraseña del certificado para el servidor: `server.key.password=newKeyPassword`
1. Inicie el servidor.

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Directivas de actividad de usuario](user-activity-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]
