---
title: "Configurar la carga de registros automática para informes continuos mediante un Docker en Windows | Microsoft Docs"
description: "En este tema se describe el proceso para configurar la carga de registros automática para informes continuos en Cloud App Security mediante Docker en Windows."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 7/16/2017
ms.topic: get-started-article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: 308c06b3-f58b-4a21-86f6-8f87823a893a
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 1ef3958d72150a1a67e92877c58270cbe17fe038
ms.sourcegitcommit: ae4c8226f6037c5eb286eb27142d6bbb397609e9
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/16/2017
---
# <a name="set-up-and-configure-the-automatic-log-collector-docker-on-windows-server-2016"></a>Instalar y configurar el Docker de recopilador de registros automático en Windows Server 2016

## <a name="technical-requirements"></a>Requisitos técnicos

-   Sistema operativo: Windows Server 2016 o Windows 10

-   Espacio en disco: 250 GB

-   CPU: 2

-   RAM: 4 GB

-   Configuración del firewall:

    -   Permitir que el recopilador de registros reciba tráfico entrante de FTP y Syslog.

    -   Permitir que el recopilador de registros inicie tráfico saliente al portal (por ejemplo, contoso.cloudappsecurity.com) en el puerto 443.

## <a name="log-collector-performance"></a>Rendimiento del recopilador de registros

El recopilador de registros puede manejar correctamente una capacidad de registros de hasta 50 GB por hora. Los principales cuellos de botella del proceso de recopilación de registros son:

-   Ancho de banda de red: el ancho de banda de red determina la velocidad de carga de registros.

-   Rendimiento de E/S de la máquina virtual asignada por TI: determina la velocidad a la que se escriben los registros en el disco del recopilador de registros. El recopilador de registros tiene un mecanismo de seguridad integrado que supervisa la velocidad a la que llegan los registros y la compara con la velocidad de carga. En caso de congestión, el recopilador de registros comienza a quitar archivos de registro. Si la configuración normalmente supera los 50 GB por hora, se recomienda dividir el tráfico entre varios recopiladores de registros.

## <a name="step-1--web-portal-configuration-define-data-sources-and-link-them-to-a-log-collector"></a>Paso 1: Configuración del portal web: definición de orígenes de datos y vinculación a un recopilador de registros

1.  Vaya a la página de configuración de carga automatizada:<br></br> En el portal de Cloud App Security, haga clic en el [icono de configuración](./media/settings-icon.png) y, después, en **Recopiladores de registros**.

2.  Cree un origen de datos coincidente para cada firewall o servidor proxy desde el que quiera cargar registros:

    ![Windows 1](./media/windows1.png)

    a. Haga clic en **Agregar origen de datos**.

    b. **Ponga nombre** al servidor proxy o firewall.

    c. Seleccione el dispositivo en la lista **Origen**.

    d. Compare el registro con el ejemplo del formato de registro esperado. Si el formato del archivo de registro no coincide con este ejemplo, debe agregar el origen de datos como **Otro**.

    e. Establezca el **Tipo de receptor** en **FTP**, **FTPS**, **Syslog: UDP**, o **Syslog: TCP** o **Syslog – TLS**.

    > [!NOTE]
    > La integración con los protocolos de transferencia segura (FTPS y Syslog – TLS) a menudo requiere una configuración adicional o el firewall o proxy.

    f. Repita este proceso para cada servidor proxy y firewall cuyos registros se puedan usar para detectar tráfico en la red.

3.  Vaya a la pestaña **Recopiladores de registros** de la parte superior.

    a. Haga clic en **Agregar recopilador de registros**.

    b. Ponga **nombre** al recopilador de registros.

    c. Escriba la **Dirección IP del host** de la máquina que usará para implementar el Docker.

    d. Seleccione todos los **Orígenes de datos** que quiere conectar al recopilador y haga clic en **Actualizar** para guardar la configuración. Vea los pasos de implementación siguientes.

    ![Windows2](./media/windows2.png)

    > [!NOTE]
    > - Un único recopilador de registros puede administrar varios orígenes de datos.

    > -   Copie el contenido de la pantalla, ya que necesitará la información al configurar el recopilador de registros para comunicarse con Cloud App Security. Si ha seleccionado Syslog, esta información incluirá información sobre el puerto en el que escucha el agente de escucha de Syslog.

