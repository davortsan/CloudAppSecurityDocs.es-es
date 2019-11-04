---
title: Integración de SIEM genérica con Cloud App Security
description: En este artículo se proporciona información sobre cómo integrar el SIEM genérico con Cloud App Security.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 10/28/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: b4d0cce7d6f46b362ad75c7316bc799bdba008a6
ms.sourcegitcommit: 2c2a14a58492990be5bbac88ff9beb071d556c80
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2019
ms.locfileid: "73198738"
---
# <a name="generic-siem-integration"></a>Integración de SIEM genérica

*Se aplica a: Microsoft Cloud App Security*

Puede integrar Microsoft Cloud App Security con el servidor de SIEM genérico para habilitar la supervisión centralizada de alertas y actividades de aplicaciones conectadas. A medida que las aplicaciones conectadas admiten nuevos eventos y actividades, podrá supervisarlas en Microsoft Cloud App Security. La integración de un servicio SIEM le permite proteger mejor sus aplicaciones de nube a la vez que mantiene el flujo de trabajo de seguridad habitual, automatizando así los procedimientos de seguridad y estableciendo correlaciones entre eventos basados en la nube y eventos locales. El agente SIEM de Microsoft Cloud App Security se ejecuta en el servidor y extrae las alertas y las actividades de Microsoft Cloud App Security y las transmite al servidor SIEM.

Cuando integre por primera vez su SIEM con Cloud App Security, las actividades y las alertas de los dos últimos días se reenviarán al SIEM, así como todas las actividades y alertas (en función del filtro seleccionado) que se produzcan a partir de entonces. Si deshabilita esta característica durante un período prolongado y la habilita de nuevo, se reenviarán las alertas y las actividades de los dos últimos días, así como las que se produzcan a partir de entonces.

Entre las soluciones de integración adicionales se incluyen:

