---
title: Protección con el control de aplicaciones de acceso condicional de Microsoft Cloud App Security
description: En este artículo encontrará información sobre el funcionamiento del proxy inverso de control de aplicaciones de acceso condicional de Cloud App Security.
keywords: ''
author: ShlomoSagir-MS
ms.author: shsagir
manager: ShlomoSagir-MS
ms.date: 7/2/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 35a43120-bf67-4cf9-9b48-ebe157dbbd18
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: fca34e1bb6a9f83928ef3a4eaf388090468ce06a
ms.sourcegitcommit: ee00e0033bf45a5f795bfd3e1d71fa1f70f97acb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/02/2019
ms.locfileid: "67511366"
---
# <a name="protect-apps-with-microsoft-cloud-app-security-conditional-access-app-control"></a>Proteger aplicaciones con el control de aplicaciones de acceso condicional de Microsoft Cloud App Security

*Se aplica a: Microsoft Cloud App Security*

>[!div class="step-by-step"]
[SIGUIENTE: Implementación del control de aplicaciones de acceso condicional »](proxy-deployment-aad.md)

En las empresas actuales, a menudo no resulta suficiente con saber lo que sucede en el entorno de nube después de que pase. Le interesa detener las infracciones de seguridad y las fugas en tiempo real, antes de que los empleados intencionadamente o por accidente pongan los datos y la organización en riesgo. Es importante permitir que los usuarios de la organización tengan a su disposición la mayoría de los servicios y las herramientas en aplicaciones de nube, y lleven al trabajo sus propios dispositivos. Al mismo tiempo, se necesitan herramientas que permitan proteger la organización de fugas o robos de datos en tiempo real. Junto con Azure Active Directory, Microsoft Cloud App Security proporciona estas funcionalidades en una experiencia integrada y holística con el control de aplicaciones de acceso condicional.

