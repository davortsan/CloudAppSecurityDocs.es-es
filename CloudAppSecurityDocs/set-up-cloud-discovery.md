---
title: Implementar Cloud Discovery Cloud App Security | Microsoft Docs
description: En este artículo se describe el procedimiento de instalación para obtener Cloud Discovery en funcionamiento.
author: shsagir
ms.author: shsagir
ms.service: cloud-app-security
ms.topic: conceptual
ms.date: 8/15/2019
ms.collection: M365-security-compliance
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: fe21bbb39b52981d7aeba0839367d2fd54073983
ms.sourcegitcommit: 4f3883a9e85d0aaf2802b10433b221c3f1838d88
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/13/2020
ms.locfileid: "79285689"
---
# <a name="set-up-cloud-discovery"></a>Configuración de Cloud Discovery

*Se aplica a: Microsoft Cloud App Security*

Cloud Discovery analiza los registros de tráfico en el catálogo de aplicaciones en la nube de Microsoft Cloud App Security de más de 16.000 aplicaciones en la nube. Las aplicaciones se clasifican y puntuan en función de más de 80 factores de riesgo para proporcionar visibilidad continua del uso de la nube, Shadow IT y el riesgo que Shadow IT supone para su organización.

## <a name="snapshot-and-continuous-risk-assessment-reports"></a>Informes de la evaluación de riesgos continuos y de instantáneas

Hay dos tipos de informes que puede generar:

- **Informes de instantáneas** : proporciona visibilidad ad hoc de un conjunto de registros de tráfico que se cargan manualmente desde los firewalls y los servidores proxy.

- **Informes continuos** : analice todos los registros que se reenvían desde la red mediante Cloud App Security. Proporcionan una mejor visibilidad de todos los datos e identifican de forma automática el uso anómalo mediante el motor de detección de anomalías Machine Learning o mediante el uso de directivas personalizadas definidas por el usuario. Estos informes se pueden crear mediante la conexión de las siguientes maneras:

  - [Integración de ATP de Microsoft defender](wdatp-integration.md): Cloud App Security se integra con protección contra amenazas avanzada (ATP) de Microsoft defender de forma nativa para simplificar el lanzamiento de Cloud Discovery, ampliar las funcionalidades de Cloud Discovery más allá de la red corporativa y habilitar la investigación basada en equipo.
  - [Recopilador de registros](discovery-docker.md): los recopiladores de registros permiten automatizar fácilmente la carga de registros desde la red. El recopilador de registros se ejecuta en la red y recibe los registros a través de Syslog o FTP.
  - [Integración de Zscaler](zscaler-integration.md): Si trabaja con Cloud App Security y Zscaler, puede integrar los dos productos para mejorar su experiencia de Cloud Discovery de seguridad. Juntos, Cloud App Security y Zscaler proporcionan una implementación sin problemas de Cloud Discovery, el bloqueo automático de aplicaciones no autorizadas y la evaluación de riesgos directamente en el portal de Zscaler.
  - [integración de iboss](iboss-integration.md): Si trabaja con Cloud App Security y iboss, puede integrar los dos productos para mejorar su experiencia de Cloud Discovery de seguridad. Juntos, Cloud App Security y iboss proporcionan una implementación sin problemas de Cloud Discovery, el bloqueo automático de aplicaciones no autorizadas y la evaluación de riesgos directamente en el portal de iboss.

## <a name="log-process-flow-from-raw-data-to-risk-assessment"></a>Flujo del proceso de registro: de datos sin procesar a evaluación de riesgos

El proceso de generación de una evaluación de riesgos consta de los siguientes pasos. El proceso tarda entre unos minutos y varias horas en función de la cantidad de datos procesados.

- **Cargar** : los registros de tráfico web de la red se cargan en el portal.

- **Parse** – Cloud App Security analiza y extrae datos de tráfico de los registros de tráfico con un analizador dedicado para cada origen de datos.

- **Analizar** : se analizan los datos de tráfico con el catálogo de aplicaciones en la nube para identificar más de 16.000 aplicaciones en la nube y evaluar su puntuación de riesgo. Los usuarios activos y las direcciones IP también se identifican como parte del análisis.

- **Generar informe** : se genera un informe de evaluación de riesgos de los datos extraídos de los archivos de registro.

>[!NOTE]
> Los datos de informe continuos se analizan dos veces al día.

## Firewalls y servidores proxy compatibles<a name="supported-firewalls-and-proxies"></a>

- Barracuda: firewall de aplicaciones web (W3C)
- Proxy de decubrimiento azul de SG-registro de acceso (W3C)
- Check Point
- Cisco ASA con FirePOWER
- Firewall de Cisco ASA (para los firewalls de Cisco ASA, es necesario establecer el nivel de información en 6)
- Seguridad Web de Cisco Cloud
- Cisco FWSM
- Cisco IronPort WSA
- Cisco Meraki – registro de direcciones URL
- Clavister NGFW (syslog)
- ContentKeeper
- FILTRO i Digital Arts
- Forcepoint
- Fortinet FortiGate
- Puerta de enlace de nube segura de iboss
- Juniper SRX
- SSG de Juniper
- Puerta de enlace Web de McAfee Secure
- Microsoft Forefront Threat Management Gateway (W3C)
- Firewall de palo alto series
- SonicWALL (anteriormente Dell)
- Sophos SG
- Sophos XG
- Sophos Cyberoam
- Squid (común)
- Squid (nativo)
- Stormshield
- Websense-soluciones de seguridad Web-informe de detalle de investigación (CSV)
- Websense-soluciones de seguridad Web-registro de actividad de Internet (CEF)
- Zscaler

