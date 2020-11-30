---
title: Cómo Cloud App Security ayuda a proteger su entorno de Amazon Web Services
description: En este artículo se proporciona información sobre las ventajas de conectar la aplicación AWS a Cloud App Security mediante el conector de API para la visibilidad y el control del uso.
ms.date: 09/15/2020
ms.topic: article
ms.openlocfilehash: 79c13b4102b69442355071f34a7b36aede1c344b
ms.sourcegitcommit: d87372b47ca98e942c2bf94032a6a61902627d69
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/30/2020
ms.locfileid: "96315317"
---
# <a name="how-cloud-app-security-helps-protect-your-amazon-web-services-aws-environment"></a>Cómo Cloud App Security ayuda a proteger el entorno de Amazon Web Services (AWS)

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Amazon Web Services es un proveedor de IaaS que permite a su organización hospedar y administrar sus cargas de trabajo completas en la nube. Junto con las ventajas de aprovechar la infraestructura en la nube, los activos más críticos de su organización pueden estar expuestos a las amenazas. Los recursos expuestos incluyen instancias de almacenamiento con información potencialmente confidencial, recursos de proceso que operan algunas de las aplicaciones, puertos y redes privadas virtuales más importantes que permiten el acceso a su organización.

La conexión de AWS a Cloud App Security le ayuda a proteger sus activos y detectar posibles amenazas mediante la supervisión de las actividades administrativas e inicios de sesión, notificando posibles ataques por fuerza bruta, uso malintencionado de una cuenta de usuario con privilegios, eliminaciones inusuales de máquinas virtuales y cubos de almacenamiento expuestos públicamente.

## <a name="main-threats"></a>Amenazas principales

- Abuso de recursos en la nube
- Cuentas en peligro e Insider amenazas
- Pérdida de datos
- Configuración inadecuada de recursos y control de acceso insuficiente

## <a name="how-cloud-app-security-helps-to-protect-your-environment"></a>Cómo Cloud App Security ayuda a proteger su entorno

- [Detección de amenazas en la nube, cuentas en peligro e Insiders malintencionados](best-practices.md#detect-cloud-threats-compromised-accounts-malicious-insiders-and-ransomware)
- [Limitación de la exposición de datos compartidos y aplicación de directivas de colaboración](best-practices.md#limit-exposure-of-shared-data-and-enforce-collaboration-policies)
- [Manténgase al día con la recomendación de configuración de seguridad más reciente](security-config-aws.md)
- [Uso de la traza de auditoría de actividades para investigaciones forenses](best-practices.md#use-the-audit-trail-of-activities-for-forensic-investigations)
- [Revisar recomendaciones de configuración de seguridad](security-config-aws.md)

## <a name="control-aws-with-built-in-policies-and-policy-templates"></a>Control de AWS con directivas integradas y plantillas de Directiva

Puede usar las siguientes plantillas de directiva integradas para detectar y notificar las posibles amenazas:

| Tipo | Nombre |
| ---- | ---- |
| Plantilla de directiva de actividad | Errores de inicio de sesión en la consola de administración<br />Cambios de configuración de CloudTrail<br />Cambios de configuración de la instancia de EC2<br />Cambios en la Directiva IAM<br />Inicio de sesión desde una dirección IP de riesgo<br />Cambios en la lista de control de acceso (ACL) de red<br />Cambios de puerta de enlace de red<br />Cambios de configuración de S3<br />Cambios de configuración del grupo de seguridad<br />Cambios en la red privada virtual |
| Directiva de detección de anomalías integrada | [Actividad desde una dirección IP anónima](anomaly-detection-policy.md#activity-from-anonymous-ip-addresses)<br />[Actividad desde un país poco frecuente](anomaly-detection-policy.md#activity-from-infrequent-country)<br />[Actividad desde direcciones IP sospechosas](anomaly-detection-policy.md#activity-from-suspicious-ip-addresses)<br />[Viaje imposible](anomaly-detection-policy.md#impossible-travel)<br />[Actividad realizada por el usuario Terminado](anomaly-detection-policy.md#activity-performed-by-terminated-user) (requiere AAD como IDP)<br />[Varios intentos incorrectos de inicio de sesión](anomaly-detection-policy.md#multiple-failed-login-attempts)<br />[Actividades administrativas poco habituales](anomaly-detection-policy.md#unusual-activities-by-user)<br />[Actividades inusuales de eliminación de almacenamiento múltiple](anomaly-detection-policy.md#unusual-activities-by-user) (versión preliminar)<br />[Varias actividades de eliminación de VM](anomaly-detection-policy.md#multiple-delete-vm-activities)<br />[Actividades de creación de varias máquinas virtuales inusuales](anomaly-detection-policy.md#unusual-activities-by-user) (versión preliminar)<br />[Región inusual para el recurso de nube](anomaly-detection-policy.md#unusual-activities-by-user) (versión preliminar) |
| Plantilla de directiva de archivo | El cubo S3 es accesible públicamente |

Para obtener más información sobre la creación de directivas, vea [crear una directiva](control-cloud-apps-with-policies.md#create-a-policy).

## <a name="automate-governance-controls"></a>Automatizar los controles de gobierno

Además de supervisar posibles amenazas, puede aplicar y automatizar las siguientes acciones de gobierno de AWS para corregir las amenazas detectadas:

| Tipo | Acción |
| ---- | ---- |
| Regulación de usuario | -Notificar al usuario sobre la alerta (a través de Azure AD)<br />-Requerir al usuario que inicie sesión de nuevo (a través de Azure AD)<br />-Suspender usuario (a través de Azure AD) |
| Gobernanza de datos | -Crear un cubo S3 privado<br />-Quitar un colaborador para un cubo S3 |

Para obtener más información acerca de cómo corregir amenazas de aplicaciones, consulte [control de aplicaciones conectadas](governance-actions.md).

## <a name="security-recommendations"></a>Recomendaciones de seguridad

Cloud App Security proporciona una visión general del cumplimiento de la configuración de la plataforma AWS para todas las cuentas de AWS basadas en el benchmark Center for Internet Security (CIS) para AWS.

Debe revisar continuamente las recomendaciones de seguridad para evaluar y evaluar el estado actual de la postura de seguridad de su plataforma e identificar los intervalos de configuración importantes. A continuación, debe crear un plan para mitigar los problemas en la plataforma AWS.

Para obtener más información, [recomendaciones de seguridad de AWS](security-config-aws.md).

## <a name="protect-aws-in-real-time"></a>Protección de AWS en tiempo real

Revise nuestras prácticas recomendadas para [bloquear y proteger la descarga de datos confidenciales en dispositivos no administrados o peligrosos](best-practices.md#block-and-protect-download-of-sensitive-data-to-unmanaged-or-risky-devices).

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Cómo conectar AWS con Microsoft Cloud App Security](connect-aws-to-microsoft-cloud-app-security.md)
