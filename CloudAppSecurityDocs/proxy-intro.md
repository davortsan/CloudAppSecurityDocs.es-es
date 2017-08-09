---
title: Trabajo con el proxy de Cloud App Security | Microsoft Docs
description: "En este tema se proporciona información sobre el funcionamiento del proxy de Cloud App Security."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 7/31/2017
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: 28317b70-1851-4610-b1d6-863bc5994bb6
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 82e1ee0b5161dce88db815dc8eea06340bdbc532
ms.sourcegitcommit: f9851779aa15b11f559e56ac818f1333f027c000
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/07/2017
---
# <a name="working-with-the-cloud-app-security-proxy"></a>Trabajo con el proxy de Cloud App Security

En el ámbito laboral actual, a menudo no basta con saber lo que ocurre en el entorno de nube después de los hechos, sino que también se requiere tener la posibilidad de detener brechas y fugas en tiempo real antes de que los empleados pongan en riesgo su organización y los datos, ya sea de manera intencional como por accidente. Debe ser capaz de permitir que los usuarios de la organización tengan a su disposición la mayoría de los servicios y las herramientas en aplicaciones de nube, y lleven al trabajo sus propios dispositivos. Al mismo tiempo, necesita herramientas que le permitan proteger la organización de fugas de datos, ataques de ransomware y el robo masivo de datos. 

## <a name="introducing-the-cloud-app-security-proxy"></a>Introducción al proxy de Cloud App Security
El proxy de Cloud App Security ofrece las herramientas necesarias para supervisar en tiempo real y controlar el acceso del entorno de nube, al igual que las actividades que se realizan en él.
Con el proxy de Cloud App Security puede proteger a su organización:
- Bloquee las descargas antes de que se realicen para evitar las fugas de datos
- Minimice su exposición a ransomware mediante la administración y el bloqueo del acceso a su red desde dispositivos no administrados que probablemente no estén protegidos con contraseña ni tengan instalado ningún software antivirus
- Establezca reglas que obliguen a proteger cifrados los datos almacenados y descargados de la nube
- Obtenga visibilidad de los puntos de conexión no protegidos para que pueda supervisar lo que se hace en los dispositivos no administrados
- Controle el acceso desde direcciones IP de riesgo y proveedores de identidades heredados

Para habilitar estas funcionalidades únicas, use los dos niveles de control que proporciona el proxy: control de acceso y control de sesión. Ambos tipos de control aprovechan la información del usuario, la información de la ubicación y la información del dispositivo (que se usan para identificar cuáles son los dispositivos administrados y cuáles los no administrados) para tomar decisiones relacionadas con las directivas en cada aplicación.

### <a name="access-control"></a>Control de acceso
<more information about what is access control including examples> El control de acceso del proxy le permite crear directivas de acceso eficaces para las aplicaciones de nube y ofrece las funcionalidades siguientes:

Para usar el control de acceso en Cloud App Security, haga algunos cambios en la configuración del proveedor de identidades para implementar el proxy y establezca una directiva para controlar las aplicaciones de nube. 

> [!NOTE]
> -  No es necesario cambiar las directivas existentes del proveedor de identidades.

#### <a name="supported-apps-and-identity-providers"></a>Proveedores de identidades y aplicaciones compatibles

El control de acceso del proxy está diseñado para admitir cualquier aplicación y cualquier proveedor de identidades que sea compatible con los protocolos SAML o WS-Federation. El equipo de Cloud App Security prueba los proveedores de identidades y las aplicaciones líderes con las funcionalidades de control de acceso. Sin embargo, como existen muchos proveedores de identidades y muchas aplicaciones de nube, no se prueban todas las combinaciones de proveedores de identidades y aplicaciones. Se recomienda probar el proceso de inicio de sesión único con el proveedor de identidades y una aplicación en un espacio aislado o en un entorno de prueba antes de implementarlo en un entorno de producción.

### <a name="session-control"></a>Control de sesión

El control de sesión es un nivel de control adicional que brinda el proxy. Permite un control en tiempo real más pormenorizado de las aplicaciones de nube. En lugar de establecer una directiva global que permita o bloquee el acceso a cierta aplicación, ahora puede obtener acceso y, cuando supervise cada sesión de usuario en la aplicación, limitar el acceso de distintas formas. Por ejemplo, puede decidir que desde ciertos dispositivos, o en sesiones que provienen de ubicaciones específicas, desea permitir que el usuario acceda a la aplicación, pero también limitar la descarga de archivos confidenciales.

#### <a name="supported-apps-and-flows"></a>Aplicaciones y flujos compatibles

