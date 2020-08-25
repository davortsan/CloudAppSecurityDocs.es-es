---
title: Conectar GitHub Enterprise Cloud a Cloud App Security
description: En este artículo se proporciona información sobre cómo conectar la aplicación GitHub Enterprise Cloud a Cloud App Security mediante el conector de API para la visibilidad y el control del uso.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 06/28/2020
ms.topic: how-to
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ROBOTS: NOINDEX
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: bb3196fb47641fad788fda6c98777bbe2ce70a8c
ms.sourcegitcommit: 29a8e66c665f51d831516924ae4d9d8047b39276
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2020
ms.locfileid: "88781147"
---
# <a name="connect-github-enterprise-cloud-to-microsoft-cloud-app-security"></a>Conectar GitHub Enterprise Cloud a Microsoft Cloud App Security

*Se aplica a: Microsoft Cloud App Security*

En este artículo se proporcionan instrucciones para conectar Microsoft Cloud App Security a la organización en la nube de GitHub Enterprise existente mediante las API del conector de aplicaciones. Esta conexión le proporciona visibilidad y control sobre el uso de GitHub Enterprise Cloud de su organización. Para obtener más información sobre cómo Cloud App Security protege GitHub Enterprise Cloud, consulte [protección de github Enterprise](protect-github.md).

## <a name="prerequisites"></a>Requisitos previos

- Su organización debe tener una licencia de GitHub Enterprise Cloud.
- La cuenta de GitHub usada para conectarse a Cloud App Security debe tener permisos de *propietario* para su organización.
- Para comprobar los propietarios de la organización, vaya a la página de su organización, seleccione **contactos**y, a continuación, filtre por *propietario*.

## <a name="how-to-connect-github-enterprise-cloud-to-cloud-app-security"></a>Cómo conectar GitHub Enterprise Cloud a Cloud App Security

### <a name="verify-your-github-domains"></a>Comprobar los dominios de GitHub

La comprobación de los dominios es opcional. Sin embargo, se recomienda encarecidamente que compruebe los dominios para que Cloud App Security pueda hacer coincidir los mensajes de correo electrónico del dominio de los miembros de su organización de GitHub con el usuario de Azure Active Directory correspondiente.

