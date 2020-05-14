---
title: 'Implementación de Cloud Discovery: Cloud App Security | Microsoft Docs'
description: En este artículo se describe el procedimiento de configuración de Cloud Discovery para que entre en funcionamiento.
author: shsagir
ms.author: shsagir
ms.service: cloud-app-security
ms.topic: conceptual
ms.date: 8/15/2019
ms.collection: M365-security-compliance
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: a4ee042c3f24fe2fa5f15fa5ce3eb2ca0f7f2be1
ms.sourcegitcommit: a693d0bc9102a8320f9933d80ab9357f449d5316
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/13/2020
ms.locfileid: "83369332"
---
# <a name="set-up-cloud-discovery"></a>Configuración de Cloud Discovery

*Se aplica a: Microsoft Cloud App Security*

Cloud Discovery analiza los registros de tráfico en el catálogo de aplicaciones en la nube de Microsoft Cloud App Security de más de 16 000 aplicaciones en la nube. Las aplicaciones se clasifican y puntuan en función de más de 80 factores de riesgo para proporcionar visibilidad continua del uso de la nube, Shadow IT y el riesgo que Shadow IT supone para su organización.

## <a name="snapshot-and-continuous-risk-assessment-reports"></a>Informes de instantáneas y de evaluación continua de riesgos

Se pueden generar dos tipos de informes:

- **Informes de instantáneas**: proporcionan visibilidad ad hoc de un conjunto de registros de tráfico que puede cargar manualmente desde los firewalls y los servidores proxy.

- **Informes continuos**: analizan todos los registros que se reenvían desde la red mediante Cloud App Security. Proporcionan una mejor visibilidad de todos los datos e identifican automáticamente los usos erróneos, ya sea mediante el motor de detección de anomalías de aprendizaje automático o mediante las directivas personalizadas que haya definido. Estos informes pueden crearse conectándose de varias maneras:

  - [Integración de ATP de Microsoft defender](wdatp-integration.md): Cloud App Security se integra con protección contra amenazas avanzada (ATP) de Microsoft defender de forma nativa para simplificar el lanzamiento de Cloud Discovery, ampliar las funcionalidades de Cloud Discovery más allá de la red corporativa y habilitar la investigación basada en equipo.
  - [Recopilador de registros](discovery-docker.md): los recopiladores de registros permiten automatizar fácilmente la carga de registros desde la red. El recopilador de registros se ejecuta en la red y recibe los registros a través de Syslog o FTP.
  - [Integración de Zscaler](zscaler-integration.md): si trabaja con Cloud App Security y Zscaler, puede integrar los dos productos para mejorar la seguridad de la experiencia de Cloud Discovery. Juntos, Cloud App Security y Zscaler proporcionan una implementación fluida de Cloud Discovery, bloqueo automático de aplicaciones no autorizadas y evaluación de riesgos directamente en el portal de Zscaler.
  - [integración de iboss](iboss-integration.md): Si trabaja con Cloud App Security y iboss, puede integrar los dos productos para mejorar su experiencia de Cloud Discovery de seguridad. Juntos, Cloud App Security y iboss proporcionan una implementación sin problemas de Cloud Discovery, el bloqueo automático de aplicaciones no autorizadas y la evaluación de riesgos directamente en el portal de iboss.

## <a name="log-process-flow-from-raw-data-to-risk-assessment"></a>Flujo del proceso de registro: de datos sin procesar a evaluación de riesgos

El proceso de generación de una evaluación de riesgos consta de los siguientes pasos. El proceso tarda desde unos minutos hasta varias horas según la cantidad de datos procesados.

- **Cargar**: se cargan los registros de tráfico web de la red en el portal.

- **Redistribuir**: Cloud App Security redistribuye y extrae datos de tráfico de los registros de tráfico con un analizador dedicado para cada origen de datos.

- **Analizar**: se analizan los datos de tráfico con el catálogo de aplicaciones en la nube para identificar más de 16 000 aplicaciones en la nube y evaluar su puntuación de riesgo. Los usuarios activos y las direcciones IP también se identifican como parte del análisis.

- **Generar informe**: se genera un informe de evaluación de riesgos de los datos extraídos de los archivos de registro.

>[!NOTE]
> Los datos de informes continuos se analizan dos veces al día.

## <a name="supported-firewalls-and-proxies"></a>Firewalls y servidores proxy compatibles<a name="supported-firewalls-and-proxies"></a>

- Barracuda - Firewall de aplicación web (W3C)
- Blue Coat Proxy SG - Registros de acceso (W3C)
- Punto de comprobación
- Cisco ASA con FirePOWER
- Firewall de Cisco ASA (en el caso de los firewalls de Cisco ASA, es necesario establecer el nivel de información en 6)
- Seguridad Web de Cisco Cloud
- Cisco FWSM
- Cisco IronPort WSA
- Cisco Meraki – Registro de direcciones URL
- Clavister NGFW (Syslog)
- ContentKeeper
- Digital Arts i-FILTER
- Forcepoint
- Fortinet Fortigate
- iboss Secure Cloud Gateway
- Juniper SRX
- Juniper SSG
- Puerta de enlace web de McAfee Secure
- Microsoft Forefront Threat Management Gateway (W3C)
- Firewall de serie Palo Alto
- Sonicwall (anteriormente Dell)
- Sophos SG
- Sophos XG
- Sophos Cyberoam
- Squid (Common)
- Squid (Native)
- Stormshield
- Websense - Soluciones de seguridad web - Informe de detalle de investigación (CSV)
- Websense - Soluciones de seguridad web - Registro de actividad de Internet (CEF)
- Zscaler

