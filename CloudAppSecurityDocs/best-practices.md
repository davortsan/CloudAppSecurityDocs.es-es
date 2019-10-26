---
title: 'Prácticas recomendadas para proteger su organización: Cloud App Security'
description: En este artículo se proporciona un conjunto de procedimientos recomendados para proteger la organización.
author: shsagir
ms.author: shsagir
ms.service: cloud-app-security
ms.topic: best-practice
ms.date: 10/24/2019
ms.collection: M365-security-compliance
ms.openlocfilehash: 9e505044d94ce633bdba5f2b684873391d57f772
ms.sourcegitcommit: 3a44f020c6ae7f6c4956bf53727dfb0e82fd7cf0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2019
ms.locfileid: "72887947"
---
# <a name="cloud-app-security-best-practices"></a>Procedimientos recomendados de Cloud App Security

*Se aplica a: Microsoft Cloud App Security*

En este artículo se proporcionan prácticas recomendadas para proteger su organización mediante el uso de Microsoft Cloud App Security. Estos procedimientos recomendados proceden de nuestra experiencia con Cloud App Security y las experiencias de clientes como usted.

Los procedimientos recomendados que se describen en este artículo son:

> [!div class="checklist"]
> * [Detección y evaluación de aplicaciones en la nube](#discover-and-assess-cloud-apps)
> * [Aplicar directivas de gobierno en la nube](#apply-cloud-governance-policies)
> * [Limitar la exposición de los datos compartidos y aplicar directivas de colaboración](#limit-exposure-of-shared-data-and-enforce-collaboration-policies)
> * [Detectar, clasificar, etiquetar y proteger la información regulada y confidencial almacenada en la nube](#discover-classify-label-and-protect-regulated-and-sensitive-data-stored-in-the-cloud)
> * [Aplicación de directivas de cumplimiento y DLP para los datos almacenados en la nube](#enforce-dlp-and-compliance-policies-for-data-stored-in-the-cloud)
> * [Bloquear y proteger la descarga de datos confidenciales en dispositivos no administrados o peligrosos](#block-and-protect-download-of-sensitive-data-to-unmanaged-or-risky-devices)
> * [Colaboración segura con usuarios externos mediante la aplicación de controles de sesión en tiempo real](#secure-collaboration-with-external-users-by-enforcing-real-time-session-controls)
> * [Detección de amenazas en la nube, cuentas en peligro, Insiders malintencionados y ransomware](#detect-cloud-threats-compromised-accounts-malicious-insiders-and-ransomware)
> * [Usar la traza de auditoría de actividades para investigaciones forenses](#use-the-audit-trail-of-activities-for-forensic-investigations)
> * [Servicios de IaaS seguros y aplicaciones personalizadas](#secure-iaas-services-and-custom-apps)

## <a name="discover-and-assess-cloud-apps"></a>Detección y evaluación de aplicaciones en la nube

La integración de Cloud App Security con protección contra amenazas avanzada de Microsoft defender (ATP de Microsoft defender) le ofrece la posibilidad de usar Cloud Discovery más allá de la red corporativa o de puertas de enlace web seguras. Con la información de usuario y equipo combinada, puede identificar equipos o usuarios de riesgo, ver qué aplicaciones están usando e investigar más en el portal de ATP de Microsoft defender.

**Procedimiento**recomendado: habilitar Shadow it Discovery mediante ATP de Microsoft defender  
**Detalle**: Cloud Discovery analiza los registros de tráfico recopilados por ATP de Microsoft defender y evalúa las aplicaciones identificadas con el catálogo de aplicaciones en la nube para proporcionar información de seguridad y cumplimiento normativo. Al configurar Cloud Discovery, obtiene visibilidad del uso de la nube, la sombra y la supervisión continua de las aplicaciones no autorizadas que usan los usuarios.  
**Para obtener más información**:

* [Integración de ATP de Microsoft defender con Cloud App Security](wdatp-integration.md)
* [Configurar Cloud Discovery](set-up-cloud-discovery.md)
* [Detección y administración de shadow IT en la red](tutorial-shadow-it.md)

---

**Procedimiento**recomendado: configuración de directivas de detección de aplicaciones para identificar de forma proactiva aplicaciones de riesgo, no compatibles y de tendencias  
**Detalles**: las directivas de detección de aplicaciones facilitan el seguimiento de las aplicaciones importantes detectadas en su organización para ayudarle a administrar estas aplicaciones de forma eficaz. Cree directivas para recibir alertas cuando detecte nuevas aplicaciones que se identifican como peligrosas, no compatibles, de tendencia o de gran volumen.  
**Para obtener más información**:

* [Directivas de Cloud Discovery](cloud-discovery-policies.md)
* [Directiva de detección de anomalías de Cloud Discovery](cloud-discovery-anomaly-detection-policy.md)
* [Obtención de análisis de comportamiento y detección de anomalías instantáneos](anomaly-detection-policy.md)

---

**Procedimiento**recomendado: administración de aplicaciones de OAuth autorizadas por los usuarios  
**Detalle**: muchos usuarios conceden casualmente permisos de OAuth a aplicaciones de terceros para acceder a la información de su cuenta y, al hacerlo, también proporcionan acceso involuntariamente a sus datos en otras aplicaciones en la nube. Normalmente, no tiene visibilidad en estas aplicaciones, por lo que resulta difícil sopesar el riesgo de seguridad de una aplicación frente a las ventajas de productividad que proporciona.

Cloud App Security le proporciona la capacidad de investigar y supervisar los permisos de aplicación que los usuarios han concedido. Puede usar esta información para identificar una aplicación potencialmente sospechosa y, si determina que es arriesgado, puede ser prohibir el acceso a ella.  
**Para obtener más información**:

* [Administrar aplicaciones de OAuth](manage-app-permissions.md)
* [Directivas de aplicación de OAuth](app-permission-policy.md)

---
---
---
---

## <a name="apply-cloud-governance-policies"></a>Aplicar directivas de gobierno en la nube

**Procedimiento**recomendado: aplicaciones de etiquetas y scripts de bloques de exportación  
**Detalles**: después de revisar la lista de aplicaciones detectadas en su organización, puede proteger su entorno contra el uso no deseado de la aplicación. Puede aplicar la etiqueta **autorizada** a las aplicaciones aprobadas por su organización y la etiqueta no **autorizada** a las aplicaciones que no lo están. Puede supervisar aplicaciones no autorizadas con filtros de detección o exportar un script para bloquear aplicaciones no autorizadas mediante los dispositivos de seguridad locales. El uso de etiquetas y scripts de exportación le permite organizar las aplicaciones y proteger su entorno, ya que solo permite el acceso a las aplicaciones seguras.  
**Para obtener más información**:

* [Control de aplicaciones detectadas](governance-discovery.md)

---
---
---
---

## <a name="limit-exposure-of-shared-data-and-enforce-collaboration-policies"></a>Limitar la exposición de los datos compartidos y aplicar directivas de colaboración

**Procedimiento**recomendado: conectar Office 365  
**Detalle**: la conexión de Office 365 a Cloud App Security ofrece visibilidad inmediata de las actividades de los usuarios, los archivos a los que acceden y proporciona acciones de gobierno para Office 365, SharePoint, OneDrive, Teams, Power BI, Exchange y Dynamics.  
**Para obtener más información**:

* [Conectar aplicaciones](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md)
* [Conectar Office 365 con Microsoft Cloud App Security](connect-office-365-to-microsoft-cloud-app-security.md)

---

**Procedimiento**recomendado: conectar aplicaciones de terceros  
**Detalles**: la conexión de aplicaciones de terceros a Cloud App Security ofrece información mejorada sobre las actividades de los usuarios, la detección de amenazas y las capacidades de gobierno. Se admiten las siguientes API de aplicación de terceros: [Amazon Web Services (AWS)](connect-aws-to-microsoft-cloud-app-security.md), [Box](connect-box-to-microsoft-cloud-app-security.md), [Dropbox](connect-dropbox-to-microsoft-cloud-app-security.md), [G Suite](connect-google-apps-to-microsoft-cloud-app-security.md), [Okta](connect-okta-to-microsoft-cloud-app-security.md), [Salesforce](connect-salesforce-to-microsoft-cloud-app-security.md), [ServiceNow](connect-servicenow-to-microsoft-cloud-app-security.md), [WebEx](connect-webex-to-microsoft-cloud-app-security.md)y [WorkDay](connect-workday-to-microsoft-cloud-app-security.md).  
**Para obtener más información**:

* [Conectar aplicaciones](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md)

---

**Procedimiento**recomendado: revisar la exposición de los datos de la organización  
**Detalle**: Use los informes de exposición de archivos para obtener visibilidad sobre el modo en que los usuarios comparten archivos con aplicaciones en la nube. Los informes siguientes están disponibles y se pueden exportar a para un análisis más exhaustivo en herramientas como Microsoft Power BI:

* **Información general sobre el uso compartido de datos**: muestra los archivos por permisos de acceso almacenados en cada una de las aplicaciones en la nube
* **Uso compartido de salida por dominio**: enumera los dominios con los que los empleados comparten los archivos corporativos
* **Propietarios de archivos compartidos**: muestra los usuarios que comparten archivos corporativos con el mundo exterior.  
**Para obtener más información**:

* [Generar informes de administración de datos](built-in-reports.md)

---

**Procedimiento**recomendado: crear directivas para quitar el uso compartido con cuentas personales  
**Detalle**: la conexión de Office 365 a Cloud App Security ofrece visibilidad inmediata de las actividades de los usuarios, los archivos a los que acceden y proporciona acciones de gobierno para Office 365, SharePoint, OneDrive, Teams, Power BI, Exchange y Dynamics.  
**Para obtener más información**:

* [Control de aplicaciones conectadas](governance-actions.md)

---
---
---
---

## <a name="discover-classify-label-and-protect-regulated-and-sensitive-data-stored-in-the-cloud"></a>Detectar, clasificar, etiquetar y proteger la información regulada y confidencial almacenada en la nube

**Procedimiento**recomendado: integración con Azure Information Protection  
**Detalle**: la integración con Azure Information Protection ofrece la capacidad de aplicar automáticamente etiquetas de clasificación y, opcionalmente, agregar protección de cifrado. Una vez que la integración está activada, puede aplicar etiquetas como una acción de gobierno, ver archivos por clasificación, investigar archivos por nivel de clasificación y crear directivas granulares para asegurarse de que los archivos clasificados se controlan correctamente. Si no activa la integración, no podrá beneficiarse de la capacidad de examinar, etiquetar y cifrar archivos automáticamente en la nube.  
**Para obtener más información**:

* [Integración de Azure Information Protection](azip-integration.md)
* [Tutorial: aplicar automáticamente etiquetas de clasificación de Azure Information Protection](use-case-information-protection.md)

---

**Procedimiento**recomendado: crear directivas de exposición de datos  
**Detalles**: Use las directivas de archivo para detectar información confidencial y el uso compartido de información en las aplicaciones en la nube. Cree las siguientes directivas de archivo para avisarle cuando se detecten exposiciones de datos:

* Archivos compartidos externamente que contienen datos confidenciales
* Archivos compartidos externamente y etiquetados como **confidenciales**
* Archivos compartidos con dominios no autorizados
* Protección de archivos confidenciales en aplicaciones SaaS

**Para obtener más información**:

* [Inspección de contenido](content-inspection.md)
* [Directivas de archivos](data-protection-policies.md)
* [Directivas de protección de información](policies-information-protection.md)

---

**Procedimiento**recomendado: revisar informes en la página **archivos**  
**Detalles**: una vez que haya conectado varias aplicaciones SaaS mediante conectores de aplicaciones, Cloud App Security examinará los archivos almacenados por estas aplicaciones. Además, cada vez que se modifica un archivo, se vuelve a examinar. Puede usar la página **archivos** para entender e investigar los tipos de datos que se almacenan en las aplicaciones en la nube. Para ayudarle a investigar, puede filtrar por dominios, grupos, usuarios, fecha de creación, extensión, nombre de archivo y tipo, ID. de archivo, etiqueta de clasificación, etc. El uso de estos filtros le permite controlar el modo en que decide investigar los archivos para asegurarse de que ninguno de los datos está en riesgo. Una vez que tenga una mejor comprensión de cómo se usan los datos, puede crear directivas para buscar contenido confidencial en estos archivos.  
**Para obtener más información**:

* [Conectar aplicaciones](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md)
* [Filtros de archivo](file-filters.md)
* [Inspección de contenido](content-inspection.md)

---
---
---
---

## <a name="enforce-dlp-and-compliance-policies-for-data-stored-in-the-cloud"></a>Aplicación de directivas de cumplimiento y DLP para los datos almacenados en la nube

**Procedimiento**recomendado: evitar que los datos confidenciales se compartan con usuarios externos  
**Detalle**: cree una directiva de archivo que detecte Cuándo un usuario intenta compartir un archivo con la etiqueta de clasificación **confidencial** con una persona externa a la organización y configure su acción de gobierno para quitar usuarios externos. Esta Directiva garantiza que los datos confidenciales no salen de su organización y los usuarios externos no pueden obtener acceso a ellos.  
**Para obtener más información**:

* [Control de aplicaciones conectadas](governance-actions.md)

---
---
---
---

## <a name="block-and-protect-download-of-sensitive-data-to-unmanaged-or-risky-devices"></a>Bloquear y proteger la descarga de datos confidenciales en dispositivos no administrados o peligrosos

**Procedimiento**recomendado: administrar y controlar el acceso a dispositivos de alto riesgo  
**Detalle**: Use control de aplicaciones de acceso condicional para establecer controles en las aplicaciones SaaS. Puede crear directivas de sesión para supervisar las sesiones de bajo riesgo y de bajo nivel de confianza. Del mismo modo, puede crear directivas de sesión para bloquear y proteger las descargas de los usuarios que intentan acceder a datos confidenciales desde dispositivos no administrados o de riesgo. Si no va a crear directivas de sesión para supervisar las sesiones de alto riesgo, perderá la capacidad de bloquear y proteger las descargas en el cliente web, así como la capacidad de supervisar sesiones de confianza baja en aplicaciones de Microsoft y de terceros.  
**Para obtener más información**:

* [Protección de aplicaciones con Microsoft Cloud App Security Control de aplicaciones de acceso condicional](proxy-intro-aad.md)
* [Directivas de sesión](session-policy-aad.md)

---
---
---
---

## <a name="secure-collaboration-with-external-users-by-enforcing-real-time-session-controls"></a>Colaboración segura con usuarios externos mediante la aplicación de controles de sesión en tiempo real

**Procedimiento**recomendado: supervisar sesiones con usuarios externos mediante control de aplicaciones de acceso condicional  
**Detalle**: para proteger la colaboración en su entorno, puede crear una directiva de sesión para supervisar las sesiones entre los usuarios internos y externos. Esto no solo le ofrece la capacidad de supervisar la sesión entre los usuarios (y les notifica que sus actividades de sesión se están supervisando), pero también le permite limitar las actividades específicas. Al crear directivas de sesión para supervisar la actividad, puede elegir las aplicaciones y los usuarios que le gustaría supervisar.  
**Para obtener más información**:

* [Protección de aplicaciones con Microsoft Cloud App Security Control de aplicaciones de acceso condicional](proxy-intro-aad.md)
* [Directivas de sesión](session-policy-aad.md)

---
---
---
---

## <a name="detect-cloud-threats-compromised-accounts-malicious-insiders-and-ransomware"></a>Detección de amenazas en la nube, cuentas en peligro, Insiders malintencionados y ransomware

**Procedimiento**recomendado: ajuste de directivas de anomalías, establecimiento de intervalos IP y envío de comentarios para alertas  
**Detalle**: las directivas de detección de anomalías proporcionan análisis de comportamiento de usuarios y entidades (UEBA) y aprendizaje automático (ml) para que pueda ejecutar inmediatamente la detección de amenazas avanzada en el entorno de nube.

Las directivas de detección de anomalías se desencadenan cuando hay actividades inusuales realizadas por los usuarios de su entorno. Cloud App Security supervisa continuamente las actividades de los usuarios y usa UEBA y ML para aprender y comprender el comportamiento *normal* de los usuarios. Puede ajustar la configuración de la Directiva para que se adapte a los requisitos de su organización, por ejemplo, puede establecer la confidencialidad de una directiva, así como definir el ámbito de una directiva para un grupo específico.

* **Ajuste y ámbito de las directivas de detección de anomalías**: por ejemplo, para reducir el número de falsos positivos dentro de la alerta de viaje imposible, puede establecer el control deslizante de sensibilidad de la Directiva en Low. Si tiene usuarios de su organización que tienen una frecuencia de viajeros corporativas, puede agregarlos a un grupo de usuarios y seleccionar ese grupo en el ámbito de la Directiva.

* **Establecer intervalos IP**: Cloud App Security puede identificar direcciones IP conocidas una vez que se establecen intervalos de direcciones IP. Con los intervalos de direcciones IP configurados, puede etiquetar, clasificar y personalizar la forma en que se muestran e investigan los registros y las alertas. Agregar intervalos de direcciones IP ayuda a reducir las detecciones de falsos positivos y a mejorar la precisión de las alertas. Si decide no agregar las direcciones IP, es posible que vea un mayor número de posibles falsos positivos y alertas para investigar.

* **Enviar comentarios para las alertas**

    Al descartar o resolver las alertas, asegúrese de enviar comentarios con el motivo por el que descartó la alerta o cómo se resolvió. Esta información ayuda a Cloud App Security a mejorar nuestras alertas y reducir los falsos positivos.

**Para obtener más información**:

* [Obtención de análisis de comportamiento y detección de anomalías instantáneos](anomaly-detection-policy.md)
* [Trabajar con etiquetas y intervalos IP](ip-tags.md)
* [Supervisión de alertas en Cloud App Security](monitor-alerts.md)

---

**Procedimiento**recomendado: detección de la actividad de lugares o países inesperados  
**Detalle**: cree una directiva de actividad para recibir una notificación cuando los usuarios inicien sesión desde ubicaciones o países inesperados. Estas notificaciones pueden alertarle de posibles sesiones en peligro en su entorno para que pueda detectar y corregir amenazas antes de que se produzcan.  
**Para obtener más información**:

* [Directivas de protección contra amenazas](policies-threat-protection.md)

---

**Procedimiento**recomendado: crear directivas de aplicación de OAuth  
**Detalle**: cree una directiva de aplicación de OAuth para recibir una notificación cuando una aplicación de OAuth cumpla determinados criterios. Por ejemplo, puede optar por recibir una notificación cuando una aplicación específica que requiera un nivel de permisos elevado sea accesible por más de 100 usuarios.  
**Para obtener más información**:

* [Directivas de aplicación de OAuth](app-permission-policy.md)

---
---
---
---

## <a name="use-the-audit-trail-of-activities-for-forensic-investigations"></a>Usar la traza de auditoría de actividades para investigaciones forenses

**Procedimiento**recomendado: usar la traza de auditoría de las actividades al investigar alertas  
**Detalle**: las alertas se desencadenan cuando las actividades de usuario, administrador o inicio de sesión no cumplen las directivas. Es importante investigar las alertas para saber si hay una posible amenaza en el entorno.

Puede investigar una alerta seleccionándola en la página de **alertas** y revisando la traza de auditoría de las actividades relacionadas con esa alerta. La traza de auditoría ofrece visibilidad en las actividades del mismo tipo, el mismo usuario, la misma dirección IP y la misma ubicación, para proporcionarle la historia general de una alerta. Si una alerta garantiza más investigación, cree un plan para resolver estas alertas en su organización.

Al descartar las alertas, es importante investigar y comprender por qué no son de importancia o si son falsos positivos. Si hay un gran volumen de estas actividades, también puede considerar la posibilidad de revisar y optimizar la Directiva que desencadena la alerta.  
**Para obtener más información**:

* [Actividades](activity-filters.md)

---
---
---
---

## <a name="secure-iaas-services-and-custom-apps"></a>Servicios de IaaS seguros y aplicaciones personalizadas

**Procedimiento**recomendado: conectar Azure y AWS  
**Detalle**: la conexión de cada una de estas aplicaciones de almacenamiento en la nube a Cloud App Security le ayuda a mejorar las capacidades de detección de amenazas. Mediante la supervisión de las actividades administrativas e inicios de sesión para estos servicios, puede detectar y recibir notificaciones sobre posibles ataques por fuerza bruta, el uso malintencionado de una cuenta de usuario con privilegios y otras amenazas de su entorno. Por ejemplo, puede identificar riesgos como eliminaciones inusuales de máquinas virtuales o incluso actividades de suplantación en estas aplicaciones.  
**Para obtener más información**:

* [Conectar Azure con Microsoft Cloud App Security](connect-azure-to-microsoft-cloud-app-security.md)
* [Conectar AWS con Microsoft Cloud App Security](connect-aws-to-microsoft-cloud-app-security.md)

---

**Procedimiento**recomendado: revisión de CSPM para Azure y AWS  
**Detalle**: la integración con Azure Security Center proporciona una evaluación de la configuración de seguridad de su entorno de Azure. La evaluación proporciona recomendaciones para la configuración y el control de seguridad que faltan. Revisar estas recomendaciones le ayuda a identificar anomalías y posibles vulnerabilidades en su entorno y navegar directamente en la ubicación correspondiente en el portal de seguridad de Azure para resolverlas.

AWS le ofrece la capacidad de obtener visibilidad de las recomendaciones de configuración de seguridad sobre cómo mejorar la seguridad en la nube. Con estas recomendaciones, puede supervisar el estado de cumplimiento de las cuentas de AWS.  
**Para obtener más información**:

* [Configuración de seguridad de Azure](security-config.md)
* [Configuración de seguridad para AWS](security-config-aws.md)

---

**Procedimiento**recomendado: incorporación de aplicaciones personalizadas  
**Detalle**: para obtener visibilidad adicional de las actividades de las aplicaciones de línea de negocio, puede incorporar aplicaciones personalizadas a Cloud App Security. Una vez configuradas las aplicaciones personalizadas, verá información sobre los datos de su uso, las direcciones IP desde las que se usan y la cantidad de tráfico que entra y sale de la aplicación.

Además, puede incorporar una aplicación personalizada como Control de aplicaciones de acceso condicional aplicación para supervisar sus sesiones de confianza baja.  
**Para obtener más información**:

* [Incorporación de aplicaciones personalizadas a Cloud Discovery](cloud-discovery-custom-apps.md)
* [Incorporación e implementación de Control de aplicaciones de acceso condicional para cualquier aplicación](proxy-deployment-any-app.md)
