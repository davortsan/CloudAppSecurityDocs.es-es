---
title: Protección con el control de aplicaciones de acceso condicional de Microsoft Cloud App Security
description: En este artículo encontrará información sobre el funcionamiento del proxy inverso de control de aplicaciones de acceso condicional de Cloud App Security.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 01/15/2020
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: b3517591eba70dde048041c7b55a57679e7cc829
ms.sourcegitcommit: dabfa885ebb82db25a92127d87e8d1283340e834
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/15/2020
ms.locfileid: "76020768"
---
# <a name="protect-apps-with-microsoft-cloud-app-security-conditional-access-app-control"></a>Proteger aplicaciones con el control de aplicaciones de acceso condicional de Microsoft Cloud App Security

*Se aplica a: Microsoft Cloud App Security*

En las empresas actuales, a menudo no resulta suficiente con saber lo que sucede en el entorno de nube después de que pase. Le interesa detener las infracciones de seguridad y las fugas en tiempo real, antes de que los empleados intencionadamente o por accidente pongan los datos y la organización en riesgo. Es importante permitir que los usuarios de la organización tengan a su disposición la mayoría de los servicios y las herramientas en aplicaciones de nube, y lleven al trabajo sus propios dispositivos. Al mismo tiempo, se necesitan herramientas que permitan proteger la organización de fugas o robos de datos en tiempo real. Junto con Azure Active Directory (Azure AD), Microsoft Cloud App Security ofrece estas funcionalidades en una experiencia holística e integrada con Control de aplicaciones de acceso condicional.

