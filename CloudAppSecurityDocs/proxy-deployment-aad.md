---
title: Implementación del control de aplicaciones de acceso condicional para aplicaciones de Azure AD
description: En este artículo se ofrece información sobre cómo implementar las características del proxy inverso de control de aplicaciones de acceso condicional de Microsoft Cloud App Security para aplicaciones de Azure AD.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 03/31/2020
ms.topic: how-to
ms.collection: M365-security-compliance
ms.service: cloud-app-security
ms.suite: ems
ms.openlocfilehash: e94a6691987d89fc44f05a1bd0a12f8ef04d74fa
ms.sourcegitcommit: 29a8e66c665f51d831516924ae4d9d8047b39276
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2020
ms.locfileid: "88779414"
---
# <a name="deploy-conditional-access-app-control-for-featured-apps"></a>Implementación del Control de aplicaciones de acceso condicional para aplicaciones destacadas

*Se aplica a: Microsoft Cloud App Security*

Los controles de sesión de Microsoft Cloud App Security funcionan con las aplicaciones destacadas. Para obtener una lista de las aplicaciones que se incluyen en Cloud App Security trabajar de forma integrada, consulte [proteger aplicaciones con Cloud App Security control de aplicaciones de acceso condicional](proxy-intro-aad.md#featured-apps).

## <a name="prerequisites"></a>Requisitos previos

- Su organización debe tener las licencias siguientes para usar Control de aplicaciones de acceso condicional:

  - [Azure Active Directory (Azure ad) Premium P1](https://docs.microsoft.com/azure/active-directory/license-users-groups) o superior, o la licencia requerida por su solución de proveedor de identidades (IDP)
  - Microsoft Cloud App Security

- Las aplicaciones deben configurarse con el inicio de sesión único
- Las aplicaciones deben usar uno de los protocolos de autenticación siguientes:

    |IdP|Protocolos|
    |---|---|
    |Azure AD|SAML 2.0 u OpenID Connect|
    |Otros|SAML 2.0|

## <a name="to-deploy-featured-apps"></a>Para implementar aplicaciones destacadas

Siga estos pasos para configurar las aplicaciones destacadas que se van a controlar mediante Microsoft Cloud App Security Control de aplicaciones de acceso condicional.

**Paso 1: [configurar el IDP para trabajar con Cloud App Security](#conf-idp)**

**Paso 2: [iniciar sesión en cada aplicación con un usuario con ámbito en la Directiva](#sign-in-scoped)**

**Paso 3: [comprobar que las aplicaciones están configuradas para usar controles de acceso y de sesión](#portal)**

**Paso 4: [probar la implementación](#test)**

## <a name="step-1--configure-your-idp-to-work-with-cloud-app-security"></a>Paso 1: configurar el IdP para trabajar con Cloud App Security<a name="conf-idp"></a><a name="add-azure-ad"></a>

### <a name="configure-integration-with-azure-ad"></a>Configuración de la integración con Azure AD

Use los pasos siguientes para crear una Azure AD Directiva de acceso condicional que enruta las sesiones de la aplicación a Cloud App Security. Para otras soluciones IdP, consulte [configuración de la integración con otras soluciones IDP](#configure-integration-with-other-idp-solutions).

1. En Azure ad, vaya a **Security**  >  **acceso condicional**de seguridad.

1. En el panel **acceso condicional** , en la barra de herramientas de la parte superior, haga clic en **nueva Directiva**.

1. En el panel **nuevo** , en el cuadro de texto **nombre** , escriba el nombre de la Directiva.

1. En **asignaciones**, haga clic en **usuarios y grupos**, asigne los usuarios que van a incorporar (inicio de sesión y comprobación iniciales) a la aplicación y, a continuación, haga clic en **listo**.

1. En **asignaciones**, haga clic en **aplicaciones en la nube**, asigne las aplicaciones que quiera controlar con control de aplicaciones de acceso condicional y, a continuación, haga clic en **listo**.

1. En **controles de acceso**, haga clic en **sesión**, seleccione **usar control de aplicaciones de acceso condicional** y elija una directiva integrada (**supervisar solo** o **bloquear descargas**) o **use la directiva personalizada** para establecer una directiva avanzada en Cloud App Security y, a continuación, haga clic en **seleccionar**.

    ![Acceso condicional de Azure AD](media/azure-ad-caac-policy.png)

1. Opcionalmente, agregue condiciones y conceda controles según sea necesario.

1. Establezca **Habilitar Directiva** en **activado** y, a continuación, haga clic en **crear**.

### <a name="configure-integration-with-other-idp-solutions"></a>Configuración de la integración con otras soluciones IdP

Use los pasos siguientes para enrutar las sesiones de la aplicación desde otras soluciones IdP a Cloud App Security. Para obtener Azure AD, consulte Configuración de la [integración con Azure ad](#configure-integration-with-azure-ad).

1. En Cloud App Security, vaya a **investigar**  >  **aplicaciones conectadas**  >  **control de aplicaciones de acceso condicional aplicaciones**.

1. Haga clic en el signo más y, en el elemento emergente, seleccione la aplicación que desea implementar y, a continuación, haga clic en **iniciar el asistente**.
1. En la página información de la **aplicación** , rellene el formulario con la información de la página de configuración de inicio de sesión único de la aplicación y, a continuación, haga clic en **siguiente**.
    - Si el IdP proporciona un archivo de metadatos de inicio de sesión único para la aplicación seleccionada, seleccione **Cargar archivo de metadatos desde la aplicación** y cargue el archivo de metadatos.
    - O bien, seleccione **rellenar datos manualmente** y proporcione la siguiente información:
        - **URL del servicio de consumidor de aserciones**
        - Si la aplicación proporciona un certificado SAML, seleccione **usar <app_name> certificado SAML** y cargue el archivo de certificado.

    ![Captura de pantalla que muestra la página de información de la aplicación](media/proxy-deploy-add-idp-app-info.png)

1. En la página **proveedor de identidades** , use los pasos proporcionados para configurar una nueva aplicación en el portal del IDP y, a continuación, haga clic en **siguiente**.
    1. Vaya al portal del IdP y cree una nueva aplicación SAML personalizada.
    1. Copie la configuración de inicio de sesión único de la `<app_name>` aplicación existente en la nueva aplicación personalizada.
    1. Asigne usuarios a la nueva aplicación personalizada.
    1. Copie el inf'rmation de configuración de inicio de sesión único de las aplicaciones, lo necesitará en el paso siguiente.

    ![Captura de pantalla que muestra la página recopilar información del proveedor de identidades](media/proxy-deploy-add-idp-get-conf.png)

    > [!NOTE]
    > Estos pasos pueden diferir ligeramente en función del proveedor de identidades. Este paso se recomienda por las razones siguientes:
    >
    > - Algunos proveedores de identidades no permiten cambiar las propiedades de los atributos SAML o de la dirección URL de una aplicación de la galería
    > - La configuración de una aplicación personalizada le permite probar esta aplicación con controles de acceso y de sesión sin cambiar el comportamiento existente para su organización.

1. En la página siguiente, rellene el formulario con la información de la página de configuración de inicio de sesión único de la aplicación y, a continuación, haga clic en **siguiente**.
    - Si el IdP proporciona un archivo de metadatos de inicio de sesión único para la aplicación seleccionada, seleccione **Cargar archivo de metadatos desde la aplicación** y cargue el archivo de metadatos.
    - O bien, seleccione **rellenar datos manualmente** y proporcione la siguiente información:
        - **URL del servicio de consumidor de aserciones**
        - Si la aplicación proporciona un certificado SAML, seleccione **usar <app_name> certificado SAML** y cargue el archivo de certificado.

    ![Captura de pantalla que muestra la página especificar información del proveedor de identidades](media/proxy-deploy-add-idp-enter-conf.png)

1. En la página siguiente, copie la siguiente información y, a continuación, haga clic en **siguiente**. Necesitará la información en el paso siguiente.

    - URL de inicio de sesión único
    - Atributos y valores

    ![Captura de pantalla que muestra la página de información de SAML proveedores de identidades](media/proxy-deploy-add-idp-ext-conf.png)

1. En el portal del IdP, haga lo siguiente:
    > [!NOTE]
    > La configuración se encuentra normalmente en la página de configuración de la aplicación personalizada del portal IdP.

    1. En el campo dirección URL de inicio de sesión único, escriba la dirección URL de inicio de sesión único que anotó anteriormente.
        > [!NOTE]
        > Algunos proveedores pueden hacer referencia a la dirección URL de inicio de sesión único como *dirección URL de respuesta*.
    1. Agregue los atributos y valores que anotó anteriormente a las propiedades de la aplicación.
        > [!NOTE]
        >
        > - Algunos proveedores pueden hacer referencia a ellos como atributos o *notificaciones*de *usuario* .
        > - Al crear una nueva aplicación SAML, el proveedor de identidades Okta limita los atributos a 1024 caracteres. Para mitigar esta limitación, cree primero la aplicación sin los atributos pertinentes. Después de crear la aplicación, edítela y, a continuación, agregue los atributos pertinentes.
    1. Compruebe que el identificador de nombre tiene el formato de dirección de correo electrónico.
    1. Guarde la configuración.
1. En la página cambios en la **aplicación** , realice lo siguiente y, a continuación, haga clic en **siguiente**. Necesitará la información en el paso siguiente.

    - Copia de la dirección URL de inicio de sesión único
    - Descargar el certificado SAML Cloud App Security

    ![Captura de pantalla que muestra recopilar Cloud App Security página de información de SAML](media/proxy-deploy-add-idp-app-changes.png)

1. En el portal de la aplicación, en la configuración de inicio de sesión único, realice lo siguiente:
    1. Recomendar Cree una copia de seguridad de la configuración actual.
    1. En el campo dirección URL de inicio de sesión único, escriba la dirección URL de inicio de sesión único que anotó anteriormente.
    1. Cargue el certificado SAML Cloud App Security que anotó anteriormente.
    > [!NOTE]
    > Después de guardar la configuración, todas las solicitudes de inicio de sesión asociadas a esta aplicación se enrutarán a través de Control de aplicaciones de acceso condicional.

## <a name="step-2-sign-in-to-each-app-using-a-user-scoped-to-the-policy"></a>Paso 2: iniciar sesión en cada aplicación con un usuario con ámbito en la Directiva<a name="sign-in-scoped"></a>

> [!NOTE]
> Antes de continuar, asegúrese de cerrar primero las sesiones existentes.

Después de crear la directiva, inicie sesión en cada aplicación configurada en esa directiva. Asegúrese de que inicia sesión con un usuario configurado en la directiva.

Cloud App Security sincronizará los detalles de la Directiva con sus servidores para cada nueva aplicación en la que inicie sesión. Este proceso puede tardar hasta un minuto.

## <a name="step-3-verify-the-apps-are-configured-to-use-access-and-session-controls"></a>Paso 3: comprobar que las aplicaciones están configuradas para usar controles de acceso y de sesión<a name="portal"></a>

Las instrucciones anteriores le han ayudado a crear una directiva integrada de Cloud App Security para aplicaciones destacadas directamente en Azure AD. En este paso, compruebe que los controles de sesión y acceso estén configurados para estas aplicaciones.

1. En el portal de Cloud App Security, haga clic en el icono configuración engranaje ![configuración](media/settings-icon.png "icono de configuración")y seleccione **control de aplicaciones de acceso condicional**.

1. En la tabla Control de aplicaciones de acceso condicional Apps, fíjese en la columna **controles disponibles** y compruebe que el **control de acceso** o el **acceso condicional Azure ad**y el **control de sesión** aparecen para las aplicaciones.

    > [!NOTE]
    > Si el control de sesión no aparece para una aplicación, aún no está disponible para esa aplicación específica. Puede agregarla inmediatamente como una [aplicación personalizada](proxy-deployment-any-app.md)o puede abrir una solicitud para agregarla como una aplicación destacada haciendo clic en **solicitar control**de la sesión.
    >
    >![Solicitud del Control de aplicaciones de acceso condicional](media/caac-request.png)

## <a name="step-4-test-the-deployment"></a>Paso 4: probar la implementación<a name="test"></a>

1. Primero, cierre cualquier sesión existente. Después, intente iniciar sesión en cada aplicación que se ha implementado correctamente. Inicie sesión con un usuario que coincida con la Directiva configurada en Azure AD, o para una aplicación SAML configurada con el proveedor de identidades.

1. En el portal de Cloud App Security en **Investigar**, seleccione **Registro de actividad** y asegúrese de que se capturan las actividades de inicio de sesión de cada aplicación.

1. Puede filtrar haciendo clic en **Avanzadas** y, luego, mediante la opción **Origen es igual a Acceso condicional**.

    ![Filtrar por Acceso condicional de Azure AD](media/sso-logon.png)

1. Se recomienda que inicie sesión en aplicaciones de escritorio y móviles desde dispositivos administrados y no administrados. Esto es para asegurarse de que las actividades se capturan correctamente en el registro de actividad.  
Para comprobar que la actividad se ha capturado correctamente, haga clic en una actividad de inicio de sesión de inicio de sesión único para que se abra el cajón de actividades. Asegúrese de que la propiedad **Etiqueta de agente de usuario** refleja correctamente si el dispositivo es un cliente nativo (es decir, un aplicación de escritorio o móvil) o si es un dispositivo administrado (Compatible, Unido a dominio o Certificado de cliente válido).

> [!NOTE]
> Después de implementarse, no se puede quitar una aplicación de la página Control de aplicaciones de acceso condicional. Mientras no establezca una sesión o una directiva de acceso en la aplicación, el Control de aplicaciones de acceso condicional no cambiará el comportamiento de la aplicación.

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [«ANTERIOR: Introducción a la Control de aplicaciones de acceso condicional](proxy-intro-aad.md)

> [!div class="nextstepaction"]
> [SIGUIENTE: incorporación e implementación de Control de aplicaciones de acceso condicional para cualquier aplicación»](proxy-deployment-any-app.md)

> [!div class="nextstepaction"]
> [Solución de problemas de controles de sesión y acceso](troubleshooting-proxy.md)

[!INCLUDE [Open support ticket](includes/support.md)]
