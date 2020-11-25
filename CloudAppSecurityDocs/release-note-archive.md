---
title: Archivado de actualizaciones anteriores en Cloud App Security
description: Este artículo es un archivo que describe las actualizaciones realizadas en versiones anteriores de Cloud App Security.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 11/25/2020
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: c279b64cd63152cdd8ec4c824926a9859dcd4803
ms.sourcegitcommit: faf7c8f85721dd143ca81c6854ad5c4e8fa50e69
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/25/2020
ms.locfileid: "96025359"
---
# <a name="past-release-archive-of-microsoft-cloud-app-security"></a>Archivo de versiones anteriores de Microsoft Cloud App Security

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Este artículo es un archivo que describe las actualizaciones realizadas en versiones anteriores de Cloud App Security. Para ver la lista de novedades más reciente, consulte [Novedades de Microsoft Cloud App Security](release-notes.md).

## <a name="updates-made-in-2019"></a>Actualizaciones realizadas en 2019

### <a name="cloud-app-security-release-162-163-and-164"></a>Notas de la versión 162, 163 y 164 de Cloud App Security

Fecha de publicación: 8 de diciembre de 2019

- **Cambio a las actividades y alertas de SIEM en formato CEF**  
El [formato de dirección URL del portal (CS1)](siem.md#sample-cloud-app-security-alerts-in-cef-format) para la actividad y la información de alertas que envía Cloud App Security a SIEMs ha cambiado a `https://<tenant_name>.portal.cloudappsecurity.com` y ya no contiene la ubicación del centro de datos. Los clientes que usen la coincidencia de patrones para la dirección URL del portal deben actualizar el patrón para reflejar este cambio.

### <a name="cloud-app-security-release-160-and-161"></a>Notas de la versión 160 y 161 de Cloud App Security

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

  - **Cambios sospechosos en el servicio de registro de AWS (versión preliminar)** : Le avisa cuando un usuario realiza cambios en el servicio de registro de CloudTrail. Por ejemplo, los atacantes suelen desactivar la auditoría en CloudTrail para ocultar las huellas de su ataque.

  - **Varias actividades de creación de máquinas virtuales**: Le avisa cuando un usuario realiza un número inusual de actividades de creación de máquinas virtuales, en comparación con la línea de base aprendida. Ahora se aplica a AWS.

### <a name="cloud-app-security-release-159"></a>Notas de la versión 159 de Cloud App Security

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

### <a name="cloud-app-security-release-158"></a>Notas de la versión 158 de Cloud App Security

Publicado el 15 de septiembre de 2019

- **Personalización de un nombre de informe de Cloud Discovery**  
El informe ejecutivo de Cloud Discovery proporciona información general sobre el uso de Shadow IT en la organización. Ahora tiene la opción de personalizar el nombre del informe antes de generarlo. Para más información, consulte [Generación de un informe ejecutivo de Cloud Discovery](discovered-apps.md#generate-cloud-discovery-executive-report).

- **Nuevo informe de información general sobre directivas**  
Cloud App Security detecta coincidencias de directivas y, cuando está definido, registra alertas que puede utilizar para comprender mejor su entorno en la nube. Ahora puede exportar un informe de información general de directivas que muestra las métricas de alerta agregadas por directiva para ayudarle a supervisar, comprender y personalizar las directivas para proteger mejor la organización. Para más información sobre cómo exportar el informe, consulte [Informe de información general sobre directivas](control-cloud-apps-with-policies.md#policies-overview-report).

### <a name="cloud-app-security-release-157"></a>Cloud App Security, versión 157

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

### <a name="cloud-app-security-release-156"></a>Notas de la versión 156 de Cloud App Security

Publicado el 18 de agosto de 2019

- **Nuevos analizadores de registro de Cloud Discovery**  
Cloud Discovery de Cloud App Security analiza una amplia gama de registros de tráfico para clasificar y puntuar aplicaciones. Ahora Cloud Discovery incluye un analizador de registros integrado para admitir los formatos de registro Stormshield y Forcepoint LEEF.

- **Mejoras en el Registro de actividad**  
Cloud App Security ahora proporciona una mayor visibilidad de las actividades sin clasificar realizadas por las aplicaciones en el entorno. Estas actividades están disponibles en el Registro de actividad y también en las directivas de actividad. Para ver actividades sin clasificar, en el filtro **Tipo** seleccione **Sin especificar**. Para obtener más información sobre los filtros de actividad, vea [Filtros y consultas de actividad](activity-filters-queries.md).

- **Mejora de la investigación de usuarios de riesgo**  
Cloud App Security ofrece la posibilidad de identificar a usuarios de riesgo en la página **Usuarios y cuentas** mediante la especificación de grupos, aplicaciones e incluso roles concretos. Ahora también puede investigar a los usuarios de la organización por su puntuación de **prioridad de investigación**. Para obtener más información, vea [Comprender la puntuación de prioridad de investigación](tutorial-ueba.md#risk-score).

- **Mejoras de la directiva de actividad**  
Ahora puede crear alertas de directiva de actividad basadas en objetos de actividad. Por ejemplo, esta capacidad permite crear alertas sobre los cambios en los roles administrativos de Azure Active Directory. Para obtener más información sobre los objetos de actividad, vea [Filtros de actividad](activity-filters-queries.md#activity-filters).

### <a name="cloud-app-security-release-155"></a>Notas de la versión 155 de Cloud App Security

Publicado el 4 de agosto de 2019

- **Nuevas plantillas de directiva**  
Cloud App Security ahora incluye nuevas plantillas de directiva de actividad integradas para los procedimientos recomendados de seguridad de AWS.

- **Aviso: Fin de la compatibilidad con TLS 1.0 y 1.1 el 8 de septiembre**  
Microsoft está moviendo todos sus servicios en línea a la Seguridad de la capa de transporte (TLS) 1.2+ para proporcionar el mejor cifrado de la clase. Por lo tanto, a partir del 8 de septiembre de 2019 Cloud App Security dejará de ser compatible con TLS 1.0 y 1.1, y no se admitirán las conexiones que usen estos protocolos. Para más información sobre cómo le afecta el cambio, consulte [nuestra entrada de blog](https://techcommunity.microsoft.com/t5/Enterprise-Mobility-Security/End-of-support-for-TLS-1-0-and-1-1-in-Microsoft-Cloud-App/ba-p/770507).

- **Lógica mejorada para actividades de inicio de sesión interactivas (implementación gradual)**  
Estamos implementando gradualmente una nueva lógica para identificar si una actividad de inicio de sesión de Azure Active Directory es interactiva. La nueva lógica mejora la capacidad de Cloud App Security de solo investigar las actividades de inicio de sesión iniciadas por un usuario.

### <a name="cloud-app-security-release-154"></a>Cloud App Security, versión 154

Publicado el 21 de julio de 2019

- **La incorporación y la implementación del Control de aplicaciones de acceso condicional para cualquier aplicación está ahora disponible con carácter general**  
Desde que lanzamos la versión preliminar de Control de aplicaciones de acceso condicional para cualquier aplicación el mes pasado, hemos recibido comentarios muy positivos y nos complace anunciar que ya está disponible con carácter general. Esta nueva funcionalidad permite implementar cualquier aplicación web para trabajar con directivas de sesión y acceso, con lo que se habilita la supervisión y el control eficaces en tiempo real.

- **Evaluación de la configuración de seguridad para AWS**  
Cloud App Security está implementando de forma gradual la funcionalidad de obtener una evaluación de la configuración de seguridad del entorno de Amazon Web Services para el cumplimiento de CIS, y proporciona recomendaciones para los controles de seguridad y los valores de configuración que falten. Esta capacidad proporciona a las organizaciones una única vista para supervisar el estado de cumplimiento de todas las cuentas de AWS conectadas.

- **Detecciones de anomalías de aplicaciones de OAuth**  
Hemos ampliado nuestra capacidad actual para detectar aplicaciones de OAuth sospechosas. Ya hay disponibles cuatro detecciones nuevas listas para usar que perfilan los metadatos de las aplicaciones de OAuth autorizadas de su organización para identificar cuáles son potencialmente maliciosas.

### <a name="cloud-app-security-release-153"></a>Notas de la versión 153 de Cloud App Security

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

### <a name="cloud-app-security-release-152"></a>Notas de la versión 152 de Cloud App Security

Publicada el 23 de junio de 2019

- **Implementación del Control de aplicaciones de acceso condicional para cualquier aplicación (versión preliminar)**  
Nos complace anunciar que hemos ampliado la compatibilidad con el Control de aplicaciones de acceso condicional a cualquier aplicación web, además de la amplia compatibilidad que ya ofrecemos para las [aplicaciones destacadas](proxy-intro-aad.md). Esta nueva funcionalidad permite implementar cualquier aplicación web para trabajar con directivas de sesión y acceso, con lo que se habilita la supervisión y el control eficaces en tiempo real. Por ejemplo, puede proteger las descargas con etiquetas de Azure Information Protection y bloquear la carga de documentos confidenciales, brindando auditoría, entre muchas otras acciones.
- **Auditoría de la actividad del portal**  
Cloud App Security hace una auditoría de toda la actividad del administrador del portal para ofrecer una supervisión e investigación integrales de las actividades realizadas. Ahora también puede exportar hasta 90 días de actividades para realizar más investigación y análisis como, por ejemplo, realizar una auditoría a un administrador que investiga a un usuario específico o ver alertas específicas. Para exportar el registro, vaya a la página de configuración **Administrar el acceso de administrador**.
- **Cierre de sesión personalizado desde el portal de Cloud App Security**  
Ahora puede configurar el cierre de sesión automático de las sesiones del administrador en el portal que están inactivas por más tiempo que un período especificado.

### <a name="cloud-app-security-release-151"></a>Versión 151 de Cloud App Security

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

### <a name="cloud-app-security-release-150"></a>Versión 150 de Cloud App Security

Fecha de publicación: 26 de mayo de 2019

- **Mejora en la exportación de alertas**  
Ahora, al exportar las alertas a CSV desde la página **Alertas**, los resultados incluyen la fecha de la resolución o del descarte de la alerta.

### <a name="cloud-app-security-release-148-and-149"></a>Notas de la versión 148 y 149 de Cloud App Security

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

### <a name="cloud-app-security-release-147"></a>Notas de la versión 147 de Cloud App Security

Fecha de publicación: 14 de abril de 2019

- **Nuevos analizadores de registro de Cloud Discovery**  
Cloud Discovery de Cloud App Security ahora incluye un analizador de registros integrado para admitir el formato de registro LEEF de Palo Alto.

- **Actualizaciones de directivas de sesión**  
  - **Método de inspección de contenido adicional para las directivas de sesión**:  Al establecer una directiva de sesión, ahora tiene la opción de elegir el servicio de clasificación de datos como método de inspección de contenido de los archivos. El servicio de clasificación de datos ofrece al usuario un amplio rango de tipos de datos confidenciales integrados para utilizarlos en la identificación de información confidencial.
  - **Control mejorado de los permisos de archivo en las directivas de sesión**:  Al crear una directiva de sesión para controlar las descargas mediante Cloud App Security, ahora puede aplicar automáticamente permisos por usuario, como por ejemplo de solo lectura, a los documentos una vez descargados desde las aplicaciones en la nube. Esto proporciona un nivel mucho mayor de flexibilidad y la capacidad de proteger la información más allá de las etiquetas corporativas configuradas previamente.
  - **Control de descarga de archivos grandes**:  Cuando se habilita la inspección de contenido en las directivas de sesión, ahora puede controlar lo que sucede cuando un usuario intenta descargar un archivo muy grande. Si el archivo es demasiado grande para analizarlo durante la descarga, puede elegir si desea bloquear o permitir dicho análisis.

### <a name="cloud-app-security-release-146"></a>Notas de la versión 146 de Cloud App Security

Fecha de publicación: 31 de marzo de 2019

- **Mejora de viaje imposible**  
Se ha mejorado la detección de viajes imposibles con compatibilidad específica para los países/regiones vecinos.
- **Compatibilidad adicional de atributos para el analizador genérico de CEF**  
La compatibilidad del analizador de registros de Cloud Discovery para el formato genérico CEF se ha mejorado para admitir atributos adicionales.
- **Acceso limitado a los informes de Cloud Discovery**  
Además del rol de administrador de Discovery, ahora puede limitar el acceso a informes específicos de Discovery. Esta mejora le permite configurar privilegios para los datos de sitios y unidades de negocio específicos.
- **Compatibilidad con nuevos roles: Lector global**  
Microsoft Cloud App Security ahora admite el rol de lector global de Azure AD. El lector global tiene acceso de solo lectura a todos los aspectos de Microsoft Cloud App Security, pero no puede cambiar ninguna configuración ni realizar ninguna acción.

### <a name="cloud-app-security-release-145"></a>Notas de la versión 145 de Cloud App Security

Fecha de publicación: 17 de marzo de 2019

- **Integración con Microsoft Defender ATP disponible para público general**  
El año pasado anunciamos la [integración con Protección contra amenazas avanzada de Windows Defender](https://techcommunity.microsoft.com/t5/Enterprise-Mobility-Security/Microsoft-Cloud-App-Security-and-Windows-Defender-ATP-better/ba-p/263265) que mejora la detección de shadow IT de su organización y la amplía más allá de la red corporativa. [Habilitada con un solo clic](https://query.prod.cms.rt.microsoft.com/cms/api/am/binary/RWtNmG), nos complace poder anunciar que esta integración única ya está disponible con carácter general.
- **Soporte técnico de Dynamics 365 CRM**  
Cloud App Security agregó control y supervisión en tiempo real para Dynamics 365 CRM, lo que permite proteger las aplicaciones empresariales y el contenido confidencial almacenado en estas aplicaciones. Para más información sobre lo que se puede hacer con Dynamics 365 CRM, consulte [este artículo](proxy-intro-aad.md#how-it-works).

### <a name="cloud-app-security-release-144"></a>Notas de la versión 144 de Cloud App Security

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

### <a name="cloud-app-security-release-143"></a>Notas de la versión 143 de Cloud App Security

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

### <a name="cloud-app-security-release-142"></a>Notas de la versión 142 de Cloud App Security

Publicado el 3 de febrero de 2019

- **Configuración de la directiva de sesión en Azure AD**  
Ahora puede configurar directivas de sesión para supervisar a los usuarios o bloquear las descargas en tiempo real, directamente en el acceso condicional de Azure AD. Todavía puede configurar directivas de sesión avanzadas directamente en Cloud App Security. Para recorrer esta implementación, consulte [Implementación del Control de aplicaciones de acceso condicional para aplicaciones destacadas](proxy-deployment-aad.md).

- **Consultas sugeridas y guardadas para aplicaciones de OAuth**  
Las consultas sugeridas se han agregado a la página de aplicaciones de OAuth y proporcionan plantillas de investigación predefinidas para filtrar las aplicaciones de OAuth. Las consultas sugeridas incluyen filtros personalizados para identificar aplicaciones arriesgadas, como las aplicaciones autorizadas por los administradores. Las consultas guardadas permiten guardar consultas personalizadas para su uso futuro, de forma similar a las consultas guardadas disponibles hoy en las páginas de detección y registro de actividad.

- **Configuración predeterminada de auditoría de Office 365**  
Si desea habilitar la supervisión de las actividades de Office 365 en Cloud App Security, ahora es necesario habilitar la auditoría en el [Centro de seguridad y cumplimiento de Office](/office365/securitycompliance/turn-audit-log-search-on-or-off#turn-on-audit-log-search), lo que se debe a un [cambio en la auditoría de Office 365](/office/office-365-management-api/office-365-management-activity-api-faq#what-happens-if-i-disable-auditing-for-my-office-365-organization-will-i-still-get-events-via-the-management-activity-api). Este cambio solo debe realizarse si aún no ha habilitado la supervisión de las actividades de Office 365 en Cloud App Security.

- **Compatibilidad mejorada con Box**  
Cloud App Security ahora admite dos nuevas acciones de gobierno para Box:

  - **Expiración de vínculo compartido**: esta acción de gobierno le proporciona la capacidad de establecer una fecha de expiración para un vínculo compartido después del cual dejará de estar activo.

  - **Cambio del nivel de acceso del vínculo de uso compartido**: esta acción de gobierno proporciona la capacidad de cambiar el nivel de acceso del vínculo compartido entre solo la empresa, solo colaboradores y el público.

- **Compatibilidad con múltiples ubicaciones en OneDrive**  
Cloud App Security ahora proporciona visibilidad completa de los archivos de OneDrive, incluso si están dispersos en varias ubicaciones geográficas. La protección está disponible ahora para los archivos que se encuentran en las ubicaciones adicionales, así como en la ubicación principal.

- **Mejora en la navegación del portal**  
El portal de Cloud App Security se ha mejorado para ofrecer una mejor navegación y una mejor alineación de Cloud App Security con los otros servicios de seguridad de Microsoft, para simplificar la facilidad de uso.

### <a name="cloud-app-security-release-141"></a>Notas de la versión 141 de Cloud App Security

Fecha de publicación: 20 de enero de 2019

- **Mejoras en la evaluación de riesgos en la nube**  
  - La evaluación de riesgos de Cloud App se mejoró con dos experiencias nuevas.
    - Un nuevo atributo de **tipo de datos** evalúa el tipo de contenido que los usuarios pueden cargar en la aplicación. Puede usar este atributo para evaluar una aplicación en función de la confidencialidad de cada tipo de datos de su organización.
    - Para obtener una información general más completa sobre los riesgos de una aplicación, ahora puede dinamizar fácilmente desde la evaluación de riesgos de la aplicación hasta la evaluación de riesgos de la empresa de hospedaje. Para ello, haga clic en el atributo de **empresa de hospedaje**.

- **Contexto de archivo mejorado para la investigación de alertas de detección de anomalías**  
  - La investigación de detección de anomalías se ha mejorado para que pueda ver información adicional asociada a los archivos implicados en una alerta. Cuando se desencadenan las alertas para alertas de actividad inusual relacionadas con archivos (descargar, compartir, eliminar), esta exploración en profundidad está disponible. Por ejemplo, si la mayoría de los archivos afectados proceden de la misma carpeta o comparten la misma extensión de archivo, verá esta información en la sección de riesgos adicionales de la alerta.

- **Consultas para la investigación de archivos**  
  - La capacidad de Cloud App Security para crear y guardar consultas personalizadas se amplió a la página **Archivos**. Las consultas de la página de **archivos** permiten crear plantillas de consulta que se pueden reutilizar para una investigación en profundidad.

### <a name="cloud-app-security-release-139-140"></a>Notas de la versión 139, 140 de Cloud App Security

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

## <a name="updates-made-in-2018"></a>Actualizaciones realizadas en 2018

### <a name="cloud-app-security-release-138"></a>Notas de la versión 138 de Cloud App Security

Fecha de publicación: 9 de diciembre de 2018

- **Carga automática del Registro con Docker en Windows**  
Cloud App Security ahora admite la carga automática del Registro para Windows 10 (Fall Creators Update) y Windows Server, versión 1709 y posteriores, mediante un Docker para Windows. Para más información e instrucciones sobre cómo se puede configurar este, consulte [Docker en Windows local](discovery-docker-windows.md).

- Cloud App Security se integra con [Microsoft Flow](/flow/getting-started) para proporcionar una automatización de alertas personalizada y cuadernos de estrategias de orquestación. Para más información e instrucciones de integración, consulte [Integración con Flow para la automatización de alertas personalizada](flow-integration.md).

### <a name="cloud-app-security-release-137"></a>Notas de la versión 137 de Cloud App Security

Fecha de publicación: 25 de noviembre de 2018

- **Compatibilidad agregada para Dynamics**  
Cloud App Security ahora incluye compatibilidad para las actividades de Microsoft Dynamics que se admiten en el registro de auditoría de Office 365.

- **Examen del contenido cifrado (versión preliminar)**  
Cloud App Security ahora permite examinar el contenido protegido por las etiquetas de protección de Azure Information Protection. Esto le permitirá buscar contenido confidencial, incluso en archivos que ya se han cifrado mediante Azure Information Protection.

- **Aviso: Nueva terminología.**  
El nombre de las funcionalidades de los permisos de aplicación se ha cambiado para mayor claridad: ahora se denominan **aplicaciones de OAuth**.

### <a name="cloud-app-security-release-136"></a>Notas de la versión 136 de Cloud App Security

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

### <a name="cloud-app-security-release-133-134-135"></a>Notas de la versión 133, 134, 135 de Cloud App Security

Fecha de publicación: octubre de 2018

- **Nuevas directivas de detección de anomalías que se implementan gradualmente**  
  - La nueva directiva Filtración de datos a aplicaciones no autorizadas se habilita automáticamente para enviarle una alerta cada vez que un usuario o una dirección IP use una aplicación que no tenga permitido realizar una actividad que pueda suponer un intento de filtrar información de la organización.
    - La nueva directiva Varias actividades de eliminación de VM genera perfiles de su entorno y desencadena alertas cuando los usuarios eliminan varias máquinas virtuales en una sola sesión, en relación con la línea de base de su organización.

- **Servicio de clasificación de datos disponible para APAC**  
  - La inspección de contenido del servicio de clasificación de datos ahora está disponible para los clientes de APAC. Para obtener una lista de soporte técnico regional completo, consulte [Integración de los servicios de clasificación de datos de Microsoft](dcs-inspection.md).

- **Compatibilidad de Cloud Discovery con i-Filter**  
  - La característica de Cloud Discovery de Cloud App Security ahora tiene compatibilidad mejorada con el analizador Syslog de i-Filter.

### <a name="cloud-app-security-release-132"></a>Notas de la versión 132 de Cloud App Security

Fecha de publicación: 25 de septiembre de 2018

- **Control de aplicaciones de acceso condicional para Office 365 está ahora en versión preliminar pública**  
  - Control de aplicaciones de acceso condicional ahora admite Office 365 y cualquier aplicación que esté configurada con Open ID Connect.
  - Proporcione comentarios en una sesión: Esta nueva herramienta le permite enviar comentarios al equipo de Cloud App Security sobre el rendimiento de una aplicación bajo control de sesión, directamente desde dentro de la sesión.

- **Integración nativa con Microsoft Defender ATP para Shadow IT Discovery más allá de los límites de la empresa**  
  - Microsoft Cloud App Security ahora se integra de forma nativa con Protección contra amenazas avanzada (ATP) de Windows Defender para proporcionar las funcionalidades de Shadow IT Discovery sin implementación para el uso de la red corporativa de aplicaciones en la nube.  Esto le permite ejecutar Cloud Discovery en las máquinas, incluso cuando no están dentro de la red corporativa. También habilita la investigación basada en máquinas: después de identificar a un usuario de riesgo, puede comprobar todas las máquinas a las que el usuario ha tenido acceso para detectar posibles riesgos. Si identifica una máquina de riesgo, puede comprobar todos los usuarios que la usaban para investigar posibles riesgos. Para más información, consulte integración de Protección contra amenazas avanzada de Windows Defender con [Microsoft Cloud App Security](mde-integration.md).

- **Inspección de contenido para archivos cifrados**  
  - Cloud App Security admite ahora la inspección de contenido de archivos protegidos cifrados que se protegieron con Azure Information Protection. Ahora puede inspeccionar estos archivos cifrados para volver a clasificarlos e identificar infracciones adicionales de la directiva de seguridad y exposición de DLP.

### <a name="cloud-app-security-release-131"></a>Notas de la versión 131 de Cloud App Security

Fecha de publicación: 2 de septiembre de 2018

- **Revocación automática de los permisos en aplicaciones de OAuth de riesgo**  
Ahora puede controlar a qué aplicaciones de OAuth tienen acceso los usuarios, revocando el permiso de aplicación para las aplicaciones de OAuth en Office, Google o Salesforce. Al crear una **directiva de permisos de aplicación**, ahora puede establecer la directiva para revocar el permiso de una aplicación.

- **Analizador integrado adicional de Cloud Discovery compatible**  
Cloud Discovery ahora admite el formato de registro de Forcepoint Web Security Cloud.

### <a name="cloud-app-security-release-130"></a>Notas de la versión 130 de Cloud App Security

Fecha de publicación: 22 de agosto de 2018

- **Nueva barra de menús**  
Para proporcionar una experiencia de administración más coherente en los productos de Office 365 y permitirle cambiar más fácilmente entre las soluciones de seguridad de Microsoft, la barra de menús del portal de Cloud App Security se ha desplazado al lado izquierdo de la pantalla. Esta experiencia de navegación coherente le ayuda a orientarse al pasar de un portal de seguridad de Microsoft a otro.

- **Impacto de la puntuación de la aplicación OAuth**  
Ahora puede enviar los comentarios del equipo de Cloud App Security para indicarnos si hay una aplicación de OAuth detectada en la organización que parece malintencionada. Esta nueva característica le permite formar parte de nuestra comunidad de seguridad y mejorar el análisis y la puntuación de riesgo de las aplicaciones de OAuth. Para más información, consulte [Administrar permisos de aplicación](manage-app-permissions.md).

- **Nuevos analizadores de Cloud Discovery**  
Los analizadores de Cloud Discovery admiten ahora Secure Cloud Gateway y Sophos XG de iboss.

### <a name="cloud-app-security-release-129"></a>Notas de la versión 129 de Cloud App Security

Fecha de publicación: 5 de agosto de 2018

- **Nuevas directivas de detección de anomalías: reglas de correo electrónico sospechosas**  
Se agregaron nuevas directivas de detección de anomalías que detectan reglas de reenvío de correo electrónico sospechosas, por ejemplo, si un usuario creó una regla de bandeja de entrada sospechosa que reenvía una copia de todos los correos electrónicos a una dirección externa.

- Esta versión incluye correcciones y mejoras para varios problemas.

### <a name="cloud-app-security-release-128"></a>Notas de la versión 128 de Cloud App Security

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

### <a name="cloud-app-security-release-127"></a>Notas de la versión 127 de Cloud App Security

Publicado el 8 de julio de 2018

- Ahora tiene la capacidad de ver actividades genéricas para Office 365. En el **Registro de actividad** y en las **Directivas de actividad** ahora puede filtrar las actividades de Office 365 para las actividades **sin especificar**. Revisar estas actividades le permite investigar la información sobre las actividades realizadas que todavía no están clasificadas por tipo en Cloud App Security, y puede usar estas actividades para enviar solicitudes al equipo de Cloud App Security para crear nuevos tipos de actividad basados en estas actividades.

### <a name="cloud-app-security-release-126"></a>Notas de la versión 126 de Cloud App Security

Publicado el 24 de junio de 2018

- **Disponibilidad general de Control de aplicaciones de acceso condicional**  
Control de aplicaciones de acceso condicional (proxy inverso) de Microsoft Cloud App Security ahora está disponible para todas las aplicaciones de SAML. Control de aplicaciones de acceso condicional se integra directamente con las directivas de acceso condicional de Azure AD para **supervisar y controlar las sesiones de los usuarios en tiempo real**, a la vez que permite que sean productivas. Desde la primera versión preliminar de la característica, se han realizado muchas características y mejoras, entre las que se incluyen:
  - La capacidad de crear una [directiva de acceso](access-policy-aad.md) para administrar el acceso a las mismas aplicaciones desde clientes nativos, además de crear una directiva de sesión para el tráfico del explorador.
  - El proceso de incorporación de la aplicación se optimizó para admitir aplicaciones SAML personalizadas en su organización.
  - Como parte de la red mundial de Azure, se han mejorado la integración y la interfaz para ofrecer una experiencia sin problemas para los usuarios ubicados en cualquier lugar del mundo.

- **Disponibilidad general de la inspección de contenido con el Servicio de clasificación de datos de Microsoft**  
La integración de Microsoft Cloud App Security con los Servicios de clasificación de datos de Microsoft ahora está disponible con carácter general. Esta integración le permite usar el servicio de clasificación de datos de Microsoft de forma nativa para clasificar los archivos de las aplicaciones en la nube. Para más información, consulte [Integración de los servicios de clasificación de datos de Microsoft](dcs-inspection.md). Esta característica solo está disponible actualmente en EE. UU. y Europa (excepto en Francia).

- **Informe ejecutivo de Cloud Discovery**  
Microsoft Cloud App Security está implementando gradualmente la funcionalidad para generar un informe ejecutivo en PDF de Cloud Discovery. Este informe proporciona información general sobre el uso de Shadow IT que se ha identificado en la organización, destacando las principales aplicaciones y los usuarios en uso en general y en las principales categorías, y se centra en el riesgo que Shadow IT supone en la organización. Además, el informe proporciona una lista de recomendaciones para mejorar la visibilidad y el control sobre Shadow IT en la organización. Use este informe para asegurarse de que se eliminan riesgos y amenazas potenciales y de que la organización sigue siendo segura.

- **Detección de malware**  
La funcionalidad de detección de malware se está implantando de forma gradual para **detectar automáticamente los archivos maliciosos en el almacenamiento en la nube**, con independencia del tipo de archivo. Microsoft Cloud App Security usa la inteligencia sobre amenazas de Microsoft para reconocer si ciertos archivos están asociados a ataques de malware conocidos o son potencialmente malintencionados. Para más información, consulte [Directivas de detección de anomalías](anomaly-detection-policy.md).

- **Corrección automatizada de actividades sospechosas**  
Ahora puede establecer acciones de corrección automática para una sesión sospechosa desencadenadas por las directivas de detección de anomalías. Esta mejora le permite recibir alertas al instante cuando se produce una vulneración y **aplicar acciones de gobierno automáticamente**, como suspender al usuario. Para más información, consulte [Directivas de detección de anomalías](anomaly-detection-policy.md#adp-automated-gov).

- **Evaluación de la configuración de seguridad para Azure**  
Microsoft Cloud App Security está implementando de forma gradual la funcionalidad de obtener una evaluación de la configuración de seguridad del entorno de Azure, y proporciona recomendaciones para el control de la seguridad y los valores de configuración que falten. Por ejemplo, le indicará si falta la autenticación multifactor para los usuarios administrativos. Para más información, consulte [Configuración de seguridad para Azure](security-config.md).

- **Detección automatizada de aplicaciones de OAuth de riesgo**  
Además de la investigación existente de aplicaciones de OAuth conectadas al entorno, ahora Microsoft Cloud App Security está implementando de forma gradual la funcionalidad para establecer notificaciones automatizadas que avisen cuando una aplicación de OAuth cumple determinados criterios. Por ejemplo, puede recibir automáticamente una alerta cuando haya aplicaciones que requieran un nivel de permisos elevado y que hayan sido autorizadas por más de 50 usuarios. Para obtener más información, consulte [Directivas de permisos de aplicación](app-permission-policy.md).

- **Compatibilidad con la administración de proveedores de servicios de seguridad administrada (MSSP)**  
Microsoft Cloud App Security ahora proporciona una mejor experiencia de administración para MSSP. Los usuarios externos ahora se pueden configurar como administradores y se les puede asignar cualquiera de los [roles disponibles actualmente en Microsoft Cloud App Security](manage-admins.md). Además, para permitir que MSSP proporcionen servicios en varios inquilinos de cliente, los administradores con derechos de acceso a más de un inquilino ahora pueden cambiar con facilidad los inquilinos dentro del portal. Para obtener información sobre cómo administrar administradores, consulte [Administrar los administradores](manage-admins.md).

- **Integración con la disponibilidad general de DLP externa**  
Microsoft Cloud App Security permite [aprovechar las inversiones existentes en sistemas de clasificación de terceros](icap-stunnel.md), como soluciones de prevención de pérdida de datos (DLP), y permite examinar el contenido de aplicaciones en la nube mediante las implementaciones que se ejecutan en el entorno. Para obtener más información, consulte [Integración de DLP externa](icap-stunnel.md).

### <a name="cloud-app-security-release-125"></a>Notas de la versión 125 de Cloud App Security

Fecha de publicación: 10 de junio de 2018

- **Nueva funcionalidad de investigación de los usuarios principales:**  
Microsoft Cloud App Security agregó un nuevo widget de investigación al panel que muestra los usuarios principales por el número de alertas de detección de amenazas abiertas. Este widget de investigación le permite centrar su investigación de amenazas en usuarios con el mayor número de sesiones sospechosas.

- **Compatibilidad con los cubos S3 de AWS:**  
Microsoft Cloud App Security ahora puede detectar cubos S3 de AWS y sus niveles de uso compartido. Esto proporciona alertas y visibilidad de los cubos AWS de acceso público. También le permite crear directivas basadas en cubos y aplicar una gobernanza automática. Además, hay una nueva plantilla de directiva disponible llamada **Cubos S3 de acceso público (AWS)** que puede usar para crear con facilidad una directiva que controle su almacenamiento de AWS. Para habilitar estas nuevas funcionalidades, asegúrese de actualizar sus aplicaciones conectadas de AWS agregando los nuevos permisos descritos en [Conectar AWS](connect-aws-to-microsoft-cloud-app-security.md).

- **Privilegios de administración basados en grupos de usuarios**:  
ahora puede establecer permisos administrativos en administradores de Microsoft Cloud App Security por grupo de usuarios. Por ejemplo, puede establecer un usuario específico como administrador solo para los usuarios de Alemania. Esto permitiría al usuario ver y modificar la información en Microsoft Cloud App Security solo para el grupo de usuarios “Alemania: todos los usuarios”. Para obtener más información, consulte [Administrar el acceso de administrador](manage-admins.md).

### <a name="cloud-app-security-release-124"></a>Notas de la versión 124 de Cloud App Security

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

### <a name="cloud-app-security-release-123"></a>Notas de la versión 123 de Cloud App Security

Fecha de publicación: 13 de mayo de 2018

- **Ámbito de la directiva de detección de anomalías**:  
ahora se pueden asignar los ámbitos correspondientes a las directivas de detección de anomalías. Esto le permite establecer cada directiva de detección de anomalías para incluir solo usuarios o grupos específicos y excluir usuarios o grupos específicos. Por ejemplo, puede establecer la actividad a partir de la detección de condados poco frecuentes para omitir un usuario específico que viaja de forma habitual.

### <a name="cloud-app-security-release-122"></a>Notas de la versión 122 de Cloud App Security

Fecha de publicación: 29 de abril de 2018

- Implementación gradual: ahora puede **establecer permisos administrativos en administradores de Microsoft Cloud App Security por aplicación**. Por ejemplo, puede establecer un usuario específico como administrador solo para G Suite. Esto permitiría al usuario ver y modificar la información en Microsoft Cloud App Security solo al relacionarse exclusivamente con G Suite. Para obtener más información, consulte [Administrar el acceso de administrador](manage-admins.md).

- Implementación gradual: **los roles de administrador de Okta ahora se pueden ver** en Microsoft Cloud App Security y están disponibles para cada rol como etiqueta en **Configuración** > **Grupos de usuarios**.

### <a name="cloud-app-security-release-121"></a>Notas de la versión 121 de Cloud App Security

Fecha de publicación: 22 de abril de 2018

- La versión preliminar pública de **Control de aplicaciones de acceso condicional (anteriormente denominado proxy de Cloud App Security)** se ha mejorado con funcionalidades que facilitan una visibilidad más profunda de diversas aplicaciones y control sobre las mismas. Ahora puede crear una directiva de sesión con un filtro *Tipo de actividad* para supervisar y bloquear diferentes actividades específicas de la aplicación. Este nuevo filtro aumenta las características de control de descarga de archivos existentes para proporcionarle un control exhaustivo de las aplicaciones de su organización y trabaja en sintonía con el acceso condicional de Azure Active Directory para proporcionar visibilidad en tiempo real y control de sesiones de usuario de riesgo (por ejemplo, sesiones con usuarios de colaboración B2B o usuarios procedentes de un dispositivo no administrado). Para obtener más información, consulte [Directivas de sesión](session-policy-aad.md).

- Implementación gradual: **se han mejorado las directivas de detección de anomalías** de Cloud App Security para incluir dos nuevos tipos de detección de amenazas: actividad de ransomware y actividad del usuario cancelado. Cloud App Security amplió sus funcionalidades de detección de ransomware con la detección de anomalías para garantizar una cobertura más completa frente a los ataques sofisticados de ransomware. Al usar nuestra experiencia en investigación de seguridad para identificar patrones de comportamiento que reflejan la actividad de ransomware, Cloud App Security garantiza una protección holística y sólida. La actividad del usuario cancelado le permite supervisar las cuentas de usuarios cancelados, cuyo aprovisionamiento puede haberse cancelado de las aplicaciones corporativas, pero en muchos casos siguen reteniendo el acceso a determinados recursos corporativos. Para obtener más información, consulte [Obtención de análisis de comportamiento y detección de anomalías instantáneos](anomaly-detection-policy.md).

### <a name="cloud-app-security-release-120"></a>Notas de la versión 120 de Cloud App Security

Fecha de publicación: 8 de abril de 2018

- En Office 365 y Azure AD, estamos implementando gradualmente la capacidad de detectar aplicaciones internas como actividades de la cuenta de usuario realizadas por las aplicaciones de Office 365 y Azure AD (tanto internas como externas). Esto le permite crear directivas que le avisarán si una aplicación realiza actividades inesperadas y no autorizadas.

- Al exportar una lista de permisos de aplicación a csv, se incluyen campos adicionales como publicador, nivel de permisos y uso de la comunidad para ayudar con el proceso de cumplimiento e investigación.

- La aplicación conectada de ServiceNow se ha mejorado para que las actividades de servicio internas dejen de registrarse como si las realizara el "invitado" y dejen de desencadenar alertas de falsos positivos. Estas actividades ahora se representan como N/D como todas las demás aplicaciones conectadas.

### <a name="cloud-app-security-release-119"></a>Notas de la versión 119 de Cloud App Security

Fecha de publicación: 18 de marzo de 2018

- En la página Intervalos de direcciones IP se incluyen direcciones IP detectadas por Cloud App Security. Entre estas se incluyen direcciones IP para servicios en la nube identificados, como Azure y Office 365, así como la fuente de inteligencia sobre amenazas que enriquece automáticamente direcciones IP con información sobre direcciones IP de riesgo conocidas.

- Si Cloud App Security intenta ejecutar una acción de gobernanza en un archivo, pero no lo consigue porque el archivo está bloqueado, ahora volverá a intentar la acción de gobernanza.

### <a name="cloud-app-security-release-118"></a>Notas de la versión 118 de Cloud App Security

Fecha de publicación: 4 de marzo de 2018

- Ahora puede aprovechar las funcionalidades de supervisión y detección de shadow IT de Microsoft Cloud App Security en sus propias aplicaciones personalizadas de propietario. La nueva capacidad de agregar aplicaciones personalizadas a Cloud Discovery le permite supervisar el uso de la aplicación y recibir avisos sobre los cambios en el patrón de uso. Para obtener más información, consulte el artículo sobre cómo [proteger las aplicaciones personalizadas](cloud-discovery-custom-apps.md). Esta característica se está implantando gradualmente.

- Se rediseñaron las páginas **Configuración** del portal de Cloud App Security. El nuevo diseño consolida todas las páginas de configuración, proporciona la funcionalidad de búsqueda y un diseño mejorado.

- Cloud Discovery ahora admite Barracuda F-Series Firewalls y Barracuda F-Series Firewall Web Log Streaming.

- La funcionalidad de búsqueda de las páginas Usuario y Dirección IP ahora habilita Autocompletar para que pueda encontrar lo que busca con mayor facilidad.

- Ahora puede realizar acciones en masa en las páginas de configuración de exclusión de entidades y direcciones IP. Esto le permitirá seleccionar con más facilidad varios usuarios o direcciones IP y evitar que se supervisen como parte de Cloud Discovery en su organización.

### <a name="cloud-app-security-release-117"></a>Notas de la versión 117 de Cloud App Security

Publicado el 20 de febrero de 2018

- La mejor integración de Cloud App Security con Azure Information Protection ahora le permite proteger archivos en G Suite. Esta característica de versión preliminar pública permite examinar y clasificar archivos en G Suite y aplicar de forma automática las etiquetas de protección de Azure Information Protection. Para más información, consulte [Integración de Azure Information Protection](azip-integration.md).

- Ahora, Cloud Discovery es compatible con [Digital Arts i-FILTER](https://www.daj.jp/en/products/if/).

- La tabla de agentes SIEM ahora incluye más detalles para facilitar la administración.

### <a name="cloud-app-security-release-116"></a>Notas de la versión 116 de Cloud App Security

Fecha de publicación: 4 de febrero de 2018

- La directiva de detección de anomalías de Cloud App Security se ha mejorado con nuevas **detecciones basadas en los escenarios**, incluidos un viaje imposible, la actividad de una dirección IP sospechosa y varios intentos incorrectos de inicio de sesión. Las nuevas directivas se habilitan automáticamente, proporcionando una detección de amenazas predefinida en su entorno en la nube. Además, las nuevas directivas exponen más datos del motor de detección de Cloud App Security para ayudarle a acelerar el proceso de investigación e incluir amenazas en curso. Para obtener más información, consulte [Obtención de análisis de comportamiento y detección de anomalías instantáneos](anomaly-detection-policy.md).

- Implementación gradual: Cloud App Security ahora se correlaciona entre los usuarios y sus cuentas en las aplicaciones SaaS. Esto le permite investigar fácilmente todas las actividades para un usuario, en todas sus diferentes aplicaciones SaaS correlacionadas, sin importar la aplicación o cuenta que usaron.

- Implementación gradual: Cloud App Security ahora admite varias instancias de la misma aplicación conectada. Si tiene varias instancias de, por ejemplo, Salesforce (una para ventas y otra para marketing), podrá conectarlas a Cloud App Security y administrarlas desde la misma consola para crear directivas granulares y una investigación más profunda.

- Los analizadores de Cloud Discovery ahora admiten dos formatos de punto de control, XML y KPC.

### <a name="cloud-app-security-release-115"></a>Notas de la versión 115 de Cloud App Security

Fecha de publicación: 21 de enero de 2018

- Esta versión proporciona una experiencia mejorada al seleccionar carpetas específicas en las directivas de archivos. Ahora puede ver y seleccionar con facilidad varias carpetas para incluirlas en una directiva.
- En la página **Aplicaciones detectadas**:
  - la característica de etiquetado masivo le permite aplicar etiquetas personalizadas (además de las etiquetas autorizadas y no autorizadas).
  - Al **generar un informe de direcciones IP** o **generar un informe de usuarios**, los informes exportados ahora incluyen la información sobre si el tráfico tenía su origen en aplicaciones autorizadas o no autorizadas.
- Ahora puede solicitar un nuevo conector de aplicaciones de API del equipo de Microsoft Cloud App Security directamente en el portal, en la página **Conectar una aplicación**.

### <a name="cloud-app-security-release-114"></a>Notas de la versión 114 de Cloud App Security

Fecha de publicación: 7 de enero de 2018

- A partir de la versión 114, implementamos gradualmente la capacidad de crear y guardar consultas personalizadas en las páginas Registro de actividad y Aplicaciones detectadas. Las consultas personalizadas permiten crear plantillas de filtro que se pueden reutilizar para una investigación en profundidad. Además, las **consultas sugeridas** se han agregado para proporcionar plantillas de investigación predefinidas para filtrar las actividades y aplicaciones detectadas. Las **consultas sugeridas** incluyen filtros personalizados para identificar riesgos como actividades de suplantación, actividades del administrador, aplicaciones de almacenamiento en la nube no compatibles de riesgo, aplicaciones empresariales con cifrado débil y riesgos de seguridad. Puede usar las **consultas sugeridas** como punto de partida, modificarlas como mejor le parezca y, a continuación, guardarlas como nueva consulta. Para obtener más información, consulte [Consultas y filtros de actividad](activity-filters-queries.md) y [Consultas y filtros de aplicaciones detectadas](discovered-app-queries.md).

- Ahora puede comprobar el estado del servicio de Cloud App Security yendo a [status.cloudappsecurity.com](https://status.cloudappsecurity.com) o directamente desde dentro del portal haciendo clic en **Ayuda**>**Estado del sistema**.

## <a name="updates-made-in-2017"></a>Actualizaciones realizadas en 2017

### <a name="cloud-app-security-release-113"></a>Notas de la versión 113 de Cloud App Security

Fecha de publicación: 25 de diciembre de 2017

- Nos complace anunciar que Cloud App Security ahora permite una mayor integración con Azure Information Protection. Esta característica de versión preliminar pública permite examinar y clasificar archivos en aplicaciones en la nube y aplicar de forma automática las etiquetas de protección de Azure Information Protection. Esta característica está disponible en Box, SharePoint y OneDrive. Para más información, consulte [Integración de Azure Information Protection](azip-integration.md).

- Los analizadores de registros de Cloud Discovery ahora admiten formatos genéricos: LEEF, CEF y W3C.

### <a name="cloud-app-security-release-112"></a>Versión 112 de Cloud App Security

Fecha de publicación: 10 de diciembre de 2017

- Ahora puede tener acceso al espacio de información relevante haciendo clic en un nombre de usuario o la dirección IP en el registro de actividad.
- Al investigar actividades, ahora puede ver fácilmente todas las actividades del mismo período de tiempo desde el espacio de información haciendo clic en el icono de reloj. El icono de reloj le permite ver todas las actividades realizadas en un período de 48 horas en relación con la actividad que está viendo.
- Se han realizado mejoras en el analizador de registros de Cloud Discovery para Juniper SRX.
- En el caso de las actividades supervisadas por el proxy, el **objeto de actividad** se ha expandido para incluir información pertinente para los exámenes de DLP. Las directivas coincidentes se han expandido para incluir las infracciones de DLP (si existen).

### <a name="cloud-app-security-release-111"></a>Notas de la versión 111 de Cloud App Security

Publicado el 26 de noviembre de 2017

- Las directivas de detección ahora admiten etiquetas de la aplicación como condición y acción de gobernanza. Esta adición le permite etiquetar automáticamente las aplicaciones recién detectadas con etiquetas personalizadas, tales como **Tendencias en aplicaciones**. También puede usar la etiqueta de la aplicación como filtro. Por ejemplo, "Avisarme cuando una aplicación de la" reproducción "tiene más de 100 usuarios en un solo día".

- El filtro **Tiempo** se ha mejorado para hacerlo más fácil de usar.

- La inspección de contenido ahora permite distinguir entre contenido, metadatos y nombre de archivo, lo que permite seleccionar lo que se quiere inspeccionar.

- Se agregó una nueva acción de gobernanza para G Suite. Ahora puede **reducir el acceso público** a los archivos compartidos. Esta acción permite establecer que los archivos disponibles públicamente solo estén disponibles con un vínculo compartido.

- Todas las actividades de inicio de sesión de OKTA en otras aplicaciones se mostrarán ahora en Cloud App Security como originadas desde OKTA. Puede ver y filtrar en función de la aplicación de destino en la que se realizó el inicio de sesión en el campo **objetos de actividad** de la actividad.

### <a name="cloud-app-security-release-110"></a>Notas de la versión 110 de Cloud App Security

Publicado el 12 de noviembre de 2017

- Ahora disponible con carácter general: hemos empezado a aplicar un nuevo modo de implementación para el recopilador de registros. Además de la implementación actual basada en el dispositivo virtual, el nuevo recopilador de registros basado en Docker (contenedor) puede instalarse como un paquete en [máquinas Ubuntu](discovery-docker.md), tanto locales como en Azure. Cuando se usa Docker, el cliente es el propietario del equipo host y puede aplicarle revisiones y supervisarlo libremente.

- Con el nuevo signo de interrogación azul en la esquina, ahora puede acceder a la página de documentación pertinente de Cloud App Security en docs.microsoft.com desde las páginas del portal. Cada vínculo es contextual, le lleva a la información que necesita en función de la página en la que se encuentra.
- Ahora puede enviar comentarios desde cada página del portal de Cloud App Security. Los comentarios le permiten informar sobre errores, solicitar nuevas características y compartir su experiencia directamente con el equipo de Cloud App Security.
- Se han realizado mejoras en la capacidad de detección en la nube para reconocer subdominios para investigaciones de análisis profundo del uso de la nube de la organización. Para más información, consulte [Trabajar con aplicaciones detectadas](discovered-apps.md).

### <a name="cloud-app-security-release-109"></a>Notas de la versión 109 de Cloud App Security

Publicado el 29 de octubre de 2017

- La implantación de la característica de proxy de Microsoft Cloud App Security ha comenzado. El proxy de Microsoft Cloud App Security proporciona las herramientas que necesita para tener visibilidad en tiempo real y control del acceso al entorno en la nube y a las actividades realizadas en él. Por ejemplo:

  - Bloquee las descargas antes de que se realicen para evitar la pérdida de datos.
  - Establezca reglas que obliguen a proteger con cifrado los datos almacenados y descargados de la nube.
  - Obtenga visibilidad de los puntos de conexión no protegidos para que pueda supervisar lo que se hace en los dispositivos no administrados.
  - Controle el acceso desde redes no corporativas o direcciones IP de riesgo.

  Para más información, vea [Proteger las aplicaciones con el control de la aplicación de acceso condicional](proxy-intro-aad.md).

- Implementaremos gradualmente la capacidad para aplicar filtros a partir de nombres de actividad de servicio específicos. Este nuevo filtro Tipo de actividad es más granular y le permite supervisar actividades de la aplicación concretas, en lugar de los tipos de actividad más generales habituales. Por ejemplo, antes se podía filtrar por el **Comando Ejecutar**, mientras que ahora se puede filtrar por cmdlets de EXO específicos. El nombre de actividad también se puede ver en el cajón de actividades, en **Tipo (en la aplicación)**. Esta capacidad acabará reemplazando al filtro Tipo de actividad.

- Cloud Discovery ya admite Cisco ASA con FirePOWER.

- Se han realizado mejoras de rendimiento en las páginas de IP y usuario de Discovery para mejorar la experiencia del usuario.

### <a name="cloud-app-security-releases-105-106-107-108"></a>Versiones 105, 106, 107, 108 de Cloud App Security

Publicado en septiembre/octubre de 2017

- Ahora, Cloud App Security incluye un centro de datos en la Unión Europea. Así, aparte de nuestro centro de datos en Estados Unidos, el centro de datos de la UE permitirá a los clientes de Cloud App Security cumplir plenamente con las nuevas normas y certificaciones europeas y las que están por venir.
- Se han agregado nuevos filtros a la página **Conectores de aplicaciones** que permiten un filtrado más sencillo y obtener más información.
- Se ha mejorado Cloud Discovery en los archivos de registro que contienen solo información de las direcciones IP de destino.

### <a name="cloud-app-security-release-104"></a>Notas de la versión 104 de Cloud App Security

Fecha de publicación: 27 de agosto de 2017

- Ahora puede agregar intervalos de direcciones IP de forma masiva creando un script mediante la **API de intervalos de direcciones IP**. La API puede encontrase en la barra de menús del portal de Cloud App Security haciendo clic en el signo de interrogación y después en **Documentación de API**.
- Cloud Discovery ahora ofrece una visibilidad mejorada de las transacciones bloqueadas. Para ello, presenta tanto las transacciones totales como las bloqueadas.
- Ahora puede filtrar aplicaciones en la nube en función de si tienen la certificación **ISO 27017** o no. Este nuevo factor de riesgo del catálogo de aplicaciones en la nube determina si el proveedor de la aplicación tiene esta certificación. ISO 27017 establece los controles y directrices comúnmente aceptados para el procesamiento y la protección de la información de usuario en un entorno informático en la nube pública.
- Para ayudarle a prepararse para el cumplimiento de RGPD, hemos recopilado las instrucciones de preparación de RGPD desde las aplicaciones en la nube del catálogo de aplicaciones en la nube. Aún no afecta a la puntuación de riesgo de la aplicación, pero proporciona un vínculo a la página de preparación de RGPD del editor de la aplicación, cuando se proporciona. Microsoft no ha comprobado el contenido y no es responsable de su validez.

### <a name="cloud-app-security-release-103"></a>Notas de la versión 103 de Cloud App Security

Publicado el 13 de agosto de 2017

- Cloud App Security ahora incluye compatibilidad de protección nativa de Azure Information Protection con los siguientes archivos de Office: .docm, .docx, .dotm, .dotx, .xlam, .xlsb, .xlsm, .xlsx, .xltx, .xps, .potm, .potx, .ppsx, .ppsm, .pptm, .pptx, .thmx, .vsdx, .vsdm, .vssx, .vssm, .vstx, .vstm (en lugar de protección genérica).

- Se concederán automáticamente permisos similares en Cloud App Security a cualquier administrador de cumplimiento de Azure Active Directory. Los permisos incluyen la capacidad de solo leer y administrar alertas, crear y modificar directivas de archivo, permitir acciones de control de archivos y ver todos los informes integrados en Administración de datos.

- Se ha ampliado el contexto de infracción de DLP de 40 a 100 caracteres para ayudarle a entender mejor el contexto de la infracción.

- Se incluyen mensajes de error detallados en la herramienta de carga de registros personalizados de Cloud Discovery para permitirle solucionar fácilmente los errores en la carga de registros.

- El script del bloque de Cloud Discovery se ha ampliado para admitir el formato de Zscaler.

- Nuevo factor de riesgo del Catálogo de aplicaciones en la nube: retención de datos después de la finalización de la cuenta. Esto le permite asegurarse de que los datos se quitan completamente una vez que finaliza una cuenta dentro de una aplicación en la nube.

### <a name="cloud-app-security-release-102"></a>Versión 102 de Cloud App Security

Publicada el 30 de julio de 2017

- Debido a que la información de dirección IP es fundamental para casi todas las investigaciones, ahora puede ver información detallada sobre las direcciones IP en el cajón de actividades. Ahora puede hacer clic en la pestaña Dirección IP dentro de una actividad específica para ver los datos consolidados sobre la dirección IP. Los datos incluyen el número de alertas abiertas para la dirección IP específica, un gráfico de tendencias de actividad reciente y un mapa de ubicación. Esta característica permite explorar en profundidad. Por ejemplo, cuando se investigan alertas de viajes imposibles, puede comprender fácilmente dónde se usó la dirección IP y si participó o no en actividades sospechosas. Puede realizar acciones directamente en el cajón de direcciones IP que le permiten etiquetar una dirección IP como de riesgo, VPN o corporativa para facilitar una investigación futura y la creación de directivas. Para obtener más información, consulte información de [dirección IP](activity-filters.md#ip-address-insights) .

- En Cloud Discovery, ahora puede usar [formatos de registros personalizados](custom-log-parser.md) para [cargas de registros automatizadas](discovery-docker.md). Los formatos de registros personalizados le permiten automatizar fácilmente la carga de registros desde SIEM como servidores Splunk o cualquier otro formato no compatible.

- Las nuevas acciones de investigación de usuario permiten un nivel agregado de exploración en las investigaciones de usuario. En las páginas **Investigación**, ahora puede hacer clic con el botón derecho de una actividad, usuario o cuenta, y aplicar uno de los siguientes filtros nuevos para una investigación y filtración avanzadas: **Ver actividad relacionada**, **Ver gobernanza relacionada**, **Ver alertas relacionadas**, **Ver archivos con propietario**, **Ver archivos compartidos con este usuario**.

- El Catálogo de aplicaciones en la nube ahora contiene un campo nuevo de retención de datos después de la terminación de la cuenta. El factor de riesgo le permite asegurarse de que los datos se quitan completamente una vez que da término a una cuenta dentro de una aplicación de nube.

- Cloud App Security ahora cuenta con mayor visibilidad de las actividades relacionadas con objetos de Salesforce. Los objetos incluyen clientes potenciales, cuentas, campañas, oportunidades, perfiles y casos. Por ejemplo, la visibilidad sobre el acceso de las páginas de cuentas le permite configurar una directiva que le envía una alerta si un usuario ve una cantidad inusualmente grande de páginas de cuentas. Esto está disponible a través del conector de aplicaciones de Salesforce si tiene habilitada la supervisión de eventos de Salesforce en Salesforce (parte de Salesforce Shield).

- No realizar seguimiento ahora está disponible para los clientes de la versión preliminar privada. Ahora puede controlar qué datos de actividad de los usuarios se procesan. Esta característica permite establecer grupos específicos en Cloud App Security como "no rastrear". Por ejemplo, ahora puede decidir no procesar ningún dato de actividad de usuarios ubicados en Alemania ni ningún país que no esté sometido a ninguna ley de cumplimiento específica. Esto se puede implementar en todas las aplicaciones en Cloud App Security para una aplicación específica e, incluso, para una subaplicación específica. Además, esta característica se puede usar para facilitar la implementación gradual de Cloud App Security. Para más información sobre la versión preliminar privada de esta característica o para unirse a ella, póngase en contacto con el soporte técnico o con su representante de cuenta.

### <a name="cloud-app-security-release-100"></a>Notas de la versión 100 de Cloud App Security

Publicado el 3 de julio de 2017

**Nuevas características:**

- **Extensiones de seguridad:** se trata de un nuevo panel para la administración centralizada de todas las extensiones de seguridad de Cloud App Security.  Las extensiones incluyen la administración de tokens de API, agentes SIEM y conectores de DLP externa. El nuevo panel está disponible en Cloud App Security en "configuración".

  - Tokens de API: genere y administre sus propios [tokens de API](api-tokens.md) para integrar Cloud App Security con software de terceros mediante nuestras API de RESTful.
  - Agentes SIEM: la [integración de Siem](siem.md) se encontraba anteriormente en "configuración", que ahora está disponible como una pestaña en las extensiones de seguridad.
  - DLP externa (versión preliminar): Cloud App Security permite [aprovechar las inversiones existentes en sistemas de clasificación de terceros](icap-stunnel.md), como soluciones de prevención de pérdida de datos (DLP), y permite examinar el contenido de aplicaciones en la nube mediante las implementaciones que se ejecutan en el entorno. Póngase en contacto con el administrador de cuentas para tomar parte en la versión preliminar.

- **Autorizar o no autorizar automáticamente:** las nuevas directivas de detección de aplicaciones permiten que Cloud Discovery aplique automáticamente a las aplicaciones la etiqueta Autorizada/No autorizada. Esto le ofrece la posibilidad de identificar automáticamente las aplicaciones que infringen la Directiva y la normativa de la organización y agregarlas al script de bloqueo generado.
- **Etiquetas de archivo de Cloud App Security:** actualmente se pueden aplicar etiquetas de archivo de Cloud App Security para proporcionar más información sobre los archivos que se examinan. Ahora ya puede saber si se ha impedido que la DLP de Cloud App Security inspeccione los archivos porque estaban dañados o cifrados. Por ejemplo, puede configurar directivas para que le alerten y pongan en cuarentena archivos protegidos con contraseña que se comparten externamente. Esta característica está disponible para los archivos examinados después del 3 de julio de 2017.

    Puede filtrar estos archivos mediante las **etiquetas de clasificación** de filtro  >  **Cloud App Security**:

  - **Azure RMS encrypted** (Cifrado con Azure RMS): archivos cuyo contenido no se ha inspeccionado porque tienen establecido un cifrado de Azure RMS.
  - **Cifrado con contraseña**: archivos cuyo contenido no se ha inspeccionado porque el usuario los ha protegido con una contraseña.
  - **Archivo dañado**: archivos cuyo contenido no se ha inspeccionado porque no se ha podido leer su contenido.

- **Información de usuario**: la experiencia de investigación se ha mejorado para que incluya información predeterminada sobre el usuario activo. Con un solo clic, ahora puede ver una descripción detallada de los usuarios desde el cajón de actividades, la información incluye la ubicación desde la que se han conectado, con cuántas alertas abiertas están relacionados e información sobre sus metadatos.
- **App connector insights** (Información del conector de aplicaciones): en **Conectores de aplicaciones**, cada aplicación conectada incluye ahora un cajón de aplicaciones en la tabla para explorar más fácilmente su estado. Entre los detalles que se proporcionan se incluyen cuándo se ha conectado el conector de aplicaciones y cuándo se ha realizado la última comprobación de estado del conector. También puede supervisar el estado del examen de DLP en cada aplicación, es decir, el número total de archivos inspeccionados por DLP, así como el estado de los exámenes en tiempo real (exámenes solicitados frente a exámenes reales). Podrá saber si el porcentaje de archivos examinados por Cloud App Security en tiempo real es inferior al número solicitado, y si el inquilino excede su capacidad y experimenta un retraso en los resultados de DLP.

- **Personalización del Catálogo de aplicaciones en la nube:**

  - **Etiquetas de aplicación**: ahora puede crear etiquetas personalizadas para las aplicaciones. Estas etiquetas pueden usarse como filtros para profundizar un poco más en los tipos de aplicaciones específicos que quiere investigar. Por ejemplo, lista de supervisión personalizada, asignación a una unidad de negocio específica o aprobaciones personalizadas, como "aprobada por legal".
  - **Notas personalizadas**: ahora, a medida que revise y evalúe las diferentes aplicaciones detectadas en el entorno, puede guardar las conclusiones y la información en notas.
  - **Puntuación de riesgo personalizada**: ahora puede reemplazar la puntuación de riesgo de una aplicación. Por ejemplo, si la puntuación de riesgo de una aplicación es 8 y es una aplicación autorizada en la organización, puede cambiar la puntuación de riesgo a 10 para la organización. También puede agregar notas para que el motivo de este cambio le quede claro a los usuarios que revisen la aplicación.

- **Nuevo modo de implementación del recopilador de registros:** hemos empezado a aplicar un nuevo modo de implementación para el recopilador de registros. Además de la implementación actual basada en el dispositivo virtual, el nuevo recopilador de registros basado en Docker (contenedor) puede instalarse como un paquete en equipos Windows y Ubuntu locales y en Azure. Cuando se usa Docker, el cliente es el propietario del equipo host y puede aplicarle revisiones y supervisarlo libremente.

**Anuncios**

- El Catálogo de aplicaciones en la nube ahora admite más de 15 000 aplicaciones reconocibles
- Cumplimiento: Cloud App Security cuenta oficialmente con la certificación SOC1/2/3 de Azure. Para obtener la lista completa de certificaciones, consulte [ofertas de cumplimiento](https://www.microsoft.com/trustcenter/compliance/complianceofferings) y filtre los resultados de Cloud App Security.

**Otras mejoras:**

- **Análisis mejorado:** se ha mejorado el mecanismo de análisis de registros de Cloud Discovery. Es mucho menos probable que se produzcan errores internos.
- **Formatos de registro esperados:** ahora, el formato de registro esperado para los registros de Cloud Discovery proporciona ejemplos del formato Syslog y del formato FTP.
- **Estado de carga del recopilador de registros:** ahora puede ver el estado del recopilador de registros en el portal y solucionar los errores más rápidamente gracias a las notificaciones de estado en el portal y las alertas del sistema.

### <a name="cloud-app-security-release-99"></a>Notas de la versión 99 de Cloud App Security

Publicado el 18 de junio de 2017

**Nuevas características**

- Ahora puede requerir a los usuarios que inicien sesión de nuevo en todas las aplicaciones de Office 365 y de Azure AD. Requerir el inicio de sesión es una solución rápida y eficaz en el caso de alertas de actividad sospechosa del usuario y cuentas en peligro. Encontrará la nueva acción de gobernanza en la configuración de directiva y las páginas de alertas, junto a la opción Suspender usuario.
- Ahora puede filtrar las actividades para **agregar asignación de roles de suplantación** en el registro de actividades. Esta actividad permite detectar si un administrador ha concedido un rol de **suplantación de aplicación** a una cuenta de usuario o del sistema, mediante el cmdlet **New-ManagementRoleAssignment**. Este rol permite al suplantador realizar operaciones con los permisos asociados a la cuenta suplantada, en lugar de los permisos asociados a la cuenta del suplantador.

**Mejoras de Cloud Discovery:**

- Ahora es posible mejorar los datos de Cloud Discovery con datos de nombre de usuario de Azure Active Directory. Cuando se habilita esta característica, el nombre de usuario que se recibe en los registros de tráfico de detección se hará coincidir con el nombre de usuario de Azure AD y se reemplazará por este. Las mejoras incluyen las siguientes características nuevas:
  - Puede investigar el uso de Shadow IT por parte del usuario de Azure Active Directory.
  - Puede correlacionar el uso de las aplicaciones en la nube detectadas con las actividades de API recopiladas.
  - Después, puede crear registros personalizados en función de los grupos de usuarios de Azure AD. Por ejemplo, un informe de Shadow IT para un departamento de marketing específico.
- Se han realizado mejoras en el analizador de Syslog de Juniper. Ahora admite los formatos welf y sd-syslog.
- Se han realizado mejoras en el analizador de Palo Alto para optimizar la detección de aplicaciones.
- Para comprobar que los registros se están cargando correctamente, ahora puede ver el estado de los recopiladores de registros en el portal de Cloud App Security.

**Mejoras generales:**

- Las etiquetas de dirección IP integradas y las etiquetas IP personalizadas ahora se consideran de forma jerárquica, y las etiquetas IP personalizadas tienen prioridad sobre las etiquetas IP integradas. Por ejemplo, si una dirección IP se etiqueta como **De riesgo** en función de la información disponible sobre las amenazas pero hay una etiqueta IP personalizada que la identifica como **Corporativa**, la categoría y las etiquetas personalizadas tendrán prioridad.

### <a name="cloud-app-security-release-98"></a>Notas de la versión 98 de Cloud App Security

Publicado el 4 de junio de 2017

**Cloud Discovery actualizaciones:**

- Los usuarios ahora pueden realizar el filtrado avanzado de aplicaciones detectadas. El filtrado permite realizar una investigación en profundidad. Por ejemplo, filtrar aplicaciones según el uso. ¿Qué cantidad de tráfico de carga es de aplicaciones detectadas de ciertos tipos? ¿Cuántos usuarios han usado determinadas categorías de aplicaciones detectadas? También puede seleccionar al mismo tiempo varias categorías en el panel izquierdo.
- Se ha iniciado la implementación de nuevas plantillas para Cloud Discovery basadas en búsquedas frecuentes, por ejemplo, "aplicación de almacenamiento en la nube no compatible". Estos filtros básicos se pueden usar como plantillas para realizar el análisis de las aplicaciones detectadas.
- Para facilitar el uso, ahora puede realizar determinadas acciones como autorizar y no autorizar varias aplicaciones de una sola vez.
- Estamos implementando la capacidad de crear informes de detección personalizados en función de los grupos de usuarios de Azure Active Directory. Por ejemplo, si quiere ver el uso de la nube por parte del departamento de marketing, puede importar el grupo de marketing mediante la característica para importar grupos de usuarios y, después, crear un informe personalizado para este grupo.

**Nuevas características:**

- Se ha completado la implementación de RBAC para los lectores de seguridad. Esta característica permite administrar los permisos que se conceden a los administradores dentro de la consola de Cloud App Security. De forma predeterminada, todos los administradores de Azure Active Directory, los administradores globales de Office 365 y los administradores de seguridad tienen permisos completos en el portal. Todos los lectores de seguridad de Azure Active Directory y Office 365 tienen acceso de solo lectura en Cloud App Security. Puede agregar administradores adicionales o reemplazar los permisos mediante la opción "administrar acceso". Para obtener más información, vea [administrar permisos de administrador](manage-admins.md).
- Ahora estamos implementando informes de inteligencia de amenazas detallados para las direcciones IP de riesgo detectadas por el gráfico de seguridad inteligente de Microsoft. Cuando una red de robots (botnet) realice una actividad, verá el nombre de la red de robots (si está disponible) con un vínculo a un informe detallado sobre la botnet específica.

### <a name="cloud-app-security-release-97"></a>Notas de la versión 97 de Cloud App Security

Publicado el 24 de mayo de 2017

**Nuevas características:**

- Al investigar archivos e infracciones de directivas, ahora puede ver todas las coincidencias de directivas en la página Archivos. Además, se ha mejorado la página de alertas de archivo para que ahora incluya una pestaña independiente para el historial del archivo específico. La mejora permite explorar en profundidad el historial de infracciones de todas las directivas del archivo específico. Cada evento del historial incluye una instantánea del archivo en el momento de la alerta e indica si el archivo se ha eliminado o se ha puesto en cuarentena.
- Ya está disponible la [cuarentena de administrador](use-case-admin-quarantine.md) en versión preliminar privada para archivos de Office 365 SharePoint y OneDrive para la Empresa. Esta característica permite poner en cuarentena archivos que coinciden con las directivas o establecer una acción automatizada para ponerlos en cuarentena. Poner en cuarentena quita los archivos del directorio de SharePoint del usuario y copia los originales en la ubicación de cuarentena de administrador que elija.

**Mejoras Cloud Discovery:**

- Se ha mejorado la compatibilidad de Cloud Discovery con los registros de Cisco Meraki.
- La opción para proponer una mejora de Cloud Discovery permite sugerir un nuevo factor de riesgo.
- Se ha mejorado el analizador de registros personalizado para que admita formatos de registro mediante la separación de la configuración de fecha y hora y para ofrecer la opción de establecer una marca de tiempo.
- Se ha empezado a implementar la capacidad de crear informes de detección personalizados en función de los grupos de usuarios de Azure Active Directory. Por ejemplo, si quiere ver el uso de la nube por parte del departamento de marketing, importe el grupo de marketing mediante la característica para importar grupos de usuarios y después cree un informe personalizado para este grupo.

**Otras actualizaciones:**

- Cloud App Security ahora incluye compatibilidad con las actividades de Microsoft Power BI que se admiten en el registro de auditoría de Office 365. Esta característica se está implantando gradualmente. Debe habilitar [esta funcionalidad en el portal de Power BI](https://powerbi.microsoft.com/documentation/powerbi-admin-auditing/).
- En las directivas de actividad, ahora puede establecer que se realicen acciones para enviar notificaciones y suspender al usuario en todas las aplicaciones conectadas. Por ejemplo, puede establecer una directiva para notificar siempre al administrador del usuario y suspender al usuario de inmediato si este tiene varios inicios de sesión erróneos en una aplicación conectada.

### <a name="oob-release"></a>Lanzamiento de OOM

- En respuesta a los ataques de ransomware que se están constatando en todo el mundo, el equipo de Cloud App Security agregó el domingo en el portal una nueva plantilla de [directiva de detección de posible actividad de ransomware](use-case-ransomware.md) que incluye la extensión de firma de WannaCrypt. Le recomendamos que establezca esta directiva hoy mismo.

### <a name="cloud-app-security-release-96"></a>Notas de la versión 96 de Cloud App Security

Fecha de publicación: 8 de mayo de 2017

**Nuevas características:**

- Continuación de la implementación gradual del permiso de Lector de seguridad, que le permite administrar los permisos que concede a los administradores dentro de la consola de Cloud App Security. De forma predeterminada, todos los administradores globales de Azure Active Directory y de Office 365, y los administradores de seguridad tienen permisos completos en el portal. Todos los lectores de seguridad de Azure Active Directory y Office 365 tendrán acceso de solo lectura en Cloud App Security. Para obtener más información, vea [administrar permisos de administrador](manage-admins.md).
- Implementación completada de Cloud Discovery para analizadores de registros definidos por el usuario para registros basados en CSV. Cloud App Security le permite configurar un analizador para los dispositivos que antes no eran compatibles, proporcionándole las herramientas para delinear las columnas que se correlacionan con datos específicos. Para obtener más información, vea [Uso del analizador de registros personalizado](custom-log-parser.md).

**Mejoras:**

- Cloud Discovery ahora admite dispositivos Juniper SSG.
- Se ha mejorado la compatibilidad de Cloud Discovery para los registros de Cisco ASA para una mejor visibilidad.
- Ahora puede ejecutar más fácilmente acciones masivas y seleccionar varios registros en las tablas del portal de Cloud App Security: la longitud de la página se ha aumentado para mejorar las operaciones masivas.
- Los informes integrados **Uso compartido externo por dominio** y **Propietarios de archivos compartidos** ahora se pueden ejecutar para datos de Salesforce.
- Estamos comenzando el lanzamiento de actividades de Salesforce adicionales que permiten realizar un seguimiento de la información interesante extraída de los datos de actividad. Estas actividades incluyen ver y editar cuentas, clientes potenciales, oportunidades y otros objetos de Salesforce interesantes.
- Se han agregado nuevas actividades de Exchange para permitirle supervisar los permisos que se concedieron para buzones o carpetas de buzones. Estas actividades incluyen:
  - Agregar permisos de destinatario
  - Quitar permisos de destinatario
  - Agregar permisos de carpeta de buzón
  - Quitar permisos de carpeta de buzón
  - Establecer permisos de carpeta de buzón

   Por ejemplo, ahora puede supervisar a los usuarios a los que se les han concedido permisos de **envío** a los buzones de otros usuarios y, como resultado, ahora pueden enviar mensajes de correo electrónico en su nombre.

### <a name="cloud-app-security-release-95"></a>Notas de la versión 95 de Cloud App Security

Publicado el 24 de abril de 2017

**Actualizaciones**

- La página **Cuentas** se ha actualizado con mejoras que facilitan la detección de riesgos. Ahora puede filtrar más fácilmente las cuentas internas y externas. Compruebe de un vistazo si un usuario tiene permisos de administrador. Puede realizar acciones en cada cuenta por aplicación, como quitar permisos, quitar las colaboraciones del usuario y suspender al usuario. Además, se muestran los [grupos de usuarios](user-groups.md) importados de cada cuenta.

- En el caso de las cuentas Microsoft profesionales (Office 365 y Azure Active Directory), Cloud App Security agrupa distintos identificadores de usuario como direcciones proxy, alias, SID, etc., en una sola cuenta. Todos los alias relacionados con una cuenta aparecen en la dirección de correo electrónico principal. Basándose en la lista de identificadores de usuario, en las actividades cuyo actor sea un identificador de usuario, dicho actor se mostrará como UPN (nombre principal de usuario). Se asignarán los grupos y se aplicarán las directivas de acuerdo con el UPN. Este cambio mejorará la investigación de actividades y fusionará todas las relacionadas con la misma sesión para detectar anomalías y directivas basadas en grupos. Esta característica se implementará de forma gradual durante el próximo mes.

- Se ha agregado la etiqueta Robot como un posible factor de riesgo en el informe integrado de uso del explorador. Ahora, además de etiquetar como obsoleto el uso del explorador, puede ver si ha sido un robot el que ha usado el explorador.
- Al crear una directiva de archivo de inspección de contenido, ahora puede establecer el filtro para incluir solo los archivos con un mínimo de 50 coincidencias.

### <a name="cloud-app-security-release-94"></a>Versión 94 de Cloud App Security

Publicada el 2 de abril de 2017

**Nuevas características:**

- Cloud App Security ahora se integra con Azure RMS. Puede proteger archivos en Office 365 OneDrive y Sharepoint Online con Microsoft Rights Management directamente desde el portal de Cloud App Security. La protección puede realizarse desde la página **Archivos**. Para obtener más información, vea [Integración de Azure Information Protection](azip-integration.md). En versiones futuras se proporcionará compatibilidad con aplicaciones adicionales.
- Hasta ahora, cuando las actividades de robot y rastreador (crawler) tienen lugar en la red, era especialmente difícil de identificar porque dichas actividades no las realizaba un usuario de la red. Sin su conocimiento, los robots y rastreadores pueden ejecutar herramientas malintencionados en los equipos. Ahora, Cloud App Security proporciona las herramientas para ver cuándo los robots y los rastreadores están realizando actividades en la red. Puede usar la nueva etiqueta de agente de usuario para filtrar actividades en el registro de actividades. La etiqueta de agente de usuario le permite filtrar todas las actividades que realizan por robots y usarlo para crear una directiva que le avise cada vez que se detecte este tipo de actividad. El usuario se actualizará cuando las versiones futuras incluyan esta actividad de riesgo como insertada en las alertas de detección de anomalías.
- La nueva página de permisos de aplicación unificada permite investigar más fácilmente los permisos que se han concedido a los usuarios a aplicaciones de terceros. Al hacer clic en **investigar**  >  **permisos de aplicación**, ahora puede ver una lista de todos los permisos que los usuarios dieron a las aplicaciones de terceros. Una página de permisos de aplicación por aplicación conectada le permite comparar mejor las distintas aplicaciones y los permisos concedidos. Para más información, vea [Administrar permisos de aplicación](manage-app-permissions.md).
- Puede filtrar los datos desde el cajón de tablas para una investigación más sencilla.
En el **Registro de actividades**, la tabla **Archivos** y las páginas **Permisos de aplicación** ahora se han mejorado con nuevas acciones contextuales, lo que facilita bastante los giros en el proceso de investigación. También agregamos vínculos rápidos a páginas de configuración y la capacidad de copiar los datos con un solo clic. Para obtener más información, vea la información sobre el [trabajo con los cajones de archivos y actividades](file-filters.md).
- Se ha completado el soporte para Microsoft Teams para la implementación de registros y alertas de actividad de Office 365.

### <a name="cloud-app-security-release-93"></a>Notas de la versión 93 de Cloud App Security

Fecha de publicación: 20 de marzo de 2017

**Nuevas características:**

- Ahora puede aplicar directivas para incluir o excluir grupos de usuarios importados.
- Anonimización de datos de Cloud Discovery ahora le permite configurar una clave de cifrado personalizada. Para más información, vea [Cloud Discovery Anonymization](cloud-discovery-anonymizer.md) (Anonimización de Cloud Discovery).
- Para tener más control sobre la administración de cuentas y de usuario, ahora tiene acceso directo a la configuración de la cuenta de Azure AD para cada usuario y cuenta desde dentro de la página **Cuenta**. Simplemente haga clic en el engranaje junto a cada usuario. Este cambio permite facilitar el acceso a la administración del grupo de características de administración de usuario avanzado, la configuración de MFA, los detalles sobre los inicios de sesión de usuario y la capacidad de bloquear el inicio de sesión.
- Ahora puede exportar un script de bloqueo para las aplicaciones sin aprobación a través de la API de Cloud App Security. Obtenga más información sobre las API en el portal de Cloud App Security haciendo clic en el signo de interrogación en la barra de menús, seguido por **Documentación de la API**.
- El conector de la aplicación de Cloud App Security para ServiceNow se ha expandido para incluir compatibilidad con tokens de OAuth (tal como se presenta en Ginebra, Helsinki y Estambul). Este cambio proporciona una conexión más sólida de la API con ServiceNow, que no se basa en el usuario de implementación. Para obtener más información, vea [Conectar ServiceNow con Microsoft Cloud App Security](connect-servicenow-to-microsoft-cloud-app-security.md). Los clientes existentes pueden actualizar su configuración en la página del conector de ServiceNow App.
- Si configura escáneres DLP adicionales de terceros, el estado del examen DLP ahora mostrará el estado de cada conector de forma independiente para mejorar la visibilidad.
- Cloud App Security ahora incluye compatibilidad para las actividades de Microsoft Teams que se admiten en el registro de auditoría de Office 365. Esta característica se está implantando gradualmente.
- En el caso de los eventos de suplantación de Exchange Online, ahora puede filtrar por el nivel de permiso usado-delegado, administrador o administrador delegado. Puede buscar eventos que muestren el nivel de suplantación que le interese en el **registro de actividad** mediante la búsqueda de elementos de **objetos de actividad**  >  **Item**.
- En el cajón de aplicaciones de la pestaña **Permisos de la aplicación** de aplicaciones Office 365, ahora puede ver el **publicador** de cada aplicación. También puede utilizar el publicador como un filtro para la investigación de las aplicaciones adicionales del mismo publicador.
- Las direcciones IP de riesgo aparecen ahora como un factor de riesgo independiente en lugar de ponderado en el factor de riesgo de la **ubicación** general.
- Cuando las etiquetas de Azure Information Protection están deshabilitadas en un archivo, las etiquetas deshabilitadas aparecerán como deshabilitadas en Cloud App Security. No se mostrarán las etiquetas eliminadas.

**Compatibilidad adicional de Salesforce:**

- Ahora puede suspender y quitar la suspensión de los usuarios de Salesforce en Cloud App Security. Esta acción puede realizarse en la pestaña **Cuentas** del conector de Salesforce. Haga clic en el engranaje al final de la fila de un usuario específico y seleccione **Suspender** o **Anular suspensión**. La suspensión y la anulación de la suspensión también se pueden aplicar como una acción de gobernanza como parte de una directiva. Todas las actividades de suspensión y de anulación de la suspensión realizadas en Cloud App Security se almacenarán en el [registro de control](governance-actions.md).
- Visibilidad mejorada para el uso compartido de contenido de Salesforce: ahora puede ver qué archivos se comparten con quién, incluidos los archivos compartidos públicamente, compartidos con grupos de archivos y compartidos con todo el dominio de Salesforce. La visibilidad mejorada se extenderá retroactivamente a aplicaciones de Salesforce conectadas nuevas y actuales. Puede que esta información tarde en actualizarse la primera vez.
- Mejoramos la cobertura de los siguientes eventos de Salesforce y los separamos de la actividad **Administrar usuarios**:
  - Editar permisos
  - Crear usuario
  - Cambio de rol
  - Restablecimiento de contraseña

### <a name="cloud-app-security-release-90-91-92"></a>Notas de la versión 90, 91 y 92 de Cloud App Security

Fecha de publicación: febrero de 2017

**Anuncio especial:**

Cloud App Security ahora está certificada oficialmente con Microsoft Compliance para ISO, HIPAA, CSA STAR y cláusulas de modelo EU, entre otros. Vea la lista completa de certificaciones en el artículo [Ofertas de cumplimiento de Microsoft](https://www.microsoft.com/trustcenter/compliance/complianceofferings) seleccionando Cloud App Security.

**Nuevas características:**

- **Importar grupos de usuarios (versión preliminar)**   Al conectar aplicaciones mediante conectores de API, Cloud App Security ahora permite importar grupos de usuarios de Office 365 y Azure Active Directory. Puede aprovechar la existencia de grupos de usuarios importados para investigar qué documentos consulta el departamento de Recursos Humanos, para comprobar si sucede algo inusual en el grupo ejecutivo o para verificar si un miembro del grupo de administración ha llevado a cabo alguna actividad fuera del país. Para obtener más información e instrucciones, vea [Importar grupos de usuarios](user-groups.md).

- En el registro de actividad, ahora puede filtrar los usuarios y los usuarios de grupos para mostrar las actividades realizadas por y en un usuario específico. Por ejemplo, puede investigar las actividades en las que el usuario ha suplantado a otras personas, así como las actividades en las que otras personas han suplantado a este usuario. Para obtener más información, vea [Actividades](activity-filters.md).

- Al investigar un archivo en la página **Archivos**, si profundiza en los **Colaboradores** de un archivo específico, ahora puede ver más información sobre ellos. Esta información incluye si son usuarios internos o externos, escritores o lectores (permisos de archivo), y cuando se comparte un archivo con un grupo ahora puede ver todos los usuarios que son miembros del grupo. Ver todos los usuarios le permite ver si los miembros del grupo son usuarios externos.

- Ahora hay compatibilidad con IPv6 disponible para todos los dispositivos.

- Cloud Discovery ahora admite dispositivos Barracuda.

- Las alertas del sistema de Cloud App Security ahora incluyen errores de conectividad SIEM. Para más información, consulte [Integración de SIEM](siem.md).

- Cloud App Security ahora es compatible con las actividades siguientes:

  - **Office 365, SharePoint/OneDrive**: actualizar la configuración de aplicaciones, quitar el propietario del grupo, eliminar sitio, crear carpeta.

  - **Dropbox**: agregar un miembro a un grupo, quitar un miembro de un grupo, crear grupo, cambiar el nombre de grupo, cambiar el nombre de un miembro de un equipo.

  - **Box**: quitar un elemento de un grupo, actualizar un recurso compartido de elemento, agregar un usuario a un grupo, eliminar un usuario de un grupo.

### <a name="cloud-app-security-release-89"></a>Notas de la versión 89 de Cloud App Security

Publicado el 22 de enero de 2017

**Nuevas características:**

- Estamos empezando a implementar la capacidad de ver los eventos de DLP del Centro de seguridad y cumplimiento de Office 365 en Cloud App Security. Si configuró directivas DLP en el Centro de seguridad y cumplimiento de Office 365, cuando se detecten coincidencias de directiva, las verá en el registro de actividades de Cloud App Security. La información del registro de actividades incluirá el archivo o el correo electrónico que desencadenó la coincidencia y la directiva o la alerta con la que coincide. La actividad **Evento de seguridad** permite ver las coincidencias de la directiva DLP de Office 365 en el registro de actividades de Cloud App Security. Con esta característica, puede:
  - Vea todas las coincidencias de DLP que proceden del motor DLP de Office 365.
  - Alertar sobre las coincidencias de la directiva DLP de Office 365 para un archivo específico, un sitio de SharePoint o una directiva.
  - Investigar las coincidencias de DLP con un contexto más amplio, por ejemplo, los usuarios externos que han obtenido acceso a un archivo o que han descargado un archivo que desencadenó una coincidencia de la directiva DLP.

- Se han mejorado las descripciones de las actividades para una mayor claridad y coherencia. Ahora, cada actividad proporciona un botón de comentarios. Si hay algo que no entiende o que tiene alguna pregunta, puede hacernos saber.

**Mejoras:**

- Se ha agregado una nueva acción de gobernanza para Office 365 que permite quitar todos los usuarios externos de un archivo. Por ejemplo, esta acción permite implementar directivas que **quitan recursos compartidos externos de los archivos que tienen una clasificación solo interna**.
- Se ha mejorado la identificación de los usuarios externos en SharePoint Online. Al filtrar por el grupo "usuarios externos", la cuenta de APP @"sharepoint" System no se mostrará.

### <a name="cloud-app-security-release-88"></a>Notas de la versión 88 de Cloud App Security

Publicado el 8 de enero de 2017

**Nuevas características:**

- Conecte su SIEM con Cloud App Security. Ahora puede enviar alertas y actividades automáticamente al SIEM de su elección mediante la configuración de agentes de SIEM. Ahora está disponible como versión preliminar pública.  Para obtener documentación completa y detalles, consulte la información relativa a la integración con SIEM.
- Ahora, Cloud Discovery es compatible con IPv6. Hemos incluido compatibilidad con Palo Alto y Juniper y en versiones futuras se incluirán más dispositivos.

**Mejoras:**

- Hay un nuevo factor de riesgo en el catálogo de aplicaciones de nube. Ahora puede valorar una aplicación en función de si requiere autenticación de usuario. Las aplicaciones que exijan la autenticación y que no permitan el uso anónimo recibirán una mejor puntuación de riesgo.
- Estamos implementando nuevas descripciones de actividades para que sean más coherentes y fáciles de usar. La búsqueda de actividades no se verá afectada por este cambio.
- Hemos incluido una identificación mejorada del dispositivo de usuario al permitir que Cloud App Security enriquezca más eventos con información del dispositivo.

## <a name="updates-made-in-2016"></a>Actualizaciones realizadas en 2016

### <a name="cloud-app-security-release-87"></a>Notas de la versión 87 de Cloud App Security

Fecha de publicación 25 de diciembre de 2016

**Nuevas características:**

- Estamos en proceso de lanzar la [anonimización de los datos](cloud-discovery-anonymizer.md) para que pueda disfrutar de Cloud Discovery a la vez que se protege la privacidad de los usuarios. La anonimización de los datos se realiza mediante el cifrado de la información del nombre de usuario.
- Estamos en proceso de lanzar la capacidad de exportar un script de bloqueo desde Cloud App Security a dispositivos adicionales. El script le permitirá reducir fácilmente Shadow IT mediante el bloqueo del tráfico a aplicaciones no autorizadas. Esta opción ya está disponible para:
  - BlueCoat ProxySG
  - Cisco ASA
  - Fortinet
  - Juniper SRX
  - Palo Alto
  - Websense
- Se ha agregado una nueva acción de control de archivos que le permite forzar a un archivo heredar permisos del elemento principal, eliminando así los permisos únicos que se hayan configurado para el archivo o carpeta. Esta acción de gobierno de archivos permite cambiar los permisos de archivo o carpeta para que se hereden de la carpeta principal.
- Se ha agregado un nuevo grupo de usuarios con el nombre Externos. Este es un grupo de usuarios predeterminado configurado previamente por Cloud App Security para incluir todos los usuarios que no forman parte de los dominios internos. Puede usar este grupo de usuarios como filtro. Por ejemplo, puede buscar actividades realizadas por los usuarios externos.
- La característica Cloud Discovery ahora admite dispositivos Sophos Cyberoam.

**Correcciones de errores:**

- Los archivos de SharePoint Online y OneDrive para la Empresa se mostraban en el informe de directiva de archivo y en la página de archivos como para uso interno en lugar de privado. Este error se ha corregido.

### <a name="cloud-app-security-release-86"></a>Notas de la versión 86 de Cloud App Security

Fecha de publicación: 13 de diciembre de 2016

**Nuevas características:**

- Todas las licencias independientes de Cloud App Security proporcionan la capacidad de habilitar el análisis de Azure Information Protection desde la configuración general (sin necesidad de crear una directiva).

**Mejoras:**

- Ahora puede usar "o" en el filtro de archivos para el nombre de archivo y en el filtro de tipo MIME para los archivos y directivas. Este cambio permite escenarios como escribir la palabra "Passport" o "controlador" al crear una directiva para los datos personales. El filtro coincidirá con cualquier archivo que tenga "Passport" o "controlador" en el nombre de archivo.
- De forma predeterminada, cuando se ejecuta una directiva DLP de inspección de contenido, los datos de las infracciones resultantes se enmascaran. Ahora puede mostrar los últimos cuatro caracteres de la infracción.

**Mejoras menores:**

- Nuevos eventos relacionados con el buzón de Office 365 (Exchange) que tienen que ver con las reglas de reenvío y con agregar y quitar permisos de buzón delegados.
- Nuevo evento que audita la concesión de consentimiento para nuevas aplicaciones en Azure Active Directory.

### <a name="cloud-app-security-release-85"></a>Notas de la versión 85 de Cloud App Security

Publicado el 27 de noviembre de 2016

**Nuevas características:**

- Se ha creado una distinción entre las aplicaciones conectadas y las aplicaciones autorizadas. La autorización y la desautorización de aplicaciones funcionan ahora como etiquetas, de modo que se pueden aplicar a las aplicaciones detectadas o a cualquier aplicación del catálogo. Las aplicaciones conectadas son aplicaciones que ha conectado con el conector de la API para supervisarlas y controlarlas con mayor profundidad. Ahora puede etiquetar aplicaciones como autorizadas o no autorizadas, así como conectarlas mediante el conector de aplicaciones, en caso de que esté disponible.
- Como parte de este cambio, se ha sustituido la página de aplicaciones autorizadas por la página **Aplicaciones conectadas**, que se ha rediseñado. Esta página externaliza los datos de estado de los conectores.
- Se puede acceder más fácilmente a los recopiladores de registros desde el menú **Configuración**, en **Orígenes**.
- Al crear un filtro de directiva de actividad, puede reducir el número de falsos positivos si selecciona la opción para ignorar las actividades repetidas cuando un mismo usuario las realiza de forma repetida en el mismo objeto. Este es el caso, por ejemplo, cuando una misma persona intenta descargar el mismo archivo varias veces, de modo que no se generará ninguna alerta.
- Se han realizado mejoras en el cajón de actividades. Ahora, al hacer clic en un objeto de actividad, puede explorarlo en profundidad para obtener más información.

**Mejoras:**

- Se han realizado mejoras en el motor de detección de anomalías, incluidas las alertas de desplazamiento imposible. Ahora, la información sobre la IP para este tipo de alertas está disponible en su descripción.
- También se han realizado mejoras en los filtros complejos, de modo que permitan agregar el mismo filtro más de una vez para ajustar los resultados que se filtran.
- Se han separado las actividades de archivos y carpetas de Dropbox del resto para que se puedan consultar con mayor facilidad.

**Correcciones de errores:**

- Se ha corregido un error en el mecanismo del sistema de alertas que creaba falsos positivos.

### <a name="cloud-app-security-release-84"></a>Notas de la versión 84 de Cloud App Security

Publicado el 13 de noviembre de 2016

**Nuevas características:**

- Cloud App Security ahora admite Microsoft Azure Information Protection, que incluye una integración mejorada y autoaprovisionamiento. Puede filtrar los archivos y establecer directivas de archivo mediante la clasificación segura de etiquetas y, después, establecer la etiqueta de clasificación que quiere ver. Las etiquetas también indican si la clasificación la estableció alguien de su organización o un usuario de otro inquilino (externo). También puede establecer directivas de actividad, en función de las etiquetas de clasificación de Azure Information Protection y habilitar la detección automática de etiquetas de clasificación en Office 365. Para obtener más información acerca de cómo sacar partido a esta nueva característica increíble, consulte [Integración con Azure Information Protection](azip-integration.md).

**Mejoras:**

- Se realizaron mejoras en el registro de actividad de Cloud App Security:
  - Los eventos de Office 365 del Centro de seguridad y cumplimiento de Office 365 ahora se integran con Cloud App Security y se ven en el **Registro de actividades**.
  - Toda la actividad de Cloud App Security se registra en el registro de actividades de Cloud App Security como actividad administrativa.
- Para ayudarle a investigar alertas relacionadas con archivos, en cada alerta derivada de una directiva de archivo, ahora puede ver la lista de actividades que se realizaron en el archivo coincidente.
- El algoritmo de viaje imposible del motor de detección de anomalías se ha mejorado para proporcionar una mayor compatibilidad para inquilinos pequeños.

**Mejoras menores:**

- El **Activity export limit** (Límite de exportación de actividades) se elevó a 10 000.
- Al crear un **Informe de instantáneas** en el proceso de carga del registro manual de Cloud Discovery, ahora recibirá una estimación precisa de cuánto tardará el procesamiento del registro.
- En una directiva de archivo, la acción de gobernanza **Remove collaborator** (Quitar colaborador) ahora funciona en grupos.
- Se realizaron mejoras menores en la página **Permisos de la aplicación**.
- Si había más de 10 000 usuarios que disponían de permisos para una aplicación que se conectaba a Office 365, la lista se cargaba lentamente. Se ha corregido esta carga lenta.
- Se han agregado atributos adicionales al **Catálogo de aplicaciones** con relación al sector de tarjetas de pago.

### <a name="cloud-app-security-release-83"></a>Notas de la versión 83 de Cloud App Security

Publicado el 30 de octubre de 2016

**Nuevas características:**

- Para simplificar el filtrado en el [registro de actividad](activity-filters.md) y en el [registro de archivo](file-filters.md), se han consolidado filtros similares. Use los filtros de actividad: Objeto de actividad, Dirección IP y Usuario. Utilice el filtro de archivos Colaboradores para encontrar exactamente lo que necesita.
- Desde la actividad de cajón del registro, en **Origen**, puede hacer clic en el vínculo para **Ver datos sin procesar**. Esta acción descarga los datos sin procesar que se usan para generar el registro de actividad para profundizar en los eventos de aplicación.
- Compatibilidad agregada para las actividades de inicio de sesión adicionales en Okta. [Versión preliminar privada]
- Compatibilidad agregada para las actividades de inicio de sesión adicionales en Salesforce.

**Mejoras:**

- Facilidad de uso mejorada para informes y solución de problemas de instantáneas de Cloud Discovery.
- Visibilidad mejorada en la lista de alertas de varias aplicaciones.
- Facilidad de uso mejorada al crear nuevos informes continuos de Cloud Discovery.
- Facilidad de uso mejorada en el registro de gobernanza.

### <a name="cloud-app-security-release-82"></a>Notas de la versión 82 de Cloud App Security

Publicado el 9 de octubre de 2016

**Mejoras:**

- Las actividades **Cambiar correo electrónico** y **Cambiar contraseña** ahora son independientes de la actividad genérica **Administrar usuarios** en Salesforce.
- Se ha agregado una aclaración sobre el límite de alertas diarias por SMS. Se envía un máximo de 10 mensajes por número de teléfono y por día (UTC).
- Se ha agregado un nuevo certificado a los atributos de Cloud Discovery para Privacy Shield que reemplaza Safe Harbor (relevante solo para proveedores de EE. UU.).
- Se ha agregado un proceso de solución de problemas a los mensajes de error del conector de API para que sea más fácil solucionar los problemas.
- Mejora de la frecuencia de actualización del examen de aplicaciones de terceros de Office 365.
- Mejoras en el panel de Cloud Discovery.
- Se ha mejorado el analizador de Syslog de punto de control.
- Mejoras en el registro de gobernanza para prohibir aplicaciones de terceros y para eliminar la prohibición.

**Correcciones de errores:**

- Mejora del proceso para cargar un logotipo.

### <a name="cloud-app-security-release-81"></a>Notas de la versión 81 de Cloud App Security

Publicado el 18 de septiembre de 2016

**Mejoras:**

- Cloud App Security ya es una aplicación de origen en Office 365. De ahora en adelante, puede conectar Office 365 con Cloud App Security con un solo clic.

- Nuevo aspecto del registro de gobernanza: se ha actualizado para que tenga el mismo aspecto útil que el registro de actividad y la tabla de archivos. Use los nuevos filtros para encontrar fácilmente lo que necesita y supervisar las acciones de gobernanza.
- Se han realizado mejoras en el motor de detección de anomalías en lo que respecta a varios inicios de sesión erróneos y otros factores de riesgo.
- Se han realizado mejoras en los informes de instantáneas de Cloud Discovery.
- Se han realizado mejoras en las actividades administrativas del registro de actividades. Ahora, en Cambiar contraseña, Actualizar usuario y Restablecer contraseña se muestra si la actividad se realizó como una actividad administrativa.
- Se han mejorado los filtros de alerta para las alertas del sistema.
- Ahora, la etiqueta de la directiva de una alerta contiene un vínculo al informe de directiva.
- Si no hay ningún propietario especificado para un archivo de Dropbox, los mensajes de correo electrónico de notificación se envían al destinatario que establezca.
- Cloud App Security admite 24 idiomas más, con lo que la compatibilidad se amplía a un total de 41 idiomas.

### <a name="cloud-app-security-release-80"></a>Notas de la versión 80 de Cloud App Security

Publicado el 4 de septiembre de 2016

**Mejoras:**

- Cuando se produce un error en el examen de DLP, ahora se proporciona una explicación de por qué Cloud App Security no pudo examinar el archivo. Para obtener más información, consulte [Content Inspection](./content-inspection.md) (Inspección de contenido).
- Se han realizado mejoras en los motores de detección de anomalías, incluido en las alertas de viaje imposible.
- Se han realizado mejoras en la experiencia de descartar alertas. También puede agregar comentarios para que pueda permitir que el equipo de Cloud App Security sepa si la alerta era interesante y por qué. Sus comentarios se usarán para mejorar las detecciones de Cloud App Security.
- Se han mejorado los analizadores de Cloud Discovery de Cisco ASA.
- Ahora recibirá una notificación por correo electrónico cuando se complete la carga manual de registros de Cloud Discovery.

### <a name="cloud-app-security-release-79"></a>Notas de la versión 79 de Cloud App Security

Publicado el 21 de agosto de 2016

**Nuevas características:**

- **Nuevo panel de información de Cloud Discovery**: ahora hay disponible un nuevo panel de Cloud Discovery, diseñado para proporcionar más información sobre cómo se usan las aplicaciones de nube en la organización. Proporciona una visión general a simple vista sobre los tipos de aplicaciones que se usan, las alertas abiertas y los niveles de riesgo de las aplicaciones de la organización. También permite saber quiénes son los usuarios de la organización que más usan las aplicaciones y proporciona un mapa de ubicación de la sede central de la aplicación. El nuevo panel tiene más opciones para filtrar los datos, de modo que pueda generar vistas específicas en función de lo que más le interese y gráficos fáciles de entender para que se haga una idea general de un vistazo.

- **Nuevos informes de Cloud Discovery**: para ver los resultados de Cloud Discovery, ahora puede generar dos tipos de informes: de instantáneas y continuos. Los informes de instantáneas proporcionan visibilidad ad hoc de un conjunto de registros de tráfico que puede cargar manualmente desde los firewalls y los servidores proxy. Los informes continuos muestran los resultados de todos los registros que se reenvían desde la red mediante los recopiladores de registros de Cloud App Security. Estos nuevos informes proporcionan una mejor visibilidad de todos los datos, la identificación automática de un uso anómalo según lo que identifique el motor de detección de anomalías de aprendizaje automático de Cloud App Security y la identificación de un uso anómalo según lo defina usted mediante el motor de directivas pormenorizadas y sólidas. Para obtener más información, vea [configurar Cloud Discovery](set-up-cloud-discovery.md).

**Mejoras:**

- Mejoras generales en la facilidad de uso de las páginas siguientes: páginas de directivas, configuración general y configuración de correo electrónico.
- En la tabla de alertas, es más fácil distinguir las alertas leídas de las no leídas. Las alertas leídas tienen una línea azul a la izquierda y aparecen atenuadas para indicar que ya se han leído.
- Se han actualizado los parámetros de **Actividad repetida** de la directiva de actividad.
- En la página de cuentas, se ha agregado la columna **Tipo** de usuario, por lo que ahora puede ver qué tipo de cuenta de usuario tiene cada usuario. Los tipos de usuario son específicos de la aplicación.
- Se ha agregado soporte prácticamente en tiempo real para las actividades relacionadas con archivos en OneDrive y SharePoint. Cuando un archivo cambia, Cloud App Security desencadena un examen casi de inmediato.

### <a name="cloud-app-security-release-78"></a>Notas de la versión 78 de Cloud App Security

Publicado el 7 de agosto de 2016

**Mejoras:**

- Ahora puede hacer clic con el botón derecho en un archivo específico y **Buscar relacionados**. En el registro de actividades, puede usar el filtro del objeto de destino y seleccionar el archivo específico.

- Se han mejorado los analizadores de archivos de registro de Cloud Discovery, incluida la adición de Juniper y Cisco ASA.
- Cloud App Security ahora permite proporcionar comentarios para la mejora de las alertas cuando se descarta una alerta. Puede ayudar a mejorar la calidad de la característica de alerta de Cloud App Security informándonos sobre por qué está descartando la alerta. Por ejemplo, no es interesante, ha recibido demasiadas alertas similares, la gravedad real debe ser inferior, la alerta no es correcta.
- En la vista de la directiva de archivo o al ver un archivo, cuando se abre el cajón de archivos, se ha agregado un vínculo nuevo a las directivas coincidentes. Al hacer clic en él, puede ver todas las coincidencias y ahora puede descartarlas todas.
- Ahora se ha agregado en todas las alertas correspondientes la unidad organizativa a la que pertenece un usuario.
- Ahora se envía una notificación por correo electrónico para informarle de que se ha completado el procesamiento de los registros cargados manualmente.

### <a name="cloud-app-security-release-77"></a>Notas de la versión 77 de Cloud App Security

Publicado el 24 de julio de 2016

**Mejoras:**

- El icono del botón Exportar de Cloud Discovery se ha mejorado para una mayor facilidad de uso.
- Al investigar una actividad, si no se ha analizado el agente de usuario, ahora se pueden ver los datos sin procesar.
- Se han agregado dos nuevos factores de riesgo al motor de detección de anomalías:
  - Cloud App Security ahora usa las etiquetas de direcciones IP que están asociadas a una red de robots (botnet) y direcciones IP anónimas como parte del cálculo de riesgo.
  - La actividad de Office 365 ahora se supervisa para detectar frecuencias de descarga alta. Si la frecuencia de descarga de Office 365 es mucho mayor que la frecuencia de descarga normal de la organización o de un usuario específico, se desencadenará una alerta de detección de anomalías.
- Ahora Cloud App Security es compatible con la nueva API de [función de uso compartido seguro](https://blogs.dropbox.com/dropbox/2016/06/new-dropbox-productivity-tools/) de Dropbox.
- Se han realizado mejoras para agregar detalles en los errores de análisis de registro de Discovery, por ejemplo, para indicar que no hay transacciones relacionadas con la nube, todos los eventos están obsoletos, el archivo está dañado o el formato del registro no coincide.
- Se ha mejorado el filtro de fecha del registro de actividad y ahora incluye la capacidad de filtrar por hora.
- La página de intervalos de direcciones IP se ha mejorado para una mayor facilidad de uso.
- Ahora Cloud App Security incluye compatibilidad con Microsoft Azure Information Protection (versión preliminar). Puede filtrar los archivos y establecer directivas de archivo mediante la clasificación segura de etiquetas. Después, establezca la etiqueta de clasificación que quiere ver. Las etiquetas también indican si la clasificación la estableció alguien de su organización o un usuario de otro inquilino (externo).

### <a name="cloud-app-security-release-76"></a>Notas de la versión 76 de Cloud App Security

Publicado el 10 de julio de 2016

**Mejoras:**

- Ahora se pueden exportar listas con los usuarios de los informes integrados.
- Se ha mejorado la facilidad de uso de la directiva de actividad agregada.
- Se ha mejorado la compatibilidad con el analizador de mensajes de registro de firewall de W3C de TMG.
- Se ha mejorado la facilidad de uso del menú desplegable de la acción de gobernanza de archivos, que ahora se divide en acciones de colaboración, seguridad e investigación.
- Se ha mejorado la detección de viaje imposible de la actividad Enviar correo de Exchange Online.
- Se ha agregado una nueva lista de títulos (rutas de navegación) en la parte superior de las páginas de alertas y de directiva para facilitar la navegación.

**Correcciones de errores:**

- La expresión preestablecida para la tarjeta de crédito de la configuración de DLP para las directivas de archivo se ha cambiado a Todos: Finanzas: Número de tarjeta de crédito.

### <a name="cloud-app-security-release-75"></a>Notas de la versión 75 de Cloud App Security

Publicado el 27 de junio de 2016

**Nuevas características:**

- Se agregaron nuevas adiciones a nuestra creciente lista de eventos compatibles con Salesforce.  Los eventos proporcionan información sobre informes, vínculos compartidos, distribución de contenido, inicio de sesión suplantado y mucho más.
- Los iconos de las aplicaciones conectadas del panel de Cloud App Security se han alineado con el estado de las aplicaciones tal como se muestra en el panel para reflejar los últimos 30 días.
- Compatibilidad con pantallas de ancho completo.

**Correcciones de errores:**

- Los números de teléfono de alerta por SMS ahora se validan tras la inserción.

### <a name="cloud-app-security-release-74"></a>Notas de la versión 74 de Cloud App Security

Fecha de publicación: 13 de junio de 2016

- Se ha actualizado la pantalla Alerta para proporcionar más información de un vistazo. Las actualizaciones incluyen la posibilidad de ver todas las actividades del usuario con una sola mirada, un mapa de actividades, registros de gobernanza de usuarios relacionados, una descripción del motivo por el que se ha desencadenado la alerta y gráficos adicionales y mapas de la página del usuario.
- Los eventos generados por Cloud App Security ahora incluyen el tipo de evento, el formato, grupos de directivas, objetos relacionados y una descripción.
- Se han agregado nuevas etiquetas de direcciones IP para Office 365 apps for Enterprise, OneNote, Office Online y Exchange Online Protection.
- Ahora tiene la opción de cargar registros desde el menú de detección principal.
- Se ha mejorado el filtro de categoría de direcciones IP. La categoría de dirección IP Nula ahora se denomina Sin categoría. Se ha agregado una nueva categoría denominada Sin valor para incluir todas las actividades que no tienen datos de dirección IP.
- Los grupos de seguridad de Cloud App Security ahora se denominan grupos de usuarios para evitar la confusión con los grupos de seguridad de Active Directory.
- Ahora es posible filtrar por dirección IP y dejar fuera los eventos sin una dirección IP.
- Se han realizado cambios en la configuración de los correos electrónicos de notificación cuando se detectan coincidencias en las directivas de actividad y de archivo. Ahora se pueden agregar direcciones de correo electrónico de destinatarios a CC con la notificación.

### <a name="cloud-app-security-release-73"></a>Notas de la versión 73 de Cloud App Security

Fecha de publicación: 29 de mayo de 2016

- Funciones de alerta actualizadas: ahora las alertas por directiva se pueden configurar para enviarse por correo o como mensaje de texto.
- Página de alertas: diseño mejorado para habilitar opciones de resolución avanzadas y la administración de incidentes.
- Ajuste de directiva: ahora es posible desplazarse desde las opciones de resolución de alertas directamente a la página de configuración de directiva y, así, permitir un mejor ajuste basado en alertas.
- Mejoras en el cálculo de la puntuación de riesgo de detección de anomalías y un menor índice de falsos positivos gracias a los comentarios de los clientes.
- Ahora la exportación del registro de actividades incluye el identificador de evento, la categoría de evento y el nombre del tipo de evento.
- Mejor apariencia y facilidad de uso de las acciones de gobernanza de creación de directivas.
- Investigación y control simplificados para Office 365: con la selección de Office 365 se seleccionan automáticamente todas las aplicaciones que forman parte del conjunto de aplicaciones de Office 365.
- Ahora las notificaciones se envían a la dirección de correo configurada en la aplicación conectada.
- Tras un error de conexión, ahora la aplicación de nube proporciona una descripción detallada de ese error.
- Cuando un archivo coincide con una directiva, ahora el cajón de archivos proporciona una dirección URL para tener acceso a ese archivo.
- Cuando se desencadena una alerta a raíz de una directiva de actividad o de una directiva de detección de anomalías, se envía una nueva notificación detallada que proporciona información sobre la coincidencia.
- Cuando un conector de aplicaciones se desconecta, se desencadena una alerta del sistema automatizada.
- Ahora puede descartar y resolver una sola alerta o una selección masiva de alertas desde la página de alertas.

### <a name="cloud-app-security-release-72"></a>Notas de la versión 72 de Cloud App Security

Fecha de publicación: 15 de mayo de 2016

- Mejoras generales en la infraestructura y apariencia:

  - Nuevo diagrama que proporciona más ayuda en el proceso de carga de registro manual de Cloud Discovery.
  - Se ha mejorado el proceso de actualización de archivos de registro no reconocidos ("Otros"). Este proceso incluye una ventana emergente que le permite saber que el archivo requiere revisión adicional. Se le notificará cuando los datos estén disponibles.
  - Se destacan más infracciones de actividad y de archivo al investigar un registro de actividad y de archivo en busca de sistemas operativos y exploradores obsoletos.

- Mejores analizadores de archivos de registro de Cloud Discovery, incluida la adición de Cisco ASA, Cisco FWSM, Cisco Meraki y W3C.
- Mejoras en los problemas conocidos de Cloud Discovery.
- Nuevos filtros de actividad agregados para la afiliación interna/externa y de dominio del propietario.
- Se agregó un nuevo filtro que permite buscar cualquier objeto de Office 365 (archivos, carpetas, direcciones URL).
- Se agregó la capacidad de configurar una puntuación de riesgo mínima para las directivas de detección de anomalías.
- Al configurar una alerta para que se envíe cuando se infrinja una directiva, ahora se puede establecer un nivel de gravedad mínimo a partir del cual se recibirán las alertas. Puede elegir usar la configuración predeterminada de la organización para esto o establecer una configuración de alerta específica como valor predeterminado de la organización.

[!INCLUDE [Open support ticket](includes/support.md)]