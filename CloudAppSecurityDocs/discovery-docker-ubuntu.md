---
title: "Configurar la carga de registros automática para informes continuos | Microsoft Docs"
description: "En este tema se describe el proceso de configuración de carga de registros automática para informes continuos en Cloud App Security con Docker en Ubuntu."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 9/27/2017
ms.topic: get-started-article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: cc29a6cb-1c03-4148-8afd-3ad47003a1e3
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 42e562f484ee5e0a980ab3678c34508cbff113f3
ms.sourcegitcommit: 8759541301241e03784c5ac87b56986f22bd0561
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/28/2017
---
# <a name="set-up-and-configuration-on-ubuntu"></a>Configuración en Ubuntu

> [!NOTE]
> Esta característica se está implantando gradualmente entre los inquilinos. Póngase en contacto con soporte técnico si quiere agregarse a la versión preliminar.

## <a name="technical-requirements"></a>Requisitos técnicos

-   SO: Ubuntu 14.04 o superior

-   Espacio en disco: 250 GB

-   CPU: 2

-   RAM: 4 GB

-   Configuración del firewall:

    -   Permita que el recopilador de registros reciba tráfico entrante de FTP y Syslog.

    -   Permita que el recopilador de registros inicie tráfico saliente al portal (por ejemplo, contoso.cloudappsecurity.com) en el puerto 443.

