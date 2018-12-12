---
title: Solución de problemas de la integración de SIEM con Cloud App Security | Microsoft Docs
description: En este artículo se proporciona una lista de posibles problemas al conectar su SIEM con Cloud App Security, así como soluciones para cada uno de ellos.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 12/9/2018
ms.topic: conceptual
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: de64d9ca-eaed-4243-bcf7-adca5aff18c8
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 9711115763babc9807d4761f62bde675b435a68d
ms.sourcegitcommit: c497253a7ab63973bb806607e5f15dece91640be
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/10/2018
ms.locfileid: "53124067"
---
# <a name="troubleshooting-the-siem-agent"></a>Solución de problemas del agente SIEM

*Se aplica a: Microsoft Cloud App Security*

En este artículo se proporciona una lista de posibles problemas al conectar su SIEM con Cloud App Security, así como posibles soluciones.

## <a name="troubleshooting"></a>Solucionar problemas

Asegúrese de que el estado del agente SIEM en el portal de Microsoft Cloud App Security no sea **Error de conexión** ni **Desconectado** y de que no haya ninguna notificación del agente. El estado se muestra como **Error de conexión** si la conexión está inactiva durante más de dos horas. El estado cambia a **Desconectado** si la conexión está inactiva durante más de 12 horas.

Si ve alguno de los errores siguientes en el símbolo del sistema mientras se ejecuta al agente, siga estos pasos para corregir el problema:

|Error|Descripción|Solución|
|----|----|----|
|Error general durante el arranque|Error inesperado durante el arranque del agente.|Póngase en contacto con el soporte técnico.|
|Demasiados errores críticos|Se han producido demasiados errores críticos al conectar la consola. Apagando el equipo.|Póngase en contacto con el soporte técnico.|
|Token no válido|El token proporcionado no es válido.|Asegúrese de que haya copiado el token adecuado. Puede usar el proceso anterior para volver a generar el token.|
|Dirección de proxy no válida|La dirección de proxy proporcionada no es válida.|Asegúrese de que haya escrito el proxy y el puerto correctos.|


Después de crear el agente, consulte la página del agente SIEM en el portal de Cloud App Security. Si ve alguna de las **Notificaciones del agente** siguientes, siga estos pasos para corregir el problema:

|Error|Descripción|Solución|
|----|----|----|
|**Error interno**|Se ha producido un problema desconocido con el agente SIEM.|Póngase en contacto con el soporte técnico.|
|**Error en el envío al servidor de datos**|Este error puede aparecer si está trabajando con un servidor de Syslog sobre TCP. El agente SIEM no puede conectarse a su servidor de Syslog.  Si se le muestra este error, el agente dejará de extraer nuevas actividades hasta que se solucione. Debe seguir los pasos de corrección indicados hasta que el error deje de aparecer.|1. También es necesario haber definido correctamente el servidor de Syslog: en la UI de Cloud App Security, edite el agente SIEM como se ha descrito anteriormente. Compruebe que haya escrito correctamente el nombre del servidor y establecido el puerto correcto. </br>2. Compruebe la conectividad con el servidor de Syslog: asegúrese de que el firewall no esté bloqueando la comunicación.| 
|**Error en la conexión al servidor de datos**| Este error puede aparecer si está trabajando con un servidor de Syslog sobre TCP. El agente SIEM no puede conectarse a su servidor de Syslog.  Si se le muestra este error, el agente dejará de extraer nuevas actividades hasta que se solucione. Debe seguir los pasos de corrección indicados hasta que el error deje de aparecer.|1. También es necesario haber definido correctamente el servidor de Syslog: en la UI de Cloud App Security, edite el agente SIEM como se ha descrito anteriormente. Compruebe que haya escrito correctamente el nombre del servidor y establecido el puerto correcto. </br>2. Compruebe la conectividad con el servidor de Syslog: asegúrese de que el firewall no esté bloqueando la comunicación.|
|**Error del agente SIEM**|El agente SIEM ha estado desconectado durante más de X horas.|Asegúrese de que no ha cambiado la configuración de SIEM en el portal de Cloud App Security. De lo contrario, este error podría indicar problemas de conectividad entre Cloud App Security y el equipo en el que se ejecuta el agente SIEM.|
|**Error de notificación del agente SIEM**|Se han recibido errores de reenvío de notificación de agente SIEM procedentes de un agente SIEM.|Este error indica que ha recibido errores relacionados con la conexión entre el agente SIEM y el servidor SIEM. Asegúrese de que no hay ningún firewall que bloquee el servidor SIEM o el equipo en el que se ejecuta el agente SIEM. Compruebe también que la dirección IP del servidor SIEM no ha cambiado.|


## <a name="next-steps"></a>Pasos siguientes
  
[Actividades diarias para proteger el entorno de nube](daily-activities-to-protect-your-cloud-environment.md)   

[Los clientes Premier también pueden crear una solicitud de soporte técnico directamente en el portal Premier.](https://premier.microsoft.com/)  
  
