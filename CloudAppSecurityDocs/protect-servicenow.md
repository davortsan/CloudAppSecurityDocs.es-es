---
title: Cómo Cloud App Security ayuda a proteger su entorno de ServiceNow
description: En este artículo se proporciona información sobre las ventajas de conectar la aplicación de ServiceNow a Cloud App Security mediante el conector de API para la visibilidad y el control del uso.
ms.date: 12/04/2019
ms.topic: article
ms.openlocfilehash: 7c317ec64859b8bc1ed56bb7ebb6e815aa035595
ms.sourcegitcommit: d87372b47ca98e942c2bf94032a6a61902627d69
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/30/2020
ms.locfileid: "96315198"
---
# <a name="how-cloud-app-security-helps-protect-your-servicenow-environment"></a>Cómo Cloud App Security ayuda a proteger su entorno de ServiceNow

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Como proveedor principal de la nube de CRM, ServiceNow incorpora grandes cantidades de información confidencial acerca de los clientes, los procesos internos, los incidentes y los informes dentro de la organización. Ser una aplicación crítica para la empresa, se accede a ServiceNow y la usan las personas de la organización y otras personas que no pertenezcan a él (como asociados y contratistas) con fines diferentes. En muchos casos, una gran parte de los usuarios que acceden a ServiceNow tienen un reconocimiento reducido de la seguridad y pueden poner en peligro la información confidencial al compartirla de forma involuntaria. En otros casos, los actores malintencionados pueden obtener acceso a los recursos más confidenciales relacionados con los clientes.

La conexión de ServiceNow a Cloud App Security le proporciona información más detallada sobre las actividades de los usuarios, proporciona detección de amenazas mediante detecciones de anomalías basadas en aprendizaje automático y detecciones de protección de la información, como la identificación cuando se carga información confidencial del cliente en la nube de ServiceNow.

## <a name="main-threats"></a>Amenazas principales

- Cuentas en peligro e Insider amenazas
- Pérdida de datos
- Reconocimiento de seguridad insuficiente
- Ransomware
- No administrada traiga su propio dispositivo (BYOD)

## <a name="how-cloud-app-security-helps-to-protect-your-environment"></a>Cómo Cloud App Security ayuda a proteger su entorno

- [Detección de amenazas en la nube, cuentas en peligro e Insiders malintencionados](best-practices.md#detect-cloud-threats-compromised-accounts-malicious-insiders-and-ransomware)
- [Detección, clasificación, etiquetado y protección de datos regulados y confidenciales almacenados en la nube](best-practices.md#discover-classify-label-and-protect-regulated-and-sensitive-data-stored-in-the-cloud)
- [Aplicación de directivas de cumplimiento y de DLP para datos almacenados en la nube](best-practices.md#enforce-dlp-and-compliance-policies-for-data-stored-in-the-cloud)
- [Limitación de la exposición de datos compartidos y aplicación de directivas de colaboración](best-practices.md#limit-exposure-of-shared-data-and-enforce-collaboration-policies)
- [Uso de la traza de auditoría de actividades para investigaciones forenses](best-practices.md#use-the-audit-trail-of-activities-for-forensic-investigations)

## <a name="control-servicenow-with-built-in-policies-and-policy-templates"></a>Control de ServiceNow con directivas integradas y plantillas de Directiva

Puede usar las siguientes plantillas de directiva integradas para detectar y notificar las posibles amenazas:

| Tipo | Nombre |
| ---- | ---- |
| Directiva de detección de anomalías integrada | [Actividad desde una dirección IP anónima](anomaly-detection-policy.md#activity-from-anonymous-ip-addresses)<br />[Actividad desde un país poco frecuente](anomaly-detection-policy.md#activity-from-infrequent-country)<br />[Actividad desde direcciones IP sospechosas](anomaly-detection-policy.md#activity-from-suspicious-ip-addresses)<br />[Viaje imposible](anomaly-detection-policy.md#impossible-travel)<br />[Actividad realizada por el usuario Terminado](anomaly-detection-policy.md#activity-performed-by-terminated-user) (requiere AAD como IDP)<br />[Varios intentos incorrectos de inicio de sesión](anomaly-detection-policy.md#multiple-failed-login-attempts)<br />[Detección de ransomware](anomaly-detection-policy.md#ransomware-activity)<br />[Varias actividades de descarga de archivos poco habituales](anomaly-detection-policy.md#unusual-activities-by-user) |
| Plantilla de directiva de actividad | Inicio de sesión desde una dirección IP de riesgo<br />Descarga masiva de un solo usuario<br />Actividad potencial de ransomware |
| Plantilla de directiva de archivo | Detección de un archivo compartido con un dominio no autorizado<br />Detección de un archivo compartido con direcciones de correo electrónico personales<br />Detección de archivos con PII/PCI/PHI |

Para obtener más información sobre la creación de directivas, vea [crear una directiva](control-cloud-apps-with-policies.md#create-a-policy).

## <a name="automate-governance-controls"></a>Automatizar los controles de gobierno

Además de supervisar posibles amenazas, puede aplicar y automatizar las siguientes acciones de gobierno de ServiceNow para corregir las amenazas detectadas:

| Tipo | Acción |
| ---- | ---- |
| Regulación de usuario | -Notificar al usuario sobre la alerta (a través de Azure AD)<br />-Requerir al usuario que inicie sesión de nuevo (a través de Azure AD)<br />-Suspender usuario (a través de Azure AD) |

Para obtener más información acerca de cómo corregir amenazas de aplicaciones, consulte [control de aplicaciones conectadas](governance-actions.md).

## <a name="protect-servicenow-in-real-time"></a>Protección de ServiceNow en tiempo real

Revise nuestras prácticas recomendadas para [proteger y colaborar con usuarios externos](best-practices.md#secure-collaboration-with-external-users-by-enforcing-real-time-session-controls) y [bloquear y proteger la descarga de datos confidenciales en dispositivos no administrados o de riesgo](best-practices.md#block-and-protect-download-of-sensitive-data-to-unmanaged-or-risky-devices).

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Cómo conectar ServiceNow con Microsoft Cloud App Security](connect-servicenow-to-microsoft-cloud-app-security.md)