> [!NOTE]
>
> - Para usar Cloud App Security Control de aplicaciones de acceso condicional, necesita una [licencia de Azure Active Directory P1](https://azure.microsoft.com/pricing/details/active-directory/)y una suscripción de Microsoft Cloud App Security o de Office 365 E5. Para obtener una lista de las aplicaciones destacadas incluidas con Office 365 E5, consulte [aplicaciones destacadas de office 365](#O365-apps).
> - Los controles de acceso y de sesión también admiten las aplicaciones configuradas con proveedores de identidades distintos de Azure AD. Para obtener más información sobre este escenario, envíe un correo electrónico a mcaspreview@microsoft.com.

## <a name="how-it-works"></a>Cómo funciona

Control de aplicaciones de acceso condicional usa una arquitectura de proxy inverso y se integra de forma exclusiva con el acceso condicional de Azure AD. Azure AD el acceso condicional permite aplicar controles de acceso en las aplicaciones de la organización en función de ciertas condiciones. Las condiciones definen *quién* (usuario o grupo de usuarios) y *qué* (qué aplicaciones en la nube) y *dónde* (a qué ubicaciones y redes) se aplica una directiva de acceso condicional. Tras establecer las condiciones, puede dirigir a los usuarios a Microsoft Cloud App Security, donde podrá proteger los datos con el control de aplicaciones de acceso condicional, aplicando para ello controles de sesión y acceso.

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

El control de aplicaciones de acceso condicional permite crear directivas que tienen en cuenta si un dispositivo está administrado o no. Para identificar el estado de un dispositivo, puede configurar las directivas de acceso y de sesión para comprobar lo siguiente:

- Dispositivos compatibles con Microsoft Intune (Intune)
- Dispositivos unidos a la implementación híbrida de Azure AD
- Presencia de certificados de cliente en una cadena de confianza

### <a name="intune-compliant-and-hybrid-azure-ad-joined-devices"></a>Dispositivos de Azure AD híbridos y compatibles con Intune

Azure AD el acceso condicional permite pasar información del dispositivo compatible y de la Unión híbrida directamente a Microsoft Cloud App Security. Desde allí, se puede desarrollar una directiva de sesión o acceso que use el estado del dispositivo como filtro. Para más información, vea [Introducción a la administración de dispositivos en Azure Active Directory](https://docs.microsoft.com/azure/active-directory/device-management-introduction).

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

Para configurar una directiva para aprovechar la administración de dispositivos mediante certificados de cliente:

1. En Cloud App Security, en la barra de menús, haga clic en el ![icono](media/settings-icon.png "icono de configuración") de configuración engranaje de configuración y seleccione **configuración**.

1. Seleccione la pestaña **identificación del dispositivo** .
1. Cargue todos los certificados raíz o intermedios que necesite.

Una vez cargados los certificados, puede crear directivas de acceso y de sesión basadas en la **etiqueta del dispositivo** y el certificado de **cliente válido**.

## <a name="supported-apps-and-clients"></a>Aplicaciones y clientes compatibles

Los controles de acceso y de sesión se pueden aplicar a cualquier inicio de sesión único interactivo, mediante los protocolos de autenticación SAML 2,0 o Open ID Connect. También puede aplicar estos controles a las aplicaciones hospedadas localmente con el proxy de [aplicación de Azure ad](https://docs.microsoft.com/azure/active-directory/manage-apps/application-proxy). Además, los controles de acceso se pueden aplicar a las aplicaciones de cliente de escritorio y móviles nativas.

Cloud App Security identifica aplicaciones que usan información disponible en el catálogo de aplicaciones en la nube. Algunas organizaciones y usuarios personalizan las aplicaciones mediante la adición de complementos. Sin embargo, para que los controles de sesión funcionen correctamente con estos complementos, los dominios personalizados asociados deben agregarse a la aplicación correspondiente en el catálogo.

> [!NOTE]
> La aplicación Authenticator, entre otros flujos de inicio de sesión de aplicaciones cliente nativas, usa un flujo de inicio de sesión no interactivo y no se puede usar con controles de acceso.

### <a name="access-controls"></a>Controles de acceso

Muchas organizaciones que optan por usar controles de sesión para aplicaciones en la nube para controlar las actividades en la sesión, también pueden aplicar controles de acceso para bloquear el mismo conjunto de aplicaciones de cliente de escritorio y móviles nativas, lo que proporciona una seguridad completa para las aplicaciones.

Puede bloquear el acceso a las aplicaciones de cliente de escritorio y móviles nativas con directivas de acceso. para ello, establezca el filtro de la **aplicación cliente** en **móvil y escritorio**. Algunas aplicaciones cliente nativas se pueden reconocer individualmente, mientras que otras que forman parte de un conjunto de aplicaciones solo se pueden identificar como su aplicación de nivel superior. Por ejemplo, las aplicaciones como SharePoint Online solo se pueden reconocer mediante la creación de una directiva de acceso que se aplica a las aplicaciones de Office 365.

> [!NOTE]
> A menos que el filtro de **aplicación cliente** se establezca específicamente en **móvil y escritorio**, la Directiva de acceso resultante solo se aplicará a las sesiones del explorador. La razón de esto es evitar que las sesiones de usuario se configuran de forma inadvertida para el proxy, lo que puede ser un subproducto del uso de este filtro. Aunque la mayoría de los exploradores principales admiten la comprobación de certificados de cliente, algunas aplicaciones móviles y de escritorio usan exploradores integrados que es posible que no admitan esta comprobación. Por lo tanto, el uso de este filtro puede afectar a la autenticación de estas aplicaciones.

### <a name="session-controls"></a>Controles de sesión

**El control de sesión está disponible para cualquier explorador en las principales plataformas en cualquier sistema operativo**. Se recomienda usar Internet Explorer 11, Microsoft Edge (latest), Google Chrome (latest), Mozilla Firefox (latest) o Apple Safari (latest). También se puede bloquear o permitir el acceso a aplicaciones móviles y de escritorio.

> [!NOTE]
> Cloud App Security aprovecha los protocolos de Seguridad de la capa de transporte (TLS) 1.2+ para proporcionar el mejor cifrado de la clase. Las aplicaciones cliente nativas y los exploradores que no admiten TLS 1.2 + no serán accesibles cuando se configuran con el control de sesión. Sin embargo, las aplicaciones SaaS que usen TLS 1.1 o versiones anteriores aparecerán en el explorador como usuarias de TLS 1.2+ al configurarse con Cloud App Security.

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

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Implementación de Control de aplicaciones de acceso condicional para aplicaciones destacadas](proxy-deployment-aad.md)

> [!div class="nextstepaction"]
> [Implementación del Control de aplicaciones de acceso condicional para cualquier aplicación](proxy-deployment-any-app.md)

[!INCLUDE [Open support ticket](includes/support.md)]
