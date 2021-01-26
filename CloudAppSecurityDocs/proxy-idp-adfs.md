---
title: Implemente Cloud App Security Control de aplicaciones de acceso condicional para cualquier aplicación Web mediante AD FS
description: En este artículo se proporciona información sobre cómo implementar el Control de aplicaciones de acceso condicional de Microsoft Cloud App Security para cualquier aplicación web que use AD FS como proveedor de identidades.
ms.date: 01/26/2021
ms.topic: how-to
ms.openlocfilehash: 74a454332125162dbec74f076d150ffe1b9d9b45
ms.sourcegitcommit: f56a2060b99ab087b8637606a1fb66e5577aded8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/26/2021
ms.locfileid: "98795130"
---
# <a name="onboard-and-deploy-conditional-access-app-control-for-any-web-app-using-active-directory-federation-services-ad-fs-as-the-identity-provider-idp"></a>Incorporación e implementación de Control de aplicaciones de acceso condicional para cualquier aplicación web que use Servicios de federación de Active Directory (AD FS) (AD FS) como proveedor de identidades (IdP)

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Puede configurar controles de sesión en Microsoft Cloud App Security para que funcionen con cualquier aplicación web y con un IdP de terceros. En este artículo se describe cómo enrutar las sesiones de la aplicación desde AD FS a Cloud App Security para los controles de sesión en tiempo real.

En este artículo, usaremos la aplicación Salesforce como ejemplo de una aplicación web que se configura para usar Cloud App Security controles de sesión.

## <a name="prerequisites"></a>Requisitos previos

- Su organización debe tener las licencias siguientes para usar Control de aplicaciones de acceso condicional:

  - Un entorno de AD FS configurado previamente
  - Microsoft Cloud App Security

- Una configuración de inicio de sesión único (AD FS) existente para la aplicación mediante el protocolo de autenticación SAML 2,0

## <a name="to-configure-session-controls-for-your-app-using-ad-fs-as-the-idp"></a>Para configurar los controles de sesión de la aplicación mediante AD FS como IdP

