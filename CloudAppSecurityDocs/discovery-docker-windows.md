---
title: Implementación de informes continuos para Cloud App Security con Docker en Windows
description: En este artículo se describe el proceso de configuración de la carga de registros automática para los informes continuos de Cloud App Security con Docker. Se utiliza un servidor local de Windows.
ms.date: 12/02/2020
ms.topic: how-to
ms.openlocfilehash: 7164cdb91664e131915c489d00085c164321afbb
ms.sourcegitcommit: c2c9bd46229ebe9e22bb03d43487d4c544f5e5f4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/02/2020
ms.locfileid: "96509968"
---
# <a name="docker-on-windows-on-premises"></a>Docker en Windows local

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Puede configurar la carga de registros automática para los informes continuos de Cloud App Security con Docker y en Windows.

## <a name="prerequisites"></a>Requisitos previos

* Sistema operativo:
  * **Windows 10** (Fall Creators Update)
  * Windows Server **versión 1709 +** (SAC)
  * **Windows Server 2019 (LTSC)**

* Espacio en disco: 250 GB

* CPU: 2

* RAM: 4 GB

* Configuración del firewall, tal como se describe en [Requisitos de red](network-requirements.md#log-collector)

* La virtualización en el sistema operativo debe estar habilitada con Hyper-V.

> [!IMPORTANT]
>
> * Un usuario debe haber iniciado sesión en Docker para recopilar registros. Se recomienda avisar a los usuarios de Docker para que se desconecten sin cerrar sesión.
> * Docker para Windows no se admite oficialmente en escenarios de virtualización de VMWare.
> * Docker para Windows no se admite oficialmente en escenarios de virtualización anidada. Si todavía tiene previsto usar la virtualización anidada, consulte [la guía oficial de Docker](https://docs.docker.com/docker-for-windows/troubleshoot/#running-docker-desktop-in-nested-virtualization-scenarios).

> [!NOTE]
> Si tiene un recopilador de registros existente y desea quitarlo antes de implementarlo de nuevo, o si simplemente desea quitarlo, ejecute los siguientes comandos:
>
> ```console
> docker stop <collector_name>
> docker rm <collector_name>
> ```

## <a name="log-collector-performance"></a>Rendimiento del recopilador de registros

El recopilador de registros puede manejar correctamente una capacidad de registros de hasta 50 GB por hora. Los principales cuellos de botella del proceso de recopilación de registros son:

* Ancho de banda de red: el ancho de banda de red determina la velocidad de carga de registros.

* Rendimiento de e/s de la máquina virtual: determina la velocidad a la que se escriben los registros en el disco del recopilador de registros. El recopilador de registros tiene un mecanismo de seguridad integrado que supervisa la velocidad a la que llegan los registros y la compara con la velocidad de carga. En caso de congestión, el recopilador de registros comienza a quitar archivos de registro. Si la configuración normalmente supera los 50 GB por hora, se recomienda dividir el tráfico entre varios recopiladores de registros.

## <a name="set-up-and-configuration"></a>Establecimiento y configuración

### <a name="step-1--web-portal-configuration-define-data-sources-and-link-them-to-a-log-collector"></a>Paso 1: Configuración del portal web: definición de orígenes de datos y vinculación a un recopilador de registros

1. Vaya a la página de configuración **Carga de registros automática**.

    1. En el portal de Cloud App Security, haga clic en el icono de configuración y en **Recopiladores de registros**.

    ![icono de configuración](media/settings-icon.png)

1. Cree un origen de datos coincidente para cada firewall o servidor proxy desde el que quiera cargar registros.

    1. Haga clic en **Agregar origen de datos**.  
    ![Agregar un origen de datos](media/add-data-source.png)
    1. **Ponga nombre** al servidor proxy o firewall.  
    ![Agregar nombre para el origen de datos](media/ubuntu1.png)
    1. Seleccione el dispositivo en la lista **Origen**. Si selecciona **Formato de los registros personalizados** para trabajar con un dispositivo de red que no aparezca en la lista, consulte el artículo sobre cómo [trabajar con el analizador de registros personalizados](custom-log-parser.md) para ver las instrucciones de configuración.
    1. Compare el registro con el ejemplo del formato de registro esperado. Si el formato de archivo del registro no coincide con este ejemplo, debe agregar el origen de datos como **Otro**.
    1. Establezca el **tipo de receptor** en **FTP**, **FTPS**, **Syslog – UDP**, **Syslog – TCP** o **Syslog – TLS**.

    > [!NOTE]
    > La integración con protocolos de transferencia segura (FTPS y Syslog – TLS) a menudo requiere una configuración adicional o firewall/proxy.

    f. Repita este proceso para cada servidor proxy y firewall cuyos registros se puedan usar para detectar tráfico en la red. Se recomienda configurar un origen de datos dedicado por dispositivo de red para poder hacer lo siguiente:

    * Supervisar el estado de cada dispositivo por separado para fines de investigación.
    * Explorar Shadow IT Discovery de cada dispositivo, si cada uno de ellos lo usa un segmento de usuarios distinto.

1. Vaya a la pestaña **Recopiladores de registros** de la parte superior.

    1. Haga clic en **Agregar recopilador de registros**.
    1. Ponga **nombre** al recopilador de registros.
    1. Escriba la **dirección IP de host** de la máquina que se va a usar para implementar Docker. La dirección IP del host puede reemplazarse con el nombre del equipo si un servidor DNS (o equivalente) resolverá el nombre de host.
    1. Seleccione todos los **orígenes de datos** que desea conectar al recopilador y haga clic en **Actualizar** para guardar la configuración.
    ![Seleccionar origen de datos para conectarse](media/ubuntu2.png)

1. Aparecerá más información de implementación. **Copie** el comando de ejecución desde el cuadro de diálogo. Puede usar el icono Copiar al portapapeles, ![ copiar al portapapeles ](media/copy-icon.png) . Lo necesitará más adelante.

1. **Exporte** la configuración de origen de datos esperada. Esta configuración describe cómo debe establecer la exportación de registro en los dispositivos.

    ![Crear un recopilador de registros](media/windows7.png)

    > [!NOTE]
    >
    > * Un único recopilador de registros puede administrar varios orígenes de datos.
    > * Copie el contenido de la pantalla, ya que necesitará la información al configurar el recopilador de registros para comunicarse con Cloud App Security. Si ha seleccionado Syslog, esta información incluirá información sobre el puerto en el que escucha el agente de escucha de Syslog.
    > * Para que los usuarios envíen datos de registro a través de FTP por primera vez, se recomienda cambiar la contraseña del usuario de FTP. Para obtener más información, consulte [cambiar la contraseña de FTP](log-collector-advanced-management.md#changing-the-ftp-password).

### <a name="step-2--on-premises-deployment-of-your-machine"></a>Paso 2: Implementación local de la máquina

En los pasos siguientes se describe la implementación en Windows. Los pasos de implementación en otras plataformas son ligeramente diferentes.

1. Abra un terminal de PowerShell como administrador en la máquina Windows.

1. Ejecute el siguiente comando para descargar el archivo de script de PowerShell del instalador de Docker de Windows: `Invoke-WebRequest https://adaprodconsole.blob.core.windows.net/public-files/LogCollectorInstaller.ps1 -OutFile (Join-Path $Env:Temp LogCollectorInstaller.ps1)`

    Para comprobar que el instalador está firmado por Microsoft, consulte [Validate Installer Signature](#validate-signature) .

1. Para habilitar la ejecución de scripts de PowerShell, ejecute `Set-ExecutionPolicy RemoteSigned`

1. Ejecutar: `& (Join-Path $Env:Temp LogCollectorInstaller.ps1)` se instala el cliente de Docker en la máquina. Durante la instalación del contenedor de recopilador de registros, la máquina se reiniciará dos veces y tendrá que volver a iniciar sesión. **Asegúrese de que el cliente de Docker está configurado para usar contenedores de Linux.**

1. Después de cada reinicio, abra un terminal de PowerShell como administrador en la máquina y vuelva a ejecutar: `& (Join-Path $Env:Temp LogCollectorInstaller.ps1)`

1. Antes de que finalice la instalación, tendrá que pegar el comando de ejecución que ha copiado anteriormente.

1. Implemente la imagen del recopilador en la máquina host al importar la configuración del recopilador. Para importar la configuración, copie el comando de ejecución generado en el portal. Si necesita configurar un proxy, agregue la dirección IP del proxy y el número de puerto. Por ejemplo, si los detalles de proxy son 192.168.10.1:8080, el comando de ejecución actualizado es:

    ```console
    (echo db3a7c73eb7e91a0db53566c50bab7ed3a755607d90bb348c875825a7d1b2fce) | docker run --name MyLogCollector -p 21:21 -p 20000-20099:20000-20099 -e "PUBLICIP='192.168.1.1'" -e "PROXY=192.168.10.1:8080" -e "CONSOLE=mod244533.us.portal.cloudappsecurity.com" -e "COLLECTOR=MyLogCollector" --security-opt apparmor:unconfined --cap-add=SYS_ADMIN --restart unless-stopped -a stdin -i mcr.microsoft.com/mcas/logcollector starter
    ```

    ![Crear un recopilador de registros](media/windows7.png)

1. Ejecute el comando siguiente para comprobar si el recopilador se ejecuta correctamente: `docker logs <collector_name>`

Debería ver el mensaje: **finalizó correctamente.**

![Comprobar que el recopilador se está ejecutando correctamente](media/ubuntu8.png)

### <a name="step-3---on-premises-configuration-of-your-network-appliances"></a>Paso 3: Configuración local de los dispositivos de red

Configure los firewalls y los servidores proxy de la red de modo que exporten periódicamente los registros al puerto Syslog dedicado del directorio FTP según las instrucciones del cuadro de diálogo. Por ejemplo:

```console
BlueCoat_HQ - Destination path: \<<machine_name>>\BlueCoat_HQ\
```

### <a name="step-4---verify-the-successful-deployment-in-the-cloud-app-security-portal"></a>Paso 4: Comprobación de la implementación correcta en el portal Cloud App Security

Compruebe el estado del recopilador en la tabla **Recopilador de registros** y asegúrese de que el estado es **Conectado**. Si es **Creado**, es posible que la conexión y el análisis del recopilador de registros no se hayan completado.

![Comprobar que el recopilador se ha implementado correctamente](media/ubuntu9.png)

También puede ir al **registro de gobernanza** y comprobar que los registros se están cargando periódicamente en el portal.

Como alternativa, puede comprobar el estado del recopilador de registros desde el contenedor de Docker mediante los siguientes comandos:

1. Inicie sesión en el contenedor con este comando: `docker exec -it <Container Name> bash`
1. Compruebe el estado del recopilador de registros con este comando: `collector_status -p`

Si tiene problemas durante la implementación, consulte [Solución de problemas de Cloud Discovery](troubleshooting-cloud-discovery.md).

### <a name="optional---create-custom-continuous-reports"></a>Opcional: crear informes continuos personalizados <a name="continuous-reports"></a>

Compruebe que se cargan los registros de Cloud App Security y que se generan los informes. Después de la comprobación, cree informes personalizados. Puede crear informes de detección personalizados en función de los grupos de usuarios de Azure Active Directory. Por ejemplo, si quiere ver el uso de la nube por parte del departamento de marketing, importe el grupo de marketing mediante la característica para importar grupos de usuarios. Después, cree un informe personalizado para este grupo. También puede personalizar un informe en función de la etiqueta de dirección IP o los intervalos de direcciones IP.

1. En el portal de Cloud App Security, en el engranaje de configuración, seleccione Configuración de Cloud Discovery y después **Informes continuos**.
1. Haga clic en el botón **Crear informe** y rellene los campos.
1. En **Filtros**, puede filtrar los datos por origen de datos, por [grupo de usuarios importados](user-groups.md) o por [etiquetas e intervalos de direcciones IP](ip-tags.md).

    ![Informe continuo personalizado](media/custom-continuous-report.png)

### <a name="optional---validate-installer-signature"></a>Opcional: validar la firma del programa de instalación <a name="validate-signature"></a>

Para asegurarse de que el programa de instalación de Docker está firmado por Microsoft:

1. Haga clic con el botón derecho en el archivo y seleccione **Propiedades**.
1. Haga clic en **Firmas digitales** y asegúrese de que indica **Esta firma digital es correcta**.
1. Asegúrese de que **Microsoft Corporation** aparece como la única entrada en **Nombre del firmante**.

    ![Firma digital válida](media/digital-signature-successful.png)

Si la firma digital no es válida, se indicará **La firma digital no es válida**:

![Firma digital no válida](media/digital-signature-unsuccessful.png)

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Modificación de la configuración de FTP del recopilador de registros](log-collector-advanced-management.md)

[!INCLUDE [Open support ticket](includes/support.md)]
