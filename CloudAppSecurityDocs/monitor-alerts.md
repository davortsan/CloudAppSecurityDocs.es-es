---
title: Supervisar alertas | Microsoft Docs
description: "En este tema se proporciona una lista y una descripción de todas las alertas."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 11/26/2016
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: f118a3bf-1663-46ba-884f-b1b03a84ab66
ms.reviewer: reutam
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 9565d8a51e4c06963861d9dfaef9595944bda1ff
ms.openlocfilehash: ee4b4e7a43603654eb415ff225a4ae3d8b139383


---

# <a name="monitor-alerts"></a>Supervisar alertas
Para ver alertas:

En el portal de Cloud App Security, haga clic en Alertas.


![Menú Alertas](./media/alert-menu.png)


Se mostrarán los siguientes tipos de alertas. 

## <a name="built-in-alerts"></a>Alertas integradas

|Nombre de alerta|Id. de alerta|Descripción|
|----|----|----|
|Nueva ubicación|ALERT_GEOLOCATION_NEW_COUNTRY|Se ha detectado una nueva ubicación desde que comenzó el examen (hasta 6 meses). Solo se muestra una vez para cada país para toda la organización. |
|Nuevo usuario administrador|ALERT_ADMIN_USER|Se ha detectado un nuevo administrador en una aplicación específica. Puede tratarse de una persona que es un administrador de una aplicación y ahora es un administrador de otra aplicación. Esta alerta está relacionada con el tipo de administrador específico, por lo que se mostrará cada vez que cambie el tipo de administrador. Si un usuario había perdido los privilegios de administrador y los ha recuperado, se mostrará esta alerta.|
|Cuenta inactiva|ALERT_ZOMBIE_USER|Si un usuario está inactivo durante 60 días por aplicación (por ejemplo, si alguien está activo en Box pero no ha tocado Google Apps durante 60 días), el usuario se considerará inactivo en Google Apps. Se agrega una etiqueta a estos usuarios, por lo que se pueden buscar cuentas inactivas.|
|Ubicación de administrador inesperada|ALERT_NEW_ADMIN_LOCATION|Se ha detectado una nueva ubicación de los administradores desde que comenzó el examen (hasta 6 meses). Solo se muestra una vez para cada país para cualquier administrador de la organización. |
|Cuenta en peligro|ALERT_COMPROMISED_ACCOUNT|Si se ha producido una infracción en una aplicación y se publica la lista de cuentas que se han infringido, Cloud App Security descarga la lista y la compara con la lista de usuarios, incluidos los usuarios internos, los usuarios externos y las cuentas personales. |

## <a name="custom-alerts"></a>Alertas personalizadas

|Nombre de alerta|Id. de alerta|Descripción|
|----|----|----|
|Alerta de actividad sospechosa|ALERT_SUSPICIOUS_ACTIVITY|Las actividades sospechosas se puntúan según lo sospechosa que sea la actividad anómala (¿hay una cuenta inactiva implicada?, ¿se produce desde una nueva ubicación?). Todos estos criterios se calculan juntos para proporcionar una puntuación de riesgo en función de los siguientes factores de riesgo: <br>El usuario es un administrador <br>Usuario estrictamente remoto<br>Proxy anónimo<br> Todos los inicios de sesión son erróneos<br>Numerosos inicios de sesión fallidos<br>Nuevo (administrador)<br>IP/ISP/país/agente de usuario para usuario/inquilino<br> IP/ISP/país/agente de usuario usado solo por el usuario (administrador)<br>Primera actividad de usuario (administrador) tras un tiempo<br>Primera vez que se realiza esta actividad administrativa tras un tiempo<br>Esta actividad administrativa no es común o no se había realizado nunca<br>Esta dirección IP solo tuvo inicios de sesión erróneos en el pasado<br>Viaje imposible|
|Alerta de uso sospechoso de la nube|ALERT_DISCOVERY_ANOMALY_DETECTION|La detección de anomalías de Cloud Discovery comprueba el patrón de comportamiento normal y busca los usuarios o las aplicaciones que se usan de manera inusual. |
|Infracción de directiva de actividad|ALERT_CABINET_EVENT_MATCH_AUDIT|Esta alerta le informa cuando se detecta una coincidencia de directiva.|
|Infracción de directiva de archivo|ALERT_CABINET_EVENT_MATCH_FILE|Esta alerta le informa cuando se detecta una coincidencia de directiva.|
|Infracción de directiva de proxy|ALERT_CABINET_INLINE_EVENT_MATCH|Esta alerta le informa cuando se detecta una coincidencia de directiva.|
|Infracción de directiva de campo|ALERT_CABINET_EVENT_MATCH_OBJECT|Esta alerta le informa cuando se detecta una coincidencia de directiva.|
|Nuevo servicio detectado|ALERT_CABINET_DISCOVERY_NEW_SERVICE|Se ha detectado una nueva aplicación.|
|Uso de cuenta personal|ALERT_PERSONAL_USER_SAGE|El motor de detección busca cuentas personales en función de los recursos compartidos de archivos y los nombres de usuario. |

## <a name="see-also"></a>Consulte también  
[Actividades diarias para proteger el entorno de nube](daily-activities-to-protect-your-cloud-environment.md)   
[Para obtener soporte técnico, visite la página de soporte técnico asistido de Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Los clientes Premier también pueden elegir Cloud App Security directamente desde el Portal Premier.](https://premier.microsoft.com/)  
  
  


<!--HONumber=Nov16_HO5-->