Siga estos pasos para enrutar las sesiones de la aplicación web desde AD FS a Cloud App Security. Para Azure AD pasos de configuración, consulte Configuración de la [integración con Azure ad](proxy-deployment-any-app.md#configure-integration-with-azure-ad).

> [!NOTE]
> Puede configurar la información de inicio de sesión único de SAML de la aplicación proporcionada por AD FS con uno de los métodos siguientes:
>
> - **Opción 1**: cargar el archivo de metadatos de SAML de la aplicación.
> - **Opción 2**: proporcionar manualmente los datos de SAML de la aplicación.
>
> En los pasos siguientes, usaremos la opción 2.

**Paso 1: [obtener la configuración de inicio de sesión único de SAML de la aplicación](#idp1-get-your-app-saml-sso-info)**

**Paso 2: [configuración de Cloud App Security con la información de SAML de la aplicación](#idp1-conf-cas-with-your-app-saml-info)**

**Paso 3: [crear un nuevo AD FS relación de confianza para usuario autenticado y configuración de Sign-On única de la aplicación](#idp1-create-custom-app-adfs)**

**Paso 4: [configuración de Cloud App Security con la información de la aplicación de AD FS](#idp1-conf-cas-with-adfs-app-info)**

**Paso 5: [completar la configuración de la relación de confianza para usuario autenticado de AD FS](#idp1-complete-custom-app-in-adfs)**

**Paso 6: [obtener los cambios de la aplicación en Cloud App Security](#idp1-get-app-changes-in-cas)**

**Paso 7: [completar los cambios de la aplicación](#idp1-complete-app-changes)**

**Paso 8: [completar la configuración en Cloud App Security](#idp1-complete-conf-in-cas)**

<a name="idp1-get-your-app-saml-sso-info"></a>

## <a name="step-1-get-your-apps-saml-single-sign-on-settings"></a>Paso 1: obtener la configuración de inicio de sesión único de SAML de la aplicación

1. En Salesforce, **vaya a configuración configuración**  >    >  **identidad**  >  **Sign-On configuración**.

1. En **configuración de Sign-On única**, haga clic en el nombre de la configuración de AD FS existente.

    ![Selección de la configuración de SSO de Salesforce](media/proxy-idp-adfs/idp-adfs-sf-select-sso-settings.png)

1. En la página de **configuración de Sign-On único de SAML** , tome nota de la **dirección URL de inicio de sesión** de Salesforce. Lo necesitará más adelante al configurar Cloud App Security.

    > [!NOTE]
    > Si la aplicación proporciona un certificado SAML, descargue el archivo de certificado.

    ![Seleccione la dirección URL de inicio de sesión de Salesforce SSO](media/proxy-idp-adfs/idp-adfs-sf-copy-saml-sso-login-url.png)

<a name="idp1-conf-cas-with-your-app-saml-info"></a>

## <a name="step-2-configure-cloud-app-security-with-your-apps-saml-information"></a>Paso 2: configuración de Cloud App Security con la información de SAML de la aplicación

1. En Cloud App Security, vaya a **investigar**  >  **aplicaciones conectadas**  >  **control de aplicaciones de acceso condicional aplicaciones**.

1. Haga clic en el signo más y, en el elemento emergente, seleccione la aplicación que desea implementar y, a continuación, haga clic en **iniciar el asistente**.
1. En la **página información** de la aplicación, seleccione **rellenar datos manualmente**, en la **dirección URL del servicio de consumidor de aserciones** , escriba la **dirección URL de inicio de sesión** de Salesforce que anotó anteriormente y, a continuación, haga clic en **siguiente**.

    > [!NOTE]
    > Si la aplicación proporciona un certificado SAML, seleccione **usar <app_name> certificado SAML** y cargue el archivo de certificado.

    ![Rellenar manualmente la información de Salesforce SAML](media/proxy-idp-adfs/idp-adfs-cas-sf-app-info.png)

<a name="idp1-create-custom-app-adfs"></a>

## <a name="step-3-create-a-new-ad-fs-relying-party-trust-and-app-single-sign-on-configuration"></a>Paso 3: crear un nuevo AD FS relación de confianza para usuario autenticado y configuración de Sign-On única de la aplicación

> [!NOTE]
> Para limitar el tiempo de inactividad de los usuarios finales y conservar la configuración correcta existente, se recomienda crear una nueva relación de confianza para usuario **autenticado** y una **configuración de Sign-On única**. Si esto no es posible, omita los pasos correspondientes. Por ejemplo, si la aplicación que está configurando no admite la creación de varias **configuraciones de Sign-On único**, omita el paso crear nuevo inicio de sesión único.

1. En la consola de **Administración de AD FS** , en relaciones de confianza para usuario **autenticado**, vea las propiedades de la relación de confianza para usuario autenticado existente para la aplicación y tome nota de la configuración.

1. En **acciones**, haga clic en **Agregar relación de confianza para usuario autenticado**. Además del valor del **identificador** que debe ser un nombre único, configure la nueva confianza con la configuración que anotó anteriormente. Necesitará esta confianza más adelante al configurar Cloud App Security.
1. Abra el archivo de metadatos de Federación y tome nota de la **ubicación AD FS SingleSignOnService**. Lo necesitará más adelante.

    > [!NOTE]
    > Puede usar el siguiente punto de conexión para tener acceso al archivo de metadatos de Federación: `https://<Your_Domain>/federationmetadata/2007-06/federationmetadata.xml`

    ![Anote la ubicación del servicio SSO de la aplicación de Salesforce existente](media/proxy-idp-adfs/idp-adfs-sf-app-copy-saml-sso-service-location.png)

1. Descargue el certificado de firma del proveedor de identidades. Lo necesitará más adelante.
    1. En   >  **certificados** de servicios, haga clic con el botón derecho en el certificado de firma de AD FS y, a continuación, seleccione **Ver certificado**.

        ![Ver las propiedades del certificado de firma de IdP](media/proxy-idp-adfs/idp-adfs-view-signing-cert-props.png)

    1. En la pestaña detalles del certificado, haga clic en **Copiar en archivo** y siga los pasos del **Asistente para exportación de certificados** para exportar el certificado como un *X. 509 codificado en base 64 (. CER)* .

        ![Guardar el archivo de certificado de firma de IdP](media/proxy-idp-adfs/idp-adfs-save-signing-cert-file.png)

1. De nuevo en Salesforce, en la página Configuración de inicio de sesión único de AD FS existente, anote todos los valores de configuración.
1. Cree una nueva configuración de inicio de sesión único de SAML. Además del valor de **identificador de entidad** que debe coincidir con el **identificador** de la relación de confianza para usuario autenticado, configure el inicio de sesión único con la configuración que anotó anteriormente. Lo necesitará más adelante al configurar Cloud App Security.

<a name="idp1-conf-cas-with-adfs-app-info"></a>

## <a name="step-4-configure-cloud-app-security-with-the-ad-fs-apps-information"></a>Paso 4: configuración de Cloud App Security con la información de la aplicación de AD FS

1. De nuevo en la página **proveedor de identidad** de Cloud App Security, haga clic en **siguiente** para continuar.

1. En la página siguiente, seleccione **rellenar datos manualmente**, realice lo siguiente y, a continuación, haga clic en **siguiente**.
    - Para la **dirección URL del servicio** de inicio de sesión único, escriba la **dirección URL de inicio de sesión** de Salesforce que anotó anteriormente.
    - Seleccione **cargar certificado SAML del proveedor de identidades** y cargue el archivo de certificado que descargó anteriormente.

    ![Agregar la dirección URL del servicio SSO y el certificado SAML](media/proxy-idp-adfs/idp-adfs-cas-sf-app-idp-info.png)

1. En la página siguiente, tome nota de la siguiente información y, a continuación, haga clic en **siguiente**. Necesitará la información más adelante.

    - Cloud App Security dirección URL de inicio de sesión único
    - Cloud App Security atributos y valores

    > [!NOTE]
    > Si ve una opción para cargar el **certificado SAML Cloud App Security para el proveedor de identidades**, haga clic en el vínculo para descargar el archivo de certificado. Lo necesitará más adelante.

    ![En Cloud App Security, tenga en cuenta los atributos y la dirección URL de SSO](media/proxy-idp-adfs/idp-adfs-cas-get-sf-app-external-config.png)

<a name="idp1-complete-custom-app-in-adfs"></a>

## <a name="step-5-complete-the-configuration-of-the-ad-fs-relying-party-trust"></a>Paso 5: completar la configuración de la relación de confianza para usuario autenticado de AD FS

1. De nuevo en la consola de **Administración de AD FS** , haga clic con el botón derecho en la relación de confianza para usuario autenticado que creó anteriormente y, a continuación, seleccione **Editar Directiva de emisión de notificaciones**.

    ![Localizar y editar la emisión de notificaciones de confianza de confianza](media/proxy-idp-adfs/idp-adfs-sf-relying-trust-edit.png)

1. En el cuadro de diálogo **Editar Directiva de emisión de notificaciones** , en **reglas de transformación de emisión**, use la información proporcionada en la tabla siguiente para completar los pasos para crear reglas personalizadas.

    | Nombre de la regla de notificación | Regla personalizada |
    | --- | --- |
    | McasSigningCert | `=> issue(type="McasSigningCert", value="<value>");` donde `<value>` es el valor de **McasSigningCert** del Asistente para Cloud App Security que anotó anteriormente |
    | McasAppId | `=> issue(type="McasAppId", value="<value>");` es el valor de **McasAppId** del asistente para Cloud App Security que anotó anteriormente |

    1. Haga clic en **Agregar regla**, en **plantilla de regla de notificación** , seleccione **enviar notificaciones mediante una regla personalizada** y, a continuación, haga clic en **siguiente**.
    1. En la página **configurar regla** , escriba el nombre de la **regla de notificaciones** correspondiente y la **regla personalizada** proporcionada.

    > [!NOTE]
    > Estas reglas se suman a las reglas o atributos de notificaciones que requiere la aplicación que está configurando.

1. De nuevo en la página relación de confianza para usuario **autenticado** , haga clic con el botón derecho en la relación de confianza para usuario autenticado que creó anteriormente y, a continuación, seleccione **propiedades**.
1. En la pestaña **extremos** , seleccione **extremo de consumidor de aserciones de SAML**, haga clic en **Editar** y reemplace la **dirección URL de confianza** por la Cloud App Security dirección URL de inicio de sesión único que anotó anteriormente y, a continuación, haga clic en **Aceptar**.

    ![Actualizar la dirección URL de confianza de las propiedades de punto de conexión de confianza](media/proxy-idp-adfs/idp-adfs-sf-relying-trust-endpoint-properties.png)

1. Si descargó un **certificado SAML Cloud App Security para el proveedor de identidades**, en la pestaña **firma** , haga clic en **Agregar** y cargue el archivo de certificado y, a continuación, haga clic en **Aceptar**.

    ![Actualizar el certificado SAML de propiedades de firma de confianza de confianza](media/proxy-idp-adfs/idp-adfs-sf-relying-trust-signature-properties.png)

1. Guarde la configuración.

<a name="idp1-get-app-changes-in-cas"></a>

## <a name="step-6-get-the-app-changes-in-cloud-app-security"></a>Paso 6: obtener los cambios de la aplicación en Cloud App Security

De nuevo en la página Cloud App Security cambios en la **aplicación** , realice lo siguiente, pero **no haga clic en finalizar**. Necesitará la información más adelante.

- Copia de la dirección URL de inicio de sesión único de SAML Cloud App Security
- Descargar el certificado SAML Cloud App Security

![Anote el Cloud App Security dirección URL de SSO de SAML y descargue el certificado.](media/proxy-idp-adfs/idp-adfs-cas-sf-app-changes.png)

<a name="idp1-complete-app-changes"></a>

## <a name="step-7-complete-the-app-changes"></a>Paso 7: completar los cambios de la aplicación

En Salesforce, **vaya a configuración configuración**  >    >  **identidad**  >  **única Sign-On configuración** y haga lo siguiente:

1. Recomendado: cree una copia de seguridad de la configuración actual.
1. Reemplace el valor del campo **dirección URL de inicio de sesión del proveedor de identidad** por el Cloud App Security dirección URL de inicio de sesión único de SAML que anotó anteriormente.
1. Cargue el certificado SAML Cloud App Security que descargó anteriormente.
1. Haga clic en **Save**(Guardar).

    > [!NOTE]
    > El certificado SAML Cloud App Security es válido durante un año. Una vez que expire, se deberá generar un nuevo certificado.

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