> [!NOTE]
> Si el firewall requiere una lista de acceso de dirección IP estática y no admite la creación de listas blancas basada en direcciones URL, permita que el recopilador de registros enrute el tráfico saliente hacia los [intervalos IP del centro de datos de Microsoft Azure a través del puerto 443](https://www.microsoft.com/download/details.aspx?id=41653&751be11f-ede8-5a0c-058c-2ee190a24fa6=True).

## <a name="log-collector-performance"></a>Rendimiento del recopilador de registros

El recopilador de registros puede manejar correctamente una capacidad de registros de hasta 50 GB por hora. Los principales cuellos de botella del proceso de recopilación de registros son:

-   Ancho de banda de red: el ancho de banda de red determina la velocidad de carga de registros.

-   Rendimiento de E/S de la máquina virtual asignada por TI: determina la velocidad a la que se escriben los registros en el disco del recopilador de registros. El recopilador de registros tiene un mecanismo de seguridad integrado que supervisa la velocidad a la que llegan los registros y la compara con la velocidad de carga. En caso de congestión, el recopilador de registros comienza a quitar archivos de registro. Si la configuración normalmente supera los 50 GB por hora, se recomienda dividir el tráfico entre varios recopiladores de registros.

## <a name="set-up-and-configuration"></a>Establecimiento y configuración  

### <a name="step-1--web-portal-configuration-define-data-sources-and-link-them-to-a-log-collector"></a>Paso 1: Configuración del portal web: definición de orígenes de datos y vinculación a un recopilador de registros

1.  Vaya a la página de configuración de carga automatizada:  <br></br>En el portal de Cloud App Security, haga clic en el ![icono de configuración](./media/settings-icon.png) y, después, en **Recopiladores de registros**.

2.  Cree un origen de datos coincidente para cada firewall o servidor proxy desde el que quiera cargar registros:

    ![ubuntu1](./media/ubuntu1.png)

    a. Haga clic en **Agregar origen de datos**.

    b. **Ponga nombre** al servidor proxy o firewall.

    c. Seleccione el dispositivo en la lista **Origen**. Si selecciona **Formato de registro personalizado** para trabajar con un dispositivo de red que no aparezca específicamente en la lista, consulte el artículo sobre cómo [trabajar con el analizador de registro personalizado](custom-log-parser.md) para ver las instrucciones de configuración.

    d. Compare el registro con el ejemplo del formato de registro esperado. Si el formato del archivo de registro no coincide con este ejemplo, debe agregar el origen de datos como **Otro**.

    e. Establezca el **tipo de receptor** en **FTP**, **FTPS**, **Syslog – UDP**, **Syslog – TCP** o **Syslog – TLS**.
    >[!NOTE]
    >La integración con protocolos de transferencia segura (FTPS y Syslog – TLS) a menudo requiere una configuración adicional o firewall/proxy.

    f. Repita este proceso para cada servidor proxy y firewall cuyos registros se puedan usar para detectar tráfico en la red.

3.  Vaya a la pestaña **Recopiladores de registros** de la parte superior.

    a. Haga clic en **Agregar recopilador de registros**.

    b. Ponga **nombre** al recopilador de registros.

    c. Escriba la **dirección IP de host** de la máquina que usará para implementar Docker.

    d. Seleccione todos los **orígenes de datos** que desea conectar al recopilador y haga clic en **Actualizar** para guardar la configuración. Luego, consulte los pasos de implementación siguientes.

    ![ubuntu2](./media/ubuntu2.png)

    >  [!NOTE]
    > - Un único recopilador de registros puede administrar varios orígenes de datos.
    >- Copie el contenido de la pantalla, ya que necesitará la información al configurar el recopilador de registros para comunicarse con Cloud App Security. Si ha seleccionado Syslog, esta información incluirá información sobre el puerto en el que escucha el agente de escucha de Syslog.

4.  Aparecerá más información de implementación.

 ![ubuntu3](./media/ubuntu3.png)

5.  **Copie** el comando de ejecución desde el cuadro de diálogo. Puede usar el icono Copiar al Portapapeles ![icono Copiar al Portapapeles](./media/copy-icon.png).

6.  **Exporte** la configuración de origen de datos esperada. Esta configuración describe cómo debe establecer la exportación de registro en los dispositivos.

  ![ubuntu4](./media/ubuntu4.png)

### <a name="step-2--on-premises-deployment-of-your-machine"></a>Paso 2: Implementación local de la máquina

> [!Note]
> En los pasos siguientes se describe la implementación de Ubuntu. Los pasos de implementación en otras plataformas son ligeramente diferentes.

1.  Abra un terminal en la máquina Ubuntu.

2.  Cambie a los privilegios raíz con el comando: `sudo -i`

3.  Desinstale las versiones anteriores e instale Docker CE con el comando siguiente:

    `curl -o /tmp/MCASInstallDocker.sh
    https://adaprodconsole.blob.core.windows.net/public-files/MCASInstallDocker.sh
    && chmod +x /tmp/MCASInstallDocker.sh; sudo /tmp/MCASInstallDocker.sh`

    ![ubuntu5](./media/ubuntu5.png)

4.  Implemente la imagen del recopilador con el comando de ejecución que se generó en el portal.

    ![ubuntu6](./media/ubuntu6.png)

    >[!NOTE]
    >Si necesita configurar un proxy, agregue la dirección IP del proxy y el puerto. Por ejemplo, si los detalles de proxy son 192.168.10.1:8080, el comando de ejecución actualizado es:<br></br>
     `sudo docker run --name MyLogCollector -p 21:21 -p 20000-20099:20000-20099 -e
    "PUBLICIP='192.168.1.1'" -e "PROXY=192.168.10.1:8080" -e
    "TOKEN=41f8f442c9a30519a058dd3bb9a19c79eb67f34a8816270dc4a384493988863a" -e
    "CONSOLE=tenant2.eu1-rs.adallom.com" -e "COLLECTOR=MyLogCollector" --security-opt
    apparmor:unconfined --cap-add=SYS_ADMIN -dt microsoft/caslogcollector starter`

    ![ubuntu7](./media/ubuntu7.png)

5.  Ejecute el comando siguiente para comprobar si el recopilador se ejecuta correctamente: `docker logs \<collector_name\>`

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
[Trabajar con datos de Cloud Discovery](working-with-cloud-discovery-data.md)  
[Para obtener soporte técnico, visite la página de soporte técnico asistido de Cloud App Security](http://support.microsoft.com/oas/default.aspx?prid=16031)  
[Los clientes Premier también pueden elegir Cloud App Security directamente desde el Portal Premier](https://premier.microsoft.com/)

