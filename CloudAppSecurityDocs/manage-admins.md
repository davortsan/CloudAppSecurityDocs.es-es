---
title: Administración del acceso de administrador al portal de Cloud App Security | Microsoft Docs
description: En este tema se ofrecen instrucciones para configurar el acceso al portal de Cloud App Security para sus administradores.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 6/10/2018
ms.topic: get-started-article
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: b718edad-350c-4d90-b045-92529d701dc5
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 6e9a2f9466352296caea57ee3219fa6a5151f1c8
ms.sourcegitcommit: 41fbc8e235befd240ad7a1eed52339cfafb5d906
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/10/2018
ms.locfileid: "35251776"
---
*Se aplica a: Microsoft Cloud App Security*


## <a name="managing-admin-access"></a>Administración del acceso de administrador

Microsoft Cloud App Security es compatible con el control de acceso basado en roles. De forma predeterminada, los siguientes roles de administrador de Office 365 y Azure AD tienen acceso a Microsoft Cloud App Security:

- Administrador global y administrador de seguridad: los administradores con **acceso total** tienen todos los permisos de Cloud App Security para agregar administradores, directivas y parámetros de configuración, cargar registros y realizar acciones de gobierno.

- Administrador de cumplimiento: tiene permisos de solo lectura y puede administrar alertas. Puede crear y modificar directivas de archivo, permitir acciones de control de archivos y ver todos los informes integrados en Administración de datos. 

- Lector de seguridad: tiene permisos de solo lectura y puede administrar alertas. El lector de seguridad no puede realizar las siguientes acciones:

   - Crear directivas o editar y cambiar las existentes 

   - Desempeñar acciones de control 

   - Cargar registros de detección

   - Prohibición o aprobación de aplicaciones de terceros

   - Obtener acceso a la página de configuración del intervalo de direcciones IP ni verla

   - Obtener acceso a cualquier página de configuración ni verla 

   - Obtener acceso a la configuración de detección ni verla 

   - Obtener acceso a la página de conectores de aplicaciones ni verla

   - Obtener acceso al registro de gobierno ni verlo 

   - Obtener acceso a la página de informes de instantáneas de administración ni verla 

- Administrador de aplicaciones/instancias: tiene permisos en todos los datos en Microsoft Cloud App Security que tengan que ver exclusivamente con la aplicación o instancia específica de una aplicación seleccionada aquí. Por ejemplo, si concede un permiso de administración de usuarios a la instancia europea de Cuadro, el administrador podrá ver solo los datos relativos a esta instancia de la aplicación, ya sean archivos, actividades, directivas o alertas, del siguiente modo:

  - Página de actividades (solo actividades relacionadas con la aplicación específica)
  - Alertas (solo alertas relacionadas con la aplicación específica)
  - Directivas (puede ver todas las directivas y editar o crear solo directivas que tengan que ver exclusivamente con la instancia o aplicación)
  - Cuenta (solo cuentas de la aplicación/instancia específica)
  - Permisos de la aplicación (solo permisos de la aplicación/instancia específica)
  - Página de archivos (solo archivos de la aplicación/instancia específica)
  - Control de aplicaciones de acceso condicional (sin permisos)
  - Actividad de Cloud Discovery (sin permisos)
  - Extensiones de seguridad (permisos únicamente para el token de API con permisos de usuario)
  - Acciones de gobierno (solo para la aplicación/instancia específica) 

- Administrador de grupo: tiene permisos en todos los datos en Microsoft Cloud App Security que tengan que ver exclusivamente con el grupo específico seleccionado aquí. Por ejemplo, si concede permiso a un administrador de usuarios para el grupo "Alemania: todos los usuarios", el administrador podrá ver y modificar información en Microsoft Cloud App Security solo para ese grupo de usuarios, de la manera siguiente:

  - Página de actividades (solo actividades relacionadas con los usuarios del grupo)
  -     Alertas (solo alertas relacionadas con los usuarios del grupo)
  -     Directivas (puede ver todas las directivas y editar o crear solo directivas que tengan que ver exclusivamente con usuarios del grupo)
  -     Cuenta (solo cuentas de los usuarios del grupo específicos)
  -     Permisos de aplicación (sin permisos)
  -     Página Archivos (sin permisos)
  -     Control de aplicaciones de acceso condicional (sin permisos)
  -     Actividad de Cloud Discovery (sin permisos)
  -     Extensiones de seguridad (permisos únicamente para el token de API con usuarios del grupo)
  -     Acciones de gobierno (solo para los usuarios del grupo específicos)



Para obtener más información, vea [Asignación de roles de administrador en Azure Active Directory](https://docs.microsoft.com/en-us/azure/active-directory/active-directory-assign-admin-roles).

También puede agregar más administradores a Cloud App Security sin agregar usuarios a los roles administrativos de Azure Active Directory siguiendo estos pasos:

1. Haga clic en el engranaje de configuración ![icono de configuración](./media/settings-icon.png "settings icon") y luego en **Administrar los administradores**. 

2. Haga clic en el signo más para agregar los administradores que deben tener acceso a Cloud App Security.
  
  ![agregar administradores](./media/add-admin.png)
    
3. Después, haga clic en la lista desplegable para establecer qué tipo de rol tiene el administrador, a saber, **Administrador global**, **Lector de seguridad**, **Administrador de cumplimiento** o **Administrador de aplicación/instancia**. Si selecciona **Administrador de aplicación/instancia**, seleccione la aplicación y la instancia en las que el administrador va a tener permisos.

     >[!NOTE]
      >Si un administrador cuyo acceso está limitado intenta obtener acceso a una página restringida o realizar una acción restringida, recibirá un error por el que se notifica que no tiene permiso para obtener acceso a la página o realizar la acción.
4. Haga clic en **Agregar administrador**.  

   >[!NOTE]
    >Solo los administradores globales o de seguridad pueden conceder acceso a otros usuarios a Cloud App Security.
  
**Para invalidar los permisos de administrador:**

Si quiere invalidar un permiso de administrador de Azure Active Directory u Office 365, puede hacerlo manualmente agregando el usuario a Cloud App Security y asignándole permisos.
Por ejemplo, si desea que Stephanie, una usuaria que tiene el rol de Lector de seguridad en Azure Active Directory, tenga **Acceso completo** en Cloud App Security, puede agregarla manualmente a Cloud App Security y asignarle **Acceso completo** a fin de invalidar su rol y concederle los permisos deseados en Cloud App Security. 


Para agregar administradores adicionales a Cloud App Security:
1. Haga clic en el engranaje de configuración ![icono de configuración](./media/settings-icon.png "icono de configuración") y luego en **Administrar acceso de administrador**. 

2. Agregue los administradores que deben tener acceso a Cloud App Security. Seleccione su nivel de acceso y haga clic en **Cerrar**.

## <a name="see-also"></a>Consulte también  
[Configurar Cloud Discovery](set-up-cloud-discovery.md)   

[Los clientes Premier también pueden elegir Cloud App Security directamente desde el Portal Premier.](https://premier.microsoft.com/)  
  
  