---
title: Protección con el control de aplicaciones de acceso condicional de Microsoft Cloud App Security
description: En este artículo encontrará información sobre el funcionamiento del proxy inverso de control de aplicaciones de acceso condicional de Cloud App Security.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 9/23/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: d4b800afa927b8a9151837cfbff76478c98bf71f
ms.sourcegitcommit: 094bb42a198fe733cfd3aec79d74487672846dfa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/24/2019
ms.locfileid: "74460539"
---
# <a name="protect-apps-with-microsoft-cloud-app-security-conditional-access-app-control"></a>Proteger aplicaciones con el control de aplicaciones de acceso condicional de Microsoft Cloud App Security

*Se aplica a: Microsoft Cloud App Security*

>[!div class="step-by-step"]
[SIGUIENTE: Implementación del control de aplicaciones de acceso condicional »](proxy-deployment-aad.md)

En las empresas actuales, a menudo no resulta suficiente con saber lo que sucede en el entorno de nube después de que pase. Le interesa detener las infracciones de seguridad y las fugas en tiempo real, antes de que los empleados intencionadamente o por accidente pongan los datos y la organización en riesgo. Es importante permitir que los usuarios de la organización tengan a su disposición la mayoría de los servicios y las herramientas en aplicaciones de nube, y lleven al trabajo sus propios dispositivos. Al mismo tiempo, se necesitan herramientas que permitan proteger la organización de fugas o robos de datos en tiempo real. Junto con Azure Active Directory, Microsoft Cloud App Security proporciona estas funcionalidades en una experiencia integrada y holística con el control de aplicaciones de acceso condicional.

