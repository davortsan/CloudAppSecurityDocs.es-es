---
title: Administración del acceso de administrador al portal de Cloud App Security
description: En este artículo se ofrecen instrucciones para configurar el acceso al portal de Cloud App Security para los administradores.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: rkarlin
ms.date: 04/04/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: b718edad-350c-4d90-b045-92529d701dc5
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 9a086df199107c08481c464fd5a15769b6c00921
ms.sourcegitcommit: 9f0c562322394a3dfac7f1d84286e673276a28b1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/14/2019
ms.locfileid: "65568649"
---
# <a name="manage-admin-access"></a>Administrar el acceso de administrador

*Se aplica a: Microsoft Cloud App Security*

Microsoft Cloud App Security es compatible con el control de acceso basado en roles. En este artículo se ofrecen instrucciones para configurar el acceso al portal de Cloud App Security para los administradores. Para obtener más información sobre la asignación de roles de administrador, vea los artículos para [Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-assign-admin-roles) y [Office 365](https://docs.microsoft.com/office365/admin/add-users/assign-admin-roles).

## <a name="office-365-and-azure-ad-roles-with-access-to-cloud-app-security"></a>Roles de Office 365 y de Azure AD con acceso a Cloud App Security

De forma predeterminada, los siguientes roles de administrador de Office 365 y [Azure Active Directory (Azure AD)](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-assign-admin-roles) tienen acceso a Microsoft Cloud App Security:

- **Administrador global y Administrador de seguridad:** los administradores con **acceso completo** tienen permisos completos en Cloud App Security. Pueden agregar administradores, incorporar directivas y configuración, cargar registros y realizar acciones de gobernanza.

- **Administrador de cumplimiento**: tiene permisos de solo lectura y puede administrar alertas. Puede crear y modificar directivas de archivo, permitir acciones de control de archivos y ver todos los informes integrados en Administración de datos. 

- **Lector de seguridad**: tiene permisos de solo lectura y puede administrar alertas. El lector de seguridad no puede realizar las siguientes acciones:

  - Crear directivas o editar y cambiar las existentes 
  - Desempeñar acciones de control 
  - Cargar registros de detección
  - Prohibición o aprobación de aplicaciones de terceros
  - Obtener acceso a la página de configuración del intervalo de direcciones IP ni verla
  - Obtener acceso a cualquier página de configuración ni verla 
  - Obtener acceso a la configuración de detección ni verla 
  - Obtener acceso a la página de conectores de aplicaciones ni verla
  - Obtener acceso al registro de gobernanza ni verlo 
  - Obtener acceso a la página de informes de instantáneas de administración ni verla 

- **Administración de aplicaciones e instancias**: tiene permisos en todos los datos en Microsoft Cloud App Security que tengan que ver exclusivamente con la aplicación o instancia específica de una aplicación seleccionada. Por ejemplo, da a un usuario permiso de administrador para la instancia europea de Box. El administrador verá solo los datos que se relacionan con la instancia europea de Box, ya sean archivos, actividades, directivas o alertas:

  - Página de actividades (solo actividades relacionadas con la aplicación específica)
  - Alertas (solo alertas relacionadas con la aplicación específica)
  - Directivas (puede ver todas las directivas y editar o crear solo directivas que tengan que ver exclusivamente con la instancia o aplicación)
  - Página Cuentas: solo cuentas de la aplicación o instancia específica
  - Permisos de la aplicación (solo permisos de la aplicación o instancia específica)
  - Página de archivos (solo archivos de la aplicación o instancia específica)
  - Control de aplicaciones de acceso condicional (sin permisos)
  - Actividad de Cloud Discovery (sin permisos)
  - Extensiones de seguridad (permisos únicamente para el token de API con permisos de usuario)
  - Acciones de gobernanza (solo para la aplicación o instancia específica) 

- **Administrador de grupo de usuarios:** tiene permisos en todos los datos en Microsoft Cloud App Security que tengan que ver exclusivamente con el grupo específico seleccionado aquí. Por ejemplo, si concede permiso a un administrador de usuarios para el grupo "Alemania: todos los usuarios", el administrador podrá ver y modificar información en Microsoft Cloud App Security solo para ese grupo de usuarios:

  - Página de actividades (solo actividades relacionadas con los usuarios del grupo)
  - Alertas (solo alertas relacionadas con los usuarios del grupo)
  - Directivas (puede ver todas las directivas y editar o crear solo directivas que tengan que ver exclusivamente con usuarios del grupo)
  - Pagina cuentas: solo cuentas de los usuarios del grupo específicos
  - Permisos de aplicación (sin permisos)
  - Página Archivos (sin permisos)
  - Control de aplicaciones de acceso condicional (sin permisos)
  - Actividad de Cloud Discovery (sin permisos)
  - Extensiones de seguridad (permisos únicamente para el token de API con usuarios del grupo)
  - Acciones de gobernanza (solo para los usuarios del grupo específicos)

- **Administrador global de cloud Discovery:**  Tiene permiso para ver y editar todos los datos y la configuración de Cloud Discovery. El administrador de detección global tiene acceso de la siguiente manera:

  - Configuración: 
     -  Configuración del sistema: solo ver
     - Configuración de Cloud Discovery: ver y editar todo (los permisos de anonimización dependen de si se permite durante la asignación de funciones)
  - Actividad de Cloud Discovery: todos los permisos
  - Alertas: solo las alertas relacionadas con datos de Cloud Discovery
  - Directivas: puede ver todas las directivas y puede editar o crear solo las directivas de Cloud Discovery
  - Página Actividades: sin permisos
  - Página Cuentas: sin permisos
  - Permisos de aplicación (sin permisos)
  - Página Archivos (sin permisos)
  - Control de aplicaciones de acceso condicional (sin permisos)
  - Extensiones de seguridad: sin permisos
  - Acciones de gobernanza: solo acciones relacionadas con Cloud Discovery

- **Administrador de informes de detección en la nube:** Tiene permisos para ver todos los datos en Microsoft Cloud App Security que se ocupa exclusivamente de los informes de Cloud Discovery específicos seleccionado. Por ejemplo, puede concede a alguien permisos de administrador para el informe continuo de Microsoft Defender ATP. El Administrador de detección verán únicamente los datos de Cloud Discovery que correspondan a ese origen de datos y en el catálogo de aplicaciones.
Este administrador no tendrán acceso a la **actividades** o **archivos** páginas y acceso limitado a las directivas.

- **Lector global:** Tiene acceso completo de solo lectura a todos los aspectos de Microsoft Cloud App Security. No puede cambiar la configuración ni realizar ninguna acción.
 
## <a name="override-admin-permissions"></a>Invalidación de los permisos de administrador

Si quiere invalidar un permiso de administrador de Azure Active Directory u Office 365, puede hacerlo manualmente agregando el usuario a Cloud App Security y asignándole permisos.
Por ejemplo, si quiere que Claudia, una usuaria que tiene el rol de Lector de seguridad en Azure Active Directory, tenga **Acceso completo** en Cloud App Security, puede agregarla manualmente a Cloud App Security y asignarle **Acceso completo** a fin de invalidar su rol y concederle los permisos necesarios en Cloud App Security. 

## <a name="add-additional-admins"></a>Agregar administradores adicionales

Puede agregar más administradores a Cloud App Security sin agregar usuarios a los roles administrativos de Azure Active Directory. Para hacerlo, realice estos pasos:

   >[!IMPORTANT]
   > Solo los administradores globales o de seguridad pueden conceder acceso a otros usuarios a Cloud App Security.


1. Haga clic en el engranaje de configuración ![icono de configuración](./media/settings-icon.png "icono de configuración") y luego en **Administrar acceso de administrador**. 

2. Haga clic en el signo más para agregar los administradores que deben tener acceso a Cloud App Security. Puede escribir una dirección de correo electrónico interno o externo para permitir que los administradores de la organización o los proveedores de servicios de seguridad administrada (MSSP) externos administren las alertas de seguridad.
  
   ![agregar administradores](./media/add-admin.png)

3. Después, haga clic en la lista desplegable para establecer qué tipo de rol tiene el administrador, a saber, **Administrador global**, **Lector de seguridad**, **Administrador de cumplimiento** o **Administrador de aplicación/instancia**. Si selecciona **Administrador de aplicación/instancia**, seleccione la aplicación y la instancia en las que el administrador va a tener permisos.

     >[!NOTE]
      >Si un administrador cuyo acceso está limitado intenta acceder a una página restringida o realizar una acción restringida, recibirá un error por el que se notifica que no tiene permiso para acceder a la página o realizar la acción.

4. Haga clic en **Agregar administrador**.  

## <a name="invite-external-admins"></a>Invitar a administradores externos

Microsoft Cloud App Security permite invitar a proveedores de servicios de seguridad administrada (MSSP) externos como administradores del portal de Microsoft Cloud App Security. Ahora es posible configurar a usuarios externos como administradores y asignarles cualquiera de los roles disponibles en Microsoft Cloud App Security. Además, para permitir que los MSSP proporcionen servicios en varios inquilinos de clientes, los administradores que tienen derechos de acceso a más de un inquilino ahora pueden cambiar de inquilino fácilmente en el portal. 

Para cambiar de inquilino, una vez que tenga permisos para varios inquilinos, haga clic en el icono de usuario. Verá una lista con los inquilinos para los que dispone de permisos. Seleccione el inquilino que quiera administrar.

![seleccionar inquilino](./media/choose-tenant.png "seleccionar inquilino")

## <a name="next-steps"></a>Pasos siguientes  
[Configurar Cloud Discovery](set-up-cloud-discovery.md)   
  
  
  
