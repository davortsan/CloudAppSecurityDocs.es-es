---
title: Implementación de Cloud Discovery
description: En este artículo se describe el procedimiento de configuración de Cloud Discovery para que entre en funcionamiento.
ms.date: 08/09/2020
ms.topic: how-to
ms.openlocfilehash: e4ac4ce0e6148ca37c4c666b94da6779578ca77a
ms.sourcegitcommit: 16a65ab2c8ca778d0b3cfa97b847af4c812363b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/03/2021
ms.locfileid: "97855241"
---
# <a name="set-up-cloud-discovery"></a>Configuración de Cloud Discovery

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Cloud Discovery analiza los registros de tráfico en el catálogo de aplicaciones en la nube de Microsoft Cloud App Security de más de 16 000 aplicaciones en la nube. Las aplicaciones se clasifican y puntuan en función de más de 80 factores de riesgo para proporcionar visibilidad continua del uso de la nube, Shadow IT y el riesgo que Shadow IT supone para su organización.

## <a name="snapshot-and-continuous-risk-assessment-reports"></a>Informes de instantáneas y de evaluación continua de riesgos

Puede generar los siguientes tipos de informes:

- **Informes de instantáneas**: proporcionan visibilidad ad hoc de un conjunto de registros de tráfico que puede cargar manualmente desde los firewalls y los servidores proxy.

- **Informes continuos**: analizan todos los registros que se reenvían desde la red mediante Cloud App Security. Proporcionan una mejor visibilidad de todos los datos e identifican automáticamente los usos erróneos, ya sea mediante el motor de detección de anomalías de aprendizaje automático o mediante las directivas personalizadas que haya definido. Estos informes pueden crearse conectándose de varias maneras:

  - [**Microsoft defender for Endpoint Integration**](mde-integration.md): Cloud App Security se integra con defender para el punto de conexión de forma nativa, para simplificar el lanzamiento de Cloud Discovery, ampliar las funcionalidades de Cloud Discovery más allá de la red corporativa y habilitar la investigación basada en el equipo.
  - [**Recopilador de registros**](discovery-docker.md): los recopiladores de registros permiten automatizar fácilmente la carga de registros desde la red. El recopilador de registros se ejecuta en la red y recibe los registros a través de Syslog o FTP.
  - **Puerta de enlace web segura (SWG)**: Si trabaja con Cloud App Security y uno de los siguientes SWGs, puede integrar los productos para mejorar su experiencia de Cloud Discovery de seguridad. Juntos, Cloud App Security y SWGs proporcionan una implementación sin problemas de Cloud Discovery, el bloqueo automático de aplicaciones no autorizadas y la evaluación de riesgos directamente en el portal de SWG.
    - [Integración de Zscaler](zscaler-integration.md)
    - [integración de iboss](iboss-integration.md)
    - [Integración de Corrata](corrata-integration.md)
    - [Integración de seguridad de Menlo](menlo-integration.md)

- **[API de Cloud Discovery](api-discovery.md)** : Use la api de Cloud Discovery de Cloud App Security para automatizar la carga del registro de tráfico y obtener análisis automatizado de la Cloud Discovery de informes y riesgos. También puede usar la API para [generar scripts de bloqueo](api-discovery-script.md) y optimizar los controles de aplicación directamente en el dispositivo de red.

## <a name="log-process-flow-from-raw-data-to-risk-assessment"></a>Flujo del proceso de registro: de datos sin procesar a evaluación de riesgos

El proceso de generación de una evaluación de riesgos consta de los siguientes pasos. El proceso tarda desde unos minutos hasta varias horas según la cantidad de datos procesados.

- **Cargar**: se cargan los registros de tráfico web de la red en el portal.

- **Redistribuir**: Cloud App Security redistribuye y extrae datos de tráfico de los registros de tráfico con un analizador dedicado para cada origen de datos.

- **Analizar**: se analizan los datos de tráfico con el catálogo de aplicaciones en la nube para identificar más de 16 000 aplicaciones en la nube y evaluar su puntuación de riesgo. Los usuarios activos y las direcciones IP también se identifican como parte del análisis.

- **Generar informe**: se genera un informe de evaluación de riesgos de los datos extraídos de los archivos de registro.

>[!NOTE]
> Los datos de informe continuos se analizan cuatro veces al día.

## <a name="supported-firewalls-and-proxies"></a>Firewalls y servidores proxy compatibles <a name="supported-firewalls-and-proxies"></a>

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
- Corrata
- Digital Arts i-FILTER
- Forcepoint
- Fortinet Fortigate
- iboss Secure Cloud Gateway
- Juniper SRX
- Juniper SSG
- Puerta de enlace web de McAfee Secure
- Seguridad de Menlo (CEF)
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
- WatchGuard
- Zscaler

> [!NOTE]
> Cloud Discovery admite tanto direcciones IPv4 como IPv6.

