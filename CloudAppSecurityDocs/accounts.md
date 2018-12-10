---
title: Visibilidad de las cuentas de aplicaciones en la nube | Microsoft Docs
description: En este artículo se proporciona información sobre la revisión de las cuentas de las aplicaciones conectadas.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 11/13/2018
ms.topic: conceptual
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 7811f23b-6100-427f-93b1-44f5f81f6c76
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 7785b9ea4e9f9d6dbc164ec7636e4f7a8ec79121
ms.sourcegitcommit: 77850c6777504c2478611cb71a387e7fcc5f2551
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/13/2018
ms.locfileid: "51596701"
---
# <a name="accounts"></a>Cuentas

*Se aplica a: Microsoft Cloud App Security*

Microsoft Cloud App Security le ofrece la posibilidad de supervisar las cuentas de sus aplicaciones conectadas. Después de conectar Cloud App Security a una aplicación mediante el conector de aplicaciones, Cloud App Security lee la información de la cuenta asociada a las aplicaciones conectadas. La página Cuentas permite investigar esas cuentas, los permisos, los grupos a los que pertenecen, sus alias y las aplicaciones que usan. Además, cuando Cloud App Security detecta una cuenta nueva que no se había detectado previamente en ninguna de las aplicaciones conectadas (por ejemplo, en la actividad o el uso compartido de archivos), la cuenta se agrega a la lista de cuentas de la aplicación en cuestión. Esto le permite supervisar la actividad de los usuarios externos que interactúan con sus aplicaciones en la nube.

Los administradores pueden buscar los metadatos de un usuario específico o su actividad. La página **Usuarios y cuentas** proporciona detalles completos acerca de la entidad extraídos de aplicaciones en la nube conectadas. También presenta el historial de la actividad de un usuario y sus alertas de seguridad.

[!INCLUDE [Handle personal data](../includes/gdpr-intro-sentence.md)]


La página **Usuarios y cuentas** se puede filtrar para buscar cuentas concretas y profundizar en diferentes tipos de cuentas. Por ejemplo, puede filtrar por todas las cuentas externas a las que no se haya accedido desde el año pasado. 

La página **Usuarios y cuentas** permite investigar fácilmente las cuentas, incluidos los problemas siguientes:  

-   Compruebe si alguna cuenta ha estado inactiva en un servicio determinado durante mucho tiempo, ya que quizás se deba revocar la licencia de ese usuario en ese servicio.  
-   Puede filtrar por la lista de usuarios con permisos de administrador.  

-   Puede buscar usuarios que ya no formen parte de su organización, pero que es posible que aún tengan cuentas activas.  

-   Puede realizar acciones de gobierno en la cuenta, como suspender una aplicación o ir a la página de configuración de la cuenta. Para obtener una lista completa de acciones de gobierno, vea el [registro de gobierno](governance-actions.md).
    
-   Puede ver qué cuentas están incluidas en cada grupo de usuarios.  

-   Puede ver a qué aplicaciones accede cada cuenta y qué aplicaciones se han eliminado en cuentas concretas.
    

![pantalla cuentas](./media/accounts-page.png)

## <a name="users-and-accounts-filters"></a>Filtros de usuarios y cuentas
A continuación, se muestra una lista de los filtros de cuenta que se pueden aplicar. La mayoría de los filtros admiten varios valores, así como NOT, para proporcionarle una herramienta eficaz para la creación de directivas.  
  
<!--- **Account name**: The account name is the primary alias of the user, but other identifiers from other Microsoft accounts (Office 365 and Azure Active Directory) such as proxy addresses, aliases, SID are supported and consolidated beneath the primary alias. -->

- **Afiliación**: la afiliación es **Interna** o **Externa**. Para establecer qué usuarios y cuentas son internos, en **Configuración** asegúrese de establecer el **intervalo de direcciones IP** de la organización interna. En caso de que la cuenta tenga permisos de administrador, el icono de la tabla Cuentas aparece con un lazo rojo. ![icono de administrador de cuentas](./media/accounts-admin-icon.png)

- **Aplicación**: puede filtrar por cualquier aplicación conectada a la API y que esté en uso en las cuentas de la organización.

- **Dominio**: permite filtrar por usuarios de dominios concretos.

- **Grupos**: permite filtrar por miembros de grupos de usuarios de Cloud App Security, tanto grupos de usuarios integrados como importados.

- **Instancia**: permite filtrar por miembros de una instancia de una aplicación específica. 

- **Visto por última vez**: el filtro **Visto por última vez** permite buscar cuentas que estén inactivas y cuyos usuarios no hayan tenido actividad durante un tiempo.

- **Organización**: permite filtrar por miembros de determinados grupos organizativos definidos en sus aplicaciones conectadas.

- **Show Admins only** (Mostrar solo administradores): filtra cuentas y usuarios que son administradores.

- **Estado**: filtra según el estado de la cuenta de usuario de N/D, ensayo, activa, suspendida o eliminado.

- **Tipo**: permite filtrar por el usuario o el tipo de cuenta.

- **Nombre de usuario**: permite filtrar a usuarios específicos. 


## <a name="next-steps"></a>Pasos siguientes  
[Actividades diarias para proteger el entorno de nube](daily-activities-to-protect-your-cloud-environment.md)   

[Los clientes Premier también pueden elegir Cloud App Security directamente desde el Portal Premier.](https://premier.microsoft.com/)  
  
  