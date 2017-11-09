---
title: Proteger con el proxy de Microsoft Cloud App Security | Microsoft Docs
description: "En este tema encontrará información sobre el funcionamiento del proxy de Cloud App Security."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 10/31/2017
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: 35a43120-bf67-4cf9-9b48-ebe157dbbd18
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 764428c87317d5b4ab706b5a9d4b3c83147628b3
ms.sourcegitcommit: 3bc510959e66a29d474cbef412deac0daefa8a24
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="protect-apps-with-microsoft-cloud-app-security-proxy"></a>Proteger aplicaciones con el proxy de Microsoft Cloud App Security

> [!NOTE]
> La implantación de la característica de proxy de Microsoft Cloud App Security ha comenzado.

En el ámbito laboral actual, a menudo no basta con saber lo que ocurre en el entorno de nube después de los hechos, sino que también se requiere tener la posibilidad de detener brechas y fugas en tiempo real antes de que los empleados pongan en riesgo su organización y los datos, ya sea de manera intencional como por accidente. Es importante permitir que los usuarios de la organización tengan a su disposición la mayoría de los servicios y las herramientas en aplicaciones de nube, y lleven al trabajo sus propios dispositivos. Al mismo tiempo, se necesitan herramientas que permitan proteger la organización de fugas o robos de datos en tiempo real. Junto con Azure Active Directory, el proxy de Cloud App Security proporciona estas funcionalidades en una experiencia integrada y holística.

## <a name="how-it-works"></a>Cómo funciona

El proxy de Cloud App Security se integra con el acceso condicional de Azure AD. El acceso condicional de Azure AD permite exigir el uso de controles de acceso en las aplicaciones de la organización según determinadas condiciones. Las condiciones definen *quién* (por ejemplo, un usuario o un grupo de usuarios), *qué* (qué aplicaciones en la nube) y *dónde* (qué ubicaciones y redes) se aplica una directiva de acceso condicional. Tras establecer las condiciones, puede enrutar a los usuarios al proxy de Cloud App Security, donde se aplica el control de la sesión.

Cuando un usuario se enruta al proxy de Cloud App Security, sus sesiones de aplicación se pueden supervisar y controlar en tiempo real según las directivas de sesión definidas. Las directivas de sesión se usan en el portal de Cloud App Security para perfeccionar los filtros de la sesión y establecer las medidas que hay que tomar con respecto a un usuario. Con las directivas de sesión, puede:

-   **Bloquear descargas**: puede bloquear la descarga de documentos confidenciales. Por ejemplo, en los dispositivos no administrados.

-   **Proteger las descargas**: en lugar de bloquear la descarga de documentos confidenciales, puede requerir que los documentos se protejan con cifrado. Esto garantiza que el documento está protegido y el acceso de usuario debe autenticarse si se descargan datos en un dispositivo que no es de confianza. 

-   **Restringir las sesiones de usuario desde redes no corporativas**: los usuarios que tienen acceso a una aplicación protegida desde una ubicación que no forma parte de la red corporativa tienen un acceso restringido y la descarga de material confidencial está bloqueado o protegido.

-   **Supervisar las sesiones de usuario con un nivel de confianza bajo**: los usuarios que entrañen riesgo se supervisan cuando inician sesión en aplicaciones e, igualmente, sus acciones se registran en la sesión. Puede investigar y analizar el comportamiento de los usuarios para entender dónde (y en qué condiciones) se deben aplicar directivas de sesión en el futuro. 

### <a name="how-session-control-works"></a>Funcionamiento del control de sesión

El control de sesión del proxy se basa en el acceso condicional. Después de controlar el acceso a una aplicación, puede redirigir las sesiones de usuario al control de sesión del proxy, en lugar de directamente a la aplicación. A partir de ese momento, las solicitudes y respuestas del usuario pasarán por el proxy en lugar de ir directamente a la aplicación.

Para mantener al usuario dentro de la sesión, el proxy reemplaza todas las direcciones URL, scripts de Java y cookies pertinentes de la sesión de aplicación por direcciones URL del proxy. Por ejemplo, si la aplicación devuelve una página con vínculos cuyos dominios terminan en myapp.com, el proxy reemplazará esos vínculos por dominios que terminan en algo parecido a myapp.com.us.cas.ms. 

Este método no requiere que se instale nada en el dispositivo, lo cual es ideal para supervisar sesiones desde dispositivos no administrados. 

Después de que una sesión pase por el proxy, este puede realizar lo siguiente:
1. Inspeccionar el tráfico en busca de actividades de usuario
3. Mostrar las actividades detectadas en el portal de proxy de Cloud App
2. Guardar los registros de tráfico y analizarlos
3. Permitir que el administrador exporte los registros de tráfico
4. Exigir la aplicación de directivas en la sesión

## <a name="managed-device-identification"></a>Identificación de dispositivos administrados

El proxy permite crear directivas que tienen en cuenta si un dispositivo está administrado o no. Para saber si un dispositivo está administrado o no, el proxy consulta lo siguiente:

-   Dispositivos compatibles 
-   Dispositivos unidos a dominio 
-   Implementación de certificados de cliente
 
 
### <a name="compliant-and-domain-joined-devices"></a>Dispositivos compatibles y unidos a dominio
El acceso condicional de Azure AD permite pasar información sobre los dispositivos compatibles y unidos a un dominio directamente al proxy de Cloud App Security. Desde allí, se puede desarrollar una directiva de sesión que use el estado del dispositivo como filtro.
Para más información, vea [Introducción a la administración de dispositivos en Azure Active Directory](https://docs.microsoft.com/azure/active-directory/device-management-introduction). 

### <a name="client-certificate-authenticated-devices"></a>Dispositivos autenticados con certificado de cliente

El mecanismo de identificación de dispositivos de proxy puede solicitar la autenticación de los dispositivos que usan certificados de cliente. Esto permite aprovechar los certificados de cliente existentes ya implementados en la organización o implantar nuevos certificados de cliente en los dispositivos administrados y, después, usar la existencia de tales certificados para definir directivas de acceso y de sesión. Para más información sobre cómo implementar certificados de cliente, vea [Implementar el proxy para aplicaciones de Azure AD](proxy-deployment-aad.md).
 
## <a name="supported-apps-and-clients"></a>Aplicaciones y clientes compatibles

Actualmente, el proxy admite aplicaciones configuradas con un inicio de sesión único en SAML en Azure AD. De igual modo, el control de sesión no está automáticamente disponible para todas las aplicaciones. El equipo de Cloud App Security ha comprobado muchas aplicaciones populares con control de sesión. Otras aplicaciones pueden requerir un proceso de incorporación, que se realizará junto con el cliente.
En cuanto a los clientes, el control de sesión está disponible para cualquier explorador en las principales plataformas, pero no se admiten aplicaciones de escritorio ni móviles. 

> [!NOTE]
> Las aplicaciones de Office 365 no están configuradas con SAML, por lo que no son compatibles actualmente.

## <a name="see-also"></a>Consulte también  
[Implementar el proxy de Cloud App Security](proxy-deployment-aad.md)   
[Para obtener soporte técnico, visite la página de soporte técnico asistido de Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Los clientes Premier también pueden elegir Cloud App Security directamente desde el Portal Premier.](https://premier.microsoft.com/)  
  


