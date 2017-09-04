---
title: Implementar Cloud Discovery con Cloud App Security | Microsoft Docs
description: "En este tema se describe el procedimiento de configuración de Cloud Discovery para que entre en funcionamiento."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 9/03/2017
ms.topic: get-started-article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: a9b5bd8d-305b-4e93-9a4c-a4683ea09080
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: be08317610ec1f32c78be9c942c64bba7bbdcd0f
ms.sourcegitcommit: de133f251ceab10d9c2306dd76e75a68db206743
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/03/2017
---
# <a name="set-up-cloud-discovery"></a>Configurar Cloud Discovery
Cloud Discovery analiza los registros de tráfico del catálogo de aplicaciones en la nube de Cloud App Security de más de 15 000 aplicaciones en la nube que se clasifican y se puntúan en función de más de 60 factores de riesgo, a fin de proporcionar visibilidad continua del uso de la nube, Shadow IT y el riesgo que Shadow IT supone para la organización.
 
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
Por ejemplo, el formato de registro estándar del **firewall de Cisco ASA** no contiene la **cantidad de bytes cargados por transacción** ni el **nombre de usuario**, y no contiene la **dirección URL de destino** (solo la IP de destino).
Por lo tanto, estos atributos no se mostrarán en los datos de Cloud Discovery de estos registros, y la visibilidad de las aplicaciones en la nube será limitada. En el caso de los firewalls de Cisco ASA, es necesario establecer el nivel de información en 6. 
 

Para generar correctamente un informe de Cloud Discovery, los registros de tráfico deben cumplir las condiciones siguientes:
1.  Se admite el origen de datos (consulte la lista siguiente).
2.  El formato de registro coincide con el formato estándar esperado (esto se comprobará después de la carga mediante la herramienta de registro).
3.  Los eventos no tienen más de 90 días.
4.  El archivo de registro es válido e incluye información sobre el tráfico saliente.
 


## <a name="supported-firewalls-and-proxies"></a>Firewalls y servidores proxy compatibles

- Barracuda - Web App Firewall (W3C)
- Blue Coat Proxy SG - registros de acceso (W3C)
- Check Point
- Firewall de Cisco ASA (en el caso de los firewalls de Cisco ASA, es necesario establecer el nivel de información en 6)
- Cisco IronPort WSA
- Cisco ScanSafe
- Cisco Meraki – Registro de direcciones URL
- Clavister NGFW (Syslog)
- Dell Sonicwall
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

Si el registro no es compatible, seleccione **Otro** como **Origen de datos** y especifique el dispositivo y el registro que está intentando cargar. El equipo de analistas de la nube de Cloud App Security examinará el registro y se le notificará si se ha agregado compatibilidad con el tipo de registro. También puede definir un analizador personalizado que coincida con el formato. Para obtener más información, consulte [Uso del analizador de registros personalizado](custom-log-parser.md).


Atributos de datos (según la documentación del proveedor):

|Origen de datos|Dirección URL de la aplicación de destino|IP de la aplicación de destino|Nombre de usuario|IP de origen|Tráfico total|Bytes cargados|
|----|----|----|-----|----|----|----|
|Barracuda|**Sí**|**Sí**|**Sí**|**Sí**|No|No|
|Blue Coat|**Sí**|No|**Sí**|**Sí**|**Sí**|**Sí**|
|Checkpoint|No|**Sí**|No|**Sí**|No|No|
|Cisco ASA|No|**Sí**|No|**Sí**|**Sí**|No|
|Cisco FWSM|No|**Sí**|No|**Sí**|**Sí**|No|
|Cisco Ironport WSA|**Sí**|**Sí**|**Sí**|**Sí**|**Sí**|**Sí**|
|Cisco Meraki|**Sí**|**Sí**|No|**Sí**|No|No||Cisco Scansafe|**Sí**|No|**Sí**|**Sí**|**Sí**|**Sí**|
|Clavister NGFW (Syslog)|**Sí**|**Sí**|**Sí**|**Sí**|**Sí**|**Sí**|
|Dell SonicWall|**Sí**|**Sí**|No|**Sí**|**Sí**|**Sí**|
|FortiGate|No|**Sí**|No|**Sí**|**Sí**|**Sí**|
|Juniper SRX|No|**Sí**|No|**Sí**|**Sí**|**Sí**|
|Juniper SSG|No|**Sí**|No|**Sí**|**Sí**|**Sí**|
|McAfee SWG|**Sí**|No|No|**Sí**|**Sí**|**Sí**|
|MS TMG|**Sí**|No|**Sí**|**Sí**|**Sí**|**Sí**|
|Palo Alto Networks|**Sí**|**Sí**|**Sí**|**Sí**|**Sí**|**Sí**|
|Sophos|**Sí**|**Sí**|**Sí**|**Sí**|**Sí**|No|
|Squid (Common)|**Sí**|No|**Sí**|**Sí**|No|**Sí**|
|Squid (Native)|**Sí**|No|**Sí**|**Sí**|No|**Sí**|
|Websense: informe de detalle de investigación (CSV)|**Sí**|**Sí**|**Sí**|**Sí**|**Sí**|**Sí**|
|Websense: registro de actividad de Internet (CEF)|**Sí**|**Sí**|**Sí**|**Sí**|**Sí**|**Sí**|
|Zscaler|**Sí**|**Sí**|**Sí**|**Sí**|**Sí**|**Sí**|



## <a name="see-also"></a>Vea también
 
[Crear informes de instantáneas de Cloud Discovery](create-snapshot-cloud-discovery-reports.md)

[Configurar la carga de registros automática para informes continuos](configure-automatic-log-upload-for-continuous-reports.md)

[Trabajar con datos de Cloud Discovery](working-with-cloud-discovery-data.md)