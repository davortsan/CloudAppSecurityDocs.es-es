---
title: Implementar Control de aplicaciones de acceso condicional de Cloud App Security para las aplicaciones
description: En este artículo se proporciona información sobre cómo implementar las características de Microsoft Cloud App Security Control de aplicaciones de acceso condicional proxy inverso para las aplicaciones.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 03/31/2020
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.suite: ems
ms.openlocfilehash: c0676bf371e13be602fcbeea1625b19480a348a1
ms.sourcegitcommit: 97563af6076ccbad0d994ac69a85a998a625d06a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/28/2020
ms.locfileid: "87296975"
---
# <a name="onboard-and-deploy-conditional-access-app-control-for-any-app"></a>Incorporación e implementación de Control de aplicaciones de acceso condicional para cualquier aplicación

*Se aplica a: Microsoft Cloud App Security*

Los controles de sesión de Microsoft Cloud App Security se pueden configurar para que funcionen con cualquier aplicación Web. En este artículo se describe cómo incorporar e implementar aplicaciones de línea de negocio personalizadas, aplicaciones SaaS no destacadas y aplicaciones locales hospedadas a través del proxy de aplicación de Azure Active Directory (Azure AD) con controles de sesión.

Para obtener una lista de las aplicaciones que se incluyen en Cloud App Security trabajar de forma integrada, consulte [proteger aplicaciones con Cloud App Security control de aplicaciones de acceso condicional](proxy-intro-aad.md#featured-apps).

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

## <a name="to-deploy-any-app"></a>Para implementar cualquier aplicación

Siga estos pasos para configurar cualquier aplicación que se controlará Cloud App Security Control de aplicaciones de acceso condicional.

**Paso 1: [configurar el IDP para trabajar con Cloud App Security](#conf-idp)**

**Paso 2: [configurar los usuarios que van a implementar la aplicación](#conf-users)**

**Paso 3: [configurar la aplicación que va a implementar](#conf-app)**

**Paso 4: [comprobar que la aplicación funciona correctamente](#verify-app)**

**Paso 5: [habilitación de la aplicación para su uso en la organización](#enable-app)**

**Paso 6: [actualización de la Directiva de Azure ad](#update-azure-ad)**

> [!NOTE]
> Para implementar Control de aplicaciones de acceso condicional para aplicaciones de Azure AD, necesita una [licencia válida para Azure Active Directory Premium P1 o superior](https://docs.microsoft.com/azure/active-directory/license-users-groups) , así como una licencia de Cloud App Security.

## <a name="step-1--configure-your-idp-to-work-with-cloud-app-security"></a>Paso 1: configurar el IdP para trabajar con Cloud App Security<a name="conf-idp"></a><a name="conf-azure-ad"></a>

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
    1. Copie la información de configuración de inicio de sesión único de las aplicaciones, la necesitará en el paso siguiente.

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

## <a name="step-2-configure-the-users-that-will-deploy-the-app"></a>Paso 2: configurar los usuarios que van a implementar la aplicación<a name="conf-users"></a>

1. En Cloud App Security, en la barra de menús, haga clic en el ![icono](media/settings-icon.png "icono de configuración") de configuración engranaje de configuración y seleccione **configuración**.

1. En **control de aplicaciones de acceso condicional**, seleccione **incorporación/mantenimiento**de la aplicación.

1. Escriba el nombre principal de usuario o el correo electrónico de los usuarios que van a incorporar la aplicación y, a continuación, haga clic en **Guardar**.

    ![Captura de pantalla de la configuración de incorporación y mantenimiento de la aplicación.](media/app-onboarding-settings.png)

## <a name="step-3-configure-the-app-that-you-are-deploying"></a>Paso 3: configurar la aplicación que va a implementar<a name="conf-app"></a>

Vaya a la aplicación que va a implementar. La página que vea dependerá de si se reconoce la aplicación. Lleve a cabo una de las siguientes acciones:

| Estado de la aplicación | Description | Pasos |
| --- | --- | --- |
| No reconocido | Verá una página de aplicación no reconocida que le pide que configure la aplicación. | 1. [agregue la aplicación a control de aplicaciones de acceso condicional](#add-app).<br /> 2. [agregue los dominios de la aplicación](#add-domains)y, a continuación, vuelva a la aplicación y actualice la página.<br /> 3. [Instale los certificados para la aplicación](#install-certs). |
| Recognized | Verá una página de incorporación que le pide que continúe con el proceso de configuración de la aplicación. | - [Instale los certificados para la aplicación](#install-certs). <br /><br /> **Nota:** Asegúrese de que la aplicación esté configurada con todos los dominios necesarios para que la aplicación funcione correctamente. Para configurar dominios adicionales, vaya a [Agregar los dominios de la aplicación](#add-domains)y, a continuación, vuelva a la página de la aplicación. |

### <a name="to-add-a-new-app"></a>Para agregar una nueva aplicación<a name="add-app"></a>

1. En la barra de menús, haga clic en el icono configuración engranaje ![configuración](media/settings-icon.png "icono de configuración")y, a continuación, seleccione **control de aplicaciones de acceso condicional**.

1. En el encabezado, haga clic en **ver nuevas aplicaciones**.

    ![Vista de nuevas aplicaciones del Control de aplicaciones de acceso condicional](media/caac-view-apps.png)

1. En la lista de aplicaciones nuevas, para cada aplicación que está incorporando, haga clic en el **+** signo y, a continuación, haga clic en **Agregar**.

    > [!NOTE]
    > Si una aplicación no aparece en el catálogo de aplicaciones de Cloud App Security, aparecerá en la sección Aplicación no identificada del cuadro de diálogo junto con la dirección URL de inicio de sesión. Al hacer clic en el signo + en estas aplicaciones, puede incorporarlas como aplicación personalizada.

    ![Aplicaciones de Azure AD detectadas mediante el Control de aplicaciones de acceso condicional](media/caac-discovered-aad-apps.png)

### <a name="to-add-domains-for-an-app"></a>Para agregar dominios para una aplicación<a name="add-domains"></a>

La Asociación de los dominios correctos a una aplicación permite Cloud App Security para aplicar directivas y actividades de auditoría.

Por ejemplo, si ha configurado una directiva que bloquea la descarga de archivos para un dominio asociado, se bloqueará la descarga de archivos por parte de la aplicación de ese dominio. Sin embargo, las descargas de archivos de la aplicación de dominios que no estén asociados a la aplicación no se bloquearán y la acción no se auditará en el registro de actividad.
> [!NOTE]
> Cloud App Security sigue agregando un sufijo a los dominios que no están asociados a la aplicación para garantizar una experiencia de usuario sin problemas.

1. Desde la aplicación, en la barra de herramientas del administrador de Cloud App Security, haga clic en **dominios detectados**.
    > [!NOTE]
    > La barra de herramientas de administración solo es visible para los usuarios con permisos para incorporar o mantener aplicaciones.
1. En el panel dominios detectados, tome nota de los nombres de dominio o exporte la lista como archivo. csv.
    > [!NOTE]
    > El panel muestra una lista de dominios detectados que no están asociados en la aplicación. Los nombres de dominio son completos.
1. Vaya a Cloud App Security, en la barra de menús, haga clic en el icono configuración engranaje ![configuración](media/settings-icon.png "icono de configuración") y seleccione **control de aplicaciones de acceso condicional**.
1. En la lista de aplicaciones, en la fila en la que aparece la aplicación que va a implementar, elija los tres puntos al final de la fila y, luego, en detalles de la **aplicación**, elija **Editar**.
    > [!TIP]
    > Para ver la lista de los dominios configurados en la aplicación, haga clic en **Ver dominios de aplicación**.
1. En **dominios definidos por el usuario**, escriba todos los dominios que desea asociar a esta aplicación y, a continuación, haga clic en **Guardar**.
    > [!NOTE]
    > Puede usar el carácter comodín * como un marcador de posición para cualquier carácter. Al agregar dominios, decida si desea agregar dominios específicos ( `sub1.contoso.com` , `sub2.contoso.com` ) o varios dominios ( `*.contoso.com` ).

### <a name="to-install-root-certificates"></a>Para instalar certificados raíz<a name="install-certs"></a>

1. Repita los pasos siguientes para instalar la **entidad de certificación actual** y los certificados raíz autofirmados de la **entidad de certificación** .
    1. Seleccione el certificado.
    1. Haga clic en **abrir**y, cuando se le pida, haga clic en **abrir** de nuevo.
    1. Haga clic en **instalar certificado**.
    1. Elija el **usuario actual** o el **equipo local**.
    1. Seleccione **colocar todos los certificados en el siguiente almacén** y, a continuación, haga clic en **examinar**.
    1. Seleccione **entidades de certificación raíz de confianza** y, a continuación, haga clic en **Aceptar**.
    1. Haga clic en **Finalizar**.

    > [!NOTE]
    > Para que se reconozcan los certificados, una vez que haya instalado el certificado, debe reiniciar el explorador e ir a la misma página.<!-- You'll see a check-mark by the certificates links confirmation they are installed.-->

1. Haga clic en **Continue**.

## <a name="step-4-verify-that-the-app-is-working-correctly"></a>Paso 4: comprobar que la aplicación funciona correctamente<a name="verify-app"></a>

1. Compruebe que el flujo de inicio de sesión funciona correctamente.
    <!--
    > [!NOTE]
    > Some apps issue a nonce hash during authentication that may break the sign-in process. If this happens, see the Troubleshooting Guide to resolve the issue.-->
1. Una vez que esté en la aplicación, realice las siguientes comprobaciones:
    1. Visite todas las páginas de la aplicación que forman parte del proceso de trabajo de los usuarios y compruebe que las páginas se representan correctamente.
    1. Compruebe que el comportamiento y la funcionalidad de la aplicación no se ven afectados por la realización de acciones comunes, como la descarga y la carga de archivos.
    1. Revise la lista de dominios asociados a la aplicación. Para obtener más información, consulte [Agregar los dominios de la aplicación](#add-domains).

## <a name="step-5-enable-the-app-for-use-in-your-organization"></a>Paso 5: habilitación de la aplicación para su uso en la organización<a name="enable-app"></a>

Una vez que esté listo para habilitar la aplicación para su uso en el entorno de producción de su organización, siga estos pasos.

1. En Cloud App Security, haga clic en el ![icono](media/settings-icon.png "icono de configuración")configuración engranaje configuración y, a continuación, seleccione **control de aplicaciones de acceso condicional**.
1. En la lista de aplicaciones, en la fila en la que aparece la aplicación que va a implementar, elija los tres puntos al final de la fila y, después, elija **Editar aplicación**.
1. Seleccione **usar con control de aplicaciones de acceso condicional** y, a continuación, haga clic en **Guardar**.

## <a name="step-6-update-the-azure-ad-policy-azure-ad-only"></a>Paso 6: actualización de la Directiva de Azure AD (solo Azure AD)<a name="update-azure-ad"></a>

1. En Azure AD, en **seguridad**, haga clic en **acceso condicional**.
1. Actualice la Directiva que creó anteriormente para incluir los usuarios, los grupos y los controles pertinentes que necesite.
1. En uso de **sesión**  >  **control de aplicaciones de acceso condicional**, si seleccionó **usar directiva personalizada**, vaya a Cloud App Security y cree una directiva de sesión correspondiente. Para obtener más información, consulte [Directivas de sesión](session-policy-aad.md).

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [«ANTERIOR: implementar Control de aplicaciones de acceso condicional para aplicaciones destacadas](proxy-deployment-aad.md)

> [!div class="nextstepaction"]
> [SIGUIENTE: Cómo crear una directiva de sesión»](session-policy-aad.md)

## <a name="see-also"></a>Consulte también

> [!div class="nextstepaction"]
> [Introducción a Control de aplicaciones de acceso condicional](proxy-intro-aad.md)

> [!div class="nextstepaction"]
> [Solución de problemas de controles de sesión y acceso](troubleshooting-proxy.md)

[!INCLUDE [Open support ticket](includes/support.md)]
