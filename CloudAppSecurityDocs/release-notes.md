---
title: Novedades de Cloud App Security
description: Este artículo se actualiza con frecuencia para informarle de las novedades de la versión más reciente de Cloud App Security.
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 12/08/2019
ms.topic: overview
ms.service: cloud-app-security
ms.collection: M365-security-compliance
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 8f96792a57c2a6306a61271cb315491687c07a20
ms.sourcegitcommit: 362ec5187cb13f152d240b75ed1ecebb5236b0ee
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/15/2019
ms.locfileid: "75033397"
---
# <a name="whats-new-with-microsoft-cloud-app-security"></a>Novedades de Microsoft Cloud App Security

*Se aplica a: Microsoft Cloud App Security*

Este artículo se actualiza con frecuencia para informarle de las novedades de la versión más reciente de Cloud App Security.

Fuente RSS: Reciba una notificación cuando se actualice esta página. Para ello, copie y pegue la siguiente dirección URL en su lector de fuentes: `https://docs.microsoft.com/api/search/rss?search=%22This+article+is+updated+frequently+to+let+you+know+what%27s+new+in+the+latest+release+of+Cloud+App+Security%22&locale=en-us`

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
Hemos puesto en marcha la capacidad de los administradores de personalizar la página de aterrizaje que ven los usuarios al navegar a una aplicación a la que se aplica una directiva de sesión. Ahora puede mostrar el logotipo de su organización y personalizar el mensaje que se muestra. Para iniciar la personalización, vaya a la página de **configuración** y, en la opción de **control de aplicaciones de acceso a la nube**, seleccione **Supervisión de usuarios**.

- **Nuevas detecciones**  

  - **Cambios en el servicio de registro sospechoso de AWS (versión preliminar)** : Le avisa cuando un usuario realiza cambios en el servicio de registro de CloudTrail. Por ejemplo, los atacantes suelen desactivar la auditoría en CloudTrail para ocultar las huellas de su ataque.

  - **Varias actividades de creación de máquinas virtuales**: Le avisa cuando un usuario realiza un número inusual de actividades de creación de máquinas virtuales, en comparación con la línea de base aprendida. Ahora se aplica a AWS.

## <a name="cloud-app-security-release-159"></a>Notas de la versión 159 de Cloud App Security

Publicado el 6 de octubre de 2019

