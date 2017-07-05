---
title: "Administración del acceso de administrador al portal de Cloud App Security | Microsoft Docs"
description: En este tema se ofrecen instrucciones para configurar el acceso al portal de Cloud App Security para sus administradores.
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 5/10/2017
ms.topic: get-started-article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: b718edad-350c-4d90-b045-92529d701dc5
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: f4d336b48dc7f3655a60d64ec4fe7e066db7f438
ms.sourcegitcommit: 2f4474084c7e07ac4853945ab5aa1ea78950675d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/28/2017
---
## <a name="managing-admin-access"></a>Administración del acceso de administrador

Cloud App Security es compatible con el control de acceso basado en rol. De forma predeterminada, los siguientes roles de administrador de Office 365 y Azure AD tienen acceso a Cloud App Security:

- Administrador global y administrador de seguridad: los administradores con **Acceso completo** tendrán todos los permisos de Cloud App Security para agregar administradores, directivas y parámetros de configuración, cargar registros y realizar acciones de gobierno.

- Lector de seguridad: tiene permisos de solo lectura y puede administrar alertas. El lector de seguridad no puede realizar las siguientes acciones:
      - Crear directivas o editar y cambiar las existentes 
      - Desempeñar acciones de control 
      - Cargar registros de detección
      - Prohibir o aprobar aplicaciones de terceros
      - Obtener acceso a la página de configuración del intervalo de direcciones IP ni verla
      - Obtener acceso a cualquier página de configuración ni verla 
      - Obtener acceso a la configuración de detección ni verla 
      - Obtener acceso a la página de conectores de aplicaciones ni verla
      - Obtener acceso al registro de gobierno ni verlo 
      - Obtener acceso a la página de informes de instantáneas de administración ni verla 

Para obtener más información, consulte [Asignación de roles de administrador en Azure Active Directory](https://docs.microsoft.com/en-us/azure/active-directory/active-directory-assign-admin-roles).

También puede agregar más administradores a Cloud App Security sin agregar usuarios a los roles administrativos de Azure Active Directory haciendo lo siguiente:

1. Haga clic en el engranaje de configuración ![icono de configuración](./media/settings-icon.png "icono de configuración") y luego en **Administrar acceso de administrador**. 

2. Agregue los administradores que deben tener acceso a Cloud App Security.
  
      
3. A continuación, haga clic en la lista desplegable para establecer el tipo de acceso que tendrá el administrador: **Acceso completo** o **Solo lectura y administración de alertas**.

     >[!NOTE]
      >Si un administrador cuyo acceso esté limitado a **Solo lectura y administración de alertas** intenta obtener acceso a una página restringida o realizar una acción restringida, recibirá un error por el que se notifica que no tiene permiso para obtener acceso a la página o realizar la acción.

   ![administrar el acceso de administrador](./media/manage-admin-access.png "administrar el acceso de administrador")  

4. Haga clic en **Cerrar**.  

   >[!NOTE]
    >Solo los administradores globales o de seguridad pueden conceder acceso a otros usuarios a Cloud App Security.
  
**Para invalidar los permisos de administrador:**

Si quiere invalidar un permiso de administrador de Azure Active Directory u Office 365, puede hacerlo manualmente agregando el usuario a Cloud App Security y asignándole permisos.
Por ejemplo, si desea que Stephanie, una usuaria que tiene el rol de Lector de seguridad en Azure Active Directory, tenga **Acceso completo** en Cloud App Security, puede agregarla manualmente a Cloud App Security y asignarle **Acceso completo** a fin de invalidar su rol y concederle los permisos deseados en Cloud App Security. 


Para agregar administradores adicionales a Cloud App Security:
1. Haga clic en el engranaje de configuración ![icono de configuración](./media/settings-icon.png "icono de configuración") y luego en **Administrar acceso de administrador**. 

2. Agregue los administradores que deben tener acceso a Cloud App Security, seleccione su nivel de acceso y haga clic en **Cerrar**.



## <a name="see-also"></a>Consulte también  
[Configurar Cloud Discovery](set-up-cloud-discovery.md)   
[Para obtener soporte técnico, visite la página de soporte técnico asistido de Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Los clientes Premier también pueden elegir Cloud App Security directamente desde el Portal Premier.](https://premier.microsoft.com/)  
  
  