---
title: Configuración de la carga de registros automática con Docker en Azure
description: En este artículo se describe el proceso de configuración de carga de registros automática para informes continuos en Cloud App Security con Docker en Ubuntu o RHEL en Azure.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 1/27/2019
ms.topic: conceptual
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 9c51b888-54c0-4132-9c00-a929e42e7792
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 9d3d0aad417050011a5a5780e5563ac3d040eb37
ms.sourcegitcommit: c24732bc40350c3cf416640b7d15f3c6f7be371d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/28/2019
ms.locfileid: "55086454"
---
# <a name="set-up-and-configuration-on-ubuntu-or-rhel-in-azure"></a>Instalación y configuración en Ubuntu o RHEL en Azure

*Se aplica a: Microsoft Cloud App Security*

Puede configurar la carga de registros automática para informes continuos en Cloud App Security con Docker en Ubuntu o Red Hat Enterprise Linux (RHEL) en Azure. En este artículo se describe cómo configurar la carga de registros automática. 

## <a name="technical-requirements"></a>Requisitos técnicos

- Sistema operativo: Ubuntu 14.04 y 16.04 (para versiones más recientes, póngase en contacto con el soporte técnico), o RHEL 7.2 o superior

- Espacio en disco 250 GB

- CPU: 2

- RAM: 4 GB

