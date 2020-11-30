---
title: Cómo Cloud App Security ayuda a proteger su entorno de Salesforce
description: En este artículo se proporciona información sobre las ventajas de conectar su aplicación de Salesforce a Cloud App Security mediante el conector de API para la visibilidad y el control del uso.
ms.date: 12/04/2019
ms.topic: article
ms.openlocfilehash: 477f7372bc65a704d6a68f6fd2c9e43de2a27da8
ms.sourcegitcommit: d87372b47ca98e942c2bf94032a6a61902627d69
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/30/2020
ms.locfileid: "96310829"
---
# <a name="how-cloud-app-security-helps-protect-your-salesforce-environment"></a>Cómo Cloud App Security ayuda a proteger su entorno de Salesforce

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Como proveedor principal de la nube de CRM, Salesforce incorpora grandes cantidades de información confidencial sobre clientes, guías de precios y principales negocios dentro de su organización. Ser una aplicación crítica para la empresa, se accede a Salesforce y la usan las personas dentro de la organización y otros usuarios ajenos a ella (como asociados y contratistas) para distintos propósitos. En muchos casos, una gran parte de los usuarios que acceden a Salesforce tienen un reconocimiento reducido de la seguridad y pueden poner en peligro la información confidencial al compartirla de forma involuntaria. En otros casos, los actores malintencionados pueden obtener acceso a los recursos más confidenciales relacionados con los clientes.

La conexión de Salesforce a Cloud App Security le proporciona información más detallada sobre las actividades de los usuarios, proporciona detección de amenazas mediante detecciones de anomalías basadas en aprendizaje automático y detecciones de protección de la información (como la detección de uso compartido de información externo), habilita los controles de corrección automatizada y detecta amenazas de aplicaciones de terceros habilitadas en su organización.

## <a name="main-threats"></a>Amenazas principales

- Cuentas en peligro e Insider amenazas
- Pérdida de datos
- Privilegios elevados
- Reconocimiento de seguridad insuficiente
- Aplicaciones de terceros malintencionadas y complementos de Google
- Ransomware
- No administrada traiga su propio dispositivo (BYOD)

## <a name="how-cloud-app-security-helps-to-protect-your-environment"></a>Cómo Cloud App Security ayuda a proteger su entorno

- [Detección de amenazas en la nube, cuentas en peligro e Insiders malintencionados](best-practices.md#detect-cloud-threats-compromised-accounts-malicious-insiders-and-ransomware)
- [Detección, clasificación, etiquetado y protección de datos regulados y confidenciales almacenados en la nube](best-practices.md#discover-classify-label-and-protect-regulated-and-sensitive-data-stored-in-the-cloud)
- [Detección y administración de aplicaciones de OAuth que tienen acceso a su entorno](manage-app-permissions.md)
- [Aplicación de directivas de cumplimiento y de DLP para datos almacenados en la nube](best-practices.md#enforce-dlp-and-compliance-policies-for-data-stored-in-the-cloud)
- [Limitación de la exposición de datos compartidos y aplicación de directivas de colaboración](best-practices.md#limit-exposure-of-shared-data-and-enforce-collaboration-policies)
- [Uso de la traza de auditoría de actividades para investigaciones forenses](best-practices.md#use-the-audit-trail-of-activities-for-forensic-investigations)

## <a name="control-salesforce-with-built-in-policies-and-policy-templates"></a>Control de Salesforce con directivas integradas y plantillas de Directiva

Puede usar las siguientes plantillas de directiva integradas para detectar y notificar las posibles amenazas:

| Tipo | Nombre |
| ---- | ---- |
| Directiva de detección de anomalías integrada | [Actividad desde una dirección IP anónima](anomaly-detection-policy.md#activity-from-anonymous-ip-addresses)<br />[Actividad desde un país poco frecuente](anomaly-detection-policy.md#activity-from-infrequent-country)<br />[Actividad desde direcciones IP sospechosas](anomaly-detection-policy.md#activity-from-suspicious-ip-addresses)<br />[Viaje imposible](anomaly-detection-policy.md#impossible-travel)<br />[Actividad realizada por el usuario Terminado](anomaly-detection-policy.md#activity-performed-by-terminated-user) (requiere AAD como IDP)<br />[Varios intentos incorrectos de inicio de sesión](anomaly-detection-policy.md#multiple-failed-login-attempts)<br />[Detección de ransomware](anomaly-detection-policy.md#ransomware-activity)<br />[Actividades administrativas poco habituales](anomaly-detection-policy.md#unusual-activities-by-user)<br />[Actividades inusuales de eliminación de archivos](anomaly-detection-policy.md#unusual-activities-by-user)<br />[Actividades inusuales de uso compartido de archivos](anomaly-detection-policy.md#unusual-activities-by-user)<br />[Actividades inusuales de suplantación](anomaly-detection-policy.md#unusual-activities-by-user)<br />[Varias actividades de descarga de archivos poco habituales](anomaly-detection-policy.md#unusual-activities-by-user) |
| Plantilla de directiva de actividad | Inicio de sesión desde una dirección IP de riesgo<br />Descarga masiva de un solo usuario<br />Actividad potencial de ransomware |
| Plantilla de directiva de archivo | Detección de un archivo compartido con un dominio no autorizado<br />Detección de un archivo compartido con direcciones de correo electrónico personales<br />Detección de archivos con PII/PCI/PHI |

Para obtener más información sobre la creación de directivas, vea [crear una directiva](control-cloud-apps-with-policies.md#create-a-policy).

## <a name="automate-governance-controls"></a>Automatizar los controles de gobierno

Además de supervisar posibles amenazas, puede aplicar y automatizar las siguientes acciones de control de Salesforce para corregir las amenazas detectadas:

| Tipo | Acción |
| ---- | ---- |
| Regulación de usuario | -Notificar a los usuarios de las alertas pendientes<br />-Enviar el Resumen de infracciones de DLP a los propietarios de archivos<br />-Suspender usuario<br />-Notificar al usuario sobre la alerta (a través de Azure AD)<br />-Requerir al usuario que inicie sesión de nuevo (a través de Azure AD)<br />-Suspender usuario (a través de Azure AD) |
| Control de aplicaciones de OAuth | -Revocar aplicación de OAuth para usuarios |

Para obtener más información acerca de cómo corregir amenazas de aplicaciones, consulte [control de aplicaciones conectadas](governance-actions.md).

## <a name="protect-salesforce-in-real-time"></a>Protección de Salesforce en tiempo real

Revise nuestras prácticas recomendadas para [proteger y colaborar con usuarios externos](best-practices.md#secure-collaboration-with-external-users-by-enforcing-real-time-session-controls) y [bloquear y proteger la descarga de datos confidenciales en dispositivos no administrados o de riesgo](best-practices.md#block-and-protect-download-of-sensitive-data-to-unmanaged-or-risky-devices).

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Cómo conectar Salesforce a Microsoft Cloud App Security](connect-salesforce-to-microsoft-cloud-app-security.md)
