---
title: Configure los valores de la organización en Cloud App Security
description: En este artículo se explica cómo proporcionar información sobre su organización en Cloud App Security.
ms.date: 11/08/2020
ms.topic: how-to
ms.openlocfilehash: e46b7c651d67fbd655d548f9d77228c29794ab74
ms.sourcegitcommit: 1bea874c7531c1926b6e46b96eac00ceeeeb69f2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/07/2020
ms.locfileid: "96749840"
---
# <a name="basic-setup-for-cloud-app-security"></a>Configuración básica de Cloud App Security

[!INCLUDE [Banner for top of topics](includes/banner.md)]

En el siguiente procedimiento se proporcionan instrucciones para personalizar el portal de Microsoft Cloud App Security.

## <a name="prerequisites"></a>Requisitos previos

Para el acceso al portal, es necesario agregar las siguientes direcciones IP a la lista de permitidos del firewall para proporcionar acceso al portal de Cloud App Security:

* 104.42.231.28

En el caso de los clientes de la administración pública de Estados Unidos, también es necesario agregar las siguientes direcciones IP a la lista de permitidos del firewall para proporcionar acceso al portal de Cloud App Security GCC High:

* 52.227.143.223
* 13.72.19.4

> [!NOTE]
> Para obtener actualizaciones cuando las direcciones URL y las direcciones IP cambien, suscríbase al RSS como se explica en: [URL de Office 365 e intervalos de direcciones IP](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2).

## <a name="set-up-the-portal"></a>Configurar el portal

1. En el portal de Cloud App Security, en la barra de menús, haga clic en el icono configuración engranaje ![configuración](media/settings-icon.png "icono de configuración") y seleccione **configuración** para configurar los detalles de su organización.

1. En **Detalles de la organización**, es importante que indique un **nombre para mostrar de la organización** para su organización. Este nombre se mostrará en los correos electrónicos y páginas web enviados desde el sistema.

1. Proporcione un **Nombre del entorno** (inquilino). Esta información es especialmente importante si administra más de un inquilino.

1. También se puede proporcionar un **logotipo**, que se mostrará en las notificaciones de correo electrónico y en las páginas web enviadas desde el sistema. El logotipo tiene que ser un archivo .png con un tamaño máximo de 150x50 píxeles con fondo transparente.

1. Asegúrese de agregar una lista de los **dominios administrados** para identificar a los usuarios internos. La adición de dominios administrados es un paso fundamental. Cloud App Security usa los dominios administrados para determinar qué usuarios son internos y cuáles son externos, así como dónde se deben compartir archivos y dónde no. Esta información se usa para los informes y las alertas.

    * Los usuarios en dominios que no están configurados como internos se marcan como externos. Los usuarios externos no se analizan en busca de actividades o archivos.

1. En **cierre de sesión automático**, especifique la cantidad de tiempo que una sesión puede permanecer inactiva antes de que se cierre la sesión automáticamente.

1. Si está integrando mediante la integración de Azure Information Protection, vea [Integración de Azure Information Protection](azip-integration.md) para obtener información.

    * Para trabajar con la integración de Azure Information Protection, primero debe habilitar el [conector de aplicaciones para Office 365](connect-office-365-to-microsoft-cloud-app-security.md).

1. Si está realizando la integración con Microsoft defender para la integración de identidades, consulte [Microsoft defender para la integración de identidades](azip-integration.md) para obtener información.

1. Si, en un momento determinado, quiere hacer una copia de seguridad de la configuración del portal, puede hacerlo en esta pantalla. Haga clic en **exportar configuración del portal** para crear un archivo JSON de toda la configuración del portal, incluidas las reglas de directivas, los grupos de usuarios y los intervalos de direcciones IP.

> [!NOTE]
> Si utiliza ExpressRoute, Cloud App Security se ha implementado en Azure y está totalmente integrado con [ExpressRoute](/azure/expressroute/expressroute-introduction). Todas las interacciones con las aplicaciones Cloud App Security y el tráfico enviado a Cloud App Security, incluida la carga de registros de detección, se enrutan a través de ExpressRoute para mejorar la latencia, el rendimiento y la seguridad. No hay ningún paso de configuración necesario en el lado cliente.
>
> Para obtener más información sobre el emparejamiento público, vea [Circuitos ExpressRoute y dominios de enrutamiento](/azure/expressroute/expressroute-circuit-peerings).

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Configuración de Cloud Discovery](set-up-cloud-discovery.md)

[!INCLUDE [Open support ticket](includes/support.md)]