- **Nuevo analizador de registros de ContentKeeper de Cloud Discovery**  
Cloud Discovery de Cloud App Security analiza una amplia gama de registros de tráfico para clasificar y puntuar aplicaciones. Ahora Cloud Discovery incluye un analizador de registros integrado para admitir los formatos de registro de ContentKeeper. Para ver una lista de los analizadores de registros admitidos, vea [Firewalls y proxies admitidos](set-up-cloud-discovery.md#supported-firewalls-and-proxies).

- **Nuevas detecciones**  
Las siguientes nuevas directivas de detección de anomalías vienen integradas y habilitadas automáticamente:

  - **Actividad de eliminación de correos electrónicos sospechosos (versión preliminar)**  
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

- **Nueva detección: Uso compartido sospechoso en Microsoft Power BI (versión preliminar)**  
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
Nos complace anunciar que expandimos la compatibilidad con el Control de aplicaciones de acceso condicional a cualquier aplicación web, además de la amplia compatibilidad que ya ofrecemos para las [aplicaciones destacadas](proxy-intro-aad.md). Esta nueva funcionalidad permite implementar cualquier aplicación web para trabajar con directivas de sesión y acceso, con lo que se habilita la supervisión y el control eficaces en tiempo real. Por ejemplo, puede proteger las descargas con etiquetas de Azure Information Protection y bloquear la carga de documentos confidenciales, brindando auditoría, entre muchas otras acciones.
- **Auditoría de la actividad del portal**  
Cloud App Security hace una auditoría de toda la actividad del administrador del portal para ofrecer una supervisión e investigación integrales de las actividades realizadas. Ahora también puede exportar hasta 90 días de actividades para realizar más investigación y análisis como, por ejemplo, realizar una auditoría a un administrador que investiga a un usuario específico o ver alertas específicas. Para exportar el registro, vaya a la página de configuración **Administrar el acceso de administrador**.
- **Cierre de sesión personalizado desde el portal de Cloud App Security**  
Ahora puede configurar el cierre de sesión automático de las sesiones del administrador en el portal que están inactivas por más tiempo que un período especificado.

## <a name="cloud-app-security-release-151"></a>Versión 151 de Cloud App Security

Publicada el 9 de junio de 2019

- **UEBA híbrido: integración nativa con Azure ATP (versión preliminar)**  
Cloud App Security ahora se integra de manera nativa con Azure ATP para proporcionar una vista única de las actividades de identidad en ambas aplicaciones en la nube y la red local. Para más información, consulte [Integración de Azure Advanced Threat Protection](aatp-integration.md).
- **Mejoras de UEBA**  
Para ayudarlo a identificar las amenazas que están por debajo del radar, Cloud App Security ahora usa la generación de perfiles única para brindar puntuaciones de riesgo a actividades y alertas individuales. Las puntuaciones de riesgo se pueden usar para identificar las actividades que no son suficientemente sospechosas como para desencadenar las alertas. Sin embargo, al agregar las puntuaciones de riesgo a la **puntuación de prioridad de investigación** de un usuario, Cloud App Security ayuda a identificar el comportamiento de riesgo y a centrar la investigación. Estas funcionalidades nuevas ahora están disponibles en la página de usuario rediseñada.
- **Factor de riesgo nuevo agregado al Catálogo de aplicaciones en la nube**  
El Catálogo de aplicaciones en la nube ahora incluye el factor de riesgo del plan de recuperación ante desastres para permitirle evaluar las aplicaciones en el Catálogo de aplicaciones en la nube para permitir la continuidad empresarial.
- **Disponibilidad general del conector de Microsoft Flow**  
Desde la versión preliminar de la compatibilidad de Microsoft Cloud App Security con el conector de Microsoft Flow el año pasado, ahora el conector está disponible con carácter general.
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
Ahora, al exportar las alertas a CSV desde la página **Alertas**, los resultados incluyen la fecha de la resolución o del descarte de la alerta.

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
Al conectar Office 365 con Microsoft Cloud App Security, ahora tiene control sobre qué cargas de trabajo desea conectar. Por ejemplo, los clientes interesados solo en conectar Office 365 para la supervisión de la actividad ahora pueden hacerlo durante el proceso de conexión, o mediante la edición de un conector de Office 365 existente. Como parte de este cambio, OneDrive y SharePoint Online ya no se mostrarán como conectores independientes, sino que se incluirán en el conector de Office 365 como la carga de trabajo de _archivos de Office 365_. Los clientes con un conector de Office 365 existente no se ven afectados por este cambio.

- **Compatibilidad mejorada con Teams**  
Ahora puede supervisar y bloquear el envío de mensajes en la aplicación web de Teams en tiempo real, mediante la configuración de una directiva de sesión basada en contenido confidencial.

## <a name="cloud-app-security-release-147"></a>Notas de la versión 147 de Cloud App Security

Fecha de publicación: 14 de abril de 2019

- **Nuevos analizadores de registro de Cloud Discovery**  
Cloud Discovery de Cloud App Security ahora incluye un analizador de registros integrado para admitir el formato de registro LEEF de Palo Alto.

- **Actualizaciones de directivas de sesión**  
  - **Método de inspección de contenido adicional para las directivas de sesión**:  Al establecer una directiva de sesión, ahora tiene la opción de elegir el servicio de clasificación de datos como método de inspección de contenido de los archivos. El servicio de clasificación de datos ofrece al usuario un amplio rango de tipos de datos confidenciales integrados para utilizarlos en la identificación de información confidencial.
  - **Control mejorado de los permisos de archivo en las directivas de sesión**:  Al crear una directiva de sesión para controlar las descargas mediante Cloud App Security, ahora puede aplicar automáticamente permisos por usuario, como por ejemplo de solo lectura, a los documentos una vez descargados desde las aplicaciones en la nube. Esto proporciona un nivel mucho mayor de flexibilidad y la capacidad de proteger la información más allá de las etiquetas corporativas configuradas previamente.
  - **Control de descarga de archivos grandes**:  Cuando se habilita la inspección de contenido en las directivas de sesión, ahora puede controlar lo que sucede cuando un usuario intenta descargar un archivo muy grande. Si el archivo es demasiado grande para analizarlo durante la descarga, puede elegir si desea bloquear o permitir dicho análisis.

## <a name="cloud-app-security-release-146"></a>Notas de la versión 146 de Cloud App Security

Fecha de publicación: 31 de marzo de 2019

- **Mejora de viaje imposible**  
Se ha mejorado la detección de viajes imposibles con compatibilidad específica para los países vecinos.
- **Compatibilidad adicional de atributos para el analizador genérico de CEF**  
La compatibilidad del analizador de registros de Cloud Discovery para el formato genérico CEF se ha mejorado para admitir atributos adicionales.
- **Acceso limitado a los informes de Cloud Discovery**  
Además del rol de administrador de Discovery, ahora puede limitar el acceso a informes específicos de Discovery. Esta mejora le permite configurar privilegios para los datos de sitios y unidades de negocio específicos.
- **Compatibilidad con nuevos roles: Lector global**  
Microsoft Cloud App Security ahora admite el rol de lector global de Azure AD. El lector global tiene acceso de solo lectura a todos los aspectos de Microsoft Cloud App Security, pero no puede cambiar ninguna configuración ni realizar ninguna acción.

## <a name="cloud-app-security-release-145"></a>Cloud App Security versión 145

Fecha de publicación: 17 de marzo de 2019

- **Integración con Microsoft Defender ATP disponible para público general**  
El año pasado anunciamos la [integración con Protección contra amenazas avanzada de Windows Defender](https://techcommunity.microsoft.com/t5/Enterprise-Mobility-Security/Microsoft-Cloud-App-Security-and-Windows-Defender-ATP-better/ba-p/263265) que mejora Shadow IT Discovery en la organización y la extiende más allá de la red corporativa. [Habilitado con un solo clic](https://query.prod.cms.rt.microsoft.com/cms/api/am/binary/RWtNmG), nos complace anunciar que esta integración única ya tiene el carácter de disponibilidad general.
- **Soporte técnico de Dynamics 365 CRM**  
Cloud App Security agregó control y supervisión en tiempo real para Dynamics 365 CRM, lo que permite proteger las aplicaciones empresariales y el contenido confidencial almacenado en estas aplicaciones. Para más información sobre lo que se puede hacer con Dynamics 365 CRM, consulte [este artículo](proxy-intro-aad.md#how-it-works).

## <a name="cloud-app-security-release-144"></a>Notas de la versión 144 de Cloud App Security

Fecha de publicación: 3 de marzo de 2019

- **Investigación unificada de SecOps para entornos híbridos**  
Como muchas organizaciones tienen entornos híbridos, los ataques empiezan en la nube y se dirigen al entorno local, lo que significa que los equipos de SecOps necesitan investigar estos ataques desde distintos lugares. Mediante la combinación de señales de orígenes locales y de la nube, como Microsoft Cloud App Security, Azure ATP y Azure AD Identity Protection, Microsoft fortalece a los analistas de seguridad al proporcionarles información de usuario e identidad unificada, en una sola consola, con lo que se termina la necesidad de alternar entre distintas soluciones de seguridad. Con esto, los equipos de SecOps tienen más tiempo y cuentan con la información correcta para tomar mejores decisiones y corregir activamente los riesgos y amenazas reales a la identidad. Para más información, consulte [Investigación unificada de SecOps para entornos híbridos](https://techcommunity.microsoft.com/t5/Enterprise-Mobility-Security/Unified-SecOps-Investigation-for-Hybrid-Environments/ba-p/360850).

- **Funcionalidades de espacio aislado para la detección de malware** (implementación gradual)  
Las funcionalidades de detección de malware de Cloud App Security se están expandiendo para incluir la capacidad de identificar malware de día cero a través de la tecnología avanzada de espacio aislado.  
Como parte de esta funcionalidad, Cloud App Security identifica automáticamente los archivos sospechosos y los detona para busca algún comportamiento sospechoso e indicadores de que se trata de un archivo malintencionado (malware).
Como parte de este cambio, las directivas de detección de malware ahora incluyen el campo Tipo de detección que le permite filtrar según la inteligencia de la amenaza, además de espacio aislado.

- **Actualizaciones del acceso condicional**  
El Control de aplicaciones de acceso condicional agregó la capacidad de supervisar y bloquear estas actividades:
  - Cargas de archivo en cualquier aplicación, que permite escenarios en los que se impide la carga de extensiones conocidas de malware y garantiza a los usuarios la protección de sus archivos con AIP antes de la carga.
  - Copiar y pegar en cualquier aplicación, que redondea los sólidos controles de filtración de datos que ya incluían el control de descargas, impresión y actividades personalizadas, como el uso compartido.
  - Enviar mensajes, que garantiza que los datos de información de identificación personal como contraseñas no se compartan en herramientas de colaboración populares, como Slack, Salesforce y Workplace de Facebook.
  - Las directivas de sesión ahora incluyen plantillas integradas para permitir que la organización habilite sin problemas la supervisión popular en tiempo real y controlen las aplicaciones autorizadas, como **Bloquear carga según la inspección de contenido en tiempo real**.

## <a name="cloud-app-security-release-143"></a>Notas de la versión 143 de Cloud App Security

Fecha de publicación: 17 de febrero de 2019

- **Implementación con ámbito para las instancias de la aplicación**  
La implementación con ámbito ahora puede configurarse en el nivel de instancia de la aplicación, lo que permite mayor granularidad y control.
- **Mejoras de roles**  
  - Ahora se admiten los roles de administrador de datos y operador de seguridad de Office 365 en Cloud App Security. El rol de administrador de datos permite a los usuarios administrar todo lo que se relaciona con archivos, así como ver los informes de Cloud Discovery. Los operadores de seguridad tienen permiso para administrar las alertas y ver la configuración de directivas.
  - El rol de lector de seguridad ahora tiene la capacidad para configurar al agente de SIEM, lo que permite un mejor de ámbito de permiso.

- **Soporte de Microsoft Flow**  
Cloud App Security ahora supervisa las actividades del usuario en Microsoft Flow. Las actividades admitidas son las actividades notificadas por Flow en el registro de auditoría de Office 365.

- **Agrupación de entidades de alertas**  
La página **Alerta** ahora agrupa las entidades relacionadas que están involucradas en la alerta para ayudar en la investigación.

## <a name="cloud-app-security-release-142"></a>Notas de la versión 142 de Cloud App Security

Fecha de publicación: 3 de febrero de 2019

- **Configuración de la directiva de sesión en Azure AD**  
Ahora puede configurar las directivas de sesión para supervisar usuarios o bloquear descargas en tiempo real directamente en el acceso condicional de Azure AD. Puede seguir configurando las directivas de sesión avanzadas directamente en Cloud App Security. Para ver una guía paso a paso de esta implementación, consulte [Implementación del control de aplicaciones de acceso condicional para aplicaciones de Azure AD](proxy-deployment-aad.md).

- **Consultas sugeridas y guardadas para aplicaciones de OAuth**  
Se han agregado consultas sugeridas a la página Aplicaciones de OAuth para proporcionar plantillas de investigación predeterminadas con el fin de filtrar las aplicaciones de OAuth. Las consultas sugeridas incluyen filtros personalizados para identificar las aplicaciones de riesgo, como las que autorizan los administradores. Las consultas guardadas permiten guardar las consultas personalizadas para usarlas en un futuro; son similares a las consultas guardadas disponibles actualmente en las páginas Registro de actividad y Detección.

- **Configuración predeterminada de auditoría de Office 365**  
Si desea habilitar la supervisión de actividades de Office 365 en Cloud App Security, ahora debe habilitar la auditoría en el [Centro de seguridad y cumplimiento de Office](/office365/securitycompliance/turn-audit-log-search-on-or-off#turn-on-audit-log-search) como resultado de un [cambio en la auditoría de Office 365](/office/office-365-management-api/office-365-management-activity-api-faq#what-happens-if-i-disable-auditing-for-my-office-365-organization-will-i-still-get-events-via-the-management-activity-api). Este cambio solo debe realizarse si aún no ha habilitado la supervisión de actividades de Office 365 en Cloud App Security.

- **Mayor compatibilidad con Box**  
Cloud App Security ahora admite dos nuevas acciones de gobernanza para Box:

  - **Expiración del vínculo compartido**: esta acción de gobernanza proporciona la opción de establecer una fecha de expiración para un vínculo compartido después de la cual dejará de estar activo.

  - **Cambio del nivel de acceso del vínculo compartido**: esta acción de gobernanza ofrece la posibilidad de cambiar el nivel de acceso del vínculo compartido entre la empresa únicamente, solo colaboradores y público.

- **Compatibilidad con varias ubicaciones en OneDrive**  
Ahora, Cloud App Security proporciona visibilidad completa de los archivos de OneDrive, incluso si están dispersos en varias ubicaciones geográficas. Ahora los archivos localizados en las ubicaciones adicionales, además de en la principal, estarán protegidos.

- **Mejora de la navegación por el portal**  
El portal de Cloud App Security se ha mejorado para optimizar la navegación y para que Cloud App Security tenga un aspecto más similar a otros servicios de seguridad de Microsoft, para así facilitar su uso.

## <a name="cloud-app-security-release-141"></a>Notas de la versión 141 de Cloud App Security

Fecha de publicación: 20 de enero de 2019

- **Mejoras de evaluación de riesgos en la nube**  
  - Se ha mejorado la evaluación de riesgos de las aplicaciones en la nube con dos nuevas experiencias.
    - Un nuevo atributo **Tipo de datos** evalúa qué tipo de contenido pueden cargar los usuarios a la aplicación. Puede utilizar este atributo para evaluar una aplicación según la sensibilidad de cada tipo de datos de la organización.
    - Para obtener una información general más completa de los riesgos de una aplicación, puede pasar fácilmente de la evaluación de riesgos de la aplicación a la evaluación de riesgos de la empresa de hospedaje haciendo clic en el atributo **Empresa de hospedaje**.

- **Contexto de archivo mejorado para la investigación de alertas de detección de anomalías**  
  - Se mejoró la investigación de detección de anomalías para permitirle ver información adicional asociada con los archivos que intervienen en una alerta. Cuando se desencadenan las alertas para alertas de actividad inusual relacionadas con archivos (descargar, compartir, eliminar), esta exploración en profundidad está disponible. Por ejemplo, si la mayoría de los archivos afectados proceden de la misma carpeta o comparten la misma extensión de archivo, verá esta información en la sección de riesgos adicionales de la alerta.

- **Consultas sobre la investigación de archivos**  
  - La capacidad de Cloud App Security para crear y guardar consultas personalizadas se amplió a la página **Archivos**. Las consultas de la página **Archivo** le permiten crear plantillas de consulta que se pueden volver a usar para investigar en profundidad.

## <a name="cloud-app-security-release-139-140"></a>Notas de la versión 139, 140 de Cloud App Security

Fecha de publicación: 6 de enero de 2019

- **Cambio en la detección de los archivos**  
Los archivos compartidos con todos los usuarios de SharePoint y OneDrive ahora se consideran **internos** [debido a los cambios realizados en SharePoint y OneDrive](https://support.microsoft.com/help/4089534/how-to-grant-the-everyone-claim-to-external-users-in-office-365). Así pues, si se detecta un archivo que se comparte con todos los usuarios, ahora se tratará como interno. Esto afecta al modo de controlar el archivo mediante el uso de directivas y su visualización en la página de archivos.

- **Cambio en la supervisión de los archivos**  
El comportamiento predeterminado de supervisión de los archivos ha cambiado para los clientes nuevos e inactivos. Ahora deberá activar la supervisión de los archivos para habilitar la función, a través de **Configuración** > **Archivos**. Los clientes activos existentes no se verán afectados por este cambio.

- **Ajuste avanzado para directivas de detección de anomalías**  
Ahora puede influir en el motor de detección de anomalías con el fin de suprimir o exponer alertas de acuerdo con sus preferencias.
  - En la directiva correspondiente a un viaje imposible, puede establecer el control deslizante del nivel de confidencialidad para determinar el nivel de comportamiento anómalo necesario para que se desencadene una alerta.
  - También puede configurar si las alertas de actividad desde un país no habitual, direcciones IP anónimas, direcciones IP sospechosas y viaje imposible deben analizar los inicios de sesión correctos y los erróneos, o bien solo los correctos.

- **Compatibilidad con varias cadenas de confianza**  
Control de aplicaciones de acceso condicional ahora permite agregar y usar varios certificados raíz o intermedios de confianza como forma de administración de dispositivos.

- **Nuevo rol de Cloud Discovery** (implementación gradual)  
Cloud App Security ahora incluye un nuevo rol de administrador para los usuarios de Cloud Discovery. Este rol se puede usar para limitar el acceso de un usuario administrador a solo la configuración y los datos de Cloud Discovery en el portal de Cloud App Security.

- **Compatibilidad con etiquetas unificadas de Microsoft Information Protection** (implementación gradual)  
Cloud App Security ahora admite las etiquetas unificadas de Microsoft Information Protection. En el caso de los clientes que ya [hayan migrado sus etiquetas de clasificación del Centro de seguridad y cumplimiento de Office 365](/azure/information-protection/configure-policy-migrate-labels), Cloud App Security las identificará y trabajará con ellas, tal como se describe en [Integración de Azure Information Protection](azip-integration.md).

**Compatibilidad con el etiquetado de archivos PDF** (implementación gradual)  
En el caso de los clientes que usen las etiquetas unificadas, Cloud App Security ahora admite el etiquetado automático para archivos PDF.

## <a name="cloud-app-security-release-138"></a>Notas de la versión 138 de Cloud App Security

Publicada el 9 de diciembre de 2018

- **Carga automática del registro con Docker en Windows**  
Cloud App Security ahora admite la carga automática del registro para Windows 10 (Fall Creators Update) y Windows Server, versión 1709 y posteriores, mediante un Docker para Windows. Para más información e instrucciones sobre cómo se puede configurar este, consulte [Docker en Windows local](discovery-docker-windows.md).

- Cloud App Security se integra con [Microsoft Flow](/flow/getting-started) para proporcionar cuadernos de estrategias de automatización y orquestación de alertas personalizadas. Para obtener más información e instrucciones de integración, consulte [Integración con Microsoft Flow](flow-integration.md).

## <a name="cloud-app-security-release-137"></a>Notas de la versión 137 de Cloud App Security

Publicado el 25 de noviembre de 2018

- **Se ha agregado compatibilidad para Dynamics**  
Cloud App Security ahora incluye compatibilidad para las actividades de Microsoft Dynamics que se admiten en el registro de auditoría de Office 365.

- **Análisis de contenido cifrado (versión preliminar)**  
Cloud App Security ahora permite analizar el contenido protegido por etiquetas de protección de Azure Information Protection. Esto le permitirá encontrar contenido confidencial, incluso en los archivos que ya se han cifrado con Azure Information Protection.

- **Aviso: nueva terminología**  
Se cambió el nombre de las capacidades de los permisos de aplicación para mayor claridad: ahora se denomina **aplicaciones OAuth**.

## <a name="cloud-app-security-release-136"></a>Notas de la versión 136 de Cloud App Security

Publicado el 11 de noviembre de 2018

- **Actualizaciones de Cloud Discovery**  
El analizador de registros personalizado se ha mejorado para admitir formatos de los registros de tráfico web adicionales y más complejos. Como parte de estas mejoras los usuarios ahora pueden introducir encabezados personalizados para los archivos de registro CSV sin encabezado, usar delimitadores especiales para los archivos de pares clave-valor, procesar el formato de archivo Syslog y mucho más.

- **Nuevas directivas de detección de anomalías**  
Reglas de manipulación sospechosa de la bandeja de entrada: esta directiva crea perfiles de su entorno y activa alertas cuando se establecen reglas sospechosas que eliminan o mueven los mensajes o las carpetas en la Bandeja de entrada del usuario. Esto puede indicar que la cuenta del usuario está en peligro, que se están ocultando mensajes intencionadamente y que el buzón se está usando para enviar correo no deseado o malware en la organización.

- **Compatibilidad con grupos de directivas de permisos de aplicación**  
Cloud App Security ahora le permite definir directivas de permisos de aplicación de forma más detallada, según la pertenencia a grupos de los usuarios que autorizaron las aplicaciones. Por ejemplo, un administrador puede decidir establecer una directiva que revoca aplicaciones poco habituales si solicitan permisos de nivel alto, solo si el usuario que autorizó los permisos es un miembro del grupo Administradores.

- **El Control de aplicaciones de acceso condicional ahora se integra con las aplicaciones locales mediante Azure Active Directory Application Proxy**  
  - [Azure AD Application Proxy](/azure/active-directory/manage-apps/application-proxy) proporciona inicio de sesión único y acceso remoto seguro para aplicaciones web hospedadas en el entorno local.
  - Ahora se pueden enrutar estas aplicaciones web locales a Microsoft Cloud App Security a través de acceso condicional de Azure AD para proporcionar supervisión en tiempo real y controles, a través de directivas de [acceso](access-policy-aad.md) y [sesión](session-policy-aad.md).

## <a name="cloud-app-security-release-133-134-135"></a>Cloud App Security, versión 133, 134 y 135

Publicado en octubre de 2018

- **Se están implantando gradualmente nuevas directivas de detección de anomalías**  
  - La nueva directiva Filtración de datos a aplicaciones no autorizadas se habilita automáticamente para enviarle una alerta cada vez que un usuario o una dirección IP usan una aplicación que no tiene permitido realizar una actividad que parezca un intento de filtrar información de la organización.
    - La nueva directiva Varias actividades de eliminación de VM crea un perfil del entorno y activa alertas cuando los usuarios eliminan varias máquinas virtuales en una única sesión, en relación con la línea base de la organización.

- **Servicio de clasificación de datos disponible para APAC**  
  - La inspección de contenido del servicio de clasificación de datos ya está disponible para clientes de APAC. Para obtener una lista de compatibilidad regional completa, vea [Integración de los servicios de clasificación de datos de Microsoft](dcs-inspection.md).

- **Compatibilidad de Cloud Discovery para i-Filter**  
  - La característica Cloud App Security Cloud Discovery ahora tiene compatibilidad mejorada para el analizador de syslog de i-Filter.

## <a name="cloud-app-security-release-132"></a>Cloud App Security versión 132

Publicado el 25 de septiembre de 2018

- **Control de aplicaciones de acceso condicional para Office 365 está ahora en versión preliminar pública**  
  - Control de aplicaciones de acceso condicional ahora también es compatible con Office 365 y cualquier aplicación que esté configurada con Open ID Connect.
  - Proporcionar comentarios desde dentro de una sesión: esta nueva herramienta le permite enviar comentarios al equipo de Cloud App Security sobre el rendimiento de una aplicación bajo el control de sesión, directamente desde la sesión.

- **Integración nativa con Microsoft Defender ATP para Shadow IT Discovery más allá de los límites de la empresa**  
  - Microsoft Cloud App Security ahora se integra de forma nativa con Protección contra amenazas avanzada de Windows Defender (ATP) para proporcionar capacidades de detección de Shadow IT sin implementación para activar y desactivar el uso de la red corporativa de aplicaciones en la nube.  Esto le permite realizar Cloud Discovery en las máquinas, incluso cuando no estén dentro de la red corporativa. También permite realizar investigación por máquina: después de identificar un usuario peligroso, podrá comprobar todas las máquinas a las que el usuario accedió para detectar posibles riesgos; Si identifica una máquina en riesgo, puede comprobar todos los usuarios que la usaron para investigar posibles riesgos. Para más información, vea Protección contra amenazas avanzada de Windows Defender con [Microsoft Cloud App Security](wdatp-integration.md).

- **Inspección de contenido de archivos cifrados**  
  - Cloud App Security ahora admite la inspección de contenido de archivos protegidos que están cifrados y que se protegieron con Azure Information Protection. Ahora puede inspeccionar estos archivos cifrados para volver a clasificarlos e identificar infracciones adicionales de la directiva de seguridad y exposición de DLP.

## <a name="cloud-app-security-release-131"></a>Notas de la versión 131 de Cloud App Security

Publicado el 2 de septiembre de 2018

- **Revocar permisos de forma automática en las aplicaciones de riesgo de OAuth**  
Ahora puede controlar a qué aplicaciones de OAuth tienen acceso los usuarios, revocando el permiso de la aplicación para las aplicaciones de OAuth en Office, Google o Salesforce. Al crear una **directiva de permisos de aplicaciones**, ahora puede establecer la directiva para revocar el permiso de una aplicación.

- **Analizador integrado adicional de Cloud Discovery compatible**  
Cloud Discovery ahora admite el formato de registro de Forcepoint Web Security Cloud.

## <a name="cloud-app-security-release-130"></a>Notas de la versión 130 de Cloud App Security

Publicado el 22 de agosto de 2018

- **Nueva barra de menús**  
Para proporcionar una experiencia administrativa más coherente en todos los productos de Microsoft 365 y poder cambiar más fácilmente entre las soluciones de seguridad de Microsoft, la barra de menús del portal de Cloud App Security se ha movido al lado izquierdo de la pantalla. Esta experiencia de navegación coherente le ayuda a orientarse al pasar de un portal de seguridad de Microsoft a otro.

- **Impacto en la puntuación de la aplicación OAuth**  
Ahora puede enviar comentarios al equipo de Cloud App Security para hacernos saber si se detecta una aplicación OAuth en su organización que parece malintencionada. Esta nueva característica le permite formar parte de nuestra comunidad de seguridad y mejorar el análisis y la puntuación de riesgo de las aplicaciones OAuth. Para más información, consulte [Administrar permisos de aplicación](manage-app-permissions.md).

- **Nuevos analizadores de Cloud Discovery**  
Los analizadores de Cloud Discovery ahora admiten iboss Secure Cloud Gateway y Sophos XG.

## <a name="cloud-app-security-release-129"></a>Notas de la versión 129 de Cloud App Security

Fecha de publicación: 5 de agosto de 2018

- **Nuevas directivas de detección de anomalías: reglas de correo electrónico sospechosas**  
Se agregaron nuevas directivas de detección de anomalías que detectan reglas de reenvío de correo electrónico sospechosas, por ejemplo, si un usuario creó una regla de bandeja de entrada sospechosa que reenvía una copia de todos los correos electrónicos a una dirección externa.

- Esta versión incluye correcciones y mejoras para varios problemas.

## <a name="cloud-app-security-release-128"></a>Notas de la versión 128 de Cloud App Security

Publicada el 22 de julio de 2018

- **Acciones de aplicaciones de OAuth en varias aplicaciones**  
Para las aplicaciones de OAuth a las que se han concedido permisos de aplicación, ahora puede prohibir o aprobar varias aplicaciones con una sola acción. Por ejemplo, puede revisar todas las aplicaciones a las que los usuarios de su organización han concedido un permiso, seleccionar todas las que quiera prohibir y, después, hacer clic en la opción correspondiente para revocar todos los permisos concedidos. Así, ya no se permitirá a los usuarios conceder permisos a esas aplicaciones.  Para obtener más información, vea [Administrar aplicaciones de OAuth](manage-app-permissions.md).

- **Compatibilidad mejorada para las aplicaciones de Azure**  
Para Azure, implementaremos de forma gradual la posibilidad de identificar las aplicaciones como actividades de cuenta de usuario llevadas a cabo por las aplicaciones de Azure (tanto internas como externas). Ello le permite crear directivas que le enviarán una alerta si una aplicación realiza actividades inesperadas y no autorizadas. Para obtener más información, vea [Conectar Azure con Microsoft Cloud App Security](connect-azure-to-microsoft-cloud-app-security.md).

- **Motor de clasificación de datos actualizado con los tipos de datos confidenciales que estipula el RGPD**  
El [Servicio de clasificación de datos de Cloud App Security](dcs-inspection.md) ha agregado los tipos de datos confidenciales que estipula el RGPD al motor de clasificación de datos para que pueda detectar en sus archivos el contenido relacionado con el RGPD.

- **Actualizaciones en el catálogo de aplicaciones en la nube**  
Ahora, en este catálogo se incluye una categoría de riesgo legal (además de las categorías de riesgo general, de seguridad y de cumplimiento) para que pueda administrar la privacidad de los datos y el cumplimiento relativo a la propiedad, incluida la preparación para el RGPD.
Para ayudarle a evaluar la preparación para el RGPD de cada aplicación en la nube, la nueva categoría de riesgo contiene la declaración de preparación del servicio en la nube y el estado de cada control de marco del RGPD.
Tenga en cuenta que, como parte de este entorno, los atributos de riesgo que se indican a continuación se han desplazado de la categoría de riesgo Otros a la categoría Legal:
  - DMCA
  - Propiedad de los datos
  - Directiva de retención de datos

  Además, la nueva categoría de riesgo se puede puntuar por separado para configurar la ponderación de la puntuación de acuerdo con sus preferencias y prioridades. Para obtener más información, vea [Puntuación de riesgo](risk-score.md).

- **Nueva consulta sugerida: preparación para el RGPD**  
Hay una nueva consulta sugerida para que pueda identificar las aplicaciones detectadas que están preparadas para el RGPD. Ya que el RGPD se ha convertido hace poco en una prioridad principal para los administradores de seguridad, esta consulta le permite identificar fácilmente las aplicaciones que están listas para el RGPD y mitigar las posibles amenazas evaluando el riesgo de las que no lo están.

## <a name="cloud-app-security-release-127"></a>Notas de la versión 127 de Cloud App Security

Publicada el 8 de julio de 2018

- Ahora tiene la capacidad de ver actividades genéricas para Office 365. En el **Registro de actividad** y en las **Directivas de actividad** ahora puede filtrar las actividades de Office 365 para las actividades **sin especificar**. La revisión de estas actividades le permite recabar información acerca de las actividades realizadas que aún no están clasificadas por tipo en Cloud App Security, y dichas actividades se pueden usar para enviar solicitudes al equipo de Cloud App Security para crear nuevos tipos de actividad en función de estas actividades.

## <a name="cloud-app-security-release-126"></a>Versión 126 de Cloud App Security

Publicado el 24 de junio de 2018

- **Disponibilidad general del Control de aplicaciones de acceso condicional**  
El Control de aplicaciones de acceso condicional (proxy inverso) de Microsoft Cloud App Security ahora está disponible para todas las aplicaciones de SAML. El Control de aplicaciones de acceso condicional se integra directamente con las directivas de acceso condicional de Azure AD para **supervisar y controlar las sesiones de los usuarios en tiempo real** sin impedirles ser productivos. Desde la primera versión preliminar de la característica, se han agregado muchas funciones y mejoras, incluidas las siguientes:
  - Se ha agregado la funcionalidad para crear una [directiva de acceso](access-policy-aad.md) para administrar el acceso a las mismas aplicaciones desde clientes nativos, además de crear una directiva de sesión para el tráfico del explorador.
  - Se ha simplificado el proceso de incorporación de aplicaciones para admitir aplicaciones de SAML personalizadas en la organización.
  - Como parte de la red internacional de Azure, se han mejorado la integración y la interfaz para que los usuarios ubicados en cualquier lugar del mundo puedan disfrutar de una experiencia sin problemas.

- **Disponibilidad general de la inspección de contenido con el Servicio de clasificación de datos de Microsoft**  
La integración de Microsoft Cloud App Security con los Servicios de clasificación de datos de Microsoft ahora está disponible con carácter general. Esta integración le permite usar el Servicio de clasificación de datos de Microsoft de forma nativa para clasificar los archivos de las aplicaciones en la nube. Para más información, consulte [Integración de los servicios de clasificación de datos de Microsoft](dcs-inspection.md). Esta característica solo está disponible en Estados Unidos y Europa (excepto en Francia).

- **Informe ejecutivo de Cloud Discovery**  
Microsoft Cloud App Security está implementando gradualmente la funcionalidad para generar un informe ejecutivo en PDF de Cloud Discovery. En este informe se proporciona información general sobre el uso de shadow IT que se ha identificado en la organización. Para ello, se resaltan las aplicaciones y los usuarios principales en uso en general y en las categorías principales, y se hace hincapié en el riesgo que shadow IT supone en la organización. Además, el informe proporciona una lista de recomendaciones sobre cómo mejorar la visibilidad y el control de shadow IT en la organización. Use este informe para asegurarse de eliminar los posibles riesgos y amenazas, y que la organización siga siendo segura.

- **Detección de malware**  
La funcionalidad de detección de malware se está implantando de forma gradual para **detectar automáticamente los archivos maliciosos en el almacenamiento en la nube**, con independencia del tipo de archivo. Microsoft Cloud App Security usa la inteligencia sobre amenazas de Microsoft para reconocer si determinados archivos están asociados a ataques de malware conocidos o son potencialmente maliciosos. Para obtener más información, vea [Directivas de detección de anomalías](anomaly-detection-policy.md).

- **Corrección automatizada de actividades sospechosas**  
Ahora puede establecer acciones de corrección automática para una sesión sospechosa desencadenadas por las directivas de detección de anomalías. Gracias a esta mejora, se le avisará al instante cuando se produzca una infracción y **se aplicarán automáticamente las acciones de gobernanza**, por ejemplo, la suspensión del usuario. Para obtener más información, vea [Directivas de detección de anomalías](anomaly-detection-policy.md#adp-automated-gov).

- **Evaluación de la configuración de seguridad para Azure**  
Microsoft Cloud App Security está implementando de forma gradual la funcionalidad de obtener una evaluación de la configuración de seguridad del entorno de Azure, y proporciona recomendaciones para el control de la seguridad y los valores de configuración que falten. Por ejemplo, le permitirá saber si falta MFA para los usuarios administrativos. Para obtener más información, vea [Cloud Security Posture Management integration](security-config.md) (Integración de la administración de posiciones de seguridad en la nube).

- **Detección automática de aplicaciones OAuth peligrosas**  
Además de la investigación existente de aplicaciones de OAuth conectadas al entorno, ahora Microsoft Cloud App Security está implementando de forma gradual la funcionalidad para establecer notificaciones automatizadas que avisen cuando una aplicación de OAuth cumple determinados criterios. Por ejemplo, puede recibir alertas automáticamente cuando haya aplicaciones que requieran un alto nivel de permisos y las hayan autorizado más de 50 usuarios. Para obtener más información, vea [Directivas de permisos de la aplicación](app-permission-policy.md).

- **Compatibilidad con la administración de proveedores de servicios de seguridad administrada (MSSP)**  
Microsoft Cloud App Security ahora proporciona una mejor experiencia de administración para MSSP. Ahora es posible configurar a usuarios externos como administradores y asignarles cualquiera de los [roles disponibles actualmente en Microsoft Cloud App Security](manage-admins.md). Además, para permitir que los MSSP proporcionen servicios en varios inquilinos de clientes, los administradores que tienen derechos de acceso a más de un inquilino ahora pueden cambiar de inquilino fácilmente en el portal. Para información sobre cómo administrar los administradores, vea [Administración de los administradores](manage-admins.md).

- **Disponibilidad general de la integración con DLP externa**  
Microsoft Cloud App Security permite [aprovechar las inversiones existentes en sistemas de clasificación de terceros](icap-stunnel.md), como soluciones de prevención de pérdida de datos (DLP), y permite examinar el contenido de aplicaciones en la nube mediante las implementaciones que se ejecutan en el entorno. Para obtener más información, vea [Integración de DLP externa](icap-stunnel.md).

## <a name="cloud-app-security-release-125"></a>Notas de la versión 125 de Cloud App Security

Publicado el 10 de junio de 2018

- **Nueva funcionalidad de investigación de los usuarios principales:**  
Microsoft Cloud App Security agregó un nuevo widget de investigación al panel donde aparecen los usuarios principales según el número de alertas de detección de amenazas abiertas. Este widget de investigación le permite centrar su investigación de amenazas en aquellos usuarios que cuentan con el mayor número de sesiones sospechosas.

- **Compatibilidad con los cubos de AWS S3:**  
Microsoft Cloud App Security puede detectar ahora cubos de AWS S3 y sus niveles de uso compartido. Esto proporciona alertas y visibilidad en cubos de AWS accesibles públicamente. También permite crear directivas basadas en cubos y aplicar la regulación automática. Además, hay una nueva plantilla de directiva disponible llamada **Publicly accessible S3 buckets (AWS)** (Cubos de S3 accesibles públicamente (AWS)) que puede usar para crear fácilmente una directiva que regule su almacenamiento de AWS. Para habilitar estas nuevas funcionalidades, asegúrese de actualizar sus aplicaciones conectadas mediante AWS agregando los nuevos permisos descritos en [Conectar AWS](connect-aws-to-microsoft-cloud-app-security.md).

- **Privilegios de administración basados en grupos de usuarios**:  
Ahora puede establecer los permisos administrativos de los administradores de Microsoft Cloud App Security por cada grupo de usuarios. Por ejemplo, puede establecer un usuario concreto como administrador de únicamente los usuarios de Alemania. Esto permitiría al usuario ver y modificar la información en Microsoft Cloud App Security relativa únicamente al grupo de usuarios "Alemania: todos los usuarios". Para más información, vea [Administración del acceso de administrador](manage-admins.md).

## <a name="cloud-app-security-release-124"></a>Notas de la versión 124 de Cloud App Security

Fecha de publicación: 27 de mayo de 2018

- **Se agregó la evaluación del riesgo del RGPD al catálogo de aplicaciones en la nube**  
Se agregaron 13 nuevos factores de riesgo a Microsoft Cloud App Security. Estos factores de riesgo siguen la lista de comprobación del marco del RGPD para que pueda evaluar las aplicaciones del catálogo de aplicaciones en la nube según la normativa del RGPD.

- **Integración con el servicio de clasificación de datos de Microsoft**  
Microsoft Cloud App Security ahora le permite utilizar el servicio de clasificación de datos de Microsoft de forma nativa, para clasificar los archivos de las aplicaciones en la nube.   
El servicio de clasificación de datos de Microsoft proporciona una experiencia de protección de información unificada en Office 365, Azure Information Protection y Microsoft Cloud App Security. Permite llevar el mismo marco de trabajo de clasificación de datos a las aplicaciones en la nube de terceros que están protegidas por Microsoft Cloud App Security, aprovechando las decisiones ya adoptadas en un número mayor de aplicaciones.

- **Conexión a Microsoft Azure** (implantación gradual)  
Microsoft Cloud App Security está ampliando sus capacidades de supervisión de IaaS más allá de Amazon Web Services y ahora es compatible con Microsoft Azure. Esto le permite conectarse y supervisar de manera fluida todas las suscripciones de Azure con Cloud App Security. Esta conexión le ofrece un conjunto eficaz de herramientas para proteger el entorno de Azure, como las siguientes:

  - Visibilidad en todas las actividades realizadas a través del portal

  - Posibilidad de crear directivas personalizadas para alertar sobre comportamientos no deseados, así como la posibilidad de protegerse automáticamente ante usuarios de riesgo mediante la suspensión o la exigencia de que vuelvan a iniciar sesión.

  - Todas las actividades de Azure están cubiertas por el motor de detección de anomalías, que generará una alerta automáticamente ante cualquier comportamiento sospechoso en Azure Portal, como un viaje imposible, actividades sospechosas masivas y la actividad desde un nuevo país.  

  Para obtener más información, vea [Conectar Azure con Microsoft Cloud App Security](connect-azure-to-microsoft-cloud-app-security.md).

- **Implementaciones con ámbito** (lanzamiento gradual)  
Microsoft Cloud App Security ofrece a las empresas la capacidad de determinar de forma detallada los usuarios que quieren supervisar y proteger en función de la pertenencia a grupos. Esta característica permite seleccionar usuarios cuyas actividades no se mostrarán para ninguna de las aplicaciones protegidas. La función de supervisión con ámbito es especialmente útil en los siguientes aspectos:
  - Cumplimiento normativo: si debe abstenerse de supervisar a los usuarios de determinados países debido a la normativa local.
  - Licencias: si desea supervisar menos usuarios para permanecer dentro de los límites de las licencias de Microsoft Cloud App Security.
  Para obtener más información, consulte [Scoped deployment](scoped-deployment.md) (Implementación con ámbito).

- **Alerta de aplicación infringida para aplicaciones detectadas**  
 Ahora hemos integrado una alerta para notificarle cuando alguna de las aplicaciones detectadas de un inquilino se infringe. La alerta proporcionará información acerca de la fecha y hora de la infracción y los usuarios que usaron la aplicación, y se vinculará a los orígenes disponibles públicamente que proporcionan información acerca de la infracción.

- **Nuevo servidor de correo**  
 El servidor de correo de Cloud App Security ha cambiado y utiliza distintos intervalos de direcciones IP. Para asegurarse de que puede recibir notificaciones, agregue las nuevas direcciones IP a la lista blanca de direcciones de correo no deseado. Para los usuarios que personalizan sus notificaciones, Microsoft Cloud App Security lo hace posible mediante MailChimp®, un servicio de correo electrónico de terceros. Para obtener la lista de direcciones IP de servidor de correo electrónico e instrucciones para habilitar el trabajo con MailChimp, consulte [Requisitos de red](network-requirements.md#mail-server) y [Establecimiento de preferencias de notificación de correo electrónico](mail-settings.md).

## <a name="cloud-app-security-release-123"></a>Cloud App Security versión 123

Fecha de publicación: 13 de mayo de 2018

- **Ámbito de la directiva de detección de anomalías**:  
Ahora se puede establecer un ámbito para las directivas de detección de anomalías. Esto le permite establecer cada directiva de detección de anomalías para incluir solo determinados usuarios o grupos y para excluir usuarios o grupos específicos. Por ejemplo, puede establecer la actividad desde la detección de condado poco frecuente hasta omitir un usuario específico que viaja con frecuencia.

## <a name="cloud-app-security-release-122"></a>Notas de la versión 122 de Cloud App Security

Fecha de publicación: 29 de abril de 2018

- Implementación gradual: ahora puede **establecer los permisos administrativos de los administradores de Microsoft Cloud App Security por cada aplicación**. Por ejemplo, puede establecer un usuario concreto como administrador de únicamente G Suite. Esto permitiría al usuario ver y modificar la información en Microsoft Cloud App Security relativa únicamente a G Suite. Para más información, vea [Administración del acceso de administrador](manage-admins.md).

- Implementación gradual: **ahora, los roles de administrador de Okta aparecen** en Microsoft Cloud App Security y están disponibles para cada rol como una etiqueta en **Configuración** > **Grupos de usuarios**.

## <a name="cloud-app-security-release-121"></a>Notas de la versión 121 de Cloud App Security

Fecha de publicación: 22 de abril de 2018

- La versión preliminar pública de **Conditional Access App Control (anteriormente denominado proxy de Cloud App Security)** se ha mejorado con funcionalidades que facilitan mayor visibilidad y control de las distintas aplicaciones. Ahora puede crear una directiva de sesión con un filtro *Tipo de actividad* para supervisar y bloquear diversas actividades específicas de la aplicación. Este nuevo filtro, que funciona conjuntamente con el acceso condicional de Azure Active Directory, aumenta las características de control de descarga de archivos existentes para proporcionarle control completo de las aplicaciones de su organización para ofrecer visibilidad en tiempo real y control de sesiones de usuario de riesgo: por ejemplo, las sesiones con usuarios de colaboración B2B o procedentes de un dispositivo no administrado. Para obtener más información, consulte [Directivas de sesión](session-policy-aad.md).

- Implementación gradual: **se han mejorado las directivas de detección de anomalías** de Cloud App Security para incluir dos nuevos tipos de detección de amenazas: Actividad de ransomware y Actividad del usuario cancelado. Cloud App Security ha ampliado sus funcionalidades de detección de ransomware con la detección de anomalías para garantizar una cobertura más completa frente a ataques de ransomware sofisticados. Con nuestra experiencia en investigación de seguridad para identificar patrones de comportamiento que reflejan la actividad de ransomware, Cloud App Security garantiza una protección integral y sólida. Actividad del usuario cancelado le permite supervisar las cuentas de usuarios cancelados, que es posible que se hayan desaprovisionado de aplicaciones corporativas, pero en muchos casos todavía conservan el acceso a ciertos recursos corporativos. Para obtener más información, vea [Obtención de análisis de comportamiento y detección de anomalías instantáneos](anomaly-detection-policy.md).

## <a name="cloud-app-security-release-120"></a>Notas de la versión 120 de Cloud App Security

Publicada el 8 de abril de 2018

- Para Office 365 y Azure AD, implementaremos de forma gradual la posibilidad de identificar las aplicaciones internas como actividades de cuenta de usuario llevadas a cabo por las aplicaciones de Office 365 y Azure AD (tanto internas como externas). Ello le permite crear directivas que le enviarán una alerta si una aplicación realiza actividades inesperadas y no autorizadas.

- Al exportar la lista de permisos de una aplicación a un archivo .csv, los campos adicionales, como el anunciante, el nivel de permisos y el uso de la comunidad, se incluyen para asistir durante el proceso de investigación y cumplimiento.

- La aplicación conectada ServiceNow se ha mejorado para que las actividades de servicio internas dejen de registrarse como si las hubiese llevado a cabo un invitado y dejen de activar alertas de falsos positivos. Ahora, dichas actividades constan como N/A, igual que el resto de las aplicaciones conectadas.

## <a name="cloud-app-security-release-119"></a>Notas de la versión 119 de Cloud App Security

Fecha de publicación: 18 de marzo de 2018

- En la página de intervalos de direcciones IP se incluyen las direcciones IP integradas que ha detectado Cloud App Security. Esto incluye direcciones IP para los servicios en la nube identificados, como Azure y Office 365, así como la fuente de Inteligencia sobre amenazas que agrega automáticamente direcciones IP con información acerca de las direcciones IP peligrosas conocidas.

- Cuando Cloud App Security intenta ejecutar una acción de gobernanza en un archivo, pero se produce un error porque el archivo está bloqueado, ahora se reintentará automáticamente la acción de gobernanza.

## <a name="cloud-app-security-release-118"></a>Cloud App Security versión 118

Fecha de publicación: 4 de marzo de 2018

- Ahora puede aprovechar las funcionalidades de detección y supervisión de Shadow IT de Microsoft Cloud App Security en sus propias aplicaciones personalizadas exclusivas. La nueva posibilidad de agregar aplicaciones personalizadas a Cloud Discovery permite supervisar el uso de la aplicación y recibir alertas sobre cambios en el patrón de uso. Para obtener más información, consulte [Protecting your custom apps](cloud-discovery-custom-apps.md) (Protección de las aplicaciones personalizadas). Esta característica se está implantando gradualmente.

- Las páginas de **configuración** del portal de Cloud App Security se han rediseñado. El nuevo diseño consolida todas las páginas de configuración, proporciona la funcionalidad de búsqueda y un mejor diseño.

- Cloud Discovery admite ahora Barracuda F-Series Firewalls y Barracuda F-Series Firewall Web Log Streaming.

- La funcionalidad de búsqueda en las páginas de dirección IP y de usuario habilita ahora Autocompletar para que le resulte más fácil encontrar lo que busca.

- Ahora puede realizar acciones en masa en las páginas de configuración de exclusión de entidades y de exclusión de direcciones IP. Esto hace que le resulte más fácil seleccionar varios usuarios y grupos o direcciones IP y excluirlos de la supervisión como parte de Cloud Discovery en su organización.

## <a name="cloud-app-security-release-117"></a>Cloud App Security versión 117

Publicado el 20 de febrero de 2018

- La mejor integración de Cloud App Security con Azure Information Protection ahora le permite proteger archivos en G Suite. Esta característica de versión preliminar pública permite examinar y clasificar archivos de G Suite y aplicar automáticamente etiquetas de protección de Azure Information Protection para protegerlos. Para obtener más información, consulte [Integración de Azure Information Protection](azip-integration.md).

- Cloud Discovery admite ahora [Digital Arts i-FILTER](https://www.daj.jp/en/products/if/).

- La tabla Agentes SIEM incluye ahora más detalles que facilitan la administración.

## <a name="cloud-app-security-release-116"></a>Cloud App Security versión 116

Publicado el 4 de febrero de 2018

- La directiva de detección de anomalías de Cloud App Security se ha mejorado con nuevas **detecciones basadas en escenarios** entre las que se incluyen viaje imposible, actividad desde una dirección IP sospechosa y varios intentos incorrectos de inicio de sesión. Las nuevas directivas se habilitan automáticamente, lo que proporciona la detección de amenazas desde el primer momento en todo el entorno de nube. Además, las nuevas directivas exponen más datos a partir del motor de detección de Cloud App Security, lo que le ayuda a agilizar el proceso de investigación y contener las amenazas en curso. Para obtener más información, vea [Obtención de análisis de comportamiento y detección de anomalías instantáneos](/cloud-app-security/anomaly-detection-policy).

- Implementación gradual: Cloud App Security ahora se pone en correlación entre los usuarios y sus cuentas en aplicaciones SaaS. Esto le permite investigar fácilmente todas las actividades de los usuarios, en todas sus diferentes aplicaciones de SaaS correlacionadas, con independencia de qué aplicación o cuenta utilizan.

- Implementación gradual: Cloud App Security ahora admite varias instancias de la misma aplicación conectada. Si tiene varias instancias de, por ejemplo, Salesforce (una para venta y otra para marketing) podrá conectarlas a Cloud App Security y administrarlas desde la misma consola para crear directivas granulares y una investigación más a fondo.

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

[!INCLUDE [Open support ticket](includes/support.md)]
