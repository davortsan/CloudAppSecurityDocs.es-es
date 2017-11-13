---
title: "Configuración de la carga de registros automática para informes continuos con Docker en Windows | Microsoft Docs"
description: "En este tema se describe el proceso de configuración de carga de registros automática para informes continuos en Cloud App Security con Docker en Windows."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 11/7/2017
ms.topic: get-started-article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: 308c06b3-f58b-4a21-86f6-8f87823a893a
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 0bda9f2ccc5c2e74e11edddf32789216f32958f7
ms.sourcegitcommit: 938c799a13a81f3289229ea883c65bd1669b2ec4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/07/2017
---
# <a name="set-up-and-configure-the-automatic-log-collector-docker-on-windows-server-2016"></a>Configuración del Docker del recopilador de registros automático en Windows Server 2016

> [!NOTE]
> Esta característica se está implantando gradualmente entre los inquilinos. Póngase en contacto con soporte técnico si quiere agregarse a la versión preliminar.

## <a name="technical-requirements"></a>Requisitos técnicos

-   SO: Windows Server 2016 o Windows 10

-   Espacio en disco: 250 GB

-   CPU: 2

-   RAM: 4 GB

-   Configuración del firewall:

    -   Permita que el recopilador de registros reciba tráfico entrante de FTP y Syslog.

    -   Permita que el recopilador de registros inicie tráfico saliente al portal (por ejemplo, portal.contoso.cloudappsecurity.com) en el puerto 443.

    - Permita que el recopilador de registros inicie tráfico saliente al almacenamiento de blobs de Azure (https://adaprodconsole.blob.core.windows.net/) en los puertos 80 y 443.

> [!NOTE]
> Si el firewall requiere una lista de acceso de dirección IP estática y no admite la creación de listas blancas basada en direcciones URL, permita que el recopilador de registros enrute el tráfico saliente hacia los [intervalos IP del centro de datos de Microsoft Azure a través del puerto 443](https://www.microsoft.com/download/details.aspx?id=41653&751be11f-ede8-5a0c-058c-2ee190a24fa6=True).

## <a name="log-collector-performance"></a>Rendimiento del recopilador de registros

El recopilador de registros puede manejar correctamente una capacidad de registros de hasta 50 GB por hora. Los principales cuellos de botella del proceso de recopilación de registros son:

-   Ancho de banda de red: el ancho de banda de red determina la velocidad de carga de registros.

-   Rendimiento de E/S de la máquina virtual asignada por TI: determina la velocidad a la que se escriben los registros en el disco del recopilador de registros. El recopilador de registros tiene un mecanismo de seguridad integrado que supervisa la velocidad a la que llegan los registros y la compara con la velocidad de carga. En caso de congestión, el recopilador de registros comienza a quitar archivos de registro. Si la configuración normalmente supera los 50 GB por hora, se recomienda dividir el tráfico entre varios recopiladores de registros.

## <a name="set-up-and-configuration"></a>Establecimiento y configuración  

### <a name="step-1--web-portal-configuration-define-data-sources-and-link-them-to-a-log-collector"></a>Paso 1: Configuración del portal web: definición de orígenes de datos y vinculación a un recopilador de registros

1.  Vaya a la página de configuración de carga automatizada:<br></br> En el portal de Cloud App Security, haga clic en el [icono de configuración](./media/settings-icon.png) y, después, en **Recopiladores de registros**.

2.  Cree un origen de datos coincidente para cada firewall o servidor proxy desde el que quiera cargar registros:

    ![Windows 1](./media/windows1.png)

    a. Haga clic en **Agregar origen de datos**.

    b. **Ponga nombre** al servidor proxy o firewall.

    c. Seleccione el dispositivo en la lista **Origen**. Si selecciona **Formato de registro personalizado** para trabajar con un dispositivo de red que no aparezca específicamente en la lista, consulte el artículo sobre cómo [trabajar con el analizador de registro personalizado](custom-log-parser.md) para ver las instrucciones de configuración.

    d. Compare el registro con el ejemplo del formato de registro esperado. Si el formato del archivo de registro no coincide con este ejemplo, debe agregar el origen de datos como **Otro**.

    e. Establezca el **tipo de receptor** en **FTP**, **FTPS**, **Syslog – UDP**, **Syslog – TCP** o **Syslog – TLS**.

    > [!NOTE]
    > La integración con protocolos de transferencia segura (FTPS y Syslog – TLS) a menudo requiere una configuración adicional o Firewall/Proxy.

    f. Repita este proceso para cada servidor proxy y firewall cuyos registros se puedan usar para detectar tráfico en la red.

3.  Vaya a la pestaña **Recopiladores de registros** de la parte superior.

    a. Haga clic en **Agregar recopilador de registros**.

    b. Ponga **nombre** al recopilador de registros.

    c. Escriba la **dirección IP de host** de la máquina que usará para implementar Docker.

    d. Seleccione todos los **orígenes de datos** que desea conectar al recopilador y haga clic en **Actualizar** para guardar la configuración. Luego, consulte los pasos de implementación siguientes.

    ![Windows2](./media/windows2.png)

    > [!NOTE]
    > - Un único recopilador de registros puede administrar varios orígenes de datos.

    > -   Copie el contenido de la pantalla, ya que necesitará la información al configurar el recopilador de registros para comunicarse con Cloud App Security. Si ha seleccionado Syslog, esta información incluirá información sobre el puerto en el que escucha el agente de escucha de Syslog.

4.  Aparecerá más información de implementación. **Copie** el comando de ejecución desde el cuadro de diálogo. Puede usar el icono Copiar al Portapapeles [icono Copiar al Portapapeles](./media/copy-icon.png).

6.  **Exporte** la configuración de orígenes de datos esperada. Esta configuración describe cómo debe establecer la exportación de registro en los dispositivos.

   ![Crear un recopilador de registros](./media/windows7.png)

### <a name="step-2--on-premises-deployment-of-your-machine"></a>Paso 2: Implementación local de la máquina

>[!NOTE]
>En los pasos siguientes se describe la implementación en Windows Server . Los pasos de implementación en otras plataformas son ligeramente diferentes.

1.  **Descargue** la [versión estable más reciente de Docker para Windows](https://docs.docker.com/docker-for-windows/install/\#download-docker-for-windows).
    
2.  **Ejecute** el instalador InstallDocker.msi.

3.  Abra un terminal de PowerShell en la máquina Windows.

4.  **Conéctese** a Docker Hub con el comando siguiente: `docker login -u caslogcollector`

5.  Use la contraseña siguiente `C0llector3nthusiast`

    ![windows5](./media/windows5.png)

6.  **Extraiga** a la imagen del recopilador desde Docker Hub con el comando siguiente: `docker pull microsoft/caslogcollector`

    ![windows6](./media/windows6.png)

7.  Implemente la imagen del recopilador con el comando de ejecución que se generó en el portal.

   ![Crear un recopilador de registros](./media/windows7.png)

   Si necesita configurar un proxy, agregue la dirección IP del proxy y el número de puerto. Por ejemplo, si los detalles de proxy son 192.168.10.1:8080, el comando de ejecución actualizado es:  
 `(echo 6f19225ea69cf5f178139551986d3d797c92a5a43bef46469fcc997aec2ccc6f) | docker run --name MyLogCollector -p 21:21 -p 20000-20099:20000-20099 -e "PUBLICIP='192.2.2.2'" -e "PROXY=192.168.10.1:8080" -e "CONSOLE=tenant2.eu1-rs.adallom.com" -e "COLLECTOR=MyLogCollector" --security-opt apparmor:unconfined --cap-add=SYS_ADMIN --restart unless-stopped -a stdin -i microsoft/caslogcollector starter`

9.  Ejecute el comando siguiente para comprobar si el recopilador se ejecuta correctamente: `docker logs <collector_name>`

Debería ver el mensaje: **Finalizó correctamente**.
  ![windows10](./media/windows10.png)

### <a name="step-3---on-premises-configuration-of-your-network-appliances"></a>Paso 3: Configuración local de los dispositivos de red

Configure los firewalls y los servidores proxy de la red de modo que exporten periódicamente los registros al puerto Syslog dedicado del directorio FTP según las instrucciones del cuadro de diálogo, por ejemplo:

        BlueCoat_HQ - Destination path: \<<machine_name>>\BlueCoat_HQ\

### <a name="step-4---verify-the-successful-deployment-in-the-cloud-app-security-portal"></a>Paso 4: Comprobación de la implementación correcta en el portal Cloud App Security

Compruebe el estado del recopilador en la tabla **Recopilador de registros** y asegúrese de que el estado es **Conectado**. Si es **Creado**, es posible que la conexión y el análisis del recopilador de registros no se hayan completado.

![windows11](./media/windows11.png)

También puede ir al **registro de gobierno** y comprobar que los registros se carguen de manera periódica en el portal.

Si tiene problemas durante la implementación, consulte [Solución de problemas de Cloud Discovery](troubleshooting-cloud-discovery.md).

## <a name="optional---create-custom-continuous-reports"></a>Opcional: crear informes continuos personalizados

Después de comprobar que los registros se cargan en Cloud App Security y que se generan los informes, puede crear informes personalizados. Ahora puede crear informes de detección personalizados en función de los grupos de usuarios de Azure Active Directory. Por ejemplo, si quiere ver el uso de la nube por parte del departamento de marketing, puede importar el grupo de marketing mediante la característica para importar grupos de usuarios y, después, crear un informe personalizado para este grupo. También puede personalizar un informe en función de la etiqueta de dirección IP o los intervalos de direcciones IP.

1. En el portal de Cloud App Security, en el engranaje de configuración, seleccione **Cloud Discovery settings** (Configuración de Cloud Discovery) y **Administrar informes continuos**. 
2. Haga clic en el botón **Crear informe** y rellene los campos.
3. En **Filtros**, puede filtrar los datos por origen de datos, por [grupo de usuarios importados](user-groups.md) o por [etiquetas e intervalos de direcciones IP](ip-tags.md). 

![Informe continuo personalizado](./media/custom-continuous-report.png)

## <a name="see-also"></a>Vea también
 
[Crear informes de instantáneas de Cloud Discovery](create-snapshot-cloud-discovery-reports.md)

[Configurar la carga de registros automática para informes continuos](configure-automatic-log-upload-for-continuous-reports.md)

[Trabajar con datos de Cloud Discovery](working-with-cloud-discovery-data.md)

