---
title: Trabajo con el proxy de Cloud App Security | Microsoft Docs
description: "En este tema se proporciona información sobre el funcionamiento del proxy de Cloud App Security."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 8/9/2017
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: 28317b70-1851-4610-b1d6-863bc5994bb6
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: d4b01d92f705566bac36d764a7aede0eaa8defcc
ms.sourcegitcommit: 4cf65f627f2d370ee4a4decae1acbb9658874056
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/13/2017
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

## <a name="access-control"></a>Control de acceso
El control de acceso le ofrece la capacidad de supervisar, auditar y bloquear el acceso (en función de la aplicación, el dispositivo, el usuario y la ubicación). De esta forma, puede controlar, en tiempo real, el acceso a las aplicaciones en la nube.

El control de acceso le permite crear directivas eficaces, por ejemplo:
 - bloquear el acceso a todas las aplicaciones en la nube desde dispositivos no administrados
 - bloquear el acceso a aplicaciones en la nube específicas a usuarios específicos
 - supervisar el acceso a aplicaciones en la nube específicas desde ubicaciones específicas
 - limitar el acceso a aplicaciones en la nube a grupos de usuarios y ubicaciones específicos

Para usar el control de acceso en Cloud App Security, haga algunos cambios en la configuración del proveedor de identidades existente para implementar el proxy y establezca una directiva para controlar las aplicaciones en la nube. 

> [!NOTE]
> -  No es necesario cambiar las directivas existentes del proveedor de identidades.

### <a name="how-access-control-works"></a>Funcionamiento del control de acceso

Como parte de la implementación del proxy, modificará la configuración de la aplicación y del proveedor de identidades para redirigir las solicitudes de inicio de sesión al proxy. 

Después de esto, todos los eventos de inicio de sesión se enrutan a través del proxy y este puede decidir si se permite, se deniega o se supervisa el acceso a la aplicación.

### <a name="supported-apps-and-identity-providers"></a>Proveedores de identidades y aplicaciones compatibles

El control de acceso admite cualquier aplicación y cualquier proveedor de identidades que sea compatible con los protocolos SAML o WS-Federation. El equipo de Cloud App Security ha probado los proveedores de identidades y las aplicaciones líderes con las funcionalidades de control de acceso. Aun así, ya que hay muchos proveedores de identidades y aplicaciones en la nube, se recomienda probar el proceso de inicio de sesión único con el proveedor de identidades y la aplicación en un espacio aislado o en un entorno de prueba antes de implementarlo en un entorno de producción.

## <a name="session-control"></a>Control de sesión

El control de sesión ofrece una capa adicional de control al proporcionar información de todas las actividades en cada sesión de usuario. El control de sesión permite supervisar detalladamente en el ámbito de la sesión, lo que le proporciona una visibilidad pormenorizada de las aplicaciones en la nube similar a la de los proxy en línea para aplicaciones locales. En lugar de permitir y bloquear el acceso por completo, con el control de sesión puede limitar actividades de sesión específicas. 

Por ejemplo, puede decidir que desde dispositivos no administrados, o en sesiones que provienen de ubicaciones específicas, quiere permitir que el usuario acceda a la aplicación, pero también limitar la descarga de archivos confidenciales. 

### <a name="how-session-control-works"></a>Funcionamiento del control de sesión

El control de sesión del proxy se basa en el control de acceso. Después de controlar el acceso a una aplicación, puede establecer directivas de sesión que redirigirán las sesiones de usuario al control de sesión del proxy. Desde ese momento, las solicitudes y respuestas del usuario pasan por el proxy en lugar de ir directamente a la aplicación.

Para mantener al usuario dentro de la sesión, el proxy reemplaza todas las direcciones URL pertinentes, los scripts de Java y las cookies dentro de la aplicación en páginas duplicadas en el proxy. Por ejemplo, si la aplicación devuelve una página con vínculos que finalizan en *myapp.com*, el proxy las reemplaza por páginas que finalizan de manera similar a *myapp.com.cas.ms*.

Una vez que se dirige una sesión a través del proxy, este puede inspeccionar el tráfico, mostrar los eventos que identifica en el portal de Cloud App Proxy y aplicar directivas sobre la sesión.