- Configuración del firewall, tal como se describe en [Requisitos de red](network-requirements.md#log-collector)

## <a name="log-collector-performance"></a>Rendimiento del recopilador de registros

El recopilador de registros puede manejar correctamente una capacidad de registros de hasta 50 GB por hora. Los principales cuellos de botella del proceso de recopilación de registros son:

- Ancho de banda de red: el ancho de banda de red determina la velocidad de carga de registros.

- Rendimiento de E/S de la máquina virtual: determina la velocidad a la que se escriben los registros en el disco del recopilador de registros. El recopilador de registros tiene un mecanismo de seguridad integrado que supervisa la velocidad a la que llegan los registros y la compara con la velocidad de carga. En caso de congestión, el recopilador de registros comienza a quitar archivos de registro. Si la configuración normalmente supera los 50 GB por hora, se recomienda dividir el tráfico entre varios recopiladores de registros.

## <a name="set-up-and-configuration"></a>Establecimiento y configuración  

### <a name="step-1--web-portal-configuration-define-data-sources-and-link-them-to-a-log-collector"></a>Paso 1: Configuración del portal web: definición de orígenes de datos y vinculación a un recopilador de registros

1. Vaya a la página de configuración **Carga de registros automática**. 

     a. En el portal de Cloud App Security, haga clic en el icono de configuración y en **Recopiladores de registros**.

      ![icono de configuración](./media/settings-icon.png)

2. Cree un origen de datos coincidente para cada firewall o servidor proxy desde el que quiera cargar registros.

     a. Haga clic en **Agregar origen de datos**.

      ![Agregar un origen de datos](./media/add-data-source.png)
          
     b. **Ponga nombre** al servidor proxy o firewall.
      
      ![ubuntu1](./media/ubuntu1.png)

     c. Seleccione el dispositivo en la lista **Origen**. Si selecciona **Formato de los registros personalizados** para trabajar con un dispositivo de red que no aparezca en la lista, consulte el artículo sobre cómo [trabajar con el analizador de registros personalizados](custom-log-parser.md) para ver las instrucciones de configuración.

     d. Compare el registro con el ejemplo del formato de registro esperado. Si el formato de archivo del registro no coincide con este ejemplo, debe agregar el origen de datos como **Otro**.

     e. Establezca el **tipo de receptor** en **FTP**, **FTPS**, **Syslog – UDP**, **Syslog – TCP** o **Syslog – TLS**.
     
     >[!NOTE]
     >La integración con protocolos de transferencia segura (FTPS y Syslog – TLS) a menudo requiere una configuración adicional o firewall/proxy.

     f. Repita este proceso para cada servidor proxy y firewall cuyos registros se puedan usar para detectar tráfico en la red. Se recomienda configurar un origen de datos dedicado por dispositivo de red para poder hacer lo siguiente:
     - Supervisar el estado de cada dispositivo por separado para fines de investigación.
     - Explorar Shadow IT Discovery de cada dispositivo, si cada uno de ellos lo usa un segmento de usuarios distinto.

     
3. Vaya a la pestaña **Recopiladores de registros** de la parte superior.

     a. Haga clic en **Agregar recopilador de registros**.

     b. Ponga **nombre** al recopilador de registros.

     c. Escriba la **dirección IP de host** de la máquina que se va a usar para implementar Docker. La dirección IP del host puede reemplazarse con el nombre del equipo si un servidor DNS (o equivalente) resolverá el nombre de host.

     d. Seleccione todos los **orígenes de datos** que desea conectar al recopilador y haga clic en **Actualizar** para guardar la configuración. Luego, consulte los pasos de implementación siguientes.

      ![ubuntu2](./media/ubuntu2.png)

     > [!NOTE]
     > - Un único recopilador de registros puede administrar varios orígenes de datos.
     > - Copie el contenido de la pantalla, ya que necesitará la información al configurar el recopilador de registros para comunicarse con Cloud App Security. Si ha seleccionado Syslog, esta información incluirá información sobre el puerto en el que escucha el agente de escucha de Syslog.

4. Aparecerá más información de implementación. **Copie** el comando de ejecución desde el cuadro de diálogo. Puede usar el icono Copiar al Portapapeles. ![icono copiar al portapapeles](./media/copy-icon.png)

5. **Exporte** la configuración de origen de datos esperada. Esta configuración describe cómo debe establecer la exportación de registro en los dispositivos.

     ![Crear un recopilador de registros](./media/windows7.png)

### <a name="step-2--deployment-of-your-machine-in-azure"></a>Paso 2: Implementación de la máquina en Azure

> [!NOTE]
> En los pasos siguientes se describe la implementación de Ubuntu. Los pasos de implementación en otras plataformas son ligeramente diferentes.


1. Cree una nueva máquina Ubuntu en el entorno Azure. 
2. Cuando la máquina esté en funcionamiento, abra los puertos mediante:

     a. En la vista de la máquina, vaya a **Redes** y seleccione la interfaz adecuada haciendo doble clic en ella.

     b. Vaya a **Grupo de seguridad de red** y seleccione el grupo de seguridad de red pertinente.

     c. Vaya a **Reglas de seguridad de entrada** y haga clic en **Agregar**.
      
      ![Ubuntu en Azure](./media/ubuntu-azure.png)
    
     d. Agregue las siguientes reglas (en modo **Avanzado**):

      |Nombre|Rangos de puertos de destino|Protocolo|Origen|Destination|
      |----|----|----|----|----|
      |caslogcollector_ftp|21|TCP|<Subred de la dirección IP del dispositivo>|Cualquiera|
      |caslogcollector_ftp_passive|20000-20099|TCP|<Subred de la dirección IP del dispositivo>|Cualquiera|
      |caslogcollector_syslogs_tcp|601-700|TCP|<Subred de la dirección IP del dispositivo>|Cualquiera|
      |caslogcollector_syslogs_udp|514-600|UDP|<Subred de la dirección IP del dispositivo>|Cualquiera|
      
      ![Reglas de Ubuntu en Azure](./media/inbound-rule.png)

3. Vuelva a la máquina y haga clic en **Conectar** para abrir un terminal en ella.

4. Cambie a los privilegios raíz con `sudo -i`.

5. Si acepta los [términos de licencia del software](https://go.microsoft.com/fwlink/?linkid=862492), desinstale las versiones anteriores e instale Docker CE con el comando siguiente:
        
       curl -o /tmp/MCASInstallDocker.sh https://adaprodconsole.blob.core.windows.net/public-files/MCASInstallDocker.sh && chmod +x /tmp/MCASInstallDocker.sh; /tmp/MCASInstallDocker.sh

     ![Comando de Ubuntu en Azure](./media/ubuntu-azure-command.png)

6. En el portal de Cloud App Security, en la ventana **Create new log collector** (Crear nuevo recopilador de registros), copie el comando para importar la configuración del recopilador en la máquina host:

      ![Ubuntu en Azure](./media/windows7.png)

7. Ejecute el comando para implementar el recopilador de registros.
     
        (echo db3a7c73eb7e91a0db53566c50bab7ed3a755607d90bb348c875825a7d1b2fce) | docker run --name MyLogCollector -p 21:21 -p 20000-20099:20000-20099 -e "PUBLICIP='192.168.1.1'" -e "PROXY=192.168.10.1:8080" -e "CONSOLE=mod244533.us.portal.cloudappsecurity.com" -e "COLLECTOR=MyLogCollector" --security-opt apparmor:unconfined --cap-add=SYS_ADMIN --restart unless-stopped -a stdin -i microsoft/caslogcollector starter

     ![Proxy Ubuntu](./media/ubuntu-proxy.png)

8. Para comprobar si el recopilador de registros se ejecuta correctamente, ejecute el comando siguiente: `Docker logs <collector_name>`. Debe obtener el resultado: **Finished successfully!** (Finalizado correctamente).

   ![ubuntu8](./media/ubuntu8.png)

### <a name="step-3---on-premises-configuration-of-your-network-appliances"></a>Paso 3: Configuración local de los dispositivos de red

Configure los firewalls y los servidores proxy de la red de modo que exporten periódicamente los registros al puerto Syslog dedicado del directorio FTP según las instrucciones del cuadro de diálogo. Por ejemplo:

    BlueCoat_HQ - Destination path: \<<machine_name>>\BlueCoat_HQ\

### <a name="step-4---verify-the-successful-deployment-in-the-cloud-app-security-portal"></a>Paso 4: Comprobación de la implementación correcta en el portal Cloud App Security

Compruebe el estado del recopilador en la tabla **Recopilador de registros** y asegúrese de que el estado es **Conectado**. Si es **Creado**, es posible que la conexión y el análisis del recopilador de registros no se hayan completado.

 ![ubuntu9](./media/ubuntu9.png)

También puede ir al **registro de gobierno** y comprobar que los registros se carguen de manera periódica en el portal.

Si tiene problemas durante la implementación, consulte [Solución de problemas de Cloud Discovery](troubleshooting-cloud-discovery.md).

### <a name="optional---create-custom-continuous-reports"></a>Opcional: crear informes continuos personalizados

Compruebe que se cargan los registros de Cloud App Security y que se generan los informes. Después de la comprobación, cree informes personalizados. Puede crear informes de detección personalizados en función de los grupos de usuarios de Azure Active Directory. Por ejemplo, si quiere ver el uso de la nube por parte del departamento de marketing, importe el grupo de marketing mediante la característica para importar grupos de usuarios. Después, cree un informe personalizado para este grupo. También puede personalizar un informe en función de la etiqueta de dirección IP o los intervalos de direcciones IP.

1. En el portal de Cloud App Security, en el engranaje de configuración, seleccione Configuración de Cloud Discovery y después **Informes continuos**. 
2. Haga clic en el botón **Crear informe** y rellene los campos.
3. En **Filtros**, puede filtrar los datos por origen de datos, por [grupo de usuarios importados](user-groups.md) o por [etiquetas e intervalos de direcciones IP](ip-tags.md). 

     ![Informe continuo personalizado](./media/custom-continuous-report.png)

## <a name="next-steps"></a>Pasos siguientes
[Solución de problemas de implementación de Docker para Cloud Discovery](troubleshoot-docker.md)

[Los clientes Premier también pueden elegir Cloud App Security directamente desde el Portal Premier](https://premier.microsoft.com/)

