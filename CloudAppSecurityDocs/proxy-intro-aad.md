---
title: Protección con el control de aplicaciones de acceso condicional de Microsoft Cloud App Security
description: En este artículo encontrará información sobre el funcionamiento del proxy inverso de control de aplicaciones de acceso condicional de Cloud App Security.
keywords: ''
author: ShlomoSagir-MS
ms.author: shsagir
manager: shsagir
ms.date: 06/04/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 35a43120-bf67-4cf9-9b48-ebe157dbbd18
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 60b24e5da6fb0e8962426a49a2e568672c4ac6a9
ms.sourcegitcommit: ea1c0f7638eaf0601ae476fea0d40e01bf8a6f4d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/20/2019
ms.locfileid: "67298921"
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

- **Bloquear las descargas**: puede bloquear la descarga de documentos confidenciales. Por ejemplo, en los dispositivos no administrados.

- **Proteger las descargas**: en lugar de bloquear la descarga de documentos confidenciales, puede requerir que los documentos se protejan con cifrado al descargarse. Este cifrado garantiza que el documento está protegido y el acceso de usuario debe autenticarse si se descargan datos en un dispositivo que no es de confianza. 

- **Supervisar las sesiones de usuario con un nivel de confianza bajo**: los usuarios que entrañen riesgo se supervisan cuando inician sesión en aplicaciones y sus acciones se registran en la sesión. Puede investigar y analizar el comportamiento de los usuarios para entender dónde (y en qué condiciones) se deben aplicar directivas de sesión en el futuro. 

- **Bloquear el acceso**: puede bloquear por completo el acceso a aplicaciones específicas a usuarios de dispositivos no administrados o de redes no corporativas.

- **Crear modo de solo lectura**: mediante la supervisión y el bloqueo de actividades personalizadas dentro de la aplicación, puede crear un modo de solo lectura en aplicaciones específicas para usuarios concretos.  

- **Restringir las sesiones de usuario desde redes no corporativas**: los usuarios que acceden a una aplicación protegida desde una ubicación que no forma parte de la red corporativa tienen un acceso restringido. La descarga de material confidencial está bloqueada o protegida.

### <a name="how-session-control-works"></a>Funcionamiento del control de sesión

Al crear una directiva de sesión con control de aplicaciones de acceso condicional, podrá controlar las sesiones de usuario redirigiendo al usuario en cuestión a través de un proxy inverso, en lugar de directamente a la aplicación. A partir de ese momento, las solicitudes y respuestas del usuario pasarán por Microsoft Cloud App Security en lugar de ir directamente a la aplicación.

Para mantener al usuario dentro de la sesión, todas las direcciones URL, scripts de Java y cookies pertinentes de la sesión de aplicación se reemplazan por direcciones URL de Microsoft Cloud App Security. Por ejemplo, si la aplicación devuelve una página con vínculos cuyos dominios terminan en miaplicación.com, el vínculo se reemplazará por dominios que acaben en algo parecido a miaplicación.com.us.cas.ms 

Este método no requiere que se instale nada en el dispositivo. Por tanto, es ideal para supervisar sesiones desde dispositivos no administrados. 

Después de que una sesión se dirija a través de Microsoft Cloud App Security, se pueden realizar las siguientes acciones:

1. Inspeccionar el tráfico en busca de actividades de usuario
2. Mostrar las actividades detectadas en el registro de actividades de Microsoft Cloud App Security
3. Guardar los registros de tráfico y analizarlos
4. Permitir que el administrador exporte los registros de tráfico
5. Exigir la aplicación de directivas en la sesión

## <a name="managed-device-identification"></a>Identificación de dispositivos administrados

El control de aplicaciones de acceso condicional permite crear directivas que tienen en cuenta si un dispositivo está administrado o no. Para saber si un dispositivo está administrado o no, esta característica usa lo siguiente:

- Dispositivos compatibles
- Dispositivos unidos a dominio
- Implementación de certificados de cliente
 
### <a name="compliant-and-domain-joined-devices"></a>Dispositivos compatibles y unidos a dominio

El acceso condicional de Azure AD permite pasar información sobre los dispositivos compatibles y unidos a un dominio directamente a Microsoft Cloud App Security. Desde allí, se puede desarrollar una directiva de sesión o acceso que use el estado del dispositivo como filtro.
Para más información, vea [Introducción a la administración de dispositivos en Azure Active Directory](https://docs.microsoft.com/azure/active-directory/device-management-introduction). 

### <a name="client-certificate-authenticated-devices"></a>Dispositivos autenticados con certificado de cliente

El mecanismo de identificación de dispositivos puede solicitar la autenticación de los dispositivos que usan certificados de cliente. Puede usar certificados de cliente existentes ya implementados en la organización o implantar nuevos certificados de cliente a los dispositivos administrados. Después utilizará la presencia de esos certificados para establecer directivas de acceso y sesión. Para más información sobre cómo implementar certificados de cliente, vea [Implementar el control de la aplicación de acceso condicional para aplicaciones de Azure AD](proxy-deployment-aad.md).
 
## <a name="supported-apps-and-clients"></a>Aplicaciones y clientes compatibles

El Control de aplicaciones de acceso condicional es compatible actualmente con aplicaciones de SAML y Open ID Connect configuradas con inicio de sesión único, junto con las aplicaciones web hospedadas de forma local configuradas con el [Proxy de aplicación de Azure AD](https://docs.microsoft.com/azure/active-directory/manage-apps/application-proxy).
> [!NOTE]
> El Control de aplicaciones de acceso condicional también admite aplicaciones configuradas con proveedores de identidades que no sean Azure AD. Para obtener más información sobre este escenario, envíe un correo electrónico a mcaspreview@microsoft.com.

**El control de sesión está disponible para cualquier explorador en las principales plataformas en cualquier sistema operativo**. Las aplicaciones móviles y de escritorio también pueden bloquearse o permitirse. Gracias a la integración nativa con Azure AD, se admiten aplicaciones que estén configuradas con SAML o aplicaciones Open ID Connect con inicio de sesión único en Azure AD, incluidas estas aplicaciones destacadas:

- AWS
- Azure DevOps (Visual Studio Team Services) (versión preliminar)
- Azure Portal (versión preliminar)
- Cuadro
- Concur
- CornerStone on Demand
- DocuSign
- Dropbox
- Dynamics 365 CRM (versión preliminar)
- Egnyte
- Exchange Online (versión preliminar)
- G Suite
- Github
- HighQ
- JIRA/Confluence
- OneDrive para la Empresa (versión preliminar)
- Aprendizaje de LinkedIn
- Power BI (versión preliminar)
- Salesforce
- ServiceNow
- SharePoint Online (versión preliminar)
- Slack
- Tableau
- Microsoft Teams (versión preliminar)
- Workday
- Workiva
- Workplace de Facebook
- Yammer (versión preliminar)




Continuamente se inscriben más aplicaciones al control de sesiones. Si le interesa una aplicación específica que no se menciona aquí, [envíenos los detalles sobre la aplicación](mailto:casfeedback@microsoft.com). No olvide enviar el caso de uso que le interesa para que podamos incorporarlo.



>[!div class="step-by-step"]
[SIGUIENTE: Implementación del control de aplicaciones de acceso condicional »](proxy-deployment-aad.md)


## <a name="next-steps"></a>Pasos siguientes
[Implementar el control de la aplicación de acceso condicional para aplicaciones de Azure AD](proxy-deployment-aad.md)   

[Los clientes Premier también pueden crear una solicitud de soporte técnico directamente en el portal Premier.](https://premier.microsoft.com/)  
  