> [!NOTE]
> Para usar Control de aplicaciones de acceso condicional de Cloud App, necesita una [licencia P1 de Azure Active Directory](https://azure.microsoft.com/pricing/details/active-directory/) y una suscripción activa de Microsoft Cloud App Security.
>

## <a name="how-it-works"></a>Cómo funciona

El Control de aplicaciones de acceso condicional usa una arquitectura de proxy inverso y se integra de forma única con el acceso condicional de Azure AD. El acceso condicional de Azure AD permite exigir el uso de controles de acceso en las aplicaciones de la organización según determinadas condiciones. Las condiciones definen a *quién* (un usuario o un grupo de usuarios), *qué* (qué aplicaciones en la nube) y *dónde* (qué ubicaciones y redes) se aplica una directiva de acceso condicional. Tras establecer las condiciones, puede dirigir a los usuarios a Microsoft Cloud App Security, donde podrá proteger los datos con el control de aplicaciones de acceso condicional, aplicando para ello controles de sesión y acceso.

Gracias al control de aplicaciones de acceso condicional, las sesiones y el acceso a la aplicación de los usuarios se pueden supervisar y controlar en tiempo real según las directivas de sesión y acceso definidas. Las directivas de sesión y acceso se usan en el portal de Cloud App Security para perfeccionar los filtros y establecer las medidas que hay que tomar con respecto a un usuario. Con las directivas de acceso y sesión, puede:

- **Evitar la filtración de datos**: Puede bloquear la descarga, cortar, copiar e imprimir documentos confidenciales de, por ejemplo, los dispositivos no administrados.

- **Proteger las descargas**: En lugar de bloquear la descarga de documentos confidenciales, puede requerir documentos etiquetados y protegidos con Azure Information Protection. Esta acción garantiza que el documento está protegido y se restringe el acceso de usuario en una sesión potencialmente peligrosa.

- **Evitar la carga de archivos no etiquetados**: Antes de que un archivo confidencial se cargó, distribuido y utilizado por otras personas, es importante asegurarse de que el archivo tiene la etiqueta de la derecha y la protección. Puede asegurarse de que los archivos no etiquetados con contenido confidencial se impide que se carga hasta que el usuario clasifica el contenido.

- **Supervisar las sesiones de usuario para el cumplimiento**: los usuarios que entrañen riesgo se supervisan cuando inician sesión en aplicaciones y sus acciones se registran en la sesión. Puede investigar y analizar el comportamiento de los usuarios para entender dónde (y en qué condiciones) se deben aplicar directivas de sesión en el futuro.

- **Bloquear acceso**: Forma granular puede bloquear el acceso para aplicaciones específicas y usuarios en función de varios factores de riesgo. Por ejemplo, puede bloquearlos si usan certificados de cliente como una forma de administración de dispositivos.

- **Bloquear las actividades personalizadas**: Algunas aplicaciones tienen escenarios únicos que llevan el riesgo, por ejemplo, enviar mensajes con contenido confidencial en aplicaciones como Microsoft Teams o Slack. En estos tipos de escenarios, puede analizar los mensajes de contenido confidencial y bloquearlas en tiempo real.

### <a name="how-session-control-works"></a>Funcionamiento del control de sesión

Al crear una directiva de sesión con control de aplicaciones de acceso condicional, podrá controlar las sesiones de usuario redirigiendo al usuario en cuestión a través de un proxy inverso, en lugar de directamente a la aplicación. Desde ese momento, las solicitudes de usuario y las respuestas pasan a través de Cloud App Security, en lugar de directamente a la aplicación.

Cuando una sesión está protegida por el proxy, todas las direcciones URL y el cookies relevantes se reemplazan por Cloud App Security. Por ejemplo, si la aplicación devuelve una página con vínculos cuyos dominios terminan en miaplicación.com, el vínculo se reemplazará por dominios que acaben en algo parecido a miaplicación.com.us.cas.ms

Este método no requiere que se instale nada en el dispositivo, por lo ideal al supervisar o controlar las sesiones desde dispositivos no administrados o los usuarios asociados.

## <a name="managed-device-identification"></a>Identificación de dispositivos administrados

El control de aplicaciones de acceso condicional permite crear directivas que tienen en cuenta si un dispositivo está administrado o no. Para saber si un dispositivo está administrado o no, esta característica usa lo siguiente:

- Dispositivos compatibles
- Dispositivos unidos a dominio
- Implementación de certificados de cliente
 
### <a name="compliant-and-domain-joined-devices"></a>Dispositivos compatibles y unidos a dominio

El acceso condicional de Azure AD permite pasar información sobre los dispositivos compatibles y unidos a un dominio directamente a Microsoft Cloud App Security. Desde allí, se puede desarrollar una directiva de sesión o acceso que use el estado del dispositivo como filtro.
Para más información, vea [Introducción a la administración de dispositivos en Azure Active Directory](https://docs.microsoft.com/azure/active-directory/device-management-introduction). 

### <a name="client-certificate-authenticated-devices"></a>Dispositivos autenticados con certificado de cliente

El mecanismo de identificación de dispositivos puede solicitar la autenticación de los dispositivos que usan certificados de cliente. Puede usar certificados de cliente existentes ya implementados en la organización o implantar nuevos certificados de cliente a los dispositivos administrados. Después utilizará la presencia de esos certificados para establecer directivas de acceso y sesión.

Certificados de cliente SSL se comprueban a través de una cadena de confianza. Puede cargar un X.509 raíz o intermedio de certificación (CA) con el formato de certificado PEM. Estos certificados deben contener la clave pública de la entidad de certificación, que, a continuación, se usa para firmar los certificados de cliente presentados durante una sesión.

Una vez cargado el certificado y se configura una directiva pertinente, cuando una sesión que corresponda atraviesa Conditional Access App Control, el punto de conexión de Cloud App Security solicita al explorador que presentan los certificados de cliente SSL. El explorador sirve al cliente SSL certificados que se instalan con una clave privada. Esta combinación de certificado y clave privada se realiza mediante el PKCS #12 formato de archivo, normalmente. p12 o pfx.

Cuando se realiza una comprobación de certificado de cliente, Cloud App Security comprueba las condiciones siguientes:

1. El certificado de cliente seleccionado es válido y está en la raíz correcta o una entidad de certificación intermedia.
1. No se revoca el certificado (si está habilitada la CRL).

Para más información sobre cómo implementar certificados de cliente, vea [Implementar el control de la aplicación de acceso condicional para aplicaciones de Azure AD](proxy-deployment-aad.md).

## <a name="supported-apps-and-clients"></a>Aplicaciones y clientes compatibles

El Control de aplicaciones de acceso condicional es compatible actualmente con aplicaciones de SAML y Open ID Connect configuradas con inicio de sesión único, junto con las aplicaciones web hospedadas de forma local configuradas con el [Proxy de aplicación de Azure AD](https://docs.microsoft.com/azure/active-directory/manage-apps/application-proxy).
> [!NOTE]
> El Control de aplicaciones de acceso condicional también admite aplicaciones configuradas con proveedores de identidades que no sean Azure AD. Para obtener más información sobre este escenario, envíe un correo electrónico a mcaspreview@microsoft.com.

**El control de sesión está disponible para cualquier explorador en las principales plataformas en cualquier sistema operativo**. Se recomienda usar Internet Explorer 11, Microsoft Edge (versión más reciente), Google Chrome (más reciente), Mozilla Firefox (más reciente) o Apple Safari (más reciente). Las aplicaciones móviles y de escritorio también pueden bloquearse o permitirse. Mediante la integración nativa con Azure AD, cualquier aplicación que está configurado con SAML u OpenID Connect puede ser self incorporado. Además, las siguientes aplicaciones se destaquen por Cloud App Security y ya están incorporadas y listos para su uso en todos los inquilinos:

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
- Power BI
- Salesforce
- ServiceNow
- SharePoint Online
- Slack
- Tableau
- Microsoft Teams (versión preliminar)
- Workday
- Workiva
- Workplace de Facebook
- Yammer (versión preliminar)

Si está interesado en una aplicación específica a ser destacada, [envíenos los detalles acerca de la aplicación](mailto:casfeedback@microsoft.com). No olvide enviar el caso de uso que le interesa para que podamos incorporarlo.

>[!div class="step-by-step"]
[SIGUIENTE: Implementación del control de aplicaciones de acceso condicional »](proxy-deployment-aad.md)

## <a name="next-steps"></a>Pasos siguientes
[Implementar el control de la aplicación de acceso condicional para aplicaciones de Azure AD](proxy-deployment-aad.md)

[Los clientes Premier también pueden crear una solicitud de soporte técnico directamente en el portal Premier.](https://premier.microsoft.com/)