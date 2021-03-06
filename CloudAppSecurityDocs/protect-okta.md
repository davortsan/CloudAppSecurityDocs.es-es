---
title: Cómo Cloud App Security ayuda a proteger su entorno de Okta
description: En este artículo se proporciona información sobre las ventajas de conectar la aplicación Okta a Cloud App Security mediante el conector de API para la visibilidad y el control del uso.
ms.date: 12/04/2019
ms.topic: article
ms.openlocfilehash: aac67b4c39f95ffea36ac20a4cd0c10abb0054c3
ms.sourcegitcommit: d87372b47ca98e942c2bf94032a6a61902627d69
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/30/2020
ms.locfileid: "96315215"
---
# <a name="how-cloud-app-security-helps-protect-your-okta-environment"></a>Cómo Cloud App Security ayuda a proteger su entorno de Okta

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Como solución de administración de identidades y acceso, Okta contiene las claves para la mayoría de los servicios críticos para la empresa. Okta administra los procesos de autenticación y autorización de los usuarios y clientes. Cualquier abuso de Okta por un actor malintencionado o cualquier error humano puede exponer los recursos y servicios más importantes a posibles ataques.

La conexión de Okta a Cloud App Security proporciona información más detallada sobre las actividades de administración de Okta, los usuarios administrados y los SIGH de clientes, y proporciona detección de amenazas para un comportamiento anómalo.

## <a name="main-threats"></a>Amenazas principales

- Cuentas en peligro e Insider amenazas

## <a name="how-cloud-app-security-helps-to-protect-your-environment"></a>Cómo Cloud App Security ayuda a proteger su entorno

- [Detección de amenazas en la nube, cuentas en peligro e Insiders malintencionados](best-practices.md#detect-cloud-threats-compromised-accounts-malicious-insiders-and-ransomware)
- [Uso de la traza de auditoría de actividades para investigaciones forenses](best-practices.md#use-the-audit-trail-of-activities-for-forensic-investigations)

## <a name="control-okta-with-built-in-policies-and-policy-templates"></a>Control de Okta con directivas integradas y plantillas de Directiva

Puede usar las siguientes plantillas de directiva integradas para detectar y notificar las posibles amenazas:

| Tipo | Nombre |
| ---- | ---- |
| Directiva de detección de anomalías integrada | [Actividad desde una dirección IP anónima](anomaly-detection-policy.md#activity-from-anonymous-ip-addresses)<br />[Actividad desde un país poco frecuente](anomaly-detection-policy.md#activity-from-infrequent-country)<br />[Actividad desde direcciones IP sospechosas](anomaly-detection-policy.md#activity-from-suspicious-ip-addresses)<br />[Viaje imposible](anomaly-detection-policy.md#impossible-travel)<br />[Varios intentos incorrectos de inicio de sesión](anomaly-detection-policy.md#multiple-failed-login-attempts)<br />[Detección de ransomware](anomaly-detection-policy.md#ransomware-activity)<br />[Actividades administrativas poco habituales](anomaly-detection-policy.md#unusual-activities-by-user) |
| Plantilla de directiva de actividad | Inicio de sesión desde una dirección IP de riesgo |

Para obtener más información sobre la creación de directivas, vea [crear una directiva](control-cloud-apps-with-policies.md#create-a-policy).

## <a name="automate-governance-controls"></a>Automatizar los controles de gobierno

Actualmente no hay ningún control de gobierno disponible para Okta. Si está interesado en tener acciones de gobierno para este conector, puede [enviar la Cloud App Security comentarios del equipo](support-and-ts.md#feedback) con los detalles de las acciones que desea.

Para obtener más información acerca de cómo corregir amenazas de aplicaciones, consulte [control de aplicaciones conectadas](governance-actions.md).

## <a name="protect-okta-in-real-time"></a>Protección de Okta en tiempo real

Revise nuestras prácticas recomendadas para [proteger y colaborar con usuarios externos](best-practices.md#secure-collaboration-with-external-users-by-enforcing-real-time-session-controls) y [bloquear y proteger la descarga de datos confidenciales en dispositivos no administrados o de riesgo](best-practices.md#block-and-protect-download-of-sensitive-data-to-unmanaged-or-risky-devices).

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Cómo conectar Okta a Microsoft Cloud App Security](connect-okta-to-microsoft-cloud-app-security.md)
