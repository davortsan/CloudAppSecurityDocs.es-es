---
title: Administración del acceso de administrador al portal de Cloud App Security
description: En este artículo se ofrecen instrucciones para configurar el acceso al portal de Cloud App Security para los administradores.
ms.date: 01/11/2021
ms.topic: how-to
ms.openlocfilehash: f25524e7190a8ac75bdf0b467bba2e98c0b23b10
ms.sourcegitcommit: 2294a61e636b436ac96a02eb7d4969f445b4aebb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/28/2021
ms.locfileid: "98949527"
---
# <a name="manage-admin-access"></a>Administrar el acceso de administrador

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Microsoft Cloud App Security es compatible con el control de acceso basado en roles. En este artículo se ofrecen instrucciones para configurar el acceso al portal de Cloud App Security para los administradores. Para obtener más información sobre la asignación de roles de administrador, consulte los artículos sobre [Azure Active Directory](/azure/active-directory/active-directory-assign-admin-roles) y [Office 365](/office365/admin/add-users/assign-admin-roles).

## <a name="office-365-and-azure-ad-roles-with-access-to-cloud-app-security"></a>Roles de Office 365 y de Azure AD con acceso a Cloud App Security

De forma predeterminada, los siguientes roles de administrador de Office 365 y [Azure Active Directory (Azure ad)](/azure/active-directory/users-groups-roles/directory-assign-admin-roles) tienen acceso a Cloud App Security:

- Administrador **global y administrador de seguridad**: los administradores con **acceso completo** tienen permisos completos en Cloud App Security. Pueden agregar administradores, agregar directivas y opciones de configuración, cargar registros y realizar acciones de gobierno, acceder y administrar agentes de SIEM.

- **Administrador de cumplimiento**: tiene permisos de solo lectura y puede administrar alertas. No se puede tener acceso a recomendaciones de seguridad para plataformas en la nube. Puede crear y modificar directivas de archivo, permitir acciones de control de archivos y ver todos los informes integrados en Administración de datos.

- **Administrador de datos de cumplimiento**: tiene permisos de solo lectura, puede crear y modificar directivas de archivo, permitir acciones de control de archivos y ver todos los informes de detección. No se puede tener acceso a recomendaciones de seguridad para plataformas en la nube.

- **Operador de seguridad y lector de seguridad**: tiene permisos de solo lectura y puede administrar alertas. Estos administradores tienen restringido la realización de las siguientes acciones:

  - Crear directivas o editar y cambiar las existentes
  - Desempeñar acciones de control
  - Cargar registros de detección
  - Prohibición o aprobación de aplicaciones de terceros
  - Obtener acceso a la página de configuración del intervalo de direcciones IP ni verla
  - Acceso y visualización de las páginas de configuración del sistema
  - Obtener acceso a la configuración de detección ni verla
  - Obtener acceso a la página de conectores de aplicaciones ni verla
  - Obtener acceso al registro de gobernanza ni verlo
  - Obtener acceso a la página de informes de instantáneas de administración ni verla
  - Acceso y visualización de agentes SIEM

- **Lector global**: tiene acceso de solo lectura completo a todos los aspectos de Cloud App Security. No se puede cambiar la configuración ni realizar ninguna acción.

> [!NOTE]
> Los roles de Office 365 y Azure AD no aparecen en la página **administrar acceso de administrador** .

## <a name="built-in-cloud-app-security-admin-roles"></a>Roles de administrador de Cloud App Security integrados

En el portal de Cloud App Security se pueden configurar los siguientes roles de administrador específicos Cloud App Security:

