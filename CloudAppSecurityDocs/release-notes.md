---
title: Novedades de Cloud App Security | Microsoft Docs
description: Este tema se actualiza con frecuencia para informarle de las novedades de la versión más reciente de Cloud App Security.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 9/3/2018
ms.topic: conceptual
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: d418ef3d-76ee-45d5-b5ae-21346e5239a3
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 0f0cc3758f09ae77966ace3622e5c658a4e2cf9d
ms.sourcegitcommit: 0ac08ca7b3140b79f1d36ff7152476c188fa12b3
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/07/2018
ms.locfileid: "44144659"
---
*Se aplica a: Microsoft Cloud App Security*


# <a name="whats-new-with-microsoft-cloud-app-security"></a>Novedades de Microsoft Cloud App Security


## <a name="cloud-app-security-release-131"></a>Notas de la versión 131 de Cloud App Security

Publicado el 2 de septiembre de 2018

- **Revocar permisos de forma automática en las aplicaciones de riesgo de OAuth**<br>
Ahora puede controlar a qué aplicaciones de OAuth tienen acceso los usuarios, revocando el permiso de la aplicación para las aplicaciones de OAuth en Office, Google o Salesforce. Al crear una **directiva de permisos de aplicaciones**, ahora puede establecer la directiva para revocar el permiso de una aplicación. 

- **Analizador integrado adicional de Cloud Discovery compatible**<br>Cloud Discovery ahora admite el formato de registro de Forcepoint Web Security Cloud.

 
## <a name="cloud-app-security-release-130"></a>Notas de la versión 130 de Cloud App Security

Publicado el 22 de agosto de 2018


- **Nueva barra de menús**<br>
Para proporcionar una experiencia administrativa más coherente en todos los productos de Microsoft 365 y poder cambiar más fácilmente entre las soluciones de seguridad de Microsoft, la barra de menús del portal de Cloud App Security se ha movido al lado izquierdo de la pantalla. Esta experiencia de navegación coherente le ayuda a orientarse al pasar de un portal de seguridad de Microsoft a otro.

- **Impacto en la puntuación de la aplicación OAuth**<br>
Ahora puede enviar comentarios al equipo de Cloud App Security para hacernos saber si se detecta una aplicación OAuth en su organización que parece malintencionada. Esta nueva característica le permite formar parte de nuestra comunidad de seguridad y mejorar el análisis y la puntuación de riesgo de las aplicaciones OAuth. Para más información, vea [Administrar permisos de aplicación](manage-app-permissions.md).

- **Nuevos analizadores de Cloud Discovery**<br>
Los analizadores de Cloud Discovery ahora admiten iboss Secure Cloud Gateway y Sophos XG.


## <a name="cloud-app-security-release-129"></a>Notas de la versión 129 de Cloud App Security

Fecha de publicación: 5 de agosto de 2018

- **Nuevas directivas de detección de anomalías: reglas de correo electrónico sospechosas**<br>Se agregaron nuevas directivas de detección de anomalías que detectan reglas de reenvío de correo electrónico sospechosas, por ejemplo, si un usuario creó una regla de bandeja de entrada sospechosa que reenvía una copia de todos los correos electrónicos a una dirección externa. 
- Esta versión incluye correcciones y mejoras para varios problemas. 

## <a name="cloud-app-security-release-128"></a>Notas de la versión 128 de Cloud App Security

Publicada el 22 de julio de 2018

