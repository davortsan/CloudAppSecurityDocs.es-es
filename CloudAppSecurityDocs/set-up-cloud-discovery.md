---
title: 'Implementación de Cloud Discovery: Cloud App Security | Microsoft Docs'
description: En este artículo se describe el procedimiento de configuración de Cloud Discovery para que entre en funcionamiento.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: rkarlin
ms.date: 3/18/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: a9b5bd8d-305b-4e93-9a4c-a4683ea09080
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: a8e7c476690b1831b78a59c7c63b061aef0dc78e
ms.sourcegitcommit: 9f0c562322394a3dfac7f1d84286e673276a28b1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/14/2019
ms.locfileid: "65568516"
---
# <a name="set-up-cloud-discovery"></a>Configurar Cloud Discovery

*Se aplica a: Microsoft Cloud App Security*

Cloud Discovery analiza los registros de tráfico en el catálogo de aplicaciones en la nube de Microsoft Cloud App Security de más de 16 000 aplicaciones en la nube. Las aplicaciones se clasifican y se puntúan en función de más de 70 factores de riesgo para proporcionar visibilidad continua al uso de la nube, Shadow IT y el riesgo que Shadow IT supone para la organización.

## <a name="snapshot-and-continuous-risk-assessment-reports"></a>Informes de instantáneas y de evaluación continua de riesgos 

Se pueden generar dos tipos de informes: 

- **Informes de instantáneas**: proporcionan visibilidad ad hoc de un conjunto de registros de tráfico que puede cargar manualmente desde los firewalls y los servidores proxy.

- **Informes continuos**: analizan todos los registros que se reenvían desde la red mediante Cloud App Security. Proporcionan una mejor visibilidad de todos los datos e identifican automáticamente los usos erróneos, ya sea mediante el motor de detección de anomalías de aprendizaje automático o mediante las directivas personalizadas que haya definido. Estos informes pueden crearse conectándose de varias maneras:

  - [Integración de Microsoft Defender ATP](wdatp-integration.md): Cloud App Security se integra con Defender Advanced Threat Protection (ATP) de Microsoft de forma nativa, para simplificar la implementación de Cloud Discovery, ampliar las capacidades de Cloud Discovery más allá de la red corporativa y habilitar en el equipo de investigación.
  - [Recopilador de registros](discovery-docker.md): Los recopiladores de registros permiten automatizar fácilmente la carga de registros desde la red. El recopilador de registros se ejecuta en la red y recibe los registros a través de Syslog o FTP.
  - [Integración de Zscaler](zscaler-integration.md): Si trabaja con Cloud App Security y Zscaler, puede integrar los dos productos para mejorar la seguridad de la experiencia de Cloud Discovery. Juntos, Cloud App Security y Zscaler proporcionan una implementación fluida de Cloud Discovery, bloqueo automático de aplicaciones no autorizadas y evaluación de riesgos directamente en el portal de Zscaler.
 - [integración de iboss](iboss-integration.md): Si trabaja con Cloud App Security y iboss, puede integrar los dos productos para mejorar la experiencia de seguridad de Cloud Discovery. Juntos, Cloud App Security y iboss proporcionan una implementación fluida de Cloud Discovery automáticos de bloqueo de aplicaciones no autorizadas y evaluación de riesgos directamente en el portal de iboss.

## <a name="log-process-flow-from-raw-data-to-risk-assessment"></a>Flujo del proceso de registro: de datos sin procesar a evaluación de riesgos

El proceso de generación de una evaluación de riesgos consta de los siguientes pasos. El proceso tarda desde unos minutos hasta varias horas según la cantidad de datos procesados.  

- **Cargar**: se cargan los registros de tráfico web de la red en el portal.  

- **Redistribuir**: Cloud App Security redistribuye y extrae datos de tráfico de los registros de tráfico con un analizador dedicado para cada origen de datos.  

- **Analizar**: se analizan los datos de tráfico con el catálogo de aplicaciones en la nube para identificar más de 16 000 aplicaciones en la nube y evaluar su puntuación de riesgo. También se identifican los usuarios activos y las direcciones IP como parte del análisis.  

- **Generar informe**: se genera un informe de evaluación de riesgos de los datos extraídos de los archivos de registro.


>[!NOTE]
> Los datos de los informes continuos se analizan dos veces al día.



## Firewalls y servidores proxy compatibles <a name="supported-firewalls-and-proxies"></a>

- Barracuda - Web App Firewall (W3C)
- Blue Coat Proxy SG - registros de acceso (W3C)
- Check Point
- Firewall de Cisco ASA (en el caso de los firewalls de Cisco ASA, es necesario establecer el nivel de información en 6)
- Cisco ASA con FirePOWER
- Cisco IronPort WSA
- Cisco ScanSafe
- Cisco Meraki – Registro de direcciones URL
- Clavister NGFW (Syslog)
- Digital Arts i-FILTER
- Fortinet Fortigate
- iboss Secure Cloud Gateway
- Juniper SRX
- Juniper SSG
- McAfee Secure Web Gateway
- Microsoft Forefront Threat Management Gateway (W3C)
- Firewalls de la serie Palo Alto
- Sonicwall (anteriormente Dell)
- Sophos SG
- Sophos XG
- Sophos Cyberoam
- Squid (Common)
- Squid (Native)
- Websense - soluciones de seguridad Web - informe de detalle de investigación (CSV)
- Websense - soluciones de seguridad Web - registro de actividad de Internet (CEF)
- Zscaler

> [!NOTE]
> Cloud Discovery admite tanto direcciones IPv4 como IPv6.

