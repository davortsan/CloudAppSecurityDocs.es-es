---
title: Cómo Cloud App Security ayuda a proteger su entorno de Azure
description: En este artículo se proporciona información sobre las ventajas de conectar la aplicación de Azure a Cloud App Security mediante el conector de API para la visibilidad y el control del uso.
ms.date: 09/15/2020
ms.topic: article
ms.openlocfilehash: 2eeaca28f55bd836774e0388923ddbdb1a40eadd
ms.sourcegitcommit: d87372b47ca98e942c2bf94032a6a61902627d69
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/30/2020
ms.locfileid: "96310897"
---
# <a name="how-cloud-app-security-helps-protect-your-azure-environment"></a>Cómo Cloud App Security ayuda a proteger su entorno de Azure

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Azure es un proveedor de IaaS que permite a su organización hospedar y administrar sus cargas de trabajo completas en la nube. Junto con las ventajas de aprovechar la infraestructura en la nube, los activos más críticos de su organización pueden estar expuestos a las amenazas. Los recursos expuestos incluyen instancias de almacenamiento con información potencialmente confidencial, recursos de proceso que operan algunas de las aplicaciones, puertos y redes privadas virtuales más importantes que permiten el acceso a su organización.

La conexión de Azure a Cloud App Security le ayuda a proteger sus activos y a detectar posibles amenazas mediante la supervisión de las actividades administrativas e inicios de sesión, la notificación de posibles ataques por fuerza bruta, el uso malintencionado de una cuenta de usuario con privilegios y la eliminación inusual de las máquinas virtuales.

## <a name="main-threats"></a>Amenazas principales

- Abuso de recursos en la nube
- Cuentas en peligro e Insider amenazas
- Pérdida de datos
- Configuración inadecuada de recursos y control de acceso insuficiente

## <a name="how-cloud-app-security-helps-to-protect-your-environment"></a>Cómo Cloud App Security ayuda a proteger su entorno

- [Detección de amenazas en la nube, cuentas en peligro e Insiders malintencionados](best-practices.md#detect-cloud-threats-compromised-accounts-malicious-insiders-and-ransomware)
- [Limitación de la exposición de datos compartidos y aplicación de directivas de colaboración](best-practices.md#limit-exposure-of-shared-data-and-enforce-collaboration-policies)
- [Uso de la traza de auditoría de actividades para investigaciones forenses](best-practices.md#use-the-audit-trail-of-activities-for-forensic-investigations)
- [Revisar recomendaciones de configuración de seguridad](security-config-azure.md)

## <a name="control-azure-with-built-in-policies-and-policy-templates"></a>Control de Azure con directivas integradas y plantillas de Directiva

Puede usar las siguientes plantillas de directiva integradas para detectar y notificar las posibles amenazas:

| Tipo | Nombre |
| ---- | ---- |
| Directiva de detección de anomalías integrada | [Actividad desde una dirección IP anónima](anomaly-detection-policy.md#activity-from-anonymous-ip-addresses)<br />[Actividad desde un país poco frecuente](anomaly-detection-policy.md#activity-from-infrequent-country)<br />[Actividad desde direcciones IP sospechosas](anomaly-detection-policy.md#activity-from-suspicious-ip-addresses)<br />[Actividad realizada por el usuario Terminado](anomaly-detection-policy.md#activity-performed-by-terminated-user) (requiere AAD como IDP)<br />[Varios intentos incorrectos de inicio de sesión](anomaly-detection-policy.md#multiple-failed-login-attempts)<br />[Actividades administrativas poco habituales](anomaly-detection-policy.md#unusual-activities-by-user)<br />[Actividades inusuales de eliminación de almacenamiento múltiple](anomaly-detection-policy.md#unusual-activities-by-user) (versión preliminar)<br />[Varias actividades de eliminación de VM](anomaly-detection-policy.md#multiple-delete-vm-activities)<br />[Actividades de creación de varias máquinas virtuales inusuales](anomaly-detection-policy.md#unusual-activities-by-user) (versión preliminar) |

Para obtener más información sobre la creación de directivas, vea [crear una directiva](control-cloud-apps-with-policies.md#create-a-policy).

## <a name="security-recommendations"></a>Recomendaciones de seguridad

Cloud App Security proporciona una vista de nivel de inquilino de la plataforma Azure, donde se enumeran las recomendaciones de seguridad de todas las suscripciones de Azure del inquilino. Puede usar recomendaciones de seguridad de Azure integradas para más de 100 recursos de Azure frente a la [prueba comparativa de seguridad de Azure](/azure/security/benchmarks/introduction), así como [recomendaciones personalizadas](/azure/security-center/custom-security-policies). Entre las recomendaciones preparadas se incluyen los siguientes tipos de recursos: máquinas virtuales, identidad y acceso, datos y almacenamiento, proceso y aplicaciones, redes, contenedores y servicios de aplicaciones.

Debe revisar continuamente las recomendaciones de seguridad para evaluar y evaluar el estado actual de la postura de seguridad de su plataforma e identificar los intervalos de configuración importantes. A continuación, debe crear un plan para mitigar los problemas de la plataforma Azure.

Para obtener más información, consulte la [Guía de recomendaciones de Azure](/azure/security-center/recommendations-reference) y las recomendaciones de seguridad de [Azure](security-config-azure.md).

## <a name="automate-governance-controls"></a>Automatizar los controles de gobierno

Además de supervisar posibles amenazas, puede aplicar y automatizar las siguientes acciones de gobierno de Azure para corregir las amenazas detectadas:

| Tipo | Acción |
| ---- | ---- |
| Regulación de usuario | -Notificar al usuario sobre la alerta (a través de Azure AD)<br />-Requerir al usuario que inicie sesión de nuevo (a través de Azure AD)<br />-Suspender usuario (a través de Azure AD) |

Para obtener más información acerca de cómo corregir amenazas de aplicaciones, consulte [control de aplicaciones conectadas](governance-actions.md).

## <a name="protect-azure-in-real-time"></a>Protección de Azure en tiempo real

Revise nuestras prácticas recomendadas para [proteger y colaborar con usuarios externos](best-practices.md#secure-collaboration-with-external-users-by-enforcing-real-time-session-controls) y [bloquear y proteger la descarga de datos confidenciales en dispositivos no administrados o de riesgo](best-practices.md#block-and-protect-download-of-sensitive-data-to-unmanaged-or-risky-devices).

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Cómo conectar Azure a Microsoft Cloud App Security](connect-azure-to-microsoft-cloud-app-security.md)