-   **Acciones de permisos de aplicación en varias aplicaciones**<br>
Para las aplicaciones a las que se han concedido permisos de aplicación, ahora puede prohibir o aprobar varias aplicaciones con una sola acción. Por ejemplo, puede revisar todas las aplicaciones a las que los usuarios de su organización han concedido un permiso, seleccionar todas las que quiera prohibir y, después, hacer clic en la opción correspondiente para revocar todos los permisos concedidos. Así, ya no se permitirá a los usuarios conceder permisos a esas aplicaciones.  Para más información, vea [Administrar permisos de aplicación](manage-app-permissions.md).
-   **Compatibilidad mejorada para las aplicaciones de Azure**<br>
Para Azure, implementaremos de forma gradual la posibilidad de identificar las aplicaciones como actividades de cuenta de usuario llevadas a cabo por las aplicaciones de Azure (tanto internas como externas). Ello le permite crear directivas que le enviarán una alerta si una aplicación realiza actividades inesperadas y no autorizadas. Para obtener más información, vea [Conectar Azure con Microsoft Cloud App Security](connect-azure-to-microsoft-cloud-app-security.md).
-   **Motor de clasificación de datos actualizado con los tipos de datos confidenciales que estipula el RGPD**<br>
El [Servicio de clasificación de datos de Cloud App Security](dcs-inspection.md) ha agregado los tipos de datos confidenciales que estipula el RGPD al motor de clasificación de datos para que pueda detectar en sus archivos el contenido relacionado con el RGPD.
-   **Actualizaciones en el catálogo de aplicaciones en la nube**<br>
Ahora, en este catálogo se incluye una categoría de riesgo legal (además de las categorías de riesgo general, de seguridad y de cumplimiento) para que pueda administrar la privacidad de los datos y el cumplimiento relativo a la propiedad, incluida la preparación para el RGPD.
Para ayudarle a evaluar la preparación para el RGPD de cada aplicación en la nube, la nueva categoría de riesgo contiene la declaración de preparación del servicio en la nube y el estado de cada control de marco del RGPD.
Tenga en cuenta que, como parte de este entorno, los atributos de riesgo que se indican a continuación se han desplazado de la categoría de riesgo Otros a la categoría Legal:
     - DMCA
     - Propiedad de los datos
     - Directiva de retención de datos

     Además, la nueva categoría de riesgo se puede puntuar por separado para configurar la ponderación de la puntuación de acuerdo con sus preferencias y prioridades. Para obtener más información, vea [Puntuación de riesgo](risk-score.md).

-   **Nueva consulta sugerida: preparación para el RGPD** <br>
Hay una nueva consulta sugerida para que pueda identificar las aplicaciones detectadas que están preparadas para el RGPD. Ya que el RGPD se ha convertido hace poco en una prioridad principal para los administradores de seguridad, esta consulta le permite identificar fácilmente las aplicaciones que están listas para el RGPD y mitigar las posibles amenazas evaluando el riesgo de las que no lo están.


## <a name="cloud-app-security-release-127"></a>Notas de la versión 127 de Cloud App Security

Publicada el 8 de julio de 2018

- Ahora tiene la posibilidad de ver actividades genéricas de Office 365 en el **Registro de actividad**, y en las **Directivas de actividad** ahora puede filtrar las actividades de Office 365 para las actividades **sin especificar**. La revisión de estas actividades le permite recabar información acerca de las actividades realizadas que aún no están clasificadas por tipo en Cloud App Security, y dichas actividades se pueden usar para enviar solicitudes al equipo de Cloud App Security para crear nuevos tipos de actividad en función de estas actividades. 

## <a name="cloud-app-security-release-126"></a>Versión 126 de Cloud App Security

Publicado el 24 de junio de 2018

-   **Disponibilidad general del Control de aplicaciones de acceso condicional**<br>El Control de aplicaciones de acceso condicional (proxy inverso) de Microsoft Cloud App Security ahora está disponible para todas las aplicaciones de SAML. El Control de aplicaciones de acceso condicional se integra directamente con las directivas de acceso condicional de Azure AD para **supervisar y controlar las sesiones de los usuarios en tiempo real** sin impedirles ser productivos. Desde la primera versión preliminar de la característica, se han agregado muchas funciones y mejoras, incluidas las siguientes: 
    -   Se ha agregado la funcionalidad para crear una [directiva de acceso](access-policy-aad.md) para administrar el acceso a las mismas aplicaciones desde clientes nativos, además de crear una directiva de sesión para el tráfico del explorador.
    -   Se ha simplificado el proceso de incorporación de aplicaciones para admitir aplicaciones de SAML personalizadas en la organización.
    -   Como parte de la red internacional de Azure, se han mejorado la integración y la interfaz para que los usuarios ubicados en cualquier lugar del mundo puedan disfrutar de una experiencia sin problemas.
 

-   **Disponibilidad general de la inspección de contenido con el Servicio de clasificación de datos de Microsoft**<br>La integración de Microsoft Cloud App Security con los Servicios de clasificación de datos de Microsoft ahora está disponible con carácter general. Esta integración le permite usar el Servicio de clasificación de datos de Microsoft de forma nativa para clasificar los archivos de las aplicaciones en la nube. Para obtener más información, vea [Integración de los servicios de clasificación de datos de Microsoft](dcs-inspection.md). Esta característica solo está disponible en Estados Unidos y Europa (excepto en Francia).

