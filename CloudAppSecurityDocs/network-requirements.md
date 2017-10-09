---
title: Requisitos de red de Cloud App Security | Microsoft Docs
description: En este tema se describen las direcciones IP y los puertos que debe abrir para trabajar con Cloud App Security.
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 9/27/2017
ms.topic: get-started-article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: 4de606f2-a09e-4e48-a578-e223de8b5e69
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: a43adb2dfbfce0164384bd9fccb87d602e9eb7b7
ms.sourcegitcommit: 8759541301241e03784c5ac87b56986f22bd0561
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/28/2017
---
# <a name="network-requirements"></a>Requisitos de red

En este tema se incluye una lista de los puertos y las direcciones IP que debe permitir e incluir en la lista blanca para trabajar con Cloud App Security. 

Para obtener información sobre cómo consultar con qué centros de datos de Cloud App Security tiene conexión, consulte [Tokens de API](api-tokens.md).



## <a name="portal-access-siem-agent-authentication-gateway-and-log-collector"></a>Acceso al portal, agente SIEM, puerta de enlace de autenticación y recopilador de registros

Para acceder al portal y a la puerta de enlace de autenticación y permitir que Cloud App Security se conecte a su SIEM, así como para ejecutar el recopilador de registros de Cloud App Security, debe agregar el **puerto de salida 443** para las direcciones IP siguientes a la lista blanca de su firewall:  


> [!div class="mx-tableFixed"]
|Centro de datos|Direcciones IP|  
|----|----|
|Estados Unidos 1|13.91.91.243<br></br>52.183.75.62|
|Unión Europea 1|52.174.56.180<br></br>13.80.125.22|

## <a name="app-connector-access-and-external-dlp-integration"></a>Acceso del conector de la aplicación e integración de DLP externa

Para conectar aplicaciones de terceros e integrar soluciones de DLP externas, habilite la conexión de Cloud App Security a estas direcciones IP:


> [!div class="mx-tableFixed"]
|Centro de datos|Direcciones IP|  
|----|----|
|Estados Unidos 1|104.209.35.177<br></br>13.91.98.185<br></br>40.118.211.172<br></br>13.93.216.68<br></br>13.91.61.249<br></br>13.93.233.42<br></br>13.64.196.27<br></br>13.64.198.97<br></br>13.64.199.41<br></br>13.64.198.19|
|Unión Europea 1|13.80.22.71<br></br>13.95.29.177<br></br>13.95.30.46|


### <a name="app-connector"></a>Conector de la aplicación
Si quiere que Cloud App Security pueda acceder a ciertas aplicaciones de terceros, es posible que se usen las direcciones IP siguientes para que Cloud App Security recopile registros y proporcione acceso a su consola. 

> [!NOTE]
>Puede que vea estas direcciones IP en los registros de actividad del proveedor, ya que Cloud App Security realiza acciones de gobierno y exámenes desde ellas. 
  

### <a name="dlp-integration"></a>Integración de DLP

Para que Cloud App Security envíe datos a través de Stunnel al servidor ICAP, abra el firewall de red perimetral a estas direcciones IP con un número de puerto de origen dinámico. 

1.  Direcciones de origen: estas direcciones deben incluirse en la lista blanca como se detalla anteriormente para las aplicaciones de conector de la API de terceros
2.  Puerto TCP de origen: dinámico
3.  Direcciones de destino: una o dos direcciones IP del servidor Stunnel conectado al servidor ICAP externo
4.  Puerto TCP de destino: según se defina en su red

> [!NOTE] 
> El número de puerto de Stunnel está establecido de forma predeterminada en 11344. Si es necesario, puede cambiarlo y usar otro, pero no olvide anotar el número de puerto nuevo.

## <a name="email-server"></a>Servidor de correo electrónico

La dirección IP de correo electrónico dedicada de Cloud App Security es: 

198.2.134.139 (mail1.cloudappsecurity.com)

Asegúrese de incluir esta dirección IP en la lista blanca del servicio de correo electrónico no deseado para habilitar el envío de notificaciones.
    



  
## <a name="see-also"></a>Consulte también  
[Actividades diarias para proteger el entorno de nube](daily-activities-to-protect-your-cloud-environment.md)   
[Para obtener soporte técnico, visite la página de soporte técnico asistido de Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Los clientes Premier también pueden elegir Cloud App Security directamente desde el Portal Premier.](https://premier.microsoft.com/)  
  

   