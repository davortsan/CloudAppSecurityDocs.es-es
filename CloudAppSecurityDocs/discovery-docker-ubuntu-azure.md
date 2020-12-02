---
title: Configuración de la carga de registros automática con Docker en Azure
description: En este artículo se describe el proceso de configuración de la carga de registros automática para informes continuos en Cloud App Security mediante Docker en Linux en Azure.
ms.date: 12/02/2020
ms.topic: how-to
ms.openlocfilehash: 6c4f7243758dce46e5469d503ec572a18a7a2afe
ms.sourcegitcommit: 53e485ed8460f1123b3b55277fa5991b427b5302
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/02/2020
ms.locfileid: "96512957"
---
# <a name="docker-on-linux-in-azure"></a>Docker en Linux en Azure

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Puede configurar la carga de registros automática para informes continuos en Cloud App Security mediante Docker en Ubuntu, Red Hat Enterprise Linux (RHEL) o en Azure.

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

El compilador de registros puede administrar correctamente la capacidad de registro de hasta 50 GB por hora y que se compone de hasta 10 orígenes de datos. Los principales cuellos de botella del proceso de recopilación de registros son:

* Ancho de banda de red: el ancho de banda de red determina la velocidad de carga de registros.

* Rendimiento de e/s de la máquina virtual: determina la velocidad a la que se escriben los registros en el disco del recopilador de registros. El recopilador de registros tiene un mecanismo de seguridad integrado que supervisa la velocidad a la que llegan los registros y la compara con la velocidad de carga. En caso de congestión, el recopilador de registros comienza a quitar archivos de registro. Si la configuración normalmente supera los 50 GB por hora, se recomienda dividir el tráfico entre varios recopiladores de registros.

> [!NOTE]
> Si necesita más de 10 orígenes de datos, se recomienda dividir los orígenes de datos entre varios recopiladores de registros.

## <a name="set-up-and-configuration"></a>Establecimiento y configuración  

### <a name="step-1--web-portal-configuration-define-data-sources-and-link-them-to-a-log-collector"></a>Paso 1: Configuración del portal web: definición de orígenes de datos y vinculación a un recopilador de registros

1. Vaya a la página de configuración **Carga de registros automática**.

    1. En el portal de Cloud App Security, haga clic en el icono de configuración y en **Recopiladores de registros**.

    ![icono de configuración](media/settings-icon.png)

1. Cree un origen de datos coincidente para cada firewall o servidor proxy desde el que quiera cargar registros.

    1. Haga clic en **Agregar origen de datos**.  
    ![Agregar un origen de datos](media/add-data-source.png)
    1. **Ponga nombre** al servidor proxy o firewall.  
      ![Nombre del proxy o firewall](media/ubuntu1.png)
    1. Seleccione el dispositivo en la lista **Origen**. Si selecciona **Formato de los registros personalizados** para trabajar con un dispositivo de red que no aparezca en la lista, consulte el artículo sobre cómo [trabajar con el analizador de registros personalizados](custom-log-parser.md) para ver las instrucciones de configuración.
    1. Compare el registro con el ejemplo del formato de registro esperado. Si el formato de archivo del registro no coincide con este ejemplo, debe agregar el origen de datos como **Otro**.
    1. Establezca el **tipo de receptor** en **FTP**, **FTPS**, **Syslog – UDP**, **Syslog – TCP** o **Syslog – TLS**.

    >[!NOTE]
    >La integración con protocolos de transferencia segura (FTPS y Syslog – TLS) a menudo requiere una configuración adicional o firewall/proxy.

    f. Repita este proceso para cada servidor proxy y firewall cuyos registros se puedan usar para detectar tráfico en la red. Se recomienda configurar un origen de datos dedicado por dispositivo de red para poder hacer lo siguiente:

    * Supervisar el estado de cada dispositivo por separado para fines de investigación.
    * Explorar Shadow IT Discovery de cada dispositivo, si cada uno de ellos lo usa un segmento de usuarios distinto.