Actualmente, el control de sesión permite bloquear la descarga de archivos y la exportación de los informes en Salesforce.com. Puede crear directivas basadas en usuario, ubicación y dispositivo, además de basadas en el contenido que desea descargar.

Además, esta versión admite sesiones limitadas para usuarios que inician sesión desde exploradores. Por ejemplo, si desea limitar el acceso a sesiones desde aplicaciones nativas, deberá definir una directiva de acceso para bloquear dicho acceso cuando el filtro **Etiqueta de agente de usuario** sea equivalente a **Cliente nativo**.

Salesforce se prueba en todos los flujos normales. Sin embargo, como Salesforce tiene varias aplicaciones de terceros, es posible que algunas de estas no se hayan probado y puede que no funcionen con el control de sesión y también podrían hacer que algunas páginas no funcionen. Para comprobar que efectivamente se trata de un problema de una aplicación de terceros, quite todas las aplicaciones de este tipo y pruebe la aplicación con el control de sesión. Si todo funciona bien, agregue una a una las aplicaciones de terceros hasta que encuentre cuál es la que genera el problema. 

## <a name="device-management"></a>Administración de dispositivos

Cloud App Security le permite identificar y crear directivas de proxy basadas en la posición del dispositivo. Con el fin de identificar si un dispositivo es administrado o no, Cloud App Security usa el mecanismo de certificados de cliente, en el cual los certificados de clientes se implementan en los dispositivos administrados de la organización. Una vez que los usuarios inician sesión en una aplicación, se les pedirá proporcionar el certificado de cliente instalado en su dispositivo. Si se proporciona un certificado de cliente, Cloud App Security reconoce el dispositivo como administrado. 
> [!NOTE]
>  El usuario podría elegir declinar el envío de los certificados de cliente y, en este caso, el dispositivo se considerará como no administrado.
<¿Entonces cómo podemos saber si un dispositivos está administrado o no? ¿Qué pasa con eso?>

### <a name="supported-browsers-and-native-apps"></a>Aplicaciones nativas y exploradores compatibles

El proxy de Cloud App Security le permite... según los certificados de cliente...

Los certificados de cliente son un mecanismo conocido que los desarrolladores de exploradores y aplicaciones nativas pueden decidir si implementan o no. Es compatible con la mayoría de los exploradores en la mayoría de las plataformas, pero en las aplicaciones nativas el asunto es más complicado.

La compatibilidad con certificados de cliente en las aplicaciones nativas, que incluyen tanto aplicaciones móviles como de escritorio, podría variar según la plataforma e, incluso, según el estado del dispositivo. Por ejemplo, en Salesforce1, la aplicación móvil de Salesforce, los certificados de cliente solo funcionan si hay una MDM implementada en el dispositivo y Salesforce1 está configurada para enviar certificados de cliente.

Los certificados de cliente se probaron correctamente en Internet Explorer, Edge, Chrome, Safari y Firefox en las versiones más recientes de Windows, OSX, Android y iOS (cada una con sus respectivos exploradores).

> [!NOTE]
> En iOS, solo el explorador Safari funciona con los certificados de cliente.

Incluso en casos en los que los exploradores o las aplicaciones nativas admiten los certificados de cliente, es posible que haya casos en que los usuarios tendrán problemas para proporcionar el certificado, por ejemplo, si un usuario alguna vez declina enviar un certificado de cliente, el explorador o la aplicación nativa podría recordar esa opción y no le volverá a pedir un certificado al usuario en cuestión. Para solucionar estos problemas, se recomienda cerrar todas las instancias abiertas del explorador y luego abrir instancias nuevas, o bien eliminar todas las cookies y volver a intentarlo.

Por otro lado, hay algunos exploradores y aplicaciones nativas que admiten la opción de suprimir los mensajes emergentes que solicitan certificados de cliente y, en su lugar, los envían de forma automática.

En general, se recomienda probar las solicitudes de certificados de cliente de parte de los usuarios sin aplicar directivas, pero solo en modo de monitor. Para ello, cree una directiva de **solo registro** para identificar los dispositivos administrados.

## <a name="architecture"></a>Arquitectura

El proxy se integra con el proveedor de identidades y también con la aplicación, y ambos deben estar configurados para redirigir las solicitudes de inicio de sesión al proxy.

Además, con el fin de identificar los dispositivos administrados, el proxy puede solicitar certificados de cliente a los dispositivos administrados. Una vez que el proxy recibe un certificado de cliente, el dispositivo se considera como administrado y entran en vigor las directivas sobre los dispositivos administrados y no administrados.

Para más información sobre el proceso de implementación, consulte la sección Implementación.

![Arquitectura del proxy de Cloud App Security](./media/proxy-architecture.png)

## <a name="user-login-flow"></a>Flujo de inicio de sesión de usuario