- **Informe ejecutivo de Cloud Discovery**<br>Microsoft Cloud App Security está implementando gradualmente la funcionalidad para generar un informe ejecutivo en PDF de Cloud Discovery. En este informe se proporciona información general sobre el uso de shadow IT que se ha identificado en la organización. Para ello, se resaltan las aplicaciones y los usuarios principales en uso en general y en las categorías principales, y se hace hincapié en el riesgo que shadow IT supone en la organización. Además, el informe proporciona una lista de recomendaciones sobre cómo mejorar la visibilidad y el control de shadow IT en la organización. Use este informe para asegurarse de eliminar los posibles riesgos y amenazas, y que la organización siga siendo segura.

-   **Detección de malware**<br>La funcionalidad de detección de malware se está implantando de forma gradual para **detectar automáticamente los archivos maliciosos en el almacenamiento en la nube**, con independencia del tipo de archivo. Microsoft Cloud App Security usa la inteligencia sobre amenazas de Microsoft para reconocer si determinados archivos están asociados a ataques de malware conocidos o son potencialmente maliciosos. Para obtener más información, vea [Directivas de detección de anomalías](anomaly-detection-policy.md).
 
-   **Corrección automatizada de actividades sospechosas**<br>Ahora puede establecer acciones de corrección automática para una sesión sospechosa desencadenadas por las directivas de detección de anomalías. Gracias a esta mejora, se le avisará al instante cuando se produzca una infracción y **se aplicarán automáticamente las acciones de gobierno**, por ejemplo, la suspensión del usuario. Para obtener más información, vea [Directivas de detección de anomalías](anomaly-detection-policy.md#adp-automated-gov). 
 
-   **Evaluación de la configuración de seguridad para Azure**<br>Microsoft Cloud App Security está implementando de forma gradual la funcionalidad de obtener una evaluación de la configuración de seguridad del entorno de Azure, y proporciona recomendaciones para el control de la seguridad y los valores de configuración que falten. Por ejemplo, le permitirá saber si falta MFA para los usuarios administrativos. Para obtener más información, vea [Cloud Security Posture Management integration](security-config.md) (Integración de la administración de posiciones de seguridad en la nube).  
  
-   **Detección automática de aplicaciones OAuth peligrosas**<br>Además de la investigación existente de aplicaciones de OAuth conectadas al entorno, ahora Microsoft Cloud App Security está implementando de forma gradual la funcionalidad para establecer notificaciones automatizadas que avisen cuando una aplicación de OAuth cumple determinados criterios. Por ejemplo, puede recibir alertas automáticamente cuando haya aplicaciones que requieran un alto nivel de permisos y las hayan autorizado más de 50 usuarios. Para obtener más información, vea [Directivas de permisos de la aplicación](app-permission-policy.md).
 
-   **Compatibilidad con la administración de proveedores de servicios de seguridad administrada (MSSP)**<br>Microsoft Cloud App Security ahora proporciona una mejor experiencia de administración para MSSP. Ahora es posible configurar a usuarios externos como administradores y asignarles cualquiera de los [roles disponibles actualmente en Microsoft Cloud App Security](manage-admins.md). Además, para permitir que los MSSP proporcionen servicios en varios inquilinos de clientes, los administradores que tienen derechos de acceso a más de un inquilino ahora pueden cambiar de inquilino fácilmente en el portal. Para información sobre cómo administrar los administradores, vea [Administración de los administradores](manage-admins.md).
  
-   **Disponibilidad general de la integración con DLP externa**<br>Microsoft Cloud App Security permite [aprovechar las inversiones existentes en sistemas de clasificación de terceros](icap-stunnel.md), como soluciones de prevención de pérdida de datos (DLP), y permite examinar el contenido de aplicaciones en la nube mediante las implementaciones que se ejecutan en el entorno. Para obtener más información, vea [Integración de DLP externa](icap-stunnel.md).


## <a name="cloud-app-security-release-125"></a>Notas de la versión 125 de Cloud App Security

Publicado el 10 de junio de 2018


- **Nueva funcionalidad de investigación de los usuarios principales:**<br>
Microsoft Cloud App Security agregó un nuevo widget de investigación al panel donde aparecen los usuarios principales según el número de alertas de detección de amenazas abiertas. Este widget de investigación le permite centrar su investigación de amenazas en aquellos usuarios que cuentan con el mayor número de sesiones sospechosas.

- **Compatibilidad con los cubos de AWS S3:**<br>
Microsoft Cloud App Security puede detectar ahora cubos de AWS S3 y sus niveles de uso compartido. Esto proporciona alertas y visibilidad en cubos de AWS accesibles públicamente. También permite crear directivas basadas en cubos y aplicar la regulación automática. Además, hay una nueva plantilla de directiva disponible llamada **Publicly accessible S3 buckets (AWS)** (Cubos de S3 accesibles públicamente (AWS)) que puede usar para crear fácilmente una directiva que regule su almacenamiento de AWS. Para habilitar estas nuevas funcionalidades, asegúrese de actualizar sus aplicaciones conectadas mediante AWS agregando los nuevos permisos descritos en [Conectar AWS](connect-aws-to-microsoft-cloud-app-security.md).

- **Privilegios de administración basados en grupos de usuarios:** ahora puede establecer los permisos administrativos de los administradores de Microsoft Cloud App Security por cada grupo de usuarios. Por ejemplo, puede establecer un usuario concreto como administrador de únicamente los usuarios de Alemania. Esto permitiría al usuario ver y modificar la información en Microsoft Cloud App Security relativa únicamente al grupo de usuarios "Alemania: todos los usuarios". Para más información, vea [Administración del acceso de administrador](manage-admins.md).


## <a name="cloud-app-security-release-124"></a>Notas de la versión 124 de Cloud App Security

Fecha de publicación: 27 de mayo de 2018

-   **Se agregó la evaluación del riesgo del RGPD al catálogo de aplicaciones en la nube**<br>
Se agregaron 13 nuevos factores de riesgo a Microsoft Cloud App Security. Estos factores de riesgo siguen la lista de comprobación del marco del RGPD para que pueda evaluar las aplicaciones del catálogo de aplicaciones en la nube según la normativa del RGPD.

-   **Integración con el servicio de clasificación de datos de Microsoft**<br>
Microsoft Cloud App Security ahora le permite utilizar el servicio de clasificación de datos de Microsoft de forma nativa, para clasificar los archivos de las aplicaciones en la nube. <br>
El servicio de clasificación de datos de Microsoft proporciona una experiencia de protección de información unificada en Office 365, Azure Information Protection y Microsoft Cloud App Security. Permite llevar el mismo marco de trabajo de clasificación de datos a las aplicaciones en la nube de terceros que están protegidas por Microsoft Cloud App Security, aprovechando las decisiones ya adoptadas en un número mayor de aplicaciones. 

-   **Conexión a Microsoft Azure** (implantación gradual)<br>
Microsoft Cloud App Security está ampliando sus capacidades de supervisión de IaaS más allá de Amazon Web Services y ahora es compatible con Microsoft Azure. Esto le permite conectarse y supervisar de manera fluida todas las suscripciones de Azure con Cloud App Security. Esta conexión le ofrece un conjunto eficaz de herramientas para proteger el entorno de Azure, como las siguientes: 

       -    Visibilidad en todas las actividades realizadas a través del portal

       -    Posibilidad de crear directivas personalizadas para alertar sobre comportamientos no deseados, así como la posibilidad de protegerse automáticamente ante usuarios de riesgo mediante la suspensión o la exigencia de que vuelvan a iniciar sesión.

       -    Todas las actividades de Azure están cubiertas por el motor de detección de anomalías, que generará una alerta automáticamente ante cualquier comportamiento sospechoso en Azure Portal, como un viaje imposible, actividades sospechosas masivas y la actividad desde un nuevo país.<br>

  Para obtener más información, vea [Conectar Azure con Microsoft Cloud App Security](connect-azure-to-microsoft-cloud-app-security.md).
 
-   **Implementaciones con ámbito** (lanzamiento gradual) <br>
Microsoft Cloud App Security ofrece a las empresas la capacidad de determinar de forma detallada los usuarios que quieren supervisar y proteger en función de la pertenencia a grupos. Esta característica permite seleccionar usuarios cuyas actividades no se mostrarán para ninguna de las aplicaciones protegidas. La función de supervisión con ámbito es especialmente útil en los siguientes aspectos: 

    -   Cumplimiento normativo: si debe abstenerse de supervisar a los usuarios de determinados países debido a la normativa local.

       -    Licencias: si desea supervisar menos usuarios para permanecer dentro de los límites de las licencias de Microsoft Cloud App Security.
   Para obtener más información, consulte [Scoped deployment](scoped-deployment.md) (Implementación con ámbito).

-   **Alerta de aplicación infringida para aplicaciones detectadas**<br>
 Ahora hemos integrado una alerta para notificarle cuando alguna de las aplicaciones detectadas de un inquilino se infringe. La alerta proporcionará información acerca de la fecha y hora de la infracción y los usuarios que usaron la aplicación, y se vinculará a los orígenes disponibles públicamente que proporcionan información acerca de la infracción.

-   **Nuevo servidor de correo**<br>
 El servidor de correo de Cloud App Security ha cambiado y utiliza distintos intervalos de direcciones IP. Para asegurarse de que puede recibir notificaciones, agregue las nuevas direcciones IP a la lista blanca de direcciones de correo no deseado. Para los usuarios que personalizan sus notificaciones, Microsoft Cloud App Security lo hace posible mediante MailChimp®, un servicio de correo electrónico de terceros. Para obtener la lista de direcciones IP de servidor de correo electrónico e instrucciones para habilitar el trabajo con MailChimp, consulte [Requisitos de red](https://docs.microsoft.com/cloud-app-security/network-requirements#email-server) y [Establecimiento de preferencias de notificación de correo electrónico](mail-settings.md).


## <a name="cloud-app-security-release-123"></a>Cloud App Security versión 123

Fecha de publicación: 13 de mayo de 2018

- **Ámbito de la directiva de detección de anomalías**:<br>
Ahora se puede establecer un ámbito para las directivas de detección de anomalías. Esto le permite establecer cada directiva de detección de anomalías para incluir solo determinados usuarios o grupos y para excluir usuarios o grupos específicos. Por ejemplo, puede establecer la actividad desde la detección de condado poco frecuente hasta omitir un usuario específico que viaja con frecuencia. 


## <a name="cloud-app-security-release-122"></a>Notas de la versión 122 de Cloud App Security
Fecha de publicación: 29 de abril de 2018

-   Implementación gradual: ahora puede **establecer los permisos administrativos de los administradores de Microsoft Cloud App Security por cada aplicación**. Por ejemplo, puede establecer un usuario concreto como administrador de únicamente G Suite. Esto permitiría al usuario ver y modificar la información en Microsoft Cloud App Security relativa únicamente a G Suite. Para más información, vea [Administración del acceso de administrador](manage-admins.md).
- Implementación gradual: **ahora, los roles de administrador de Okta aparecen** en Microsoft Cloud App Security y están disponibles para cada rol como una etiqueta en **Configuración** > **Grupos de usuarios**.


## <a name="cloud-app-security-release-121"></a>Notas de la versión 121 de Cloud App Security
Fecha de publicación: 22 de abril de 2018

-   La versión preliminar pública de **Conditional Access App Control (anteriormente denominado proxy de Cloud App Security)** se ha mejorado con funcionalidades que facilitan mayor visibilidad y control de las distintas aplicaciones. Ahora puede crear una directiva de sesión con un filtro *Tipo de actividad* para supervisar y bloquear diversas actividades específicas de la aplicación. Este nuevo filtro, que funciona conjuntamente con el acceso condicional de Azure Active Directory, aumenta las características de control de descarga de archivos existentes para proporcionarle control completo de las aplicaciones de su organización para ofrecer visibilidad en tiempo real y control de sesiones de usuario de riesgo: por ejemplo, las sesiones con usuarios de colaboración B2B o procedentes de un dispositivo no administrado. Para obtener más información, consulte [Directivas de sesión](session-policy-aad.md).
-   Despliegue gradual: **se han mejorado las directivas de detección de anomalías** de Cloud App Security para incluir dos nuevos tipos de detección de amenazas: Actividad de ransomware y Actividad del usuario cancelado. Cloud App Security ha ampliado sus funcionalidades de detección de ransomware con la detección de anomalías para garantizar una cobertura más completa frente a ataques de ransomware sofisticados. Con nuestra experiencia en investigación de seguridad para identificar patrones de comportamiento que reflejan la actividad de ransomware, Cloud App Security garantiza una protección integral y sólida. Actividad del usuario cancelado le permite supervisar las cuentas de usuarios cancelados, que es posible que se hayan desaprovisionado de aplicaciones corporativas, pero en muchos casos todavía conservan el acceso a ciertos recursos corporativos. Para obtener más información, vea [Obtención de análisis de comportamiento y detección de anomalías instantáneos](anomaly-detection-policy.md).


## <a name="cloud-app-security-release-120"></a>Notas de la versión 120 de Cloud App Security
Publicada el 8 de abril de 2018

-   Para Office 365 y Azure AD, implementaremos de forma gradual la posibilidad de identificar las aplicaciones internas como actividades de cuenta de usuario llevadas a cabo por las aplicaciones de Office 365 y Azure AD (tanto internas como externas). Ello le permite crear directivas que le enviarán una alerta si una aplicación realiza actividades inesperadas y no autorizadas. 
-   Al exportar la lista de permisos de una aplicación a un archivo .csv, los campos adicionales, como el anunciante, el nivel de permisos y el uso de la comunidad, se incluyen para asistir durante el proceso de investigación y cumplimiento.
-   La aplicación conectada ServiceNow se ha mejorado para que las actividades de servicio internas dejen de registrarse como si las hubiese llevado a cabo un invitado y dejen de activar alertas de falsos positivos. Ahora, dichas actividades constan como N/A, igual que el resto de las aplicaciones conectadas.


## <a name="cloud-app-security-release-119"></a>Notas de la versión 119 de Cloud App Security
Fecha de publicación: 18 de marzo de 2018

-   En la página de intervalos de direcciones IP se incluyen las direcciones IP integradas que ha detectado Cloud App Security. Esto incluye direcciones IP para los servicios en la nube identificados, como Azure y Office 365, así como la fuente de Inteligencia sobre amenazas que agrega automáticamente direcciones IP con información acerca de las direcciones IP peligrosas conocidas. 
-   Cuando Cloud App Security intenta ejecutar una acción de gobierno en un archivo, pero se produce un error porque el archivo está bloqueado, ahora se reintentará automáticamente la acción de gobierno. 

## <a name="cloud-app-security-release-118"></a>Cloud App Security versión 118
Fecha de publicación: 4 de marzo de 2018

- Ahora puede aprovechar las funcionalidades de detección y supervisión de Shadow IT de Microsoft Cloud App Security en sus propias aplicaciones personalizadas exclusivas. La nueva posibilidad de agregar aplicaciones personalizadas a Cloud Discovery permite supervisar el uso de la aplicación y recibir alertas sobre cambios en el patrón de uso. Para obtener más información, consulte [Protecting your custom apps](cloud-discovery-custom-apps.md) (Protección de las aplicaciones personalizadas). Esta característica se está implantando gradualmente.

- Las páginas de **configuración** del portal de Cloud App Security se han rediseñado. El nuevo diseño consolida todas las páginas de configuración, proporciona la funcionalidad de búsqueda y un mejor diseño. 

- Cloud Discovery admite ahora Barracuda F-Series Firewalls y Barracuda F-Series Firewall Web Log Streaming.

- La funcionalidad de búsqueda en las páginas de dirección IP y de usuario habilita ahora Autocompletar para que le resulte más fácil encontrar lo que busca.

- Ahora puede realizar acciones en masa en las páginas de configuración de exclusión de entidades y de exclusión de direcciones IP. Esto hace que le resulte más fácil seleccionar varios usuarios y grupos o direcciones IP y excluirlos de la supervisión como parte de Cloud Discovery en su organización. 

## <a name="cloud-app-security-release-117"></a>Cloud App Security versión 117
Fecha de publicación: 20 de febrero de 2018

-   La mayor integración de Cloud App Security con Azure Information Protection permite ahora proteger archivos de G Suite. Esta característica de versión preliminar pública permite examinar y clasificar archivos de G Suite y aplicar automáticamente etiquetas de protección de Azure Information Protection para protegerlos. Para obtener más información, consulte [Integración de Azure Information Protection](azip-integration.md).

-   Cloud Discovery admite ahora [Digital Arts i-FILTER](http://www.daj.jp/en/products/if/).

-   La tabla Agentes SIEM incluye ahora más detalles que facilitan la administración.

## <a name="cloud-app-security-release-116"></a>Cloud App Security versión 116
Publicado el 4 de febrero de 2018
- La directiva de detección de anomalías de Cloud App Security se ha mejorado con nuevas **detecciones basadas en escenarios** entre las que se incluyen viaje imposible, actividad desde una dirección IP sospechosa y varios intentos incorrectos de inicio de sesión. Las nuevas directivas se habilitan automáticamente, lo que proporciona la detección de amenazas desde el primer momento en todo el entorno de nube. Además, las nuevas directivas exponen más datos a partir del motor de detección de Cloud App Security, lo que le ayuda a agilizar el proceso de investigación y contener las amenazas en curso. Para obtener más información, vea [Obtención de análisis de comportamiento y detección de anomalías instantáneos](https://docs.microsoft.com/en-us/cloud-app-security/anomaly-detection-policy).

- Despliegue gradual: Cloud App Security ahora se pone en correlación entre los usuarios y sus cuentas en aplicaciones de SaaS. Esto le permite investigar fácilmente todas las actividades de los usuarios, en todas sus diferentes aplicaciones de SaaS correlacionadas, con independencia de qué aplicación o cuenta utilizan.  

-   Despliegue gradual: Cloud App Security ahora admite varias instancias de la misma aplicación conectada. Si tiene varias instancias de, por ejemplo, Salesforce (una para venta y otra para marketing) podrá conectarlas a Cloud App Security y administrarlas desde la misma consola para crear directivas granulares y una investigación más a fondo. 

- Los analizadores de Cloud Discovery ahora admiten dos formatos adicionales de punto de control: XML y KPC.



## <a name="cloud-app-security-release-115"></a>Notas de la versión 115 de Cloud App Security
Fecha de publicación: 21 de enero de 2018

- En esta versión se proporciona una experiencia mejorada al seleccionar carpetas específicas en las directivas de archivo. Ahora puede ver y seleccionar fácilmente varias carpetas para incluirlas en una directiva. 
- En la página **Aplicaciones detectadas**: 
  - La característica de etiquetado masivo le permite aplicar etiquetas personalizadas (además de etiquetas autorizadas y no autorizadas). 
  - Cuando se **genera un informe de direcciones IP** o se **genera un informe de usuarios**, los informes exportados ahora incluyen la información sobre si el tráfico provenía de aplicaciones autorizadas o no autorizadas. 
- Ahora puede solicitar un nuevo conector de aplicación de API del equipo de Microsoft Cloud App Security directamente en el portal, desde la página **Conectar una aplicación**. 


## <a name="cloud-app-security-release-114"></a>Notas de la versión 114 de Cloud App Security
Fecha de publicación: 7 de enero de 2018

- A partir de la versión 114, estamos implementando de forma gradual la capacidad de crear y guardar las consultas personalizadas en las páginas Registro de actividad y Aplicaciones detectadas. Las consultas personalizadas le permiten crear plantillas de filtro que se pueden volver a usar para investigar en profundidad. Además, se han agregado **consultas sugeridas** para proporcionar plantillas de investigación predeterminadas para filtrar las actividades y aplicaciones detectadas. Las **consultas sugeridas** incluyen filtros personalizados para identificar los riesgos, como las actividades de suplantación, las actividades de administrador, las aplicaciones de almacenamiento en la nube no conformes que implican un riesgo, las aplicaciones empresariales con cifrado débil y los riesgos de seguridad. Puede usar las **consultas sugeridas** como punto de partida, modificarlas según considere y después guardarlas como una nueva consulta. Para obtener más información, consulte [Filtros y consultas de actividad](activity-filters-queries.md) y [Filtros y consultas de aplicaciones detectadas](discovered-app-queries.md).
 
- Ahora puede comprobar el estado actual del servicio de Cloud App Security si va a [status.cloudappsecurity.com](https://status.cloudappsecurity.com) o directamente desde el portal al hacer clic en **Ayuda**>**Estado del sistema**. 
 


## <a name="see-also"></a>Consulte también  

Para obtener una descripción de las versiones anteriores a las mencionadas aquí, consulte [Past releases of Microsoft Cloud App Security](release-note-archive.md) (Versiones anteriores de Microsoft Cloud App Security).

[Los clientes Premier también pueden elegir Cloud App Security directamente desde el Portal Premier.](https://premier.microsoft.com/)  
  
  