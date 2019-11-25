---
title: Set up your organization's settings in Cloud App Security
description: En este artículo se explica cómo proporcionar información sobre su organización en Cloud App Security.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 11/01/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 2708e8606e1838678e7d2b66fcb4e32584d475fc
ms.sourcegitcommit: 094bb42a198fe733cfd3aec79d74487672846dfa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/24/2019
ms.locfileid: "74458751"
---
# <a name="basic-setup-for-cloud-app-security"></a>Configuración básica de Cloud App Security

*Se aplica a: Microsoft Cloud App Security*

En el siguiente procedimiento se proporcionan instrucciones para personalizar el portal de Microsoft Cloud App Security.

## <a name="prerequisites"></a>Requisitos previos

For portal access, it's necessary to add the following IP addresses to your Firewall's allow list to provide access for the Cloud App Security portal:

* 104.42.231.28

For US Government GCC High customers, it's also necessary to add the following IP addresses to your Firewall’s allow list to provide access for the Cloud App Security GCC High portal:

* 52.227.143.223
* 13.72.19.4

> [!NOTE]
> Para obtener actualizaciones cuando las direcciones URL y las direcciones IP cambien, suscríbase al RSS como se explica en: [URL de Office 365 e intervalos de direcciones IP](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2).

## <a name="set-up-the-portal"></a>Configurar el portal

1. In the Cloud App Security portal, in the menu bar, click the settings cog ![settings icon](./media/settings-icon.png "icono de configuración") and select **Settings** to configure your organization's details.

1. En **Detalles de la organización**, es importante que indique un **nombre para mostrar de la organización** para su organización. Este nombre se mostrará en los correos electrónicos y páginas web enviados desde el sistema.

1. Proporcione un **Nombre del entorno** (inquilino). Esta información es especialmente importante si administra más de un inquilino.

1. También se puede proporcionar un **logotipo**, que se mostrará en las notificaciones de correo electrónico y en las páginas web enviadas desde el sistema. El logotipo tiene que ser un archivo .png con un tamaño máximo de 150x50 píxeles con fondo transparente.

1. Asegúrese de incluir una lista de los **dominios administrados**. La adición de dominios administrados es un paso fundamental. Cloud App Security usa los dominios administrados para determinar qué usuarios son internos y cuáles son externos, así como dónde se deben compartir archivos y dónde no. Esta información se usa para los informes y las alertas.

    * Los usuarios en dominios que no están configurados como internos se marcan como externos. Los usuarios externos no se analizan en busca de actividades o archivos.

1. Under **Auto sign out**, specify the amount of time a session can remain inactive before the session is automatically signed out.

1. Si está integrando mediante la integración de Azure Information Protection, vea [Integración de Azure Information Protection](azip-integration.md) para obtener información.

    * Para trabajar con la integración de Azure Information Protection, primero debe habilitar el [conector de aplicaciones para Office 365](connect-office-365-to-microsoft-cloud-app-security.md).

1. If you're integrating with Azure Advanced Threat Protection integration, see [Azure Advanced Threat Protection Integration](azip-integration.md) for information.

1. Si, en un momento determinado, quiere hacer una copia de seguridad de la configuración del portal, puede hacerlo en esta pantalla. Haga clic en **Exportar configuración del portal** para crear un archivo .json con todas las opciones de configuración del portal, incluidas las reglas de directivas, los grupos de usuarios y los intervalos de direcciones IP.

> [!NOTE]
> Si utiliza ExpressRoute, Cloud App Security se ha implementado en Azure y está totalmente integrado con [ExpressRoute](https://azure.microsoft.com/documentation/articles/expressroute-introduction/). Todas las interacciones con las aplicaciones de Cloud App Security y el tráfico enviado a Cloud App Security, incluida la carga de registros de detección, se enrutan a través del **emparejamiento público** de ExpressRoute para mejorar la latencia, el rendimiento y la seguridad. No hay ningún paso de configuración necesario en el lado cliente.
>
> Para obtener más información sobre el emparejamiento público, consulte [Circuitos ExpressRoute y dominios de enrutamiento](https://azure.microsoft.com/documentation/articles/expressroute-circuit-peerings/).

## <a name="next-steps"></a>Pasos siguientes

[Configurar Cloud Discovery](set-up-cloud-discovery.md)

[!INCLUDE [Open support ticket](includes/support.md)]