> [!NOTE]
> To use Cloud App Security Conditional Access App Control, you need an [Azure Active Directory P1 license](https://azure.microsoft.com/pricing/details/active-directory/), and an active Microsoft Cloud App Security subscription or Office 365 E5 license. For a list of featured apps included with Office 365 E5, see [Office 365 featured apps](#O365-apps).

Office 365 E5 license. For a list of apps included with supported Office 365 E5, see Office 365 featured apps

## <a name="how-it-works"></a>Cómo funciona

El Control de aplicaciones de acceso condicional usa una arquitectura de proxy inverso y se integra de forma única con el acceso condicional de Azure AD. El acceso condicional de Azure AD permite exigir el uso de controles de acceso en las aplicaciones de la organización según determinadas condiciones. Las condiciones definen a *quién* (un usuario o un grupo de usuarios), *qué* (qué aplicaciones en la nube) y *dónde* (qué ubicaciones y redes) se aplica una directiva de acceso condicional. Tras establecer las condiciones, puede dirigir a los usuarios a Microsoft Cloud App Security, donde podrá proteger los datos con el control de aplicaciones de acceso condicional, aplicando para ello controles de sesión y acceso.

Gracias al control de aplicaciones de acceso condicional, las sesiones y el acceso a la aplicación de los usuarios se pueden supervisar y controlar en tiempo real según las directivas de sesión y acceso definidas. Las directivas de sesión y acceso se usan en el portal de Cloud App Security para perfeccionar los filtros y establecer las medidas que hay que tomar con respecto a un usuario. Con las directivas de acceso y sesión, puede:

- **Prevent data exfiltration**: You can block the download, cut, copy, and print of sensitive documents on, for example, unmanaged devices.

- **Protect on download**: Instead of blocking the download of sensitive documents, you can require documents to be labeled and protected with Azure Information Protection. This action ensures the document is protected and user access is restricted in a potentially risky session.

- **Prevent upload of unlabeled files**: Before a sensitive file is uploaded, distributed, and used by others, it’s important to make sure that the file has the right label and protection. You can ensure that unlabeled files with sensitive content are blocked from being uploaded until the user classifies the content.

- **Monitor user sessions for compliance**: Risky users are monitored when they sign into apps and their actions are logged from within the session. Puede investigar y analizar el comportamiento de los usuarios para entender dónde (y en qué condiciones) se deben aplicar directivas de sesión en el futuro.

- **Block access**: You can granularly block access for specific apps and users depending on several risk factors. For example, you can block them if they are using client certificates as a form of device management.

- **Block custom activities**: Some applications have unique scenarios that carry risk, for example, sending messages with sensitive content in applications like Microsoft Teams or Slack. In these kinds of scenarios, you can scan messages for sensitive content and block them in real time.

### <a name="how-session-control-works"></a>Funcionamiento del control de sesión

Al crear una directiva de sesión con control de aplicaciones de acceso condicional, podrá controlar las sesiones de usuario redirigiendo al usuario en cuestión a través de un proxy inverso, en lugar de directamente a la aplicación. From then on, user requests and responses go through Cloud App Security rather than directly to the app.

When a session is protected by proxy, all the relevant URLs and cookies are replaced by Cloud App Security. Por ejemplo, si la aplicación devuelve una página con vínculos cuyos dominios terminan en miaplicación.com, el vínculo se reemplazará por dominios que acaben en algo parecido a miaplicación.com.us.cas.ms

This method doesn't require you to install anything on the device making it ideal when monitoring or controlling sessions from unmanaged devices or partner users.

> [!NOTE]
> Cloud App Security aprovecha los Centros de datos de Azure de todo el mundo para proporcionar un rendimiento optimizado a través de la geolocalización. Esto significa que la sesión de un usuario se puede hospedar fuera de una región determinada, dependiendo de los patrones de tráfico y su ubicación. Sin embargo, para proteger su privacidad, no se almacenan datos de la sesión en estos centros de datos.

## <a name="managed-device-identification"></a>Identificación de dispositivos administrados

El control de aplicaciones de acceso condicional permite crear directivas que tienen en cuenta si un dispositivo está administrado o no. Para saber si un dispositivo está administrado o no, esta característica usa lo siguiente:

- Dispositivos compatibles
- Dispositivos unidos a dominio
- Implementación de certificados de cliente

To configure a policy to leverage device management via client certificates:

1. Vaya al engranaje Configuración y elija **Identificación de dispositivos**.
1. Cargue al menos un certificado raíz o intermedio.
1. After the certificate is uploaded, you can create [access policies](access-policy-aad.md) and [session policies](session-policy-aad.md) based on **Device tag** and **Valid client certificate**.

    ![Id. de dispositivo del Control de aplicaciones de acceso condicional](./media/caac-device-id.png)

> [!NOTE]
> Solo se solicita un certificado a un usuario si la sesión coincide con una directiva que use el filtro de certificado de cliente válido.

### <a name="compliant-and-domain-joined-devices"></a>Dispositivos compatibles y unidos a dominio

El acceso condicional de Azure AD permite pasar información sobre los dispositivos compatibles y unidos a un dominio directamente a Microsoft Cloud App Security. Desde allí, se puede desarrollar una directiva de sesión o acceso que use el estado del dispositivo como filtro. Para más información, vea [Introducción a la administración de dispositivos en Azure Active Directory](https://docs.microsoft.com/azure/active-directory/device-management-introduction).

> [!NOTE]
> Some browsers may require additional configuration such as installing an extension. For more information, see [Conditional Access browser support](https://go.microsoft.com/fwlink/?linkid=2102732).

### <a name="client-certificate-authenticated-devices"></a>Dispositivos autenticados con certificado de cliente

El mecanismo de identificación de dispositivos puede solicitar la autenticación de los dispositivos que usan certificados de cliente. Puede usar certificados de cliente existentes ya implementados en la organización o implantar nuevos certificados de cliente a los dispositivos administrados. Después utilizará la presencia de esos certificados para establecer directivas de acceso y sesión.

SSL client certificates are verified via a trust chain. You can upload an X.509 root or intermediate certificate authority (CA) formatted in the PEM certificate format. These certificates must contain the public key of the CA, which is then used to sign the client certificates presented during a session.

Once the certificate is uploaded and a relevant policy is configured, when an applicable session traverses Conditional Access App Control, the Cloud App Security endpoint requests the browser to present the SSL client certificates. The browser serves the SSL client certificates that are installed with a private key. This combination of certificate and private key is done by using the PKCS #12 file format, typically .p12 or .pfx.

When a client certificate check is performed, Cloud App Security checks for the following conditions:

1. The selected client certificate is valid and is under the correct root or intermediate CA.
1. The certificate is not revoked (if CRL is enabled).

> [!NOTE]
> Most major browsers support performing a client certificate check. However, mobile and desktop apps often leverage built-in browsers that may not support this check and therefore affect authentication for these apps.

Para más información sobre cómo implementar certificados de cliente, vea [Implementar el control de la aplicación de acceso condicional para aplicaciones de Azure AD](proxy-deployment-aad.md).

## <a name="supported-apps-and-clients"></a>Aplicaciones y clientes compatibles

Conditional Access App Control currently supports SAML and Open ID Connect apps configured with single sign-on, along with web apps hosted on-premises configured with the [Azure AD App Proxy](https://docs.microsoft.com/azure/active-directory/manage-apps/application-proxy).
> [!NOTE]
> El Control de aplicaciones de acceso condicional también admite aplicaciones configuradas con proveedores de identidades que no sean Azure AD. Para obtener más información sobre este escenario, envíe un correo electrónico a mcaspreview@microsoft.com.

**El control de sesión está disponible para cualquier explorador en las principales plataformas en cualquier sistema operativo**. We recommend using Internet Explorer 11, Microsoft Edge (latest), Google Chrome (latest), Mozilla Firefox (latest), or Apple Safari (latest). Access to mobile and desktop apps can also be blocked or allowed.

> [!NOTE]
> Using the **Client app** filter in access policies can cause the resulting user session to be proxied by Cloud App Security.
>
> In access policies, when using the **Client app** filter it defaults to **Mobile and desktop**. This can cause the resulting user session to be proxied by Cloud App Security. To void this behavior, set the value to **Browser**.
>
> By default, evaluating whether an app is mobile or desktop can cause the resulting user session to be proxied by Cloud App Security. To avoid this behavior, set the Client App filter in your Access policies to be equal to **Browser**.

> [!NOTE]
> Cloud App Security aprovecha los protocolos de Seguridad de la capa de transporte (TLS) 1.2+ para proporcionar el mejor cifrado de la clase. No se podrá obtener acceso a las aplicaciones de cliente nativo y los exploradores que no admitan TLS 1.2+ al configurarse con el control de sesión. Sin embargo, las aplicaciones SaaS que usen TLS 1.1 o versiones anteriores aparecerán en el explorador como usuarias de TLS 1.2+ al configurarse con Cloud App Security.

<a name="featured-apps"></a>By natively integrating with Azure AD, any app that is configured with SAML or Open ID Connect you can onboard any app yourself. In addition, the following apps are featured by Cloud App Security and are already onboarded and ready to use in any tenant:

- AWS
- Azure DevOps (Visual Studio Team Services)
- Azure Portal (versión preliminar)
- Cuadro
- Concur
- CornerStone on Demand
- DocuSign
- Dropbox
- Dynamics 365 CRM (preview)
- Egnyte
- Exchange Online
- G Suite
- Github
- HighQ
- JIRA/Confluence
- OneDrive para la Empresa
- Aprendizaje de LinkedIn
- Power BI
- Salesforce
- ServiceNow
- SharePoent Onlene
- Slack
- Tableau
- Microsoft Teams (versión preliminar)
- Workday
- Workiva
- Workplace de Facebook
- Yammer (versión preliminar)

### <a name="a-ido365-apps-office-365-featured-apps"></a><a id="O365-apps" />Office 365 featured apps

The following is a list of featured apps that are supported in Office 365 Cloud App Security:

- Exchange Online
- OneDrive para la Empresa
- Power BI
- SharePoent Onlene
- Microsoft Teams (versión preliminar)
- Yammer (versión preliminar)

If you're interested in a specific app being featured, [send us details about the app](mailto:casfeedback@microsoft.com). No olvide enviar el caso de uso que le interesa para que podamos incorporarlo.

> [!div class="step-by-step"]
> [SIGUIENTE: Implementación del control de aplicaciones de acceso condicional »](proxy-deployment-aad.md)

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Implementar el control de la aplicación de acceso condicional para aplicaciones de Azure AD](proxy-deployment-aad.md)

[!INCLUDE [Open support ticket](includes/support.md)]
