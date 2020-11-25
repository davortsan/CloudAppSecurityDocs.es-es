---
title: Importación de grupos de usuarios de aplicaciones conectadas en Cloud App Security
description: En este artículo se proporcionan instrucciones para importar grupos de usuarios de aplicaciones conectadas en Cloud App Security.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 11/17/2019
ms.topic: how-to
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: ae8a3383cb1a7c56dae06217c372b2edb6027288
ms.sourcegitcommit: faf7c8f85721dd143ca81c6854ad5c4e8fa50e69
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/25/2020
ms.locfileid: "96025376"
---
# <a name="importing-user-groups-from-connected-apps"></a>Importación de grupos de usuarios de aplicaciones conectadas

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Al conectar aplicaciones mediante conectores de API, Microsoft Cloud App Security permite importar grupos de usuarios de, por ejemplo, Office 365 y Azure Active Directory. Hay dos tipos de grupos de usuarios:

- Grupos automáticos  
Microsoft Cloud App Security crea de manera predeterminada grupos automáticos. Por ejemplo, hay un grupo automático de usuarios denominado **Externos** que combina todos los usuarios de todas las aplicaciones que son externos a la organización y que tienen acceso a archivos o que se encontraban en las actividades de usuario del inquilino. En Cloud App Security existen los siguientes grupos automáticos:

  - Externo
  - Administrador de Dropbox
  - Administrador de Office 365
  - Administrador de G Suite
  - Administrador de Box
  - Todos los perfiles estándar y personalizados de Salesforce, como Administrador del sistema de Salesforce. Vea la lista completa [aquí](https://help.salesforce.com/articleView?id=standard_profiles.htm&language=en&type=0).

- Grupos importados  
Puede importar cualquier grupo de las aplicaciones conectadas. Por ejemplo, puede importar grupos de usuarios de Office 365 (Active Directory) y otras aplicaciones conectadas. Estos grupos le permiten buscar amenazas en la organización, no solo al examinar toda la organización o un usuario específico, sino al examinar un grupo específico.

  Entre los escenarios típicos que usan grupos de usuarios importados se incluyen los siguientes:

  - Investigar qué documentos consulta el personal de RR. HH.
  - Comprobar si sucede algo inusual en el grupo ejecutivo.
  - Comprobar si alguien del grupo de administración ha realizado alguna actividad fuera de Estados Unidos.

## <a name="how-to-import-user-groups"></a>Cómo importar grupos de usuarios

1. En la barra de menús, haga clic en el icono de configuración icono de ![configuración](media/settings-icon.png "icono de configuración") y seleccione **grupos de usuarios**.
1. Haga clic en **Importar grupo de usuarios**.

    ![Importar grupos de usuarios](media/user-groups-add.png)

1. Seleccione la aplicación de la que va a importar el grupo de usuarios. La lista de aplicaciones dependerá de los conectores de aplicaciones implementados.
1. Seleccione el grupo que quiere importar. La lista de grupos disponibles incluirá todos los grupos de usuarios existentes en la aplicación. Si quiere agregar un grupo nuevo, deberá hacerlo directamente en la aplicación. Cuando el grupo aparezca en la lista de aquí, selecciónelo.
1. En función del tamaño del grupo, la importación puede tardar hasta una hora. Puede seleccionar la opción de recibir una notificación por correo electrónico cuando finalice el proceso de importación.
1. Haga clic en **Import**. Después de importar un grupo, Cloud App Security sincroniza automáticamente los miembros del grupo, igual que Active Directory Connect.
1. Una vez finalizada la importación, en la página **Grupos de usuarios** puede hacer clic en un grupo específico para ver una lista de todos los miembros del grupo. Haga clic en cualquier miembro del grupo para explorar en profundidad los detalles de una cuenta específica. Puede ver qué aplicaciones usan y un resumen de la cuenta, incluidos los gráficos del usuario y su actividad.

La importación de grupos le permite seleccionar esos grupos como filtros cuando examine el **registro de actividad** y cuando cree directivas.

> [!NOTE]
>
> - El número máximo de grupos de usuarios importados es 500.
> - Puede haber un breve retraso hasta que los grupos de usuarios importados estén disponibles en los filtros.
> - Para que las actividades se etiqueten como realizadas por un miembro del grupo de usuarios, deberán llevarse a cabo después de la importación de un grupo.
> - Después de la sincronización inicial, los grupos se actualizan cada hora.

Para obtener más información sobre el uso de los filtros de grupo de usuario, vea [Actividades](activity-filters.md).

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Configuración de Cloud Discovery](set-up-cloud-discovery.md)

[!INCLUDE [Open support ticket](includes/support.md)]
