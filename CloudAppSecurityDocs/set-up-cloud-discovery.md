---
title: Implementar Cloud Discovery con Microsoft Cloud App Security | Microsoft Docs
description: En este tema se describe el procedimiento de configuración de Cloud Discovery para que entre en funcionamiento.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 4/22/2017
ms.topic: get-started-article
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: a9b5bd8d-305b-4e93-9a4c-a4683ea09080
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 3daf04f3caa2541bacafe6be33c7f9714b1dda71
ms.sourcegitcommit: 45311f2cafef79483e40d971a4c61c7673834d96
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2018
---
*Se aplica a: Microsoft Cloud App Security*


# <a name="set-up-cloud-discovery"></a>Configurar Cloud Discovery
Cloud Discovery analiza los registros de tráfico del catálogo de aplicaciones en la nube de Microsoft Cloud App Security de más de 15 000 aplicaciones en la nube que se clasifican y se puntúan en función de más de 60 factores de riesgo, a fin de proporcionar visibilidad continua del uso de la nube, Shadow IT y el riesgo que Shadow IT supone para la organización.

## <a name="snapshot-and-continuous-risk-assessment-reports"></a>Informes de instantáneas y de evaluación continua de riesgos 

Se pueden generar dos tipos de informes: 
- **Informes de instantáneas**: proporcionan visibilidad ad hoc de un conjunto de registros de tráfico que puede cargar manualmente desde los firewalls y los servidores proxy.

- **Informes continuos**: analizan todos los registros que se reenvían desde la red mediante el recopilador de registros de Cloud App Security. Proporcionan una mejor visibilidad de todos los datos e identifican automáticamente los usos erróneos, ya sea mediante el motor de detección de anomalías de aprendizaje automático o mediante las directivas personalizadas que haya definido.

## <a name="log-process-flow-from-raw-data-to-risk-assessment"></a>Flujo del proceso de registro: de datos sin procesar a evaluación de riesgos  
El proceso de generación de una evaluación de riesgos consta de los siguientes pasos y tarda entre unos minutos y varias horas en función de la cantidad de datos procesados.  

-   **Cargar**: se cargan los registros de tráfico web de la red en el portal.  

-   **Redistribuir**: Cloud App Security redistribuye y extrae datos de tráfico de los registros de tráfico con un analizador dedicado para cada origen de datos.  

-   **Analizar**: se analizan los datos de tráfico con el catálogo de aplicaciones en la nube para identificar más de 15 000 aplicaciones en la nube y evaluar su puntuación de riesgo. También se identifican los usuarios activos y las direcciones IP como parte del análisis.  

-   **Generar informe**: se genera un informe de evaluación de riesgos de los datos extraídos de los archivos de registro.   


>[!NOTE]
>- Los datos de los informes continuos se analizan dos veces al día.
>- El recopilador de registros comprime los datos antes de que se carguen. El tráfico saliente en el recopilador de registros constituirá un 10 % del tamaño de los registros de tráfico que recibe. 

## <a name="using-traffic-logs-for-cloud-discovery"></a>Uso de registros de tráfico para Cloud Discovery
Cloud Discovery usa los datos de los registros de tráfico. Cuanto más detallado sea el registro, mejor visibilidad se logrará. Cloud Discovery requiere que los datos de tráfico de web tengan los siguientes atributos:
- Fecha de la transacción
- IP de origen
- Usuario de origen: altamente recomendado
- Dirección IP de destino
- Dirección URL de destino: **recomendado** (las direcciones URL proporcionan una mayor precisión para la detección de aplicaciones en la nube que las direcciones IP)
- Cantidad total de datos (la información de datos es muy valiosa)
- Cantidad de datos cargados o descargados (proporciona información sobre los patrones de uso de las aplicaciones en la nube)
- Acción realizada (permitido/bloqueado)

Cloud Discovery no puede mostrar ni analizar los atributos que no estén incluidos en los registros.
Por ejemplo, el formato de registro estándar del **firewall de Cisco ASA** no contiene la **cantidad de bytes cargados por transacción** ni el **nombre de usuario**, y tampoco contiene la **dirección URL de destino** (solo la IP de destino).
Por lo tanto, estos atributos no se mostrarán en los datos de Cloud Discovery de estos registros, y la visibilidad de las aplicaciones en la nube será limitada. En el caso de los firewalls de Cisco ASA, es necesario establecer el nivel de información en 6. 


Para generar correctamente un informe de Cloud Discovery, los registros de tráfico deben cumplir las condiciones siguientes:
1.  Se admite el origen de datos (consulte la lista siguiente).
2.  El formato de registro coincide con el formato estándar esperado (esto se comprobará después de la carga mediante la herramienta de registro).
3.  Los eventos no tienen más de 90 días.
4.  El archivo de registro es válido e incluye información sobre el tráfico saliente.



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
- Dell Sonicwall
- Digital Arts i-FILTER
- Fortinet Fortigate
- Juniper SRX
- Juniper SSG
- McAfee Secure Web Gateway
- Microsoft Forefront Threat Management Gateway (W3C)
- Firewalls de la serie Palo Alto
- Sophos SG
- Sophos Cyberoam
- Squid (Common)
- Squid (Native)
- Websense - Web Security Solutions - Investigative detail report (CSV)
- Websense - Web Security Solutions - Internet activity log (CEF)
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
|                Dell SonicWall                | <strong>Sí</strong> | <strong>Sí</strong> |          No          | <strong>Sí</strong> | <strong>Sí</strong> | <strong>Sí</strong> |
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

## <a name="see-also"></a>Consulta también

[Crear informes de instantáneas de Cloud Discovery](create-snapshot-cloud-discovery-reports.md)

[Configurar la carga de registros automática para informes continuos](configure-automatic-log-upload-for-continuous-reports.md)

[Trabajar con datos de Cloud Discovery](working-with-cloud-discovery-data.md)