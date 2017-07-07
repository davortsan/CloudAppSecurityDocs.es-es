---
title: Conectar aplicaciones para obtener una mayor visibilidad y control con Cloud App Security | Microsoft Docs
description: "En este tema se describe el proceso para conectar aplicaciones con las aplicaciones en la nube de la organización mediante conectores de API."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 7/3/2017
ms.topic: get-started-article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: 7e718d77-aae7-4a3a-8421-5ba7cee7d67c
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: c8c9b63f4265876fc1de6a24c6576f917f9d2278
ms.sourcegitcommit: a0290ac2a662994f7771975ef6c20d0b47e9edd8
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/03/2017
---
Cloud App Security requiere acceso como se indica a continuación para conectarse a la red. 

## <a name="cloud-app-security-system-ip-addresses"></a>Direcciones IP del sistema de Cloud App Security

Cloud App Security usa las siguientes direcciones IP para conectarse a entornos de cliente. Esto es necesario al conectase mediante [ICAP](icap-stunnel.md) y al conectar conectores de aplicaciones. En el caso de algunas aplicaciones, puede que sea necesario agregar las siguientes direcciones IP a la lista blanca para habilitar Cloud App Security de modo que recopile registros y proporcione acceso a la consola de Cloud App Security. En algunas aplicaciones, estas direcciones IP también se pueden usar para identificar actividades de Cloud App Security, como en los registros de auditoría del servicio. 
  
-   Para los registros:  
  
    104.209.35.177  
  
    13.91.98.185
 
    40.118.211.172

    13.93.216.68

    13.91.61.249

    13.93.233.42

    13.64.196.27

    13.64.198.97

    13.64.199.41

    13.64.198.19
  
  
## <a name="cas-portal-url-and-ip-addresses"></a>Dirección URL y direcciones IP del portal de Cloud App Security

Para el acceso de cliente al portal, las conexiones de API al conectarse a las API de Cloud App Security, el recopilador de registros y el agente SIEM se usan la dirección URL, el puerto 443 y las direcciones IP de Cloud App Security. 
  
     104.42.231.28  

 
  
> [!NOTE]  
>  Para obtener actualizaciones cuando las direcciones URL y las direcciones IP cambien, suscríbase al RSS como se explica en: [URL de Office 365 e intervalos de direcciones IP](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2).  
  

  
## <a name="see-also"></a>Consulte también  
[Actividades diarias para proteger el entorno de nube](daily-activities-to-protect-your-cloud-environment.md)   
[Para obtener soporte técnico, visite la página de soporte técnico asistido de Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Los clientes Premier también pueden elegir Cloud App Security directamente desde el Portal Premier.](https://premier.microsoft.com/)  
  

   