1. Vaya a la pestaña **Recopiladores de registros** de la parte superior.

    1. Haga clic en **Agregar recopilador de registros**.
    1. Ponga **nombre** al recopilador de registros.
    1. Escriba la **dirección IP de host** de la máquina que se va a usar para implementar Docker. La dirección IP del host puede reemplazarse con el nombre del equipo si un servidor DNS (o equivalente) resolverá el nombre de host.
    1. Seleccione todos los **orígenes de datos** que desea conectar al recopilador y haga clic en **Actualizar** para guardar la configuración.  
    ![Seleccionar orígenes de datos](media/ubuntu2.png)

1. Aparecerá más información de implementación. **Copie** el comando de ejecución desde el cuadro de diálogo. Puede usar el icono Copiar al portapapeles. ![icono copiar al portapapeles](media/copy-icon.png)

1. **Exporte** la configuración de origen de datos esperada. Esta configuración describe cómo debe establecer la exportación de registro en los dispositivos.

    ![Crear un recopilador de registros](media/windows7.png)

    > [!NOTE]
    >
    > * Un único recopilador de registros puede administrar varios orígenes de datos.
    > * Copie el contenido de la pantalla, ya que necesitará la información al configurar el recopilador de registros para comunicarse con Cloud App Security. Si ha seleccionado Syslog, esta información incluirá información sobre el puerto en el que escucha el agente de escucha de Syslog.
    > * Para que los usuarios envíen datos de registro a través de FTP por primera vez, se recomienda cambiar la contraseña del usuario de FTP. Para obtener más información, consulte [cambiar la contraseña de FTP](log-collector-advanced-management.md#changing-the-ftp-password).

### <a name="step-2--deployment-of-your-machine-in-azure"></a>Paso 2: Implementación de la máquina en Azure

> [!NOTE]
> En los pasos siguientes se describe la implementación de Ubuntu. Los pasos de implementación en otras plataformas son ligeramente diferentes.

1. Cree una nueva máquina Ubuntu en el entorno Azure.
1. Cuando la máquina esté en funcionamiento, abra los puertos mediante:

    1. En la vista de la máquina, vaya a **Redes** y seleccione la interfaz adecuada haciendo doble clic en ella.
    1. Vaya a **Grupo de seguridad de red** y seleccione el grupo de seguridad de red pertinente.
    1. Vaya a **reglas de seguridad de entrada** y haga clic en **Agregar**, ![ agregar reglas de seguridad de entrada.](media/ubuntu-azure.png)
    1. Agregue las siguientes reglas (en modo **Avanzado**):

    |Nombre|Intervalos de puertos de destino|Protocolo|Source|Destination|
    |----|----|----|----|----|
    |caslogcollector_ftp|21|TCP|<Subred de la dirección IP del dispositivo>|Any|
    |caslogcollector_ftp_passive|20000-20099|TCP|<Subred de la dirección IP del dispositivo>|Any|
    |caslogcollector_syslogs_tcp|601-700|TCP|<Subred de la dirección IP del dispositivo>|Any|
    |caslogcollector_syslogs_udp|514-600|UDP|<Subred de la dirección IP del dispositivo>|Any|

    ![Reglas de Ubuntu en Azure](media/inbound-rule.png)

1. Vuelva a la máquina y haga clic en **Conectar** para abrir un terminal en ella.

1. Cambie a los privilegios raíz con `sudo -i`.

1. Si acepta los términos de la [licencia de software](https://go.microsoft.com/fwlink/?linkid=862492), desinstale las versiones anteriores e instale Docker CE ejecutando los comandos adecuados para su entorno:

#### <a name="centos"></a>[CentOS](#tab/centos)

1. Quite las versiones anteriores de Docker: `yum erase docker docker-engine docker.io`
1. Instale los requisitos previos del motor de Docker: `yum install -y yum-utils`
1. Agregue el repositorio de Docker:

    ```bash
    yum-config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo
    yum makecache
    ```

1. Instale el motor de Docker: `yum -y install docker-ce`
1. Iniciar Docker

    ```bash
    systemctl start docker
    systemctl enable docker
    ```

1. Prueba de la instalación de Docker: `docker run hello-world`

#### <a name="red-hat"></a>[Red Hat](#tab/red-hat)

1. Quite las versiones anteriores de Docker: `yum erase docker docker-engine docker.io`
1. Instale los requisitos previos del motor de Docker:

    ```bash
    yum install -y yum-utils
    yum install -y https://download.docker.com/linux/centos/7/x86_64/stable/Packages/containerd.io-1.3.7-3.1.el7.x86_64.rpm
    ```

1. Agregue el repositorio de Docker:

    ```bash
    yum-config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo
    yum makecache
    ```

1. Instale el motor de Docker: `yum -y install docker-ce`
1. Iniciar Docker

    ```bash
    systemctl start docker
    systemctl enable docker
    ```

1. Prueba de la instalación de Docker: `docker run hello-world`

#### <a name="ubuntu"></a>[Ubuntu](#tab/ubuntu)

1. Quite las versiones anteriores de Docker: `apt-get remove docker docker-engine docker.io`
1. Si va a instalar en Ubuntu 14,04, instale el paquete Linux-Image-extra.

    ```bash
    apt-get update -y
    apt-get install -y linux-image-extra-$(uname -r) linux-image-extra-virtual
    ```

1. Instale los requisitos previos del motor de Docker:

    ```bash
    apt-get update -y
    (apt-get install -y apt-transport-https ca-certificates curl software-properties-common && curl -fsSL https://download.docker.com/linux/ubuntu/gpg | apt-key add - )
    ```

1. Compruebe que el UID de la huella digital de la clave apt es docker@docker.com:`apt-key fingerprint | grep uid`
1. Instale el motor de Docker:

    ```bash
    add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"
    apt-get update -y
    apt-get install -y docker-ce
    ```

1. Prueba de la instalación de Docker: `docker run hello-world`

---

1. En el portal de Cloud App Security, en la ventana **Create new log collector** (Crear nuevo recopilador de registros), copie el comando para importar la configuración del recopilador en la máquina host:

    ![Copiar comando para importar la configuración del recopilador en el equipo host](media/windows7.png)

1. Ejecute el comando para implementar el recopilador de registros.

    ```bash
    (echo db3a7c73eb7e91a0db53566c50bab7ed3a755607d90bb348c875825a7d1b2fce) | docker run --name MyLogCollector -p 21:21 -p 20000-20099:20000-20099 -e "PUBLICIP='192.168.1.1'" -e "PROXY=192.168.10.1:8080" -e "CONSOLE=mod244533.us.portal.cloudappsecurity.com" -e "COLLECTOR=MyLogCollector" --security-opt apparmor:unconfined --cap-add=SYS_ADMIN --restart unless-stopped -a stdin -i mcr.microsoft.com/mcas/logcollector starter
    ```

    ![Proxy Ubuntu](media/ubuntu-proxy.png)

1. Para comprobar si el recopilador de registros se ejecuta correctamente, ejecute el comando siguiente: `Docker logs <collector_name>`. Debe obtener los resultados: **Finalizado correctamente.**

    ![Comando para comprobar que el recopilador de registros se está ejecutando correctamente](media/ubuntu8.png)

### <a name="step-3---on-premises-configuration-of-your-network-appliances"></a>Paso 3: Configuración local de los dispositivos de red

Configure los firewalls y los servidores proxy de la red de modo que exporten periódicamente los registros al puerto Syslog dedicado del directorio FTP según las instrucciones del cuadro de diálogo. Por ejemplo:

```bash
BlueCoat_HQ - Destination path: \<<machine_name>>\BlueCoat_HQ\
```

### <a name="step-4---verify-the-successful-deployment-in-the-cloud-app-security-portal"></a>Paso 4: Comprobación de la implementación correcta en el portal Cloud App Security

Compruebe el estado del recopilador en la tabla **Recopilador de registros** y asegúrese de que el estado es **Conectado**. Si es **Creado**, es posible que la conexión y el análisis del recopilador de registros no se hayan completado.

![Comprobar el estado del recopilador en el recopilador de registros](media/ubuntu9.png)

También puede ir al **registro de gobernanza** y comprobar que los registros se están cargando periódicamente en el portal.

Como alternativa, puede comprobar el estado del recopilador de registros desde el contenedor de Docker mediante los siguientes comandos:

1. Inicie sesión en el contenedor con este comando: `docker exec -it <Container Name> bash`
1. Compruebe el estado del recopilador de registros con este comando: `collector_status -p`

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
