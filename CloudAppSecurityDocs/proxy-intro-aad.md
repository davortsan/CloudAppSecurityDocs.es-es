---
title: Proteger con el control de aplicaciones de acceso condicional de Microsoft Cloud App Security | Microsoft Docs
description: En este tema encontrará información sobre el funcionamiento del proxy inverso de control de aplicaciones de acceso condicional de Cloud App Security.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 4/25/2018
ms.topic: article
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 35a43120-bf67-4cf9-9b48-ebe157dbbd18
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: ebc88634d6a4b83effe598c45f8da62338cebf53
ms.sourcegitcommit: c5dbeb75e409518feaa26200e9a02c59accc8dcc
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/30/2018
---
*Se aplica a: Microsoft Cloud App Security*


# <a name="protect-apps-with-microsoft-cloud-app-security-conditional-access-app-control"></a>Proteger aplicaciones con el control de aplicaciones de acceso condicional de Microsoft Cloud App Security

> [!NOTE]
> Se trata de una característica en vista previa.


En el ámbito laboral actual, a menudo no basta con saber lo que ocurre en el entorno de nube después de los hechos, sino que también se requiere tener la posibilidad de detener brechas y fugas en tiempo real antes de que los empleados pongan en riesgo su organización y los datos, ya sea de manera intencional como por accidente. Es importante permitir que los usuarios de la organización tengan a su disposición la mayoría de los servicios y las herramientas en aplicaciones de nube, y lleven al trabajo sus propios dispositivos. Al mismo tiempo, se necesitan herramientas que permitan proteger la organización de fugas o robos de datos en tiempo real. Junto con Azure Active Directory, Microsoft Cloud App Security proporciona estas funcionalidades en una experiencia integrada y holística con el control de aplicaciones de acceso condicional.

## <a name="how-it-works"></a>Cómo funciona

El control de aplicaciones de acceso condicional usa una arquitectura de proxy inverso y se integra de forma única con el acceso condicional de Azure AD. El acceso condicional de Azure AD permite exigir el uso de controles de acceso en las aplicaciones de la organización según determinadas condiciones. Las condiciones definen *quién* (por ejemplo, un usuario o un grupo de usuarios), *qué* (qué aplicaciones en la nube) y *dónde* (qué ubicaciones y redes) se aplica una directiva de acceso condicional. Tras establecer las condiciones, puede enrutar los usuarios a Microsoft Cloud App Security, donde podrá proteger los datos con el control de aplicaciones de acceso condicional, aplicando para ello controles de sesión y acceso.

Gracias al control de aplicaciones de acceso condicional, las sesiones y el acceso a la aplicación de los usuarios se pueden supervisar y controlar en tiempo real según las directivas de sesión y acceso definidas. Las directivas de sesión y acceso se usan en el portal de Cloud App Security para perfeccionar los filtros y establecer las medidas que hay que tomar con respecto a un usuario. Con las directivas de acceso y sesión, puede:

-   **Bloquear descargas**: puede bloquear la descarga de documentos confidenciales. Por ejemplo, en los dispositivos no administrados.

-   **Proteger las descargas**: en lugar de bloquear la descarga de documentos confidenciales, puede requerir que los documentos se protejan con cifrado. Esto garantiza que el documento está protegido y el acceso de usuario debe autenticarse si se descargan datos en un dispositivo que no es de confianza. 

-   **Restringir las sesiones de usuario desde redes no corporativas**: los usuarios que tienen acceso a una aplicación protegida desde una ubicación que no forma parte de la red corporativa tienen un acceso restringido y la descarga de material confidencial está bloqueado o protegido.

-   **Supervisar las sesiones de usuario con un nivel de confianza bajo**: los usuarios que entrañen riesgo se supervisan cuando inician sesión en aplicaciones e, igualmente, sus acciones se registran en la sesión. Puede investigar y analizar el comportamiento de los usuarios para entender dónde (y en qué condiciones) se deben aplicar directivas de sesión en el futuro. 

- **Bloquear el acceso**: puede bloquear por completo el acceso a aplicaciones específicas a usuarios de dispositivos no administrados o de redes no corporativas.


### <a name="how-session-control-works"></a>Funcionamiento del control de sesión

Al crear una directiva de sesión con control de aplicaciones de acceso condicional, podrá controlar las sesiones de usuario redirigiendo al usuario en cuestión a través de un proxy inverso, en lugar de directamente a la aplicación. A partir de ese momento, las solicitudes y respuestas del usuario pasarán por Microsoft Cloud App Security en lugar de ir directamente a la aplicación.

