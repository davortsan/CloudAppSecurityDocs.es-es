---
title: Novedades de Cloud App Security
description: Este artículo se actualiza con frecuencia para informarle de las novedades de la versión más reciente de Cloud App Security.
ms.date: 10/25/2020
ms.topic: overview
ms.openlocfilehash: a98d6305b20b7cca12754edc8804781d20dd0f4e
ms.sourcegitcommit: d87372b47ca98e942c2bf94032a6a61902627d69
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/30/2020
ms.locfileid: "96315487"
---
# <a name="whats-new-with-microsoft-cloud-app-security"></a>Novedades de Microsoft Cloud App Security

*Se aplica a: Microsoft Cloud App Security*

Este artículo se actualiza con frecuencia para informarle de las novedades de la versión más reciente de Cloud App Security.

Fuente RSS: reciba notificaciones cuando esta página se actualice copiando y pegando la siguiente dirección URL en su lector de fuentes: `https://docs.microsoft.com/api/search/rss?search=%22This+article+is+updated+frequently+to+let+you+know+what%27s+new+in+the+latest+release+of+Cloud+App+Security%22&locale=en-us`

> [!IMPORTANT]
>
> Los nombres de productos de protección contra amenazas de Microsoft están cambiando. Obtenga más información sobre esta y otras actualizaciones [en este artículo](https://www.microsoft.com/security/blog/?p=91813). Usaremos los nombres nuevos en futuras versiones.

## <a name="cloud-app-security-release-187-and-188"></a>Versiones 187 y 188 de Cloud App Security

Fecha de publicación: 22 de noviembre de 2020

- **Nueva integración de Shadow IT con Menlo Security**  
Hemos agregado integración nativa con Menlo Security, lo que ofrece visibilidad de Shadow IT sobre el uso de las aplicaciones y control de acceso a estas. Para más información, consulte [Integración de Cloud App Security con Menlo Security](menlo-integration.md).

- **Nuevo analizador de registro WatchGuard de Cloud Discovery.**  
Cloud Discovery de Cloud App Security analiza una amplia gama de registros de tráfico para clasificar y puntuar aplicaciones. Ahora Cloud Discovery incluye un analizador de registros integrado para admitir el formato WatchGuard. Para ver una lista de los analizadores de registros admitidos, vea [Firewalls y proxies admitidos](set-up-cloud-discovery.md#supported-firewalls-and-proxies).

- **Nuevo permiso para el rol de administrador global de Cloud Discovery**  
Cloud App Security ahora permite a los usuarios con el rol de administrador global de Cloud Discovery crear tokens de API y usar todas las API relacionadas con Cloud Discovery. Para más información sobre el rol, consulte el artículo sobre los [roles de administrador de Cloud App Security integrados](manage-admins.md#built-in-cloud-app-security-admin-roles).

- **Control deslizante de sensibilidad mejorada: Viaje imposible**  
Hemos actualizado el control deslizante de sensibilidad para viajes imposibles con el fin de configurar diferentes niveles de sensibilidad para diferentes ámbitos de usuario, lo que permite un mayor control sobre la fidelidad de las alertas para los ámbitos de usuario. Por ejemplo, puede definir un nivel de confidencialidad más alto para los administradores que para otros usuarios de la organización. Para obtener más información acerca de esta directiva de detección de anomalías, consulte [Viaje imposible](anomaly-detection-policy.md#impossible-travel).

- **Sufijo URL de proxy mejorado para controles de sesión (lanzamiento gradual)**  
El 7 de junio de 2020 se ha iniciado el lanzamiento gradual de los controles de sesión de proxy mejorados para usar un sufijo unificado que no incluye regiones con nombre. Por ejemplo, los usuarios verán el sufijo `<AppName>.mcas.ms` en lugar de `<AppName>.<Region>.cas.ms`. Si, por rutina, bloquea los dominios de las puertas de enlace o los dispositivos de red, asegúrese de crear una lista de permitidos con todos los dominios enumerados en [Controles de acceso y sesión](network-requirements.md#access-and-session-controls).

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
Cloud App Security proporciona la capacidad de identificar máquinas de riesgo como parte de la investigación de detección de TI en la sombra. Ahora, hemos agregado el **nivel de máquinas de riesgo** de la Protección contra amenazas avanzada de Microsoft Defender en la página de **máquinas**, lo que aportará más contexto a los analistas que investiguen las máquinas de su organización. Para más información, consulte [Investigación de dispositivos de Cloud App Security](mde-integration.md#investigate-devices-in-cloud-app-security).

- **Nueva característica: Autoservicio para la deshabilitación de conectores de aplicaciones (lanzamiento gradual)**  
Hemos agregado la capacidad de deshabilitar los conectores de aplicaciones directamente en Cloud App Security. Para obtener más información, consulte [Deshabilitación de conectores de aplicaciones](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md#disable-app-connectors).

## <a name="cloud-app-security-release-177"></a>Notas de la versión 177 de Cloud App Security

Fecha de publicación: 14 de junio de 2020

- **Nueva detección de malware en tiempo real (versión preliminar, lanzamiento gradual)**  
Hemos ampliado los controles de sesión para detectar malware potencial con la inteligencia sobre amenazas de Microsoft al cargar o descargar archivos. La nueva detección ya está disponible de serie y se puede configurar para que bloquee automáticamente los archivos identificados como posible malware. Para obtener más información, vea [Bloquear malware al cargar](session-policy-aad.md#block-malware-on-upload).

- **Nueva compatibilidad de los tokens de acceso con los controles de acceso y de sesión**  
Se ha agregado la posibilidad de tratar las solicitudes de tokens de acceso y código como inicios de sesión al incorporar aplicaciones a los controles de acceso y de sesión. Para usar tokens, haga clic en el icono de engranaje de configuración, seleccione **Control de aplicaciones de acceso condicional**, edite la aplicación correspondiente (menú de tres puntos > **Editar aplicación**), seleccione **Tratar solicitudes de código y tokens de acceso como inicios de sesión de la aplicación** y haga clic en **Guardar**. Para obtener más información sobre la incorporación de aplicaciones, vea [Incorporación e implementación para cualquier aplicación](proxy-deployment-any-app.md) e [Implementación para aplicaciones destacadas](proxy-deployment-aad.md).

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
Hemos ampliado la funcionalidad actual para detectar un comportamiento de riesgo. La nueva detección ya está disponible para su uso y se habilita automáticamente para avisarle cuando se identifica un intento de inicio de sesión inusual con errores. Los intentos inusuales de inicio de sesión con errores pueden ser un indicio de un posible ataque por fuerza bruta de *rociado de contraseñas* (también conocido como el método *lento y silencioso*). Esta detección afecta a la [clasificación de prioridad de la investigación](tutorial-ueba.md) general del usuario.

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
Ahora puede controlar la gravedad de las alertas de Azure AD Identity Protection que se introducen en Cloud App Security. Además, si aún no ha habilitado la detección del **inicio de sesión de riesgo de Azure AD**, la detección se habilitará automáticamente para ingerir alertas de gravedad alta. Para más información, consulte [Integración de Azure Active Directory Identity Protection](aadip-integration.md).

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

## <a name="see-also"></a>Consulte también

Para obtener una descripción de las versiones anteriores a las enumeradas aquí, consulte [Versiones anteriores de Microsoft Cloud App Security](release-note-archive.md).

[!INCLUDE [Open support ticket](includes/support.md)]