En el diagrama anterior se describe un inicio de sesión que comienza en el proveedor de identidades, también conocido como *inicio de sesión iniciado por el proveedor de identidades*. Si el usuario comienza en la aplicación, lo que se conoce como *inicio de sesión*, se le dirige al proxy de Cloud App Security, el que luego la dirige al proveedor de identidades. El resto del proceso de inicio de sesión es similar al flujo de *inicio de sesión iniciado por el proveedor de identidades*.

Este es el flujo de *inicio de sesión iniciado por el proveedor de identidades*:
-   El usuario envía una solicitud al proveedor de identidades y proporciona las credenciales

-   Si se permite el acceso, el proveedor de identidades redirige al usuario al proxy de Cloud App Security

-   Si el usuario tiene instalado un certificado de cliente y hay una directiva pertinente que comprueba los dispositivos administrados o no administrados, se le pedirá al usuario que proporcione certificados de cliente. En cualquier caso, se evalúa una directiva de acceso

-   En este punto hay tres opciones posibles:

    -   El usuario está autorizado a acceder a la aplicación

    -   El usuario está bloqueado y no puede acceder a la aplicación

    -   El usuario está autorizado a acceder a la aplicación, pero en modo supervisado

        -   En este caso, se vuelve a redirigir al usuario al proxy de Cloud App Security, el que supervisa toda la sesión entre el usuario y la aplicación

        -   Durante la supervisión, el proxy evalúa las directivas de sesión y puede realizar acciones de bloqueo según corresponda

## <a name="how-access-control-works"></a>Funcionamiento del control de acceso

Como parte de la implementación del proxy, necesita cambiar las configuraciones en el identificador de identidades y en la aplicación que desea controlar. Esto incluye cambios de dirección URL para que tanto el proveedor de identidades como la aplicación redirijan las solicitudes de inicio de sesión al proxy. Además, también se cambia el lugar de los certificados si es necesario.

Una vez completados estos pasos, todos los eventos de inicio de sesión pasan por el proxy y este puede decidir si tienen permitido acceder a la aplicación, si se les niega el acceso o si pueden acceder en modo supervisado. Tenga en cuenta que en esta fase el proxy puede solicitar certificados de cliente al dispositivo y usar el estado del dispositivo para tomar decisiones relativas a las directivas.

## <a name="how-session-control-works"></a>Funcionamiento del control de sesión

El control de sesión del proxy se basa en el control de acceso. Una vez que controla el acceso a una aplicación, puede decidir, en función de las directivas de acceso, supervisar la sesión si redirige sus sesiones al control de sesión del proxy. Desde ese momento, las solicitudes y respuestas del usuario pasan por el proxy en lugar de ir directamente a la aplicación.

Para mantener al usuario dentro de la sesión, el proxy reemplaza todas las direcciones URL pertinentes, los scripts de Java y las cookies dentro de la aplicación en páginas duplicadas en el proxy. Por ejemplo, si la aplicación devuelve una página con vínculos que finalizan en *myapp.com*, el proxy las reemplaza por páginas que finalizan de manera similar a *myapp.com.cas.ms*.

Una vez que se dirige una sesión a través del proxy, este puede inspeccionar el tráfico, mostrar los eventos que identifica en el portal de Cloud App Proxy y aplicar directivas sobre la sesión.

## <a name="how-identifying-managed-devices-works"></a>Funcionamiento de la identificación de dispositivos administrados

Para identificar los dispositivos administrados, el proxy usa el mecanismo de los certificados de cliente. El mecanismo funciona de la siguiente manera:

-   Si el usuario tiene instalado un certificado de cliente en su dispositivo y hay una directiva pertinente que comprueba los dispositivos administrados o no administrados.

    -   Cuando el usuario llega a la página del proxy durante la fase de inicio de sesión, el proxy solicita un certificado de cliente al dispositivo del usuario.

    -   El dispositivo del usuario debe proporcionar el certificado de cliente y, si el usuario lo aprueba, el certificado de cliente se envía al proxy.

    -   Luego el proxy autentica el certificado de cliente en el certificado raíz que proporciona el administrador.

    -   Si el certificado de cliente que proporciona el dispositivo se autentica correctamente con el certificado raíz, el dispositivo se considera como administrado.

-   Si no se completa alguna de las fases anteriores, el dispositivo se considera como no administrado.



## <a name="see-also"></a>Consulte también  
[Implementación del proxy](proxy-deployment.md)   
[Para obtener soporte técnico, visite la página de soporte técnico asistido de Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Los clientes Premier también pueden elegir Cloud App Security directamente desde el Portal Premier.](https://premier.microsoft.com/)  
  