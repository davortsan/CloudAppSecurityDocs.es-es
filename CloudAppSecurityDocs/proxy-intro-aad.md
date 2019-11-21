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
ms.openlocfilehash: 6e15775be1435c47b9f2df1cc73f3e4b5aa0ddd4
ms.sourcegitcommit: 4fb014e3563b8254635440f24e10b250af66c7f2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/20/2019
ms.locfileid: "74239948"
---
# <a name="protect-apps-with-microsoft-cloud-app-security-conditional-access-app-control"></a>Proteger aplicaciones con el control de aplicaciones de acceso condicional de Microsoft Cloud App Security

*Se aplica a: Microsoft Cloud App Security*

>[!div class="step-by-step"]
[SIGUIENTE: Implementación del control de aplicaciones de acceso condicional »](proxy-deployment-aad.md)

En las empresas actuales, a menudo no resulta suficiente con saber lo que sucede en el entorno de nube después de que pase. Le interesa detener las infracciones de seguridad y las fugas en tiempo real, antes de que los empleados intencionadamente o por accidente pongan los datos y la organización en riesgo. Es importante permitir que los usuarios de la organización tengan a su disposición la mayoría de los servicios y las herramientas en aplicaciones de nube, y lleven al trabajo sus propios dispositivos. Al mismo tiempo, se necesitan herramientas que permitan proteger la organización de fugas o robos de datos en tiempo real. Junto con Azure Active Directory, Microsoft Cloud App Security proporciona estas funcionalidades en una experiencia integrada y holística con el control de aplicaciones de acceso condicional.

