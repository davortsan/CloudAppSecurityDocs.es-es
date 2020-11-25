---
title: Administración avanzada del recopilador de registros
description: En este artículo se proporciona información sobre cómo las tareas de administración avanzadas para Cloud App Security recopiladores de registros de Cloud Discovery.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 11/25/2020
ms.topic: how-to
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: b003f47c33ef2ed749df3138ed1b6cd2a83232d3
ms.sourcegitcommit: a0a8e25bda77fb21f280a0e504896be85b89ed6f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/25/2020
ms.locfileid: "96035022"
---
# <a name="advanced-log-collector-management"></a>Administración avanzada del recopilador de registros

[!INCLUDE [Banner for top of topics](includes/banner.md)]

En este artículo se proporciona información sobre las siguientes opciones de configuración avanzada para Cloud App Security recopiladores de registros de Cloud Discovery:

- [Modificación de la configuración de FTP del recopilador de registros](#modify-the-log-collector-ftp-configuration)
- [Habilitación del recopilador de registros tras un proxy](#enable-the-log-collector-behind-a-proxy)
- [Traslado del recopilador de registros a una partición de datos diferente en Linux](#move-the-log-collector-to-a-different-data-partition-on-linux)
- [Inspeccionar el uso de disco del recopilador de registros en Linux](#inspect-the-log-collector-disk-usage-on-linux)
- [Traslado del recopilador de registros a un host accesible](#move-the-log-collector-to-an-accessible-host)
- [Definición de puertos personalizados para los receptores de syslog y FTP para los recopiladores de registros en Linux](#define-custom-ports-for-syslog-and-ftp-receivers-for-log-collectors-on-linux)
- [Validar el tráfico y el formato de registro recibidos por el recopilador de registros en Linux](#validate-the-traffic-and-log-format-received-by-log-collector-on-linux)

## <a name="modify-the-log-collector-ftp-configuration"></a>Modificación de la configuración de FTP del recopilador de registros

Siga estos pasos para modificar la configuración de la Cloud App Security Cloud Discovery Docker.

### <a name="docker-deployment"></a>Implementación de Docker

Es posible que tenga que modificar la configuración de la Cloud App Security Cloud Discovery Docker.

#### <a name="changing-the-ftp-password"></a>Cambio de la contraseña FTP

1. Conéctese al host del recopilador de registros.

1. Ejecute `docker exec -it <collector name> pure-pw passwd <ftp user>`:

    1. Escriba la nueva contraseña.
    1. Vuelva a escribir la nueva contraseña para confirmarla.

1. Ejecute `docker exec -it <collector name> pure-pw mkdb` para aplicar el cambio.

    ![cambio de la contraseña ftp](media/log-collector-advanced-tasks/ftp-connect.png)

#### <a name="customize-certificate-files"></a>Personalización de archivos de certificado

Siga este procedimiento para personalizar los archivos de certificado que se usan para proteger las conexiones con el Cloud Discovery Docker.

1. Abra un cliente FTP y conéctese al recopilador de registros.

    ![Conexión al cliente FTP](media/log-collector-advanced-tasks/ftp-connect.png)

1. Vaya al directorio `ssl_update`.
1. Cargue los nuevos archivos de certificado en el directorio `ssl_update` (los nombres son obligatorios).

    ![Cargar archivos de certificado](media/log-collector-advanced-tasks/new-certs.png)

    - **Para FTP:** se requiere un solo archivo. El archivo tiene los datos de la clave y del certificado, en ese orden, y se denomina **pure-ftpd.pem**.
    - **Para syslog:** Se necesitan tres archivos: **CA. pem**, * * Server-Key. PEM y **Server-cert. pem**. Si falta alguno de ellos, la actualización no se llevará a cabo.

1. En una ventana de terminal, ejecute: `docker exec -t <collector name> update_certs` . El comando generará una salida similar a la que se ve en la captura de pantalla que se muestra a continuación.

    ![Actualizar archivos de certificado](media/log-collector-advanced-tasks/update-certs.png)

1. En una ventana de terminal, ejecute: `docker exec <collector name> chmod -R 700 /etc/ssl/private/` .

## <a name="enable-the-log-collector-behind-a-proxy"></a>Habilitación del recopilador de registros tras un proxy

Después de configurar el recopilador de registros, si está ejecutando detrás de un proxy, es posible que el recopilador de registros tenga problemas para enviar datos a Cloud App Security. Esto puede deberse a que el recopilador de registros no confía en la entidad emisora de certificados raíz del proxy y no puede conectarse a Microsoft Cloud App Security para recuperar su configuración o cargar los registros recibidos.

Siga estos pasos para habilitar el recopilador de registros detrás de un proxy.

>[!NOTE]
> Para obtener información sobre cómo cambiar los certificados utilizados por el recopilador de registros para syslog o FTP, y para resolver problemas de conectividad de los firewalls y servidores proxy en el compilador de registros, vea [modificar la configuración de FTP del recopilador de registros](#modify-the-log-collector-ftp-configuration).
>

### <a name="set-up-the-log-collector-behind-a-proxy"></a>Configuración del recopilador de registros tras un proxy

Asegúrese de que ha realizado los pasos necesarios para ejecutar Docker en una máquina Windows o Linux y de que ha descargado correctamente la imagen de Docker de Cloud App Security en la máquina. Para más información, consulte [Configuración de la carga de registros automática para informes continuos](discovery-docker.md).

#### <a name="validate-docker-log-collector-container-creation"></a>Validación de la creación del contenedor del recopilador de registros de Docker

En el shell, compruebe que el contenedor se ha creado y se está ejecutando con el comando siguiente:

```bash
docker ps
```

![docker ps](media/log-collector-advanced-tasks/docker-1.png)

#### <a name="copy-proxy-root-ca-certificate-to-the-container"></a>Copia del certificado de entidad de certificación raíz del proxy en el contenedor

Desde la máquina virtual, copie el certificado de entidad de certificación en el contenedor de Cloud App Security. En el ejemplo siguiente, el contenedor se denomina *Ubuntu LogCollector* y el certificado de entidad de certificación se denomina *Proxy-CA.crt*.
Ejecute el comando en el host de Ubuntu y copie el certificado en una carpeta del contenedor en ejecución:

```bash
docker cp Proxy-CA.crt Ubuntu-LogCollector:/var/adallom/ftp/discovery
```

#### <a name="set-the-configuration-to-work-with-the-ca-certificate"></a>Establecimiento de la configuración para que funcione con el certificado de entidad de certificación

1. Vaya al contenedor mediante el comando siguiente. Bash se abrirá en el contenedor del recopilador de registros:

    ```bash
    docker exec -it Ubuntu-LogCollector /bin/bash
    ```

1. En una ventana de Bash dentro del contenedor, vaya a la `jre` carpeta de Java. Para evitar un error de ruta de acceso relacionada con la versión, use este comando:

    ```bash
    cd "$(find /opt/jdk/*/jre -name "bin" -printf '%h' -quit)"
    cd bin
    ```

1. Importe el certificado raíz que copió anteriormente, desde la carpeta de *detección* al almacén de claves de Java y defina una contraseña. La contraseña predeterminada es "changeit". Para obtener información sobre cómo cambiar la contraseña, consulte [cambio de la contraseña del almacén de claves de Java](#how-to-change-the-java-keystore-password).

    ```bash
    ./keytool --import --noprompt --trustcacerts --alias SelfSignedCert --file /var/adallom/ftp/discovery/Proxy-CA.crt --keystore ../lib/security/cacerts --storepass <password>
    ```

1. Valide que el certificado se importó correctamente en el almacén de claves de la entidad de certificación, mediante el siguiente comando para buscar el alias que ha proporcionado durante la importación (*SelfSignedCert*):

    ```bash
    ./keytool --list --keystore ../lib/security/cacerts | grep self
    ```

    ![keytool](media/log-collector-advanced-tasks/docker-2.png "keytool")

Debería ver el certificado de entidad de certificación de proxy importado.

#### <a name="set-the-log-collector-to-run-with-the-new-configuration"></a>Establecimiento del recopilador de registros para que se ejecute con la nueva configuración

El contenedor ya está listo.

Ejecute el comando **collector_config** mediante el token de la API que utilizó durante la creación del recopilador de registros:

![Token de API](media/log-collector-advanced-tasks/docker-3.png "Token de API")

Al ejecutar el comando, especifique su propio token de API:

```bash
collector_config abcd1234abcd1234abcd1234abcd1234 ${CONSOLE} ${COLLECTOR}
```

![Actualización de la configuración](media/log-collector-advanced-tasks/docker-4.png "Actualización de la configuración")

El recopilador de registros ahora puede comunicarse con Cloud App Security. Después de enviarle los datos, el estado cambiará de **Correcto** a **Conectado** en el portal de Cloud App Security.

![Estado](media/log-collector-advanced-tasks/docker-5.png "Status")

>[!NOTE]
> Si tiene que actualizar la configuración del recopilador de registros para, por ejemplo, agregar o eliminar un origen de datos, normalmente tiene que **eliminar** el contenedor y volver a realizar los pasos anteriores. Para evitar esto, puede volver a ejecutar la herramienta *collector_config* con el nuevo token de la API generado en el portal de Cloud App Security.

### <a name="how-to-change-the-java-keystore-password"></a>Cómo cambiar la contraseña del almacén de claves de Java

1. Detenga el servidor Java KeyStore.

<!-- /opt/jdk/amazon-corretto-8.222.10.1-linux-x64/jre/lib/security -->

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

## <a name="move-the-log-collector-to-a-different-data-partition-on-linux"></a>Traslado del recopilador de registros a una partición de datos diferente en Linux

Muchas empresas tienen el requisito de trasladar los datos a una partición independiente. Siga estos pasos para trasladar las imágenes del recopilador de registros de Docker de Cloud App Security a una partición de datos en el host de Linux.

En los pasos siguientes se describe cómo mover datos a una partición denominada *almacén* de datos y se supone que ya se ha montado la partición.

> [!NOTE]
> La adición y configuración de una nueva partición en el host de Linux no está en el ámbito de esta guía.

![Lista de particiones de Linux](media/log-collector-advanced-tasks/move-lc-new-partition-linux-disk-list.png)

1. Detenga el servicio de Docker con este comando:

    ```bash
    service docker stop
    ```

1. Mueva los datos del recopilador de registros a la nueva partición mediante este comando:

    ```bash
    mv /var/lib/docker /datastore/docker
    ```

1. Quite el directorio de almacenamiento de Docker anterior (/var/lib/Docker) y cree un vínculo simbólico al nuevo directorio (/datastore/Docker).

    ```bash
    rm -rf /var/lib/docker && ln -s /datastore/docker /var/lib/
    ```

1. Inicie el servicio de Docker con este comando:

    ```bash
    service docker start
    ```

1. Opcionalmente, compruebe el estado del recopilador de registros mediante este comando:

    ```bash
    docker ps
    ```

## <a name="inspect-the-log-collector-disk-usage-on-linux"></a>Inspeccionar el uso de disco del recopilador de registros en Linux

Siga estos pasos para revisar el uso y la ubicación del disco del recopilador de registros.

1. Identifique la ruta de acceso al directorio donde se almacenan los datos del recopilador de registros mediante este comando:

    ```bash
    docker inspect <collector_name> | grep WorkDir
    ```

    ![Identificar el directorio del recopilador de registros](media/log-collector-advanced-tasks/inspect-lc-linux-disk-usage-directory.png)

1. Obtiene el tamaño en disco del recopilador de registros mediante la ruta de acceso identificada sin el sufijo "/Work":

    ```bash
    du -sh /var/lib/docker/overlay2/<log_collector_id>/
    ```

    ![Obtener tamaño del recopilador de registros en el disco](media/log-collector-advanced-tasks/inspect-lc-linux-disk-usage-size.png)

    > [!NOTE]
    > Si solo necesita conocer el tamaño en disco, puede usar este comando: `docker ps -s`

## <a name="move-the-log-collector-to-an-accessible-host"></a>Traslado del recopilador de registros a un host accesible

En entornos regulados, es posible que se bloquee el acceso a los concentradores de Docker donde se hospeda la imagen del recopilador de registros. Esto impide que Cloud App Security importen los datos del compilador de registros y que se puedan resolver mientras se mueve la imagen del recopilador de registros a un host accesible.

Siga estos pasos para descargar la imagen del recopilador de registros con un equipo que tenga acceso a Docker hub e impórtelo al host de destino.

> [!NOTE]
>
> - La imagen descargada se puede importar en el repositorio privado o directamente en el host. Los siguientes pasos le guían en el proceso de descarga de la imagen del recopilador de registros en el equipo Windows y, a continuación, usa WinSCP para trasladar el recopilador de registros al host de destino.
> - Para instalar Docker en el host, descargue el sistema operativo deseado:
>   - https://download.docker.com/linux/ubuntu
>   - https://download.docker.com/linux/centos/
>   - https://download.docker.com/linux/rhel/
>
> Después de la descarga, use la [Guía de instalación sin conexión](https://docs.docker.com/datacenter/dtr/2.0/install/install-dtr-offline/#download-the-offline-package) para instalar el sistema operativo.

Para iniciar el proceso, [exporte la imagen del recopilador de registros](#export-the-log-collector-image-from-your-docker-hub) e [importe la imagen al host de destino](#import-and-load-the-log-collector-image-to-your-destination-host).

### <a name="export-the-log-collector-image-from-your-docker-hub"></a>Exportación de la imagen del recopilador de registros desde Docker Hub

Siga los pasos pertinentes para el sistema operativo del centro de Docker en el que se encuentra la imagen del recopilador de registros.

#### <a name="exporting-the-image-on-linux"></a>Exportación de la imagen en Linux

1. En un equipo Linux que tenga acceso a Docker Hub, ejecute el siguiente comando. Se instalará Docker y se descargará la imagen del recopilador de registros.

    ```bash
    curl -o /tmp/MCASInstallDocker.sh https://adaprodconsole.blob.core.windows.net/public-files/MCASInstallDocker.sh && chmod +x /tmp/MCASInstallDocker.sh; /tmp/MCASInstallDocker.sh
    ```

1. Exporte la imagen del recopilador de registros.

    ```bash
    docker save --output /tmp/mcasLC.targ mcr.microsoft.com/mcas/logcollector
    chmod +r /tmp/mcasLC.tar
    ```

    > [!NOTE]
    > Es importante usar el parámetro de **salida** para escribir en un archivo, en lugar de *stdout*.

1. Descargue la imagen del recopilador de registros en el equipo Windows `C:\mcasLogCollector\` mediante winscp.

    ![Descargar el recopilador de registros en un equipo Windows](media/log-collector-advanced-tasks/move-lc-to-accessible-host-download-linux-winscp.png)

#### <a name="exporting-the-image-on-windows"></a>Exportar la imagen en Windows

1. En un equipo con Windows 10 que tenga acceso al centro de Docker, instale [Docker Desktop](https://docs.docker.com/docker-for-windows/install/).

1. Descargue la imagen del recopilador de registros.

    ```dos
    docker login -u caslogcollector -p C0llector3nthusiast
    docker pull mcr.microsoft/mcas/logcollector
    ```

1. Exporte la imagen del recopilador de registros.

    ```dos
    docker save --output C:\mcasLogCollector\mcasLC.targ mcr.microsoft.com/mcas/logcollector
    ```

    > [!NOTE]
    > Es importante usar el parámetro de **salida** para escribir en un archivo, en lugar de *stdout*.

### <a name="import-and-load-the-log-collector-image-to-your-destination-host"></a>Importar y cargar la imagen del recopilador de registros en el host de destino

Siga estos pasos para transferir la imagen exportada al host de destino.

1. Cargue la imagen del recopilador de registros en el host de destino en `/tmp/` .

    ![Cargar el recopilador de registros en el host de destino](media/log-collector-advanced-tasks/move-lc-to-accessible-host-upload-host-winscp.png)

1. En el host de destino, importe la imagen del recopilador de registros en el repositorio de imágenes de Docker mediante este comando:

    ```bash
    docker load --input /tmp/mcasLC.tar
    ```

    ![Importación de la imagen del recopilador de registros en el repositorio de Docker](media/log-collector-advanced-tasks/move-lc-to-accessible-host-import-docker-repo.png)

1. Opcionalmente, compruebe que la importación se completó correctamente con este comando:

    ```bash
    docker image ls
    ```

    ![Comprobar importación de imagen del recopilador de registros correcta](media/log-collector-advanced-tasks/move-lc-to-accessible-host-verify-docker-image.png)

    Ahora puede continuar con la [creación del recopilador de registros](discovery-docker.md) mediante la imagen del host de destino.

## <a name="define-custom-ports-for-syslog-and-ftp-receivers-for-log-collectors-on-linux"></a>Definición de puertos personalizados para los receptores de syslog y FTP para los recopiladores de registros en Linux

Algunas organizaciones tienen el requisito de definir puertos personalizados para los servicios syslog y FTP.
Al agregar un origen de datos, Cloud App Security recopiladores de registros utiliza números de Puerto específicos para escuchar los registros de tráfico de uno o más orígenes de datos.

En la tabla siguiente se enumeran los puertos de escucha predeterminados para los receptores:

| Tipo de receptor | Puertos |
| --- | --- |
| syslog | \* UDP/514: UDP/51x<br />\* TCP/601-TCP/60x |
| FTP | \* TCP/21 |

Siga estos pasos para definir puertos personalizados.

1. En Cloud App Security, haga clic en el icono de configuración seguido de **recopiladores de registros**.

1. En la pestaña **recopiladores de registros** , agregue o edite un compilador de registros y después de actualizar los orígenes de datos, copie el comando ejecutar en el cuadro de diálogo.

    ![Copiar comando de ejecución del asistente del recopilador de registros](media/log-collector-advanced-tasks/define-lc-custom-ports-copy-default-run-command.png)

    > [!NOTE]
    > Si se usa tal y como se proporciona, el siguiente comando proporcionado por el asistente configura el recopilador de registros para usar los puertos 514/UDP y 515/UDP.
    >
    > ```bash
    > (echo <credentials>) | docker run --name LogCollector1 -p 514:514/udp -p 515:515/udp -p 21:21 -p 20000-20099:20000-20099 -e "PUBLICIP='10.0.0.100'" -e "PROXY=" -e "SYSLOG=true" -e "CONSOLE=machine.us2.portal.cloudappsecurity.com" -e "COLLECTOR=LogCollector1" --security-opt apparmor:unconfined --cap-add=SYS_ADMIN --restart unless-stopped -a stdin -i mcr.microsoft.com/mcas/logcollector starter
    > ```
    >
    > ![Ejecutar comando desde el Asistente para recopiladores de registros](media/log-collector-advanced-tasks/define-lc-custom-ports-default-run-command.png)

1. Antes de usar el comando en el equipo host, modifique el comando para usar los puertos personalizados. Por ejemplo, para configurar el recopilador de registros de modo que use los puertos UDP 414 y 415, cambie el comando de la siguiente manera:

    ```bash
    (echo <credentials>) | docker run --name LogCollector1 -p 414:514/udp -p 415:515/udp -p 21:21 -p 20000-20099:20000-20099 -e "PUBLICIP='10.0.0.100'" -e "PROXY=" -e "SYSLOG=true" -e "CONSOLE=machine.us2.portal.cloudappsecurity.com" -e "COLLECTOR=LogCollector1" --security-opt apparmor:unconfined --cap-add=SYS_ADMIN --restart unless-stopped -a stdin -i mcr.microsoft.com/mcas/logcollector starter
    ```

    ![Ejecutar comando personalizado en el host](media/log-collector-advanced-tasks/define-lc-custom-ports-custom-run-command.png)

    > [!NOTE]
    > Solo se modifica la asignación de Docker. Los puertos asignados internamente no cambian, lo que le permite elegir cualquier puerto de escucha en el host.

## <a name="validate-the-traffic-and-log-format-received-by-log-collector-on-linux"></a>Validar el tráfico y el formato de registro recibidos por el recopilador de registros en Linux

En ocasiones, es posible que deba investigar problemas como los siguientes:

- Los **recopiladores de registros están recibiendo datos**: Compruebe que los recopiladores de registros reciben mensajes de syslog desde sus dispositivos y que no están bloqueados por firewalls.
- **Los datos recibidos están en el formato de registro correcto**: valide el formato del registro para ayudarle a solucionar los errores de análisis comparando el formato de registro que espera Cloud App Security y el que envió el dispositivo.

Siga estos pasos para validar el tráfico recibido por los recopiladores de registros.

1. Inicie sesión en el servidor que hospeda el contenedor de Docker.

1. Compruebe que el recopilador de registros está recibiendo mensajes de syslog mediante cualquiera de los métodos siguientes:

    - Mediante el uso de *tcpdump*, o un comando similar para analizar el tráfico de red en el puerto 514:

        ```bash
        tcpdump -Als0 port 514
        ```

        Si todo está configurado correctamente, debería ver el tráfico de red de sus dispositivos.

        ![Comando analizar tráfico de red tcpdump](media/log-collector-advanced-tasks/validate-traffic-and-log-format-tcpdump-analyze-traffic.png)

    - Mediante el uso de *netcat*, o un comando similar para analizar el tráfico de red en el equipo host:

        1. Instale *netcat* y *wget*.

        1. Descargue y, si es necesario, descomprima un registro de ejemplo, como se indica a continuación:
            1. En el portal de Cloud App Security, haga clic en **detectar** y, a continuación, haga clic en **crear informe de instantáneas**.
            1. Seleccione el **origen de datos** desde el que desea cargar los archivos de registro.
            1. Haga clic en **ver y compruebe** , a continuación, haga clic con el botón derecho en **Descargar registro de ejemplo** y copie el vínculo dirección URL.
            1. Haga clic en **Cerrar**.
            1. Haga clic en **Cancelar**.

        ```bash
        wget <URL_address_to_sample_log>
        ```

        1. Ejecute `netcat` para transmitir los datos al recopilador de registros.

        ```bash
        cat <path_to_downloaded_sample_log>.log | nc -w 0 localhost <datasource_port>
        ```

        Si el recopilador está configurado correctamente, los datos de registro estarán presentes en el archivo de mensajes y poco después, se cargarán en el portal de Cloud App Security.

    - Mediante la inspección de archivos relevantes en el contenedor de Docker Cloud App Security:
        1. Inicie sesión en el contenedor con este comando:

        ```bash
        docker exec -it <Container Name> bash
        ```

        1. Determine si los mensajes de syslog se escriben en el archivo de mensajes mediante este comando:

        ```bash
        cat /var/adallom/syslog/<your_log_collector_port>/messages
        ```

        Si todo está configurado correctamente, debería ver el tráfico de red de sus dispositivos.

        > [!NOTE]
        > Este archivo se seguirá escribiendo en hasta que alcance los 40 KB de tamaño.

        ![Comando analizar tráfico de red CAT](media/log-collector-advanced-tasks/validate-traffic-and-log-format-cat-analyze-traffic.png)

1. Revise los registros que se han cargado en Cloud App Security en el `/var/adallom/discoverylogsbackup` directorio.

    ![Revisar los archivos de registro cargados](media/log-collector-advanced-tasks/validate-traffic-and-log-format-review-uploaded-logs.png)

1. Valide el formato de registro recibido por el recopilador de registros mediante la comparación de los mensajes almacenados en `/var/adallom/discoverylogsbackup` con el formato de registro de ejemplo proporcionado en el Cloud App Security Asistente para **crear recopiladores de registros** .

> [!NOTE]
> Si desea usar su propio registro de ejemplo pero no tiene acceso al dispositivo, use los siguientes comandos para escribir la salida del archivo de *mensajes* (que se encuentra en el directorio syslog del recopilador de OG) en un archivo local en el host.
>
> ```bash
> docker exec CustomerLogCollectorName tail -f -q /var/adallom/syslog/<datasource_port>/messages > /tmp/log.log
> ```
>
> Compare el archivo de salida ( `/tmp/log.log` ) con los mensajes almacenados en `/var/adallom/discoverylogsbackup` .

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Implementación de Cloud Discovery](set-up-cloud-discovery.md)

> [!div class="nextstepaction"]
> [Directivas de actividad de usuario](user-activity-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]
