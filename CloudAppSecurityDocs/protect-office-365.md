---
title: Cómo Cloud App Security ayuda a proteger el entorno de Office 365
description: En este artículo se proporciona información sobre las ventajas de conectar la aplicación Office 365 a Cloud App Security mediante el conector de API para la visibilidad y el control del uso.
author: shsagir
ms.author: shsagir
ms.service: cloud-app-security
ms.topic: article
ms.date: 12/04/2019
ms.collection: M365-security-compliance
ms.openlocfilehash: e0fb859ee6036340c75d6062f1c62a9ad4a76840
ms.sourcegitcommit: 9fe879ce7f07933866191724de5f108f43e3f923
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/24/2020
ms.locfileid: "77566897"
---
# <a name="how-cloud-app-security-helps-protect-your-office-365-environment"></a>Cómo Cloud App Security ayuda a proteger el entorno de Office 365

*Se aplica a: Microsoft Cloud App Security*

Como un importante conjunto de productividad que proporciona herramientas de almacenamiento, colaboración, BI y almacenamiento de archivos en la nube, Office 365 permite a los usuarios compartir sus documentos entre su organización y los asociados de una manera simplificada y eficaz. El uso de Office 365 puede exponer los datos confidenciales no solo internamente, sino también a colaboradores externos, o incluso peor hacer que esté disponible públicamente a través de un vínculo compartido. Estos incidentes pueden producirse debido a un actor malintencionado o a un empleado no compatible. Office 365 también proporciona un sistema de eco de aplicaciones de terceros de gran tamaño para ayudar a mejorar la productividad. El uso de estas aplicaciones puede exponer su organización al riesgo de aplicaciones malintencionadas o el uso de aplicaciones con permisos excesivos.

La conexión de Office 365 a Cloud App Security le proporciona información más detallada sobre las actividades de los usuarios, proporciona detección de amenazas mediante detecciones de anomalías basadas en aprendizaje automático, detecciones de protección de la información (como la detección de uso compartido de información externo). ), habilita los controles de corrección automatizados y detecta amenazas de aplicaciones de terceros habilitadas en su organización.

El uso del conector de Office 365 proporciona protección para los siguientes productos:

- Office 365
- Dynamics 365 CRM
- Exchange
- OneDrive
- Power BI
- SharePoint
- Equipos

## <a name="main-threats"></a>Amenazas principales

- Cuentas en peligro e Insider amenazas
- Fuga de datos
- Reconocimiento de seguridad insuficiente
- Aplicaciones malintencionadas de terceros
- Malware
- Suplantación de identidad (phishing)
- Ransomware
- No administrada traiga su propio dispositivo (BYOD)

## <a name="how-cloud-app-security-helps-to-protect-your-environment"></a>Cómo Cloud App Security ayuda a proteger su entorno

