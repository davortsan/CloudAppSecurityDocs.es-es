---
title: 'Requisitos de red: Cloud App Security | Microsoft Docs'
description: En este artículo se describen las direcciones IP y los puertos que debe abrir para trabajar con Cloud App Security.
keywords: ''
author: ShlomoSagir-MS
ms.author: shsagir
manager: ShlomoSagir-MS
ms.date: 7/4/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 4de606f2-a09e-4e48-a578-e223de8b5e69
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 7dde86b3ee21ca25510cb7e30ed08452d753aa15
ms.sourcegitcommit: 8fd13c10c2f66a553a8a8fc413555ca837fc9c56
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/07/2019
ms.locfileid: "67610737"
---
# <a name="network-requirements"></a>Requisitos de red

*Se aplica a: Microsoft Cloud App Security*

En este artículo se proporciona una lista de puertos y direcciones IP que necesita para permitir y lista para trabajar con Microsoft Cloud App Security.

## <a name="view-your-data-center"></a>Consultar el centro de datos

Algunos de los siguientes requisitos dependen del centro de datos al que esté conectado. 

Para ver el centro de datos al que se está conectando, siga estos pasos:

1. En el portal de Cloud App Security, haga clic en el **icono de signo de interrogación** en la barra de menús. Después, seleccione **Acerca de**. 

    ![clic en Acerca de](./media/about-menu.png)

2. En la pantalla de versión de Cloud App Security, podrá ver la región y el centro de datos.

    ![Consultar el centro de datos](./media/data-center.png)

## <a name="portal-access"></a>Acceso al portal

Para tener acceso al portal de Cloud App Security, agregue **puerto de salida 443** para la siguiente dirección de IP direcciones y nombres DNS al firewall de la lista de permitidos:  

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

Además, estos elementos deben estar en una lista blanca, según el centro de datos que use:
> [!div class="mx-tableFixed"]
> 
> |Centro de datos|Direcciones IP|Nombre DNS|
> |----|----|----|
> |Estados Unidos 1|13.80.125.22<br>52.183.75.62<br>13.91.91.243|\*.us.portal.cloudappsecurity.com|
> |US2|13.80.125.22<br>52.183.75.62<br>52.184.165.82|\*.us2.portal.cloudappsecurity.com<br>|
> |US3|13.80.125.22<br>52.183.75.62<br>40.90.218.198<br>40.90.218.196|*.us3.portal.cloudappsecurity.com<br>|
> |Unión Europea 1|13.80.125.22<br>52.183.75.62<br>52.174.56.180|\*.eu.portal.cloudappsecurity.com<|
> |EU2|13.80.125.22<br>52.183.75.62<br>40.81.156.154<br>40.81.156.156<br>40.81.152.172|*.eu2.portal.cloudappsecurity.com|


> 
> [!NOTE]
> En lugar de un carácter comodín (\*), puede abrir solo la dirección URL del inquilino específico, por ejemplo, de acuerdo con la captura de pantalla anterior, puede abrir: mod244533.us.portal.cloudappsecurity.com

## <a name="siem-agent-connection"></a>Conexión del agente SIEM

Para habilitar Cloud App Security se conecte a su SIEM, agregue **puerto de salida 443** para la dirección IP siguiente direcciones al firewall de la lista de permitidos:  


> [!div class="mx-tableFixed"]
> 
> |Centro de datos|Direcciones IP|  
> |----|----|
> |Estados Unidos 1|13.91.91.243|
> |US2|52.184.165.82|
> |US3|40.90.218.198<br>40.90.218.196|
> |Unión Europea 1|52.174.56.180|
> |EU2|40.81.156.154<br>40.81.156.156<br>40.81.152.172|

> [!NOTE]
> Si no ha especificado un servidor proxy al configurar el agente SIEM de Cloud App Security, deberá permitir las conexiones http a http://ocsp.msocsp.com/ y ocsp.digicert.com en el puerto 80. Esto sirve para comprobar el estado de revocación de certificado al conectarse al portal de Cloud App Security.

## <a name="app-connector"></a>Conector de la aplicación

Se pueden usar estas direcciones IP para que Cloud App Security pueda acceder a algunas aplicaciones de terceros. Las direcciones IP permiten a Cloud App Security recopilar registros y proporcionan acceso a la consola de Cloud App Security. 

> [!NOTE]
>Puede que vea estas direcciones IP en los registros de actividad del proveedor, ya que Cloud App Security realiza acciones de gobernanza y exámenes desde ellas. 

Para conectarse a aplicaciones de terceros, habilite Cloud App Security para permitir la conexión desde estas direcciones IP:


> [!div class="mx-tableFixed"]
> 
> |Centro de datos|Direcciones IP|  
> |----|----|
> |Estados Unidos 1|13.91.91.243 <br> 104.209.35.177 <br> 13.91.98.185 <br> 40.118.211.172 <br> 13.93.216.68 <br> 13.91.61.249 <br> 13.93.233.42 <br> 13.64.196.27 <br> 13.64.198.97 <br> 13.64.199.41 <br> 13.64.198.19|
> |US2|52.184.165.82<br> 40.84.4.93 <br> 40.84.4.119 <br> 40.84.2.83 |
> |US3|40.90.218.197<br>40.90.218.203|
> |Unión Europea 1|52.174.56.180<br>13.80.22.71<br>13.95.29.177<br>13.95.30.46|
> |EU2|40.81.156.155<br>40.81.156.153<br>40.81.152.172|