> [!NOTE]
> Para usar Cloud App Security Control de aplicaciones de acceso condicional, necesita una [licencia de Azure Active Directory P1](https://azure.microsoft.com/pricing/details/active-directory/)y una suscripción de Microsoft Cloud App Security o de Office 365 E5. Para obtener una lista de las aplicaciones destacadas incluidas con Office 365 E5, consulte [aplicaciones destacadas de office 365](#O365-apps).

Licencia de Office 365 E5. Para obtener una lista de las aplicaciones incluidas en el soporte técnico 365 E5 de Office, consulte Office 365 aplicaciones destacadas

## <a name="how-it-works"></a>Cómo funciona

El Control de aplicaciones de acceso condicional usa una arquitectura de proxy inverso y se integra de forma única con el acceso condicional de Azure AD. El acceso condicional de Azure AD permite exigir el uso de controles de acceso en las aplicaciones de la organización según determinadas condiciones. Las condiciones definen a *quién* (un usuario o un grupo de usuarios), *qué* (qué aplicaciones en la nube) y *dónde* (qué ubicaciones y redes) se aplica una directiva de acceso condicional. Tras establecer las condiciones, puede dirigir a los usuarios a Microsoft Cloud App Security, donde podrá proteger los datos con el control de aplicaciones de acceso condicional, aplicando para ello controles de sesión y acceso.

Gracias al control de aplicaciones de acceso condicional, las sesiones y el acceso a la aplicación de los usuarios se pueden supervisar y controlar en tiempo real según las directivas de sesión y acceso definidas. Las directivas de sesión y acceso se usan en el portal de Cloud App Security para perfeccionar los filtros y establecer las medidas que hay que tomar con respecto a un usuario. Con las directivas de acceso y sesión, puede:

- **Impedir la exfiltración de datos**: puede bloquear la descarga, cortar, copiar e imprimir documentos confidenciales en, por ejemplo, dispositivos no administrados.

- **Proteger al descargar: en**lugar de bloquear la descarga de documentos confidenciales, puede requerir que los documentos estén etiquetados y protegidos con Azure Information Protection. Esta acción garantiza que el documento está protegido y el acceso de usuario está restringido en una sesión potencialmente arriesgada.

- **Evitar la carga de archivos sin etiquetar**: antes de que otros usuarios carguen, distribuyan y usen otros, es importante asegurarse de que el archivo tiene la etiqueta y la protección adecuadas. Puede asegurarse de que los archivos sin etiqueta con contenido confidencial estén bloqueados para que no se carguen hasta que el usuario clasifique el contenido.

- **Supervisar las sesiones de usuario para el cumplimiento**: los usuarios con riesgo se supervisan cuando inician sesión en las aplicaciones y sus acciones se registran desde dentro de la sesión. Puede investigar y analizar el comportamiento de los usuarios para entender dónde (y en qué condiciones) se deben aplicar directivas de sesión en el futuro.

- **Bloquear acceso**: puede bloquear el acceso a aplicaciones y usuarios específicos en función de varios factores de riesgo. Por ejemplo, puede bloquearlos si usan certificados de cliente como forma de administración de dispositivos.

- **Bloquear actividades personalizadas**: algunas aplicaciones tienen escenarios únicos que incluyen el riesgo, por ejemplo, el envío de mensajes con contenido confidencial en aplicaciones como Microsoft Teams o el margen de demora. En estos tipos de escenarios, puede examinar mensajes para detectar contenido confidencial y bloquearlos en tiempo real.

### <a name="how-session-control-works"></a>Funcionamiento del control de sesión

Al crear una directiva de sesión con control de aplicaciones de acceso condicional, podrá controlar las sesiones de usuario redirigiendo al usuario en cuestión a través de un proxy inverso, en lugar de directamente a la aplicación. A partir de entonces, las solicitudes y respuestas de usuario pasan por Cloud App Security en lugar de hacerlo directamente a la aplicación.

Cuando una sesión está protegida por el proxy, todas las direcciones URL y cookies pertinentes se sustituyen por Cloud App Security. Por ejemplo, si la aplicación devuelve una página con vínculos cuyos dominios terminan en miaplicación.com, el vínculo se reemplazará por dominios que acaben en algo parecido a miaplicación.com.us.cas.ms

Este método no requiere la instalación de nada en el dispositivo, por lo que resulta idóneo al supervisar o controlar sesiones desde dispositivos no administrados o usuarios asociados.

> [!NOTE]
> Cloud App Security aprovecha los Centros de datos de Azure de todo el mundo para proporcionar un rendimiento optimizado a través de la geolocalización. Esto significa que la sesión de un usuario se puede hospedar fuera de una región determinada, dependiendo de los patrones de tráfico y su ubicación. Sin embargo, para proteger su privacidad, no se almacenan datos de la sesión en estos centros de datos.

## <a name="managed-device-identification"></a>Identificación de dispositivos administrados

El control de aplicaciones de acceso condicional permite crear directivas que tienen en cuenta si un dispositivo está administrado o no. Para saber si un dispositivo está administrado o no, esta característica usa lo siguiente:

- Dispositivos compatibles
- Dispositivos unidos a dominio
- Implementación de certificados de cliente

Para configurar una directiva para aprovechar la administración de dispositivos mediante certificados de cliente:

1. Vaya al engranaje Configuración y elija **Identificación de dispositivos**.
1. Cargue al menos un certificado raíz o intermedio.
1. Una vez cargado el certificado, puede crear [directivas de acceso](access-policy-aad.md) y directivas de [sesión](session-policy-aad.md) basadas en la **etiqueta del dispositivo** y el certificado de **cliente válido**.

    ![Id. de dispositivo del Control de aplicaciones de acceso condicional](./media/caac-device-id.png)

> [!NOTE]
> Solo se solicita un certificado a un usuario si la sesión coincide con una directiva que use el filtro de certificado de cliente válido.

### <a name="compliant-and-domain-joined-devices"></a>Dispositivos compatibles y unidos a dominio

El acceso condicional de Azure AD permite pasar información sobre los dispositivos compatibles y unidos a un dominio directamente a Microsoft Cloud App Security. Desde allí, se puede desarrollar una directiva de sesión o acceso que use el estado del dispositivo como filtro. Para más información, vea [Introducción a la administración de dispositivos en Azure Active Directory](https://docs.microsoft.com/azure/active-directory/device-management-introduction).

> [!NOTE]
> Algunos exploradores pueden requerir una configuración adicional, como la instalación de una extensión. Para obtener más información, consulte [compatibilidad con el explorador de acceso condicional](https://go.microsoft.com/fwlink/?linkid=2102732).

### <a name="client-certificate-authenticated-devices"></a>Dispositivos autenticados con certificado de cliente

El mecanismo de identificación de dispositivos puede solicitar la autenticación de los dispositivos que usan certificados de cliente. Puede usar certificados de cliente existentes ya implementados en la organización o implantar nuevos certificados de cliente a los dispositivos administrados. Después utilizará la presencia de esos certificados para establecer directivas de acceso y sesión.

Los certificados de cliente SSL se comprueban a través de una cadena de confianza. Puede cargar una entidad de certificación X. 509 o una entidad de certificación (CA) intermedia con formato en el formato de certificado PEM. Estos certificados deben contener la clave pública de la CA, que se usa para firmar los certificados de cliente presentados durante una sesión.

Una vez cargado el certificado y configurada una directiva relevante, cuando una sesión aplicable atraviesa Control de aplicaciones de acceso condicional, el punto de conexión de Cloud App Security solicita al explorador que presente los certificados de cliente SSL. El explorador sirve a los certificados de cliente SSL que se instalan con una clave privada. Esta combinación de certificado y clave privada se realiza mediante el formato de archivo PKCS #12, normalmente. p12 o. pfx.

Cuando se realiza una comprobación de certificado de cliente, Cloud App Security comprueba las condiciones siguientes:

1. El certificado de cliente seleccionado es válido y está en la entidad de certificación raíz o intermedia correcta.
1. No se revoca el certificado (si la CRL está habilitada).

> [!NOTE]
> La mayoría de los exploradores principales admiten la comprobación de certificados de cliente. Sin embargo, las aplicaciones móviles y de escritorio a menudo aprovechan los exploradores integrados que pueden no admitir esta comprobación y, por tanto, afectan a la autenticación de estas aplicaciones.

Para más información sobre cómo implementar certificados de cliente, vea [Implementar el control de la aplicación de acceso condicional para aplicaciones de Azure AD](proxy-deployment-aad.md).

## <a name="supported-apps-and-clients"></a>Aplicaciones y clientes compatibles

Actualmente, Control de aplicaciones de acceso condicional admite las aplicaciones SAML y Open ID Connect configuradas con el inicio de sesión único, junto con las aplicaciones web hospedadas localmente y configuradas con el [Proxy aplicación de Azure ad](https://docs.microsoft.com/azure/active-directory/manage-apps/application-proxy).
> [!NOTE]
> El Control de aplicaciones de acceso condicional también admite aplicaciones configuradas con proveedores de identidades que no sean Azure AD. Para obtener más información sobre este escenario, envíe un correo electrónico a mcaspreview@microsoft.com.

**El control de sesión está disponible para cualquier explorador en las principales plataformas en cualquier sistema operativo**. Se recomienda usar Internet Explorer 11, Microsoft Edge (latest), Google Chrome (latest), Mozilla Firefox (latest) o Apple Safari (latest). También se puede bloquear o permitir el acceso a aplicaciones móviles y de escritorio.

> [!NOTE]
> El uso del filtro de la **aplicación cliente** en las directivas de acceso puede hacer que la sesión de usuario resultante sea proxy por Cloud App Security.
>
> En las directivas de acceso, cuando se usa el filtro de **aplicación cliente** , el valor predeterminado es **móvil y escritorio**. Esto puede hacer que la sesión de usuario resultante sea proxy mediante Cloud App Security. Para anular este comportamiento, establezca el valor en **Explorador**.
>
> De forma predeterminada, la evaluación de si una aplicación es móvil o de escritorio puede hacer que la sesión de usuario resultante sea proxy mediante Cloud App Security. Para evitar este comportamiento, establezca el filtro de la aplicación cliente en las directivas de acceso para que sea igual al **Explorador**.

> [!NOTE]
> Cloud App Security aprovecha los protocolos de Seguridad de la capa de transporte (TLS) 1.2+ para proporcionar el mejor cifrado de la clase. No se podrá obtener acceso a las aplicaciones de cliente nativo y los exploradores que no admitan TLS 1.2+ al configurarse con el control de sesión. Sin embargo, las aplicaciones SaaS que usen TLS 1.1 o versiones anteriores aparecerán en el explorador como usuarias de TLS 1.2+ al configurarse con Cloud App Security.

<a name="featured-apps"></a>Al integrar de forma nativa con Azure AD, cualquier aplicación configurada con SAML o Open ID Connect puede incorporar cualquier aplicación. Además, las siguientes aplicaciones se incluyen en Cloud App Security y ya se incorporan y están listas para usarse en cualquier inquilino:

- AWS
- Azure DevOps (Visual Studio Team Services)
- Azure Portal (versión preliminar)
- Cuadro
- Concur
- CornerStone on Demand
- DocuSign
- Dropbox
- Dynamics 365 CRM (versión preliminar)
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

### <a name="a-ido365-apps-office-365-featured-apps"></a><a id="O365-apps" />aplicaciones destacadas de Office 365

A continuación se muestra una lista de las aplicaciones destacadas que se admiten en Office 365 Cloud App Security:

- Exchange Online
- OneDrive para la Empresa
- Power BI
- SharePoent Onlene
- Microsoft Teams (versión preliminar)
- Yammer (versión preliminar)

Si está interesado en una aplicación específica, [envíenos detalles sobre la aplicación](mailto:casfeedback@microsoft.com). No olvide enviar el caso de uso que le interesa para que podamos incorporarlo.

> [!div class="step-by-step"]
> [SIGUIENTE: Implementación del control de aplicaciones de acceso condicional »](proxy-deployment-aad.md)

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Implementar el control de la aplicación de acceso condicional para aplicaciones de Azure AD](proxy-deployment-aad.md)

[Los clientes Premier también pueden crear una solicitud de soporte técnico directamente en el portal Premier.](https://premier.microsoft.com/)
