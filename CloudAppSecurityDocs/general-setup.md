---
title: "Proporcionar la configuración de la organización en el portal de Cloud App Security para obtener los mejores resultados | Microsoft Docs"
description: "En este artículo se explica cómo proporcionar información sobre su organización en Cloud App Security."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 1/31/2018
ms.topic: get-started-article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: 2e7e57b0-db54-4d75-896c-4700dd9abe48
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: e5b3647abff4edfb5dbc2c1d38ce322011da901a
ms.sourcegitcommit: bfe898e82c195981cc2fdaa899b0f8ab48957a00
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/05/2018
---
# <a name="basic-setup"></a>Configuración básica
En el siguiente procedimiento se proporcionan instrucciones para personalizar el portal de Cloud App Security.

## <a name="prerequisites"></a>Requisitos previos 
Para acceder al portal de Cloud App Security, deberá agregar las direcciones IP siguientes a la lista de admitidas del firewall:  
  
- 104.42.231.28  
  
> [!NOTE]  
>  Para obtener actualizaciones cuando las direcciones URL y las direcciones IP cambien, suscríbase al RSS como se explica en: [URL de Office 365 e intervalos de direcciones IP](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2).  
  
## <a name="set-up-the-portal"></a>Configurar el portal  
  
1.  En la barra de menús del portal de Cloud App Security, haga clic en el icono de configuración ![icono de configuración](./media/settings-icon.png "icono de configuración") y seleccione **Configuración general** para configurar lo siguiente:  
     
     ![configuración general](./media/general-settings.png "configuración general")  
  
3.  En **Detalles de la organización**, es importante que indique un **nombre para mostrar de la organización** para su organización. Este nombre se mostrará en los correos electrónicos y páginas web enviados desde el sistema.  
  
4. Proporcione un **Nombre del entorno** (inquilino). Esto es especialmente importante si administra varios inquilinos.  
  
4. También se puede proporcionar un **logotipo**, que se mostrará en las notificaciones de correo electrónico y en las páginas web enviadas desde el sistema. El logotipo tiene que ser un archivo .png con un tamaño máximo de 150x50 píxeles con fondo transparente.  

4.  Asegúrese de incluir una lista de los **dominios administrados**. Este paso es fundamental porque Cloud App Security usa los dominios administrados para determinar qué usuarios son internos y cuáles son externos, así como dónde se deben compartir archivos y dónde no. Esto se usa en los informes y de cara a las alertas.  
> [!NOTE] 
> - Los usuarios de dominios que no estén configurados como internos se marcarán como externos y no se examinarán en busca de actividades o archivos.

5. Si está integrando mediante la integración de Azure Information Protection, vea [Integración de Azure Information Protection](azip-integration.md) para obtener información. 

 >[!NOTE]
 > Para trabajar con la integración de Azure Information Protection, primero debe habilitar el [conector de aplicaciones para Office 365](connect-office-365-to-microsoft-cloud-app-security.md).
  
6.  Si, en un momento determinado, quiere hacer una copia de seguridad de la configuración del portal, puede hacerlo en esta pantalla. Haga clic en **Exportar configuración del portal** para crear un archivo .json con todas las opciones de configuración del portal, incluidas las reglas de directivas, los grupos de usuarios y los intervalos de direcciones IP.  
  
   
> [!NOTE] 
> Si utiliza ExpressRoute, Cloud App Security se ha implementado en Azure y está totalmente integrado con [ExpressRoute](https://azure.microsoft.com/documentation/articles/expressroute-introduction/). Todas las interacciones con las aplicaciones de Cloud App Security y el tráfico enviado a Cloud App Security, incluida la carga de registros de detección, se enrutan a través del **emparejamiento público** de ExpressRoute para mejorar la latencia, el rendimiento y la seguridad. No hay ningún paso de configuración necesario en el lado cliente. <br></br>Para obtener más información sobre el emparejamiento público, vea [Circuitos ExpressRoute y dominios de enrutamiento](https://azure.microsoft.com/documentation/articles/expressroute-circuit-peerings/).  
    
## <a name="see-also"></a>Consulte también  
[Configurar Cloud Discovery](set-up-cloud-discovery.md)   

[Los clientes Premier también pueden elegir Cloud App Security directamente desde el Portal Premier.](https://premier.microsoft.com/)  
  
  