- [Detección de amenazas en la nube, cuentas en peligro e Insiders malintencionados](best-practices.md#detect-cloud-threats-compromised-accounts-malicious-insiders-and-ransomware)
- [Detectar, clasificar, etiquetar y proteger la información regulada y confidencial almacenada en la nube](best-practices.md#discover-classify-label-and-protect-regulated-and-sensitive-data-stored-in-the-cloud)
- [Detección y administración de aplicaciones de OAuth que tienen acceso a su entorno](manage-app-permissions.md)
- [Aplicación de directivas de cumplimiento y DLP para los datos almacenados en la nube](best-practices.md#enforce-dlp-and-compliance-policies-for-data-stored-in-the-cloud)
- [Limitar la exposición de los datos compartidos y aplicar directivas de colaboración](best-practices.md#limit-exposure-of-shared-data-and-enforce-collaboration-policies)
- [Usar la traza de auditoría de actividades para investigaciones forenses](best-practices.md#use-the-audit-trail-of-activities-for-forensic-investigations)

## <a name="control-office-365-with-built-in-policies-and-policy-templates"></a>Controlar Office 365 con directivas integradas y plantillas de Directiva

Puede usar las siguientes plantillas de directiva integradas para detectar y notificar las posibles amenazas:

| Tipo | Name |
| ---- | ---- |
| Directiva de detección de anomalías integrada | [Actividad desde direcciones IP anónimas](anomaly-detection-policy.md#activity-from-anonymous-ip-addresses)<br />[Actividad de un país poco frecuente](anomaly-detection-policy.md#activity-from-infrequent-country)<br />[Actividad desde direcciones IP sospechosas](anomaly-detection-policy.md#activity-from-suspicious-ip-addresses)<br />[Viaje imposible](anomaly-detection-policy.md#impossible-travel)<br />[Actividad realizada por el usuario Terminado](anomaly-detection-policy.md#activity-performed-by-terminated-user) (requiere AAD como IDP)<br />[Detección de malware](anomaly-detection-policy.md#malware-detection)<br />[Varios intentos de inicio de sesión erróneos](anomaly-detection-policy.md#multiple-failed-login-attempts)<br />[Detección de ransomware](anomaly-detection-policy.md#ransomware-activity)<br />[Actividad de eliminación de correos electrónicos sospechosos (versión preliminar)](anomaly-detection-policy.md#suspicious-email-deletion-activity-preview)<br />[Actividades de eliminación de archivo inusual](anomaly-detection-policy.md#unusual-activities-by-user) de [reenvío de bandeja de entrada sospechosa](anomaly-detection-policy.md#suspicious-inbox-forwarding)<br />[Actividades de recurso compartido de archivos inusuales](anomaly-detection-policy.md#unusual-activities-by-user)<br />[Actividades de descarga de varios archivos inusuales](anomaly-detection-policy.md#unusual-activities-by-user) |
| Plantilla de directiva de actividad | Inicio de sesión desde una dirección IP de riesgo<br />Descarga masiva por parte de un solo usuario<br />Posible actividad de ransomware |
| Plantilla de directiva de archivo | Detección de un archivo compartido con un dominio no autorizado<br />Detección de un archivo compartido con direcciones de correo electrónico personales<br />Detección de archivos con PII/PCI/PHI |
| Directiva de detección de anomalías de aplicación de OAuth | [Nombre de aplicación OAuth engañoso](app-permission-policy.md#oauth-app-anomaly-detection-policies)<br />[Nombre de publicador engañoso para una aplicación de OAuth](app-permission-policy.md#oauth-app-anomaly-detection-policies)<br />[Consentimiento de aplicación de OAuth malintencionado](anomaly-detection-policy.md#unusual-activities-by-user) |

Para obtener más información sobre la creación de directivas, vea [crear una directiva](control-cloud-apps-with-policies.md#create-a-policy).

## <a name="automate-governance-controls"></a>Automatizar los controles de gobierno

Además de supervisar posibles amenazas, puede aplicar y automatizar las siguientes acciones de gobierno de Office 365 para corregir las amenazas detectadas:

| Tipo | Acción |
| ---- | ---- |
| Regulación de datos | **OneDrive**<br /> -Heredar permisos de carpeta principal<br /> -Convertir en privada el archivo o la carpeta<br /> -Poner archivo o carpeta en cuarentena de administrador<br /> -Poner el archivo o la carpeta en la cuarentena de usuario<br /> -Archivo o carpeta de la papelera<br /> -Quitar un colaborador específico<br /> -Quitar colaboradores externos en archivo o carpeta<br /> -Aplicar etiqueta de clasificación de Azure Information Protection<br /> -Quitar Azure Information Protection etiqueta de clasificación<br /> **SharePoint**<br /> -Heredar permisos de carpeta principal<br /> -Convertir en privada el archivo o la carpeta<br /> -Poner archivo o carpeta en cuarentena de administrador<br /> -Poner el archivo o la carpeta en la cuarentena de usuario<br /> -Colocar archivo o carpeta en cuarentena de usuario y agregar permisos de propietario<br /> -Archivo o carpeta de la papelera<br /> -Quitar colaboradores externos en archivo o carpeta<br /> -Quitar un colaborador específico<br /> -Aplicar etiqueta de clasificación de Azure Information Protection<br /> -Quitar Azure Information Protection etiqueta de clasificación |
| Regulación de usuario | -Notificar al usuario sobre la alerta (a través de Azure AD)<br /> -Requerir al usuario que inicie sesión de nuevo (a través de Azure AD)<br /> -Suspender usuario (a través de Azure AD) |
| Control de aplicaciones de OAuth | -Revocar permiso de aplicación de OAuth |

Para obtener más información acerca de cómo corregir amenazas de aplicaciones, consulte [control de aplicaciones conectadas](governance-actions.md).

## <a name="protect-office-365-in-real-time"></a>Protección de Office 365 en tiempo real

Revise nuestras prácticas recomendadas para [proteger y colaborar con usuarios externos](best-practices.md#secure-collaboration-with-external-users-by-enforcing-real-time-session-controls) y [bloquear y proteger la descarga de datos confidenciales en dispositivos no administrados o de riesgo](best-practices.md#block-and-protect-download-of-sensitive-data-to-unmanaged-or-risky-devices).

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Cómo conectar Office 365 a Microsoft Cloud App Security](connect-office-365-to-microsoft-cloud-app-security.md)