4.  Se mostrará más información sobre la implementación.

    ![Windows3](./media/windows3.png)

5.  **Copie** el comando de ejecución en el cuadro de diálogo. Puede usar el icono Copiar al Portapapeles [icono Copiar al Portapapeles](./media/copy-icon.png).

6.  **Exporte** la configuración de los orígenes de datos esperados. Esta configuración describe cómo se debe establecer la exportación del registro en los dispositivos.

    ![Windows4](./media/windows4.png)

## <a name="step-2--on-premises-deployment-of-your-machine"></a>Paso 2: implementación local de la máquina

>[!NOTE]
>En los pasos siguientes se describe la implementación de Windows Server. Los pasos de implementación para otras plataformas son ligeramente diferentes.

1.  **Descargue** el [Docker estable más reciente para Windows](https://docs.docker.com/docker-for-windows/install/\#download-docker-for-windows).
    
2.  **Ejecute** el instalador de InstallDocker.msi.

3.  Abra un terminal de PowerShell en el equipo Windows.

4.  **Conéctese** al concentrador del docker con el comando siguiente: `docker login -u cascollector`.

5.  Use la siguiente contraseña `C0llector3nthusiast`.

    ![Windows5](./media/windows5.png)

6.  **Extraiga** a la imagen del recopilador desde el concentrador del docker con el comando siguiente: `docker pull Microsoft/caslogcollector`.

    ![Windows6](./media/windows6.png)

7.  Implemente la imagen de recopilador mediante el comando de ejecución generado en el portal.

    ![windows8](./media/windows8.png)

    >[!NOTE]
    >Si tiene que configurar un proxy, agregue la dirección IP del proxy y el puerto. Por ejemplo, si los detalles del proxy son 192.168.10.1:8080, el comando de ejecución actualizado es:  
 `   Sudo docker run --name casCollector -p 21:21 -p 20000-20099:20000-20099 -e
    "PUBLICIP='192.168.1.1'" -e "PROXY=192.168.10.1:8080" -e
    "TOKEN=41f8f442c9a30519a058dd3bb9a19c79eb67f34a8816270dc4a384493988863a" -e
    "CONSOLE=tenant2.eu1-rs.adallom.com" -e "COLLECTOR=casCollector" --security-opt
    apparmor:unconfined --cap-add=SYS_ADMIN -dt microsoft/caslogcollector starter`

    ![windows9](./media/windows9.png)

9.  Compruebe que el recopilador funciona correctamente ejecutando el siguiente comando: `Docker logs <collector_name>`

Debería ver el mensaje **Finalizado correctamente**.
  ![windows10](./media/windows10.png)

## <a name="step-4---on-premises-configuration-of-your-network-appliances"></a>Paso 4: Configuración local de los dispositivos de red

Configure los firewalls y los servidores proxy de la red de modo que exporten periódicamente los registros al puerto Syslog dedicado del directorio FTP según las instrucciones del cuadro de diálogo, por ejemplo:

        BlueCoat_HQ - Destination path: \<<machine_name>>\BlueCoat_HQ\

## <a name="step-5---verify-the-successful-deployment-in-the-cloud-app-security-portal"></a>Paso 5: Comprobación de la implementación correcta en el portal Cloud App Security

Compruebe el estado del recopilador en la tabla **Recopilador de registros** y asegúrese de que el estado es **Conectado**. Si es **Creado**, es posible que la conexión y el análisis del recopilador de registros no se hayan completado.

![windows11](./media/windows11.png)

También puede ir al **Registro de gobierno** y comprobar que los registros se están cargando periódicamente en el portal.

Si tiene problemas durante la implementación, consulte [Solución de problemas de Cloud Discovery](troubleshooting-cloud-discovery.md).

## <a name="see-also"></a>Consulte también
 
[Crear informes de instantáneas de Cloud Discovery](create-snapshot-cloud-discovery-reports.md)

[Configurar la carga de registros automática para informes continuos](configure-automatic-log-upload-for-continuous-reports.md)

[Trabajar con datos de Cloud Discovery](working-with-cloud-discovery-data.md)

