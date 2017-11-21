---
title: "Configurar la carga de registros automática para informes continuos en Cloud App Security | Microsoft Docs"
description: "En este tema se proporciona información sobre cómo cargar registros para crear informes de Cloud Discovery automáticos."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 11/12/2017
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: c4123272-4111-4445-b6bd-2a1efd3e0c5c
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 057de59d0688b28ca9f9265ff7b4010ae9b3c3aa
ms.sourcegitcommit: 7e0d28b1ac39f7e44e258ab2a0d9563b8fd2aba6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/13/2017
---
# <a name="configure-automatic-log-upload-for-continuous-reports-on-a-virtual-appliance"></a>Configuración de la carga de registros automática para informes continuos en una aplicación virtual

> [!WARNING] 
> Es muy recomendable configurar la carga de registros mediante [Docker](discovery-docker.md) para una implementación más flexible.

## <a name="technical-requirements"></a>Requisitos técnicos
- Hipervisor: Hyper-V o VMware
- Espacio en disco: 250 GB
- CPU: 2
- RAM: 4 GB 
- Configuración del firewall: 
    - Permitir que el recopilador de registros reciba tráfico entrante de FTP y Syslog
    - Permitir que el recopilador de registros inicie tráfico saliente al portal (por ejemplo, contoso.cloudappsecurity.com) en el puerto 443