Si el registro no es compatible, seleccione **Otro** como **Origen de datos** y especifique el dispositivo y el registro que está intentando cargar. El equipo de analistas de la nube de Cloud App Security examinará el registro y se le notificará si se ha agregado compatibilidad con el tipo de registro. También puede definir un analizador personalizado que coincida con el formato. Para obtener más información, vea [Uso del analizador de registros personalizado](custom-log-parser.md).


Atributos de datos (según la documentación del proveedor):


|                 Origen de datos                  |    Dirección URL de la aplicación de destino    |    IP de la aplicación de destino     |       Nombre de usuario       |      IP de origen       |    Tráfico total     |    Bytes cargados    |
|----------------------------------------------|----------------------|----------------------|----------------------|----------------------|----------------------|----------------------|
|                  Barracuda                   | <strong>Sí</strong> | <strong>Sí</strong> | <strong>Sí</strong> | <strong>Sí</strong> |          No          |          No          |
|                  Blue Coat                   | <strong>Sí</strong> |          No          | <strong>Sí</strong> | <strong>Sí</strong> | <strong>Sí</strong> | <strong>Sí</strong> |
|                  Checkpoint                  |          No          | <strong>Sí</strong> |          No          | <strong>Sí</strong> |          No          |          No          |
|              Cisco ASA (Syslog)              |          No          | <strong>Sí</strong> |          No          | <strong>Sí</strong> | <strong>Sí</strong> |          No          |
|           Cisco ASA con FirePOWER           | <strong>Sí</strong> | <strong>Sí</strong> | <strong>Sí</strong> | <strong>Sí</strong> | <strong>Sí</strong> | <strong>Sí</strong> |
|                  Cisco FWSM                  |          No          | <strong>Sí</strong> |          No          | <strong>Sí</strong> | <strong>Sí</strong> |          No          |
|              Cisco Ironport WSA              | <strong>Sí</strong> | <strong>Sí</strong> | <strong>Sí</strong> | <strong>Sí</strong> | <strong>Sí</strong> | <strong>Sí</strong> |
|                 Cisco Meraki                 | <strong>Sí</strong> | <strong>Sí</strong> |          No          | <strong>Sí</strong> |          No          |          No          |
|           Clavister NGFW (Syslog)            | <strong>Sí</strong> | <strong>Sí</strong> | <strong>Sí</strong> | <strong>Sí</strong> | <strong>Sí</strong> | <strong>Sí</strong> |
|                SonicWall (anteriormente Dell)                | <strong>Sí</strong> | <strong>Sí</strong> |          No          | <strong>Sí</strong> | <strong>Sí</strong> | <strong>Sí</strong> |
|            Digital Arts i-FILTER             | <strong>Sí</strong> | <strong>Sí</strong> | <strong>Sí</strong> | <strong>Sí</strong> | <strong>Sí</strong> | <strong>Sí</strong> |
|                  FortiGate                   |          No          | <strong>Sí</strong> |          No          | <strong>Sí</strong> | <strong>Sí</strong> | <strong>Sí</strong> |
|                 Juniper SRX                  |          No          | <strong>Sí</strong> |          No          | <strong>Sí</strong> | <strong>Sí</strong> | <strong>Sí</strong> |
|                 Juniper SSG                  |          No          | <strong>Sí</strong> | <strong>Sí</strong> | <strong>Sí</strong> | <strong>Sí</strong> | <strong>Sí</strong> |
|                  McAfee SWG                  | <strong>Sí</strong> |          No          |          No          | <strong>Sí</strong> | <strong>Sí</strong> | <strong>Sí</strong> |
|                    MS TMG                    | <strong>Sí</strong> |          No          | <strong>Sí</strong> | <strong>Sí</strong> | <strong>Sí</strong> | <strong>Sí</strong> |
|              Palo Alto Networks              |          No          | <strong>Sí</strong> | <strong>Sí</strong> | <strong>Sí</strong> | <strong>Sí</strong> | <strong>Sí</strong> |
|                    Sophos                    | <strong>Sí</strong> | <strong>Sí</strong> | <strong>Sí</strong> | <strong>Sí</strong> | <strong>Sí</strong> |          No          |
|                Squid (Common)                | <strong>Sí</strong> |          No          | <strong>Sí</strong> | <strong>Sí</strong> |          No          | <strong>Sí</strong> |
|                Squid (Native)                | <strong>Sí</strong> |          No          | <strong>Sí</strong> | <strong>Sí</strong> |          No          | <strong>Sí</strong> |
| Websense: informe de detalle de investigación (CSV) | <strong>Sí</strong> | <strong>Sí</strong> | <strong>Sí</strong> | <strong>Sí</strong> | <strong>Sí</strong> | <strong>Sí</strong> |
|    Websense: registro de actividad de Internet (CEF)    | <strong>Sí</strong> | <strong>Sí</strong> | <strong>Sí</strong> | <strong>Sí</strong> | <strong>Sí</strong> | <strong>Sí</strong> |
|                   Zscaler                    | <strong>Sí</strong> | <strong>Sí</strong> | <strong>Sí</strong> | <strong>Sí</strong> | <strong>Sí</strong> | <strong>Sí</strong> |
     


## <a name="next-steps"></a>Pasos siguientes

[Crear informes de instantáneas de Cloud Discovery](create-snapshot-cloud-discovery-reports.md)

[Configurar la carga de registros automática para informes continuos](configure-automatic-log-upload-for-continuous-reports.md)

[Trabajar con datos de Cloud Discovery](working-with-cloud-discovery-data.md)
