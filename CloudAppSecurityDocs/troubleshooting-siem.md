---
title: 'Solución de problemas de la integración de SIEM: Cloud App Security | Microsoft Docs'
description: En este artículo se proporciona una lista de posibles problemas al conectar su SIEM con Cloud App Security, así como soluciones para cada uno de ellos.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 08/30/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: de64d9ca-eaed-4243-bcf7-adca5aff18c8
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: a5ab44813959db6ad7b1f437ba88b47223ce5e41
ms.sourcegitcommit: 094bb42a198fe733cfd3aec79d74487672846dfa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/24/2019
ms.locfileid: "74459960"
---
# <a name="troubleshooting-the-siem-agent"></a>Solución de problemas del agente SIEM

*Se aplica a: Microsoft Cloud App Security*

En este artículo se proporciona una lista de posibles problemas al conectar su SIEM con Cloud App Security, así como posibles soluciones.

## <a name="recover-missing-activity-events-in-mcas-siem-agent"></a>Recover missing activity events in MCAS SIEM Agent 

If you received a system alert regarding an issue with activity delivery through the SIEM agent, follow the steps below to recover the activity events in the timeframe of the issue. These steps will guide you through setting up a new Recovery SIEM agent that will run in parallel and resend the activity events to your SIEM.

>[!NOTE]
>The recovery process will resend all activity events in the timeframe described in the system alert. If your SIEM already contains activity events from this timeframe, you will experience duplicated events after this recovery. 

### <a name="step-1--configure-a-new-siem-agent-in-parallel-to-your-existing-agent"></a>Step 1 – Configure a new SIEM Agent in parallel to your existing agent 
1. In the Cloud App Security portal, go to Security Extensions page.  
2. In the SIEM Agents tab, click on [add a new SIEM agent](siem.md), and use the wizard to configure the connection details to your SIEM. 

    >[!NOTE]
    >This agent should run in parallel to the existing one, so network configuration might not be identical. 

1. In the wizard, configure the Data Types to include **only Activities** and apply the same activity filter that was used in your original SIEM agent (if it exists). 
2. Turn on **Recovery mode** by checking the Recovery mode checkbox. This action will automatically configure the SIEM Agent to send only the missing activities due to the issue and stop sending activities once all activities are fully recovered.
3. Guarde la configuración.
4. Run the new agent using the generated token.


### <a name="step-2--validate-the-successful-data-delivery-to-your-siem"></a>Step 2 – Validate the successful data delivery to your SIEM 
1. Connect to your SIEM and validate that new data is received from the new SIEM Agent that you configured. 
2. The agent will only send activities from the timeframe of the issue, which you were alerted on. 

### <a name="step-3--remove-the-recovery-siem-agent"></a>Step 3 – Remove the Recovery SIEM agent 
1. The recovery SIEM agent will automatically stop sending data and be disabled once it reaches the end date.
2. Validate in your SIEM that no new data is sent by the recovery SIEM agent. 
3. Stop the execution of the agent on your machine. 
4. In the portal, go to SIEM Agent page, and remove the Recovery SIEM Agent. 
5. Make sure your original SIEM Agent is still running properly. 

## <a name="general-troubleshooting"></a>General troubleshooting

Asegúrese de que el estado del agente SIEM en el portal de Microsoft Cloud App Security no sea **Error de conexión** ni **Desconectado** y de que no haya ninguna notificación del agente. El estado se muestra como **Error de conexión** si la conexión está inactiva durante más de dos horas. El estado cambia a **Desconectado** si la conexión está inactiva durante más de 12 horas.

Si ve alguno de los errores siguientes en el símbolo del sistema mientras se ejecuta al agente, siga estos pasos para corregir el problema:

|Error de:|Descripción|Solución|
|----|----|----|
|Error general durante el arranque|Error inesperado durante el arranque del agente.|Póngase en contacto con el soporte técnico.|
|Demasiados errores críticos|Se han producido demasiados errores críticos al conectar la consola. Apagando el equipo.|Póngase en contacto con el soporte técnico.|
|Token no válido|El token proporcionado no es válido.|Asegúrese de que haya copiado el token adecuado. Puede usar el proceso anterior para volver a generar el token.|
|Dirección de proxy no válida|La dirección de proxy proporcionada no es válida.|Asegúrese de que haya escrito el proxy y el puerto correctos.|


Después de crear el agente, consulte la página del agente SIEM en el portal de Cloud App Security. Si ve alguna de las **Notificaciones del agente** siguientes, siga estos pasos para corregir el problema:

|Error de:|Descripción|Solución|
|----|----|----|
|**Error interno**|Se ha producido un problema desconocido con el agente SIEM.|Póngase en contacto con el soporte técnico.|
|**Error en el envío al servidor de datos**|Este error puede aparecer si está trabajando con un servidor de Syslog sobre TCP. El agente SIEM no puede conectarse a su servidor de Syslog.  Si se le muestra este error, el agente dejará de extraer nuevas actividades hasta que se solucione. Debe seguir los pasos de corrección indicados hasta que el error deje de aparecer.|1. Make sure you properly defined your Syslog server: In the Cloud App Security UI, edit your SIEM agent as described above. Compruebe que haya escrito correctamente el nombre del servidor y establecido el puerto correcto. </br>2. Check connectivity to your Syslog server: Make sure your firewall isn't blocking communication.| 
|**Error en la conexión al servidor de datos**| Este error puede aparecer si está trabajando con un servidor de Syslog sobre TCP. El agente SIEM no puede conectarse a su servidor de Syslog.  Si se le muestra este error, el agente dejará de extraer nuevas actividades hasta que se solucione. Debe seguir los pasos de corrección indicados hasta que el error deje de aparecer.|1. Make sure you properly defined your Syslog server: In the Cloud App Security UI, edit your SIEM agent as described above. Compruebe que haya escrito correctamente el nombre del servidor y establecido el puerto correcto. </br>2. Check connectivity to your Syslog server: Make sure your firewall isn't blocking communication.|
|**Error del agente SIEM**|El agente SIEM ha estado desconectado durante más de X horas.|Asegúrese de que no ha cambiado la configuración de SIEM en el portal de Cloud App Security. De lo contrario, este error podría indicar problemas de conectividad entre Cloud App Security y el equipo en el que se ejecuta el agente SIEM.|
|**Error de notificación del agente SIEM**|Se han recibido errores de reenvío de notificación de agente SIEM procedentes de un agente SIEM.|Este error indica que ha recibido errores relacionados con la conexión entre el agente SIEM y el servidor SIEM. Asegúrese de que no hay ningún firewall que bloquee el servidor SIEM o el equipo en el que se ejecuta el agente SIEM. Compruebe también que la dirección IP del servidor SIEM no ha cambiado.|


## <a name="next-steps"></a>Pasos siguientes
  
[Actividades diarias para proteger el entorno de nube](daily-activities-to-protect-your-cloud-environment.md)   

[!INCLUDE [Open support ticket](includes/support.md)]  
  
