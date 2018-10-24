---
title: Configurar la carga de registros automática para informes continuos | Microsoft Docs
description: En este tema se describe el proceso de configuración de carga de registros automática para informes continuos en Cloud App Security con Docker en Ubuntu en un servidor local.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 10/5/2018
ms.topic: conceptual
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: cc29a6cb-1c03-4148-8afd-3ad47003a1e3
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: d23ee52b6186280e7b27b56b5516a6bd9dc436f3
ms.sourcegitcommit: da651fb36d26d0dfe796b988e86205f41f7dc5de
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/03/2018
ms.locfileid: "48251546"
---
*Se aplica a: Microsoft Cloud App Security*


# <a name="docker-on-ubuntu-and-rhel-on-premises"></a>Docker en Ubuntu y RHEL locales


## <a name="technical-requirements"></a>Requisitos técnicos

-   Sistema operativo: Ubuntu 14.04, 16.04 y 18.04; o RHEL 7.2 o posterior 

-   Espacio en disco: 250 GB

-   CPU: 2

-   RAM: 4 GB

-   Configuración del firewall, tal como se describe en [Requisitos de red](network-requirements.md#log-collector)


## <a name="log-collector-performance"></a>Rendimiento del recopilador de registros

El recopilador de registros puede manejar correctamente una capacidad de registros de hasta 50 GB por hora. Los principales cuellos de botella del proceso de recopilación de registros son:

-   Ancho de banda de red: el ancho de banda de red determina la velocidad de carga de registros.

-   Rendimiento de E/S de la máquina virtual asignada por TI: determina la velocidad a la que se escriben los registros en el disco del recopilador de registros. El recopilador de registros tiene un mecanismo de seguridad integrado que supervisa la velocidad a la que llegan los registros y la compara con la velocidad de carga. En caso de congestión, el recopilador de registros comienza a quitar archivos de registro. Si la configuración normalmente supera los 50 GB por hora, se recomienda dividir el tráfico entre varios recopiladores de registros.

## <a name="set-up-and-configuration"></a>Establecimiento y configuración  

### <a name="step-1--web-portal-configuration-define-data-sources-and-link-them-to-a-log-collector"></a>Paso 1: Configuración del portal web: definición de orígenes de datos y vinculación a un recopilador de registros

1. Vaya a la página de configuración de carga automatizada:  <br></br>En el portal de Cloud App Security, haga clic en el ![icono de configuración](./media/settings-icon.png) y, después, en **Recopiladores de registros**.

2. Cree un origen de datos coincidente para cada firewall o servidor proxy desde el que quiera cargar registros:

   ![ubuntu1](./media/ubuntu1.png)

   a. Haga clic en **Agregar origen de datos**.

   b. **Ponga nombre** al servidor proxy o firewall.

   c. Seleccione el dispositivo en la lista **Origen**. Si selecciona **Formato de registro personalizado** para trabajar con un dispositivo de red que no aparezca específicamente en la lista, consulte el artículo sobre cómo [trabajar con el analizador de registro personalizado](custom-log-parser.md) para ver las instrucciones de configuración.

   d. Compare el registro con el ejemplo del formato de registro esperado. Si el formato del archivo de registro no coincide con este ejemplo, debe agregar el origen de datos como **Otro**.

   e. Establezca el **tipo de receptor** en **FTP**, **FTPS**, **Syslog – UDP**, **Syslog – TCP** o **Syslog – TLS**.
    
    >[!NOTE]
    >La integración con protocolos de transferencia segura (FTPS y Syslog – TLS) a menudo requiere una configuración adicional o firewall/proxy.

   f. Repita este proceso para cada servidor proxy y firewall cuyos registros se puedan usar para detectar tráfico en la red.
    > [!NOTE]
    >Se recomienda configurar un origen de datos dedicado por dispositivo de red para poder hacer lo siguiente:
    <br>- Supervisar el estado de cada dispositivo por separado para fines de investigación.
    <br>- Explorar Shadow IT Discovery de cada dispositivo, si cada uno de ellos lo utiliza un segmento de usuarios distinto.


3. Vaya a la pestaña **Recopiladores de registros** de la parte superior.

   a. Haga clic en **Agregar recopilador de registros**.

   b. Ponga **nombre** al recopilador de registros.

   c. Escriba la **dirección IP de host** de la máquina que usará para implementar Docker. 
       
      > [!NOTE]
      > La dirección IP del host puede reemplazarse con el nombre del equipo si un servidor DNS (o equivalente) resolverá el nombre de host.

   d. Seleccione todos los **orígenes de datos** que desea conectar al recopilador y haga clic en **Actualizar** para guardar la configuración. Luego, consulte los pasos de implementación siguientes.

   ![ubuntu2](./media/ubuntu2.png)

   > [!NOTE]
   > - Un único recopilador de registros puede administrar varios orígenes de datos.
   > - Copie el contenido de la pantalla, ya que necesitará la información al configurar el recopilador de registros para comunicarse con Cloud App Security. Si ha seleccionado Syslog, esta información incluirá información sobre el puerto en el que escucha el agente de escucha de Syslog.

4. Aparecerá más información de implementación. **Copie** el comando de ejecución desde el cuadro de diálogo. Puede usar el icono Copiar al Portapapeles ![icono Copiar al Portapapeles](./media/copy-icon.png).

5. **Exporte** la configuración de origen de datos esperada. Esta configuración describe cómo debe establecer la exportación de registro en los dispositivos.

   ![Crear un recopilador de registros](./media/windows7.png)

### <a name="step-2--on-premises-deployment-of-your-machine"></a>Paso 2: Implementación local de la máquina

> [!NOTE]
> En los pasos siguientes se describe la implementación de Ubuntu. Los pasos de implementación en otras plataformas son ligeramente diferentes.

1. Abra un terminal en la máquina Ubuntu.

2. Cambie a los privilegios raíz con el comando: `sudo -i`

3. Para omitir a un servidor proxy en la red, ejecute los dos comandos siguientes:
        
        export http_proxy='<IP>:<PORT>' (e.g. 168.192.1.1:8888)
        export https_proxy='<IP>:<PORT>'

4. Si acepta los [términos de licencia del software](https://go.microsoft.com/fwlink/?linkid=862492), desinstale las versiones anteriores e instale Docker CE con el comando siguiente:

   `curl -o /tmp/MCASInstallDocker.sh
   https://adaprodconsole.blob.core.windows.net/public-files/MCASInstallDocker.sh
   && chmod +x /tmp/MCASInstallDocker.sh; /tmp/MCASInstallDocker.sh`

    > [!NOTE] 
    > Si se produce un error en este comando al validar el certificado de servidor proxy, ejecute el comando con `curl -k` al principio.
    
   ![ubuntu5](./media/ubuntu5.png)

5. Implemente la imagen del recopilador en la máquina host al importar la configuración del recopilador. Esto se realiza copiando el comando de ejecución generado en el portal. Si necesita configurar un proxy, agregue la dirección IP del proxy y el número de puerto. Por ejemplo, si los detalles de proxy son 192.168.10.1:8080, el comando de ejecución actualizado es:

           (echo 6f19225ea69cf5f178139551986d3d797c92a5a43bef46469fcc997aec2ccc6f) | docker run --name MyLogCollector -p 21:21 -p 20000-20099:20000-20099 -e "PUBLICIP='192.2.2.2'" -e "PROXY=192.168.10.1:8080" -e "CONSOLE=tenant2.eu1-rs.adallom.com" -e "COLLECTOR=MyLogCollector" --security-opt apparmor:unconfined --cap-add=SYS_ADMIN --restart unless-stopped -a stdin -i microsoft/caslogcollector starter

   ![Crear un recopilador de registros](./media/windows7.png)

6. Ejecute el comando siguiente para comprobar si el recopilador se ejecuta correctamente: `docker logs \<collector_name\>`

Debería ver el mensaje: **Finalizó correctamente**.

  ![ubuntu8](./media/ubuntu8.png)

### <a name="step-3---on-premises-configuration-of-your-network-appliances"></a>Paso 3: Configuración local de los dispositivos de red

Configure los firewalls y los servidores proxy de la red de modo que exporten periódicamente los registros al puerto Syslog dedicado del directorio FTP según las instrucciones del cuadro de diálogo, por ejemplo:

    BlueCoat_HQ - Destination path: \<<machine_name>>\BlueCoat_HQ\

### <a name="step-4---verify-the-successful-deployment-in-the-cloud-app-security-portal"></a>Paso 4: Comprobación de la implementación correcta en el portal Cloud App Security

Compruebe el estado del recopilador en la tabla **Recopilador de registros** y asegúrese de que el estado es **Conectado**. Si es **Creado**, es posible que la conexión y el análisis del recopilador de registros no se hayan completado.

 ![ubuntu9](./media/ubuntu9.png)

También puede ir al **registro de gobierno** y comprobar que los registros se carguen de manera periódica en el portal.

Si tiene problemas durante la implementación, consulte [Solución de problemas de Cloud Discovery](troubleshooting-cloud-discovery.md).

### <a name="optional---create-custom-continuous-reports"></a>Opcional: crear informes continuos personalizados

Después de comprobar que los registros se cargan en Cloud App Security y que se generan los informes, puede crear informes personalizados. Ahora puede crear informes de detección personalizados en función de los grupos de usuarios de Azure Active Directory. Por ejemplo, si quiere ver el uso de la nube por parte del departamento de marketing, puede importar el grupo de marketing mediante la característica para importar grupos de usuarios y, después, crear un informe personalizado para este grupo. También puede personalizar un informe en función de la etiqueta de dirección IP o los intervalos de direcciones IP.

1. En el portal de Cloud App Security, en el engranaje de configuración, seleccione **Cloud Discovery settings** (Configuración de Cloud Discovery) y **Administrar informes continuos**. 
2. Haga clic en el botón **Crear informe** y rellene los campos.
3. En **Filtros**, puede filtrar los datos por origen de datos, por [grupo de usuarios importados](user-groups.md) o por [etiquetas e intervalos de direcciones IP](ip-tags.md). 

![Informe continuo personalizado](./media/custom-continuous-report.png)

## <a name="see-also"></a>Consulte también

[Solución de problemas de implementación de Docker para Cloud Discovery](troubleshoot-docker.md)

[Los clientes Premier también pueden elegir Cloud App Security directamente desde el Portal Premier](https://premier.microsoft.com/)

