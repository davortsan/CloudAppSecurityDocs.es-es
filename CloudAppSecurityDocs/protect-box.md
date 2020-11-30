---
title: Cómo Cloud App Security ayuda a proteger su entorno de Box
description: En este artículo se proporciona información sobre las ventajas de conectar la aplicación de Box a Cloud App Security mediante el conector de API para la visibilidad y el control del uso.
ms.date: 12/04/2019
ms.topic: article
ms.openlocfilehash: 6ab53ae59f13e59029ee6745922e28c89afa3566
ms.sourcegitcommit: d87372b47ca98e942c2bf94032a6a61902627d69
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/30/2020
ms.locfileid: "96315300"
---
# <a name="how-cloud-app-security-helps-protect-your-box-environment"></a>Cómo Cloud App Security ayuda a proteger su entorno de Box

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Como herramienta de colaboración y almacenamiento de archivos en la nube, el cuadro permite a los usuarios compartir sus documentos en la organización y los asociados de una manera simplificada y eficaz. Usar Box puede exponer los datos confidenciales no solo internamente, sino también a colaboradores externos, o incluso peor hacer que esté disponible públicamente a través de un vínculo compartido. Estos incidentes pueden estar causados por actores malintencionados o por empleados no conscientes de ello.

En el cuadro de conexión a Cloud App Security se proporciona información detallada sobre las actividades de los usuarios, se proporciona detección de amenazas mediante detecciones de anomalías basadas en aprendizaje automático, detecciones de protección de la información, como la detección de recursos compartidos de información externa y la habilitación de controles de corrección automatizados.

## <a name="main-threats"></a>Amenazas principales

- Cuentas en peligro e Insider amenazas
- Pérdida de datos
- Reconocimiento de seguridad insuficiente
- Malware
- Ransomware
- No administrada traiga su propio dispositivo (BYOD)

## <a name="how-cloud-app-security-helps-to-protect-your-environment"></a>Cómo Cloud App Security ayuda a proteger su entorno

- [Detección de amenazas en la nube, cuentas en peligro e Insiders malintencionados](best-practices.md#detect-cloud-threats-compromised-accounts-malicious-insiders-and-ransomware)
- [Detección, clasificación, etiquetado y protección de datos regulados y confidenciales almacenados en la nube](best-practices.md#discover-classify-label-and-protect-regulated-and-sensitive-data-stored-in-the-cloud)
- [Aplicación de directivas de cumplimiento y de DLP para datos almacenados en la nube](best-practices.md#enforce-dlp-and-compliance-policies-for-data-stored-in-the-cloud)
- [Limitación de la exposición de datos compartidos y aplicación de directivas de colaboración](best-practices.md#limit-exposure-of-shared-data-and-enforce-collaboration-policies)
- [Uso de la traza de auditoría de actividades para investigaciones forenses](best-practices.md#use-the-audit-trail-of-activities-for-forensic-investigations)

## <a name="control-box-with-built-in-policies-and-policy-templates"></a>Cuadro de control con directivas integradas y plantillas de Directiva

Puede usar las siguientes plantillas de directiva integradas para detectar y notificar las posibles amenazas:

| Tipo | Nombre |
| ---- | ---- |
| Directiva de detección de anomalías integrada | [Actividad desde una dirección IP anónima](anomaly-detection-policy.md#activity-from-anonymous-ip-addresses)<br />[Actividad desde un país poco frecuente](anomaly-detection-policy.md#activity-from-infrequent-country)<br />[Actividad desde direcciones IP sospechosas](anomaly-detection-policy.md#activity-from-suspicious-ip-addresses)<br />[Viaje imposible](anomaly-detection-policy.md#impossible-travel)<br />[Actividad realizada por el usuario Terminado](anomaly-detection-policy.md#activity-performed-by-terminated-user) (requiere AAD como IDP)<br />[Detección de malware](anomaly-detection-policy.md#malware-detection)<br />[Varios intentos incorrectos de inicio de sesión](anomaly-detection-policy.md#multiple-failed-login-attempts)<br />[Detección de ransomware](anomaly-detection-policy.md#ransomware-activity)<br />[Actividades administrativas poco habituales](anomaly-detection-policy.md#unusual-activities-by-user)<br />[Actividades inusuales de eliminación de archivos](anomaly-detection-policy.md#unusual-activities-by-user)<br />[Actividades inusuales de uso compartido de archivos](anomaly-detection-policy.md#unusual-activities-by-user)<br />[Varias actividades de descarga de archivos poco habituales](anomaly-detection-policy.md#unusual-activities-by-user) |
| Plantilla de directiva de actividad | Inicio de sesión desde una dirección IP de riesgo<br />Descarga masiva de un solo usuario<br />Actividad potencial de ransomware |
| Plantilla de directiva de archivo | Detección de un archivo compartido con un dominio no autorizado<br />Detección de un archivo compartido con direcciones de correo electrónico personales<br />Detección de archivos con PII/PCI/PHI |

Para obtener más información sobre la creación de directivas, vea [crear una directiva](control-cloud-apps-with-policies.md#create-a-policy).

## <a name="automate-governance-controls"></a>Automatizar los controles de gobierno

Además de supervisar posibles amenazas, puede aplicar y automatizar las siguientes acciones de gobierno de Box para corregir las amenazas detectadas:

| Tipo | Acción |
| ---- | ---- |
| Gobernanza de datos | -Aplicar etiqueta de clasificación de Azure Information Protection<br />-Cambiar el nivel de acceso de los vínculos compartidos<br />-Poner el archivo en cuarentena de administrador<br />-Poner el archivo en cuarentena de usuario<br />-Quitar un colaborador de un archivo<br />-Quitar Azure Information Protection etiqueta de clasificación<br />-Quitar vínculos compartidos directos<br />-Quitar colaboradores externos<br />-Enviar el Resumen de infracciones de DLP a los propietarios de archivos<br />-Enviar síntesis de infracción al último editor de archivos<br />-Establecer fecha de expiración en un vínculo compartido<br /> -Archivo de papelera |
| Regulación de usuario | -Suspender usuario<br />-Notificar al usuario sobre la alerta (a través de Azure AD)<br />-Requerir al usuario que inicie sesión de nuevo (a través de Azure AD)<br />-Suspender usuario (a través de Azure AD) |

Para obtener más información acerca de cómo corregir amenazas de aplicaciones, consulte [control de aplicaciones conectadas](governance-actions.md).

## <a name="protect-box-in-real-time"></a>Proteger el cuadro en tiempo real

Revise nuestras prácticas recomendadas para [proteger y colaborar con usuarios externos](best-practices.md#secure-collaboration-with-external-users-by-enforcing-real-time-session-controls) y [bloquear y proteger la descarga de datos confidenciales en dispositivos no administrados o de riesgo](best-practices.md#block-and-protect-download-of-sensitive-data-to-unmanaged-or-risky-devices).

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Cómo conectar Box a Microsoft Cloud App Security](connect-box-to-microsoft-cloud-app-security.md)