## <a name="third-party-dlp-integration"></a>Integración de DLP de terceros

Para permitir que Cloud App Security envíe datos a través de Stunnel al servidor ICAP, abra el firewall de red perimetral a estas direcciones IP con un número de puerto de origen dinámico. 

1. **Direcciones de origen**: estas direcciones deben incluirse en la lista de admitidas como se detalla anteriormente para las aplicaciones de conector de la API de terceros
2. **Puerto TCP de origen**: dinámico
3. **Direcciones de destino**: una o dos direcciones IP del servidor Stunnel conectado al servidor ICAP externo
4. **Puerto TCP de destino**: según se defina en la red

> [!NOTE] 
> -  El número de puerto de Stunnel está establecido de forma predeterminada en 11344. Si es necesario, puede cambiarlo y usar otro, pero no olvide anotar el número de puerto nuevo.
> - Puede que vea estas direcciones IP en los registros de actividad del proveedor, ya que Cloud App Security realiza acciones de gobernanza y exámenes desde ellas.

Para conectar aplicaciones de terceros e integrar soluciones de DLP externas, habilite la conexión de Cloud App Security desde estas direcciones IP:

> [!div class="mx-tableFixed"]
> 
> |Centro de datos|Direcciones IP|  
> |----|----|
> |Estados Unidos 1|13.91.91.243 <br> 104.209.35.177 <br> 13.91.98.185 <br> 40.118.211.172 <br> 13.93.216.68 <br> 13.91.61.249 <br> 13.93.233.42 <br> 13.64.196.27 <br> 13.64.198.97 <br> 13.64.199.41 <br> 13.64.198.19|
> |US2|52.184.165.82<br> 40.84.4.93 <br> 40.84.4.119 <br> 40.84.2.83 |
> |US3|40.90.218.197<br>40.90.218.203|
> |Unión Europea 1|52.174.56.180<br>13.80.22.71<br>13.95.29.177<br>13.95.30.46|
> |EU2|40.81.156.155<br>40.81.156.153<br>40.81.152.172|

## <a name="mail-server"></a>Servidor de correo

Para habilitar las notificaciones se envíen desde la plantilla predeterminada y la configuración, agregue la que lista de permitidos estas direcciones IP para el correo no deseado. Las direcciones IP de correo electrónico dedicadas de Cloud App Security son:

- 65.55.234.192/26
- 207.46.200.0/27
- 65.55.52.224/27
- 94.245.112.0/27
- 111.221.26.0/27
- 207.46.50.192/26

Si quiere personalizar la identidad del remitente de correo electrónico, Microsoft Cloud App Security permite la personalización mediante MailChimp®, un servicio de correo electrónico de terceros. Para facilitar el trabajo en el portal de Microsoft Cloud App Security, vaya a **Configuración**. Seleccione **Configuración de correo** y revise la declaración de privacidad y los términos de servicio de MailChimp. Después, conceda permiso a Microsoft para usar MailChimp en su nombre.

Si no personaliza la identidad del remitente, las notificaciones de correo electrónico se enviarán con todos los valores predeterminados.

Para trabajar con MailChimp, agregue esta dirección IP dirección a la basura Permitir lista habilitar el envío de notificaciones: 198.2.134.139 (mail1.cloudappsecurity.com)

## <a name="log-collector"></a>Recopilador de registros

Para habilitar características de Cloud Discovery por medio de un recopilador de registros y detectar Shadow TI en la organización, abra los siguientes elementos:

- Permita que el recopilador de registros reciba tráfico entrante de FTP y Syslog.
- Permita que el recopilador de registros inicie tráfico saliente al portal (por ejemplo, contoso.cloudappsecurity.com) en el puerto 443.
- Permita que el recopilador de registros inicie tráfico saliente a Azure Blog Storage en el puerto 443:


  | Centro de datos |                        Dirección URL                        |
  |-------------|---------------------------------------------------|
  |     Estados Unidos 1      |   https://adaprodconsole.blob.core.windows.net/   |
  |     US2     | https://prod03use2console1.blob.core.windows.net/ |
  |     US3     |https://prod5usw2console1.blob.core.windows.net/   |
  |     Unión Europea 1      | https://prod02euwconsole1.blob.core.windows.net/  |
  |     EU2     |https://prod4uksconsole1.blob.core.windows.net/    |

> [!NOTE]
> - Si el firewall requiere una lista de acceso de dirección IP estática y no admite la creación de listas de permitidos basadas en direcciones URL, permita que el recopilador de registros enrute el tráfico saliente hacia los [intervalos IP del centro de datos de Microsoft Azure](https://www.microsoft.com/download/details.aspx?id=41653) a través del puerto 443.
>- Permita que el recopilador de registros inicie tráfico saliente al portal de Cloud App Security.
>- Si no ha especificado un servidor proxy al configurar el recopilador de registros, deberá permitir las conexiones http a http://ocsp.msocsp.com/ y ocsp.digicert.com en el puerto 80. Esto sirve para comprobar el estado de revocación de certificado al conectarse al portal de Cloud App Security.

## <a name="next-steps"></a>Pasos siguientes
 
[Actividades diarias para proteger el entorno de nube](daily-activities-to-protect-your-cloud-environment.md)   

[Los clientes Premier también pueden crear una solicitud de soporte técnico directamente en el portal Premier.](https://premier.microsoft.com/)  