> [!NOTE]
> Cloud Discovery admite direcciones IPv4 e IPv6.

Si no se admite el registro, seleccione **otro** como **origen de datos** y especifique el dispositivo y el registro que está intentando cargar. El equipo de analistas de la nube de Cloud App Security revisará el registro y se le notificará si se agrega compatibilidad con el tipo de registro. Como alternativa, puede definir un analizador personalizado que coincida con su formato. Para obtener más información, vea [usar un analizador de registros personalizado](custom-log-parser.md).

Atributos de datos (según la documentación del proveedor):

| Origen de datos | URL de la aplicación de destino | IP de la aplicación de destino | Nombre de usuario | IP de origen | Tráfico total | Bytes cargados |
|----------------------------------------------|----------------------|----------------------|----------------------|----------------------|----------------------|----------------------|
| Barracuda | **Sí** | **Sí** | **Sí** | **Sí** | No | No |
| Capa azul | **Sí** | No | **Sí** | **Sí** | **Sí** | **Sí** |
| Punto de control | No | **Sí** | No | **Sí** | No | No |
| Cisco ASA (syslog) | No | **Sí** | No | **Sí** | **Sí** | No |
| Cisco ASA con FirePOWER | **Sí** | **Sí** | **Sí** | **Sí** | **Sí** | **Sí** |
| Seguridad Web de Cisco Cloud |**Sí**|**Sí**|**Sí**|**Sí**|**Sí**|**Sí**|
| Cisco FWSM | No | **Sí** | No | **Sí** | **Sí** | No |
| Cisco IronPort WSA | **Sí** | **Sí** | **Sí** | **Sí** | **Sí** | **Sí** |
| Cisco Meraki | **Sí** | **Sí** | No | **Sí** | No | No |
| Clavister NGFW (syslog) | **Sí** | **Sí** | **Sí** | **Sí** | **Sí** | **Sí** |
| ContentKeeper | **Sí** | **Sí** | **Sí** | **Sí** | **Sí** | **Sí** |
| SonicWall (anteriormente Dell) | **Sí** | **Sí** | No | **Sí** | **Sí** | **Sí** |
| FILTRO i Digital Arts | **Sí** | **Sí** | **Sí** | **Sí** | **Sí** | **Sí** |
| ForcePoint LEEF |**Sí**|**Sí**|**Sí**|**Sí**|**Sí**|**Sí**|
| Nube de seguridad Web de ForcePoint |**Sí**|**Sí**|**Sí**|**Sí**|**Sí**|**Sí**|
| FortiGate | No | **Sí** | No | **Sí** | **Sí** | **Sí** |
| Fortinet FortiOS |**Sí**|**Sí**|No|**Sí**|**Sí**|**Sí**|
| iboss |**Sí**|**Sí**|**Sí**|**Sí**|**Sí**|**Sí**|
| Juniper SRX | No | **Sí** | No | **Sí** | **Sí** | **Sí** |
| SSG de Juniper | No | **Sí** | **Sí** | **Sí** | **Sí** | **Sí** |
| McAfee SWG | **Sí** | No | No | **Sí** | **Sí** | **Sí** |
| MS TMG | **Sí** | No | **Sí** | **Sí** | **Sí** | **Sí** |
| Palo Alto Networks | No | **Sí** | **Sí** | **Sí** | **Sí** | **Sí** |
| Sophos | **Sí** | **Sí** | **Sí** | **Sí** | **Sí** | No |
| Squid (común) | **Sí** | No | **Sí** | **Sí** | No | **Sí** |
| Squid (nativo) | **Sí** | No | **Sí** | **Sí** | No | **Sí** |
| Stormshield | No | **Sí** | **Sí** | **Sí** | **Sí** | **Sí** |
| Websense-informe detallado de la investigación (CSV) | **Sí** | **Sí** | **Sí** | **Sí** | **Sí** | **Sí** |
| Websense-registro de actividad de Internet (CEF) | **Sí** | **Sí** | **Sí** | **Sí** | **Sí** | **Sí** |
| Zscaler | **Sí** | **Sí** | **Sí** | **Sí** | **Sí** | **Sí** |

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Crear informes de instantáneas de Cloud Discovery](create-snapshot-cloud-discovery-reports.md)

> [!div class="nextstepaction"]
> [Configurar la carga de registros automática para informes continuos](configure-automatic-log-upload-for-continuous-reports.md)

> [!div class="nextstepaction"]
> [Trabajar con datos de Cloud Discovery](working-with-cloud-discovery-data.md)
