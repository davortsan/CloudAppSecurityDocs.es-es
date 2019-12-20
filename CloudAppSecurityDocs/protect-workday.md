---
title: Cómo Cloud App Security ayuda a proteger su entorno de WorkDay
description: En este artículo se proporciona información sobre las ventajas de conectar la aplicación WorkDay a Cloud App Security mediante el conector de API para la visibilidad y el control del uso.
author: shsagir
ms.author: shsagir
ms.service: cloud-app-security
ms.topic: article
ms.date: 12/04/2019
ms.collection: M365-security-compliance
ms.openlocfilehash: 9a08b00cabaa7829663d391073a9a4935efdee58
ms.sourcegitcommit: db5ec79d219dd6674939c872ace7cd2ca80860a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/19/2019
ms.locfileid: "75190035"
---
# <a name="how-cloud-app-security-helps-protect-your-workday-environment"></a>Cómo Cloud App Security ayuda a proteger su entorno de WorkDay

*Se aplica a: Microsoft Cloud App Security*

Como solución principal de HCM, WorkDay contiene parte de la información más confidencial de su organización, como los datos personales de los empleados, los contratos, los detalles del proveedor, etc. La prevención de la exposición de estos datos requiere una supervisión continua para evitar que cualquier acto malintencionado o un Insider no compatible con la seguridad extraer la información confidencial.

La conexión de WorkDay a Cloud App Security le proporciona información más detallada sobre las actividades de los usuarios y proporciona detección de amenazas para un comportamiento anómalo.

## <a name="main-threats"></a>Amenazas principales

- Cuentas en peligro e Insider amenazas
- Fuga de datos
- Reconocimiento de seguridad insuficiente
- No administrada traiga su propio dispositivo (BYOD)

## <a name="how-cloud-app-security-helps-to-protect-your-environment"></a>Cómo Cloud App Security ayuda a proteger su entorno

- [Detección de amenazas en la nube, cuentas en peligro e Insiders malintencionados](best-practices.md#detect-cloud-threats-compromised-accounts-malicious-insiders-and-ransomware)
- [Usar la traza de auditoría de actividades para investigaciones forenses](best-practices.md#use-the-audit-trail-of-activities-for-forensic-investigations)

## <a name="control-workday-with-built-in-policies-and-policy-templates"></a>Control de WorkDay con directivas integradas y plantillas de Directiva

Puede usar las siguientes plantillas de directiva integradas para detectar y notificar las posibles amenazas:

| Tipo | Name |
| ---- | ---- |
| Plantilla de directiva de actividad | Inicio de sesión desde una dirección IP de riesgo |

Para obtener más información sobre la creación de directivas, vea [crear una directiva](control-cloud-apps-with-policies.md#create-a-policy).

## <a name="automate-governance-controls"></a>Automatizar los controles de gobierno

Actualmente no hay ningún control de gobierno disponible para WorkDay. Si está interesado en tener acciones de gobierno para este conector, puede [enviar la Cloud App Security comentarios del equipo](support-and-ts.md#feedback) con los detalles de las acciones que desea.

Para obtener más información acerca de cómo corregir amenazas de aplicaciones, consulte [control de aplicaciones conectadas](governance-actions.md).

## <a name="protect-workday-in-real-time"></a>Protección de WorkDay en tiempo real

Revise nuestras prácticas recomendadas para [proteger y colaborar con usuarios externos](best-practices.md#secure-collaboration-with-external-users-by-enforcing-real-time-session-controls) y [bloquear y proteger la descarga de datos confidenciales en dispositivos no administrados o de riesgo](best-practices.md#block-and-protect-download-of-sensitive-data-to-unmanaged-or-risky-devices).

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Cómo conectar WorkDay a Microsoft Cloud App Security](connect-workday-to-microsoft-cloud-app-security.md)
