---
title: Administrar el acceso de administrador al portal de Cloud App Security
description: En este artículo se proporcionan instrucciones para configurar el acceso al portal de Cloud App Security para los administradores.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 02/25/2020
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: f36b3e09abdc8f10a1e3fa5b59b32101f13f1065
ms.sourcegitcommit: c5d288898630c949bab6538f59ae196ff9bbb909
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/25/2020
ms.locfileid: "77599749"
---
# <a name="manage-admin-access"></a>Administrar el acceso de administrador

*Se aplica a: Microsoft Cloud App Security*

Microsoft Cloud App Security es compatible con el control de acceso basado en roles. En este artículo se proporcionan instrucciones para configurar el acceso al portal de Cloud App Security para los administradores. Para obtener más información sobre la asignación de roles de administrador, consulte los artículos sobre [Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-assign-admin-roles) y [Office 365](https://docs.microsoft.com/office365/admin/add-users/assign-admin-roles).

## <a name="office-365-and-azure-ad-roles-with-access-to-cloud-app-security"></a>Roles de Office 365 y Azure AD con acceso a Cloud App Security

De forma predeterminada, los siguientes roles de administrador de Office 365 y [Azure Active Directory (Azure ad)](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-assign-admin-roles) tienen acceso a Cloud App Security:

- Administrador **global y administrador de seguridad:** Los administradores con **acceso completo** tienen permisos completos en Cloud App Security. Pueden agregar administradores, agregar directivas y opciones de configuración, cargar registros y realizar acciones de gobierno.

- **Administrador de cumplimiento:** Tiene permisos de solo lectura y puede administrar alertas. Puede crear y modificar directivas de archivo, permitir acciones de control de archivos y ver todos los informes integrados en Administración de datos.

- **Administrador de datos de cumplimiento:** Tiene permisos de solo lectura, puede crear y modificar directivas de archivo, permitir acciones de control de archivos y ver todos los informes de detección.

- **Operador de seguridad:** Tiene permisos de solo lectura y puede administrar alertas.

- **Lector de seguridad:** Tiene permisos de solo lectura y puede administrar alertas. El lector de seguridad no tiene que realizar las siguientes acciones:

  - Crear directivas o editar y cambiar las existentes
  - Desempeñar acciones de gobernanza
  - Cargar registros de detección
  - Vetar o aprobar aplicaciones de terceros
  - Obtener acceso a la página de configuración del intervalo de direcciones IP ni verla
  - Obtener acceso a cualquier página de configuración ni verla
  - Obtener acceso a la configuración de detección y verla
  - Acceso y visualización de la página de conectores de aplicaciones
  - Obtener acceso al registro de gobernanza ni verlo
  - Obtener acceso a la página de informes de instantáneas de administración ni verla
  - Acceso y edición del agente SIEM

- **Lector global:** Tiene acceso de solo lectura completo a todos los aspectos de Microsoft Cloud App Security. No se puede cambiar la configuración ni realizar ninguna acción.

Además, se pueden configurar los siguientes roles de administrador específicos de Cloud App Security en el portal de Cloud App Security:

- **Administrador de aplicaciones/instancias:** Tiene permisos completos o de solo lectura para todos los datos de Microsoft Cloud App Security que se ocupan exclusivamente de la aplicación o instancia específica de una aplicación seleccionada. Por ejemplo, puede conceder un permiso de administrador de usuario a la instancia de Box Europea. El administrador solo verá los datos relacionados con la instancia Europea de Box, ya sean archivos, actividades, directivas o alertas:

  - Página de actividades: solo actividades sobre la aplicación específica
  - Alertas: solo alertas relacionadas con la aplicación específica
  - Directivas: puede ver todas las directivas y, si se asignan permisos completos, pueden editar o crear solo directivas que traten exclusivamente con la aplicación o la instancia
  - Página cuentas: solo cuentas de la aplicación o instancia específica
  - Permisos de aplicación: permisos solo para la aplicación o instancia específica
  - Archivos de página de archivos de la aplicación o instancia específica
  - Control de aplicaciones de acceso condicional: sin permisos
  - Actividad de Cloud Discovery: sin permisos
  - Extensiones de seguridad: permisos solo para el token de API con permisos de usuario
  - Acciones de gobierno: solo para la aplicación o instancia específica

- **Administrador del grupo de usuarios:** Tiene permisos completos o de solo lectura para todos los datos de Microsoft Cloud App Security que se ocupan exclusivamente del grupo específico seleccionado aquí. Por ejemplo, si concede un permiso de administrador de usuarios al grupo "Germany-All Users", el administrador puede ver y modificar la información en Microsoft Cloud App Security solo para ese grupo de usuarios:

  - Página actividades: solo actividades sobre los usuarios del grupo
  - Alertas: solo alertas relacionadas con los usuarios del grupo
  - Directivas: puede ver todas las directivas y, si se asignan permisos completos, solo se pueden editar o crear directivas que traten exclusivamente con los usuarios del grupo
  - Página cuentas: solo cuentas para los usuarios específicos del grupo
  - Permisos de aplicación: sin permisos
  - Página archivos: sin permisos
  - Control de aplicaciones de acceso condicional: sin permisos
  - Actividad de Cloud Discovery: sin permisos
  - Extensiones de seguridad: permisos solo para el token de API con usuarios del grupo
  - Acciones de gobierno: solo para los usuarios específicos del grupo

- **Administrador global de Cloud Discovery:**  Tiene permiso para ver y editar todos los datos y la configuración de Cloud Discovery. El administrador de detección global tiene acceso como se indica a continuación:

  - Configuración
    - Configuración del sistema: solo ver
    - Cloud Discovery configuración: ver y editar todos (los permisos de anonimización dependen de si se permitía durante la asignación de roles)
  - Actividad de Cloud Discovery: permisos completos
  - Alertas solo de alertas relacionadas con datos de Cloud Discovery
  - Directivas: puede ver todas las directivas y solo puede editar o crear directivas de Cloud Discovery
  - Página actividades-sin permisos
  - Página cuentas: sin permisos
  - Permisos de aplicación: sin permisos
  - Página archivos: sin permisos
  - Control de aplicaciones de acceso condicional: sin permisos
  - Extensiones de seguridad: sin permisos
  - Acciones de gobierno: solo Cloud Discovery acciones relacionadas

- **Cloud Discovery administrador de informes:** Tiene permisos para ver todos los datos de Microsoft Cloud App Security que se ocupan exclusivamente de los informes de Cloud Discovery específicos seleccionados. Por ejemplo, puede conceder permisos de administrador a un usuario para el informe continuo desde ATP de Microsoft defender. El administrador de detección verá solo los Cloud Discovery datos relacionados con ese origen de datos y con el catálogo de aplicaciones.
Este administrador no tendrá acceso a las páginas **actividades** o **archivos** y acceso limitado a las directivas.

## <a name="override-admin-permissions"></a>Reemplazar permisos de administrador

Si desea invalidar el permiso de un administrador desde Azure Active Directory u Office 365, puede hacerlo manualmente agregando el usuario a Cloud App Security y asignando los permisos de usuario.
Por ejemplo, si desea asignar Stephanie, que es un lector de seguridad en Azure Active Directory tener **acceso completo** en Cloud App Security, puede Agregar manualmente a Cloud App Security y asignarle **acceso completo** para invalidar su rol y permitirle los permisos necesarios en Cloud App Security.

## <a name="add-additional-admins"></a>Agregar administradores adicionales

Puede agregar administradores adicionales a Cloud App Security sin agregar usuarios a Azure Active Directory roles administrativos. Para agregar administradores adicionales, siga estos pasos:

> [!IMPORTANT]
> Solo los administradores globales o los administradores de seguridad pueden conceder acceso a otros usuarios para Cloud App Security.

1. Haga clic en el engranaje de configuración ![icono de configuración](media/settings-icon.png "icono de configuración") y luego en **administrar acceso de administrador**.

2. Haga clic en el signo más para agregar los administradores que deben tener acceso a Cloud App Security. Puede escribir una dirección de correo electrónico interna o externa para permitir que los administradores de dentro de la organización o proveedores de servicios de seguridad administrados externos (MSSPs) administren las alertas de seguridad.

    ![agregar administradores](media/add-admin.png)

3. A continuación, haga clic en la lista desplegable para establecer el tipo de rol que tiene el administrador, un **administrador global**, un **lector de seguridad**, un **Administrador de cumplimiento**o un **Administrador de aplicación/instancia**. Si selecciona **Administrador de instancia/aplicación**, seleccione la aplicación y la instancia para que el Administrador tenga permisos.

    >[!NOTE]
    >Cualquier administrador, cuyo acceso sea limitado, que intente obtener acceso a una página restringida o realizar una acción restringida recibirá un error que le informará de que no tiene permiso para obtener acceso a la página o realizar la acción.

4. Haga clic en **Agregar administrador**.

## <a name="admin-activity-auditing"></a>Auditoría de actividades de administración

Cloud App Security permite exportar un registro de todas las actividades de administración, incluida la auditoría de un administrador que investiga a un usuario específico o la visualización de alertas específicas.

Para exportar un registro, realice los pasos siguientes:

1. En la página de **acceso administrar administradores** , seleccione **exportar actividades de administración**.

1. Especifique el intervalo de tiempo necesario.

1. Haga clic en **Exportar**.

## <a name="invite-external-admins"></a>Invitar a administradores externos

Cloud App Security le permite invitar a los proveedores de servicios de seguridad administrados (MSSPs) externos como administradores de su portal de Cloud App Security. Los usuarios externos ahora se pueden configurar como administradores y asignar cualquiera de los roles disponibles en Cloud App Security. Además, para permitir que MSSPs proporcione servicios entre varios inquilinos de cliente, los administradores que tienen derechos de acceso a más de un inquilino ahora pueden cambiar fácilmente a los inquilinos en el portal.

Para cambiar entre los inquilinos, una vez que tenga permisos para varios inquilinos, haga clic en el icono de usuario. Verá una lista de los inquilinos para los que tiene permisos. Seleccione el inquilino que desea administrar.

![elegir inquilino](media/choose-tenant.png "elegir inquilino")

## <a name="next-steps"></a>Pasos siguientes  

> [!div class="nextstepaction"]
> [Configurar Cloud Discovery](set-up-cloud-discovery.md)