> [!NOTE]
> Cloud Discovery admite tanto direcciones IPv4 como IPv6.

Si el registro no es compatible, seleccione **Otro** como **Origen de datos** y especifique el dispositivo y el registro que está intentando cargar. El equipo de analistas de la nube de Cloud App Security examinará el registro y se le notificará si se ha agregado compatibilidad con el tipo de registro. También puede definir un analizador personalizado que coincida con el formato. Para más información, consulte [Uso de un analizador de registros personalizado](custom-log-parser.md).

Atributos de datos (según la documentación del proveedor):

| Origen de datos | Dirección URL de la aplicación de destino | IP de la aplicación de destino | Nombre de usuario | IP de origen | Tráfico total | Bytes cargados |
|----------------------------------------------|----------------------|----------------------|----------------------|----------------------|----------------------|----------------------|
| Barracuda | **Sí** | **Sí** | **Sí** | **Sí** | No | No |
| Blue Coat | **Sí** | No | **Sí** | **Sí** | **Sí** | **Sí** |
| Punto de control | No | **Sí** | No | **Sí** | No | No |
| Cisco ASA (Syslog) | No | **Sí** | No | **Sí** | **Sí** | No |
| Cisco ASA con FirePOWER | **Sí** | **Sí** | **Sí** | **Sí** | **Sí** | **Sí** |
| Seguridad Web de Cisco Cloud |**Sí**|**Sí**|**Sí**|**Sí**|**Sí**|**Sí**|
| Cisco FWSM | No | **Sí** | No | **Sí** | **Sí** | No |
| Cisco Ironport WSA | **Sí** | **Sí** | **Sí** | **Sí** | **Sí** | **Sí** |
| Cisco Meraki | **Sí** | **Sí** | No | **Sí** | No | No |
| Clavister NGFW (Syslog) | **Sí** | **Sí** | **Sí** | **Sí** | **Sí** | **Sí** |
| ContentKeeper | **Sí** | **Sí** | **Sí** | **Sí** | **Sí** | **Sí** |
| SonicWall (anteriormente Dell) | **Sí** | **Sí** | No | **Sí** | **Sí** | **Sí** |
| Digital Arts i-FILTER | **Sí** | **Sí** | **Sí** | **Sí** | **Sí** | **Sí** |
| ForcePoint LEEF |**Sí**|**Sí**|**Sí**|**Sí**|**Sí**|**Sí**|
| Nube de seguridad Web de ForcePoint |**Sí**|**Sí**|**Sí**|**Sí**|**Sí**|**Sí**|
| Fortigate | No | **Sí** | No | **Sí** | **Sí** | **Sí** |
| Fortinet FortiOS |**Sí**|**Sí**|No|**Sí**|**Sí**|**Sí**|
| iboss |**Sí**|**Sí**|**Sí**|**Sí**|**Sí**|**Sí**|
| Juniper SRX | No | **Sí** | No | **Sí** | **Sí** | **Sí** |
| Juniper SSG | No | **Sí** | **Sí** | **Sí** | **Sí** | **Sí** |
| McAfee SWG | **Sí** | No | No | **Sí** | **Sí** | **Sí** |
| MS TMG | **Sí** | No | **Sí** | **Sí** | **Sí** | **Sí** |
| Palo Alto Networks | No | **Sí** | **Sí** | **Sí** | **Sí** | **Sí** |
| Sophos | **Sí** | **Sí** | **Sí** | **Sí** | **Sí** | No |
| Squid (Common) | **Sí** | No | **Sí** | **Sí** | No | **Sí** |
| Squid (Native) | **Sí** | No | **Sí** | **Sí** | No | **Sí** |
| Stormshield | No | **Sí** | **Sí** | **Sí** | **Sí** | **Sí** |
| Websense: informe de detalle de investigación (CSV) | **Sí** | **Sí** | **Sí** | **Sí** | **Sí** | **Sí** |
| Websense - Registro de actividad de Internet (CEF) | **Sí** | **Sí** | **Sí** | **Sí** | **Sí** | **Sí** |
| Zscaler | **Sí** | **Sí** | **Sí** | **Sí** | **Sí** | **Sí** |

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Crear informes de instantáneas de Cloud Discovery](create-snapshot-cloud-discovery-reports.md)

> [!div class="nextstepaction"]
> [Configurar la carga de registros automática para informes continuos](discovery-docker.md)

> [!div class="nextstepaction"]
> [Trabajo con datos de Cloud Discovery](working-with-cloud-discovery-data.md)
