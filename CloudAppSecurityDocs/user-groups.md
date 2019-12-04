---
title: Importación de grupos de usuarios de aplicaciones conectadas en Cloud App Security
description: En este artículo se proporcionan instrucciones para importar grupos de usuarios de aplicaciones conectadas en Cloud App Security.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 11/17/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 777e672436220642df6ea739c0f2e381487dd9ee
ms.sourcegitcommit: 7c93b6f93d2699d466b172590710ed01697bbdad
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74720365"
---
# <a name="importing-user-groups-from-connected-apps"></a>Importación de grupos de usuarios de aplicaciones conectadas

*Se aplica a: Microsoft Cloud App Security*

Al conectar aplicaciones mediante conectores de API, Microsoft Cloud App Security permite importar grupos de usuarios de, por ejemplo, Office 365 y Azure Active Directory. Hay dos tipos de grupos de usuarios:

- Grupos automáticos  
Microsoft Cloud App Security crea de manera predeterminada grupos automáticos. Por ejemplo, hay un grupo automático de usuarios denominado **Externos** que combina todos los usuarios de todas las aplicaciones que son externos a la organización y que tienen acceso a archivos o que se encontraban en las actividades de usuario del inquilino. En Cloud App Security existen los siguientes grupos automáticos:

  - External
  - Administrador de Dropbox
  - Administrador de Office 365
  - Administrador de G Suite
  - Administrador de Box
  - Todos los perfiles estándar y personalizados de Salesforce, como Administrador del sistema de Salesforce. Vea [aquí](https://help.salesforce.com/articleView?id=standard_profiles.htm&language=en&type=0) la lista completa.

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
1. Haga clic en **Importar**. Después de importar un grupo, Cloud App Security sincroniza automáticamente los miembros del grupo, igual que Active Directory Connect.
1. Una vez finalizada la importación, en la página **Grupos de usuarios** puede hacer clic en un grupo específico para ver una lista de todos los miembros del grupo. Haga clic en cualquier miembro del grupo para explorar en profundidad los detalles de una cuenta específica. Puede ver qué aplicaciones usan y un resumen de la cuenta, incluidos los gráficos del usuario y su actividad.

La importación de grupos le permite seleccionar esos grupos como filtros cuando examine el **registro de actividad** y cuando cree directivas.

> [!NOTE]
>
> - Puede haber un breve retraso hasta que los grupos de usuarios importados estén disponibles en los filtros.
> - Para que las actividades se etiqueten como realizadas por un miembro del grupo de usuarios, deberán llevarse a cabo después de la importación de un grupo.
> - Después de la sincronización inicial, los grupos se actualizan cada hora.

Para obtener más información sobre el uso de los filtros de grupo de usuario, vea [Actividades](activity-filters.md).

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Configurar Cloud Discovery](set-up-cloud-discovery.md)

[!INCLUDE [Open support ticket](includes/support.md)]
