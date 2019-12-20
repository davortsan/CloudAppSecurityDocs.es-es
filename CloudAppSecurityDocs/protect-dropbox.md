---
title: Cómo Cloud App Security ayuda a proteger el entorno de Dropbox
description: En este artículo se proporciona información sobre las ventajas de conectar la aplicación de Dropbox a Cloud App Security mediante el conector de API para la visibilidad y el control del uso.
author: shsagir
ms.author: shsagir
ms.service: cloud-app-security
ms.topic: article
ms.date: 12/04/2019
ms.collection: M365-security-compliance
ms.openlocfilehash: 090aed9021a1323b99cd254d9d857bc9894ca87f
ms.sourcegitcommit: db5ec79d219dd6674939c872ace7cd2ca80860a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/19/2019
ms.locfileid: "75190075"
---
# <a name="how-cloud-app-security-helps-protect-your-dropbox-environment"></a>Cómo Cloud App Security ayuda a proteger el entorno de Dropbox

*Se aplica a: Microsoft Cloud App Security*

Como herramienta de colaboración y almacenamiento de archivos en la nube, Dropbox permite que los usuarios compartan sus documentos en su organización y asociados de una manera simplificada y eficaz. El uso de Dropbox puede exponer los datos confidenciales no solo internamente, sino también a colaboradores externos, o incluso peor hacer que esté disponible públicamente a través de un vínculo compartido. Estos incidentes pueden estar causados por actores malintencionados o por empleados no conscientes de ello.

La conexión de Dropbox a Cloud App Security ofrece información más detallada sobre las actividades de los usuarios, proporciona detección de amenazas mediante detecciones de anomalías basadas en aprendizaje automático, detecciones de protección de la información, como la detección de uso compartido externo de la información, y habilitación de los controles de corrección automatizados.

## <a name="main-threats"></a>Amenazas principales

- Cuentas en peligro e Insider amenazas
- Fuga de datos
- Reconocimiento de seguridad insuficiente
- Malware
- Ransomware
- No administrada traiga su propio dispositivo (BYOD)

## <a name="how-cloud-app-security-helps-to-protect-your-environment"></a>Cómo Cloud App Security ayuda a proteger su entorno

- [Detección de amenazas en la nube, cuentas en peligro e Insiders malintencionados](best-practices.md#detect-cloud-threats-compromised-accounts-malicious-insiders-and-ransomware)
- [Detectar, clasificar, etiquetar y proteger la información regulada y confidencial almacenada en la nube](best-practices.md#discover-classify-label-and-protect-regulated-and-sensitive-data-stored-in-the-cloud)
- [Aplicación de directivas de cumplimiento y DLP para los datos almacenados en la nube](best-practices.md#enforce-dlp-and-compliance-policies-for-data-stored-in-the-cloud)
- [Limitar la exposición de los datos compartidos y aplicar directivas de colaboración](best-practices.md#limit-exposure-of-shared-data-and-enforce-collaboration-policies)
- [Usar la traza de auditoría de actividades para investigaciones forenses](best-practices.md#use-the-audit-trail-of-activities-for-forensic-investigations)

## <a name="control-dropbox-with-built-in-policies-and-policy-templates"></a>Controlar Dropbox con directivas integradas y plantillas de Directiva

Puede usar las siguientes plantillas de directiva integradas para detectar y notificar las posibles amenazas:

| Tipo | Name |
| ---- | ---- |
| Directiva de detección de anomalías integrada | [Actividad desde direcciones IP anónimas](anomaly-detection-policy.md#activity-from-anonymous-ip-addresses)<br />[Actividad desde un país poco frecuente](anomaly-detection-policy.md#activity-from-infrequent-country)<br />[Actividad desde direcciones IP sospechosas](anomaly-detection-policy.md#activity-from-suspicious-ip-addresses)<br />[Viaje imposible](anomaly-detection-policy.md#impossible-travel)<br />[Actividad realizada por el usuario Terminado](anomaly-detection-policy.md#activity-performed-by-terminated-user) (requiere AAD como IDP)<br />[Detección de malware](anomaly-detection-policy.md#malware-detection)<br />[Varios intentos incorrectos de inicio de sesión](anomaly-detection-policy.md#multiple-failed-login-attempts)<br />[Detección de ransomware](anomaly-detection-policy.md#ransomware-activity)<br />[Actividades de eliminación de archivos inusuales](anomaly-detection-policy.md#unusual-activities-by-user)<br />[Actividades de recurso compartido de archivos inusuales](anomaly-detection-policy.md#unusual-activities-by-user)<br />[Actividades de descarga de varios archivos inusuales](anomaly-detection-policy.md#unusual-activities-by-user) |
| Plantilla de directiva de actividad | Inicio de sesión desde una dirección IP de riesgo<br />Descarga masiva de un solo usuario<br />Actividad potencial de ransomware |
| Plantilla de directiva de archivo | Detección de un archivo compartido con un dominio no autorizado<br />Detección de un archivo compartido con direcciones de correo electrónico personales<br />Detección de archivos con PII/PCI/PHI |

Para obtener más información sobre la creación de directivas, vea [crear una directiva](control-cloud-apps-with-policies.md#create-a-policy).

## <a name="automate-governance-controls"></a>Automatizar los controles de gobierno

Además de supervisar posibles amenazas, puede aplicar y automatizar las siguientes acciones de control de Dropbox para corregir las amenazas detectadas:

| Tipo | Acción |
| ---- | ---- |
| Regulación de datos | -Quitar el vínculo compartido directo<br />-Enviar el Resumen de infracciones de DLP a los propietarios de archivos<br />-Archivo de papelera |
| Regulación del usuario | -Notificar al usuario sobre la alerta (a través de Azure AD)<br /> -Requerir al usuario que inicie sesión de nuevo (a través de Azure AD)<br /> -Suspender usuario (a través de Azure AD) |

Para obtener más información acerca de cómo corregir amenazas de aplicaciones, consulte [control de aplicaciones conectadas](governance-actions.md).

## <a name="protect-dropbox-in-real-time"></a>Proteger Dropbox en tiempo real

Revise nuestras prácticas recomendadas para [proteger y colaborar con usuarios externos](best-practices.md#secure-collaboration-with-external-users-by-enforcing-real-time-session-controls) y [bloquear y proteger la descarga de datos confidenciales en dispositivos no administrados o de riesgo](best-practices.md#block-and-protect-download-of-sensitive-data-to-unmanaged-or-risky-devices).

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Cómo conectar Dropbox a Microsoft Cloud App Security](connect-dropbox-to-microsoft-cloud-app-security.md)
