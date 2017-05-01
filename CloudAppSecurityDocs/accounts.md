---
title: Visibilidad de las cuentas de aplicaciones en la nube | Microsoft Docs
description: 'En este tema:'
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 4/23/2016
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: 7811f23b-6100-427f-93b1-44f5f81f6c76
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 5d5ccc55fe0d9c3fea93446daebfcbd5bbed8c8d
ms.sourcegitcommit: fd3b6c04cec30f7c9300cc02d29d562d17bf43ea
translationtype: HT
---
# <a name="accounts"></a>Cuentas
Cloud App Security le ofrece visibilidad sobre todas las cuentas mediante las aplicaciones conectadas. Después de conectar Cloud App Security a una aplicación mediante el conector de aplicaciones, Cloud App Security examina todas las cuentas asociadas a ellas. La página Cuentas permite investigar esas cuentas, los grupos a los que pertenecen, sus alias y las aplicaciones que usan. 


El registro **Cuentas** se puede filtrar para que se puedan buscar cuentas concretas y para profundizar en diferentes tipos de cuentas. Por ejemplo, puede filtrar por todas las cuentas externas a las que no se haya accedido desde el año pasado. Puede crear directivas basadas en las cuentas y, después, definir sobre qué quiere recibir alertas y actuar en consecuencia. 

La página **Cuentas** le permite investigar fácilmente las cuentas para detectar problemas como los siguientes:  

-   Compruebe si alguna cuenta ha estado inactiva en un servicio determinado durante mucho tiempo, ya que quizás se deba revocar la licencia de ese usuario en ese servicio.  
-   Puede filtrar por la lista de usuarios con permisos de administrador.  

-   Puede ver las cuentas que estén activas pero que pertenezcan a usuarios que ya no formen parte de la organización.  

-   Puede revocar el permiso de un usuario en una aplicación concreta, según la aplicación, o exigir a un usuario determinado que realice autenticación multifactor.
    
-   Puede ver qué cuentas están incluidas en cada grupo de usuarios.  

-   Puede ver a qué aplicaciones accede cada cuenta y qué aplicaciones se han eliminado en cuentas concretas.
    
-   También puede profundizar en la cuenta de usuario y seleccionar acciones de control relevantes, como **Suspender usuario** o **Quitar las colaboraciones del usuario**. Si el usuario se ha importado desde Azure Active Directory, también puede hacer clic en **Configuración de la cuenta de Azure AD** para obtener acceso fácilmente a características avanzadas de administración de usuarios como la administración de grupos, la autenticación multifactor, los detalles sobre inicios de sesión de usuarios y la capacidad de bloquear el inicio de sesión.

![pantalla cuentas](./media/accounts-page.png)

## <a name="account-filters"></a>Filtros de cuenta
A continuación se muestra una lista de los filtros de cuenta que se pueden aplicar. La mayoría de los filtros admiten varios valores, así como NOT, para proporcionarle una herramienta muy eficaz para la creación de directivas.  
  
- **Nombre de cuenta**: el nombre de cuenta es el alias principal del usuario, pero se admiten otros identificadores de otras cuentas Microsoft (Office 365 y Azure Active Directory), como direcciones proxy, alias o SID, que se consolidan bajo el alias principal.

- **Afiliación**: la afiliación será **Interna** o **Externa**. Para establecer qué usuarios y cuentas son internos, en **Configuración** asegúrese de establecer el **intervalo de direcciones IP** de la organización interna. En caso de que la cuenta tenga permisos de administrador, el icono de la tabla Cuentas, el correspondiente al de ![administrador de cuenta](./media/accounts-admin-icon.png), aparecerá con un lazo rojo.

- **Aplicación**: puede filtrar por cualquier aplicación conectada a la API y que esté en uso en las cuentas de la organización.

- **Dominio**: permite filtrar por usuarios de dominios concretos.

- **Visto por última vez**: el filtro **Visto por última vez** permite buscar cuentas que estén inactivas y cuyos usuarios no hayan tenido actividad durante un tiempo.

- **Organización o departamento**: permite filtrar por miembros de determinados grupos organizativos de Azure Active Directory u Office 365.

- **Grupo de usuarios**: permite filtrar por miembros de grupos de usuarios de Cloud App Security, tanto grupos de usuarios integrados como importados.


## <a name="see-also"></a>Consulte también  
[Actividades diarias para proteger el entorno de nube](daily-activities-to-protect-your-cloud-environment.md)   
[Para obtener soporte técnico, visite la página de soporte técnico asistido de Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Los clientes Premier también pueden elegir Cloud App Security directamente desde el Portal Premier.](https://premier.microsoft.com/)  
  
  