- **Administrador de aplicaciones/instancias**: tiene permisos completos o de solo lectura para todos los datos de Cloud App Security que se ocupan exclusivamente de la aplicación o instancia específica de una aplicación seleccionada. Por ejemplo, da a un usuario permiso de administrador para la instancia europea de Box. El administrador verá solo los datos que se relacionan con la instancia europea de Box, ya sean archivos, actividades, directivas o alertas:

  - Página de actividades (solo actividades relacionadas con la aplicación específica)
  - Alertas (solo alertas relacionadas con la aplicación específica)
  - Directivas: puede ver todas las directivas y, si se asignan permisos completos, pueden editar o crear solo directivas que traten exclusivamente con la aplicación o la instancia
  - Página Cuentas: solo cuentas de la aplicación o instancia específica
  - Permisos de la aplicación (solo permisos de la aplicación o instancia específica)
  - Página de archivos (solo archivos de la aplicación o instancia específica)
  - Control de aplicaciones de acceso condicional (sin permisos)
  - Actividad de Cloud Discovery (sin permisos)
  - Extensiones de seguridad: solo permisos para el token de API con permisos de usuario
  - Acciones de gobernanza (solo para la aplicación o instancia específica)
  - Recomendaciones de seguridad para plataformas en la nube: sin permisos

- **Administrador de grupo de usuarios**: tiene permisos completos o de solo lectura para todos los datos de Cloud App Security que se ocupan exclusivamente de los grupos específicos asignados a ellos. Por ejemplo, si asigna permisos de administrador de usuarios al grupo "Germany-All Users", el administrador puede ver y editar información en Cloud App Security solo para ese grupo de usuarios. El administrador del grupo de usuarios tiene el siguiente acceso:

  - Página de actividades (solo actividades relacionadas con los usuarios del grupo)
  - Alertas (solo alertas relacionadas con los usuarios del grupo)
  - Directivas: puede ver todas las directivas y, si se asignan permisos completos, solo se pueden editar o crear directivas que traten exclusivamente con los usuarios del grupo
  - Pagina cuentas: solo cuentas de los usuarios del grupo específicos
  - Permisos de aplicación (sin permisos)
  - Página Archivos (sin permisos)
  - Control de aplicaciones de acceso condicional (sin permisos)
  - Actividad de Cloud Discovery (sin permisos)
  - Extensiones de seguridad: solo permisos para el token de API con usuarios del grupo
  - Acciones de gobernanza (solo para los usuarios del grupo específicos)
  - Recomendaciones de seguridad para plataformas en la nube: sin permisos

    > [!NOTE]
    >
    > - Para asignar grupos a administradores de grupos de usuarios, primero debe [importar los grupos de usuarios](user-groups.md) de las aplicaciones conectadas.
    > - Solo puede asignar permisos de administradores de grupos de usuarios a grupos de Azure AD importados.

- **Cloud Discovery administrador global**: tiene permiso para ver y editar todos los datos y la configuración de Cloud Discovery. El administrador de detección global tiene el siguiente acceso:

  - Configuración
    - Configuración del sistema: solo ver
    - Configuración de Cloud Discovery: ver y editar todo (los permisos de anonimización dependen de si se permite durante la asignación de funciones)
  - Actividad de Cloud Discovery: todos los permisos
  - Alertas: solo las alertas relacionadas con datos de Cloud Discovery
  - Directivas: puede ver todas las directivas y puede editar o crear solo las directivas de Cloud Discovery
  - Página Actividades: sin permisos
  - Página Cuentas: sin permisos
  - Permisos de aplicación (sin permisos)
  - Página Archivos (sin permisos)
  - Control de aplicaciones de acceso condicional (sin permisos)
  - Extensiones de seguridad: creación y eliminación de sus propios tokens de API
  - Acciones de gobernanza: solo acciones relacionadas con Cloud Discovery
  - Recomendaciones de seguridad para plataformas en la nube: sin permisos

- **Cloud Discovery administrador de informes**: tiene permisos para ver todos los datos de Cloud App Security que se ocupan exclusivamente de los informes de Cloud Discovery específicos seleccionados. Por ejemplo, puede conceder permisos de administrador a un usuario para el informe continuo de Microsoft defender para el punto de conexión. El administrador de detección verá solo los Cloud Discovery datos relacionados con ese origen de datos y con el catálogo de aplicaciones. Este administrador no tendrá acceso a las páginas de **actividades**, **archivos** o **recomendaciones de seguridad** y acceso limitado a las directivas.

