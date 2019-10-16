---
title: Supervisión de alertas generadas en Cloud App Security
description: En este artículo se proporcionan una lista y una descripción de todas las alertas.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 12/10/2018
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: f118a3bf-1663-46ba-884f-b1b03a84ab66
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 9e697d86bd7279e445a8fa40bf9fd5000081e469
ms.sourcegitcommit: c342abeec95359ddabdabcc3a081a0f91d52407c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72335904"
---
# <a name="monitor-alerts-in-cloud-app-security"></a>Supervisión de alertas en Cloud App Security

*Se aplica a: Microsoft Cloud App Security*

Las alertas son los puntos de entrada para comprender el entorno de nube en más profundidad. En este artículo se proporcionan una lista y una descripción de todas las alertas.

## <a name="monitoring-your-alerts"></a>Supervisión de las alertas

Revisar todas las alertas es una buena idea. Comprender por qué se produce una alerta le permite usarlas como herramientas para modificar las directivas. 

**Para ver las alertas:** En el portal de Microsoft Cloud App Security, haga clic en **alertas**.


![Menú Alertas](./media/alert-menu.png)

 - **Descarte** una alerta después de verla y determinar que no es interesante. 
     - Escriba un **comentario** para explicar por qué ha descartado la alerta. 
     - **Envíenos sus comentarios sobre esta alerta** para que nuestro equipo de investigación de seguridad la revise para mejorar las alertas.

- **Resuelva** la alerta si la ha investigado y ha mitigado el riesgo. 

     - La alerta ya no se mostrará en la tabla de alertas.
     - **Márquela como no leída** si ha empezado a investigar un problema, pero quiere asegurarse de que no se olvida de continuar trabajando en él. 
     -  **Ajuste la directiva** que coincidía con la alerta para mejorar las coincidencias de próximas alertas. 
     - Al resolver una alerta, puede escribir un comentario y **enviarlo al equipo de Cloud App Security**.
 
## <a name="built-in-alerts"></a>Alertas integradas

Se mostrarán los siguientes tipos de alertas. 

|Nombre de alerta|Id. de alerta|Descripción|
|----|----|----|
|Nueva ubicación|ALERT_GEOLOCATION_NEW_COUNTRY|Se ha detectado una nueva ubicación desde que comenzó el examen (hasta 6 meses). Esta alerta solo se muestra una vez para cada país para toda la organización. |
|Nuevo usuario administrador|ALERT_ADMIN_USER|Se ha detectado un nuevo administrador de una aplicación específica. Puede tratarse de una persona que es un administrador de una aplicación y ahora es un administrador de otra aplicación. Esta alerta está relacionada con el tipo de administrador específico, por lo que se mostrará cada vez que cambie el tipo de administrador. Si un usuario había perdido los privilegios de administrador y los ha recuperado, se mostrará esta alerta.|
|Cuenta inactiva|ALERT_ZOMBIE_USER|Si un usuario está inactivo durante 60 días por aplicación (por ejemplo, si alguien está activo en Box pero no ha tocado G Suite durante 60 días), el usuario se considerará inactivo en G Suite. Se agrega una etiqueta a estos usuarios, por lo que se pueden buscar cuentas inactivas.|
|Ubicación de administrador inesperada|ALERT_NEW_ADMIN_LOCATION|Se ha detectado una nueva ubicación de los administradores desde que comenzó el examen (hasta 6 meses). Esta alerta solo se muestra una vez para cada país para cualquier administrador de la organización. |
|Cuenta en peligro|ALERT_COMPROMISED_ACCOUNT|Si se ha producido una infracción en una aplicación y se publica la lista de cuentas que se han infringido, Cloud App Security descarga la lista y la compara con la lista de usuarios, incluidos los usuarios internos, los usuarios externos y las cuentas personales. |

## <a name="custom-alerts"></a>Alertas personalizadas

Se mostrarán los siguientes tipos de alertas. 

|Nombre de alerta|Id. de alerta|Descripción|
|----|----|----|
|Alerta de actividad sospechosa|ALERT_SUSPICIOUS_ACTIVITY|Las actividades sospechosas se puntúan según lo sospechosa que sea la actividad anómala (¿hay una cuenta inactiva implicada?, ¿Se trata de una nueva ubicación?) Estos criterios se calculan juntos para proporcionar una puntuación de riesgo en función de los siguientes factores de riesgo: <br>El usuario es un administrador <br>Usuario estrictamente remoto<br>Proxy anónimo<br> Todos los inicios de sesión son erróneos<br>Numerosos inicios de sesión fallidos<br>Nuevo (administrador)<br>IP/ISP/país/agente de usuario para usuario/inquilino<br> IP/ISP/país/agente de usuario usado solo por el usuario (administrador)<br>Primera actividad de usuario (administrador) tras un tiempo<br>Primera vez que se realiza esta actividad administrativa tras un tiempo<br>Esta actividad administrativa no es común o no se había realizado nunca<br>Esta dirección IP solo tuvo inicios de sesión erróneos en el pasado<br>Viaje imposible|
|Alerta de uso sospechoso de la nube|ALERT_DISCOVERY_ANOMALY_DETECTION|La detección de anomalías de Cloud Discovery comprueba el patrón de comportamiento normal y busca los usuarios o las aplicaciones que se usan de manera inusual. |
|Infracción de directiva de actividad|ALERT_CABINET_EVENT_MATCH_AUDIT|Esta alerta le informa cuando se detecta una coincidencia de directiva.|
|Infracción de directiva de archivo|ALERT_CABINET_EVENT_MATCH_FILE|Esta alerta le informa cuando se detecta una coincidencia de directiva.|
|Infracción de directiva de proxy|ALERT_CABINET_INLINE_EVENT_MATCH|Esta alerta le informa cuando se detecta una coincidencia de directiva.|
|Infracción de directiva de campo|ALERT_CABINET_EVENT_MATCH_OBJECT|Esta alerta le informa cuando se detecta una coincidencia de directiva.|
|Nuevo servicio detectado|ALERT_CABINET_DISCOVERY_NEW_SERVICE|Se ha detectado una nueva aplicación.|
|Uso de cuenta personal|ALERT_PERSONAL_USER_SAGE|El motor de detección busca cuentas personales en función de los recursos compartidos de archivos y los nombres de usuario. |

## <a name="next-steps"></a>Pasos siguientes 

[Actividades diarias para proteger el entorno de nube](daily-activities-to-protect-your-cloud-environment.md)

[Los clientes Premier también pueden crear una solicitud de soporte técnico directamente en el portal Premier.](https://premier.microsoft.com/)  
