---
title: Cómo Cloud App Security ayuda a proteger su entorno de Cisco WebEx
description: En este artículo se proporciona información sobre las ventajas de conectar la aplicación Cisco WebEx a Cloud App Security mediante el conector de API para la visibilidad y el control del uso.
author: shsagir
ms.author: shsagir
ms.service: cloud-app-security
ms.topic: article
ms.date: 12/04/2019
ms.collection: M365-security-compliance
ms.openlocfilehash: 5ee11b6c97bc8aa5b0ec35394ac6f1f40bd3873a
ms.sourcegitcommit: db5ec79d219dd6674939c872ace7cd2ca80860a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/19/2019
ms.locfileid: "75190215"
---
# <a name="how-cloud-app-security-helps-protect-your-cisco-webex-environment"></a>Cómo Cloud App Security ayuda a proteger su entorno de Cisco WebEx

*Se aplica a: Microsoft Cloud App Security*

Como plataforma de comunicación y colaboración, Cisco WebEx permite la comunicación y la colaboración optimizadas en toda la organización. El uso de Cisco WebEx para el intercambio de datos y activos puede exponer la información confidencial de la organización a usuarios externos, por ejemplo, en salones de chat en los que también pueden participar en una conversación con los empleados.

La conexión de Cisco WebEx a Cloud App Security le proporciona información mejorada sobre las actividades de los usuarios, proporciona detecciones de protección de la información y permite controles de gobierno automatizados.

## <a name="main-threats"></a>Amenazas principales

- Cuentas en peligro e Insider amenazas
- Fuga de datos
- Reconocimiento de seguridad insuficiente
- Ransomware
- No administrada traiga su propio dispositivo (BYOD)

## <a name="how-cloud-app-security-helps-to-protect-your-environment"></a>Cómo Cloud App Security ayuda a proteger su entorno

- [Aplicación de directivas de cumplimiento y DLP para los datos almacenados en la nube](best-practices.md#enforce-dlp-and-compliance-policies-for-data-stored-in-the-cloud)
- [Limitar la exposición de los datos compartidos y aplicar directivas de colaboración](best-practices.md#limit-exposure-of-shared-data-and-enforce-collaboration-policies)
- [Usar la traza de auditoría de actividades para investigaciones forenses](best-practices.md#use-the-audit-trail-of-activities-for-forensic-investigations)

## <a name="control-cisco-webex-with-built-in-policies-and-policy-templates"></a>Control de Cisco WebEx con directivas integradas y plantillas de Directiva

Puede usar las siguientes plantillas de directiva integradas para detectar y notificar las posibles amenazas:

| Tipo | Name |
| ---- | ---- |
| Directiva de detección de anomalías integrada | [Actividad realizada por el usuario Terminado](anomaly-detection-policy.md#activity-performed-by-terminated-user) (requiere AAD como IDP)<br />[Varios intentos incorrectos de inicio de sesión](anomaly-detection-policy.md#multiple-failed-login-attempts)<br />[Detección de ransomware](anomaly-detection-policy.md#ransomware-activity)<br />[Actividades de eliminación de archivos inusuales](anomaly-detection-policy.md#unusual-activities-by-user)<br />[Actividades de recurso compartido de archivos inusuales](anomaly-detection-policy.md#unusual-activities-by-user)<br />[Actividades de descarga de varios archivos inusuales](anomaly-detection-policy.md#unusual-activities-by-user) |
| Plantilla de directiva de archivo | Detección de un archivo compartido con un dominio no autorizado<br />Detección de un archivo compartido con direcciones de correo electrónico personales<br />Detección de archivos con PII/PCI/PHI |
| Plantilla de directiva de actividad | Descarga masiva de un solo usuario<br />Actividad potencial de ransomware |

Para obtener más información sobre la creación de directivas, vea [crear una directiva](control-cloud-apps-with-policies.md#create-a-policy).

## <a name="automate-governance-controls"></a>Automatizar los controles de gobierno

Además de supervisar posibles amenazas, puede aplicar y automatizar las siguientes acciones de gobierno de Cisco WebEx para corregir las amenazas detectadas:

| Tipo | Acción |
| ---- | ---- |
| Regulación del usuario | -Notificar al usuario sobre la alerta (a través de Azure AD)<br />-Requerir al usuario que inicie sesión de nuevo (a través de Azure AD)<br />-Suspender usuario (a través de Azure AD) |
| Regulación de datos | -Archivo de papelera |

Para obtener más información acerca de cómo corregir amenazas de aplicaciones, consulte [control de aplicaciones conectadas](governance-actions.md).

## <a name="protect-cisco-webex-in-real-time"></a>Protección de Cisco WebEx en tiempo real

Revise nuestras prácticas recomendadas para [proteger y colaborar con usuarios externos](best-practices.md#secure-collaboration-with-external-users-by-enforcing-real-time-session-controls) y [bloquear y proteger la descarga de datos confidenciales en dispositivos no administrados o de riesgo](best-practices.md#block-and-protect-download-of-sensitive-data-to-unmanaged-or-risky-devices).

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Cómo conectar Cisco WebEx a Microsoft Cloud App Security](connect-webex-to-microsoft-cloud-app-security.md)