Si el registro no es compatible, o si está usando un formato de registro recién publicado de uno de los orígenes de datos admitidos y se produce un error en la carga, seleccione **otro** como **origen de datos** y especifique el dispositivo y el registro que está intentando cargar. El equipo de analistas de la nube de Cloud App Security examinará el registro y se le notificará si se ha agregado compatibilidad con el tipo de registro. También puede definir un analizador personalizado que coincida con el formato. Para más información, consulte [Uso de un analizador de registros personalizado](custom-log-parser.md).

> [!NOTE]
> Es posible que la siguiente lista de los dispositivos compatibles no funcione con los formatos de registro publicados recientemente. Si usa un formato recién lanzado y se produce un error en la carga, [use un analizador de registros personalizado](custom-log-parser.md) y, si es necesario, abra un caso de soporte técnico.

Atributos de datos (según la documentación del proveedor):

| Origen de datos | Dirección URL de la aplicación de destino | IP de la aplicación de destino | Nombre de usuario | IP de origen | Tráfico total | Bytes cargados |
|----------------------------------------------|----------------------|----------------------|----------------------|----------------------|----------------------|----------------------|
| Barracuda | **Sí** | **Sí** | **Sí** | **Sí** | No | No |
| Blue Coat | **Sí** | No | **Sí** | **Sí** | **Sí** | **Sí** |
| Punto de comprobación | No | **Sí** | No | **Sí** | No | No |
| Cisco ASA (Syslog) | No | **Sí** | No | **Sí** | **Sí** | No |
| Cisco ASA con FirePOWER | **Sí** | **Sí** | **Sí** | **Sí** | **Sí** | **Sí** |
| Seguridad Web de Cisco Cloud |**Sí**|**Sí**|**Sí**|**Sí**|**Sí**|**Sí**|
| Cisco FWSM | No | **Sí** | No | **Sí** | **Sí** | No |
| Cisco Ironport WSA | **Sí** | **Sí** | **Sí** | **Sí** | **Sí** | **Sí** |
| Cisco Meraki | **Sí** | **Sí** | No | **Sí** | No | No |
| Clavister NGFW (Syslog) | **Sí** | **Sí** | **Sí** | **Sí** | **Sí** | **Sí** |
| ContentKeeper | **Sí** | **Sí** | **Sí** | **Sí** | **Sí** | **Sí** |
| Corrata | **Sí** | **Sí** | **Sí** | **Sí** | **Sí** | **Sí** |
| SonicWall (anteriormente Dell) | **Sí** | **Sí** | No | **Sí** | **Sí** | **Sí** |
| Digital Arts i-FILTER | **Sí** | **Sí** | **Sí** | **Sí** | **Sí** | **Sí** |
| ForcePoint LEEF |**Sí**|**Sí**|**Sí**|**Sí**|**Sí**|**Sí**|
| Nube de seguridad Web de ForcePoint\* |**Sí**|**Sí**|**Sí**|**Sí**|**Sí**|**Sí**|
| Fortigate | No | **Sí** | No | **Sí** | **Sí** | **Sí** |
| Fortinet FortiOS |**Sí**|**Sí**|No|**Sí**|**Sí**|**Sí**|
| iboss |**Sí**|**Sí**|**Sí**|**Sí**|**Sí**|**Sí**|
| Juniper SRX | No | **Sí** | No | **Sí** | **Sí** | **Sí** |
| Juniper SSG | No | **Sí** | **Sí** | **Sí** | **Sí** | **Sí** |
| McAfee SWG | **Sí** | No | No | **Sí** | **Sí** | **Sí** |
| Seguridad de Menlo (CEF) | **Sí** | **Sí** | **Sí** | **Sí** | **Sí** | **Sí** |
| MS TMG | **Sí** | No | **Sí** | **Sí** | **Sí** | **Sí** |
| Palo Alto Networks | No | **Sí** | **Sí** | **Sí** | **Sí** | **Sí** |
| Sophos | **Sí** | **Sí** | **Sí** | **Sí** | **Sí** | No |
| Squid (Common) | **Sí** | No | **Sí** | **Sí** | **Sí** | No |
| Squid (Native) | **Sí** | No | **Sí** | **Sí** | No | No |
| Stormshield | No | **Sí** | **Sí** | **Sí** | **Sí** | **Sí** |
| Websense: informe de detalle de investigación (CSV) | **Sí** | **Sí** | **Sí** | **Sí** | **Sí** | **Sí** |
| Websense - Registro de actividad de Internet (CEF) | **Sí** | **Sí** | **Sí** | **Sí** | **Sí** | **Sí** |
| WatchGuard | **Sí** | **Sí** | **Sí** | **Sí** | **Sí** | **Sí** |
| Zscaler | **Sí** | **Sí** | **Sí** | **Sí** | **Sí** | **Sí** |

\* No se admiten las versiones 8,5 y posteriores de Forcepoint Web Security Cloud

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Crear informes de instantáneas de Cloud Discovery](create-snapshot-cloud-discovery-reports.md)

> [!div class="nextstepaction"]
> [Configurar la carga de registros automática para informes continuos](discovery-docker.md)

> [!div class="nextstepaction"]
> [Trabajo con datos de Cloud Discovery](working-with-cloud-discovery-data.md)
