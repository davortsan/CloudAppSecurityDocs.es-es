---
title: Requisitos de red de Cloud App Security | Microsoft Docs
description: En este tema se describen las direcciones IP y los puertos que debe abrir para trabajar con Cloud App Security.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 11/5/2018
ms.topic: conceptual
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 4de606f2-a09e-4e48-a578-e223de8b5e69
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: a3c955a037f7ea81e0a06e673fd18030c0cbbf9b
ms.sourcegitcommit: 3253c98f1bf2fafc2578a87ee2db9698caa05c5b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/07/2018
ms.locfileid: "51265331"
---
*Se aplica a: Microsoft Cloud App Security*


# <a name="network-requirements"></a>Requisitos de red

En este tema se incluye una lista de los puertos y las direcciones IP que debe permitir e incluir en la lista de permitidos para trabajar con Microsoft Cloud App Security. 


## <a name="view-your-data-center"></a>Consultar el centro de datos

Algunos de los siguientes requisitos dependen del centro de datos al que esté conectado. 

Para saber a qué centro de datos se está conectando:

1. En el portal de Cloud App Security, haga clic en **?** en la barra de menú y seleccione **Acerca de**. 

    ![clic en Acerca de](./media/about-menu.png)

2. En la pantalla de versión de Cloud App Security, podrá ver la región y el centro de datos.

    ![Consultar el centro de datos](./media/data-center.png)

## <a name="portal-access"></a>Acceso al portal

Para tener acceso al portal de Cloud App Security, agregue a la lista de permitidos del firewall el **puerto de salida 443** de los siguientes nombres DNS y direcciones IP:  

    portal.cloudappsecurity.com
    *.portal.cloudappsecurity.com
    cdn.cloudappsecurity.com
    https://adaproddiscovery.azureedge.net 
    *.s-microsoft.com
    *.msecnd.net
    dev.virtualearth.net
    *.cloudappsecurity.com
    flow.microsoft.com
    static2.sharepointonline.com
    dc.services.visualstudio.com
    *.blob.core.windows.net

Además, estos deben estar en una lista blanca, según el centro de datos que use:
> [!div class="mx-tableFixed"]
> 
> |Centro de datos|Direcciones IP|Nombre DNS|
> |----|----|----|
> |EE.UU.|13.80.125.22<br></br>52.183.75.62<br></br>13.91.91.243|\*.us.portal.cloudappsecurity.com|
> |US2|13.80.125.22<br></br>52.183.75.62<br></br>52.184.165.82|\*.us2.portal.cloudappsecurity.com<br></br>|
> |US3|13.80.125.22<br></br>52.183.75.62<br></br>40.90.218.198<br></br>40.90.218.196|*.us3.portal.cloudappsecurity.com<br></br>|
> |EU|13.80.125.22<br></br>52.183.75.62<br></br>52.174.56.180|\*.eu.portal.cloudappsecurity.com<|
> |EU2|13.80.125.22<br></br>52.183.75.62<br></br>40.81.156.154<br></br>40.81.156.156|*.eu2.portal.cloudappsecurity.com|


> 
> [!NOTE]
> En lugar de un carácter comodín (\*), puede abrir solo la dirección URL del inquilino específico, por ejemplo, de acuerdo con la captura de pantalla anterior, puede abrir: mod244533.us.portal.cloudappsecurity.com

## <a name="siem-agent-connection"></a>Conexión del agente SIEM

Para permitir que Cloud App Security se conecte a su SIEM, agregue a la lista de permitidos del firewall el **puerto de salida 443** de las siguientes direcciones IP:  


> [!div class="mx-tableFixed"]
> 
> |Centro de datos|Direcciones IP|  
> |----|----|
> |EE.UU.|13.91.91.243|
> |US2|52.184.165.82|
> |US3|40.90.218.198<br>40.90.218.196|
> |EU|52.174.56.180|
> |EU2|40.81.156.154<br>40.81.156.156|

Si no ha especificado ningún proxy al configurar el agente SIEM de Cloud App Security, debe permitir las conexiones HTTP a http://ocsp.msocsp.com/ en el puerto 80. Esto sirve para comprobar el estado de revocación de certificado al conectarse al portal de Cloud App Security.

## <a name="app-connector"></a>Conector de la aplicación

Si quiere que Cloud App Security pueda acceder a ciertas aplicaciones de terceros, es posible que se usen las direcciones IP siguientes para que Cloud App Security recopile registros y proporcione acceso a su consola. 

> [!NOTE]
>Puede que vea estas direcciones IP en los registros de actividad del proveedor, ya que Cloud App Security realiza acciones de gobierno y exámenes desde ellas. 

Para conectarse a aplicaciones de terceros, habilite Cloud App Security para permitir la conexión desde estas direcciones IP:


> [!div class="mx-tableFixed"]
> 
> |Centro de datos|Direcciones IP|  
> |----|----|
> |EE.UU.|13.91.91.243 <br></br> 104.209.35.177 <br></br> 13.91.98.185 <br></br> 40.118.211.172 <br></br> 13.93.216.68 <br></br> 13.91.61.249 <br></br> 13.93.233.42 <br></br> 13.64.196.27 <br></br> 13.64.198.97 <br></br> 13.64.199.41 <br></br> 13.64.198.19|
> |US2|52.184.165.82<br></br> 40.84.4.93 <br></br> 40.84.4.119 <br></br> 40.84.2.83 |
> |US3|40.90.218.197<br>40.90.218.203|
> |EU|52.174.56.180<br></br>13.80.22.71<br></br>13.95.29.177<br></br>13.95.30.46|
> |EU2|40.81.156.155<br>40.81.156.153|