> [!NOTE]
> Los roles de administrador de Cloud App Security integrados solo proporcionan permisos de acceso a Cloud App Security.

## <a name="override-admin-permissions"></a>Invalidación de los permisos de administrador

Si quiere invalidar un permiso de administrador de Azure Active Directory u Office 365, puede hacerlo manualmente agregando el usuario a Cloud App Security y asignándole permisos. Por ejemplo, si quiere que Claudia, una usuaria que tiene el rol de Lector de seguridad en Azure Active Directory, tenga **Acceso completo** en Cloud App Security, puede agregarla manualmente a Cloud App Security y asignarle **Acceso completo** a fin de invalidar su rol y concederle los permisos necesarios en Cloud App Security.

## <a name="add-additional-admins"></a>Agregar administradores adicionales

Puede agregar más administradores a Cloud App Security sin agregar usuarios a los roles administrativos de Azure Active Directory. Para hacerlo, realice estos pasos:

> [!IMPORTANT]
> Solo los administradores globales o de seguridad pueden conceder acceso a otros usuarios a Cloud App Security.

1. Haga clic en el engranaje de configuración ![icono de configuración](media/settings-icon.png "icono de configuración") y luego en **administrar acceso de administrador**.

2. Haga clic en el signo más para agregar los administradores que deben tener acceso a Cloud App Security. Puede escribir una dirección de correo electrónico interno o externo para permitir que los administradores de la organización o los proveedores de servicios de seguridad administrada (MSSP) externos administren las alertas de seguridad.

    ![agregar administradores](media/add-admin.png)

3. A continuación, haga clic en la lista desplegable para establecer el tipo de rol que tiene el administrador, el administrador **global**, el **lector de seguridad**, el **Administrador de cumplimiento**, el administrador de la **aplicación/instancia**, el **Administrador del grupo de usuarios**, **Cloud Discovery administrador global** o **Cloud Discovery administrador de informes**. Si selecciona **Administrador de instancia/aplicación**, seleccione la aplicación y la instancia para que el Administrador tenga permisos.

    >[!NOTE]
    > Si un administrador cuyo acceso está limitado intenta acceder a una página restringida o realizar una acción restringida, recibirá un error por el que se notifica que no tiene permiso para acceder a la página o realizar la acción.

4. Haga clic en **Agregar administrador**.

## <a name="admin-activity-auditing"></a>Auditoría de actividades de administración

Cloud App Security le permite exportar un registro de las actividades de inicio de sesión de administrador y una auditoría de vistas de un usuario específico o de las alertas que se han llevado a cabo como parte de una investigación.

Para exportar un registro, realice los pasos siguientes:

1. En la página de **acceso administrar administradores** , seleccione **exportar actividades de administración**.

1. Especifique el intervalo de tiempo necesario.

1. Haga clic en **Exportar**.

## <a name="invite-external-admins"></a>Invitar a administradores externos

Cloud App Security le permite invitar a los proveedores de servicios de seguridad administrados (MSSPs) externos como administradores de su portal de Cloud App Security. Los usuarios externos ahora se pueden configurar como administradores y asignar cualquiera de los roles disponibles en Cloud App Security. Para agregar usuarios externos, asegúrese de que Cloud App Security esté habilitado en el inquilino de origen y proporcione una dirección de correo electrónico externa en los pasos que se indican en [agregar administradores adicionales](#add-additional-admins).

Además, para permitir que los MSSP proporcionen servicios en varios inquilinos de clientes, los administradores que tienen derechos de acceso a más de un inquilino ahora pueden cambiar de inquilino fácilmente en el portal. Para cambiar de inquilino, una vez que tenga permisos para varios inquilinos, haga clic en el icono de usuario. Verá una lista con los inquilinos para los que dispone de permisos. Seleccione el inquilino que quiera administrar.

![elegir inquilino](media/choose-tenant.png "elegir inquilino")

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Configurar Cloud Discovery](set-up-cloud-discovery.md)
