---
title: Implementación de Control de aplicaciones de acceso condicional de Cloud App Security para cualquier aplicación Web mediante PingOne
description: En este artículo se proporciona información sobre cómo implementar el Control de aplicaciones de acceso condicional de Microsoft Cloud App Security para cualquier aplicación web que use el proveedor de identidades de PingOne.
ms.date: 09/29/2020
ms.topic: how-to
ms.openlocfilehash: df0ab81e2dcb6140f939caff436d18868daad496
ms.sourcegitcommit: f56a2060b99ab087b8637606a1fb66e5577aded8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/26/2021
ms.locfileid: "98795135"
---
# <a name="onboard-and-deploy-conditional-access-app-control-for-any-web-app-using-pingone-as-the-identity-provider-idp"></a>Incorporación e implementación de Control de aplicaciones de acceso condicional para cualquier aplicación web que use PingOne como proveedor de identidades (IdP)

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Puede configurar controles de sesión en Microsoft Cloud App Security para que funcionen con cualquier aplicación web y con un IdP de terceros. En este artículo se describe cómo enrutar las sesiones de aplicación de PingOne a Cloud App Security para los controles de sesión en tiempo real.

En este artículo, usaremos la aplicación Salesforce como ejemplo de una aplicación web que se configura para usar Cloud App Security controles de sesión.

## <a name="prerequisites"></a>Requisitos previos

- Su organización debe tener las licencias siguientes para usar Control de aplicaciones de acceso condicional:

  - Una licencia de PingOne relevante (necesaria para el inicio de sesión único)
  - Microsoft Cloud App Security

- Una configuración de inicio de sesión único de PingOne existente para la aplicación mediante el protocolo de autenticación SAML 2,0

## <a name="to-configure-session-controls-for-your-app-using-pingone-as-the-idp"></a>Para configurar los controles de sesión de la aplicación mediante PingOne como IdP