* **Azure Sentinel** : un Siem escalable y nativo en la nube para la integración nativa. Para obtener información sobre la integración con Azure Sentinel, consulte [integración de centinela de Azure](siem-sentinel.md).
* **Microsoft Security Graph API** : un servicio intermediario (o agente) que proporciona una única interfaz de programación para conectar varios proveedores de seguridad. Para obtener más información, consulte [integración de soluciones de seguridad con la API de seguridad de Microsoft Graph](https://docs.microsoft.com/graph/security-integration#list-of-connectors-from-microsoft).

> [!IMPORTANT]
> Si está integrando la protección contra amenazas avanzada de Azure en Cloud App Security y ambos servicios están configurados para enviar notificaciones de alerta a un SIEM, comenzará a recibir notificaciones SIEM duplicadas para la misma alerta. Se emitirá una alerta para todos los servicios y tendrán id. de alerta distintas. Para evitar la duplicación y la confusión, asegúrese de controlar el escenario. Por ejemplo, decida dónde desea realizar la administración de alertas y, a continuación, detenga las notificaciones de SIEM que se envían desde el otro servicio.

## <a name="generic-siem-integration-architecture"></a>Arquitectura de integración de SIEM genérica

El agente SIEM se implementa en la red de su organización. Una vez implementado y configurado, extrae los tipos de datos que se han configurado (alertas y actividades) mediante las API de RESTful de Cloud App Security.
El tráfico se envía a través de un canal HTTPS cifrado en el puerto 443.

Una vez que el agente SIEM recupere los datos de Cloud App Security, enviará los mensajes de Syslog al SIEM local. Cloud App Security usa las configuraciones de red que proporcionó durante la instalación (TCP o UDP con un puerto personalizado).

![Arquitectura de integración de SIEM](media/siem-architecture.png)

## <a name="supported-siems"></a>SIEM admitidos

Cloud App Security actualmente admite Micro Focus ArcSight y CEF genérico.

## <a name="how-to-integrate"></a>Integración

La integración con SIEM se realiza en tres pasos:

1. Configuración en el portal de Cloud App Security
2. Descarga del archivo JAR y ejecución en el servidor
3. Valide que el agente SIEM funcione.

### <a name="prerequisites"></a>Requisitos previos

- Servidor Windows o Linux estándar (puede ser una máquina virtual).
- Sistema operativo: Windows o Linux
- CPU: 2
- Espacio en disco: 20 GB
- RAM: 2 GB
- El servidor debe ejecutar Java 8. No se admiten las versiones anteriores.
- Configuración del firewall, tal como se describe en [Requisitos de red](network-requirements.md)

## <a name="integrating-with-your-siem"></a>Integración con su SIEM

### <a name="step-1-set-it-up-in-the-cloud-app-security-portal"></a>Paso 1: configuración en el portal de Cloud App Security

1. En el portal de Cloud App Security, en el engranaje de **configuración** , haga clic en **extensiones de seguridad**.

1. En la pestaña **agentes Siem** , haga clic en agregar ( **+** ) y, a continuación, elija **Siem genérico**.

    ![Captura de pantalla que muestra el menú Agregar integración de SIEM](media/siem0.png)

1. En el asistente, haga clic en **Iniciar asistente**.
1. En el asistente, asigne un nombre, **seleccione el formato SIEM** y establezca la **Configuración avanzada** que esté relacionada con ese formato. Haga clic en **Siguiente**.

    ![Configuración general de SIEM](media/siem1.png)

1. Escriba la dirección IP o nombre de host del **host de syslog remoto** y el **número de puerto de syslog**. Seleccione TCP o UDP como protocolo de syslog remoto.
    Puede trabajar con el administrador de seguridad para obtener estos detalles si no los tiene. Haga clic en **Siguiente**.

    ![Configuración remota de Syslog](media/siem2.png)

1. Seleccione los tipos de datos que quiera exportar al servidor SIEM para **Alertas** y **Actividades**. Use el control deslizante para habilitarlas y deshabilitarlas; de forma predeterminada todo está seleccionado. Puede usar el menú desplegable **Apply to** (Aplicar a) para establecer filtros para enviar solo alertas y actividades específicas al servidor SIEM. Haga clic en **Editar y obtener vista previa de resultados** para comprobar que el filtro funciona según lo esperado. Haga clic en **Siguiente**.

   ![Configuración de tipos de datos](media/siem3.png)

1. Copie el token y guárdelo para más adelante.
    Haga clic en Finalizar y salga del asistente. Vuelva a la página de SIEM para ver al agente SIEM que ha agregado en la tabla. Mostrará que está **Creado** hasta que se conecte más adelante.

> [!NOTE]
> Los tokens que se creen se enlazan al administrador que los haya creado. Esto significa que, si se elimina al usuario administrador de Cloud App Security, el token dejará de ser válido.

### <a name="step-2-download-the-jar-file-and-run-it-on-your-server"></a>Paso 2: descarga del archivo JAR y ejecución en el servidor

1. En [Centro de descarga de Microsoft](https://go.microsoft.com/fwlink/?linkid=838596), después de aceptar los [términos de licencia del software](https://go.microsoft.com/fwlink/?linkid=862491), descargue el archivo .zip y descomprímalo.

1. Ejecute el archivo extraído en el servidor:

    `java -jar mcas-siemagent-0.87.20-signed.jar [--logsDirectory DIRNAME] [--proxy ADDRESS[:PORT]] --token TOKEN`

> [!NOTE]
>
> - El nombre de archivo puede diferir dependiendo de la versión del agente SIEM.
> - Los parámetros entre corchetes [  ] son opcionales y solo deben usarse si procede.
> - Se recomienda ejecutar el archivo JAR mientras el servidor se inicia.
>   - Windows: ejecute como una tarea programada y asegúrese de configurar la tarea para que se **ejecute si el usuario ha iniciado sesión o no** y desactive la casilla **detener la tarea si se ejecuta durante más tiempo que** .
>   - Linux: agregue el comando run con un símbolo **&** al archivo rc.local. Por ejemplo: `java -jar mcas-siemagent-0.87.20-signed.jar [--logsDirectory DIRNAME] [--proxy ADDRESS[:PORT]] --token TOKEN &`

Se usan las variables siguientes:

- NOMBRE_DIRECTORIO es la ruta de acceso al directorio que quiere usar para los registros de depuración del agente local.
- DIRECCIÓN[:PUERTO] es la dirección del servidor proxy y el puerto que usa el servidor para conectarse a Internet.
- TOKEN es el token del agente SIEM que ha copiado en el paso anterior.

Puede escribir -h en cualquier momento para obtener ayuda.

#### Ejemplo de registros de actividad<a name="siem-samples"></a>

Estos son registros de actividad de ejemplo que se envían al servidor SIEM:

```
2017-11-22T17:50:04.000Z CEF:0|MCAS|SIEM_Agent|0.111.85|EVENT_CATEGORY_LOGOUT|Log out|0|externalId=1511373015679_167ae3eb-ed33-454a-b548-c2ed6cea6ef0 rt=1511373004000 start=1511373004000 end=1511373004000 msg=Log out suser=admin@contoso.com destinationServiceName=ServiceNow dvc=13.82.149.151 requestClientApplication= cs1Label=portalURL cs1=https://contoso.portal.cloudappsecurity.com/#/audits?activity.id\=eq(1511373015679_167ae3eb-ed33-454a-b548-c2ed6cea6ef0,) cs2Label=uniqueServiceAppIds cs2=APPID_SERVICENOW cs3Label=targetObjects cs3=admin@contoso.com,admin@contoso.com,admin@contoso.com cs4Label=policyIDs cs4= c6a1Label="Device IPv6 Address" c6a1=

2017-11-28T19:40:15.000Z CEF:0|MCAS|SIEM_Agent|0.112.68|EVENT_CATEGORY_VIEW_REPORT|View report|0|externalId=1511898027370_e272cd5f-31a3-48e3-8a6a-0490c042950a rt=1511898015000 start=1511898015000 end=1511898015000 msg=View report: ServiceNow Report 23 suser=admin@contoso.com destinationServiceName=ServiceNow dvc= requestClientApplication= cs1Label=portalURL cs1=https://contoso.portal.cloudappsecurity.com/#/audits?activity.id\=eq(1511898027370_e272cd5f-31a3-48e3-8a6a-0490c042950a,) cs2Label=uniqueServiceAppIds cs2=APPID_SERVICENOW cs3Label=targetObjects cs3=23,sys_report,admin@contoso.com,admin@contoso.com,admin@contoso.com cs4Label=policyIDs cs4= c6a1Label="Device IPv6 Address" c6a1=

2017-11-28T19:25:34.000Z CEF:0|MCAS|SIEM_Agent|0.112.68|EVENT_CATEGORY_DELETE_OBJECT|Delete object|0|externalId=1511897141625_7558b33f-218c-40ff-be5d-47d2bdd6b798 rt=1511897134000 start=1511897134000 end=1511897134000 msg=Delete object: ServiceNow Object f5122008db360300906ff34ebf96198a suser=admin@contoso.com destinationServiceName=ServiceNow dvc= requestClientApplication= cs1Label=portalURL cs1=https://contoso.portal.cloudappsecurity.com/#/audits?activity.id\=eq(1511897141625_7558b33f-218c-40ff-be5d-47d2bdd6b798,) cs2Label=uniqueServiceAppIds cs2=APPID_SERVICENOW cs3Label=targetObjects cs3=,,admin@contoso.com,admin@contoso.com,admin@contoso.com cs4Label=policyIDs cs4= c6a1Label="Device IPv6 Address" c6a1=

2017-11-27T20:40:14.000Z CEF:0|MCAS|SIEM_Agent|0.112.49|EVENT_CATEGORY_CREATE_USER|Create user|0|externalId=1511815215873_824f8f8d-2ecd-439b-98b1-99a1adf7ba1c rt=1511815214000 start=1511815214000 end=1511815214000 msg=Create user: user 747518c0db360300906ff34ebf96197c suser=admin@contoso.com destinationServiceName=ServiceNow dvc= requestClientApplication= cs1Label=portalURL cs1=https://contoso.portal.cloudappsecurity.com/#/audits?activity.id\=eq(1511815215873_824f8f8d-2ecd-439b-98b1-99a1adf7ba1c,) cs2Label=uniqueServiceAppIds cs2=APPID_SERVICENOW cs3Label=targetObjects cs3=,747518c0db360300906ff34ebf96197c,sys_user,admin@contoso.com,admin@contoso.com,admin@contoso.com cs4Label=policyIDs cs4= c6a1Label="Device IPv6 Address" c6a1=

2017-11-27T20:41:20.000Z CEF:0|MCAS|SIEM_Agent|0.112.49|EVENT_CATEGORY_DELETE_USER|Delete user|0|externalId=1511815287798_bcf60601-ecef-4207-beda-3d2b8d87d383 rt=1511815280000 start=1511815280000 end=1511815280000 msg=Delete user: user 233490c0db360300906ff34ebf9619ef suser=admin@contoso.com destinationServiceName=ServiceNow dvc= requestClientApplication= cs1Label=portalURL cs1=https://contoso.portal.cloudappsecurity.com/#/audits?activity.id\=eq(1511815287798_bcf60601-ecef-4207-beda-3d2b8d87d383,) cs2Label=uniqueServiceAppIds cs2=APPID_SERVICENOW cs3Label=targetObjects cs3=,233490c0db360300906ff34ebf9619ef,,admin@contoso.com,admin@contoso.com,admin@contoso.com cs4Label=policyIDs cs4= c6a1Label="Device IPv6 Address" c6a1=

2017-11-28T19:24:55.000Z LAB-EUW-ARCTEST CEF:0|MCAS|SIEM_Agent|0.112.68|EVENT_CATEGORY_DELETE_OBJECT|Delete object|0|externalId=1511897117617_5be018ee-f676-4473-a9b5-5982527409be rt=1511897095000 start=1511897095000 end=1511897095000 msg=Delete object: ServiceNow Object b1709c40db360300906ff34ebf961923 suser=admin@contoso.com destinationServiceName=ServiceNow dvc= requestClientApplication= cs1Label=portalURL cs1=https://contoso.portal.cloudappsecurity.com/#/audits?activity.id\=eq(1511897117617_5be018ee-f676-4473-a9b5-5982527409be,) cs2Label=uniqueServiceAppIds cs2=APPID_SERVICENOW cs3Label=targetObjects cs3=,,admin@contoso.com,admin@contoso.com,admin@contoso.com cs4Label=policyIDs cs4= c6a1Label="Device IPv6 Address" c6a1=
```

El siguiente texto es un ejemplo de archivo de registro de alertas:

```
2017-07-15T20:42:30.531Z CEF:0|MCAS|SIEM_Agent|0.102.17|ALERT_CABINET_EVENT_MATCH_AUDIT|myPolicy|3|externalId=596a7e360c204203a335a3fb start=1500151350531 end=1500151350531 msg=Activity policy ''myPolicy'' was triggered by ''admin@box-contoso.com'' suser=admin@box-contoso.com destinationServiceName=Box cn1Label=riskScore cn1= cs1Label=portalURL cs1=https://cloud-app-security.com/#/alerts/596a7e360c204203a335a3fb cs2Label=uniqueServiceAppIds cs2=APPID_BOX cs3Label=relatedAudits cs3=1500151288183_acc891bf-33e1-424b-a021-0d4370789660 cs4Label=policyIDs cs4=59f0ab82f797fa0681e9b1c7

2017-07-16T09:36:26.550Z CEF:0|MCAS|SIEM_Agent|0.102.17|ALERT_CABINET_EVENT_MATCH_AUDIT|test-activity-policy|3|externalId=596b339b0c204203a33a51ae start=1500197786550 end=1500197786550 msg=Activity policy ''test-activity-policy'' was triggered by ''user@contoso.com'' suser=user@contoso.com destinationServiceName=Salesforce cn1Label=riskScore cn1= cs1Label=portalURL cs1=https://cloud-app-security.com/#/alerts/596b339b0c204203a33a51ae cs2Label=uniqueServiceAppIds cs2=APPID_SALESFORCE cs3Label=relatedAudits cs3=1500197720691_b7f6317c-b8de-476a-bc8f-dfa570e00349 cs4Label=policyIDs cs4=

2017-07-16T09:17:03.361Z CEF:0|MCAS|SIEM_Agent|0.102.17|ALERT_CABINET_EVENT_MATCH_AUDIT|test-activity-policy3|3|externalId=596b2fd70c204203a33a3eeb start=1500196623361 end=1500196623361 msg=Activity policy ''test-activity-policy3'' was triggered by ''admin@contoso.com'' suser=admin@contoso.com destinationServiceName=Office 365 cn1Label=riskScore cn1= cs1Label=portalURL cs1=https://cloud-app-security.com/#/alerts/596b2fd70c204203a33a3eeb cs2Label=uniqueServiceAppIds cs2=APPID_O365 cs3Label=relatedAudits cs3=1500196549157_a0e01f8a-e29a-43ae-8599-783c1c11597d cs4Label=policyIDs cs4=

2017-07-16T09:17:15.426Z CEF:0|MCAS|SIEM_Agent|0.102.17|ALERT_CABINET_EVENT_MATCH_AUDIT|test-activity-policy|3|externalId=596b2fd70c204203a33a3eec start=1500196635426 end=1500196635426 msg=Activity policy ''test-activity-policy'' was triggered by ''admin@contoso.com'' suser=admin@contoso.com destinationServiceName=Microsoft 365 admin center cn1Label=riskScore cn1= cs1Label=portalURL cs1=https://cloud-app-security.com/#/alerts/596b2fd70c204203a33a3eec cs2Label=uniqueServiceAppIds cs2=APPID_O365_PORTAL cs3Label=relatedAudits cs3=1500196557398_3e102b20-d9fa-4f66-b550-8c7a403bb4d8 cs4Label=policyIDs cs4=59f0ab35f797fa9811e9b1c7

2017-07-16T09:17:46.290Z CEF:0|MCAS|SIEM_Agent|0.102.17|ALERT_CABINET_EVENT_MATCH_AUDIT|test-activity-policy4|3|externalId=596b30200c204203a33a4765 start=1500196666290 end=1500196666290 msg=Activity policy ''test-activity-policy4'' was triggered by ''admin@contoso.com'' suser=admin@contoso.com destinationServiceName=Microsoft Exchange Online cn1Label=riskScore cn1= cs1Label=portalURL cs1=https://cloud-app-security.com/#/alerts/596b30200c204203a33a4765 cs2Label=uniqueServiceAppIds cs2=APPID_OUTLOOK cs3Label=relatedAudits cs3=1500196587034_a8673602-7e95-46d6-a1fe-c156c4709c5d cs4Label=policyIDs cs4=

2017-07-16T09:41:04.369Z CEF:0|MCAS|SIEM_Agent|0.102.17|ALERT_CABINET_EVENT_MATCH_AUDIT|test-activity-policy2|3|externalId=596b34b10c204203a33a5240 start=1500198064369 end=1500198064369 msg=Activity policy ''test-activity-policy2'' was triggered by ''user2@test15-adallom.com'' suser=user2@test15-adallom.com destinationServiceName=Google cn1Label=riskScore cn1= cs1Label=portalURL cs1=https://cloud-app-security.com/#/alerts/596b34b10c204203a33a5240 cs2Label=uniqueServiceAppIds cs2=APPID_33626 cs3Label=relatedAudits cs3=1500197996117_fd71f265-1e46-4f04-b372-2e32ec874cd3 cs4Label=policyIDs cs4=
```

#### <a name="sample-cloud-app-security-alerts-in-cef-format"></a>Alertas de Cloud App Security de ejemplo en formato CEF

|   Aplicable a   |      Nombre del campo CEF      |                                                   Descripción                                                   |
|-------------------|--------------------------|-----------------------------------------------------------------------------------------------------------------|
| Actividades y alertas |          start           |                                           Marca de tiempo de actividad o alerta                                           |
| Actividades y alertas |           end            |                                           Marca de tiempo de actividad o alerta                                           |
| Actividades y alertas |            rt            |                                           Marca de tiempo de actividad o alerta                                           |
| Actividades y alertas |           msg            |                              Descripción de la actividad o alerta, tal como se muestra en el portal                               |
| Actividades y alertas |          suser           |                                         Usuario asunto de la actividad o alerta                                          |
| Actividades y alertas |  destinationServiceName  |                  Aplicación que origina la actividad o alerta, por ejemplo, Office 365, SharePoint, Box.                   |
| Actividades y alertas |        cs<X>Label        |        Cada etiqueta tiene un significado diferente, pero la misma etiqueta lo explica, por ejemplo, targetObjects.        |
| Actividades y alertas |          cs<X>           | La información correspondiente a la etiqueta (el usuario de destino de la actividad o alerta según el ejemplo de etiqueta). |
|    Actividades     |     EVENT_CATEGORY_*     |                                       Categoría general de la actividad                                       |
|    Actividades     |         <ACTION>         |                                  Tipo de actividad, tal como se muestra en el portal                                  |
|    Actividades     |        externalId        |                                                    Identificador de evento                                                     |
|    Actividades     |           dvc            |                                             Dirección IP del dispositivo del cliente                                             |
|    Actividades     | requestClientApplication |                                         Agente de usuario del dispositivo del cliente                                         |
|      Alertas       |       <alert type>       |                                  Por ejemplo "ALERT_CABINET_EVENT_MATCH_AUDIT"                                  |
|      Alertas       |          <name>          |                                             Nombre de la directiva coincidente                                             |
|      Alertas       |        externalId        |                                                    Id. de alerta                                                     |

### <a name="step-3-validate-that-the-siem-agent-is-working"></a>Paso 3: validación del correcto funcionamiento del agente SIEM

1. Asegúrese de que el estado del agente SIEM en el portal de Cloud App Security no sea **Error de conexión** o **Desconectado**, y de que no haya ninguna notificación del agente. Se mostrará como **Error de conexión** si la conexión está inactiva durante más de dos horas. El estado se muestra como **Desconectado** si la conexión está inactiva durante más de 12 horas.
 ![SIEM desconectado](media/siem-not-connected.png)

    En su lugar, el estado debe ser Conectado, tal como se muestra aquí: ![SIEM conectado](media/siem-connected.png).

1. En el servidor Syslog o SIEM, asegúrese de que vea las alertas y actividades procedentes de Cloud App Security.

## <a name="regenerating-your-token"></a>Volver a generar el token

Si pierde el token, siempre puede volver a generarlo haciendo clic en los tres puntos al final de la fila del agente SIEM de la tabla. Seleccione **Regenerar token** para obtener un nuevo token.

![SIEM: volver a generar el token](media/siem-regenerate-token.png)

## <a name="editing-your-siem-agent"></a>Editar el agente SIEM

Para editar el agente SIEM, haga clic en los tres puntos al final de la fila del agente SIEM de la tabla y seleccione **Editar**. Si edita el agente SIEM, no es necesario volver a ejecutar el archivo .jar, ya que se actualiza automáticamente.

![SIEM: edición](media/siem-edit.png)

## <a name="deleting-your-siem-agent"></a>Eliminación al agente SIEM

Para eliminar el agente SIEM, haga clic en los tres puntos al final de la fila del agente SIEM de la tabla y seleccione **Eliminar**.

![SIEM: eliminación](media/siem-delete.png)

> [!NOTE]
> Esta característica está en versión preliminar pública.

## <a name="next-steps"></a>Pasos siguientes

[Solución de problemas de integración de SIEM](troubleshooting-siem.md)

[Los clientes Premier también pueden crear una solicitud de soporte técnico directamente en el portal Premier.](https://premier.microsoft.com/)
