---
title: Solución de problemas de controles de sesión y acceso
description: En este artículo se proporcionan a los administradores instrucciones sobre cómo investigar y resolver controles de acceso y de sesión comunes.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 07/15/2020
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.suite: ems
ms.openlocfilehash: f9d29046b0a63b89926d3ba95bab75aba5964cad
ms.sourcegitcommit: 75cdc376a0aea79dc7f339af52a90f0ec6dfc526
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/18/2020
ms.locfileid: "88514361"
---
# <a name="troubleshooting-access-and-session-controls"></a>Solución de problemas de controles de sesión y acceso

En este artículo se proporcionan a los administradores instrucciones sobre cómo investigar y resolver problemas comunes de acceso y control de sesión que experimentan los [administradores](#issues-experienced-by-admins) y [los usuarios finales](#issues-experienced-by-end-users).

Antes de continuar, asegúrese de que el entorno cumple los siguientes requisitos generales mínimos para los controles de acceso y de sesión.

- **Licencias**: Asegúrese de que tiene una [licencia](https://aka.ms/mcaslicensing)válida.
- **Inicio de sesión único (SSO)**: las aplicaciones se deben configurar con una de las soluciones de SSO admitidas.
  - Azure Active Directory (Azure AD) con SAML 2,0 o OpenID Connect 2,0
  - IdP de terceros con SAML 2,0
- **Compatibilidad con exploradores**: los controles de sesión están disponibles para sesiones basadas en explorador en estos exploradores admitidos: Microsoft Edge (latest), Google Chrome (latest), Mozilla Firefox (latest) o Apple Safari (latest)
- **Tiempo de inactividad**: Cloud App Security permite definir el comportamiento predeterminado que se aplicará en caso de que se produzca una interrupción del servicio, como que un componente no funcione correctamente. Puede optar por proteger (bloquear) o omitir (permitir) que los usuarios realicen acciones en contenido potencialmente confidencial cuando no se puedan aplicar los controles de directiva normales. Este comportamiento predeterminado durante el tiempo de inactividad del sistema puede configurarse en el portal de Cloud App Security, como se indica a continuación: **configuración**  >  **control de aplicaciones de acceso condicional**  >  **comportamiento predeterminado**  >  **permitir** o **bloquear** el acceso.

## <a name="issues-experienced-by-admins"></a>Problemas experimentados por los administradores

Esta sección es para los administradores que configuran los controles de acceso y de sesión con Cloud App Security y ayuda a identificar situaciones comunes que pueden surgir en las siguientes áreas:

|Sección|Issues|
|---|---|
|[Las condiciones de la red](#network-conditions)|- [Errores de red al navegar a una página del explorador](#network-errors-when-navigating-to-a-browser-page)<br />- [Inicio de sesión lento](#slow-login)<br />- [Consideraciones adicionales](#network-conditions-additional-considerations)|
|[Identificación del dispositivo](#device-identification)|- [Dispositivos compatibles con Intune o Azure AD híbrido Unidos indefinidos](#misidentified-intune-compliant-or-hybrid-azure-ad-joined-devices)<br />- [Los certificados de cliente no se solicitan cuando se espera](#client-certificates-are-not-prompting-when-expected)<br />- [Los certificados de cliente se solicitan en cada inicio de sesión](#client-certificates-are-prompting-at-every-login)<br />- [Consideraciones adicionales](#device-identification-additional-considerations)|
|[Incorporación de una aplicación](#onboarding-an-app)|- [La aplicación no aparece en la página de **aplicaciones de control de aplicaciones de acceso condicional**](#app-does-not-appear-on-the-conditional-access-app-control-apps-page)<br />- [Estado de la aplicación: continuar con la instalación](#app-status-continue-setup)<br />- [No se pueden configurar controles para aplicaciones nativas](#cannot-configure-controls-for-native-apps)<br />- [Aparece la página **no se reconoce la aplicación**](#something-went-wrong-page-appears)<br />- [Aparece la opción de **control de sesión de solicitud**](#request-session-control-option-appears)<br />- [Consideraciones adicionales](#onboarding-apps-additional-considerations)|
|[Crear directivas de acceso y de sesión](#creating-access-and-session-policies)|- [En las directivas de acceso condicional, no se puede ver la opción **control de aplicaciones de acceso condicional**](#in-conditional-access-policies-you-cannot-see-the-conditional-access-app-control-option)<br />- [Mensaje de error al crear una directiva: no tiene ninguna aplicación implementada con Control de aplicaciones de acceso condicional](#error-message-when-creating-a-policy-you-dont-have-any-apps-deployed-with-conditional-access-app-control)<br />- [No se pueden crear directivas de sesión para una aplicación](#cannot-create-session-policies-for-an-app)<br />- [No se puede elegir el **método de inspección**: servicio de **clasificación de datos**](#cannot-choose-inspection-method-data-classification-service)<br />- [No se puede elegir la **acción**: **proteger**](#cannot-choose-action-protect)<br />- [Consideraciones adicionales](#policies-additional-considerations)|

### <a name="network-conditions"></a>Las condiciones de la red

Entre los problemas de condiciones de red más comunes que puede encontrar se encuentran:

- [Errores de red al navegar a una página del explorador](#network-errors-when-navigating-to-a-browser-page)
- [Inicio de sesión lento](#slow-login)
- [Consideraciones adicionales](#network-conditions-additional-considerations)

#### <a name="network-errors-when-navigating-to-a-browser-page"></a>Errores de red al navegar a una página del explorador

Cuando se configura por primera vez Cloud App Security controles de acceso y de sesión para una aplicación, los errores de red más comunes que pueden surgir son los siguientes: "este sitio no es seguro" y "no hay conexión a Internet". Estos mensajes pueden indicar un error general de configuración de red.

**Pasos recomendados**

1. Configure el firewall para que funcione con Cloud App Security con las direcciones IP de Azure y los nombres DNS pertinentes para su entorno.
    1. Agregue el **Puerto de salida 443** para las siguientes direcciones IP y nombres DNS para el [centro de datos de Cloud App Security](network-requirements.md#access-and-session-controls).
    1. Reinicie el equipo y la sesión del explorador
    1. Comprobar que el inicio de sesión funciona como se esperaba
1. Habilite TLS 1,2 en las opciones de Internet del explorador.

    > [!NOTE]
    >
    > - Cloud App Security aprovecha los protocolos de seguridad de la capa de transporte (TLS) 1.2 + para proporcionar el mejor cifrado de la clase. No se podrá obtener acceso a las aplicaciones y exploradores de cliente nativo que no admitan TLS 1.2 + cuando se configuran con el control de sesión. Sin embargo, las aplicaciones SaaS que usen TLS 1.1 o versiones anteriores aparecerán en el explorador como usuarias de TLS 1.2+ al configurarse con Cloud App Security.
    > - Aunque los controles de sesión se compilan para trabajar con cualquier explorador en cualquier plataforma principal de cualquier sistema operativo, se admite Microsoft Edge (latest), Google Chrome (latest), Mozilla Firefox (latest) o Apple Safari (latest). También se puede bloquear o permitir el acceso a aplicaciones móviles y de escritorio.

    | Browser | Pasos |
    |---|---|
    | Microsoft Internet Explorer | 1. abrir Internet Explorer<br />2. seleccionar **herramientas**  >  **Opciones**  >  **avanzadas** de Internet (pestaña)<br />3. en **seguridad**, seleccione **TLS 1,2**<br />4. Seleccione **aplicar**y, después, haga clic en **Aceptar** .<br />5. Reinicie el explorador y compruebe que puede acceder a la aplicación |
    | Cromo de Microsoft Edge/Edge | 1. Abra la búsqueda desde la barra de tareas y busque "opciones de Internet"<br />2. Seleccione **Opciones de Internet**<br />3. en **seguridad**, seleccione **TLS 1,2**<br />4. Seleccione **aplicar**y, después, haga clic en **Aceptar** .<br />5. Reinicie el explorador y compruebe que puede acceder a la aplicación |
    | Google Chrome | 1. Abra Google Chrome<br />2. en la parte superior derecha, haga clic en **más** (3 puntos verticales) > **configuración** .<br />3. en la parte inferior, haga clic en **Opciones avanzadas** .<br />4. en **sistema**, haga clic en **abrir configuración de proxy** .<br />5. en la pestaña **Opciones avanzadas** , en **seguridad**, seleccione **TLS 1,2**<br />6. Haga clic en **Aceptar** .<br />7. Reinicie el explorador y compruebe que puede acceder a la aplicación |
    | Mozilla Firefox | 1. Abra Mozilla Firefox<br />2. en la barra de direcciones y busque "About: config"<br />3. en el cuadro de búsqueda, busque "TLS"<br />4. Haga doble clic en la entrada de **Security. TLS. version. min**<br />5. establezca el valor entero en 3 para forzar TLS 1,2 como la versión mínima requerida.<br />6. Haga clic en **Guardar** (marca de verificación a la derecha del cuadro valor)<br />7. Reinicie el explorador y compruebe que puede acceder a la aplicación |
    | Safari | Si usa la versión 7 o posterior de Safari, TLS 1,2 se habilita automáticamente. |

#### <a name="slow-login"></a>Inicio de sesión lento

El encadenamiento de proxy y el control de nonce son algunos de los problemas comunes que pueden dar lugar a un rendimiento de inicio de sesión lento.

**Pasos recomendados**

1. Configure el entorno para quitar el firewall y el encadenamiento de proxy de reenvío, conectando dos o más servidores proxy para ir a la página deseada y otros factores externos que pueden provocar lentitud en el proceso de inicio de sesión.
    1. Identificar si el encadenamiento de proxy se está produciendo en el entorno
    1. Quitar servidores proxy de reenvío adicionales siempre que sea posible
1. Desactive el control de nonce para las aplicaciones que no usan nonce.

    > [!NOTE]
    > Algunas aplicaciones usan un hash de nonce durante la autenticación para evitar ataques de reproducción. De forma predeterminada, Cloud App Security supone que una aplicación usa un valor de seguridad (nonce). Si la aplicación con la que está trabajando no usa el nonce, puede deshabilitar el control de nonce para esta aplicación en Cloud App Security.

    1. En Cloud App Security, en la barra de menús, haga clic en el engranaje de configuración y seleccione **control de aplicaciones de acceso condicional**.
    1. En la lista de aplicaciones, en la fila en la que aparece la aplicación que está configurando, elija los tres puntos al final de la fila y, después, elija **Editar** aplicación.
    1. Haga clic en **control de nonce** para expandir la sección y, a continuación, desactive **Habilitar el control de nonce**.
    1. Cierre la sesión de la aplicación y cierre todas las sesiones del explorador.
    1. Reinicie el explorador e inicie sesión en la aplicación y compruebe que el inicio de sesión funciona según lo previsto.

<a name="network-conditions-additional-considerations"></a>

#### <a name="additional-considerations"></a>Consideraciones adicionales

Al solucionar problemas de condiciones de red, hay algunos aspectos adicionales que hay que tener en cuenta sobre el proxy de Cloud App Security.

- **La sesión se enruta a otro centro de datos**

    Cloud App Security aprovecha los centros de datos de Azure de todo el mundo para optimizar el rendimiento a través de la ubicación geográfica. Esto significa que la sesión de un usuario se puede hospedar fuera de una región, en función de los patrones de tráfico y su ubicación. Sin embargo, para proteger su privacidad, no se almacenan datos de la sesión en estos centros de datos.

- **Rendimiento del proxy**

    Derivar una línea base de rendimiento depende de muchos factores fuera del proxy de Cloud App Security, como:

    - Qué otros servidores proxy o puertas de enlace se encuentran en serie con este proxy
    - Desde dónde proviene el usuario
    - Dónde reside el recurso de destino
    - Solicitudes específicas en la página

    En general, cualquier proxy agregará latencia. Las ventajas del proxy de Cloud App Security son:

    - Aprovechamiento de la disponibilidad global de los controladores de dominio de Azure para ubicar a los usuarios en el nodo más cercano y reducir la distancia de ida y vuelta, en una escala que tienen pocos servicios de todo el mundo.
    - El uso de la integración con Azure AD el acceso condicional para enrutar solo las sesiones que desea incluir en el proxy en nuestro servicio, en lugar de todos los usuarios en todas las situaciones.

### <a name="device-identification"></a>Identificación de dispositivos

Cloud App Security proporciona las siguientes opciones para identificar el estado de administración de un dispositivo.

1. Cumplimiento de Microsoft Intune
1. Azure AD híbrido unido al dominio
1. Certificados de cliente

Para obtener más información sobre la identificación de dispositivos, consulte [identificación de dispositivos administrados](proxy-intro-aad.md#managed-device-identification).

Entre los problemas comunes de identificación de dispositivos que puede encontrar se encuentran

- [Dispositivos compatibles con Intune o Azure AD híbrido Unidos indefinidos](#misidentified-intune-compliant-or-hybrid-azure-ad-joined-devices)
- [Los certificados de cliente no se solicitan cuando se espera](#client-certificates-are-not-prompting-when-expected)
- [Los certificados de cliente se solicitan en cada inicio de sesión](#client-certificates-are-prompting-at-every-login)
- [Consideraciones adicionales](#device-identification-additional-considerations)

#### <a name="misidentified-intune-compliant-or-hybrid-azure-ad-joined-devices"></a>Dispositivos compatibles con Intune o Azure AD híbrido Unidos indefinidos

Azure AD el acceso condicional permite que la información del dispositivo compatible con Intune y la Azure AD híbrido combinada se pase directamente a Cloud App Security, donde el estado del dispositivo se puede usar como filtro para las directivas de acceso o de sesión. Para obtener más información, vea [Introducción a la administración de dispositivos en Azure Active Directory](/azure/active-directory/devices/overview).

**Pasos recomendados**

1. En Cloud App Security, en la barra de menús, haga clic en la configuración engranaje y, a continuación, seleccione **configuración**.
1. En **control de aplicaciones de acceso condicional**, seleccione **identificación del dispositivo**. En esta página se muestran las opciones de identificación de dispositivos disponibles en Cloud App Security.
1. Para la **identificación de dispositivos compatibles con Intune** y la **identificación combinada de Azure ad híbrido** , respectivamente, haga clic en **Ver configuración** y compruebe que los servicios están configurados.

    > [!NOTE]
    > Estos se sincronizan automáticamente desde Azure AD e Intune, respectivamente.
1. Cree una directiva de acceso o sesión con el filtro de **etiquetas de dispositivo** igual a **Azure ad híbrido Unido**, **compatible con Intune**o ambos.
1. En un explorador, inicie sesión en un dispositivo que esté Azure AD híbrido Unido o compatible con Intune según el filtro de la Directiva.
1. Compruebe que las actividades de estos dispositivos rellenan el registro. En Cloud App Security, en la página **registro de actividad** , [filtre](activity-filters.md) por la **etiqueta de dispositivo** igual a **Azure ad híbrido unida**, **compatible con Intune**o ambos según los filtros de la Directiva.
1. Si las actividades no se rellenan en el registro de actividad Cloud App Security, vaya a Azure AD y haga lo siguiente:
    1. En **Monitoring**  >  **inicios de sesión**de supervisión, compruebe que hay actividades de inicio de sesión en los registros.
    1. Seleccione la entrada de registro correspondiente al dispositivo en el que ha iniciado sesión.
    1. En el panel **Detalles**, en la pestaña **Información del dispositivo**, compruebe que el dispositivo está **administrado** (unido a Azure AD híbrido) o es **compatible** (compatible con Intune). Si no puede comprobar ninguno de estos estados, pruebe con otra entrada de registro o asegúrese de que los datos del dispositivo estén configurados correctamente en Azure AD.
    1. En el caso del acceso condicional, algunos exploradores pueden requerir una configuración adicional, como la instalación de una extensión. Utilice la información de la guía de [soporte del explorador de acceso condicional](/azure/active-directory/conditional-access/concept-conditional-access-conditions#supported-browsers) para configurar el explorador.
    1. Si sigue sin ver la información del dispositivo en la página **inicios de sesión** , abra una incidencia de soporte técnico para Azure ad.

#### <a name="client-certificates-are-not-prompting-when-expected"></a>Los certificados de cliente no se solicitan cuando se espera

El mecanismo de identificación de dispositivos puede solicitar la autenticación de los dispositivos que usan certificados de cliente. Puede cargar una entidad de certificación X. 509 o una entidad de certificación (CA) intermedia con formato en el formato de certificado PEM. Estos certificados deben contener la clave pública de la CA, que se usa para firmar los certificados de cliente presentados durante una sesión. Para obtener más información sobre los certificados de cliente, consulte [dispositivos autenticados con el certificado de cliente](proxy-intro-aad.md#client-certificate-authenticated-devices).

**Pasos recomendados**

1. En Cloud App Security, en la barra de menús, haga clic en la configuración engranaje y, a continuación, seleccione **configuración**.
1. En **control de aplicaciones de acceso condicional**, seleccione **identificación del dispositivo**. En esta página se muestran las opciones de identificación de dispositivos disponibles en Cloud App Security.
1. Compruebe que cargó una entidad de certificación X. 509 o una CA intermedia. Debe cargar la CA que se usa para firmar la entidad de certificación correspondiente.
1. Cree una directiva de acceso o sesión con el filtro **etiqueta de dispositivo** igual a **certificado de cliente válido**.
1. Asegúrese de que el certificado de cliente es:
    - implementado con el formato de archivo PKCS #12, normalmente una extensión de archivo. p12 o. pfx
    - instalado en el almacén del usuario, no en el almacén del dispositivo, de la máquina que está usando para las pruebas
1. Reiniciar la sesión del explorador
1. Al iniciar sesión en la aplicación protegida
    - Compruebe que se le redirige a la dirección URL. `<https://*.managed.access-control.cas.ms/aad_login>`
    - Si usa iOS, asegúrese de que está usando el explorador Safari.
    - Si usa Firefox, también debe agregar el certificado al propio almacén de certificados de Firefox. Todos los demás exploradores usan el mismo almacén de certificados predeterminado. Obtenga información acerca [de cómo agregar un certificado al almacén de certificados de Firefox](http://www.jscape.com/blog/firefox-client-certificate).
1. Compruebe que el certificado de cliente se le ha solicitado en el explorador.
    - Si no aparece, pruebe con otro explorador. La mayoría de los exploradores principales admiten la comprobación de certificados de cliente. Sin embargo, las aplicaciones móviles y de escritorio a menudo aprovechan los exploradores integrados que pueden no admitir esta comprobación y, por tanto, afectan a la autenticación de estas aplicaciones.
1. Compruebe que las actividades de estos dispositivos rellenan el registro. En Cloud App Security, en la **Página registro de actividad** , [filtre](activity-filters.md) por la **etiqueta de dispositivo** igual a **certificado de cliente válido**.
1. Si todavía no ve el mensaje, abra una incidencia de [soporte técnico](support-and-ts.md) e incluya la siguiente información:
    - Los detalles del explorador o la aplicación nativa en la que experimentó el problema
    - La versión del sistema operativo (por ejemplo, iOS/Android/Windows 10)
    - Mencione si el aviso está funcionando en el cromo perimetral

#### <a name="client-certificates-are-prompting-at-every-login"></a>Los certificados de cliente se solicitan en cada inicio de sesión

Si está experimentando el certificado de cliente que se está expulsando después de abrir una nueva pestaña, esto puede deberse a que la configuración está oculta en **las opciones de Internet**.

| Browser | Pasos |
|---|---|
| Microsoft Internet Explorer | 1. abrir Internet Explorer<br />2. seleccionar **herramientas**  >  **Opciones**  >  **avanzadas** de Internet (pestaña)<br />3. en **seguridad**, seleccione **no solicitar la selección de certificado de cliente cuando solo existe un certificado** .<br />4. Seleccione **aplicar**y, después, haga clic en **Aceptar** .<br />5. Reinicie el explorador y compruebe que puede acceder a la aplicación sin los mensajes adicionales. |
| Cromo de Microsoft Edge/Edge | 1. Abra la búsqueda desde la barra de tareas y busque "opciones de Internet"<br />2. Seleccione **Opciones de Internet**<br />3. en **seguridad**, seleccione **no solicitar la selección de certificado de cliente cuando solo existe un certificado** .<br />4. Seleccione **aplicar**y, después, haga clic en **Aceptar** .<br />5. Reinicie el explorador y compruebe que puede acceder a la aplicación sin los mensajes adicionales. |

<a name="device-identification-additional-considerations"></a>

#### <a name="additional-considerations"></a>Consideraciones adicionales

Al solucionar problemas de identificación de dispositivos, debe tener en cuenta algunos aspectos adicionales.

- **Protocolo de revocación de certificados de cliente**

    Puede exigir la revocación de certificados para los certificados de cliente. Los certificados revocados por la CA ya no son de confianza. Si selecciona esta opción, se requerirán todos los certificados para pasar el protocolo CRL. Si el certificado de cliente no contiene un punto de conexión de CRL, no podrá conectarse desde el dispositivo administrado.

### <a name="onboarding-an-app"></a>Incorporación de una aplicación

Puede incorporar los siguientes tipos de aplicaciones para los controles de acceso y de sesión:

- Aplicaciones destacadas: aplicaciones que se incorporan a los controles de sesión, tal y como se indica en la etiqueta de **control de sesión**

- Cualquier aplicación (personalizada): un administrador puede incorporar las aplicaciones de línea de negocio (LOB) personalizadas o locales a los controles de sesión.

![Lista de proxy que muestra aplicaciones destacadas (personalizadas)](media/troubleshooting-onboarding.png)

Al incorporar una aplicación, es fundamental asegurarse de que sigue cada paso en las guías de implementación de proxy:

1. [Implementación de aplicaciones destacadas con controles de sesión](proxy-deployment-aad.md)
1. [Implementación de aplicaciones de LOB personalizadas, aplicaciones SaaS no destacadas y aplicaciones locales hospedadas a través del proxy de aplicación de Azure AD con controles de sesión](proxy-deployment-any-app.md)

Entre los escenarios comunes que pueden surgir durante la incorporación de una aplicación se incluyen:

- [La aplicación no aparece en la página de **aplicaciones de control de aplicaciones de acceso condicional**](#app-does-not-appear-on-the-conditional-access-app-control-apps-page)
- [Estado de la aplicación: continuar con la instalación](#app-status-continue-setup)
- [No se pueden configurar controles para aplicaciones nativas](#cannot-configure-controls-for-native-apps)
- [Aparece la página **no se reconoce la aplicación**](#something-went-wrong-page-appears)
- [Aparece la opción de **control de sesión de solicitud**](#request-session-control-option-appears)
- [Consideraciones adicionales](#onboarding-apps-additional-considerations)

#### <a name="app-does-not-appear-on-the-conditional-access-app-control-apps-page"></a>La aplicación no aparece en la página de aplicaciones de Control de aplicaciones de acceso condicional

Al incorporar una aplicación para Control de aplicaciones de acceso condicional, el último paso de las guías de implementación es hacer que el usuario final navegue hasta la aplicación. Las recomendaciones que se enumeran a continuación son pasos que se pueden realizar si la aplicación no aparece después de haber pasado por las guías.

**Pasos recomendados**

1. Asegúrese de que la aplicación cumple los requisitos previos de la aplicación de acceso condicional

| Proveedor de identidades | Validations (Validaciones) |
|---|---|
| Azure AD | 1. Asegúrese de que tiene una licencia válida para Azure AD Premium P1 además de una licencia de Cloud App Security<br />2. Asegúrese de que la aplicación usa el protocolo SAML 2,0 o OpenID Connect.<br />3. Asegúrese de que el inicio de sesión único de la aplicación en Azure AD |
| Aplicaciones de terceros | 1. Asegúrese de que tiene una licencia de Cloud App Security válida<br />2. crear una aplicación duplicada<br />3. Asegúrese de que la aplicación usa el protocolo SAML.<br />4. Compruebe que ha incorporado completamente la aplicación y que el estado de la aplicación está **conectado** . |

1. En la Directiva de Azure AD, en la **sesión**, asegúrese de que la sesión se ve obligada a enrutar a Cloud App Security, que a su vez permitirá que la aplicación aparezca en en la página **control de aplicaciones de acceso condicional aplicaciones** , como se indica a continuación:
    1. Control de aplicaciones de acceso condicional está seleccionado
    1. En la lista desplegable directivas integradas, asegúrese de que **monitor solo** está seleccionado.
1. Asegúrese de navegar a la aplicación en una nueva sesión del explorador mediante un nuevo modo de incógnito o iniciando sesión de nuevo.

#### <a name="app-status-continue-setup"></a>Estado de la aplicación: continuar con la instalación

El estado de una aplicación puede variar de **continuar la instalación**, **conectarse**y **no actividades**.

En el caso de las aplicaciones conectadas a través de otros proveedores de identidades (IdP), si la instalación no se completa, al acceder a la aplicación, verá una página con el estado de **continuar la instalación**. Siga los pasos que se indican a continuación para completar la instalación.

**Pasos recomendados**

1. Haga clic en **continuar configuración**.
1. Siga la [Guía de implementación](proxy-deployment-any-app.md#conf-app) y compruebe que ha completado todos los pasos. Preste especial atención a lo siguiente:
    1. Asegúrese de crear una nueva aplicación SAML personalizada. Lo necesita para cambiar las direcciones URL y los atributos SAML que podrían no estar disponibles en las aplicaciones de la galería.
    1. Si el proveedor de identidades no permite la reutilización del mismo identificador (también conocido como identificador de entidad o audiencia), cambie el identificador de la aplicación original.

#### <a name="cannot-configure-controls-for-native-apps"></a>No se pueden configurar controles para aplicaciones nativas

Las aplicaciones nativas se pueden detectar heurísticamente y puede usar directivas de acceso para supervisarlas o bloquearlas. Siga estos pasos para configurar controles para aplicaciones nativas.

**Pasos recomendados**

1. En una directiva de acceso, agregue un filtro de **aplicación cliente** y establézcalo igual a **móvil y escritorio**.
1. En acciones, seleccione **bloquear**.
1. Opcionalmente, puede personalizar el mensaje de bloqueo que los usuarios obtienen cuando no pueden descargar archivos, por ejemplo, "debe usar un explorador Web para tener acceso a esta aplicación".
1. Pruebe y valide que el control funciona según lo previsto.

#### <a name="app-is-not-recognized-page-appears"></a>Aparece la página no se reconoce la aplicación

Cloud App Security pueden reconocer más de 16.000 aplicaciones a través del catálogo de aplicaciones en la nube (**detectar**el catálogo de aplicaciones en la  ->  **nube**). Si usa una aplicación personalizada que se configura a través de Azure AD SSO que no es una de las aplicaciones 16.000, **no se reconoce** la página de la aplicación. Para resolver el problema, debe configurar la aplicación en el Control de aplicaciones de acceso condicional.

**Pasos recomendados**

1. En Cloud App Security, en la barra de menús, haga clic en el engranaje de configuración y seleccione **control de aplicaciones de acceso condicional**.
1. En el encabezado, haga clic en **ver nuevas aplicaciones**.
1. En la lista de aplicaciones nuevas, busque la aplicación que está incorporando, haga clic en el **+** signo y, a continuación, haga clic en **Agregar**.
    1. Seleccione si la aplicación es una aplicación **estándar** o **personalizada** .
    1. Continúe con el asistente, asegúrese de que los **dominios definidos** por el usuario especificados son correctos para la aplicación que está configurando.
1. Compruebe que la aplicación aparece en la página **control de aplicaciones de acceso condicional aplicaciones** .

#### <a name="request-session-control-option-appears"></a>Aparece la opción de control de sesión de solicitud

Después de agregar una aplicación, puede ver la opción **solicitar control de sesión** . Esto se debe a que solo las aplicaciones destacadas tienen controles de sesión listos para su aplicación. Para cualquier otra aplicación, debe pasar por un proceso de incorporación automática.

**Pasos recomendados**

1. En Cloud App Security, en la barra de menús, haga clic en el engranaje de configuración y seleccione **configuración**.
1. En **control de aplicaciones de acceso condicional**, seleccione **incorporación/mantenimiento**de la aplicación.
1. Escriba el nombre principal de usuario o el correo electrónico de los usuarios que van a incorporar la aplicación y, a continuación, haga clic en **Guardar**.
1. Vaya a la aplicación que va a implementar. La página que vea dependerá de si se reconoce la aplicación. Realice una de las siguientes acciones:

    | Estado de la aplicación | Description | Pasos |
    | --- | --- | --- |
    | No reconocido | Verá una página de aplicación no reconocida que le pide que configure la aplicación. | 1. [agregue la aplicación a control de aplicaciones de acceso condicional](proxy-deployment-any-app.md#add-app).<br /> 2. [agregue los dominios de la aplicación](proxy-deployment-any-app.md#add-domains)y, a continuación, vuelva a la aplicación y actualice la página.<br /> 3. [Instale los certificados para la aplicación](proxy-deployment-any-app.md#install-certs). |
    | Recognized | Verá una página de incorporación que le pide que continúe con el proceso de configuración de la aplicación. | - [Instale los certificados para la aplicación](proxy-deployment-any-app.md#install-certs). <br /><br /> **Nota:** Asegúrese de que la aplicación esté configurada con todos los dominios necesarios para que la aplicación funcione correctamente. Para configurar dominios adicionales, vaya a [Agregar los dominios de la aplicación](proxy-deployment-any-app.md#add-domains)y, a continuación, vuelva a la página de la aplicación. |

<a name="onboarding-apps-additional-considerations"></a>

#### <a name="additional-considerations"></a>Consideraciones adicionales

Al solucionar problemas de las aplicaciones de incorporación, hay algunos aspectos adicionales que hay que tener en cuenta.

- **Las aplicaciones de Control de aplicaciones de acceso condicional no se alinean con Azure AD aplicaciones**

    Los nombres de aplicación de Azure AD y Cloud App Security pueden diferir en función de las formas en que los productos identifican las aplicaciones. Cloud App Security identifica las aplicaciones que usan los dominios de la aplicación y las agrega al [Catálogo de aplicaciones](risk-score.md#the-cloud-app-catalog)en la nube, donde tenemos más de 16.000 aplicaciones. En cada aplicación, puede ver o agregar al subconjunto de dominios. Por el contrario, Azure AD identifica las aplicaciones que usan entidades de servicio. Para obtener más información, consulte [objetos de aplicación y de entidad de servicio en Azure ad](/azure/active-directory/develop/app-objects-and-service-principals).

    En la práctica, esto significa que seleccionar **SharePoint Online** en Azure ad es equivalente a seleccionar aplicaciones, como Word online y equipos, en Cloud App Security porque las aplicaciones usan el `sharepoint.com` dominio.

### <a name="creating-access-and-session-policies"></a>Crear directivas de acceso y de sesión

Cloud App Security proporciona las siguientes directivas configurables:

1. [Directivas de acceso](access-policy-aad.md): para supervisar o bloquear el acceso a las aplicaciones de explorador, móviles o de escritorio
1. [Directivas de sesión](session-policy-aad.md). Para supervisar, bloquear y realizar acciones específicas para evitar escenarios de infiltración de datos y de exfiltración en el explorador

Para usar estas directivas en Cloud App Security, primero debe configurar una directiva en Azure AD el acceso condicional para extender los controles de sesión, como se indica a continuación: en la Directiva de Azure AD, en **controles de acceso**, haga clic en **sesión**, seleccione **usar control de aplicaciones de acceso condicional** y elija una directiva integrada (**supervisar solo** o **bloquear descargas**) o use **la** **directiva personalizada** para establecer una directiva avanzada en Cloud App Security

Entre los escenarios comunes que puede encontrar al configurar estas directivas se incluyen:

- [En las directivas de acceso condicional, no se puede ver la opción **control de aplicaciones de acceso condicional**](#in-conditional-access-policies-you-cannot-see-the-conditional-access-app-control-option)
- [Mensaje de error al crear una directiva: no tiene ninguna aplicación implementada con Control de aplicaciones de acceso condicional](#error-message-when-creating-a-policy-you-dont-have-any-apps-deployed-with-conditional-access-app-control)
- [No se pueden crear directivas de sesión para una aplicación](#cannot-create-session-policies-for-an-app)
- [No se puede elegir el **método de inspección**: servicio de **clasificación de datos**](#cannot-choose-inspection-method-data-classification-service)
- [No se puede elegir la **acción**: **proteger**](#cannot-choose-action-protect)
- [Consideraciones adicionales](#policies-additional-considerations)

#### <a name="in-conditional-access-policies-you-cannot-see-the-conditional-access-app-control-option"></a>En las directivas de acceso condicional, no se puede ver la opción Control de aplicaciones de acceso condicional

Para enrutar las sesiones a Cloud App Security, Azure AD las directivas de acceso condicional deben configurarse para incluir Control de aplicaciones de acceso condicional controles de sesión.

**Pasos recomendados**

- Si no ve la opción **control de aplicaciones de acceso condicional** en la Directiva de acceso condicional, asegúrese de que tiene una licencia válida para Azure ad Premium P1, así como una licencia Cloud App Security válida.

#### <a name="error-message-when-creating-a-policy-you-dont-have-any-apps-deployed-with-conditional-access-app-control"></a>Mensaje de error al crear una directiva: no tiene ninguna aplicación implementada con Control de aplicaciones de acceso condicional

Al crear una directiva de acceso o sesión, es posible que vea el siguiente mensaje de error: "no tiene ninguna aplicación implementada con Control de aplicaciones de acceso condicional". Este error indica que la aplicación no se ha implementado.

**Pasos recomendados**

1. En Cloud App Security, en la barra de menús, haga clic en el engranaje de configuración y seleccione **control de aplicaciones de acceso condicional**.
1. Si ve el mensaje **no hay ninguna aplicación conectada**, use la guía siguiente para implementar aplicaciones:

    - [Implementar aplicaciones destacadas que tienen habilitado el control de sesión](proxy-deployment-aad.md)
    - [Implementación de aplicaciones de línea de negocio personalizadas, aplicaciones SaaS no destacadas y aplicaciones locales](proxy-deployment-any-app.md) hospedadas a través del proxy de aplicación de Azure Active Directory (Azure ad) con controles de sesión
1. Si surge algún problema durante la implementación de la aplicación, consulte [incorporación de una aplicación](#onboarding-an-app).

#### <a name="cannot-create-session-policies-for-an-app"></a>No se pueden crear directivas de sesión para una aplicación

Después de agregar una aplicación personalizada, en la página **control de aplicaciones de acceso condicional aplicaciones** , puede ver la opción: **solicitar control**de la sesión.

> [!NOTE]
> [Aplicaciones destacadas](proxy-intro-aad.md#session-controls) tienen controles de sesión listos para su el cuadro. En el caso de otras aplicaciones, debe pasar por un proceso de incorporación automática.

**Pasos recomendados**

1. Use la siguiente guía de auto-incorporación para implementar cualquier aplicación en el control de sesión: [implementar aplicaciones de línea de negocio personalizadas, aplicaciones SaaS no destacadas y aplicaciones locales](proxy-deployment-any-app.md) hospedadas a través del proxy de aplicación de Azure Active Directory (Azure ad) con controles de sesión.
1. Cree una directiva de sesión, seleccione el filtro de **aplicación** , asegúrese de que la aplicación aparece ahora en la lista desplegable.

#### <a name="cannot-choose-inspection-method-data-classification-service"></a>No se puede elegir el **método de inspección**: servicio de **clasificación de datos**

En las directivas de sesión, al usar el tipo de control de sesión control de la **descarga de archivos (con inspección)** , puede usar el método de inspección del **servicio de clasificación de datos** para examinar los archivos en tiempo real y detectar contenido confidencial que coincida con cualquiera de los criterios que ha configurado. Si el método de inspección del **servicio de clasificación de datos** no está disponible, siga estos pasos para investigar el problema.

**Pasos recomendados**

1. Compruebe que el **tipo de control de sesión** está configurado para **controlar la descarga de archivos (con inspección)**.

    > [!NOTE]
    > El método de inspección del **servicio de clasificación de datos** solo está disponible para la opción controlar la descarga de **archivos (con inspección)** .

1. Determine si la característica **servicio de clasificación de datos** está disponible en su [región](dcs-inspection.md).
    1. Si la característica no está disponible en su región, use el método de inspección **de DLP integrado** .
    1. Si la característica está disponible en su región, pero todavía no puede ver el método de inspección del **servicio de clasificación de datos** , abra una incidencia de [soporte técnico](support-and-ts.md).

#### <a name="cannot-choose-action-protect"></a>No se puede elegir la acción: proteger

En las directivas de sesión, cuando se usa el tipo de control de sesión control de la **descarga de archivos (con inspección)** , además de las acciones de **supervisión** y **bloqueo** , se puede especificar la acción de **protección** . Esta acción le permite permitir la descarga de archivos con la opción de cifrar o aplicar permisos al archivo en función de las condiciones, la inspección de contenido o ambos. Si la acción **proteger** no está disponible, siga estos pasos para investigar el problema.

**Pasos recomendados**

1. Si la acción de **protección** no está disponible o está atenuada, compruebe que dispone de la licencia de Azure Information Protection (AIP) Premium P1. Para más información, consulte [Integración de Azure Information Protection](azip-integration.md).
1. Si la acción de **protección** está disponible, pero no ve las etiquetas adecuadas.
    1. En Cloud App Security, en la barra de menús, haga clic en el engranaje de configuración, seleccione **Azure Information Protection**y compruebe que la integración de AIP está habilitada.
    1. En el caso de las etiquetas de Office, en el portal de AIP, asegúrese de que está seleccionado el **etiquetado unificado** .

<a name="policies-additional-considerations"></a>

#### <a name="additional-considerations"></a>Consideraciones adicionales

Al solucionar problemas de las aplicaciones de incorporación, hay algunos aspectos adicionales que hay que tener en cuenta.

- **Descripción de la diferencia entre el Azure AD la configuración de la Directiva de acceso condicional: "solo supervisar", "bloquear descargas" y "usar directiva personalizada"**

    En Azure AD las directivas de acceso condicional, puede configurar los siguientes controles de Cloud App Security integrados: **supervisar solo** y **bloquear descargas**. Esto se aplica y exige la característica de proxy de Cloud App Security para las aplicaciones en la nube y las condiciones configuradas en Azure AD. Para las directivas más complejas, seleccione **usar directiva personalizada**, que le permite configurar directivas de acceso y sesión en Cloud App Security.

- **Descripción de la opción de filtro de la aplicación cliente "móvil y escritorio" en las directivas de acceso**

    En Cloud App Security directivas de acceso, a menos que el filtro de la **aplicación cliente** se establezca específicamente en **móvil y escritorio**, la Directiva de acceso resultante solo se aplicará a las sesiones del explorador. La razón de esto es evitar que las sesiones de usuario se configuran de forma inadvertida para el proxy, lo que puede ser un subproducto del uso de este filtro.

## <a name="issues-experienced-by-end-users"></a>Problemas experimentados por los usuarios finales

Esta sección es para los usuarios finales que usan aplicaciones protegidas por Cloud App Security y ayuda a identificar las situaciones comunes que pueden surgir en las siguientes áreas:

- [La página de supervisión de usuarios no aparece](#user-monitoring-page-is-not-appearing)
- [No se puede tener acceso a la aplicación desde un proveedor de identidades de terceros](#not-able-to-access-app-from-a-third-party-identity-provider)
- [Aparece **un error** en la página](#something-went-wrong-page-appears)
- [No se bloquean las acciones o los controles de archivo del portapapeles](#clipboard-actions-or-file-controls-are-not-being-blocked)
- [No se están protegiendo las descargas](#downloads-are-not-being-protected)
- [Navegación a una dirección URL concreta de una aplicación con sufijo y aterrizaje en una página genérica](#navigating-to-a-particular-url-of-a-suffixed-app-and-landing-on-a-generic-page)
- [Consideraciones adicionales](#app-additional-considerations)

### <a name="user-monitoring-page-is-not-appearing"></a>La página de supervisión de usuarios no aparece

Al enrutar a un usuario a través del Cloud App Security, puede notificar al usuario que se va a supervisar su sesión. De forma predeterminada, la página supervisión de usuarios está habilitada.

**Pasos recomendados**

1. En Cloud App Security, en la barra de menús, haga clic en la configuración engranaje y, a continuación, seleccione **configuración**.
1. En **control de aplicaciones de acceso condicional**, seleccione **supervisión de usuarios**. En esta página se muestran las opciones de supervisión de usuarios disponibles en Cloud App Security.

    ![Captura de pantalla que muestra las opciones de supervisión de usuarios](media/proxy-user-monitoring.png)

1. Compruebe que la opción **notificar a los usuarios que se está supervisando su actividad** está seleccionada.
1. Elija si desea usar el mensaje predeterminado o proporcionar un mensaje personalizado.

    | Tipo de mensaje | Detalles |
    | --- | --- |
    | Valor predeterminado | **Encabezado**:<br />El acceso a [nombre de la aplicación aparecerá aquí] está supervisado<br />**Cuerpo**:<br />Para mejorar la seguridad, su organización permite el acceso a [el nombre de la aplicación aparecerá aquí] en modo de supervisión. El acceso solo está disponible desde un explorador Web. |
    | Personalizado | **Encabezado**:<br />Use este cuadro para proporcionar un encabezado personalizado para informar a los usuarios que se están supervisando.<br />**Cuerpo**:<br />Use este cuadro para agregar información personalizada adicional para el usuario, como quién debe ponerse en contacto con preguntas y admite las siguientes entradas: texto sin formato, texto enriquecido, hipervínculos. |
1. Haga clic en **vista previa** para comprobar la página de supervisión de usuarios que aparece antes de acceder a una aplicación.
1. Haga clic en **Save**(Guardar).

### <a name="not-able-to-access-app-from-a-third-party-identity-provider"></a>No se puede tener acceso a la aplicación desde un proveedor de identidades de terceros

Si un usuario final recibe un error general después de iniciar sesión en una aplicación de un proveedor de identidades de terceros, valide la configuración de IdP de terceros.

**Pasos recomendados**

1. En Cloud App Security, en la barra de menús, haga clic en el engranaje de configuración y seleccione **control de aplicaciones de acceso condicional**.
1. En la lista de aplicaciones, en la fila en la que no se puede acceder a la aplicación, elija los tres puntos al final de la fila y, después, elija **Editar** aplicación.
    1. Validar que el certificado SAML que se cargó es correcto
    1. Compruebe que se han proporcionado direcciones URL de SSO válidas en la configuración de la aplicación.
    1. Compruebe que los atributos y valores de la aplicación personalizada se reflejan en la captura de pantalla de la configuración del proveedor de identidades  ![ que muestra la página de información de SAML de proveedores de identidades.](media/proxy-deploy-add-idp-ext-conf.png)
1. Si sigue sin poder acceder a la aplicación, abra una [incidencia de soporte técnico](support-and-ts.md).

### <a name="something-went-wrong-page-appears"></a>Aparece un error en la página

A veces, durante una sesión de proxy, es posible que aparezca la página se produjo **un error** . Esto puede suceder cuando:

1. Un usuario inicia sesión después de estar inactivo durante un tiempo
1. La actualización del explorador y la carga de la página tarda más de lo esperado
1. La aplicación de IdP de terceros no está configurada correctamente

**Pasos recomendados**

1. Si el usuario final intenta acceder a una aplicación que está configurada con un IdP de terceros, consulte [no se puede acceder a la aplicación desde un IDP de terceros y estado de la](#not-able-to-access-app-from-a-third-party-identity-provider) [aplicación: continuar con la instalación](#app-status-continue-setup).
1. Si el usuario final llegó a esta página de forma inesperada, haga lo siguiente:
    1. Reiniciar la sesión del explorador
    1. Borrar el historial, las cookies y la memoria caché desde el explorador

### <a name="clipboard-actions-or-file-controls-are-not-being-blocked"></a>No se bloquean las acciones o los controles de archivo del portapapeles

La capacidad de bloquear acciones del portapapeles, como cortar, copiar, pegar y controles de archivo como descargar, cargar e imprimir, es necesaria para evitar escenarios de infiltración de datos y de infiltración. Esta capacidad permite a las empresas equilibrar la seguridad y la productividad de los usuarios finales. Si tiene problemas con estas características, siga estos pasos para investigar el problema.

**Pasos recomendados**

Si la sesión se está procesando en proxy, siga estos pasos para comprobar la Directiva:

1. En Cloud App Security, en **investigar**, seleccione **registro de actividad**.
1. Use el filtro avanzado, seleccione **acción aplicada** y establezca su valor en **bloqueado**.
1. Compruebe que existen actividades de archivos bloqueados.
    1. Si hay una actividad, expanda el cajón de actividades haciendo clic en la actividad.
    1. En la pestaña **General** del cajón de actividades, haga clic en el vínculo directivas coincidentes para comprobar que la Directiva que ha aplicado está presente.
    1. Si no ve la Directiva, consulte [crear directivas de acceso y de sesión](#creating-access-and-session-policies).
    1. Si ve **acceso bloqueado/permitido debido al comportamiento predeterminado**, esto indica que el sistema estaba inactivo y se aplicó el comportamiento predeterminado.
        1. Para cambiar el comportamiento predeterminado, en Cloud App Security, en la barra de menús, haga clic en el engranaje de configuración y seleccione **configuración**. A continuación, en **control de aplicaciones de acceso condicional**, seleccione **comportamiento predeterminado**y establezca el comportamiento predeterminado para **permitir** o **bloquear** el acceso.
        1. Vaya a `https://status.cloudappsecurity.com/` y supervise las notificaciones sobre el tiempo de inactividad del sistema.
1. Si todavía no puede ver la actividad bloqueada, abra una [incidencia de soporte técnico](support-and-ts.md).

### <a name="downloads-are-not-being-protected"></a>No se están protegiendo las descargas

Como usuario final, podría ser necesario descargar datos confidenciales en un dispositivo no administrado. En estos casos, puede proteger los documentos con Azure Information Protection. Si el usuario final no pudo cifrar el documento correctamente, siga estos pasos para investigar el problema.

**Pasos recomendados**

1. En Cloud App Security, en **investigar**, seleccione **registro de actividad**.
1. Use el filtro avanzado, seleccione **acción aplicada** y establezca su valor en **protegido**.
1. Compruebe que existen actividades de archivos bloqueados.
    1. Si hay una actividad, expanda el cajón de actividades haciendo clic en la actividad.
    1. En la pestaña **General** del cajón de actividades, haga clic en el vínculo directivas coincidentes para comprobar que la Directiva que ha aplicado está presente.
    1. Si no ve la Directiva, consulte [crear directivas de acceso y de sesión](#creating-access-and-session-policies).
    1. Si ve **acceso bloqueado/permitido debido al comportamiento predeterminado**, esto indica que el sistema estaba inactivo y se aplicó el comportamiento predeterminado.
        1. Para cambiar el comportamiento predeterminado, en Cloud App Security, en la barra de menús, haga clic en el engranaje de configuración y, a continuación, seleccione **configuración**. A continuación, en **control de aplicaciones de acceso condicional**, seleccione **comportamiento predeterminado**y establezca el comportamiento predeterminado para **permitir** o **bloquear** el acceso.
        1. Vaya a `https://status.cloudappsecurity.com/` y supervise las notificaciones sobre el tiempo de inactividad del sistema.
    1. Si va a proteger el archivo con una etiqueta de AIP o permisos personalizados, en la descripción de la **actividad**, asegúrese de que la extensión de archivo es uno de los siguientes tipos de archivo admitidos:
        - Word: docm, docx, dotm, dotx
        - Excel: xlam, xlsm, xlsx, xltx
        - PowerPoint: potm, potx, ppsx, ppsm, pptm, pptx
        - PDF * si está habilitada la etiqueta unificada
    - Si no se admite el tipo de archivo, en la Directiva de sesión, puede seleccionar **bloquear la descarga de cualquier archivo que no sea compatible con la protección nativa o donde la protección nativa no sea correcta**.
1. Si todavía no puede ver la actividad bloqueada, abra una [incidencia de soporte técnico](support-and-ts.md).

### <a name="navigating-to-a-particular-url-of-a-suffixed-app-and-landing-on-a-generic-page"></a>Navegación a una dirección URL concreta de una aplicación con sufijo y aterrizaje en una página genérica

Todos los servidores proxy que son susceptibles a la pérdida de contexto, un problema en el que la navegación a un vínculo pierde la ruta de acceso completa del vínculo y que normalmente se encuentran en la Página principal de la aplicación. Cloud App Security está posicionada de forma exclusiva para abordar esta limitación y resolver la pérdida de contexto mediante la asociación con proveedores de Microsoft y otros fabricantes.

Las aplicaciones de nuestra página de aplicaciones destacadas marcadas como **(vista previa)** pueden sufrir una pérdida de contexto. Del mismo modo, la pérdida de contexto puede deberse a directivas globales que bloquean cookies de terceros o seguimiento entre sitios. Puede corregir el problema deshabilitando estas opciones. En el caso de las aplicaciones no destacadas que experimentan pérdida de contexto, envíe una incidencia de soporte técnico. Estamos trabajando con cada proveedor de aplicaciones individualmente para corregir estos problemas principales.

Como mitigación temporal, puede solucionar problemas de pérdida de contexto, como se indica a continuación:

1. Navegue a una dirección URL donde se produzca la pérdida de contexto.
1. Anote el dominio de dirección URL con sufijo incluido el sufijo agregado por Cloud App Security, por ejemplo `https://www.yammer.com.us2.cas.ms` .
1. Copie la ruta de acceso de la dirección URL original, por ejemplo, si la dirección URL concreta original era `https://www.yammer.com/organization/threads/threadnumber` , Copy `/organization/threads/threadnumber` .
1. Anexe la ruta de acceso copiada al dominio con sufijo, por ejemplo `https://www.yammer.com.us2.cas.ms/organization/threads/threadnumber` .
1. Navegue a la nueva dirección URL con sufijo.

<a name="app-additional-considerations"></a>

### <a name="additional-considerations"></a>Consideraciones adicionales

Al solucionar problemas de las aplicaciones, hay algunos aspectos adicionales que hay que tener en cuenta.

- **Compatibilidad de los controles de sesión con los exploradores modernos**

    Los controles de sesión de Cloud App Security ahora incluyen compatibilidad con el nuevo explorador Microsoft Edge basado en Chromium. Aunque continuaremos admitiendo las versiones más recientes de Internet Explorer y la versión heredada de Microsoft Edge, la compatibilidad será limitada y se recomienda usar el nuevo explorador Microsoft Edge.

- **Inicio de sesión doble**

    Se produce un inicio de sesión doble debido al uso supuesto de un valor de seguridad (nonce), un token criptográfico que usan las aplicaciones para evitar ataques de reproducción. De forma predeterminada, Cloud App Security supone que una aplicación usa un valor de seguridad (nonce). Si está seguro de que la aplicación no usa un nonce, puede deshabilitarla editando la aplicación en Cloud App Security y se resolverá el problema. Para conocer los pasos para deshabilitar el nonce, consulte [Inicio de sesión lento](#slow-login).

    Si la aplicación usa un nonce y esta característica no se puede deshabilitar, el segundo inicio de sesión puede ser transparente para los usuarios o se le pedirá que vuelva a iniciar sesión.

- **Es posible que se bloquee la vista previa o la impresión de archivos PDF**

    Este es el comportamiento normal cuando se tiene una directiva configurada para bloquear descargas. En ocasiones, al obtener una vista previa de los archivos PDF o imprimirlos, las aplicaciones inician una descarga del archivo que hace que Cloud App Security intervenir para asegurarse de que la descarga está bloqueada y que los datos no se pierden del entorno.

    Si desea permitir descargas de archivos PDF, puede excluir archivos PDF en función de su extensión de archivo en la Directiva de sesión correspondiente.