Siga estos pasos para enrutar las sesiones de la aplicación web desde PingOne a Cloud App Security. Para Azure AD pasos de configuración, consulte Configuración de la [integración con Azure ad](proxy-deployment-any-app.md#configure-integration-with-azure-ad).

> [!NOTE]
> Puede configurar la información de inicio de sesión único de SAML de la aplicación proporcionada por PingOne mediante uno de los métodos siguientes:
>
> - **Opción 1**: cargar el archivo de metadatos de SAML de la aplicación.
> - **Opción 2**: proporcionar manualmente los datos de SAML de la aplicación.
>
> En los pasos siguientes, usaremos la opción 2.

**Paso 1: [obtener la configuración de inicio de sesión único de SAML de la aplicación](#idp1-get-your-app-saml-sso-info)**

**Paso 2: [configuración de Cloud App Security con la información de SAML de la aplicación](#idp1-conf-cas-with-your-app-saml-info)**

**Paso 3: [creación de una aplicación personalizada en PingOne](#idp1-create-custom-app-pingone)**

**Paso 4: [configuración de Cloud App Security con la información de la aplicación PingOne](#idp1-conf-cas-with-pingone-app-info)**

**Paso 5: [completar la aplicación personalizada en PingOne](#idp1-complete-custom-app-in-pingone)**

**Paso 6: [obtener los cambios de la aplicación en Cloud App Security](#idp1-get-app-changes-in-cas)**

**Paso 7: [completar los cambios de la aplicación](#idp1-complete-app-changes)**

**Paso 8: [completar la configuración en Cloud App Security](#idp1-complete-conf-in-cas)**

<a name="idp1-get-your-app-saml-sso-info"></a>

## <a name="step-1-get-your-apps-saml-single-sign-on-settings"></a>Paso 1: obtener la configuración de inicio de sesión único de SAML de la aplicación

1. En Salesforce, **vaya a configuración configuración**  >    >  **identidad**  >  **Sign-On configuración**.

1. En **configuración de Sign-On única**, haga clic en el nombre de la configuración de SAML 2,0 existente.

    ![Selección de la configuración de SSO de Salesforce](media/proxy-idp-pingone/idp-pingone-sf-select-sso-settings.png)

1. En la página de **configuración de Sign-On único de SAML** , tome nota de la **dirección URL de inicio de sesión** de Salesforce. Lo necesitará más adelante.

    > [!NOTE]
    > Si la aplicación proporciona un certificado SAML, descargue el archivo de certificado.

    ![Seleccione la dirección URL de inicio de sesión de Salesforce SSO](media/proxy-idp-pingone/idp-pingone-sf-copy-saml-sso-login-url.png)

<a name="idp1-conf-cas-with-your-app-saml-info"></a>

## <a name="step-2-configure-cloud-app-security-with-your-apps-saml-information"></a>Paso 2: configuración de Cloud App Security con la información de SAML de la aplicación

1. En Cloud App Security, vaya a **investigar**  >  **aplicaciones conectadas**  >  **control de aplicaciones de acceso condicional aplicaciones**.

1. Haga clic en el signo más ( **+** ) y, en el elemento emergente, seleccione la aplicación que desea implementar y, a continuación, haga clic en **iniciar el asistente**.
1. En la **página información** de la aplicación, seleccione **rellenar datos manualmente**, en la **dirección URL del servicio de consumidor de aserciones** , escriba la **dirección URL de inicio de sesión** de Salesforce que anotó anteriormente y, a continuación, haga clic en **siguiente**.

    > [!NOTE]
    > Si la aplicación proporciona un certificado SAML, seleccione **usar <app_name> certificado SAML** y cargue el archivo de certificado.

    ![Rellenar manualmente la información de Salesforce SAML](media/proxy-idp-pingone/idp-pingone-cas-sf-app-info.png)

<a name="idp1-create-custom-app-pingone"></a>

## <a name="step-3-create-a-custom-app-in-pingone"></a>Paso 3: creación de una aplicación personalizada en PingOne

Antes de continuar, siga los pasos que se indican a continuación para obtener información de la aplicación existente de Salesforce.

1. En PingOne, edite la aplicación existente de Salesforce.

1. En la página **asignación de atributos de SSO** , anote el valor y el atributo de SAML_SUBJECT y, a continuación, descargue el certificado de **firma** y los archivos de **metadatos de SAML** .

    ![Nota: atributos de la aplicación de Salesforce existentes](media/proxy-idp-pingone/idp-pingone-sf-app-copy-saml-sso-attributes.png)

1. Abra el archivo de metadatos de SAML y tome nota de la **Ubicación de SingleSignOnService** de PingOne. Lo necesitará más adelante.

    ![Anote la ubicación del servicio SSO de la aplicación de Salesforce existente](media/proxy-idp-pingone/idp-pingone-sf-app-copy-saml-sso-service-location.png)

1. En la página **acceso al grupo** , tome nota de los grupos asignados.

    ![Nota los grupos asignados de la aplicación de Salesforce existentes](media/proxy-idp-pingone/idp-pingone-sf-app-copy-saml-sso-user-groups.png)

Después, siga las instrucciones de la página **Agregar una aplicación SAML con el proveedor de identidades** para configurar una aplicación personalizada en el portal del IDP.

![Agregar una aplicación SAML con el proveedor de identidades](media/proxy-deploy-add-idp-get-conf.png)

> [!NOTE]
> La configuración de una aplicación personalizada le permite probar la aplicación existente con controles de acceso y de sesión sin cambiar el comportamiento actual de la organización.

1. Cree una **nueva aplicación de SAML**.

    ![En PingOne, cree una nueva aplicación personalizada de Salesforce.](media/proxy-idp-pingone/idp-pingone-sf-custom-app-new.png)

1. En la página Detalles de la **aplicación** , rellene el formulario y, a continuación, haga clic en **ir al paso siguiente**.

    > [!TIP]
    > Use un nombre de aplicación que le ayude a diferenciar entre la aplicación personalizada y la aplicación existente de Salesforce.

    ![Rellene los detalles de la aplicación personalizada](media/proxy-idp-pingone/idp-pingone-sf-custom-app-details.png)

1. En la página Configuración de la **aplicación** , realice lo siguiente y, a continuación, haga clic en **ir al paso siguiente**.
    - En el campo **dirección URL del servicio de un solo SIGH** , escriba la **dirección URL de inicio de sesión** de Salesforce que anotó anteriormente.
    - En el campo ID. de **entidad** , escriba un identificador único que empiece por *https://*. Asegúrese de que es diferente de la configuración de la aplicación de Salesforce PingOne.
    - Tome nota del identificador de **entidad**. Lo necesitará más adelante.

    ![Configuración de una aplicación personalizada con detalles de SAML SAML](media/proxy-idp-pingone/idp-pingone-sf-custom-app-set-saml-sso-properties.png)

1. En la página **asignación de atributos de SSO** , agregue el atributo y el valor de **SAML_SUBJECT** de la aplicación de Salesforce existente que anotó anteriormente y, a continuación, haga clic en **continuar con el paso siguiente**.

    ![Agregar atributos a la aplicación personalizada de Salesforce](media/proxy-idp-pingone/idp-pingone-sf-custom-app-set-saml-sso-attributes.png)

1. En la página **acceso al grupo** , agregue los grupos existentes de la aplicación de Salesforce que anotó anteriormente y complete la configuración.

    ![Asignación de grupos a la aplicación personalizada de Salesforce](media/proxy-idp-pingone/idp-pingone-sf-custom-app-set-saml-sso-user-groups.png)

<a name="idp1-conf-cas-with-pingone-app-info"></a>

## <a name="step-4-configure-cloud-app-security-with-the-pingone-apps-information"></a>Paso 4: configuración de Cloud App Security con la información de la aplicación PingOne

1. De nuevo en la página **proveedor de identidad** de Cloud App Security, haga clic en **siguiente** para continuar.

1. En la página siguiente, seleccione **rellenar datos manualmente**, realice lo siguiente y, a continuación, haga clic en **siguiente**.
    - Para la **dirección URL del servicio de consumidor de aserciones**, escriba la **dirección URL de inicio de sesión** de Salesforce que anotó anteriormente.
    - Seleccione **cargar certificado SAML del proveedor de identidades** y cargue el archivo de certificado que descargó anteriormente.

    ![Agregar la dirección URL del servicio SSO y el certificado SAML](media/proxy-idp-pingone/idp-pingone-cas-sf-app-idp-info.png)

1. En la página siguiente, tome nota de la siguiente información y, a continuación, haga clic en **siguiente**. Necesitará la información más adelante.

    - Cloud App Security dirección URL de inicio de sesión único
    - Cloud App Security atributos y valores

    ![En Cloud App Security, tenga en cuenta los atributos y la dirección URL de SSO](media/proxy-idp-pingone/idp-pingone-cas-get-sf-app-external-config.png)

<a name="idp1-complete-custom-app-in-pingone"></a>

## <a name="step-5-complete-the-custom-app-in-pingone"></a>Paso 5: completar la aplicación personalizada en PingOne

1. En PingOne, busque y edite la aplicación personalizada de Salesforce.

    ![Búsqueda y edición de una aplicación de Salesforce personalizada](media/proxy-idp-pingone/idp-pingone-sf-custom-app-edit.png)

1. En el campo **servicio de consumidor de aserciones (ACS)** , sustituya la dirección URL por la Cloud App Security dirección URL de inicio de sesión único que anotó anteriormente y, a continuación, haga clic en **siguiente**.

    ![Reemplazar ACS en la aplicación personalizada de Salesforce](media/proxy-idp-pingone/idp-pingone-sf-custom-app-replace-saml-sso-properties.png)

1. Agregue los atributos y valores de Cloud App Security que anotó anteriormente a las propiedades de la aplicación.

    ![Adición de atributos de Cloud App Security a la aplicación personalizada de Salesforce](media/proxy-idp-pingone/idp-pingone-sf-custom-app-replace-saml-sso-attributes.png)

1. Guarde la configuración.

<a name="idp1-get-app-changes-in-cas"></a>

## <a name="step-6-get-the-app-changes-in-cloud-app-security"></a>Paso 6: obtener los cambios de la aplicación en Cloud App Security

De nuevo en la página Cloud App Security cambios en la **aplicación** , realice lo siguiente, pero **no haga clic en finalizar**. Necesitará la información más adelante.

- Copia de la dirección URL de inicio de sesión único de SAML Cloud App Security
- Descargar el certificado SAML Cloud App Security

![Anote el Cloud App Security dirección URL de SSO de SAML y descargue el certificado.](media/proxy-idp-pingone/idp-pingone-cas-sf-app-changes.png)

<a name="idp1-complete-app-changes"></a>

## <a name="step-7-complete-the-app-changes"></a>Paso 7: completar los cambios de la aplicación

En Salesforce, **vaya a configuración configuración**  >    >  **identidad**  >  **única Sign-On configuración** y haga lo siguiente:

1. Recomendado: cree una copia de seguridad de la configuración actual.
1. Reemplace el valor del campo **dirección URL de inicio de sesión del proveedor de identidad** por el Cloud App Security dirección URL de inicio de sesión único de SAML que anotó anteriormente.
1. Cargue el certificado SAML Cloud App Security que descargó anteriormente.
1. Reemplace el valor del campo ID. de **entidad** por el identificador de entidad de la aplicación personalizada PingOne que anotó anteriormente.
1. Haga clic en **Save**(Guardar).

    > [!NOTE]
    > El certificado SAML Cloud App Security es válido durante un año. Una vez que expire, se deberá generar un nuevo certificado.

    ![Actualización de la aplicación personalizada de Salesforce con detalles de SAML de Cloud App Security](media/proxy-idp-pingone/idp-pingone-sf-custom-app-changes.png)

<a name="idp1-complete-conf-in-cas"></a>

## <a name="step-8-complete-the-configuration-in-cloud-app-security"></a>Paso 8: completar la configuración en Cloud App Security

- De nuevo en la página cambios en la **aplicación** Cloud App Security, haga clic en **Finalizar**. Después de completar el asistente, todas las solicitudes de inicio de sesión asociadas a esta aplicación se enrutarán a través de Control de aplicaciones de acceso condicional.

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [«ANTERIOR: implementar Control de aplicaciones de acceso condicional para las aplicaciones](proxy-deployment-any-app.md)

## <a name="see-also"></a>Consulte también

> [!div class="nextstepaction"]
> [Introducción a Control de aplicaciones de acceso condicional](proxy-intro-aad.md)

> [!div class="nextstepaction"]
> [Solución de problemas de controles de sesión y acceso](troubleshooting-proxy.md)

[!INCLUDE [Open support ticket](includes/support.md)]
