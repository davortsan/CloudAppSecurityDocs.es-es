---
title: Implementación de informes continuos para Cloud App Security con Docker en Windows | Microsoft Docs
description: En este artículo se describe el proceso de configuración de la carga de registros automática para informes continuos en Cloud App Security mediante Docker en Windows en un servidor local.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 11/19/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 9122a5c5cdde5f2a1ed02946970825b75155acc2
ms.sourcegitcommit: 4f3883a9e85d0aaf2802b10433b221c3f1838d88
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/13/2020
ms.locfileid: "79285589"
---
# <a name="docker-on-windows-on-premises"></a>Docker en Windows local

*Se aplica a: Microsoft Cloud App Security*

Puede configurar la carga de registros automática para informes continuos en Cloud App Security mediante Docker en Windows.

## <a name="prerequisites"></a>Requisitos previos

* SO: **Windows 10** (Fall Creators Update), Windows Server **versión 1709 +** (SAC) o **Windows Server 2019 (LTSC)**

* Espacio en disco: 250 GB

* CPU: 2

* RAM: 4 GB

* Establezca el Firewall como se describe en [requisitos de red](network-requirements.md#log-collector) .

* La virtualización en el sistema operativo debe estar habilitada con Hyper-V

> [!IMPORTANT]
> Un usuario debe haber iniciado sesión en Docker para recopilar registros. Se recomienda avisar a los usuarios de Docker para que se desconecten sin cerrar sesión.

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

1. Vaya a la página Configuración de **carga de registros automática** .

    1. En el portal de Cloud App Security, haga clic en el icono de configuración seguido de **recopiladores de registros**.

    ![icono de configuración](media/settings-icon.png)

1. Cree un origen de datos coincidente para cada firewall o servidor proxy desde el que desea cargar los registros.

    1. Haga clic en **Agregar origen de datos**.  
    ![agregar un origen de datos](media/add-data-source.png)
    1. **Ponga nombre** al servidor proxy o firewall.  
    ![ubuntu1](media/ubuntu1.png)
    1. Seleccione el dispositivo en la lista **Origen**. Si selecciona el **formato de registro personalizado** para trabajar con un dispositivo de red que no aparece en la lista, consulte [trabajar con el analizador de registros personalizado](custom-log-parser.md) para obtener instrucciones de configuración.
    1. Compare el registro con el ejemplo del formato de registro esperado. Si el formato del archivo de registro no coincide con este ejemplo, debe agregar el origen de datos como **otro**.
    1. Establezca el **Tipo de receptor** en **FTP**, **FTPS**, **Syslog: UDP**, o **Syslog: TCP** o **Syslog – TLS**.

    > [!NOTE]
    > La integración con los protocolos de transferencia segura (FTPS y Syslog – TLS) a menudo requiere una configuración adicional o el firewall o proxy.

    f. Repita este proceso para cada servidor proxy y firewall cuyos registros se puedan usar para detectar tráfico en la red. Se recomienda configurar un origen de datos dedicado por dispositivo de red para que pueda:

    * Supervise el estado de cada dispositivo por separado, con fines de investigación.
    * Explore Shadow IT Discovery por dispositivo, si cada dispositivo lo usa otro segmento de usuario.

1. Vaya a la pestaña **Recopiladores de registros** de la parte superior.

    1. Haga clic en **Agregar recopilador de registros**.
    1. Ponga **nombre** al recopilador de registros.
    1. Escriba la **dirección IP del host** de la máquina que usará para implementar Docker. La dirección IP del host se puede reemplazar por el nombre del equipo, si hay un servidor DNS (o equivalente) que resolverá el nombre de host.
    1. Seleccione todos los **orígenes de datos** que desea conectar al recopilador y haga clic en **Actualizar** para guardar la configuración.
    ![ubuntu2](media/ubuntu2.png)

1. Se mostrará más información sobre la implementación. **Copie** el comando de ejecución en el cuadro de diálogo. Puede usar el icono Copiar al portapapeles, ![icono Copiar al portapapeles](media/copy-icon.png). Lo necesitará más adelante.

1. **Exporte** la configuración del origen de datos esperado. Esta configuración describe cómo se debe establecer la exportación del registro en los dispositivos.

    ![Crear el recopilador de registros](media/windows7.png)

    > [!NOTE]
    >
    > * Un único recopilador de registros puede administrar varios orígenes de datos.
    > * Copie el contenido de la pantalla, ya que necesitará la información al configurar el recopilador de registros para comunicarse con Cloud App Security. Si ha seleccionado Syslog, esta información incluirá información sobre el puerto en el que escucha el agente de escucha de Syslog.
    > * Para que los usuarios envíen datos de registro a través de FTP por primera vez, se recomienda cambiar la contraseña del usuario de FTP. Para obtener más información, consulte [cambiar la contraseña de FTP](log-collector-ftp.md#changing-the-ftp-password).

### <a name="step-2--on-premises-deployment-of-your-machine"></a>Paso 2: implementación local de la máquina

En los pasos siguientes se describe la implementación en Windows. Los pasos de implementación para otras plataformas son ligeramente diferentes.

1. Abra un terminal de PowerShell como administrador en la máquina Windows.

1. Ejecute el siguiente comando para descargar el archivo de script de PowerShell del instalador de Docker de Windows: `Invoke-WebRequest https://adaprodconsole.blob.core.windows.net/public-files/LogCollectorInstaller.ps1 -OutFile (Join-Path $Env:Temp LogCollectorInstaller.ps1)`

    Para comprobar que el instalador está firmado por Microsoft, consulte [Validate Installer Signature](#validate-signature) .

1. Para habilitar la ejecución de scripts de PowerShell, ejecute `Set-ExecutionPolicy RemoteSigned`

1. Ejecutar: `& (Join-Path $Env:Temp LogCollectorInstaller.ps1)` instala el cliente de Docker en la máquina. Mientras el contenedor del recopilador de registros está instalado, el equipo se reiniciará dos veces y tendrá que volver a iniciar sesión. **Asegúrese de que el cliente de Docker está configurado para usar contenedores de Linux.**

1. Después de cada reinicio, abra un terminal de PowerShell como administrador en la máquina, vuelva a ejecutar: `& (Join-Path $Env:Temp LogCollectorInstaller.ps1)`

1. Antes de que se complete la instalación, tendrá que pegar el comando ejecutar que copió anteriormente.

1. Implemente la imagen del recopilador en el equipo host mediante la importación de la configuración del recopilador. Importe la configuración copiando el comando de ejecución generado en el portal. Si necesita configurar un proxy, agregue la dirección IP del proxy y el número de puerto. Por ejemplo, si los detalles del proxy son 192.168.10.1:8080, el comando de ejecución actualizado es:

    ```console
    (echo db3a7c73eb7e91a0db53566c50bab7ed3a755607d90bb348c875825a7d1b2fce) | docker run --name MyLogCollector -p 21:21 -p 20000-20099:20000-20099 -e "PUBLICIP='192.168.1.1'" -e "PROXY=192.168.10.1:8080" -e "CONSOLE=mod244533.us.portal.cloudappsecurity.com" -e "COLLECTOR=MyLogCollector" --security-opt apparmor:unconfined --cap-add=SYS_ADMIN --restart unless-stopped -a stdin -i microsoft/caslogcollector starter
    ```

    ![Crear el recopilador de registros](media/windows7.png)

1. Compruebe que el recopilador se está ejecutando correctamente con el siguiente comando: `docker logs <collector_name>`

Debería ver el mensaje: **Finalizado correctamente**.

![ubuntu8](media/ubuntu8.png)

### <a name="step-3---on-premises-configuration-of-your-network-appliances"></a>Paso 3: configuración local de los dispositivos de red

Configure los firewalls y los servidores proxy de red para que exporten periódicamente los registros al puerto syslog dedicado del directorio FTP según las instrucciones del cuadro de diálogo. Por ejemplo:

```console
BlueCoat_HQ - Destination path: \<<machine_name>>\BlueCoat_HQ\
```

### <a name="step-4---verify-the-successful-deployment-in-the-cloud-app-security-portal"></a>Paso 4: comprobación de la implementación correcta en el portal de Cloud App Security

Compruebe el estado del recopilador en la tabla **Recopilador de registros** y asegúrese de que el estado es **Conectado**. Si se **crea**, es posible que la conexión y el análisis del recopilador de registros no se hayan completado.

![ubuntu9](media/ubuntu9.png)

También puede ir al **registro de gobernanza** y comprobar que los registros se están cargando periódicamente en el portal.

Si tiene problemas durante la implementación, consulte [solución de problemas Cloud Discovery](troubleshooting-cloud-discovery.md).

### Opcional: crear informes continuos personalizados<a name="continuous-reports"></a>

Compruebe que los registros se están cargando en Cloud App Security y que se generan los informes. Después de la comprobación, cree informes personalizados. Puede crear informes de detección personalizados basados en Azure Active Directory grupos de usuarios. Por ejemplo, si desea ver el uso en la nube de su Departamento de marketing, importe el grupo de marketing mediante la característica importar grupo de usuarios. A continuación, cree un informe personalizado para este grupo. También puede personalizar un informe en función de la etiqueta de dirección IP o los intervalos de direcciones IP.

1. En el portal de Cloud App Security, en el engranaje de configuración, seleccione Configuración de Cloud Discovery y, a continuación, seleccione **informes continuos**.
1. Haga clic en el botón **Crear informe** y rellene los campos.
1. En **Filtros**, puede filtrar los datos por origen de datos, por [grupo de usuarios importados](user-groups.md) o por [etiquetas e intervalos de direcciones IP](ip-tags.md).

    ![Informe continuo personalizado](media/custom-continuous-report.png)

### Opcional: validar la firma del instalador<a name="validate-signature"></a>

Para asegurarse de que el instalador de Docker está firmado por Microsoft:

1. Haga clic con el botón derecho en el archivo y seleccione **propiedades**.
1. Haga clic en **firmas digitales** y asegúrese de que indica que **esta firma digital es correcta**.
1. Asegúrese de que **Microsoft Corporation** aparece como la única entrada en **nombre del firmante**.

    ![Firma digital válida](media/digital-signature-successful.png)

Si la firma digital no es válida, indicará que **esta firma digital no es válida**:

![Firma digital no válida](media/digital-signature-unsuccessful.png)

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Configuración de FTP del recopilador de registros](log-collector-ftp.md)

[!INCLUDE [Open support ticket](includes/support.md)]
