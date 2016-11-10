---
title: "Configurar la carga de registros automática para informes continuos | Microsoft Docs"
description: "En este tema se proporciona información sobre cómo cargar registros para crear informes de Cloud Discovery automáticos."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 10/15/2016
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: c4123272-4111-4445-b6bd-2a1efd3e0c5c
ms.reviewer: reutam
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: ed4ea71b24767d3602d40894d1cbac7447bcd8a2
ms.openlocfilehash: 9672336d69f19875d160eb414bf3ca2c525692e1


---

# <a name="configure-automatic-log-upload-for-continuous-reports"></a>Configurar la carga de registros automática para informes continuos
Antes de configurar la recopilación automática de archivos de registros, compruebe que el registro coincide con el tipo de registro esperado, para asegurarse de que Cloud App Security puede analizar el archivo específico. 

## <a name="technical-requirements"></a>Requisitos técnicos
- Hipervisor: Hyper-V o VMware
- Espacio en disco: 250 GB
- CPU: 2
- RAM: 4 GB 
- Configuración del firewall: 
- Permitir que el recopilador de registros reciba tráfico entrante de FTP y Syslog
- Permitir que el recopilador de registros inicie tráfico saliente al portal (por ejemplo, contoso.cloudappsecurity.com) en el puerto 443

  
## <a name="set-up-automatic-log-file-collection"></a>Configurar recopilación de archivos de registro automática  
  
Los recopiladores de registros permiten automatizar fácilmente la carga de registros desde la red. El recopilador de registros se ejecuta en la red y recibe los registros a través de Syslog o FTP. Cada registro se procesa, se comprime y se transmite automáticamente al portal. Los registros de FTP se cargan en Cloud App Security una vez que el archivo haya finalizado la transferencia FTP al recopilador de registros. En el caso de Syslog, el recopilador de registros escribe los registros recibidos en el disco cada 20 minutos y, después, carga el archivo en Cloud App Security.  La máquina virtual del recopilador de registros está disponible para el hipervisor Hyper-V (formato VHD) y VMware (formato OVF) y necesita 250 GB de espacio en disco, 2 CPU y 4 GB de RAM. 
     
  
     The log collector VHD image can be downloaded and run on Azure servers.  
  
2.  Vaya a la página de configuración de carga automatizada:  
    En el portal de Cloud App Security, haga clic en el icono de configuración ![icono de configuración](./media/settings-icon.png "settings icon") y luego en **Configuración de Cloud Discovery**. Por último, seleccione la pestaña **Cargar registros automáticamente**.  
  
3.  Cree un origen de datos coincidente para cada firewall o servidor proxy desde el que quiera cargar registros:  
  
    1.  Haga clic en **Agregar origen de datos**.  
  
    2.  **Ponga nombre** al servidor proxy o firewall.  
  
    3.  Seleccione el dispositivo en la lista **Origen**.  
  
    4.  Compare el registro con el ejemplo del formato de registro esperado. Si el formato del archivo de registro no coincide con este ejemplo, debe agregar el origen de datos como **Otro**.  
  
    5.  Establezca el valor de **Tipo de receptor** en **FTP** o **Syslog**.  
  
         Para **Syslog**, seleccione **UDP** o **TCP**.  
  
    6.  Repita este proceso para cada servidor proxy y firewall cuyos registros se puedan usar para detectar tráfico en la red.  
  
4.  Vaya a la pestaña **Recopiladores de registros** de la parte superior.  
  
    1.  Haga clic en **Agregar recopilador de registros**.  
  
    2.  Ponga **nombre** al recopilador de registros.  
  
    3.  Seleccione todos los **Orígenes de datos** que quiere conectar al recopilador y haga clic en **Actualizar**.  
  
         > [!NOTE] 
       > Copie el contenido de la pantalla, ya que necesitará la información al configurar el recopilador de registros para comunicarse con Cloud App Security. Si ha seleccionado Syslog, esta información incluirá información sobre el puerto en el que escucha el agente de escucha de Syslog.
         
![orígenes de datos de detección](./media/discovery-data-sources.png)
> [!NOTE] 
         > Un único recopilador de registros puede administrar varios orígenes de datos.
  
4.  **Descargue** una nueva máquina virtual del recopilador de registros. Para ello, haga clic en Hyper-V o VMware y descomprima el archivo con la contraseña que ha recibido en el portal.  
  
## <a name="set-up-your-virtual-machine-in-hyperv"></a>Configurar la máquina virtual en Hyper-V  
  
1.  Abra el Administrador de Hyper-V.  
  
2.  Seleccione **Nuevo** y luego **Máquina virtual** y haga clic en **Siguiente**.  
  
             ![discovery hyperv virtual machine](./media/discovery-hyperv-virtual-machine.png "discovery hyperv virtual machine")  
  
3.  Proporcione un **Nombre** para la nueva máquina virtual, por ejemplo, CloudAppSecurityLogCollector01. Luego haga clic en **Siguiente**.  
  
