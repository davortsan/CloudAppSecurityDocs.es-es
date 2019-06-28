---
title: Configurar los valores de su organización en Cloud App Security
description: En este artículo se explica cómo proporcionar información sobre su organización en Cloud App Security.
keywords: ''
author: ShlomoSagir-MS
ms.author: ShlomoSagir-MS
manager: ShlomoSagir-MS
ms.date: 6/24/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 2e7e57b0-db54-4d75-896c-4700dd9abe48
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: a05ea9152c0071ee61b9e5037dd00cb1de328da5
ms.sourcegitcommit: ae617f23b36be665439dcedfbcf346715a526d7e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/27/2019
ms.locfileid: "67411809"
---
# <a name="basic-setup-for-cloud-app-security"></a>Configuración básica de Cloud App Security

*Se aplica a: Microsoft Cloud App Security*

En el siguiente procedimiento se proporcionan instrucciones para personalizar el portal de Microsoft Cloud App Security.

## <a name="prerequisites"></a>Requisitos previos 
Para acceder al portal, es necesario agregar las siguientes direcciones IP al Firewall de la lista proporcionar acceso para el portal de Cloud App Security:  
  
- 104.42.231.28  
  
> [!NOTE]  
>  Para obtener actualizaciones cuando las direcciones URL y las direcciones IP cambien, suscríbase al RSS como se explica en: [Intervalos de direcciones IP y URL de Office 365](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2).
  
## <a name="set-up-the-portal"></a>Configurar el portal  
  
1. En la barra de menús del portal de Cloud App Security, haga clic en el icono de configuración ![icono de configuración](./media/settings-icon.png "settings icon") y seleccione **Configuración** para configurar los detalles de la organización.     

1. En **Detalles de la organización**, es importante que indique un **nombre para mostrar de la organización** para su organización. Este nombre se mostrará en los correos electrónicos y páginas web enviados desde el sistema.  
  
1. Proporcione un **Nombre del entorno** (inquilino). Esta información es especialmente importante si administra más de un inquilino.  
  
1. También se puede proporcionar un **logotipo**, que se mostrará en las notificaciones de correo electrónico y en las páginas web enviadas desde el sistema. El logotipo tiene que ser un archivo .png con un tamaño máximo de 150x50 píxeles con fondo transparente.  

1. Asegúrese de incluir una lista de los **dominios administrados**. La adición de dominios administrados es un paso fundamental. Cloud App Security usa los dominios administrados para determinar qué usuarios son internos y cuáles son externos, así como dónde se deben compartir archivos y dónde no. Esta información se usa para los informes y las alertas.  

    - Los usuarios en dominios que no están configurados como internos se marcan como externos. Los usuarios externos no se analizan en busca de actividades o archivos.

1. En **cerrar sesión automática**, especifique la cantidad de tiempo puede permanecer inactiva una sesión antes de la sesión se cerrará automáticamente.

1. Si está integrando mediante la integración de Azure Information Protection, vea [Integración de Azure Information Protection](azip-integration.md) para obtener información. 

    - Para trabajar con la integración de Azure Information Protection, primero debe habilitar el [conector de aplicaciones para Office 365](connect-office-365-to-microsoft-cloud-app-security.md).
  
1. Si está realizando la integración con la integración de protección contra amenazas avanzada de Azure, consulte [Azure Advanced Threat Protection Integration](azip-integration.md) para obtener información.

1. Si, en un momento determinado, quiere hacer una copia de seguridad de la configuración del portal, puede hacerlo en esta pantalla. Haga clic en **Exportar configuración del portal** para crear un archivo .json con todas las opciones de configuración del portal, incluidas las reglas de directivas, los grupos de usuarios y los intervalos de direcciones IP.  
  
> [!NOTE]
> Si utiliza ExpressRoute, Cloud App Security se ha implementado en Azure y está totalmente integrado con [ExpressRoute](https://azure.microsoft.com/documentation/articles/expressroute-introduction/). Todas las interacciones con las aplicaciones de Cloud App Security y el tráfico enviado a Cloud App Security, incluida la carga de registros de detección, se enrutan a través del **emparejamiento público** de ExpressRoute para mejorar la latencia, el rendimiento y la seguridad. No hay ningún paso de configuración necesario en el lado cliente. <br></br>Para obtener más información sobre el emparejamiento público, vea [Circuitos ExpressRoute y dominios de enrutamiento](https://azure.microsoft.com/documentation/articles/expressroute-circuit-peerings/).  

## <a name="next-steps"></a>Pasos siguientes  
[Configurar Cloud Discovery](set-up-cloud-discovery.md)   

[Los clientes Premier también pueden crear una solicitud de soporte técnico directamente en el portal Premier.](https://premier.microsoft.com/)  
