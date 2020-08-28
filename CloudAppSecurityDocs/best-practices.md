---
title: 'Prácticas recomendadas para proteger su organización: Cloud App Security'
description: En este artículo se proporciona un conjunto de procedimientos recomendados para proteger una organización.
author: shsagir
ms.author: shsagir
ms.service: cloud-app-security
ms.topic: quickstart
ms.date: 10/24/2019
ms.collection: M365-security-compliance
ms.openlocfilehash: e26d98c00a520f710774ccd86a1406f4c8392530
ms.sourcegitcommit: 29a8e66c665f51d831516924ae4d9d8047b39276
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2020
ms.locfileid: "88781317"
---
# <a name="cloud-app-security-best-practices"></a>Procedimientos recomendados de Cloud App Security

*Se aplica a: Microsoft Cloud App Security*

En este artículo se proporcionan prácticas recomendadas para proteger su organización mediante el uso de Microsoft Cloud App Security. Estos procedimientos recomendados se han desarrollado con base en nuestra propia experiencia con Cloud App Security y en las experiencias de clientes como usted.

Los procedimientos recomendados que se describen en este artículo son los siguientes:

> [!div class="checklist"]
> * [Detección y evaluación de aplicaciones en la nube](#discover-and-assess-cloud-apps)
> * [Aplicación de directivas de gobernanza de la nube](#apply-cloud-governance-policies)
> * [Limitación de la exposición de datos compartidos y aplicación de directivas de colaboración](#limit-exposure-of-shared-data-and-enforce-collaboration-policies)
> * [Detección, clasificación, etiquetado y protección de datos regulados y confidenciales almacenados en la nube](#discover-classify-label-and-protect-regulated-and-sensitive-data-stored-in-the-cloud)
> * [Aplicación de directivas de cumplimiento y de DLP para datos almacenados en la nube](#enforce-dlp-and-compliance-policies-for-data-stored-in-the-cloud)
> * [Bloqueo y protección de la descarga de datos confidenciales en dispositivos no administrados o de riesgo](#block-and-protect-download-of-sensitive-data-to-unmanaged-or-risky-devices)
> * [Colaboración segura con usuarios externos mediante la aplicación de controles de sesión en tiempo real](#secure-collaboration-with-external-users-by-enforcing-real-time-session-controls)
> * [Detección de amenazas en la nube, cuentas en peligro, colaboradores malintencionados y ransomware](#detect-cloud-threats-compromised-accounts-malicious-insiders-and-ransomware)
> * [Uso de la traza de auditoría de actividades para investigaciones forenses](#use-the-audit-trail-of-activities-for-forensic-investigations)
> * [Servicios de IaaS seguros y aplicaciones personalizadas](#secure-iaas-services-and-custom-apps)

## <a name="discover-and-assess-cloud-apps"></a>Detección y evaluación de aplicaciones en la nube

Como Cloud App Security está integrado con Protección contra amenazas avanzada de Microsoft Defender (ATP de Microsoft Defender), podrá usar Cloud Discovery más allá de la red corporativa o de puertas de enlace web seguras. Combinando la información de usuarios y máquinas, puede identificar equipos o usuarios de riesgo, ver qué aplicaciones están usando e investigar más detalles en el portal de ATP de Microsoft Defender.

**Práctica recomendada**: Habilitación de Shadow IT Discovery mediante ATP de Microsoft defender  
**Detalle**: Cloud Discovery analiza los registros de tráfico que recopila ATP de Microsoft Defender y evalúa las aplicaciones identificadas con respecto al catálogo de aplicaciones en la nube para proporcionar información de seguridad y cumplimiento normativo. Al configurar Cloud Discovery, obtiene visibilidad del uso de la nube, de shadow IT y de la supervisión continua de las aplicaciones no autorizadas que usan los usuarios.  
**Más información**:

* [Integración de ATP de Microsoft Defender con Cloud App Security](wdatp-integration.md)
* [Configuración de Cloud Discovery](set-up-cloud-discovery.md)
* [Detección y administración de shadow IT en la red](tutorial-shadow-it.md)

---

**Práctica recomendada**: Configuración de directivas de detección de aplicaciones para identificar de forma proactiva aplicaciones de riesgo, no conformes y populares  
**Detalles**: Las directivas de detección de aplicaciones facilitan el seguimiento de las aplicaciones importantes detectadas en su organización para ayudarlo a administrarlas de forma eficaz. Cree directivas para recibir alertas cuando detecte nuevas aplicaciones que se identifican como peligrosas, no conformes, populares o de gran tamaño.  
**Más información**:

* [Crear directivas de Cloud Discovery](cloud-discovery-policies.md)
* [Directiva de detección de anomalías de Cloud Discovery](cloud-discovery-anomaly-detection-policy.md)
* [Obtención de análisis de comportamiento y detección de anomalías instantáneos](anomaly-detection-policy.md)

---

**Práctica recomendada**: Administración de aplicaciones de OAuth autorizadas por los usuarios  
**Detalle**: Muchos usuarios conceden ocasionalmente permisos de OAuth a las aplicaciones de terceros para acceder a la información de su cuenta y, al hacerlo, también proporcionan involuntariamente acceso a sus datos en otras aplicaciones en la nube. Normalmente, el equipo de TI no tiene visibilidad en estas aplicaciones, por lo que resulta difícil sopesar el riesgo de seguridad de una aplicación frente a las ventajas de productividad que proporciona.

Por lo tanto, Microsoft Cloud App Security ofrece la capacidad de investigar y supervisar los permisos de aplicaciones que sus usuarios otorgaron. Puede usar esta información para identificar una aplicación potencialmente sospechosa y, si determina que es arriesgado, puede prohibir el acceso a ella.  
**Más información**:

* [Administración de aplicaciones de OAuth](manage-app-permissions.md)
* [Directivas de aplicación de OAuth](app-permission-policy.md)

---
---
---
---

## <a name="apply-cloud-governance-policies"></a>Aplicación de directivas de gobernanza de la nube

**Práctica recomendada**: Etiquetado de aplicaciones y exportar scripts de bloqueo  
**Detalle**: Después de revisar la lista de aplicaciones detectadas en su organización, puede proteger su entorno contra el uso no deseado de una aplicación. Puede aplicar la etiqueta **Autorizada** a las aplicaciones aprobadas por su organización y la etiqueta **No autorizada** a las aplicaciones que no lo están. Puede supervisar aplicaciones no autorizadas con filtros de detección o exportar un script para bloquear aplicaciones no autorizadas mediante los dispositivos de seguridad locales. El uso de etiquetas y scripts de exportación permite organizar las aplicaciones y proteger su entorno, ya que solo permite el acceso a las aplicaciones seguras.  
**Más información**:

* [Control de aplicaciones detectadas](governance-discovery.md)

---
---
---
---

## <a name="limit-exposure-of-shared-data-and-enforce-collaboration-policies"></a>Limitación de la exposición de datos compartidos y aplicación de directivas de colaboración

**Práctica recomendada**: Conexión de Office 365  
**Detalle**: Al conectar Office 365 a Cloud App Security, se proporciona visibilidad inmediata de las actividades de los usuarios y los archivos a los que acceden, y proporciona acciones de gobernanza para Office 365, SharePoint, OneDrive, Teams, Power BI, Exchange y Dynamics.  
**Más información**:

* [Conectar aplicaciones](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md)
* [Conectar Office 365 con Microsoft Cloud App Security](connect-office-365-to-microsoft-cloud-app-security.md)

---

**Práctica recomendada**: Conexión de aplicaciones de terceros  
**Detalle**: Al conectar aplicaciones de terceros a Cloud App Security, se proporciona información mejorada sobre actividades de los usuarios, detección de amenazas y funcionalidades de gobernanza. Se admiten las siguientes API de aplicaciones de terceros: [Amazon Web Services (AWS)](connect-aws-to-microsoft-cloud-app-security.md), [Box](connect-box-to-microsoft-cloud-app-security.md), [Dropbox](connect-dropbox-to-microsoft-cloud-app-security.md), [G Suite](connect-google-apps-to-microsoft-cloud-app-security.md), [Okta](connect-okta-to-microsoft-cloud-app-security.md), [Salesforce](connect-salesforce-to-microsoft-cloud-app-security.md), [ServiceNow](connect-servicenow-to-microsoft-cloud-app-security.md), [WebEx](connect-webex-to-microsoft-cloud-app-security.md) y [Workday](connect-workday-to-microsoft-cloud-app-security.md).  
**Más información**:

* [Conectar aplicaciones](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md)

---

**Práctica recomendada**: Revisión de la exposición de los datos de la organización  
**Detalle**: Use los informes de exposición de archivos para obtener visibilidad sobre cómo los usuarios comparten archivos con aplicaciones en la nube. Los informes siguientes están disponibles y se pueden exportar para hacer un análisis más exhaustivo en herramientas como Microsoft Power BI:

* **Información general sobre el uso compartido de datos**: Enumera los archivos por los permisos de acceso almacenados en cada una de las aplicaciones en la nube.
* **Uso compartido externo por dominio**: Enumera los dominios con los que los empleados comparten los archivos corporativos.
* **Propietarios de archivos compartidos**: Enumera los usuarios que comparten archivos corporativos de forma externa.  
**Más información**:

* [Generación de informes de administración de datos](built-in-reports.md)

---

**Práctica recomendada**: Creación de directivas para quitar el uso compartido con cuentas personales  
**Detalle**: Al conectar Office 365 a Cloud App Security, se proporciona visibilidad inmediata de las actividades de los usuarios y los archivos a los que acceden, y proporciona acciones de gobernanza para Office 365, SharePoint, OneDrive, Teams, Power BI, Exchange y Dynamics.  
**Más información**:

* [Control de aplicaciones conectadas](governance-actions.md)

---
---
---
---

## <a name="discover-classify-label-and-protect-regulated-and-sensitive-data-stored-in-the-cloud"></a>Detección, clasificación, etiquetado y protección de datos regulados y confidenciales almacenados en la nube

**Práctica recomendada**: Integración con Azure Information Protection  
**Detalle**: Gracias a la integración con Azure Information Protection, es posible aplicar automáticamente etiquetas de clasificación y, opcionalmente, agregar protección de cifrado. Una vez que la integración está activada, puede aplicar etiquetas como una acción de gobernanza, ver archivos por clasificación, investigar archivos por nivel de clasificación y crear directivas granulares para asegurarse de que los archivos clasificados se controlan correctamente. Si no activa la integración, no podrá beneficiarse de la posibilidad de examinar, etiquetar y cifrar archivos automáticamente en la nube.  
**Más información**:

* [Integración de Azure Information Protection](azip-integration.md)
* [Tutorial: Aplicación automática de etiquetas de clasificación de Azure Information Protection](use-case-information-protection.md)

---

**Práctica recomendada**: Creación de directivas de exposición de datos  
**Detalle**: Use directivas de archivo para detectar información de uso compartido y análisis de información confidencial en las aplicaciones en la nube. Cree las siguientes directivas de archivo para avisarle cuando se detecten exposiciones de datos:

* Archivos compartidos externamente que contienen datos confidenciales
* Archivos compartidos externamente y etiquetados como **Confidencial**
* Archivos compartidos con un dominio no autorizado
* Protección de archivos confidenciales en aplicaciones SaaS

**Más información**:

* [Inspección de contenido](content-inspection.md)
* [Directivas de archivo](data-protection-policies.md)
* [Directivas de protección de la información](policies-information-protection.md)

---

**Práctica recomendada**: Revisión de informes en la página **Archivos**  
**Detalle**: Una vez que haya conectado varias aplicaciones SaaS mediante conectores de aplicaciones, Cloud App Security examinará los archivos que han almacenado estas aplicaciones. Además, cada vez que se modifica un archivo, se vuelve a examinar. Puede usar la página **Archivos** para comprender e investigar los tipos de datos que se almacenan en las aplicaciones en la nube. Para ayudarlo en la investigación, puede filtrar por dominios, grupos, usuarios, fecha de creación, extensión, nombre y tipo de archivo, identificador de archivo, etiqueta de clasificación, etc. El uso de estos filtros permite controlar el modo en que decide investigar los archivos para asegurarse de que ninguno de los datos esté en riesgo. Una vez que comprenda mejor cómo se usan los datos, puede crear directivas para buscar contenido confidencial en estos archivos.  
**Más información**:

* [Conectar aplicaciones](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md)
* [Filtros de archivo](file-filters.md)
* [Inspección de contenido](content-inspection.md)

---
---
---
---

## <a name="enforce-dlp-and-compliance-policies-for-data-stored-in-the-cloud"></a>Aplicación de directivas de cumplimiento y de DLP para datos almacenados en la nube

**Práctica recomendada**: Protección de los datos confidenciales para evitar que se compartan con usuarios externos  
**Detalle**: Cree una directiva de archivo que detecte cuándo un usuario intenta compartir un archivo que tenga la etiqueta de clasificación **confidencial** con alguien externo a la organización, y configure su acción de gobernanza para quitar usuarios externos. Esta directiva garantiza que los datos confidenciales no salgan de la organización y que los usuarios externos no pueden acceder a ellos.  
**Más información**:

* [Control de aplicaciones conectadas](governance-actions.md)

---
---
---
---

## <a name="block-and-protect-download-of-sensitive-data-to-unmanaged-or-risky-devices"></a>Bloqueo y protección de la descarga de datos confidenciales en dispositivos no administrados o de riesgo

**Práctica recomendada**: Administración y control del acceso a dispositivos de alto riesgo  
**Detalle**: Use Control de aplicaciones de acceso condicional para establecer controles en las aplicaciones SaaS. Puede crear directivas de sesión para supervisar las sesiones de bajo riesgo y con poco nivel de confianza. Del mismo modo, puede crear directivas de sesión para bloquear y proteger las descargas de los usuarios que intentan acceder a datos confidenciales desde dispositivos no administrados o de riesgo. Si no va a crear directivas de sesión para supervisar las sesiones de alto riesgo, no podrá bloquear y proteger las descargas en el cliente web, y tampoco supervisar sesiones de confianza baja en aplicaciones de Microsoft y de terceros.  
**Más información**:

* [Proteger aplicaciones con el Control de aplicaciones de acceso condicional de Microsoft Cloud App Security](proxy-intro-aad.md)
* [Directivas de sesión](session-policy-aad.md)

---
---
---
---

## <a name="secure-collaboration-with-external-users-by-enforcing-real-time-session-controls"></a>Colaboración segura con usuarios externos mediante la aplicación de controles de sesión en tiempo real

**Práctica recomendada**: Supervisión de sesiones con usuarios externos mediante Control de aplicaciones de acceso condicional  
**Detalle**: Para proteger la colaboración en su entorno, puede crear una directiva de sesión para supervisar las sesiones entre los usuarios internos y externos. Esto no solo le ofrece la posibilidad de supervisar la sesión entre los usuarios (y notificarles que sus actividades de sesión se están supervisando), sino que también le permite limitar actividades específicas. Al crear directivas de sesión para supervisar la actividad, puede elegir las aplicaciones y los usuarios que quiere supervisar.  
**Más información**:

* [Proteger aplicaciones con el Control de aplicaciones de acceso condicional de Microsoft Cloud App Security](proxy-intro-aad.md)
* [Directivas de sesión](session-policy-aad.md)

---
---
---
---

## <a name="detect-cloud-threats-compromised-accounts-malicious-insiders-and-ransomware"></a>Detección de amenazas en la nube, cuentas en peligro, colaboradores malintencionados y ransomware

**Práctica recomendada**: Ajuste de las directivas de anomalías, establecimiento de intervalos IP y envío de comentarios de alertas  
**Detalle**: Las directivas de detección de anomalías proporcionan análisis de comportamiento de usuarios y entidades (UEBA) y aprendizaje automático (ML) para que pueda ejecutar inmediatamente la detección de amenazas avanzada en el entorno de nube.

Las directivas de detección de anomalías se desencadenan cuando los usuarios de su entorno realizan actividades inusuales. Cloud App Security supervisa continuamente las actividades de los usuarios y usa UEBA y ML para aprender y comprender el *comportamiento normal* de los usuarios. Puede ajustar la configuración de la directiva para que se adapte a los requisitos de su organización; por ejemplo, puede establecer la confidencialidad de una directiva, así como definir el ámbito de una directiva para un grupo específico.

* **Ajuste y ámbito de directivas de detección de anomalías**: Por ejemplo, para reducir el número de falsos positivos dentro de la alerta de viaje imposible, puede establecer el control deslizante de confidencialidad de la directiva en Bajo. Si hay usuarios de su organización que realizan frecuentemente viajes corporativos, puede agregarlos a un grupo de usuarios y seleccionar ese grupo en el ámbito de la directiva.

* **Establecimiento de intervalos IP**: Cloud App Security pueden identificar direcciones IP conocidas una vez que se establecen los intervalos de direcciones IP. Con los intervalos de direcciones IP configurados, puede etiquetar, clasificar y personalizar la forma en que se muestran e investigan los registros y las alertas. Agregar intervalos de direcciones IP ayuda a reducir las detecciones de falsos positivos y a mejorar la precisión de las alertas. Si decide no agregar las direcciones IP, es posible que vea un mayor número de posibles falsos positivos y alertas para investigar.

* **Envío de comentarios de alertas**:

    Al descartar o resolver las alertas, asegúrese de enviar comentarios con el motivo por el que descartó la alerta o cómo se resolvió. Esta información ayuda a Cloud App Security a mejorar nuestras alertas y a reducir los falsos positivos.

**Más información**:

* [Obtención de análisis de comportamiento y detección de anomalías instantáneos](anomaly-detection-policy.md)
* [Trabajo con etiquetas e intervalos IP](ip-tags.md)
* [Supervisión de alertas en Cloud App Security](monitor-alerts.md)

---

**Práctica recomendada**: Detección de actividad desde ubicaciones o países inesperados  
**Detalle**: Cree una directiva de actividad que le avise cuando los usuarios inicien sesión desde ubicaciones o países inesperados. Estas notificaciones pueden alertarlo de posibles sesiones en peligro en su entorno para que pueda detectar y corregir amenazas antes de que se produzcan.  
**Más información**:

* [Directivas de protección contra amenazas](policies-threat-protection.md)

---

**Práctica recomendada**: Creación de directivas de aplicación de OAuth  
**Detalle**: Cree una directiva de aplicación de OAuth para recibir una notificación cuando una aplicación de OAuth cumpla determinados criterios. Por ejemplo, puede optar por recibir una notificación cuando una aplicación específica que requiera un nivel de permisos elevado sea accesible por más de 100 usuarios.  
**Más información**:

* [Directivas de aplicación de OAuth](app-permission-policy.md)

---
---
---
---

## <a name="use-the-audit-trail-of-activities-for-forensic-investigations"></a>Uso de la traza de auditoría de actividades para investigaciones forenses

**Práctica recomendada**: Uso de la pista de auditoría de las actividades al investigar alertas  
**Detalle**: Las alertas se desencadenan cuando las actividades de usuario, administrador o inicio de sesión no cumplen las directivas. Es importante investigar las alertas para saber si hay una posible amenaza en el entorno.

Puede investigar una alerta seleccionándola en la página **Alertas** y revisando la pista de auditoría de las actividades relacionadas con esa alerta. La pista de auditoría ofrece visibilidad de las actividades del mismo tipo, el mismo usuario, la misma dirección IP y la misma ubicación, para así proporcionarle la historia general de una alerta. Si una alerta garantiza más investigación, cree un plan para resolver esas alertas en su organización.

Al descartar las alertas, es importante investigar y comprender por qué no son de importancia o si son falsos positivos. Si hay un gran volumen de estas actividades, también puede plantearse revisar y optimizar la directiva que desencadena la alerta.  
**Más información**:

* [Actividades](activity-filters.md)

---
---
---
---

## <a name="secure-iaas-services-and-custom-apps"></a>Servicios de IaaS seguros y aplicaciones personalizadas

**Práctica recomendada**: Conexión de Azure, AWS y GCP  
**Detalle**: La conexión de cada una de estas plataformas en la nube a Cloud App Security ayuda a mejorar las funcionalidades de detección de amenazas. Mediante la supervisión de las actividades administrativas e inicios de sesión de estos servicios, puede detectar y recibir notificaciones sobre posibles ataques por fuerza bruta, el uso malintencionado de una cuenta de usuario con privilegios y otras amenazas del entorno. Por ejemplo, puede identificar riesgos tales como eliminaciones inusuales de máquinas virtuales o incluso actividades de suplantación en estas aplicaciones.  
**Más información**:

* [Conectar Azure con Microsoft Cloud App Security](connect-azure-to-microsoft-cloud-app-security.md)
* [Conectar AWS con Microsoft Cloud App Security](connect-aws-to-microsoft-cloud-app-security.md)
* [Conectar GCP a Microsoft Cloud App Security (versión preliminar)](connect-google-gcp-to-microsoft-cloud-app-security.md)

---

**Práctica recomendada**: Revisión de las evaluaciones de configuración de seguridad para Azure, AWS y GCP  
**Detalle**: La integración con Azure Security Center proporciona una evaluación de la configuración de seguridad de su entorno de Azure. Esta evaluación proporciona recomendaciones para la configuración y el control de seguridad que faltan. Revisar estas recomendaciones ayuda a identificar anomalías y posibles vulnerabilidades en su entorno, y podrá acceder directamente a la ubicación correspondiente del portal de seguridad de Azure para resolverlas.

AWS y GCP ofrecen la posibilidad de obtener visibilidad de las recomendaciones de configuración de seguridad sobre cómo mejorar la seguridad en la nube.

Siga estas recomendaciones para supervisar el estado de cumplimiento y la posición de seguridad de toda la organización, incluidas las suscripciones de Azure, las cuentas de AWS y los proyectos de GCP.  
**Más información**:

* [Configuración de seguridad para Azure](security-config.md)
* [Configuración de seguridad para AWS](security-config-aws.md)
* [Configuración de seguridad para GCP](security-config-gcp.md)

---

**Práctica recomendada**: Incorporación de aplicaciones personalizadas  
**Detalle**: Para obtener más visibilidad de las actividades de las aplicaciones de línea de negocio, puede incorporar aplicaciones personalizadas a Cloud App Security. Una vez configuradas las aplicaciones personalizadas, verá información sobre los datos de su uso, las direcciones IP desde las que se usan y la cantidad de tráfico que entra y sale de la aplicación.

Además, puede incorporar una aplicación personalizada, como Control de aplicaciones de acceso condicional, para supervisar sus sesiones de confianza baja.  
**Más información**:

* [Adición de aplicaciones personalizadas a Cloud Discovery](cloud-discovery-custom-apps.md)
* [Incorporación e implementación del Control de aplicaciones de acceso condicional para cualquier aplicación](proxy-deployment-any-app.md)