## <a name="third-party-dlp-integration"></a>Integración de DLP de terceros

Para que Cloud App Security envíe datos a través de Stunnel al servidor ICAP, abra el firewall de red perimetral a estas direcciones IP con un número de puerto de origen dinámico. 

1.  Direcciones de origen: estas direcciones deben incluirse en la lista de permitidos como se detalla anteriormente para las aplicaciones de conector de la API de terceros
2.  Puerto TCP de origen: dinámico
3.  Direcciones de destino: una o dos direcciones IP del servidor Stunnel conectado al servidor ICAP externo
4.  Puerto TCP de destino: según se defina en su red

> [!NOTE] 
> -  El número de puerto de Stunnel está establecido de forma predeterminada en 11344. Si es necesario, puede cambiarlo y usar otro, pero no olvide anotar el número de puerto nuevo.
> - Puede que vea estas direcciones IP en los registros de actividad del proveedor, ya que Cloud App Security realiza acciones de gobierno y exámenes desde ellas. 

Para conectar aplicaciones de terceros e integrar soluciones de DLP externas, habilite la conexión de Cloud App Security desde estas direcciones IP:

> [!div class="mx-tableFixed"]
> 
> |Centro de datos|Direcciones IP|  
> |----|----|
> |EE.UU.|13.91.91.243 <br></br> 104.209.35.177 <br></br> 13.91.98.185 <br></br> 40.118.211.172 <br></br> 13.93.216.68 <br></br> 13.91.61.249 <br></br> 13.93.233.42 <br></br> 13.64.196.27 <br></br> 13.64.198.97 <br></br> 13.64.199.41 <br></br> 13.64.198.19|
> |US2|52.184.165.82<br></br> 40.84.4.93 <br></br> 40.84.4.119 <br></br> 40.84.2.83 |
> |US3|40.90.218.197<br>40.90.218.203|
> |EU|52.174.56.180<br></br>13.80.22.71<br></br>13.95.29.177<br></br>13.95.30.46|
> |EU2|40.81.156.155<br>40.81.156.153|

## <a name="mail-server"></a>Servidor de correo

Para que las notificaciones se puedan enviar desde la plantilla y la configuración predeterminadas, agregue estas direcciones IP a la lista de permitidos contra el correo no deseado. Las direcciones IP de correo electrónico dedicadas de Cloud App Security son: 

- 65.55.234.192/26
- 207.46.200.0/27
- 65.55.52.224/27
- 94.245.112.0/27
- 111.221.26.0/27
- 207.46.50.192/26

Si quiere personalizar la identidad del remitente de correo electrónico, Microsoft Cloud App Security lo hace posible mediante MailChimp®, un servicio de correo electrónico de terceros. Para que funcione, en el portal de Microsoft Cloud App Security, en **Configuración**, seleccione **Configuración de correo**, lea la declaración de privacidad y los términos de servicio de MailChimp y conceda a Microsoft permiso para utilizar MailChimp en su nombre.

Si no lo hace, las notificaciones de correo electrónico se enviarán con todos los valores predeterminados.

Para trabajar con MailChimp, agregue esta dirección IP a la lista blanca contra el correo no deseado para habilitar el envío de notificaciones: 198.2.134.139 (mail1.cloudappsecurity.com)


## <a name="log-collector"></a>Recopilador de registros 

Para habilitar características de Cloud Discovery por medio de un recopilador de registros y detectar Shadow TI en la organización, es necesario abrir lo siguiente:

- Permita que el recopilador de registros reciba tráfico entrante de FTP y Syslog.
- Permita que el recopilador de registros inicie tráfico saliente al portal (por ejemplo, contoso.cloudappsecurity.com) en el puerto 443.
- Permita que el recopilador de registros inicie tráfico saliente a Azure Blog Storage en el puerto 443:


  | Centro de datos |                        Dirección URL                        |
  |-------------|---------------------------------------------------|
  |     EE.UU.      |   https://adaprodconsole.blob.core.windows.net/   |
  |     US2     | https://prod03use2console1.blob.core.windows.net/ |
  |     US3     |https://prod5usw2console1.blob.core.windows.net/   |
  |     EU      | https://prod02euwconsole1.blob.core.windows.net/  |
  |     EU2     |https://prod4uksconsole1.blob.core.windows.net/    |

> [!NOTE]
> - Si el firewall requiere una lista de acceso de dirección IP estática y no admite la creación de listas de permitidos basadas en direcciones URL, permita que el recopilador de registros enrute el tráfico saliente hacia los [intervalos IP del centro de datos de Microsoft Azure](https://www.microsoft.com/download/details.aspx?id=41653) a través del puerto 443.
>- Permita que el recopilador de registros inicie tráfico saliente al portal de Cloud App Security.
>- Si no ha especificado ningún proxy al configurar el recopilador de registros, debe permitir las conexiones HTTP a http://ocsp.msocsp.com/ en el puerto 80. Esto sirve para comprobar el estado de revocación de certificado al conectarse al portal de Cloud App Security.



## <a name="see-also"></a>Consulte también  
[Actividades diarias para proteger el entorno de nube](daily-activities-to-protect-your-cloud-environment.md)   

[Los clientes Premier también pueden elegir Cloud App Security directamente desde el Portal Premier.](https://premier.microsoft.com/)  