Estos pasos se pueden completar con independencia de los pasos de [configuración de github Enterprise Cloud](#configure-github-enterprise-cloud) y se pueden omitir si ya ha comprobado los dominios.

1. Actualice su organización a las [condiciones de servicio de la empresa](https://help.github.com/en/github/setting-up-and-managing-organizations-and-teams/upgrading-to-the-corporate-terms-of-service).
1. Compruebe [los dominios de la organización](https://help.github.com/en/github/setting-up-and-managing-organizations-and-teams/verifying-your-organizations-domain).

    > [!NOTE]
    > Asegúrese de comprobar cada uno de los dominios administrados que aparecen en el portal de Cloud App Security. Para ver los dominios administrados, en Cloud App Security, vaya a **configuración**detalles de la  >  **organización**  >  **dominios administrados**.

### <a name="configure-github-enterprise-cloud"></a>Configuración de GitHub Enterprise Cloud

1. **Buscar el nombre de inicio de sesión de la organización**  
En GitHub, vaya a la página de su organización y, en la dirección URL, anote el nombre de inicio de sesión de su organización, lo necesitará más adelante.

    > [!NOTE]
    > La página tendrá una dirección URL como `https://github.com/<your-organization>` . Por ejemplo, si la página de su organización es `https://github.com/sample-organization` , el nombre de inicio de sesión de la organización es *ejemplo de organización*.

    ![Captura de pantalla que muestra obtener el nombre de inicio de sesión](media/connect-github-org-login-name.png)

1. **Cree una aplicación de OAuth para Cloud App Security para conectar su organización de GitHub.**  
Repita este paso para cada organización conectada adicional.

    1. Vaya a **configuración**  >  **configuración del desarrollador**, seleccione **aplicaciones de OAuth**y, a continuación, haga clic en **registrar una aplicación**. Como alternativa, si tiene aplicaciones de OAuth existentes, haga clic en **nueva aplicación de OAuth**.

        ![Captura de pantalla que muestra la creación de una aplicación de OAuth](media/connect-github-create-oauth-app.png)

    1. Rellene los detalles del **registro de una nueva aplicación de OAuth** y haga clic en **registrar aplicación**.
        - En el cuadro Nombre de la **aplicación** , escriba un nombre para la aplicación.
        - En el cuadro **dirección URL de la Página principal** , escriba la dirección URL de la Página principal de la aplicación.
        - En el cuadro **dirección URL de devolución de llamada de autorización** , escriba el siguiente valor: `https://portal.cloudappsecurity.com/api/oauth/connect` .

        ![Captura de pantalla que muestra el registro de una aplicación de OAuth](media/connect-github-register-oauth-app.png)

    > [!NOTE]
    >
    > - De forma predeterminada, el acceso a la aplicación OAuth está restringido a las organizaciones. Para habilitar el acceso, vaya a **configuración**  >  **acceso de terceros**, haga clic en **quitar restricciones**y, a continuación, haga clic en **sí, quitar restricciones de aplicación**.
    > - Las aplicaciones que pertenecen a una organización tienen acceso a las aplicaciones de la organización. Para obtener más información, vea [acerca de las restricciones de acceso a la aplicación OAuth](https://help.github.com/en/github/setting-up-and-managing-organizations-and-teams/about-oauth-app-access-restrictions).

1. Vaya a **configuración**  >  **aplicaciones de OAuth**, seleccione la aplicación OAuth que acaba de crear y tome nota de su **identificador de cliente** y secreto de **cliente**.

    ![Captura de pantalla que muestra los detalles de una aplicación de OAuth](media/connect-github-oauth-app-details.png)

### <a name="configure-cloud-app-security"></a>Configurar Cloud App Security

1. En el portal de Cloud App Security, haga clic en **Investigar** y, después, en **Aplicaciones conectadas**.

1. En la página **conectores de aplicaciones** , haga clic en el botón de signo más seguido de **GitHub**.

1. En el elemento emergente, rellene el **ID. de cliente**, el **secreto de cliente**y el nombre de inicio de sesión de la **organización** que anotó anteriormente y, a continuación, haga clic en **conectar en github**.

    ![Captura de pantalla que muestra Connect GitHub API](media/connect-github-connect-app.png)

    Se abre la página de inicio de sesión de GitHub. Si es necesario, escriba sus credenciales de administrador de GitHub para permitir el acceso Cloud App Security a la instancia de GitHub Enterprise Cloud de su equipo.

1. Autorice a la aplicación a proporcionar a Cloud App Security para acceder a la organización de GitHub.

    > [!NOTE]
    > Cloud App Security requiere los siguientes ámbitos de OAuth:
    >
    > - **Administración: org:** necesaria para sincronizar el registro de auditoría de la organización
    > - **lectura: usuario** y **usuario: correo electrónico** : necesario para sincronizar los miembros de la organización
    > - **repositorio: estado** : requerido para sincronizar eventos relacionados con el repositorio en el registro de auditoría. para obtener más información sobre los ámbitos de OAuth, consulte [Descripción de los ámbitos de las aplicaciones de OAuth](https://developer.github.com/apps/building-oauth-apps/understanding-scopes-for-oauth-apps/).

    ![Captura de pantalla que muestra la autorización de github OAuth](media/connect-github-authorize-app.png)

1. De nuevo en la consola de Cloud App Security, debería recibir un mensaje que indica que GitHub se conectó correctamente.

1. Haga clic en **Probar API** para confirmar que la conexión se ha realizado correctamente.

    La prueba puede tardar unos minutos. Cuando reciba la notificación de que se ha realizado correctamente, haga clic en **Cerrar**.

Después de conectar GitHub Enterprise Cloud, recibirá eventos durante 7 días antes de la conexión.

Si tiene problemas para conectar la aplicación, consulte [solución de problemas de conectores de aplicaciones](troubleshooting-api-connectors-using-error-messages.md).

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Controlar las aplicaciones en la nube con directivas](control-cloud-apps-with-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]