> [!NOTE]
> Si el firewall requiere una lista de acceso de dirección IP estática y no admite la creación de listas blancas basada en direcciones URL, permita que el recopilador de registros enrute el tráfico saliente hacia los [intervalos IP del centro de datos de Microsoft Azure a través del puerto 443](https://www.microsoft.com/download/details.aspx?id=41653&751be11f-ede8-5a0c-058c-2ee190a24fa6=True).

## <a name="log-collector-performance"></a>Rendimiento del recopilador de registros
El recopilador de registros puede manejar correctamente una capacidad de registros de hasta 50 GB por hora.
Los principales cuellos de botella del proceso de recopilación de registros son:
- Ancho de banda de red: el ancho de banda de red determina la velocidad de carga de registros.
- Rendimiento de E/S de la máquina virtual asignada por TI: determina la velocidad a la que se escriben los registros en el disco del recopilador de registros.
El recopilador de registros tiene un mecanismo de seguridad integrado que supervisa la velocidad a la que llegan los registros y la compara con la velocidad de carga. En caso de congestión, el recopilador de registros comienza a quitar archivos de registro. Si la configuración normalmente supera los 50 GB por hora, se recomienda dividir el tráfico entre varios recopiladores de registros.

## <a name="set-up-and-configuration"></a>Establecimiento y configuración  
  
### <a name="step-1--web-portal-configuration-define-data-sources-and-link-them-to-a-log-collector"></a>Paso 1: Configuración del portal web: definición de orígenes de datos y vinculación a un recopilador de registros  
  
1.  Vaya a la página de configuración de carga automatizada:  
    En el portal de Cloud App Security, haga clic en el icono de configuración ![icono de configuración](./media/settings-icon.png "icono de configuración") y, después, en **Recopiladores de registros**.  
  
3.  Cree un origen de datos coincidente para cada firewall o servidor proxy desde el que quiera cargar registros:  
  
    a.  Haga clic en **Agregar origen de datos**.  
  
    b.  **Ponga nombre** al servidor proxy o firewall.  
  
    c.  Seleccione el dispositivo en la lista **Origen**. Si selecciona **Formato de los registros personalizados** para trabajar con un dispositivo de red que no aparezca en la lista, consulte el artículo sobre cómo [trabajar con el analizador de registro personalizado](custom-log-parser.md) para ver las instrucciones de configuración.
  
    d.  Compare el registro con el ejemplo del formato de registro esperado. Si el formato del archivo de registro no coincide con este ejemplo, debe agregar el origen de datos como **Otro**.  
  
    e.  Establezca el valor de **Tipo de receptor** en **FTP** o **Syslog**. Para **Syslog**, seleccione **UDP** o **TCP**.  
  
    f.  Repita este proceso para cada servidor proxy y firewall cuyos registros se puedan usar para detectar tráfico en la red.  
  
4.  Vaya a la pestaña **Recopiladores de registros** de la parte superior.  
  
    a.  Haga clic en **Agregar recopilador de registros**.  
  
    b.  Ponga **nombre** al recopilador de registros.  
  
    c.  Seleccione todos los **orígenes de datos** que desea conectar al recopilador y haga clic en **Actualizar** para guardar la configuración y generar un token de acceso.  
![orígenes de datos de detección](./media/discovery-data-sources.png)
  
  > [!NOTE] 
  > - Un único recopilador de registros puede administrar varios orígenes de datos.
  > - Copie el contenido de la pantalla, ya que lo usará al configurar el recopilador de registros para comunicarse con Cloud App Security. Si ha seleccionado Syslog, esta información incluye los datos sobre el puerto en el que escucha el agente de escucha de Syslog.
4.  Si acepta los [términos de licencia de usuario final](https://go.microsoft.com/fwlink/?linkid=862492), **descargue** una nueva máquina virtual del recopilador de registros; para ello, haga clic en Hyper-V o VMWare. A continuación, descomprima el archivo con la contraseña que ha recibido en el portal.  
  
### <a name="step-2--on-premises-deployment-of-the-virtual-machine-and-network-configuration"></a>Paso 2: Implementación local de la máquina virtual y la configuración de red   

> [!NOTE] 
> En los pasos siguientes se describe la implementación de Hyper-V. Los pasos de implementación para el hipervisor de la máquina virtual son ligeramente diferentes.  

1.  Abra el Administrador de Hyper-V.  
  
2.  Seleccione **Nuevo** y luego **Máquina virtual** y haga clic en **Siguiente**.  
 ![detección de máquina virtual de Hyper-V](./media/discovery-hyperv-virtual-machine.png "detección de máquina virtual de Hyper-V")  
  
3.  Proporcione un **Nombre** para la nueva máquina virtual, por ejemplo, CloudAppSecurityLogCollector01. Luego haga clic en **Siguiente**.  
  
4.  Seleccione **Generación 1** y haga clic en **Siguiente**.  
  
5.  Cambie la **Memoria de inicio** a **4096 MB**.  
        
6. Active **Usar la memoria dinámica para esta máquina virtual** y haga clic en **Siguiente**.  
  
7.  Si está disponible, seleccione la red **Conexión** y haga clic en **Siguiente**.  
  
8.  Seleccione **Usar un disco duro virtual existente** y luego el archivo **.vhd** incluido en el archivo ZIP que ha descargado.  
  
9.  Haga clic en **Siguiente** y, después, en **Finalizar**.  
    La máquina se agrega al entorno de Hyper-V.  
  
9. Haga clic en la máquina en la tabla **Máquinas virtuales** y luego en **Iniciar**.   
  
10. Conéctese a la máquina virtual del recopilador de registros para ver si se le ha asignado una dirección DHCP. Para ello, haga clic en la máquina virtual y seleccione **Conectar**. Debería ver el mensaje de inicio de sesión. Si ve una dirección IP, puede conectarse a la máquina virtual mediante una herramienta SSH o terminal.  Si no ve una dirección IP, inicie sesión mediante las herramientas de conexión de Hyper-V o VMware con las credenciales que copió al crear el recopilador de registros anteriormente. Puede cambiar la contraseña y configurar la máquina virtual con la utilidad de configuración de red mediante la ejecución del comando siguiente:
```
sudo network_config
```
> [!NOTE]
> La máquina virtual está preconfigurada para obtener una dirección IP de un servidor DHCP. Si necesita configurar direcciones IP estáticas, una puerta de enlace predeterminada, un nombre de host, servidores DNS y NTPS, puede usar la utilidad **network_config** o realizar los cambios manualmente.


En este punto, el recopilador de registros debería estar conectado a la red y ser capaz de acceder al portal de Cloud App Security.  

### <a name="step-3--on-premises-configuration-of-the-log-collection"></a>Paso 3: Configuración local de la recopilación de registros 
Para iniciar sesión por primera vez en el recopilador de registros e importar la configuración de dicho recopilador desde el portal, debe hacer lo siguiente. 

1.  Inicie sesión en el recopilador de registros a través de SSH con las credenciales de administrador interactivas proporcionadas en el portal. (Si es la primera vez que inicia sesión en la consola, deberá cambiar la contraseña y volver a iniciar sesión después de cambiarla. Si está usando una sesión de terminal, podría tener que reiniciar la sesión )
2.  Ejecute la utilidad de configuración del recopilador con el token de acceso que se le proporcionó al crear el recopilador de registros.```sudo collector_config <access token> ```
3. Escriba el dominio de la consola, por ejemplo: ```contoso.portal.cloudappsecurity.com```. Está disponible en la dirección URL que aparece después de iniciar sesión en el portal de Cloud App Security. 

4. Escriba el nombre del recopilador de registros que quiere configurar, por ejemplo: **CloudAppSecurityLogCollector01** o **NewYork** en la imagen anterior.

5.  Importe la configuración del recopilador de registros desde el portal de este modo:  
  
      a.  Inicie sesión en el recopilador de registros a través de SSH con las credenciales de administrador interactivas proporcionadas en el portal.  
  
      b.  Ejecute la utilidad de configuración del recopilador con el token de acceso proporcionado en el comando ```sudo collector_config \<access token>```  
     
      c.  Escriba el dominio de la consola, por ejemplo: ``` contoso.portal.cloudappsecurity.com ```
  
      d. Escriba el nombre del recopilador de registros que quiere configurar, por ejemplo:``` CloudAppSecurityLogCollector01  ```

### <a name="step-4---on-premises-configuration-of-your-network-appliances"></a>Paso 4: Configuración local de los dispositivos de red

Configure los firewalls y los servidores proxy de la red de modo que exporten periódicamente los registros al puerto Syslog dedicado del directorio FTP según las instrucciones del cuadro de diálogo, por ejemplo:  
  
     `London Zscaler - Destination path: 614`  
  
     BlueCoat_HQ - Destination path: \<<machine_name>>\BlueCoat_HQ\  
  
### <a name="step-5---verify-the-successful-deployment-in-the-cloud-app-security-portal"></a>Paso 5: Comprobación de la implementación correcta en el portal Cloud App Security

Compruebe el estado del recopilador en la tabla **Recopilador de registros** y asegúrese de que el estado es **Conectado**. Si es **Creado**, es posible que la conexión y el análisis del recopilador de registros no se hayan completado.

![estado del recopilador de registros](./media/log-collector-status.png)

Vaya al registro de gobierno y comprobar que los registros se están cargando periódicamente en el portal.  
  
Si tiene problemas durante la implementación, consulte [Solución de problemas de Cloud Discovery](troubleshooting-cloud-discovery.md).

### <a name="optional---create-custom-continuous-reports"></a>Opcional: crear informes continuos personalizados

Después de comprobar que los registros se cargan en Cloud App Security y que se generan los informes, puede crear informes personalizados. Ahora puede crear informes de detección personalizados en función de los grupos de usuarios de Azure Active Directory. Por ejemplo, si quiere ver el uso de la nube por parte del departamento de marketing, puede importar el grupo de marketing mediante la característica para importar grupos de usuarios y, después, crear un informe personalizado para este grupo. También puede personalizar un informe en función de la etiqueta de dirección IP o los intervalos de direcciones IP.

1. En el portal de Cloud App Security, en el engranaje de configuración, seleccione **Cloud Discovery settings** (Configuración de Cloud Discovery) y **Administrar informes continuos**. 
2. Haga clic en el botón **Crear informe** y rellene los campos.
3. En **Filtros**, puede filtrar los datos por origen de datos, por [grupo de usuarios importados](user-groups.md) o por [etiquetas e intervalos de direcciones IP](ip-tags.md). 

> [!NOTE]
> Todos los informes personalizados se limitan a un máximo de 1 GB de datos sin comprimir. Si hay más de 1 GB de datos, se exportará el primer GB de datos en el informe.

![Informe continuo personalizado](./media/custom-continuous-report.png)

## <a name="see-also"></a>Consulte también  
[Trabajo con datos de Cloud Discovery](working-with-cloud-discovery-data.md)   
[Para obtener soporte técnico, visite la página de soporte técnico asistido de Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Los clientes Premier también pueden elegir Cloud App Security directamente desde el Portal Premier.](https://premier.microsoft.com/)  
    
      
  