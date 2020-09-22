---
title: 'Solución de problemas de integración de SIEM: Cloud App Security'
description: En este artículo se proporciona una lista de posibles problemas al conectar su SIEM con Cloud App Security, así como soluciones para cada uno de ellos.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 06/29/2020
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: effcab71a9b359aeb5d97ab2dc889e10133f7b9e
ms.sourcegitcommit: 575f2b2efa9ca4477d7e60271d21e225ef2c38ea
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/22/2020
ms.locfileid: "90877009"
---
# <a name="troubleshooting-the-siem-agent"></a>Solución de problemas del agente SIEM

[!INCLUDE [Banner for top of topics](includes/banner.md)]

En este artículo se proporciona una lista de posibles problemas al conectar su SIEM con Cloud App Security, así como posibles soluciones.

## <a name="recover-missing-activity-events-in-cloud-app-security-siem-agent"></a>Recuperación de eventos de actividad que faltan en Cloud App Security agente SIEM

Antes de continuar, compruebe que la [licencia de Cloud App Security](https://aka.ms/mcaslicensing) admite la integración de Siem que está intentando configurar.

Si recibió una alerta del sistema con respecto a un problema con la entrega de actividad a través del agente SIEM, siga los pasos que se indican a continuación para recuperar los eventos de actividad en el período de tiempo del problema. Estos pasos le guiarán a través de la configuración de un nuevo agente SIEM de recuperación que se ejecutará en paralelo y volverá a enviar los eventos de actividad a su SIEM.

> [!NOTE]
> El proceso de recuperación volverá a enviar todos los eventos de actividad en el período de tiempo descrito en la alerta del sistema. Si el SIEM ya contiene eventos de actividad de este período de tiempo, se producirán eventos duplicados después de esta recuperación.

### <a name="step-1--configure-a-new-siem-agent-in-parallel-to-your-existing-agent"></a>Paso 1: configuración de un nuevo agente SIEM en paralelo para el agente existente

1. En el portal de Cloud App Security, vaya a la página extensiones de seguridad.
1. En la pestaña agentes SIEM, haga clic en [Agregar un nuevo agente Siem](siem.md)y use el Asistente para configurar los detalles de conexión a su Siem. Por ejemplo, puede crear un nuevo agente SIEM con la siguiente configuración:
    - **Protocolo**: TCP
    - **Host remoto**: cualquier equipo en el que pueda escuchar un puerto. Por ejemplo, una solución sencilla sería usar el mismo equipo que el agente y establecer la dirección IP del host remoto en 127.0.0.1
    - **Puerto**: cualquier puerto que pueda escuchar en el equipo host remoto

    > [!NOTE]
    > Este agente debe ejecutarse en paralelo al existente, por lo que es posible que la configuración de red no sea idéntica.

1. En el asistente, configure los tipos de datos para incluir **solo las actividades** y aplicar el mismo filtro de actividad que se usó en el agente Siem original (si existe).
1. Guarde la configuración
1. Ejecute el nuevo agente mediante el token generado.

### <a name="step-2--validate-the-successful-data-delivery-to-your-siem"></a>Paso 2: validar la entrega de datos correcta a su SIEM

Siga los pasos siguientes para validar la configuración:

1. Conéctese a su SIEM y compruebe que se reciben nuevos datos del nuevo agente SIEM que ha configurado.

> [!NOTE]
> El agente solo enviará actividades en el plazo del problema en el que se le ha avisado.

1. Si el SIEM no recibe los datos, en el nuevo equipo del agente SIEM, intente escuchar el puerto configurado para reenviar actividades para ver si los datos se envían desde el agente al SIEM. Por ejemplo, ejecute, `netcat -l <port>` donde `<port>` es el número de puerto configurado previamente.

> [!NOTE]
> Si usa, asegúrese `ncat` de especificar la marca IPv4 `-4` .

1. Si el agente envía datos, pero no los recibe el SIEM, compruebe el registro del agente SIEM. Si puede ver los mensajes de "conexión rechazada", asegúrese de que el agente SIEM está configurado para usar TLS 1,2 o una versión más reciente.

### <a name="step-3--remove-the-recovery-siem-agent"></a>Paso 3: eliminación del agente SIEM de recuperación

1. El agente SIEM de recuperación dejará de enviar datos automáticamente y se deshabilitará una vez que llegue a la fecha de finalización.
1. Valide en el SIEM que el agente SIEM de recuperación no envíe ningún dato nuevo.
1. Detenga la ejecución del agente en el equipo.
1. En el portal, vaya a la página del agente SIEM y quite el agente SIEM de recuperación.
1. Asegúrese de que el agente SIEM original sigue ejecutándose correctamente.

## <a name="general-troubleshooting"></a>Solución general de problemas

Asegúrese de que el estado del agente SIEM en el portal de Microsoft Cloud App Security no sea **Error de conexión** ni **Desconectado** y de que no haya ninguna notificación del agente. El estado se muestra como **Error de conexión** si la conexión está inactiva durante más de dos horas. El estado cambia a **Desconectado** si la conexión está inactiva durante más de 12 horas.

Si ve alguno de los errores siguientes en el símbolo del sistema mientras se ejecuta al agente, siga estos pasos para corregir el problema:

|Error|Descripción|Solución|
|----|----|----|
|Error general durante el arranque|Error inesperado durante el arranque del agente.|Póngase en contacto con el servicio de soporte técnico.|
|Demasiados errores críticos|Se han producido demasiados errores críticos al conectar la consola. Apagando el equipo.|Póngase en contacto con el servicio de soporte técnico.|
|Token no válido|El token proporcionado no es válido.|Asegúrese de que haya copiado el token adecuado. Puede usar el proceso anterior para volver a generar el token.|
|Dirección de proxy no válida|La dirección de proxy proporcionada no es válida.|Asegúrese de que haya escrito el proxy y el puerto correctos.|

Después de crear el agente, consulte la página del agente SIEM en el portal de Cloud App Security. Si ve alguna de las **Notificaciones del agente** siguientes, siga estos pasos para corregir el problema:

|Error|Descripción|Solución|
|----|----|----|
|**Error interno**|Se ha producido un problema desconocido con el agente SIEM.|Póngase en contacto con el servicio de soporte técnico.|
|**Error en el envío al servidor de datos**|Este error puede aparecer si está trabajando con un servidor de Syslog sobre TCP. El agente SIEM no puede conectarse a su servidor de Syslog.  Si recibe este error, el agente dejará de extraer nuevas actividades hasta que se corrija. Debe seguir los pasos de corrección indicados hasta que el error deje de aparecer.|1. Asegúrese de que ha definido correctamente el servidor de syslog: en la interfaz de usuario de Cloud App Security, edite el agente SIEM tal y como se ha descrito anteriormente. Compruebe que haya escrito correctamente el nombre del servidor y establecido el puerto correcto. </br>2. Compruebe la conectividad con el servidor de syslog: Asegúrese de que el Firewall no está bloqueando la comunicación.|
|**Error en la conexión al servidor de datos**| Este error puede aparecer si está trabajando con un servidor de Syslog sobre TCP. El agente SIEM no puede conectarse a su servidor de Syslog.  Si recibe este error, el agente dejará de extraer nuevas actividades hasta que se corrija. Debe seguir los pasos de corrección indicados hasta que el error deje de aparecer.|1. Asegúrese de que ha definido correctamente el servidor de syslog: en la interfaz de usuario de Cloud App Security, edite el agente SIEM tal y como se ha descrito anteriormente. Compruebe que haya escrito correctamente el nombre del servidor y establecido el puerto correcto. </br>2. Compruebe la conectividad con el servidor de syslog: Asegúrese de que el Firewall no está bloqueando la comunicación.|
|**Error del agente SIEM**|El agente SIEM ha estado desconectado durante más de X horas.|Asegúrese de que no ha cambiado la configuración de SIEM en el portal de Cloud App Security. De lo contrario, este error podría indicar problemas de conectividad entre Cloud App Security y el equipo en el que se ejecuta el agente SIEM.|
|**Error de notificación del agente SIEM**|Se han recibido errores de reenvío de notificación de agente SIEM procedentes de un agente SIEM.|Este error indica que ha recibido errores relacionados con la conexión entre el agente SIEM y el servidor SIEM. Asegúrese de que no hay ningún firewall que bloquee el servidor SIEM o el equipo en el que se ejecuta el agente SIEM. Compruebe también que la dirección IP del servidor SIEM no ha cambiado.|

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Actividades diarias para proteger el entorno de nube](daily-activities-to-protect-your-cloud-environment.md)

[!INCLUDE [Open support ticket](includes/support.md)]
