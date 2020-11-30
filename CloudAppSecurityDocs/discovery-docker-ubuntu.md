---
title: Configuración de la carga de registros automática mediante Docker local
description: En este artículo se describe el proceso de configuración de la carga de registros automática para informes continuos en Cloud App Security mediante Docker en Linux en un servidor local.
ms.date: 06/02/2020
ms.topic: how-to
ms.openlocfilehash: 4a339361b232cee1ee85758f4545856d4674e847
ms.sourcegitcommit: d87372b47ca98e942c2bf94032a6a61902627d69
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/30/2020
ms.locfileid: "96311866"
---
# <a name="docker-on-linux-on-premises"></a>Docker en Linux local

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Puede configurar la carga de registros automática para informes continuos en Cloud App Security mediante un Docker en un servidor Ubuntu, Red Hat Enterprise Linux (RHEL) o de la instancia local.

## <a name="prerequisites"></a>Requisitos previos

* Sistema operativo:
  * Ubuntu 14,04, 16,04 y 18,04
  * RHEL 7,2 o superior
  * Versión 7,2 o superior

* Espacio en disco: 250 GB

* CPU: 2

* RAM: 4 GB

* Configuración del firewall, tal como se describe en [Requisitos de red](network-requirements.md#log-collector)

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
    ![Nombre del origen de datos](media/ubuntu1.png)
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

    ![Seleccionar orígenes de datos para conectarse](media/ubuntu2.png)

1. Aparecerá más información de implementación. **Copie** el comando de ejecución desde el cuadro de diálogo. Puede usar el icono Copiar al portapapeles. ![icono copiar al portapapeles](media/copy-icon.png)

1. **Exporte** la configuración de origen de datos esperada. Esta configuración describe cómo debe establecer la exportación de registro en los dispositivos.

    ![Crear un recopilador de registros](media/windows7.png)

    > [!NOTE]
    >
    > * Un único recopilador de registros puede administrar varios orígenes de datos.
    > * Copie el contenido de la pantalla, ya que necesitará la información al configurar el recopilador de registros para comunicarse con Cloud App Security. Si ha seleccionado Syslog, esta información incluirá información sobre el puerto en el que escucha el agente de escucha de Syslog.
    > * Para que los usuarios envíen datos de registro a través de FTP por primera vez, se recomienda cambiar la contraseña del usuario de FTP. Para obtener más información, consulte [cambiar la contraseña de FTP](log-collector-advanced-management.md#changing-the-ftp-password).

### <a name="step-2--on-premises-deployment-of-your-machine"></a>Paso 2: Implementación local de la máquina

En los pasos siguientes se describe la implementación de Ubuntu.

> [!NOTE]
> Los pasos de implementación para otras plataformas admitidas pueden ser ligeramente diferentes.

1. Abra un terminal en la máquina Ubuntu.

1. Cambie a los privilegios raíz con el comando: `sudo -i`

1. Para omitir a un servidor proxy en la red, ejecute los dos comandos siguientes:

    ```bash
    export http_proxy='<IP>:<PORT>' (e.g. 168.192.1.1:8888)
    export https_proxy='<IP>:<PORT>'
    ```

1. Si acepta los [términos de licencia del software](https://go.microsoft.com/fwlink/?linkid=862492), desinstale las versiones anteriores e instale Docker CE con el comando siguiente:

    ```bash
    curl -o /tmp/MCASInstallDocker.sh https://adaprodconsole.blob.core.windows.net/public-files/MCASInstallDocker.sh && chmod +x /tmp/MCASInstallDocker.sh; /tmp/MCASInstallDocker.sh
    ```

    > [!NOTE]
    > Si se produce un error en este comando al validar el certificado de servidor proxy, ejecute el comando con `curl -k` al principio.

    ![Comando para instalar Docker](media/ubuntu5.png)

1. Implemente la imagen del recopilador en la máquina host al importar la configuración del recopilador. Para importar la configuración, copie el comando de ejecución generado en el portal. Si necesita configurar un proxy, agregue la dirección IP del proxy y el número de puerto. Por ejemplo, si los detalles de proxy son 192.168.10.1:8080, el comando de ejecución actualizado es:

    ```bash
    (echo 6f19225ea69cf5f178139551986d3d797c92a5a43bef46469fcc997aec2ccc6f) | docker run --name MyLogCollector -p 21:21 -p 20000-20099:20000-20099 -e "PUBLICIP='192.2.2.2'" -e "PROXY=192.168.10.1:8080" -e "CONSOLE=tenant2.eu1-rs.adallom.com" -e "COLLECTOR=MyLogCollector" --security-opt apparmor:unconfined --cap-add=SYS_ADMIN --restart unless-stopped -a stdin -i mcr.microsoft.com/mcas/logcollector starter
    ```

    ![Crear un recopilador de registros](media/windows7.png)

1. Ejecute el comando siguiente para comprobar si el recopilador se ejecuta correctamente: `docker logs <collector_name>`

Debería ver el mensaje: **finalizó correctamente.** 
 ![ Comando para comprobar que Docker se está ejecutando correctamente](media/ubuntu8.png)

### <a name="step-3---on-premises-configuration-of-your-network-appliances"></a>Paso 3: Configuración local de los dispositivos de red

Configure los firewalls y los servidores proxy de red para que exporten periódicamente los registros al puerto syslog dedicado o al directorio FTP según las instrucciones del cuadro de diálogo. Por ejemplo:

```bash
BlueCoat_HQ - Destination path: \<<machine_name>>\BlueCoat_HQ\
```

### <a name="step-4---verify-the-successful-deployment-in-the-cloud-app-security-portal"></a>Paso 4: Comprobación de la implementación correcta en el portal Cloud App Security

Compruebe el estado del recopilador en la tabla **Recopilador de registros** y asegúrese de que el estado es **Conectado**. Si es **Creado**, es posible que la conexión y el análisis del recopilador de registros no se hayan completado.

![Comprobar la implementación correcta del recopilador de registros](media/ubuntu9.png)

También puede ir al **registro de gobernanza** y comprobar que los registros se están cargando periódicamente en el portal.

Si tiene problemas durante la implementación, consulte [Solución de problemas de Cloud Discovery](troubleshooting-cloud-discovery.md).

### <a name="optional---create-custom-continuous-reports"></a>Opcional: crear informes continuos personalizados

Compruebe que se cargan los registros de Cloud App Security y que se generan los informes. Después de la comprobación, cree informes personalizados. Puede crear informes de detección personalizados en función de los grupos de usuarios de Azure Active Directory. Por ejemplo, si quiere ver el uso de la nube por parte del departamento de marketing, importe el grupo de marketing mediante la característica para importar grupos de usuarios. Después, cree un informe personalizado para este grupo. También puede personalizar un informe en función de la etiqueta de dirección IP o los intervalos de direcciones IP.

1. En el portal de Cloud App Security, en el engranaje de configuración, seleccione Configuración de Cloud Discovery y después **Informes continuos**.
1. Haga clic en el botón **Crear informe** y rellene los campos.
1. En **Filtros**, puede filtrar los datos por origen de datos, por [grupo de usuarios importados](user-groups.md) o por [etiquetas e intervalos de direcciones IP](ip-tags.md).

![Informe continuo personalizado](media/custom-continuous-report.png)

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Modificación de la configuración de FTP del recopilador de registros](log-collector-advanced-management.md)

[!INCLUDE [Open support ticket](includes/support.md)]
