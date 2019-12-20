---
title: Cómo Cloud App Security ayuda a proteger su entorno de Google Cloud Platform
description: En este artículo se proporciona información sobre las ventajas de conectar la aplicación Google Cloud Platform a Cloud App Security mediante el conector de API para la visibilidad y el control del uso.
author: shsagir
ms.author: shsagir
ms.service: cloud-app-security
ms.topic: article
ms.date: 12/04/2019
ms.collection: M365-security-compliance
ms.openlocfilehash: de9a6d460725766dee348fdd91f8c12a9bfe5745
ms.sourcegitcommit: db5ec79d219dd6674939c872ace7cd2ca80860a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/19/2019
ms.locfileid: "75190085"
---
# <a name="how-cloud-app-security-helps-protect-your-google-cloud-platform-gcp-environment"></a>Cómo Cloud App Security ayuda a proteger el entorno de Google Cloud Platform (GCP)

*Se aplica a: Microsoft Cloud App Security*

Google Cloud Platform es un proveedor de IaaS que permite a su organización hospedar y administrar sus cargas de trabajo completas en la nube. Junto con las ventajas de aprovechar la infraestructura en la nube, los activos más críticos de su organización pueden estar expuestos a las amenazas. Los recursos expuestos incluyen instancias de almacenamiento con información potencialmente confidencial, recursos de proceso que operan algunas de las aplicaciones, puertos y redes privadas virtuales más importantes que permiten el acceso a su organización.

Conectar GCP a Cloud App Security le ayuda a proteger sus activos y detectar posibles amenazas mediante la supervisión de las actividades administrativas e inicios de sesión, notificando posibles ataques por fuerza bruta, uso malintencionado de una cuenta de usuario con privilegios y eliminaciones inusuales de Máquina.

## <a name="main-threats"></a>Amenazas principales

- Abuso de recursos en la nube
- Cuentas en peligro e Insider amenazas
- Fuga de datos
- Configuración inadecuada de recursos y control de acceso insuficiente

## <a name="how-cloud-app-security-helps-to-protect-your-environment"></a>Cómo Cloud App Security ayuda a proteger su entorno

- [Detección de amenazas en la nube, cuentas en peligro e Insiders malintencionados](best-practices.md#detect-cloud-threats-compromised-accounts-malicious-insiders-and-ransomware)
- [Usar la traza de auditoría de actividades para investigaciones forenses](best-practices.md#use-the-audit-trail-of-activities-for-forensic-investigations)

## <a name="control-gcp-with-built-in-policies-and-policy-templates"></a>Controlar GCP con directivas integradas y plantillas de Directiva

Puede usar las siguientes plantillas de directiva integradas para detectar y notificar las posibles amenazas:

| Tipo | Name |
| ---- | ---- |
| Directiva de detección de anomalías integrada | [Actividad desde direcciones IP anónimas](anomaly-detection-policy.md#activity-from-anonymous-ip-addresses)<br />[Actividad desde un país poco frecuente](anomaly-detection-policy.md#activity-from-infrequent-country)<br />[Actividad desde direcciones IP sospechosas](anomaly-detection-policy.md#activity-from-suspicious-ip-addresses)<br />[Viaje imposible](anomaly-detection-policy.md#impossible-travel)<br />[Actividad realizada por el usuario Terminado](anomaly-detection-policy.md#activity-performed-by-terminated-user) (requiere AAD como IDP)<br />[Varios intentos incorrectos de inicio de sesión](anomaly-detection-policy.md#multiple-failed-login-attempts)<br />[Actividades administrativas inusuales](anomaly-detection-policy.md#unusual-activities-by-user)<br />[Varias actividades de eliminación de VM](anomaly-detection-policy.md#multiple-delete-vm-activities)<br />[Actividades de creación de varias máquinas virtuales inusuales](anomaly-detection-policy.md#unusual-activities-by-user) (versión preliminar) |
| Plantilla de directiva de actividad | Cambios en los recursos del motor de proceso<br />Cambios en la configuración de StackDriver<br />Cambios en los recursos de almacenamiento<br />Cambios en la red privada virtual<br />Inicio de sesión desde una dirección IP de riesgo |

Para obtener más información sobre la creación de directivas, vea [crear una directiva](control-cloud-apps-with-policies.md#create-a-policy).

## <a name="automate-governance-controls"></a>Automatizar los controles de gobierno

Además de supervisar posibles amenazas, puede aplicar y automatizar las siguientes acciones de gobierno de GCP para corregir las amenazas detectadas:

| Tipo | Acción |
| ---- | ---- |
| Regulación del usuario | -Requerir al usuario que restablezca la contraseña en Google (requiere la instancia vinculada de G Suite)<br />-Suspender usuario (requiere la instancia vinculada de G Suite)<br />-Notificar al usuario sobre la alerta (a través de Azure AD)<br />-Requerir al usuario que inicie sesión de nuevo (a través de Azure AD)<br />-Suspender usuario (a través de Azure AD) |

Para obtener más información acerca de cómo corregir amenazas de aplicaciones, consulte [control de aplicaciones conectadas](governance-actions.md).

## <a name="protect-gcp-in-real-time"></a>Protección de GCP en tiempo real

Revise nuestras prácticas recomendadas para [proteger y colaborar con usuarios externos](best-practices.md#secure-collaboration-with-external-users-by-enforcing-real-time-session-controls) y [bloquear y proteger la descarga de datos confidenciales en dispositivos no administrados o de riesgo](best-practices.md#block-and-protect-download-of-sensitive-data-to-unmanaged-or-risky-devices).

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Cómo conectar GCP a Microsoft Cloud App Security](connect-google-gcp-to-microsoft-cloud-app-security.md)