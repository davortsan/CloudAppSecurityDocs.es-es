---
title: Requisitos de red de Cloud App Security | Microsoft Docs
description: En este tema se describen las direcciones IP y los puertos que debe abrir para trabajar con Cloud App Security.
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 8/27/2017
ms.topic: get-started-article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: 4de606f2-a09e-4e48-a578-e223de8b5e69
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: dac230e191c7c2d8159a2f373e6ef939fdd841a4
ms.sourcegitcommit: c3fda43ef6fe0d15f0eb9ea23a6f245bad8c371b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/27/2017
---
# <a name="network-requirements"></a>Requisitos de red

En este tema se incluye una lista de los puertos y las direcciones IP que debe permitir e incluir en la lista de admitidos para trabajar con Cloud App Security. 


## <a name="portal-access"></a>Acceso al portal

Para acceder al portal de Cloud App Security, debe agregar las direcciones IP siguientes a la lista de admitidas del firewall:  
  
104.42.231.28  


## <a name="app-connector-access"></a>Acceso al conector de la aplicación

Si quiere que Cloud App Security pueda acceder a ciertas aplicaciones de terceros, es posible que deba agregar las direcciones IP siguientes a la lista de admitidas para que Cloud App Security recopile registros y proporcione acceso a su consola:  
  
104.209.35.177  
13.91.98.185 40.118.211.172 13.93.216.68 13.91.61.249 13.93.233.42 13.64.196.27 13.64.198.97 13.64.199.41 13.64.198.19

> [!NOTE]
>Puede que vea estas direcciones IP en los registros de actividad del proveedor, ya que Cloud App Security realiza acciones de gobierno y exámenes desde ellas. 
  

## <a name="siem-agent-and-log-collector"></a>Agente SIEM y recopilador de registros

Para permitir que Cloud App Security pueda conectarse a su SIEM y que su recopilador de registros pueda ejecutarse, debe abrir los elementos siguientes:

- Puerto de salida 443 para 104.42.231.28

## <a name="external-dlp-integration"></a>Integración de DLP externa

Para que Cloud App Security envíe datos a través de Stunnel al servidor ICAP, abra el firewall de red perimetral a las direcciones IP externas que usa Cloud App Security con un número de puerto de origen dinámico. 

1.  Direcciones de origen: estas direcciones deben incluirse en la lista de admitidas como se detalla anteriormente para las aplicaciones de conector de la API de terceros
2.  Puerto TCP de origen: dinámico
3.  Direcciones de destino: una o dos direcciones IP del servidor Stunnel conectado al servidor ICAP externo
4.  Puerto TCP de destino: según se defina en su red

> [!NOTE] 
> El número de puerto de Stunnel está establecido de forma predeterminada en 11344. Si es necesario, puede cambiarlo y usar otro, pero no olvide anotar el número de puerto nuevo.



  
## <a name="see-also"></a>Consulte también  
[Actividades diarias para proteger el entorno de nube](daily-activities-to-protect-your-cloud-environment.md)   
[Para obtener soporte técnico, visite la página de soporte técnico asistido de Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Los clientes Premier también pueden elegir Cloud App Security directamente desde el Portal Premier.](https://premier.microsoft.com/)  
  

   