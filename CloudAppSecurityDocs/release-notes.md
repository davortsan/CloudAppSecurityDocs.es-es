---
title: Novedades de Cloud App Security
description: Este artículo se actualiza con frecuencia para informarle de las novedades de la versión más reciente de Cloud App Security.
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 09/13/2020
ms.topic: overview
ms.service: cloud-app-security
ms.collection: M365-security-compliance
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: faf7d4fcfbdf37d7a38d155deb65aa2693e846af
ms.sourcegitcommit: 5367d8fdf99d61719a395728f2ef4b014604e3bc
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/08/2020
ms.locfileid: "94371278"
---
# <a name="whats-new-with-microsoft-cloud-app-security"></a>Novedades de Microsoft Cloud App Security

*Se aplica a: Microsoft Cloud App Security*

Este artículo se actualiza con frecuencia para informarle de las novedades de la versión más reciente de Cloud App Security.

Fuente RSS: reciba notificaciones cuando esta página se actualice copiando y pegando la siguiente dirección URL en su lector de fuentes: `https://docs.microsoft.com/api/search/rss?search=%22This+article+is+updated+frequently+to+let+you+know+what%27s+new+in+the+latest+release+of+Cloud+App+Security%22&locale=en-us`

> [!IMPORTANT]
>
> Los nombres de productos de protección contra amenazas de Microsoft están cambiando. Obtenga más información sobre esta y otras actualizaciones [en este artículo](https://www.microsoft.com/security/blog/?p=91813). Usaremos los nombres nuevos en futuras versiones.

## <a name="cloud-app-security-release-184-185-and-186"></a>Versiones 184, 185 y 186 de Cloud App Security

Fecha de publicación: 25 de octubre de 2020

- **Nueva experiencia mejorada de supervisión y administración de alertas**  
Como parte de las mejoras continuas en la supervisión y la administración de alertas, la página de alertas de Cloud App Security se ha mejorado en función de sus comentarios. En la experiencia mejorada, los estados **Resuelta** y **Descartada** se sustituyen por el estado **Cerrada** con un tipo de resolución. [Más información](monitor-alerts.md#deployment-of-our-enhanced-alert-monitoring-and-management-experience)

- **Nueva configuración de gravedad global para señales enviadas a Microsoft Defender for Endpoint**  
Se ha agregado la posibilidad de establecer la configuración de gravedad global para las señales enviadas a Microsoft Defender for Endpoint. Para más información, consulte [Integración de Microsoft Defender for Endpoint con Cloud App Security](mde-integration.md#how-to-integrate-microsoft-defender-for-endpoint-with-cloud-app-security).

- **Nuevo informe de recomendaciones de seguridad**  
Cloud App Security ofrece valoraciones de la configuración de seguridad de Azure, Amazon Web Services (AWS) y Google Cloud Platform (GCP) que le proporcionan información sobre las deficiencias de dicha configuración en el entorno de varias nubes. Ahora, puede exportar informes detallados de recomendaciones de seguridad para que le ayuden a supervisar, comprender y personalizar los entornos de nube a fin de proteger mejor su organización. Para más información sobre cómo exportar el informe, consulte [Informe de recomendaciones de seguridad](security-config.md#security-recommendations-report).

- **Sufijo URL de proxy mejorado para controles de sesión (lanzamiento gradual)**  
El 7 de junio de 2020 se ha iniciado el lanzamiento gradual de los controles de sesión de proxy mejorados para usar un sufijo unificado que no incluye regiones con nombre. Por ejemplo, los usuarios verán el sufijo `<AppName>.mcas.ms` en lugar de `<AppName>.<Region>.cas.ms`. Si, por rutina, bloquea los dominios de las puertas de enlace o los dispositivos de red, asegúrese de crear una lista de permitidos con todos los dominios enumerados en [Controles de acceso y sesión](network-requirements.md#access-and-session-controls).

- **Actualizaciones del catálogo de aplicaciones en la nube**  
Se han realizado las siguientes actualizaciones en el catálogo de aplicaciones en la nube:

  - El centro de administración de Teams se ha actualizado como una aplicación independiente.
  - El nombre del centro de administración de Microsoft Office 365 se ha cambiado por Portal de Office.

- **Actualización terminológica**  
Como parte del esfuerzo general de Microsoft por alinear la terminología entre los productos, se ha actualizado el término **máquina** a **dispositivo**.

## <a name="cloud-app-security-release-182-and-183"></a>Notas de las versiones 182 y 183 de Cloud App Security

Fecha de publicación: 6 de septiembre de 2020

- **Controles de acceso y sesión para Azure Portal (GA)**  
El control de aplicaciones de acceso condicional para Azure Portal ya está disponible de forma general. Para obtener información sobre la configuración de estos controles, vea la [guía de implementación](proxy-deployment-aad.md).

## <a name="cloud-app-security-release-181"></a>Versión 181 de Cloud App Security

Fecha de publicación: 9 de agosto de 2020

- **Nuevo analizador de registros de Menlo Security de Cloud Discovery**  
Cloud Discovery de Cloud App Security analiza una amplia gama de registros de tráfico para clasificar y puntuar aplicaciones. Ahora Cloud Discovery incluye un analizador de registros integrado para admitir el formato CEF de Menlo Security. Para ver una lista de los analizadores de registros admitidos, vea [Firewalls y proxies admitidos](set-up-cloud-discovery.md#supported-firewalls-and-proxies).

- **En el portal se muestra el nombre Azure Active Directory (AD) Cloud App Discovery**  
Hemos actualizado el nombre del producto a **Cloud App Discovery** para las licencias P1 y P2 de Azure AD en el portal. Más información sobre [Cloud App Discovery](editions-cloud-app-security-aad.md)

## <a name="cloud-app-security-release-179-and-180"></a>Notas de la versión 179 y 180 de Cloud App Security

Fecha de publicación: 26 de julio de 2020

- **Nueva detección de anomalías: Actividades sospechosas de descarga de archivos en aplicaciones de OAuth**  
Hemos ampliado las detecciones de anomalías para incluir las actividades de descarga sospechosas en aplicaciones de OAuth. La nueva detección ya está disponible para su uso y se habilita automáticamente para avisarle cuando una aplicación de OAuth descarga varios archivos de Microsoft SharePoint o Microsoft OneDrive de forma inusual para el usuario.

- **Mejoras de rendimiento de los controles de sesión mediante almacenamiento en caché de proxy (implementación gradual)**  
Hemos realizado mejoras de rendimiento adicionales en los controles de sesión al perfeccionar nuestros mecanismos de almacenamiento en caché de contenido. El servicio mejorado está todavía más optimizado y proporciona una mayor capacidad de respuesta cuando se usan controles de sesión. Tenga en cuenta que los controles de sesión no almacenan en caché el contenido privado y se alinean con los estándares adecuados para almacenar en caché solo el contenido compartido (público). Para obtener más información, vea [Funcionamiento del control de sesión](proxy-intro-aad.md#how-session-control-works).

- **Nueva característica: Guardado de las consultas de configuración de seguridad**  
Hemos agregado la capacidad de guardar las consultas para los filtros del panel de configuración de seguridad de Azure, Amazon Web Services (AWS) y Google Cloud Platform (GCP). Esto puede ayudar a simplificar aún más las investigaciones futuras mediante la reutilización de consultas comunes. Obtenga más información sobre nuestras [recomendaciones para la configuración de seguridad](security-config.md).

- **Alertas de detección de anomalías mejoradas**  
Hemos ampliado la información que se proporciona en las alertas de detección de anomalías con el fin de incluir una asignación a la táctica de MITRE ATT\&CK correspondiente. Esta asignación le permitirá conocer la fase y el impacto del ataque y le ayudará con sus investigaciones. Obtenga más información sobre [cómo investigar alertas de detección de anomalías](investigate-anomaly-alerts.md).

- **Lógica de detección mejorada: Actividad de ransomware**  
Hemos actualizado la lógica de detección de actividades de ransomware con el fin de mejorar la precisión y reducir el volumen de alertas. Para obtener más información acerca de esta directiva de detección de anomalías, consulte la sección [Actividad de ransomware](anomaly-detection-policy.md#ransomware-activity).

- **Informes de la posición de seguridad de las identidades: Visibilidad de las etiquetas**  
Hemos agregado etiquetas de entidad a los informes de la posición de seguridad de las identidades que proporcionan información adicional de las entidades. Por ejemplo, la etiqueta **Confidencial** puede ayudarle a identificar a los usuarios de riesgo y a priorizar sus investigaciones. Obtenga más información sobre la [investigación de usuarios de riesgo](tutorial-ueba.md).

## <a name="cloud-app-security-release-178"></a>Versión 178 de Cloud App Security

Fecha de publicación: 28 de junio de 2020

- **Nuevas configuraciones de seguridad para Google Cloud Platform (lanzamiento gradual)**  
Hemos ampliado nuestras configuraciones de seguridad multinube a fin de proporcionar recomendaciones de seguridad para Google Cloud Platform según el banco de pruebas de CIS de GCP. Con esta nueva capacidad, Cloud App Security ofrece a las organizaciones una vista única para supervisar el estado de cumplimiento en todas las plataformas en la nube. Esto incluye las [suscripciones de Azure ](security-config-azure.md), las [cuentas de AWS](security-config-aws.md) y, más recientemente, los [proyectos de GCP](security-config-gcp.md).

- **Disponibilidad general de nuevos conectores de aplicaciones**  
Hemos agregado los conectores de aplicaciones siguientes a nuestra gama de conectores de API con disponibilidad general, lo que le ofrece más visibilidad y control sobre cómo se usan las aplicaciones en una organización:
  - [Nube de GitHub Enterprise](protect-github.md)
  - [Google Cloud Platform](protect-gcp.md)
  - [Workday](protect-workday.md)

- **Disponibilidad general de la nueva detección de malware en tiempo real**  
Hemos ampliado los controles de sesión para detectar malware potencial con la inteligencia sobre amenazas de Microsoft al cargar o descargar archivos. La nueva detección ya tiene disponibilidad general de serie y se puede configurar para que bloquee automáticamente los archivos identificados como posible malware. Para obtener más información, vea [Bloquear malware al cargar](session-policy-aad.md#block-malware-on-upload).

- **Disponibilidad general de los controles de acceso y de sesión mejorados con cualquier IdP**  
La compatibilidad de los controles de acceso y de sesión con aplicaciones SAML configuradas con cualquier proveedor de identidades ya está disponible de manera general. Para obtener información sobre la configuración de estos controles, vea la [guía de implementación](proxy-deployment-aad.md).

- **Mejora de la investigación de máquinas de riesgo**  
Cloud App Security proporciona la capacidad de identificar máquinas de riesgo como parte de la investigación de detección de TI en la sombra. Ahora, hemos agregado el **nivel de máquinas de riesgo** de la Protección contra amenazas avanzada de Microsoft Defender en la página de **máquinas** , lo que aportará más contexto a los analistas que investiguen las máquinas de su organización. Para más información, consulte [Investigación de dispositivos de Cloud App Security](mde-integration.md#investigate-devices-in-cloud-app-security).

- **Nueva característica: Autoservicio para la deshabilitación de conectores de aplicaciones (lanzamiento gradual)**  
Hemos agregado la capacidad de deshabilitar los conectores de aplicaciones directamente en Cloud App Security. Para obtener más información, consulte [Deshabilitación de conectores de aplicaciones](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md#disable-app-connectors).

## <a name="cloud-app-security-release-177"></a>Notas de la versión 177 de Cloud App Security

Fecha de publicación: 14 de junio de 2020

- **Nueva detección de malware en tiempo real (versión preliminar, lanzamiento gradual)**  
Hemos ampliado los controles de sesión para detectar malware potencial con la inteligencia sobre amenazas de Microsoft al cargar o descargar archivos. La nueva detección ya está disponible de serie y se puede configurar para que bloquee automáticamente los archivos identificados como posible malware. Para obtener más información, vea [Bloquear malware al cargar](session-policy-aad.md#block-malware-on-upload).

- **Nueva compatibilidad de los tokens de acceso con los controles de acceso y de sesión**  
Se ha agregado la posibilidad de tratar las solicitudes de tokens de acceso y código como inicios de sesión al incorporar aplicaciones a los controles de acceso y de sesión. Para usar tokens, haga clic en el icono de engranaje de configuración, seleccione **Control de aplicaciones de acceso condicional** , edite la aplicación correspondiente (menú de tres puntos > **Editar aplicación** ), seleccione **Tratar solicitudes de código y tokens de acceso como inicios de sesión de la aplicación** y haga clic en **Guardar**. Para obtener más información sobre la incorporación de aplicaciones, vea [Incorporación e implementación para cualquier aplicación](proxy-deployment-any-app.md) e [Implementación para aplicaciones destacadas](proxy-deployment-aad.md).

- **Sufijo URL de proxy mejorado para controles de sesión (lanzamiento gradual)**  
El 7 de junio de 2020 se ha iniciado el lanzamiento gradual de los controles de sesión de proxy mejorados para usar un sufijo unificado que no incluye regiones con nombre. Por ejemplo, los usuarios verán el sufijo `<AppName>.mcas.ms` en lugar de `<AppName>.<Region>.cas.ms`. Si, por rutina, bloquea los dominios de las puertas de enlace o los dispositivos de red, asegúrese de crear una lista de permitidos con todos los dominios enumerados en [Controles de acceso y sesión](network-requirements.md#access-and-session-controls).

- **Nueva documentación**  
La documentación de Cloud App Security se ha ampliado para incluir el siguiente contenido nuevo:

  - **[Uso de las API de REST de Cloud App Security](api-introduction.md)** : obtenga información sobre las capacidades de API e inicie la integración de las aplicaciones con Cloud App Security.
  - **[Investigación de alertas de detección de anomalías](investigate-anomaly-alerts.md)** : familiarícese con las alertas de UEBA disponibles, lo que significan, identifique el riesgo que suponen, comprenda el ámbito de una infracción y la acción que puede llevar a cabo para remediar la situación.

## <a name="cloud-app-security-release-176"></a>Notas de la versión 176 de Cloud App Security

Fecha de publicación: 31 de mayo de 2020

- **Nueva característica de privacidad de las actividades**  
Se ha mejorado la capacidad de determinar con minuciosidad qué usuarios desea supervisar con la posibilidad de convertir las actividades en privadas. Esta nueva característica permite especificar usuarios en función de la pertenencia a grupos, cuyas actividades se ocultarán de forma predeterminada. Solo los administradores autorizados tienen la opción de elegir la opción de ver estas actividades privadas, con la auditoría de cada instancia en el registro de gobernanza. Para más información, vea [Privacidad de la actividad](activity-privacy.md).

- **Nueva integración con la galería de Azure Active Directory (Azure AD)**  
Se recurre a la integración nativa con Azure AD para ofrecer la posibilidad de navegar directamente desde una aplicación del catálogo de aplicaciones en la nube hasta su aplicación correspondiente de la galería de Azure AD, para poder administrarla en la galería. Para más información, vea [Administración de aplicaciones con la galería de Azure AD](tutorial-shadow-it.md#gallery-apps).

- **Nueva opción de comentarios disponible en las directivas seleccionadas**  
Nos interesa recibir sus comentarios para saber cómo podemos ayudarle. Por ello, ahora un nuevo cuadro de diálogo de comentarios le ofrece la oportunidad de mejorar Cloud App Security, al crear, modificar o eliminar un archivo, una detección de anomalías o una directiva de sesión.

- **Sufijo URL de proxy mejorado para controles de sesión (lanzamiento gradual)**  
A partir del 7 de junio de 2020, se implementarán gradualmente los controles de sesión de proxy mejorado para usar un sufijo unificado que no incluye regiones con nombre. Por ejemplo, los usuarios verán el sufijo `<AppName>.mcas.ms` en lugar de `<AppName>.<Region>.cas.ms`. Si, por rutina, crea listas negras de dominios en las puertas de enlace o los dispositivos de red, asegúrese de crear una lista blanca de todos los dominios enumerados en [Controles de acceso y sesión](network-requirements.md#access-and-session-controls).

- **Mejoras de rendimiento de los controles de sesión (implementación gradual)**  
Se han introducido mejoras significativas en el rendimiento de la red para el servicio de proxy. El servicio mejorado está todavía más optimizado y proporciona una mayor capacidad de respuesta cuando se usan controles de sesión.

- **Nueva detección de actividad de riesgo: inicio de sesión inusual con errores**  
Hemos ampliado la funcionalidad actual para detectar un comportamiento de riesgo. La nueva detección ya está disponible para su uso y se habilita automáticamente para avisarle cuando se identifica un intento de inicio de sesión inusual con errores. Los intentos inusuales de inicio de sesión con errores pueden ser un indicio de un posible ataque por fuerza bruta de *rociado de contraseñas* (también conocido como el método *lento y silencioso* ). Esta detección afecta a la [clasificación de prioridad de la investigación](tutorial-ueba.md) general del usuario.

- **Experiencia de tabla mejorada**  
Se ha agregado la capacidad de cambiar el tamaño de los anchos de las columnas de la tabla de modo que pueda ampliar o reducir las columnas para personalizar y mejorar la manera de verlas. También tiene la opción de restaurar el diseño original seleccionando el menú de configuración de la tabla y eligiendo **Ancho predeterminado**.

## <a name="cloud-app-security-release-175"></a>Cloud App Security, versión 175

Fecha de publicación: 17 de mayo de 2020

- **Nueva integración de Shadow IT Discovery con Corrata (versión preliminar)**  
Hemos agregado integración nativa con Corrata, lo que ofrece visibilidad de TI en la sombra sobre el uso de las aplicaciones y control de acceso a estas. Para obtener más información, consulte [Integración de Cloud App Security con Corrata](corrata-integration.md).

- **Nuevos analizadores de registro de Cloud Discovery**  
Cloud Discovery de Cloud App Security analiza una amplia gama de registros de tráfico para clasificar y puntuar aplicaciones. Ahora Cloud Discovery incluye un analizador de registros integrado para admitir Corrata y Cisco ASA con formatos de registro de FirePOWER 6.4. Para ver una lista de los analizadores de registros admitidos, vea [Firewalls y proxies admitidos](set-up-cloud-discovery.md#supported-firewalls-and-proxies).

- **Panel mejorado (implementación gradual)** : como parte de las mejoras continuas en el diseño del portal, implementaremos el panel de Cloud App Security mejorado gradualmente. El panel se ha modernizado atendiendo a los comentarios de los usuarios y ofrece una experiencia de uso mejorada con nuevos datos y contenidos. Para obtener más información, consulte [Implementación gradual de nuestro panel mejorado](daily-activities-to-protect-your-cloud-environment.md).

- **Gobernanza mejorada: confirmación de vulneración de la identidad del usuario para la detección de anomalías**  
Hemos ampliado las acciones de gobernanza. Ahora, las directivas de anomalías incluyen la opción **Confirmar vulneración de la identidad del usuario**. Esto permite proteger de forma proactiva su entorno ante actividades de usuario sospechosas. Para obtener más información, vea [Acciones de gobernanza de actividades](governance-actions.md#activity-governance-actions).

## <a name="cloud-app-security-release-173-and-174"></a>Notas de la versión 173 y 174 de Cloud App Security

Fecha de publicación: 26 de abril de 2020

- **Nuevo formato de CEF de agente de SIEM para alertas**  
Como parte de nuestro esfuerzo por enriquecer la información de alertas proporcionada en los archivos CEF que usan los servidores SIEM genéricos, hemos ampliado el formato para incluir los siguientes campos de cliente:
  - Dirección IPv4
  - Dirección IPv6
  - Ubicación de la dirección IP

    Para obtener más información, vea [Formato de archivo CEF](siem.md#sample-cloud-app-security-alerts-in-cef-format).
- **Lógica de detección mejorada: Viaje imposible**  
Hemos actualizado la lógica de detección para un viaje imposible con el fin de mejorar la precisión y reducir el volumen de alertas. Para obtener más información acerca de esta directiva de detección de anomalías, consulte [Viaje imposible](anomaly-detection-policy.md#impossible-travel).

## <a name="cloud-app-security-release-172"></a>Versión 172 de Cloud App Security

Fecha de publicación: 5 de abril de 2020

- **Controles de acceso y de sesión mejorados con cualquier IdP (versión preliminar)**  
Los controles de acceso y de sesión ahora admiten aplicaciones SAML configuradas con cualquier proveedor de identidades. La versión preliminar pública de esta nueva característica ahora se implementa gradualmente. Para configurar estos controles, consulte la [guía de desarrollo](proxy-deployment-aad.md).
- **Nueva desanonimización masiva de usuarios y máquinas**  
Hemos ampliado y simplificado el proceso de desanonimizar uno o varios usuarios y máquinas objeto de investigación. Para más información sobre la desanonimización, consulte [Cómo funciona la anonimización de datos](cloud-discovery-anonymizer.md#how-data-anonymization-works).

## <a name="cloud-app-security-release-170-and-171"></a>Notas de la versión 170 y 171 de Cloud App Security

Fecha de publicación: 22 de marzo de 2020

- **Nueva detección de anomalías: Región inusual de recurso de nube (versión preliminar)**  
Hemos ampliado nuestra funcionalidad actual para detectar un comportamiento anómalo para AWS. La nueva detección ahora está disponible de manera predeterminada y se habilita automáticamente para alertarle cuando se crea un recurso en una región de AWS en la que la actividad no se realiza normalmente. A menudo, los atacantes aprovechan los créditos de AWS de una organización para realizar actividades malintencionadas, como la minería de datos criptográficos. La detección de este comportamiento anómalo puede ayudar a mitigar un ataque.

- **Nuevas plantillas de directiva de actividad para Microsoft Teams**  
Cloud App Security ahora proporciona las siguientes nuevas plantillas de directiva de actividad que permiten detectar actividades potencialmente sospechosas en Microsoft Teams:
  - **Cambio del nivel de acceso (Teams):** Alerta cuando se cambia el nivel de acceso de un equipo de privado a público.
  - **Usuario externo agregado (Teams):** Alerta cuando se agrega un usuario externo a un equipo.
  - **Eliminación masiva (Teams):** Alerta cuando un usuario elimina un gran número de equipos.

- **Integración de Active Directory (Azure AD) Identity Protection**  
Ahora puede controlar la gravedad de las alertas de Azure AD Identity Protection que se introducen en Cloud App Security. Además, si aún no ha habilitado la detección del **inicio de sesión de riesgo de Azure AD** , la detección se habilitará automáticamente para ingerir alertas de gravedad alta. Para más información, consulte [Integración de Azure Active Directory Identity Protection](aadip-integration.md).

## <a name="cloud-app-security-release-169"></a>Notas de la versión 169 de Cloud App Security

Fecha de publicación: 1 de marzo de 2020

- **Nueva detección para WorkDay**  
Hemos ampliado nuestras alertas actuales de comportamiento anómalo para Workday. Las nuevas alertas incluyen las siguientes detecciones de ubicación geográfica de usuario:
  - [Actividad desde una dirección IP anónima](anomaly-detection-policy.md#activity-from-anonymous-ip-addresses)
  - [Actividad desde un país poco frecuente](anomaly-detection-policy.md#activity-from-infrequent-country)
  - [Actividad desde direcciones IP sospechosas](anomaly-detection-policy.md#activity-from-suspicious-ip-addresses)
  - [Viaje imposible](anomaly-detection-policy.md#impossible-travel)

- **Recopilación de registros de Salesforce mejorada**  
Cloud App Security ahora es compatible con el registro de eventos por hora de Salesforce. Los registros de eventos por hora proporcionan una supervisión acelerada casi en tiempo real de las actividades de los usuarios. Para más información, consulte [Conectar Salesforce](connect-salesforce-to-microsoft-cloud-app-security.md).

- **Compatibilidad con la configuración de seguridad de AWS mediante una cuenta maestra**  
Cloud App Security admite ahora el uso de una cuenta maestra. La conexión de su cuenta maestra le permite recibir recomendaciones de seguridad para todas las cuentas de miembro en todas las regiones. Para obtener más información sobre cómo conectarse con una cuenta maestra, consulte [Cómo conectar la configuración de seguridad de AWS a Cloud App Security](connect-aws-to-microsoft-cloud-app-security.md#how-to-connect-aws-security-configuration-to-cloud-app-security).

- **Compatibilidad de los controles de sesión con los exploradores modernos**  
Los controles de sesión de Cloud App Security ahora incluyen compatibilidad con el nuevo explorador Microsoft Edge basado en Chromium. Aunque continuaremos admitiendo las versiones más recientes de Internet Explorer y la versión heredada de Microsoft Edge, la compatibilidad será limitada y se recomienda usar el nuevo explorador Microsoft Edge.

## <a name="cloud-app-security-release-165-166-167-and-168"></a>Notas de la versión 165, 166, 167 y 168 de Cloud App Security

Publicado el 16 de febrero de 2020

- **Nuevo bloqueo de aplicaciones no autorizadas con ATP de Microsoft Defender**  
Cloud App Security ha ampliado su integración nativa con Protección contra amenazas avanzada (ATP) de Microsoft Defender. Ahora puede bloquear el acceso a las aplicaciones marcadas como no autorizadas mediante la funcionalidad de protección de red de ATP de Microsoft Defender. Para más información, consulte [Bloquear el acceso a aplicaciones no autorizadas en la nube](mde-integration.md#block-access-to-unsanctioned-cloud-apps).

- **Nuevas detecciones de anomalías de aplicaciones de OAuth**  
Hemos ampliado nuestra capacidad actual para detectar un consentimiento de aplicaciones de OAuth malintencionado. La nueva detección ahora está disponible de forma predeterminada y se habilita automáticamente para avisarle cuando una aplicación OAuth potencialmente malintencionada está autorizada en su entorno. Esta detección aprovecha la investigación de seguridad de Microsoft y la experiencia con la inteligencia sobre amenazas para identificar aplicaciones malintencionadas.

- **Actualizaciones del recopilador de registros**  
El recopilador de registros basado en Docker se ha mejorado con las siguientes actualizaciones importantes:

  - Actualización de la versión del sistema operativo del contenedor

  - Revisiones de vulnerabilidades de seguridad de Java

  - Actualización del servicio Syslog

  - Mejoras en el rendimiento y la estabilidad

    Le recomendamos encarecidamente que actualice su entorno a esta nueva versión. Para más información, consulte la sección sobre [modos de implementación del recopilador de registros](discovery-docker.md#deployment-modes).

- **Compatibilidad con ServiceNow New York**  
Cloud App Security ahora admite la versión más reciente (New York) de ServiceNow. Para más información sobre cómo proteger ServiceNow, consulte [Conectar ServiceNow a Microsoft Cloud App Security](connect-servicenow-to-microsoft-cloud-app-security.md).

- **Lógica de detección mejorada: Viaje imposible**  
Hemos actualizado la lógica de detección para un viaje imposible con el fin de proporcionar una mejor cobertura y una mayor precisión. Como parte de esta actualización, también se actualizó la lógica de detección para un [viaje imposible desde redes corporativas](anomaly-detection-policy.md#impossible-travel).

- **Nuevo umbral para las directivas de actividad**  
Hemos agregado un umbral para las [directivas de actividad](user-activity-policies.md) para ayudarle a administrar el volumen de alertas. Las directivas que desencadenan un gran volumen de coincidencias durante varios días se deshabilitan automáticamente. Si recibe una alerta del sistema sobre esto, debe intentar perfeccionar las directivas agregando filtros adicionales o, si usa directivas para la elaboración de informes, considere la posibilidad de guardarlas como consultas en su lugar.

## <a name="cloud-app-security-release-162-163-and-164"></a>Notas de la versión 162, 163 y 164 de Cloud App Security

Fecha de publicación: 8 de diciembre de 2019

- **Cambio a las actividades y alertas de SIEM en formato CEF**  
El [formato de dirección URL del portal (CS1)](siem.md#sample-cloud-app-security-alerts-in-cef-format) para la actividad y la información de alertas que envía Cloud App Security a SIEMs ha cambiado a `https://<tenant_name>.portal.cloudappsecurity.com` y ya no contiene la ubicación del centro de datos. Los clientes que usen la coincidencia de patrones para la dirección URL del portal deben actualizar el patrón para reflejar este cambio.

## <a name="cloud-app-security-release-160-and-161"></a>Notas de la versión 160 y 161 de Cloud App Security

Fecha de publicación: 3 de noviembre de 2019

- **Datos de detección en Azure Sentinel (versión preliminar)**  
Cloud App Security ahora se integra con Azure Sentinel. Compartir datos de alertas y detección con Azure Sentinel ofrece las siguientes ventajas:

  - Habilitar la correlación de datos de detección con otros orígenes de datos para un análisis más profundo.

  - Ver los datos en Power BI con paneles predefinidos o crear sus propias visualizaciones.

  - Disfrutar de períodos de retención más largos con Log Analytics.

  Para más información, consulte [Integración con Azure Sentinel](siem-sentinel.md).

- **Conector de Google Cloud Platform (versión preliminar)**  
Cloud App Security está ampliando sus funcionalidades de supervisión de IaaS más allá de Amazon Web Services y ahora admite Google Cloud Platform. Esto le permite conectarse y supervisar de manera fluida todas las cargas de GCP con Cloud App Security. Esta conexión le ofrece un conjunto eficaz de herramientas para proteger el entorno de GCP, como las siguientes:

  - Visibilidad en todas las actividades realizadas mediante la consola de administrador y las llamadas API.

  - Capacidad para crear directivas personalizadas y usar plantillas predefinidas para alertar sobre eventos de riesgo.

  - Todas las actividades de GCP están cubiertas por el motor de detección de anomalías, que generará una alerta automáticamente ante cualquier comportamiento sospechoso, como un viaje imposible, actividades sospechosas masivas y la actividad desde un nuevo país.

  Para más información, consulte [Conexión de Google Cloud Platform con Microsoft Cloud App Security](connect-google-gcp-to-microsoft-cloud-app-security.md).

- **Nuevas plantillas de directiva**  
Cloud App Security ahora incluye nuevas plantillas de directiva de actividad integradas para los procedimientos recomendados de seguridad de Google Cloud Platform.

- **Analizadores mejorados de registro de Cloud Discovery**  
Cloud Discovery de Cloud App Security analiza una amplia gama de registros de tráfico para clasificar y puntuar aplicaciones. Ahora el analizador de registros integrado de Cloud Discovery admite el formato de registro de Ironport WSA 10.5.1.

- **Página de aterrizaje del usuario personalizable para controles de sesión**  
Hemos puesto en marcha la capacidad de los administradores de personalizar la página de aterrizaje que ven los usuarios al navegar a una aplicación a la que se aplica una directiva de sesión. Ahora puede mostrar el logotipo de su organización y personalizar el mensaje que se muestra. Para iniciar la personalización, vaya a la página de **configuración** y, en la opción de **control de aplicaciones de acceso a la nube** , seleccione **Supervisión de usuarios**.

- **Nuevas detecciones**  

  - **Cambios sospechosos en el servicio de registro de AWS (versión preliminar)** : Le avisa cuando un usuario realiza cambios en el servicio de registro de CloudTrail. Por ejemplo, los atacantes suelen desactivar la auditoría en CloudTrail para ocultar las huellas de su ataque.

  - **Varias actividades de creación de máquinas virtuales** : Le avisa cuando un usuario realiza un número inusual de actividades de creación de máquinas virtuales, en comparación con la línea de base aprendida. Ahora se aplica a AWS.

## <a name="cloud-app-security-release-159"></a>Notas de la versión 159 de Cloud App Security

Publicado el 6 de octubre de 2019

- **Nuevo analizador de registros de ContentKeeper de Cloud Discovery**  
Cloud Discovery de Cloud App Security analiza una amplia gama de registros de tráfico para clasificar y puntuar aplicaciones. Ahora Cloud Discovery incluye un analizador de registros integrado para admitir los formatos de registro de ContentKeeper. Para ver una lista de los analizadores de registros admitidos, vea [Firewalls y proxies admitidos](set-up-cloud-discovery.md#supported-firewalls-and-proxies).

- **Nuevas detecciones**  
Las siguientes nuevas directivas de detección de anomalías vienen integradas y habilitadas automáticamente:

  - **Actividad sospechosa de eliminación de correos electrónicos (versión preliminar)**  
    Le avisa cuando un usuario realiza actividades inusuales de eliminación de correos electrónicos. Esta directiva puede ayudarlo a detectar los buzones de usuario que pueden estar en peligro por posibles vectores de ataque, como la comunicación de comando y control (C&C/C2) por correo electrónico.

  - **Varias actividades de uso compartido de informes de Power BI (versión preliminar)**  
    Le avisa cuando un usuario realiza un número inusual de actividades de uso compartido de informes de Power BI, en comparación con la línea de base aprendida.

  - **Varias actividades de creación de máquinas virtuales (versión preliminar)**  
    Le avisa cuando un usuario realiza un número inusual de actividades de creación de máquinas virtuales, en comparación con la línea de base aprendida. Actualmente se aplica a Azure.

  - **Varias actividades de eliminación de almacenamiento (versión preliminar)**  
    Le avisa cuando un usuario realiza un número inusual de actividades de eliminación de almacenamiento, en comparación con la línea de base aprendida. Actualmente se aplica a Azure.

## <a name="cloud-app-security-release-158"></a>Notas de la versión 158 de Cloud App Security

Publicado el 15 de septiembre de 2019

- **Personalización de un nombre de informe de Cloud Discovery**  
El informe ejecutivo de Cloud Discovery proporciona información general sobre el uso de Shadow IT en la organización. Ahora tiene la opción de personalizar el nombre del informe antes de generarlo. Para más información, consulte [Generación de un informe ejecutivo de Cloud Discovery](discovered-apps.md#generate-cloud-discovery-executive-report).

- **Nuevo informe de información general sobre directivas**  
Cloud App Security detecta coincidencias de directivas y, cuando está definido, registra alertas que puede utilizar para comprender mejor su entorno en la nube. Ahora puede exportar un informe de información general de directivas que muestra las métricas de alerta agregadas por directiva para ayudarle a supervisar, comprender y personalizar las directivas para proteger mejor la organización. Para más información sobre cómo exportar el informe, consulte [Informe de información general sobre directivas](control-cloud-apps-with-policies.md#policies-overview-report).

## <a name="cloud-app-security-release-157"></a>Cloud App Security, versión 157

Publicada el 1 de septiembre de 2019

- **Aviso: Fin de la compatibilidad con TLS 1.0 y 1.1 el 8 de septiembre**  
Microsoft está moviendo todos sus servicios en línea a la Seguridad de la capa de transporte (TLS) 1.2+ para proporcionar el mejor cifrado de la clase. Por lo tanto, a partir del 8 de septiembre de 2019 Cloud App Security dejará de ser compatible con TLS 1.0 y 1.1, y no se admitirán las conexiones que usen estos protocolos. Para más información sobre cómo le afecta el cambio, consulte [nuestra entrada de blog](https://techcommunity.microsoft.com/t5/Enterprise-Mobility-Security/End-of-support-for-TLS-1-0-and-1-1-in-Microsoft-Cloud-App/ba-p/770507).

- **Nueva detección: Uso compartido sospechoso de Microsoft Power BI (versión preliminar)**  
La nueva directiva del informe de uso compartido sospechoso de Power BI está disponible de forma predeterminada y se habilita automáticamente para enviarle un aviso cuando un informe de Power BI que parezca confidencial se comparta de forma sospechosa fuera de su organización.

- **Nueva característica de exportación para la auditoría de aplicaciones de OAuth**  
Cloud App Security audita todas las actividades de autorización OAuth para ofrecerle funciones completas de supervisión e investigación de las actividades realizadas. Ahora también puede exportar los detalles de los usuarios que hayan autorizado una aplicación de OAuth específica, lo que le proporciona información adicional sobre los usuarios que podrá usar para un análisis más detallado.

- **Auditoría mejorada de eventos de Okta**  
Cloud App Security ahora admite la nueva API System Log publicada por Okta. Para obtener más información sobre cómo conectarse a Okta, vea [Conectar Okta con Microsoft Cloud App Security](connect-okta-to-microsoft-cloud-app-security.md).

- **Conector de Workday (versión preliminar)**  
Hay disponible un nuevo conector de aplicación para Workday. Ahora puede conectar Workday a Cloud App Security para supervisar actividades y proteger a sus usuarios y actividades. Para obtener más información, vea [Conexión de WorkDay a Microsoft Cloud App Security](connect-workday-to-microsoft-cloud-app-security.md).

- **Evaluación mejorada para el factor de riesgo "Directiva de contraseñas"**  
El Catálogo de aplicaciones en la nube ahora ofrece una evaluación granular para el factor de riesgo **Directiva de contraseñas**. Al mantener el mouse sobre el icono de información, se muestra un desglose de las directivas específicas exigidas por la aplicación.

## <a name="cloud-app-security-release-156"></a>Notas de la versión 156 de Cloud App Security

Publicado el 18 de agosto de 2019

- **Nuevos analizadores de registro de Cloud Discovery**  
Cloud Discovery de Cloud App Security analiza una amplia gama de registros de tráfico para clasificar y puntuar aplicaciones. Ahora Cloud Discovery incluye un analizador de registros integrado para admitir los formatos de registro Stormshield y Forcepoint LEEF.

- **Mejoras en el Registro de actividad**  
Cloud App Security ahora proporciona una mayor visibilidad de las actividades sin clasificar realizadas por las aplicaciones en el entorno. Estas actividades están disponibles en el Registro de actividad y también en las directivas de actividad. Para ver actividades sin clasificar, en el filtro **Tipo** seleccione **Sin especificar**. Para obtener más información sobre los filtros de actividad, vea [Filtros y consultas de actividad](activity-filters-queries.md).

- **Mejora de la investigación de usuarios de riesgo**  
Cloud App Security ofrece la posibilidad de identificar a usuarios de riesgo en la página **Usuarios y cuentas** mediante la especificación de grupos, aplicaciones e incluso roles concretos. Ahora también puede investigar a los usuarios de la organización por su puntuación de **prioridad de investigación**. Para obtener más información, vea [Comprender la puntuación de prioridad de investigación](tutorial-ueba.md#risk-score).

- **Mejoras de la directiva de actividad**  
Ahora puede crear alertas de directiva de actividad basadas en objetos de actividad. Por ejemplo, esta capacidad permite crear alertas sobre los cambios en los roles administrativos de Azure Active Directory. Para obtener más información sobre los objetos de actividad, vea [Filtros de actividad](activity-filters-queries.md#activity-filters).

## <a name="cloud-app-security-release-155"></a>Notas de la versión 155 de Cloud App Security

Publicado el 4 de agosto de 2019

- **Nuevas plantillas de directiva**  
Cloud App Security ahora incluye nuevas plantillas de directiva de actividad integradas para los procedimientos recomendados de seguridad de AWS.

- **Aviso: Fin de la compatibilidad con TLS 1.0 y 1.1 el 8 de septiembre**  
Microsoft está moviendo todos sus servicios en línea a la Seguridad de la capa de transporte (TLS) 1.2+ para proporcionar el mejor cifrado de la clase. Por lo tanto, a partir del 8 de septiembre de 2019 Cloud App Security dejará de ser compatible con TLS 1.0 y 1.1, y no se admitirán las conexiones que usen estos protocolos. Para más información sobre cómo le afecta el cambio, consulte [nuestra entrada de blog](https://techcommunity.microsoft.com/t5/Enterprise-Mobility-Security/End-of-support-for-TLS-1-0-and-1-1-in-Microsoft-Cloud-App/ba-p/770507).

- **Lógica mejorada para actividades de inicio de sesión interactivas (implementación gradual)**  
Estamos implementando gradualmente una nueva lógica para identificar si una actividad de inicio de sesión de Azure Active Directory es interactiva. La nueva lógica mejora la capacidad de Cloud App Security de solo investigar las actividades de inicio de sesión iniciadas por un usuario.

## <a name="cloud-app-security-release-154"></a>Cloud App Security, versión 154

Publicado el 21 de julio de 2019

- **La incorporación y la implementación del Control de aplicaciones de acceso condicional para cualquier aplicación está ahora disponible con carácter general**  
Desde que lanzamos la versión preliminar de Control de aplicaciones de acceso condicional para cualquier aplicación el mes pasado, hemos recibido comentarios muy positivos y nos complace anunciar que ya está disponible con carácter general. Esta nueva funcionalidad permite implementar cualquier aplicación web para trabajar con directivas de sesión y acceso, con lo que se habilita la supervisión y el control eficaces en tiempo real.

- **Evaluación de la configuración de seguridad para AWS**  
Cloud App Security está implementando de forma gradual la funcionalidad de obtener una evaluación de la configuración de seguridad del entorno de Amazon Web Services para el cumplimiento de CIS, y proporciona recomendaciones para los controles de seguridad y los valores de configuración que falten. Esta capacidad proporciona a las organizaciones una única vista para supervisar el estado de cumplimiento de todas las cuentas de AWS conectadas.

- **Detecciones de anomalías de aplicaciones de OAuth**  
Hemos ampliado nuestra capacidad actual para detectar aplicaciones de OAuth sospechosas. Ya hay disponibles cuatro detecciones nuevas listas para usar que perfilan los metadatos de las aplicaciones de OAuth autorizadas de su organización para identificar cuáles son potencialmente maliciosas.

## <a name="cloud-app-security-release-153"></a>Notas de la versión 153 de Cloud App Security

Publicada el 7 de julio de 2019

- **Compatibilidad mejorada con Dropbox**  
Cloud App Security ahora admite la acción de gobernanza **Papelera** para Dropbox: esta acción de gobernanza se puede utilizar de forma manual o automática como parte de una directiva de archivo.
- **Nuevas aplicaciones destacadas para el control de aplicaciones de acceso a la nube**  
El control de aplicaciones de acceso condicional para las siguientes aplicaciones destacadas ahora está disponible con carácter general:

    - OneDrive para la Empresa
    - SharePoint Online
    - Azure DevOps
    - Exchange Online
    - Power BI

- **Autorización de archivos identificados como malware**  
Cloud App Security examina los archivos de las aplicaciones conectadas para comprobar la exposición a DLP y la existencia de malware. Ahora puede autorizar los archivos identificados como malware cuya seguridad se confirmó después de una investigación. La autorización de un archivo quita el informe de detección de malware y suprime futuras coincidencias en este archivo. Para obtener más información sobre la detección de malware, consulte el tema sobre la [detección de anomalías de Cloud App Security](anomaly-detection-policy.md).

## <a name="cloud-app-security-release-152"></a>Notas de la versión 152 de Cloud App Security

Publicada el 23 de junio de 2019

- **Implementación del Control de aplicaciones de acceso condicional para cualquier aplicación (versión preliminar)**  
Nos complace anunciar que hemos ampliado la compatibilidad con el Control de aplicaciones de acceso condicional a cualquier aplicación web, además de la amplia compatibilidad que ya ofrecemos para las [aplicaciones destacadas](proxy-intro-aad.md). Esta nueva funcionalidad permite implementar cualquier aplicación web para trabajar con directivas de sesión y acceso, con lo que se habilita la supervisión y el control eficaces en tiempo real. Por ejemplo, puede proteger las descargas con etiquetas de Azure Information Protection y bloquear la carga de documentos confidenciales, brindando auditoría, entre muchas otras acciones.
- **Auditoría de la actividad del portal**  
Cloud App Security hace una auditoría de toda la actividad del administrador del portal para ofrecer una supervisión e investigación integrales de las actividades realizadas. Ahora también puede exportar hasta 90 días de actividades para realizar más investigación y análisis como, por ejemplo, realizar una auditoría a un administrador que investiga a un usuario específico o ver alertas específicas. Para exportar el registro, vaya a la página de configuración **Administrar el acceso de administrador**.
- **Cierre de sesión personalizado desde el portal de Cloud App Security**  
Ahora puede configurar el cierre de sesión automático de las sesiones del administrador en el portal que están inactivas por más tiempo que un período especificado.

## <a name="cloud-app-security-release-151"></a>Versión 151 de Cloud App Security

Publicada el 9 de junio de 2019

- **UEBA híbrido: integración nativa con Azure ATP (versión preliminar)**  
Cloud App Security ahora se integra de manera nativa con Azure ATP para proporcionar una vista única de las actividades de identidad en ambas aplicaciones en la nube y la red local. Para más información, consulte [Integración de Azure Advanced Threat Protection](mdi-integration.md).
- **Mejoras de UEBA**  
Para ayudarlo a identificar las amenazas que están por debajo del radar, Cloud App Security ahora usa la generación de perfiles única para brindar puntuaciones de riesgo a actividades y alertas individuales. Las puntuaciones de riesgo se pueden usar para identificar las actividades que no son suficientemente sospechosas como para desencadenar las alertas. Sin embargo, al agregar las puntuaciones de riesgo a la **puntuación de prioridad de investigación** de un usuario, Cloud App Security ayuda a identificar el comportamiento de riesgo y a centrar la investigación. Estas funcionalidades nuevas ahora están disponibles en la página de usuario rediseñada.
- **Factor de riesgo nuevo agregado al Catálogo de aplicaciones en la nube**  
El Catálogo de aplicaciones en la nube ahora incluye el factor de riesgo del plan de recuperación ante desastres para permitirle evaluar las aplicaciones en el Catálogo de aplicaciones en la nube para permitir la continuidad empresarial.
- **Disponibilidad general del conector de Microsoft Flow**  
Desde la versión preliminar de la compatibilidad de Microsoft Cloud App Security con el conector de Microsoft Flow el año pasado, ahora el conector está disponible con carácter general.
- **Mejora de la gobernanza automatizada para las directivas de archivo**  
Cloud App Security ahora admite la configuración de la acción de gobernanza **Trash** (Enviar a la papelera) para las directivas de archivo. Esta acción de gobernanza brinda la capacidad de mover automáticamente archivos a la carpeta de la papelera.
- **Compatibilidad mejorada con Google Drive**  
Cloud App Security ahora admite la acción de gobernanza **Trash** (Enviar a la papelera) para Google Drive. Esta acción de gobernanza brinda la capacidad de mover archivos de Google Drive a la carpeta de la papelera.
- **Permiso nuevo para los roles de administrador de grupo y administrador de aplicación**  
Los roles de *administrador de aplicación o instancia* y de *administrador de grupo de usuarios* ahora admiten el acceso de solo lectura.
- **Actividades de inicio de sesión de autenticación heredada (implementación gradual)**  
Cloud App Security ahora investiga las actividades de inicio de sesión de Azure Active Directory que usan protocolos heredados como ActiveSync. Estas actividades de inicio de sesión se pueden ver en el registro de actividad y se pueden usar al configurar las directivas.

## <a name="cloud-app-security-release-150"></a>Versión 150 de Cloud App Security

Fecha de publicación: 26 de mayo de 2019

- **Mejora en la exportación de alertas**  
Ahora, al exportar las alertas a CSV desde la página **Alertas** , los resultados incluyen la fecha de la resolución o del descarte de la alerta.

## <a name="cloud-app-security-release-148-and-149"></a>Notas de la versión 148 y 149 de Cloud App Security

Fecha de publicación: 12 de mayo de 2019

- **Conector de la aplicación WebEx disponible**  
Hay disponible un nuevo conector de aplicación web para Cisco WebEx Teams en versión preliminar pública. Ahora puede conectar Microsoft Cloud­ App Security a Cisco WebEx Teams para supervisar y proteger a los usuarios, actividades y archivos. Para más información, consulte [Conexión a WebEx](connect-webex-to-microsoft-cloud-app-security.md).

- **Nuevas ubicaciones del servicio de clasificación de datos de Microsoft**  
El [servicio de clasificación de datos de Microsoft](dcs-inspection.md) ahora está disponible en cuatro nuevas ubicaciones: Australia, India, Canadá y Japón. Si su inquilino de Office se encuentra en estas ubicaciones, ahora puede usar el servicio de clasificación de datos de Microsoft como método de inspección de contenido en las directivas de archivo de Microsoft Cloud­ App Security.

- **Detección de PaaS e IaaS de Shadow**  
Microsoft Cloud App Security ha ampliado sus capacidades de Cloud Discovery y ahora también proporciona Shadow IT para los recursos que se hospedan en soluciones de IaaS y PaaS, como Microsoft Azure, Amazon Web Services y Google Cloud Platform. Cloud Discovery ahora le ofrece visibilidad sobre qué aplicaciones personalizadas se ejecutan sobre IaaS y PaaS y las cuentas de almacenamiento que se están creando, entre otras cosas. Use esta nueva funcionalidad con el fin de detectar los recursos que existen, quién tiene acceso a cada uno de ellos y la cantidad de tráfico que se transmite.

- **Certificación de aplicaciones**  
La evaluación de cumplimiento y riesgo de Microsoft Cloud App Security ahora permite que los proveedores de la nube certifiquen que la aplicación está actualizada en el catálogo de aplicaciones de la nube. Este programa piloto permite a los proveedores de la nube completar un cuestionario de autocertificación basado en los atributos de riesgo del catálogo de aplicaciones de la nube para asegurarse de que su evaluación de riesgos en Cloud App Security es precisa y está actualizada. Luego, los usuarios pueden obtener una indicación de qué atributos de riesgo fueron certificados por el proveedor (en lugar de que sea el equipo de Cloud App Security quien los evalúe) y el momento en que el proveedor envió cada atributo. Para obtener más información, consulte [Comprobaciones sobre la aplicación](attest-your-app.md).

- **Granularidad de la carga de trabajo de Office 365**  
Al conectar Office 365 con Microsoft Cloud App Security, ahora tiene control sobre qué cargas de trabajo desea conectar. Por ejemplo, los clientes interesados solo en conectar Office 365 para la supervisión de la actividad ahora pueden hacerlo durante el proceso de conexión, o mediante la edición de un conector de Office 365 existente. Como parte de este cambio, OneDrive y SharePoint ya no se mostrarán como conectores independientes, sino que se incluirán en el conector de Office 365 como la carga de trabajo _Archivos de Office 365_. Los clientes con un conector de Office 365 existente no se ven afectados por este cambio.

- **Compatibilidad mejorada con Teams**  
Ahora puede supervisar y bloquear el envío de mensajes en la aplicación web de Teams en tiempo real, mediante la configuración de una directiva de sesión basada en contenido confidencial.

## <a name="cloud-app-security-release-147"></a>Notas de la versión 147 de Cloud App Security

Fecha de publicación: 14 de abril de 2019

- **Nuevos analizadores de registro de Cloud Discovery**  
Cloud Discovery de Cloud App Security ahora incluye un analizador de registros integrado para admitir el formato de registro LEEF de Palo Alto.

- **Actualizaciones de directivas de sesión**  
  - **Método de inspección de contenido adicional para las directivas de sesión** :  Al establecer una directiva de sesión, ahora tiene la opción de elegir el servicio de clasificación de datos como método de inspección de contenido de los archivos. El servicio de clasificación de datos ofrece al usuario un amplio rango de tipos de datos confidenciales integrados para utilizarlos en la identificación de información confidencial.
  - **Control mejorado de los permisos de archivo en las directivas de sesión** :  Al crear una directiva de sesión para controlar las descargas mediante Cloud App Security, ahora puede aplicar automáticamente permisos por usuario, como por ejemplo de solo lectura, a los documentos una vez descargados desde las aplicaciones en la nube. Esto proporciona un nivel mucho mayor de flexibilidad y la capacidad de proteger la información más allá de las etiquetas corporativas configuradas previamente.
  - **Control de descarga de archivos grandes** :  Cuando se habilita la inspección de contenido en las directivas de sesión, ahora puede controlar lo que sucede cuando un usuario intenta descargar un archivo muy grande. Si el archivo es demasiado grande para analizarlo durante la descarga, puede elegir si desea bloquear o permitir dicho análisis.

## <a name="cloud-app-security-release-146"></a>Notas de la versión 146 de Cloud App Security

Fecha de publicación: 31 de marzo de 2019

- **Mejora de viaje imposible**  
Se ha mejorado la detección de viajes imposibles con compatibilidad específica para los países/regiones vecinos.
- **Compatibilidad adicional de atributos para el analizador genérico de CEF**  
La compatibilidad del analizador de registros de Cloud Discovery para el formato genérico CEF se ha mejorado para admitir atributos adicionales.
- **Acceso limitado a los informes de Cloud Discovery**  
Además del rol de administrador de Discovery, ahora puede limitar el acceso a informes específicos de Discovery. Esta mejora le permite configurar privilegios para los datos de sitios y unidades de negocio específicos.
- **Compatibilidad con nuevos roles: Lector global**  
Microsoft Cloud App Security ahora admite el rol de lector global de Azure AD. El lector global tiene acceso de solo lectura a todos los aspectos de Microsoft Cloud App Security, pero no puede cambiar ninguna configuración ni realizar ninguna acción.

## <a name="cloud-app-security-release-145"></a>Notas de la versión 145 de Cloud App Security

Fecha de publicación: 17 de marzo de 2019

- **Integración con Microsoft Defender ATP disponible para público general**  
El año pasado anunciamos la [integración con Protección contra amenazas avanzada de Windows Defender](https://techcommunity.microsoft.com/t5/Enterprise-Mobility-Security/Microsoft-Cloud-App-Security-and-Windows-Defender-ATP-better/ba-p/263265) que mejora la detección de shadow IT de su organización y la amplía más allá de la red corporativa. [Habilitada con un solo clic](https://query.prod.cms.rt.microsoft.com/cms/api/am/binary/RWtNmG), nos complace poder anunciar que esta integración única ya está disponible con carácter general.
- **Soporte técnico de Dynamics 365 CRM**  
Cloud App Security agregó control y supervisión en tiempo real para Dynamics 365 CRM, lo que permite proteger las aplicaciones empresariales y el contenido confidencial almacenado en estas aplicaciones. Para más información sobre lo que se puede hacer con Dynamics 365 CRM, consulte [este artículo](proxy-intro-aad.md#how-it-works).

## <a name="cloud-app-security-release-144"></a>Notas de la versión 144 de Cloud App Security

Fecha de publicación: 3 de marzo de 2019

- **Investigación unificada de SecOps para entornos híbridos**  
Como muchas organizaciones tienen entornos híbridos, los ataques empiezan en la nube y se dirigen al entorno local, lo que significa que los equipos de SecOps necesitan investigar estos ataques desde distintos lugares. Al combinar señales de orígenes locales y en la nube, incluidos Microsoft Cloud App Security, Azure ATP y Azure AD Identity Protection, Microsoft capacita a los analistas de seguridad proporcionando información de usuario e identidad unificada, en una sola consola, lo que pone fin a la necesidad de alternar entre las soluciones de seguridad. Esto proporciona a los equipos de SecOps más tiempo y la información adecuada para tomar mejores decisiones y corregir de forma activa las amenazas y los riesgos de identidad reales. Para más información, consulte [Investigación unificada de SecOps para entornos híbridos](https://techcommunity.microsoft.com/t5/Enterprise-Mobility-Security/Unified-SecOps-Investigation-for-Hybrid-Environments/ba-p/360850).

- **Funcionalidades de espacio aislado para la detección de malware** (implementación gradual)  
Las funcionalidades de detección de malware de Cloud App Security se expanden para incluir la capacidad de identificar malware zero-day a través de tecnología de espacio aislado avanzada.  
Como parte de esta funcionalidad, Cloud App Security identifica automáticamente los archivos sospechosos y los detona para buscar un comportamiento sospechoso del archivo e indicadores de que el archivo tiene intenciones maliciosas (malware).
Como parte de este cambio, las directivas de detección de malware ahora incluyen un campo de tipo de detección que le permite filtrar por inteligencia sobre amenazas, así como el espacio aislado.

- **Actualizaciones del acceso condicional**  
El Control de aplicaciones de acceso condicional agregó la capacidad de supervisar y bloquear estas actividades:
  - Cargas de archivos en cualquier aplicación: habilitación de escenarios como la prevención de la carga de extensiones de malware conocidas y la garantía de protección de los archivos por parte de los usuarios con Azure Information Protection antes de cargarlos.
  - Copiar y pegar en cualquier aplicación: redondeo de controles sólidos de filtración de datos que ya incluía el control de actividades de descarga, impresión y personalizadas como el uso compartido.
  - Enviar mensaje: garantía de que los datos personales como las contraseñas no se comparten en herramientas de colaboración populares como Slack, Salesforce y Workplace de Facebook.
  - Las directivas de sesión ahora incluyen plantillas integradas para permitir que su organización habilite sin esfuerzo la supervisión en tiempo real y el control populares sobre sus aplicaciones autorizadas, como **Bloquear carga según la inspección de contenido en tiempo real**.

## <a name="cloud-app-security-release-143"></a>Notas de la versión 143 de Cloud App Security

Fecha de publicación: 17 de febrero de 2019

- **Implementación de ámbito para instancias de la aplicación**  
La implementación con ámbito ahora se puede configurar en el nivel de instancia de la aplicación, lo que permite un aumento de la granularidad y el control.
- **Mejoras de roles**  
  - Los roles de Office 365 de administrador de datos y operador de seguridad se admiten ahora en Cloud App Security. El rol de administrador de datos permite a los usuarios administrar todo aquello relacionado con los archivos, así como ver los informes de Cloud Discovery. Los operadores de seguridad tienen permiso para administrar alertas y ver la configuración de directivas.
  - El rol de lector de seguridad ahora puede configurar el agente SIEM, lo que permite un mejor ámbito de permiso.

- **Soporte técnico de Microsoft Flow**  
Cloud App Security ahora supervisa las actividades del usuario en Microsoft Flow. Las actividades admitidas son las actividades notificadas por Flow al registro de auditoría de Office 365.

- **Agrupación de entidades de alerta**  
La página **Alerta** ahora agrupa las entidades relacionadas que están involucradas en la alerta para ayudar en la investigación.

## <a name="cloud-app-security-release-142"></a>Notas de la versión 142 de Cloud App Security

Publicado el 3 de febrero de 2019

- **Configuración de la directiva de sesión en Azure AD**  
Ahora puede configurar directivas de sesión para supervisar a los usuarios o bloquear las descargas en tiempo real, directamente en el acceso condicional de Azure AD. Todavía puede configurar directivas de sesión avanzadas directamente en Cloud App Security. Para recorrer esta implementación, consulte [Implementación del Control de aplicaciones de acceso condicional para aplicaciones destacadas](proxy-deployment-aad.md).

- **Consultas sugeridas y guardadas para aplicaciones de OAuth**  
Las consultas sugeridas se han agregado a la página de aplicaciones de OAuth y proporcionan plantillas de investigación predefinidas para filtrar las aplicaciones de OAuth. Las consultas sugeridas incluyen filtros personalizados para identificar aplicaciones arriesgadas, como las aplicaciones autorizadas por los administradores. Las consultas guardadas permiten guardar consultas personalizadas para su uso futuro, de forma similar a las consultas guardadas disponibles hoy en las páginas de detección y registro de actividad.

- **Configuración predeterminada de auditoría de Office 365**  
Si desea habilitar la supervisión de las actividades de Office 365 en Cloud App Security, ahora es necesario habilitar la auditoría en el [Centro de seguridad y cumplimiento de Office](/office365/securitycompliance/turn-audit-log-search-on-or-off#turn-on-audit-log-search), lo que se debe a un [cambio en la auditoría de Office 365](/office/office-365-management-api/office-365-management-activity-api-faq#what-happens-if-i-disable-auditing-for-my-office-365-organization-will-i-still-get-events-via-the-management-activity-api). Este cambio solo debe realizarse si aún no ha habilitado la supervisión de las actividades de Office 365 en Cloud App Security.

- **Compatibilidad mejorada con Box**  
Cloud App Security ahora admite dos nuevas acciones de gobierno para Box:

  - **Expiración de vínculo compartido** : esta acción de gobierno le proporciona la capacidad de establecer una fecha de expiración para un vínculo compartido después del cual dejará de estar activo.

  - **Cambio del nivel de acceso del vínculo de uso compartido** : esta acción de gobierno proporciona la capacidad de cambiar el nivel de acceso del vínculo compartido entre solo la empresa, solo colaboradores y el público.

- **Compatibilidad con múltiples ubicaciones en OneDrive**  
Cloud App Security ahora proporciona visibilidad completa de los archivos de OneDrive, incluso si están dispersos en varias ubicaciones geográficas. La protección está disponible ahora para los archivos que se encuentran en las ubicaciones adicionales, así como en la ubicación principal.

- **Mejora en la navegación del portal**  
El portal de Cloud App Security se ha mejorado para ofrecer una mejor navegación y una mejor alineación de Cloud App Security con los otros servicios de seguridad de Microsoft, para simplificar la facilidad de uso.

## <a name="cloud-app-security-release-141"></a>Notas de la versión 141 de Cloud App Security

Fecha de publicación: 20 de enero de 2019

- **Mejoras en la evaluación de riesgos en la nube**  
  - La evaluación de riesgos de Cloud App se mejoró con dos experiencias nuevas.
    - Un nuevo atributo de **tipo de datos** evalúa el tipo de contenido que los usuarios pueden cargar en la aplicación. Puede usar este atributo para evaluar una aplicación en función de la confidencialidad de cada tipo de datos de su organización.
    - Para obtener una información general más completa sobre los riesgos de una aplicación, ahora puede dinamizar fácilmente desde la evaluación de riesgos de la aplicación hasta la evaluación de riesgos de la empresa de hospedaje. Para ello, haga clic en el atributo de **empresa de hospedaje**.

- **Contexto de archivo mejorado para la investigación de alertas de detección de anomalías**  
  - La investigación de detección de anomalías se ha mejorado para que pueda ver información adicional asociada a los archivos implicados en una alerta. Cuando se desencadenan las alertas para alertas de actividad inusual relacionadas con archivos (descargar, compartir, eliminar), esta exploración en profundidad está disponible. Por ejemplo, si la mayoría de los archivos afectados proceden de la misma carpeta o comparten la misma extensión de archivo, verá esta información en la sección de riesgos adicionales de la alerta.

- **Consultas para la investigación de archivos**  
  - La capacidad de Cloud App Security para crear y guardar consultas personalizadas se amplió a la página **Archivos**. Las consultas de la página de **archivos** permiten crear plantillas de consulta que se pueden reutilizar para una investigación en profundidad.

## <a name="cloud-app-security-release-139-140"></a>Notas de la versión 139, 140 de Cloud App Security

Fecha de publicación: 6 de enero de 2019

- **Cambio en la detección de archivos**  
Los archivos compartidos con todos los usuarios de SharePoint y OneDrive ahora se consideran **internos** [debido a los cambios realizados en SharePoint y OneDrive](https://support.microsoft.com/help/4089534/how-to-grant-the-everyone-claim-to-external-users-in-office-365). Por tanto, si se detecta un archivo que se comparte con todo el mundo, ahora se tratará como un archivo interno; esto afectará a la forma en que el archivo se controla mediante directivas y se muestra en la página de archivos.

- **Cambio en la supervisión de archivos**  
El comportamiento predeterminado de la supervisión de archivos ha cambiado para los clientes nuevos e inactivos. Ahora tendrá que activar la supervisión de archivos para habilitar la característica, mediante **Configuración** > **Archivos**. Los clientes activos existentes no se verán afectados por este cambio.

- **Optimización avanzada de directivas de detección de anomalías**  
Ahora puede influir en el motor de detección de anomalías para suprimir o exponer alertas según sus preferencias.
  - En la directiva de viaje imposible, puede establecer el control deslizante de sensibilidad para determinar el nivel de comportamiento anómalo necesario antes de que se desencadene una alerta.
  - También puede configurar si las alertas de actividad de un país o región poco frecuente, direcciones IP anónimas, direcciones IP sospechosas y viajes imposibles deben analizar tanto inicios de sesión con errores como correctos o simplemente inicios de sesión correctos.

- **Compatibilidad con varias cadenas de confianza**  
Control de aplicaciones de acceso condicional ahora permite agregar y usar varios certificados raíz o intermedios de confianza como forma de administración de dispositivos.

- **Nuevo rol de Cloud Discovery** (implementación gradual)  
Cloud App Security ahora incluye un nuevo rol de administrador para los usuarios de Cloud Discovery. Este rol se puede usar para limitar el acceso de un usuario administrador a solo la configuración y los datos de Cloud Discovery en el portal de Cloud App Security.

- **Compatibilidad con etiquetas unificadas de Microsoft Information Protection** (implementación gradual)  
Cloud App Security ahora admite las etiquetas unificadas de Microsoft Information Protection. En el caso de los clientes que ya [hayan migrado sus etiquetas de clasificación del Centro de seguridad y cumplimiento de Office 365](/azure/information-protection/configure-policy-migrate-labels), Cloud App Security las identificará y trabajará con ellas, tal como se describe en [Integración de Azure Information Protection](azip-integration.md).

**Compatibilidad con el etiquetado de archivos PDF** (implementación gradual)  
En el caso de los clientes que usen las etiquetas unificadas, Cloud App Security ahora admite el etiquetado automático para archivos PDF.

## <a name="cloud-app-security-release-138"></a>Notas de la versión 138 de Cloud App Security

Fecha de publicación: 9 de diciembre de 2018

- **Carga automática del Registro con Docker en Windows**  
Cloud App Security ahora admite la carga automática del Registro para Windows 10 (Fall Creators Update) y Windows Server, versión 1709 y posteriores, mediante un Docker para Windows. Para más información e instrucciones sobre cómo se puede configurar este, consulte [Docker en Windows local](discovery-docker-windows.md).

- Cloud App Security se integra con [Microsoft Flow](/flow/getting-started) para proporcionar una automatización de alertas personalizada y cuadernos de estrategias de orquestación. Para más información e instrucciones de integración, consulte [Integración con Flow para la automatización de alertas personalizada](flow-integration.md).

## <a name="cloud-app-security-release-137"></a>Notas de la versión 137 de Cloud App Security

Fecha de publicación: 25 de noviembre de 2018

- **Compatibilidad agregada para Dynamics**  
Cloud App Security ahora incluye compatibilidad para las actividades de Microsoft Dynamics que se admiten en el registro de auditoría de Office 365.

- **Examen del contenido cifrado (versión preliminar)**  
Cloud App Security ahora permite examinar el contenido protegido por las etiquetas de protección de Azure Information Protection. Esto le permitirá buscar contenido confidencial, incluso en archivos que ya se han cifrado mediante Azure Information Protection.

- **Aviso: Nueva terminología.**  
El nombre de las funcionalidades de los permisos de aplicación se ha cambiado para mayor claridad: ahora se denominan **aplicaciones de OAuth**.

## <a name="cloud-app-security-release-136"></a>Notas de la versión 136 de Cloud App Security

Fecha de publicación: 11 de noviembre de 2018

- **Actualizaciones de Cloud Discovery**  
El analizador de registros personalizado se ha mejorado para admitir formatos de registros de tráfico web adicionales y más complejos. Como parte de estas mejoras, los usuarios ahora pueden introducir encabezados personalizados para los archivos de registro CSV sin encabezado, usar delimitadores especiales para los archivos de valor de clave, procesar el formato de archivo Syslog, etc.

- **Nuevas directivas de detección de anomalías**  
Reglas de manipulación sospechosa de la bandeja de entrada: Esta directiva genera un perfil del entorno y activa alertas cuando se establecen reglas sospechosas que eliminan o mueven mensajes o carpetas en la bandeja de entrada de un usuario. Esto puede indicar que la cuenta del usuario está en peligro, que los mensajes se están ocultando de manera intencionada o que el buzón se está usando para enviar correo no deseado y malware en la organización.

- **Compatibilidad con grupos en las directivas de permisos de aplicación**  
Cloud App Security ofrece ahora la capacidad de definir directivas de permisos de aplicación de forma más granular, en función de la pertenencia a grupos de los usuarios que han autorizado las aplicaciones. Por ejemplo, un administrador puede decidir establecer una directiva que revoca aplicaciones no comunes si requieren permisos elevados, solo si el usuario que autoriza los permisos es miembro del grupo de administradores.

- **Control de aplicaciones de acceso condicional ahora se integra con las aplicaciones locales mediante Azure Active Directory Application Proxy**  
  - [Azure AD Application Proxy](/azure/active-directory/manage-apps/application-proxy) proporciona un inicio de sesión único y un acceso remoto seguro para aplicaciones web hospedadas en local.
  - Estas aplicaciones web locales ahora se pueden enrutar a Microsoft Cloud App Security mediante el acceso condicional de Azure AD para proporcionar controles y supervisión en tiempo real, con directivas de [acceso](access-policy-aad.md) y de [sesión](session-policy-aad.md).

## <a name="cloud-app-security-release-133-134-135"></a>Notas de la versión 133, 134, 135 de Cloud App Security

Fecha de publicación: octubre de 2018

- **Nuevas directivas de detección de anomalías que se implementan gradualmente**  
  - La nueva directiva Filtración de datos a aplicaciones no autorizadas se habilita automáticamente para enviarle una alerta cada vez que un usuario o una dirección IP use una aplicación que no tenga permitido realizar una actividad que pueda suponer un intento de filtrar información de la organización.
    - La nueva directiva Varias actividades de eliminación de VM genera perfiles de su entorno y desencadena alertas cuando los usuarios eliminan varias máquinas virtuales en una sola sesión, en relación con la línea de base de su organización.

- **Servicio de clasificación de datos disponible para APAC**  
  - La inspección de contenido del servicio de clasificación de datos ahora está disponible para los clientes de APAC. Para obtener una lista de soporte técnico regional completo, consulte [Integración de los servicios de clasificación de datos de Microsoft](dcs-inspection.md).

- **Compatibilidad de Cloud Discovery con i-Filter**  
  - La característica de Cloud Discovery de Cloud App Security ahora tiene compatibilidad mejorada con el analizador Syslog de i-Filter.

## <a name="cloud-app-security-release-132"></a>Notas de la versión 132 de Cloud App Security

Fecha de publicación: 25 de septiembre de 2018

- **Control de aplicaciones de acceso condicional para Office 365 está ahora en versión preliminar pública**  
  - Control de aplicaciones de acceso condicional ahora admite Office 365 y cualquier aplicación que esté configurada con Open ID Connect.
  - Proporcione comentarios en una sesión: Esta nueva herramienta le permite enviar comentarios al equipo de Cloud App Security sobre el rendimiento de una aplicación bajo control de sesión, directamente desde dentro de la sesión.

- **Integración nativa con Microsoft Defender ATP para Shadow IT Discovery más allá de los límites de la empresa**  
  - Microsoft Cloud App Security ahora se integra de forma nativa con Protección contra amenazas avanzada (ATP) de Windows Defender para proporcionar las funcionalidades de Shadow IT Discovery sin implementación para el uso de la red corporativa de aplicaciones en la nube.  Esto le permite ejecutar Cloud Discovery en las máquinas, incluso cuando no están dentro de la red corporativa. También habilita la investigación basada en máquinas: después de identificar a un usuario de riesgo, puede comprobar todas las máquinas a las que el usuario ha tenido acceso para detectar posibles riesgos. Si identifica una máquina de riesgo, puede comprobar todos los usuarios que la usaban para investigar posibles riesgos. Para más información, consulte integración de Protección contra amenazas avanzada de Windows Defender con [Microsoft Cloud App Security](mde-integration.md).

- **Inspección de contenido para archivos cifrados**  
  - Cloud App Security admite ahora la inspección de contenido de archivos protegidos cifrados que se protegieron con Azure Information Protection. Ahora puede inspeccionar estos archivos cifrados para volver a clasificarlos e identificar infracciones adicionales de la directiva de seguridad y exposición de DLP.

## <a name="cloud-app-security-release-131"></a>Notas de la versión 131 de Cloud App Security

Fecha de publicación: 2 de septiembre de 2018

- **Revocación automática de los permisos en aplicaciones de OAuth de riesgo**  
Ahora puede controlar a qué aplicaciones de OAuth tienen acceso los usuarios, revocando el permiso de aplicación para las aplicaciones de OAuth en Office, Google o Salesforce. Al crear una **directiva de permisos de aplicación** , ahora puede establecer la directiva para revocar el permiso de una aplicación.

- **Analizador integrado adicional de Cloud Discovery compatible**  
Cloud Discovery ahora admite el formato de registro de Forcepoint Web Security Cloud.

## <a name="cloud-app-security-release-130"></a>Notas de la versión 130 de Cloud App Security

Fecha de publicación: 22 de agosto de 2018

- **Nueva barra de menús**  
Para proporcionar una experiencia de administración más coherente en los productos de Office 365 y permitirle cambiar más fácilmente entre las soluciones de seguridad de Microsoft, la barra de menús del portal de Cloud App Security se ha desplazado al lado izquierdo de la pantalla. Esta experiencia de navegación coherente le ayuda a orientarse al pasar de un portal de seguridad de Microsoft a otro.

- **Impacto de la puntuación de la aplicación OAuth**  
Ahora puede enviar los comentarios del equipo de Cloud App Security para indicarnos si hay una aplicación de OAuth detectada en la organización que parece malintencionada. Esta nueva característica le permite formar parte de nuestra comunidad de seguridad y mejorar el análisis y la puntuación de riesgo de las aplicaciones de OAuth. Para más información, consulte [Administrar permisos de aplicación](manage-app-permissions.md).

- **Nuevos analizadores de Cloud Discovery**  
Los analizadores de Cloud Discovery admiten ahora Secure Cloud Gateway y Sophos XG de iboss.

## <a name="cloud-app-security-release-129"></a>Notas de la versión 129 de Cloud App Security

Fecha de publicación: 5 de agosto de 2018

- **Nuevas directivas de detección de anomalías: reglas de correo electrónico sospechosas**  
Se agregaron nuevas directivas de detección de anomalías que detectan reglas de reenvío de correo electrónico sospechosas, por ejemplo, si un usuario creó una regla de bandeja de entrada sospechosa que reenvía una copia de todos los correos electrónicos a una dirección externa.

- Esta versión incluye correcciones y mejoras para varios problemas.

## <a name="cloud-app-security-release-128"></a>Notas de la versión 128 de Cloud App Security

Publicada el 22 de julio de 2018

- **Acciones de las aplicaciones de OAuth en varias aplicaciones**  
En el caso de las aplicaciones de OAuth a las que se han concedido permisos de aplicación, ahora puede prohibir o aprobar varias aplicaciones en una única acción. Por ejemplo, puede revisar todas las aplicaciones a las que los usuarios de su organización han concedido permisos, seleccionar todas las aplicaciones que quiera prohibir y, a continuación, hacer clic en la opción de prohibir aplicaciones para revocar todo el consentimiento concedido y ya no permitirá que los usuarios concedan permiso a esas aplicaciones.  Para más información, consulte [Administrar aplicaciones de OAuth](manage-app-permissions.md).

- **Compatibilidad mejorada con aplicaciones de Azure**  
En Azure, estamos implementando gradualmente la capacidad de detectar aplicaciones como actividades de la cuenta de usuario realizadas por las aplicaciones de Azure (tanto internas como externas). Esto le permite crear directivas que le avisarán si una aplicación realiza actividades inesperadas y no autorizadas. Para obtener más información, consulte [Conectar Azure con Microsoft Cloud App Security](connect-azure-to-microsoft-cloud-app-security.md).

- **Motor de clasificación de datos actualizado con nuevos tipos confidenciales de RGPD**  
El [servicio de clasificación de datos de Cloud App Security](dcs-inspection.md) ha agregado nuevos tipos confidenciales de RGPD a nuestro motor de clasificación de datos para que pueda detectar contenido relacionado con RGPD en los archivos.

- **Actualizaciones del catálogo de aplicaciones en la nube**  
El catálogo de aplicaciones en la nube ahora incluye una categoría de riesgo legal (además de general, seguridad y cumplimiento) para ayudarle a administrar la privacidad de los datos y el cumplimiento de la propiedad, incluida la preparación de RGPD.
Para ayudar a evaluar la preparación de RGPD de cada aplicación en la nube, la nueva categoría de riesgo contiene la instrucción de preparación de RGPD del servicio en la nube y el estado de cada control de marco de trabajo de RGPD.
Tenga en cuenta que, como parte de esta mejora, los siguientes atributos de riesgo se movieron de otra categoría de riesgo a la categoría legal:
  - DMCA
  - Propiedad de los datos
  - Directiva de retención de datos

  Además, la nueva categoría de riesgo se puntúa por separado para que pueda configurar la ponderación de la puntuación de acuerdo con sus preferencias y prioridades. Para más información, consulte [Trabajar con la puntuación de riesgo de la aplicación](risk-score.md).

- **Nueva consulta sugerida: Preparación para el RGPD**  
Hay una nueva consulta sugerida que le permite identificar las aplicaciones detectadas que están preparadas para RGPD. Dado que RGPD se ha convertido recientemente en una prioridad máxima para los administradores de seguridad, esta consulta le ayuda a identificar fácilmente las aplicaciones que están preparadas para RGPD y a mitigar la amenaza mediante la evaluación del riesgo de las que no lo están.

## <a name="cloud-app-security-release-127"></a>Notas de la versión 127 de Cloud App Security

Publicado el 8 de julio de 2018

- Ahora tiene la capacidad de ver actividades genéricas para Office 365. En el **Registro de actividad** y en las **Directivas de actividad** ahora puede filtrar las actividades de Office 365 para las actividades **sin especificar**. Revisar estas actividades le permite investigar la información sobre las actividades realizadas que todavía no están clasificadas por tipo en Cloud App Security, y puede usar estas actividades para enviar solicitudes al equipo de Cloud App Security para crear nuevos tipos de actividad basados en estas actividades.

## <a name="cloud-app-security-release-126"></a>Notas de la versión 126 de Cloud App Security

Publicado el 24 de junio de 2018

- **Disponibilidad general de Control de aplicaciones de acceso condicional**  
Control de aplicaciones de acceso condicional (proxy inverso) de Microsoft Cloud App Security ahora está disponible para todas las aplicaciones de SAML. Control de aplicaciones de acceso condicional se integra directamente con las directivas de acceso condicional de Azure AD para **supervisar y controlar las sesiones de los usuarios en tiempo real** , a la vez que permite que sean productivas. Desde la primera versión preliminar de la característica, se han realizado muchas características y mejoras, entre las que se incluyen:
  - La capacidad de crear una [directiva de acceso](access-policy-aad.md) para administrar el acceso a las mismas aplicaciones desde clientes nativos, además de crear una directiva de sesión para el tráfico del explorador.
  - El proceso de incorporación de la aplicación se optimizó para admitir aplicaciones SAML personalizadas en su organización.
  - Como parte de la red mundial de Azure, se han mejorado la integración y la interfaz para ofrecer una experiencia sin problemas para los usuarios ubicados en cualquier lugar del mundo.

- **Disponibilidad general de la inspección de contenido con el Servicio de clasificación de datos de Microsoft**  
La integración de Microsoft Cloud App Security con los Servicios de clasificación de datos de Microsoft ahora está disponible con carácter general. Esta integración le permite usar el servicio de clasificación de datos de Microsoft de forma nativa para clasificar los archivos de las aplicaciones en la nube. Para más información, consulte [Integración de los servicios de clasificación de datos de Microsoft](dcs-inspection.md). Esta característica solo está disponible actualmente en EE. UU. y Europa (excepto en Francia).

- **Informe ejecutivo de Cloud Discovery**  
Microsoft Cloud App Security está implementando gradualmente la funcionalidad para generar un informe ejecutivo en PDF de Cloud Discovery. Este informe proporciona información general sobre el uso de Shadow IT que se ha identificado en la organización, destacando las principales aplicaciones y los usuarios en uso en general y en las principales categorías, y se centra en el riesgo que Shadow IT supone en la organización. Además, el informe proporciona una lista de recomendaciones para mejorar la visibilidad y el control sobre Shadow IT en la organización. Use este informe para asegurarse de que se eliminan riesgos y amenazas potenciales y de que la organización sigue siendo segura.

- **Detección de malware**  
La funcionalidad de detección de malware se está implantando de forma gradual para **detectar automáticamente los archivos maliciosos en el almacenamiento en la nube** , con independencia del tipo de archivo. Microsoft Cloud App Security usa la inteligencia sobre amenazas de Microsoft para reconocer si ciertos archivos están asociados a ataques de malware conocidos o son potencialmente malintencionados. Para más información, consulte [Directivas de detección de anomalías](anomaly-detection-policy.md).

- **Corrección automatizada de actividades sospechosas**  
Ahora puede establecer acciones de corrección automática para una sesión sospechosa desencadenadas por las directivas de detección de anomalías. Esta mejora le permite recibir alertas al instante cuando se produce una vulneración y **aplicar acciones de gobierno automáticamente** , como suspender al usuario. Para más información, consulte [Directivas de detección de anomalías](anomaly-detection-policy.md#adp-automated-gov).

- **Evaluación de la configuración de seguridad para Azure**  
Microsoft Cloud App Security está implementando de forma gradual la funcionalidad de obtener una evaluación de la configuración de seguridad del entorno de Azure, y proporciona recomendaciones para el control de la seguridad y los valores de configuración que falten. Por ejemplo, le indicará si falta la autenticación multifactor para los usuarios administrativos. Para más información, consulte [Configuración de seguridad para Azure](security-config.md).

- **Detección automatizada de aplicaciones de OAuth de riesgo**  
Además de la investigación existente de aplicaciones de OAuth conectadas al entorno, ahora Microsoft Cloud App Security está implementando de forma gradual la funcionalidad para establecer notificaciones automatizadas que avisen cuando una aplicación de OAuth cumple determinados criterios. Por ejemplo, puede recibir automáticamente una alerta cuando haya aplicaciones que requieran un nivel de permisos elevado y que hayan sido autorizadas por más de 50 usuarios. Para obtener más información, consulte [Directivas de permisos de aplicación](app-permission-policy.md).

- **Compatibilidad con la administración de proveedores de servicios de seguridad administrada (MSSP)**  
Microsoft Cloud App Security ahora proporciona una mejor experiencia de administración para MSSP. Los usuarios externos ahora se pueden configurar como administradores y se les puede asignar cualquiera de los [roles disponibles actualmente en Microsoft Cloud App Security](manage-admins.md). Además, para permitir que MSSP proporcionen servicios en varios inquilinos de cliente, los administradores con derechos de acceso a más de un inquilino ahora pueden cambiar con facilidad los inquilinos dentro del portal. Para obtener información sobre cómo administrar administradores, consulte [Administrar los administradores](manage-admins.md).

- **Integración con la disponibilidad general de DLP externa**  
Microsoft Cloud App Security permite [aprovechar las inversiones existentes en sistemas de clasificación de terceros](icap-stunnel.md), como soluciones de prevención de pérdida de datos (DLP), y permite examinar el contenido de aplicaciones en la nube mediante las implementaciones que se ejecutan en el entorno. Para obtener más información, consulte [Integración de DLP externa](icap-stunnel.md).

## <a name="cloud-app-security-release-125"></a>Notas de la versión 125 de Cloud App Security

Fecha de publicación: 10 de junio de 2018

- **Nueva funcionalidad de investigación de los usuarios principales:**  
Microsoft Cloud App Security agregó un nuevo widget de investigación al panel que muestra los usuarios principales por el número de alertas de detección de amenazas abiertas. Este widget de investigación le permite centrar su investigación de amenazas en usuarios con el mayor número de sesiones sospechosas.

- **Compatibilidad con los cubos S3 de AWS:**  
Microsoft Cloud App Security ahora puede detectar cubos S3 de AWS y sus niveles de uso compartido. Esto proporciona alertas y visibilidad de los cubos AWS de acceso público. También le permite crear directivas basadas en cubos y aplicar una gobernanza automática. Además, hay una nueva plantilla de directiva disponible llamada **Cubos S3 de acceso público (AWS)** que puede usar para crear con facilidad una directiva que controle su almacenamiento de AWS. Para habilitar estas nuevas funcionalidades, asegúrese de actualizar sus aplicaciones conectadas de AWS agregando los nuevos permisos descritos en [Conectar AWS](connect-aws-to-microsoft-cloud-app-security.md).

- **Privilegios de administración basados en grupos de usuarios** :  
ahora puede establecer permisos administrativos en administradores de Microsoft Cloud App Security por grupo de usuarios. Por ejemplo, puede establecer un usuario específico como administrador solo para los usuarios de Alemania. Esto permitiría al usuario ver y modificar la información en Microsoft Cloud App Security solo para el grupo de usuarios “Alemania: todos los usuarios”. Para obtener más información, consulte [Administrar el acceso de administrador](manage-admins.md).

## <a name="cloud-app-security-release-124"></a>Notas de la versión 124 de Cloud App Security

Fecha de publicación: 27 de mayo de 2018

- **Evaluación de riesgo de RGPD agregada al catálogo de aplicaciones en la nube**  
Se han agregado 13 nuevos factores de riesgo a Microsoft Cloud App Security. Estos factores de riesgo siguen la lista de comprobación del marco RGPD para permitirle evaluar las aplicaciones en el catálogo de aplicaciones en la nube según la normativa de RGPD.

- **Integración con el servicio de clasificación de datos de Microsoft**  
Microsoft Cloud App Security ahora le permite usar el servicio de clasificación de datos de Microsoft de forma nativa para clasificar los archivos en sus aplicaciones en la nube.   
El servicio de clasificación de datos de Microsoft proporciona una experiencia de protección de información unificada en Office 365, Azure Information Protection y Microsoft Cloud App Security. Le permite ampliar el mismo marco de clasificación de datos a las aplicaciones en la nube de terceros protegidas por Microsoft Cloud App Security, aprovechando las decisiones que ya tomó en un número de aplicaciones incluso mayor.

- **Conectar con Microsoft Azure** (implementación gradual)  
Microsoft Cloud App Security está ampliando sus funcionalidades de supervisión de IaaS más allá de Amazon Web Services y ahora admite Microsoft Azure. Esto le permite conectarse y supervisar de manera fluida todas las suscripciones de Azure con Cloud App Security. Esta conexión le ofrece un conjunto eficaz de herramientas para proteger el entorno de Azure, como las siguientes:

  - Visibilidad en todas las actividades realizadas mediante el portal

  - Capacidad de crear directivas personalizadas para alertar sobre comportamientos no deseados, además de la capacidad de proteger automáticamente a posibles usuarios de riesgo suspendiéndoles o forzándoles a iniciar sesión de nuevo.

  - Todas las actividades de Azure están cubiertas por el motor de detección de anomalías, que generará una alerta automáticamente ante cualquier comportamiento sospechoso en Azure Portal, como un viaje imposible, actividades sospechosas masivas y la actividad desde un nuevo país.  

  Para obtener más información, consulte [Conectar Azure con Microsoft Cloud App Security](connect-azure-to-microsoft-cloud-app-security.md).

- **Implementaciones con ámbito** (implementación gradual)  
Microsoft Cloud App Security proporciona a las empresas la capacidad de determinar granularmente los usuarios a los que desean supervisar y proteger en función de la pertenencia a grupos. Esta característica le permite seleccionar usuarios cuyas actividades no se mostrarán para ninguna de las aplicaciones protegidas. La funcionalidad de supervisión con ámbito es especialmente útil para:
  - Cumplimiento: si su normativa de cumplimiento requiere que se abstenga de supervisar a usuarios de determinados países/regiones debido a la normativa local.
  - Licencias: si desea supervisar a menos usuarios para permanecer dentro de los límites de sus licencias de Microsoft Cloud App Security.
  Para más información, vea [Implementación con ámbito](scoped-deployment.md).

- **Alerta de aplicación infringida para aplicaciones detectadas**  
 Ahora tenemos una alerta integrada que le informará cada vez que se infrinja cualquiera de las aplicaciones detectadas de un inquilino. La alerta proporcionará información sobre la hora y la fecha de la infracción, los usuarios que usaron la aplicación y se vinculará a orígenes disponibles públicamente que proporcionen información sobre la infracción.

- **Nuevo servidor de correo**  
 El servidor de correo de Cloud App Security ha cambiado y usa otros intervalos de direcciones IP. Para asegurarse de que puede obtener notificaciones, agregue las nuevas direcciones IP a la lista de direcciones permitidas en el sistema antispam. En el caso de los usuarios que personalizan sus notificaciones, Microsoft Cloud App Security habilita esto automáticamente mediante MailChimp&reg;, un servicio de correo electrónico externo. Para ver la lista de direcciones IP del servidor de correo e instrucciones para habilitar el trabajo con MailChimp, consulte [Requisitos de red](network-requirements.md#mail-server) y [Configuración de correo](mail-settings.md).

## <a name="cloud-app-security-release-123"></a>Notas de la versión 123 de Cloud App Security

Fecha de publicación: 13 de mayo de 2018

- **Ámbito de la directiva de detección de anomalías** :  
ahora se pueden asignar los ámbitos correspondientes a las directivas de detección de anomalías. Esto le permite establecer cada directiva de detección de anomalías para incluir solo usuarios o grupos específicos y excluir usuarios o grupos específicos. Por ejemplo, puede establecer la actividad a partir de la detección de condados poco frecuentes para omitir un usuario específico que viaja de forma habitual.

## <a name="cloud-app-security-release-122"></a>Notas de la versión 122 de Cloud App Security

Fecha de publicación: 29 de abril de 2018

- Implementación gradual: ahora puede **establecer permisos administrativos en administradores de Microsoft Cloud App Security por aplicación**. Por ejemplo, puede establecer un usuario específico como administrador solo para G Suite. Esto permitiría al usuario ver y modificar la información en Microsoft Cloud App Security solo al relacionarse exclusivamente con G Suite. Para obtener más información, consulte [Administrar el acceso de administrador](manage-admins.md).

- Implementación gradual: **los roles de administrador de Okta ahora se pueden ver** en Microsoft Cloud App Security y están disponibles para cada rol como etiqueta en **Configuración** > **Grupos de usuarios**.

## <a name="cloud-app-security-release-121"></a>Notas de la versión 121 de Cloud App Security

Fecha de publicación: 22 de abril de 2018

- La versión preliminar pública de **Control de aplicaciones de acceso condicional (anteriormente denominado proxy de Cloud App Security)** se ha mejorado con funcionalidades que facilitan una visibilidad más profunda de diversas aplicaciones y control sobre las mismas. Ahora puede crear una directiva de sesión con un filtro *Tipo de actividad* para supervisar y bloquear diferentes actividades específicas de la aplicación. Este nuevo filtro aumenta las características de control de descarga de archivos existentes para proporcionarle un control exhaustivo de las aplicaciones de su organización y trabaja en sintonía con el acceso condicional de Azure Active Directory para proporcionar visibilidad en tiempo real y control de sesiones de usuario de riesgo (por ejemplo, sesiones con usuarios de colaboración B2B o usuarios procedentes de un dispositivo no administrado). Para obtener más información, consulte [Directivas de sesión](session-policy-aad.md).

- Implementación gradual: **se han mejorado las directivas de detección de anomalías** de Cloud App Security para incluir dos nuevos tipos de detección de amenazas: actividad de ransomware y actividad del usuario cancelado. Cloud App Security amplió sus funcionalidades de detección de ransomware con la detección de anomalías para garantizar una cobertura más completa frente a los ataques sofisticados de ransomware. Al usar nuestra experiencia en investigación de seguridad para identificar patrones de comportamiento que reflejan la actividad de ransomware, Cloud App Security garantiza una protección holística y sólida. La actividad del usuario cancelado le permite supervisar las cuentas de usuarios cancelados, cuyo aprovisionamiento puede haberse cancelado de las aplicaciones corporativas, pero en muchos casos siguen reteniendo el acceso a determinados recursos corporativos. Para obtener más información, consulte [Obtención de análisis de comportamiento y detección de anomalías instantáneos](anomaly-detection-policy.md).

## <a name="cloud-app-security-release-120"></a>Notas de la versión 120 de Cloud App Security

Fecha de publicación: 8 de abril de 2018

- En Office 365 y Azure AD, estamos implementando gradualmente la capacidad de detectar aplicaciones internas como actividades de la cuenta de usuario realizadas por las aplicaciones de Office 365 y Azure AD (tanto internas como externas). Esto le permite crear directivas que le avisarán si una aplicación realiza actividades inesperadas y no autorizadas.

- Al exportar una lista de permisos de aplicación a csv, se incluyen campos adicionales como publicador, nivel de permisos y uso de la comunidad para ayudar con el proceso de cumplimiento e investigación.

- La aplicación conectada de ServiceNow se ha mejorado para que las actividades de servicio internas dejen de registrarse como si las realizara el "invitado" y dejen de desencadenar alertas de falsos positivos. Estas actividades ahora se representan como N/D como todas las demás aplicaciones conectadas.

## <a name="cloud-app-security-release-119"></a>Notas de la versión 119 de Cloud App Security

Fecha de publicación: 18 de marzo de 2018

- En la página Intervalos de direcciones IP se incluyen direcciones IP detectadas por Cloud App Security. Entre estas se incluyen direcciones IP para servicios en la nube identificados, como Azure y Office 365, así como la fuente de inteligencia sobre amenazas que enriquece automáticamente direcciones IP con información sobre direcciones IP de riesgo conocidas.

- Si Cloud App Security intenta ejecutar una acción de gobernanza en un archivo, pero no lo consigue porque el archivo está bloqueado, ahora volverá a intentar la acción de gobernanza.

## <a name="cloud-app-security-release-118"></a>Notas de la versión 118 de Cloud App Security

Fecha de publicación: 4 de marzo de 2018

- Ahora puede aprovechar las funcionalidades de supervisión y detección de shadow IT de Microsoft Cloud App Security en sus propias aplicaciones personalizadas de propietario. La nueva capacidad de agregar aplicaciones personalizadas a Cloud Discovery le permite supervisar el uso de la aplicación y recibir avisos sobre los cambios en el patrón de uso. Para obtener más información, consulte el artículo sobre cómo [proteger las aplicaciones personalizadas](cloud-discovery-custom-apps.md). Esta característica se está implantando gradualmente.

- Se rediseñaron las páginas **Configuración** del portal de Cloud App Security. El nuevo diseño consolida todas las páginas de configuración, proporciona la funcionalidad de búsqueda y un diseño mejorado.

- Cloud Discovery ahora admite Barracuda F-Series Firewalls y Barracuda F-Series Firewall Web Log Streaming.

- La funcionalidad de búsqueda de las páginas Usuario y Dirección IP ahora habilita Autocompletar para que pueda encontrar lo que busca con mayor facilidad.

- Ahora puede realizar acciones en masa en las páginas de configuración de exclusión de entidades y direcciones IP. Esto le permitirá seleccionar con más facilidad varios usuarios o direcciones IP y evitar que se supervisen como parte de Cloud Discovery en su organización.

## <a name="cloud-app-security-release-117"></a>Notas de la versión 117 de Cloud App Security

Publicado el 20 de febrero de 2018

- La mejor integración de Cloud App Security con Azure Information Protection ahora le permite proteger archivos en G Suite. Esta característica de versión preliminar pública permite examinar y clasificar archivos en G Suite y aplicar de forma automática las etiquetas de protección de Azure Information Protection. Para más información, consulte [Integración de Azure Information Protection](azip-integration.md).

- Ahora, Cloud Discovery es compatible con [Digital Arts i-FILTER](https://www.daj.jp/en/products/if/).

- La tabla de agentes SIEM ahora incluye más detalles para facilitar la administración.

## <a name="cloud-app-security-release-116"></a>Notas de la versión 116 de Cloud App Security

Fecha de publicación: 4 de febrero de 2018

- La directiva de detección de anomalías de Cloud App Security se ha mejorado con nuevas **detecciones basadas en los escenarios** , incluidos un viaje imposible, la actividad de una dirección IP sospechosa y varios intentos incorrectos de inicio de sesión. Las nuevas directivas se habilitan automáticamente, proporcionando una detección de amenazas predefinida en su entorno en la nube. Además, las nuevas directivas exponen más datos del motor de detección de Cloud App Security para ayudarle a acelerar el proceso de investigación e incluir amenazas en curso. Para obtener más información, consulte [Obtención de análisis de comportamiento y detección de anomalías instantáneos](anomaly-detection-policy.md).

- Implementación gradual: Cloud App Security ahora se correlaciona entre los usuarios y sus cuentas en las aplicaciones SaaS. Esto le permite investigar fácilmente todas las actividades para un usuario, en todas sus diferentes aplicaciones SaaS correlacionadas, sin importar la aplicación o cuenta que usaron.

- Implementación gradual: Cloud App Security ahora admite varias instancias de la misma aplicación conectada. Si tiene varias instancias de, por ejemplo, Salesforce (una para ventas y otra para marketing), podrá conectarlas a Cloud App Security y administrarlas desde la misma consola para crear directivas granulares y una investigación más profunda.

- Los analizadores de Cloud Discovery ahora admiten dos formatos de punto de control, XML y KPC.

## <a name="cloud-app-security-release-115"></a>Notas de la versión 115 de Cloud App Security

Fecha de publicación: 21 de enero de 2018

- Esta versión proporciona una experiencia mejorada al seleccionar carpetas específicas en las directivas de archivos. Ahora puede ver y seleccionar con facilidad varias carpetas para incluirlas en una directiva.
- En la página **Aplicaciones detectadas** :
  - la característica de etiquetado masivo le permite aplicar etiquetas personalizadas (además de las etiquetas autorizadas y no autorizadas).
  - Al **generar un informe de direcciones IP** o **generar un informe de usuarios** , los informes exportados ahora incluyen la información sobre si el tráfico tenía su origen en aplicaciones autorizadas o no autorizadas.
- Ahora puede solicitar un nuevo conector de aplicaciones de API del equipo de Microsoft Cloud App Security directamente en el portal, en la página **Conectar una aplicación**.

## <a name="cloud-app-security-release-114"></a>Notas de la versión 114 de Cloud App Security

Fecha de publicación: 7 de enero de 2018

- A partir de la versión 114, implementamos gradualmente la capacidad de crear y guardar consultas personalizadas en las páginas Registro de actividad y Aplicaciones detectadas. Las consultas personalizadas permiten crear plantillas de filtro que se pueden reutilizar para una investigación en profundidad. Además, las **consultas sugeridas** se han agregado para proporcionar plantillas de investigación predefinidas para filtrar las actividades y aplicaciones detectadas. Las **consultas sugeridas** incluyen filtros personalizados para identificar riesgos como actividades de suplantación, actividades del administrador, aplicaciones de almacenamiento en la nube no compatibles de riesgo, aplicaciones empresariales con cifrado débil y riesgos de seguridad. Puede usar las **consultas sugeridas** como punto de partida, modificarlas como mejor le parezca y, a continuación, guardarlas como nueva consulta. Para obtener más información, consulte [Consultas y filtros de actividad](activity-filters-queries.md) y [Consultas y filtros de aplicaciones detectadas](discovered-app-queries.md).

- Ahora puede comprobar el estado del servicio de Cloud App Security yendo a [status.cloudappsecurity.com](https://status.cloudappsecurity.com) o directamente desde dentro del portal haciendo clic en **Ayuda**>**Estado del sistema**.

## <a name="see-also"></a>Consulte también

Para obtener una descripción de las versiones anteriores a las enumeradas aquí, consulte [Versiones anteriores de Microsoft Cloud App Security](release-note-archive.md).

[!INCLUDE [Open support ticket](includes/support.md)]