Para mantener al usuario dentro de la sesión, todas las direcciones URL, scripts de Java y cookies pertinentes de la sesión de aplicación se reemplazan por direcciones URL de Microsoft Cloud App Security. Por ejemplo, si la aplicación devuelve una página con vínculos cuyos dominios terminan en myapp.com, el vínculo se reemplazará por dominios que acaben en algo parecido a myapp.com.us.cas.ms. 

Este método no requiere que se instale nada en el dispositivo, lo cual es ideal para supervisar sesiones desde dispositivos no administrados. 

Después de que una sesión se dirija a través de Microsoft Cloud App Security, se pueden realizar las siguientes acciones:
1. Inspeccionar el tráfico en busca de actividades de usuario
2. Mostrar las actividades detectadas en el registro de actividades de Microsoft Cloud App Security
3. Guardar los registros de tráfico y analizarlos
4. Permitir que el administrador exporte los registros de tráfico
5. Exigir la aplicación de directivas en la sesión

## <a name="managed-device-identification"></a>Identificación de dispositivos administrados

El control de aplicaciones de acceso condicional permite crear directivas que tienen en cuenta si un dispositivo está administrado o no. Para saber si un dispositivo está administrado o no, esta característica consulta lo siguiente:

-   Dispositivos compatibles 
-   Dispositivos unidos a dominio 
-   Implementación de certificados de cliente
 
 
### <a name="compliant-and-domain-joined-devices"></a>Dispositivos compatibles y unidos a dominio
El acceso condicional de Azure AD permite pasar información sobre los dispositivos compatibles y unidos a un dominio directamente a Microsoft Cloud App Security. Desde allí, se puede desarrollar una directiva de sesión o acceso que use el estado del dispositivo como filtro.
Para más información, vea [Introducción a la administración de dispositivos en Azure Active Directory](https://docs.microsoft.com/azure/active-directory/device-management-introduction). 

### <a name="client-certificate-authenticated-devices"></a>Dispositivos autenticados con certificado de cliente

El mecanismo de identificación de dispositivos puede solicitar la autenticación de los dispositivos que usan certificados de cliente. Esto permite aprovechar los certificados de cliente existentes ya implementados en la organización o implantar nuevos certificados de cliente en los dispositivos administrados y, después, usar la existencia de tales certificados para definir directivas de acceso y de sesión. Para más información sobre cómo implementar certificados de cliente, vea [Implementar el control de la aplicación de acceso condicional para aplicaciones de Azure AD](proxy-deployment-aad.md).
 
## <a name="supported-apps-and-clients"></a>Aplicaciones y clientes compatibles

Actualmente, el control de aplicaciones de acceso condicional admite aplicaciones configuradas con un inicio de sesión único en SAML en Azure AD. 

> [!NOTE]
> - El control de aplicaciones de acceso condicional también admite aplicaciones que están configuradas con proveedores de identidades que no sean Azure AD en Private Preview. Para obtener más información sobre Private Preview, envíe un correo electrónico a mcaspreview@microsoft.com.
> - Las aplicaciones de Office 365 no están configuradas con SAML, por lo que no son compatibles actualmente.

El control de sesiones está disponible para todos los exploradores de cualquier plataforma principal. En estos momentos no se admiten aplicaciones móviles ni de escritorio. Gracias a la integración nativa, Azure AD admite cualquier aplicación configurada con el inicio de sesión único de SAML, incluidas las siguientes, que son las más populares:

-   Salesforce

-   Cuadro

-   G Suite

-   Workday

-   Slack

-   Workplace de Facebook

-   ServiceNow

-   JIRA/Confluence

-   AWS

-   Workiva

-   CornerStone on Demand

-   DocuSign

-   HighQ 

Continuamente se inscriben más aplicaciones al control de sesiones. Si está interesado en alguna aplicación específica que no figure aquí, [envíenos los detalles](mailto:casfeedback@microsoft.com) y el caso de uso que le interese, y la inscribiremos.




## <a name="see-also"></a>Consulte también  
[Implementar el control de la aplicación de acceso condicional para aplicaciones de Azure AD](proxy-deployment-aad.md)   

[Los clientes Premier también pueden elegir Cloud App Security directamente desde el Portal Premier.](https://premier.microsoft.com/)  
  