## <a name="device-identification"></a>Identificación de dispositivos

Cloud App Security le permite identificar y crear directivas de proxy basadas en la posición del dispositivo. Para identificar si un dispositivo está administrado o no, Cloud App Security usa:
 - Dispositivos compatibles con Intune* 
 - Dispositivos unidos a un dominio de Azure AD* 
 - Implementación de certificados de cliente (para todas las aplicaciones)

* Solo está disponible para aplicaciones de Azure AD, donde el acceso condicional está disponible

## <a name="architecture"></a>Arquitectura

La integración con capacidades de proxy es sencilla con Azure Active Directory. También puede usar dispositivos unidos a un dominio de Azure AD y compatibles con Intune para facilitar la identificación del dispositivo al crear la directiva. 

Para establecer otros proveedores de identidades y aplicaciones para que funcionen con el proxy, ambos deben estar configurados para redirigir las solicitudes de inicio de sesión al proxy.

Además, con el fin de identificar los dispositivos administrados, el proxy puede solicitar certificados de cliente a los dispositivos administrados. Una vez que el proxy recibe un certificado de cliente, el dispositivo se considera como administrado y entran en vigor las directivas sobre los dispositivos administrados y no administrados.

Para obtener más información sobre el proceso de implementación, consulte [Implementación del proxy](proxy-deployment.md).

![Arquitectura del proxy de Cloud App Security](./media/proxy-architecture.png)

## <a name="user-login-flow"></a>Flujo de inicio de sesión de usuario

1. El usuario envía una solicitud al proveedor de identidades y proporciona las credenciales.
2.  Si se permite el acceso, el proveedor de identidades redirige al usuario al proxy de Cloud App Security.
3.  Si el usuario tiene instalado un certificado de cliente y hay una directiva pertinente que comprueba los dispositivos administrados o no administrados, se le pedirá al usuario que proporcione certificados de cliente. En cualquier caso, se evalúa una directiva de acceso.
4.   En este punto hay tres opciones posibles:
    -   El usuario está autorizado a acceder a la aplicación
    -   El usuario está bloqueado y no puede acceder a la aplicación
    -   El usuario está autorizado a acceder a la aplicación, pero en modo supervisado
        -   En este caso, se vuelve a redirigir al usuario al proxy de Cloud App Security, que supervisa toda la sesión entre el usuario y la aplicación. Durante la supervisión, el proxy evalúa las directivas de sesión y puede realizar acciones de bloqueo según corresponda.

>[!NOTE]
> En el diagrama anterior, se muestra un *inicio de sesión iniciado por el proveedor de identidades*. Si el usuario inicia la aplicación, un *inicio de sesión iniciado por el proveedor de servicios*, se le dirige al proxy de Cloud App Security y, luego, al proveedor de identidades, antes de completar el flujo de *inicio de sesión iniciado por el proveedor de identidades*.

## <a name="managed-devices-flow"></a>Flujo de dispositivos administrados

Para identificar los dispositivos no administrados por Azure AD, el proxy usa el mecanismo de los certificados de cliente. El mecanismo funciona de la siguiente manera:

1. Si el usuario tiene instalado un certificado de cliente en su dispositivo y hay una directiva pertinente que comprueba los dispositivos administrados o no administrados.
   -   Cuando el usuario llega a la página del proxy durante la fase de inicio de sesión, el proxy solicita un certificado de cliente al dispositivo del usuario.

   -   El dispositivo del usuario debe proporcionar el certificado de cliente y, si el usuario lo aprueba, el certificado de cliente se envía al proxy.

   -   Luego el proxy autentica el certificado de cliente en el certificado raíz que proporciona el administrador.

   -   Si el certificado de cliente que proporciona el dispositivo se autentica correctamente con el certificado raíz, el dispositivo se considera como administrado.

-   Si no se completa alguna de las fases anteriores, el dispositivo se considera como no administrado.



## <a name="see-also"></a>Consulte también  
[Implementación del proxy](proxy-deployment.md)   
[Para obtener soporte técnico, visite la página de soporte técnico asistido de Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Los clientes Premier también pueden elegir Cloud App Security directamente desde el Portal Premier.](https://premier.microsoft.com/)  
  