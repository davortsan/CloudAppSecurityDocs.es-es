---
title: Solución de problemas de la integración de SIEM con Cloud App Security | Microsoft Docs
description: En este tema se proporciona una lista de posibles problemas al conectar su SIEM con Cloud App Security y soluciones para cada uno de ellos.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 4/22/2018
ms.topic: conceptual
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: de64d9ca-eaed-4243-bcf7-adca5aff18c8
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 175dbd52bcde0aba78fb8723cdddde19a2410f6a
ms.sourcegitcommit: 0ac08ca7b3140b79f1d36ff7152476c188fa12b3
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/07/2018
ms.locfileid: "44143605"
---
*Se aplica a: Microsoft Cloud App Security*


# <a name="troubleshooting-the-siem-agent"></a>Solución de problemas del agente SIEM

Asegúrese de que el estado del agente SIEM en el portal de Microsoft Cloud App Security no sea **Error de conexión** ni **Desconectado** y de que no haya ninguna notificación del agente. Verá **Error de conexión** si la conexión está inactiva durante más de dos horas y **Desconectado** si la conexión está inactiva durante más de 12 horas.

Si ve alguno de los errores siguientes en el símbolo del sistema mientras se ejecuta al agente, siga estos pasos para corregir el problema:

|Error|Descripción|Solución|
|----|----|----|
|Error general durante el arranque|Error inesperado durante el arranque del agente.|Póngase en contacto con el soporte técnico.|
|Demasiados errores críticos|Se han producido demasiados errores críticos al conectar la consola. Apagando el equipo.|Póngase en contacto con el soporte técnico.|
|Token no válido|El token proporcionado no es válido.|Asegúrese de que haya copiado el token adecuado. Puede usar el proceso anterior para volver a generar el token.|
|Dirección de proxy no válida|La dirección de proxy proporcionada no es válida.|Asegúrese de que haya escrito el proxy y el puerto correctos.|


Después de crear el agente, si ve una de las siguientes **Notificaciones de agente** en el portal de Cloud App Security en la página del agente SIEM, siga estos pasos para corregir el problema:

|Error|Descripción|Solución|
|----|----|----|
|**Error interno**|Se ha producido un problema desconocido con el agente SIEM.|Póngase en contacto con el soporte técnico.|
|**Error en el envío al servidor de datos**|Este error puede aparecer si está trabajando con un servidor de Syslog sobre TCP. El agente SIEM no puede conectarse a su servidor de Syslog.  Si recibe este error, el agente dejará de extraer nuevas actividades hasta que se corrija, por lo que debe asegurarse de seguir los pasos de corrección hasta que el error deje de aparecer.|1. Asegúrese de que se haya definido correctamente el servidor de Syslog: en la interfaz de Cloud App Security, edite el agente SIEM como se ha descrito anteriormente, asegúrese de que haya escrito correctamente el nombre del servidor y establezca el puerto correcto. </br>2. Compruebe la conectividad con el servidor de Syslog: asegúrese de que el firewall no esté bloqueando la comunicación.| 
|**Error en la conexión al servidor de datos**| Este error puede aparecer si está trabajando con un servidor de Syslog sobre TCP. El agente SIEM no puede conectarse a su servidor de Syslog.  Si recibe este error, el agente dejará de extraer nuevas actividades hasta que se corrija, por lo que debe asegurarse de seguir los pasos de corrección hasta que el error deje de aparecer.|1. Asegúrese de que se haya definido correctamente el servidor de Syslog: en la interfaz de Cloud App Security, edite el agente SIEM como se ha descrito anteriormente, asegúrese de que haya escrito correctamente el nombre del servidor y establezca el puerto correcto. </br>2. Compruebe la conectividad con el servidor de Syslog: asegúrese de que el firewall no esté bloqueando la comunicación.|
|**Error del agente SIEM**|El agente SIEM ha estado desconectado durante más de X horas.|Asegúrese de que no ha cambiado la configuración de SIEM en el portal de Cloud App Security. De lo contrario, esto podría indicar problemas de conectividad entre Cloud App Security y el equipo en el que se ejecuta el agente SIEM.|
|**Error de notificación del agente SIEM**|Se han recibido errores de reenvío de notificación de agente SIEM procedentes de un agente SIEM.|Esto indica que ha recibido errores relacionados con la conexión entre el agente SIEM y el servidor SIEM. Asegúrese de que no hay ningún firewall que bloquee el servidor SIEM o el equipo en el que se ejecuta el agente SIEM. Compruebe también que la dirección IP del servidor SIEM no ha cambiado.|



## <a name="see-also"></a>Consulte también  
[Actividades diarias para proteger el entorno de nube](daily-activities-to-protect-your-cloud-environment.md)   

[Los clientes Premier también pueden elegir Cloud App Security directamente desde el Portal Premier.](https://premier.microsoft.com/)  
  
  