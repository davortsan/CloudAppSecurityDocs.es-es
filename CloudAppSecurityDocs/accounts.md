---
title: Visibilidad de las cuentas de aplicaciones en la nube
description: En este artículo se proporciona información sobre la revisión de las cuentas de las aplicaciones conectadas.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 05/20/2020
ms.topic: how-to
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 434e68484dad0ef3d372760242282b5e5c5826af
ms.sourcegitcommit: a0a8e25bda77fb21f280a0e504896be85b89ed6f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/25/2020
ms.locfileid: "96033232"
---
# <a name="accounts"></a>Cuentas

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Microsoft Cloud App Security le ofrece la posibilidad de supervisar las cuentas de sus aplicaciones conectadas. Después de conectar Cloud App Security a una aplicación mediante el conector de aplicaciones, Cloud App Security lee la información de la cuenta asociada a las aplicaciones conectadas. La página Cuentas permite investigar esas cuentas, los permisos, los grupos a los que pertenecen, sus alias y las aplicaciones que usan. Además, cuando Cloud App Security detecta una cuenta nueva que no se había detectado previamente en ninguna de las aplicaciones conectadas (por ejemplo, en la actividad o el uso compartido de archivos), la cuenta se agrega a la lista de cuentas de la aplicación en cuestión. Esto le permite supervisar la actividad de los usuarios externos que interactúan con sus aplicaciones en la nube.

Los administradores pueden buscar los metadatos o la actividad de un usuario específico. La página **usuarios y cuentas** proporciona detalles completos sobre las entidades que se extraen de las aplicaciones en la nube conectadas. También se proporciona el historial de actividad del usuario y las alertas de seguridad relacionadas con él.

[!INCLUDE [Handle personal data](../includes/gdpr-intro-sentence.md)]

La página **usuarios y cuentas** se puede [filtrar](#users-and-accounts-filters) para que pueda buscar cuentas específicas y profundizar en diferentes tipos de cuentas. por ejemplo, puede filtrar por todas las cuentas externas a las que no se ha accedido desde el año pasado.

La página **Usuarios y cuentas** permite investigar fácilmente las cuentas, incluidos los problemas siguientes:

* Compruebe si alguna cuenta ha estado inactiva en un servicio determinado durante mucho tiempo, ya que quizás se deba revocar la licencia de ese usuario en ese servicio.

* Puede filtrar por la lista de usuarios con permisos de administrador.
* Puede buscar usuarios que ya no formen parte de su organización, pero que es posible que aún tengan cuentas activas.
* Puede realizar [acciones de gobierno](#governance-actions) en las cuentas, como suspender una aplicación o ir a la página de configuración de la cuenta.
* Puede ver qué cuentas están incluidas en cada grupo de usuarios.  
* Puede ver a qué aplicaciones accede cada cuenta y qué aplicaciones se han eliminado en cuentas concretas.

    ![pantalla cuentas](media/accounts-page.png)

## <a name="users-and-accounts-filters"></a>Filtros de usuarios y cuentas

A continuación, se muestra una lista de los filtros de cuenta que se pueden aplicar. La mayoría de los filtros admiten varios valores, así como NOT, para proporcionarle una herramienta eficaz para la creación de directivas.  
  
<!--- **Account name**: The account name is the primary alias of the user, but other identifiers from other Microsoft accounts (Office 365 and Azure Active Directory) such as proxy addresses, aliases, SID are supported and consolidated beneath the primary alias. -->

* **Afiliación**: la afiliación es **Interna** o **Externa**. Para establecer qué usuarios y cuentas son internos, en **Configuración** asegúrese de establecer el **intervalo de direcciones IP** de la organización interna. En caso de que la cuenta tenga permisos de administrador, el icono de la tabla Cuentas aparece con un lazo rojo. ![icono de administrador de cuentas](media/accounts-admin-icon.png)

* **Aplicación**: puede filtrar por cualquier aplicación conectada a la API y que esté en uso en las cuentas de la organización.
* **Dominio**: permite filtrar por usuarios de dominios concretos.
* **Grupos**: permite filtrar por miembros de grupos de usuarios de Cloud App Security, tanto grupos de usuarios integrados como importados.
* **Instancia**: permite filtrar por miembros de una instancia de una aplicación específica.
* **Visto por última vez**: el filtro **Visto por última vez** permite buscar cuentas que estén inactivas y cuyos usuarios no hayan tenido actividad durante un tiempo.
* **Organización**: permite filtrar por miembros de determinados grupos organizativos definidos en sus aplicaciones conectadas.
* **Show Admins only** (Mostrar solo administradores): filtra cuentas y usuarios que son administradores.
* **Estado**: filtra según el estado de la cuenta de usuario de N/D, ensayo, activa, suspendida o eliminado. Un estado de no disponible (N/A) es normal y puede aparecer, por ejemplo, para las cuentas anónimas.
* **Tipo**: permite filtrar por el usuario o el tipo de cuenta.
* **Nombre de usuario**: permite filtrar a usuarios específicos.

## <a name="governance-actions"></a>Acciones de gobernanza

En la página **usuarios y cuentas** , puede realizar acciones de gobierno como suspender una aplicación o ir a la página de configuración de la cuenta. Para obtener una lista completa de las acciones de gobierno, consulte el [registro de gobierno](governance-actions.md).

Por ejemplo, si identifica un usuario que está en peligro, puede aplicar la acción **confirmar usuario comprometido** para establecer el nivel de riesgo del usuario en alto, lo que provoca que se apliquen las acciones de directiva relevantes definidas en Azure Active Directory. La acción se puede aplicar manualmente o mediante [directivas relevantes que admitan acciones de gobierno](governance-actions.md).

### <a name="to-manually-apply-a-user-or-account-governance-action"></a>Para aplicar manualmente una acción de gobierno de cuentas o usuarios

Puede aplicar manualmente la acción **confirmar el compromiso del usuario** mediante uno de los métodos siguientes:

* En la página **usuarios y cuentas** , en la fila donde aparece el usuario o la cuenta correspondiente, elija los tres puntos al final de la fila y, a continuación, elija **confirmar usuario comprometido**.

* En la **página usuario**, seleccione **acciones del usuario** y, a continuación, elija **confirmar usuario comprometido**.

* **Nombre de usuario**: permite filtrar a usuarios específicos.

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Actividades diarias para proteger el entorno de nube](daily-activities-to-protect-your-cloud-environment.md)

[!INCLUDE [Open support ticket](includes/support.md)]