4.  Seleccione **Generación 1** y haga clic en **Siguiente**.  
  
5.  Cambie la **Memoria de inicio** a **4096 MB**.  
        
6. Active **Usar la memoria dinámica para esta máquina virtual** y haga clic en **Siguiente**.  
  
7.  Si está disponible, seleccione la red **Conexión** y haga clic en **Siguiente**.  
  
8.  Seleccione **Usar un disco duro virtual existente** y luego el archivo .**vhd** incluido en el archivo ZIP que ha descargado.  
  
9.  Haga clic en **Siguiente** y, después, en **Finalizar**.  
  
             The machine will be added to your Hyper-V environment.  
  
9. Haga clic en la máquina en la tabla **Máquinas virtuales** y luego en **Iniciar**.   
  
10. Conéctese a la máquina virtual del recopilador de registros para ver si se le ha asignado una dirección DHCP. Para ello, haga clic en la máquina virtual y seleccione **Conectar**. Debería ver el mensaje de inicio de sesión. Si ve una dirección IP, puede conectarse a la máquina virtual mediante una herramienta SSH o terminal.  Si no ve una dirección IP, inicie sesión mediante las herramientas de conexión de Hyper-V o VMware con las credenciales que copió al crear el recopilador de registros más arriba. Puede cambiar la contraseña y configurar la máquina virtual mediante la ejecución del comando siguiente:
```
sudo network_config
```
> [!NOTE]
> La máquina virtual está preconfigurada para obtener una dirección IP de un servidor DHCP. Si necesita configurar direcciones IP estáticas, una puerta de enlace predeterminada, un nombre de host, servidores DNS y NTPS, puede usar la utilidad **network_config** o realizar los cambios manualmente.


En este punto, el recopilador de registros debería estar conectado a la red y ser capaz de acceder al portal de Cloud App Security.  

## <a name="log-in-and-import"></a>Iniciar sesión e importar 
Para iniciar sesión por primera vez en el recopilador de registros e importar la configuración del recopilador de registros desde el portal, debe hacer lo siguiente. 

1.  Inicie sesión en el recopilador de registros a través de SSH con las credenciales de administrador interactivas proporcionadas en el portal. (Si es la primera vez que inicia sesión en la consola, deberá cambiar la contraseña y volver a iniciar sesión después de cambiar la contraseña. Si está usando una sesión de terminal, podría tener que reiniciar la sesión. )
2.  Ejecute la utilidad de configuración del recopilador con el token de acceso que se le proporcionó al crear el recopilador de registros. 

```
sudo collector_config <access token>
```

3. Escriba el dominio de la consola, por ejemplo:

```
contoso.portal.cloudappsecurity.com
```

Está disponible en la dirección URL que aparece después de iniciar sesión en el portal de Cloud App Security. 
 

4. Escriba el nombre del recopilador de registros que quiere configurar, por ejemplo:

**CloudAppSecurityLogCollector01** o **NewYork** en la imagen anterior.
 
8.  Importe la configuración del recopilador de registros desde el portal de este modo:  
  
      1.  Inicie sesión en el recopilador de registros a través de SSH con las credenciales de administrador interactivas proporcionadas en el portal.  
  
       2.  Ejecute la utilidad de configuración del recopilador con el token de acceso proporcionado en el comando **sudo collector_config \<token de acceso>**.  
  
             Escriba el dominio de la consola, por ejemplo:  
  
             **contoso.portal.cloudappsecurity.com ** 
  
             Escriba el nombre del recopilador de registros que quiere configurar, por ejemplo:  
  
             **CloudAppSecurityLogCollector01**  
  
5.  Configure los firewalls y los servidores proxy de la red de modo que exporten periódicamente los registros al puerto Syslog dedicado del directorio FTP según las instrucciones del cuadro de diálogo, por ejemplo:  
  
     `London Zscaler - Destination path: 614`  
  
     `SF Blue Coat - Destination path: \\CloudAppSecurityCollector01\BlueCoat\`  
  
6.  Use el registro de gobierno para comprobar que los registros se están cargando periódicamente en el portal.  
  
## <a name="log-collector-performance"></a>Rendimiento del recopilador de registros
El recopilador de registros puede manejar correctamente una capacidad de registros de hasta 50 GB por hora.

Los principales cuellos de botella del proceso de recopilación de registros son:
* Ancho de banda de red: el ancho de banda de red determina la velocidad de carga de registros.
* Rendimiento de E/S de la máquina virtual asignada por TI: determina la velocidad a la que se escriben los registros en el disco del recopilador de registros.

El recopilador de registros tiene un mecanismo de seguridad integrado que supervisa la velocidad a la que llegan los registros y la compara con la velocidad de carga. En caso de congestión, el recopilador de registros comienza a quitar archivos de registro. Si la configuración normalmente supera los 50 GB por hora, se recomienda dividir el tráfico entre varios recopiladores de registros.


<!--HONumber=Oct16_HO4-->


