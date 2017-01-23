---
title: Implementar Cloud Discovery | Microsoft Docs
description: "En este tema se describe el procedimiento de configuración de Cloud Discovery para que entre en funcionamiento."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 12/26/2016
ms.topic: get-started-article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: a9b5bd8d-305b-4e93-9a4c-a4683ea09080
ms.reviewer: reutam
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 98b16c96c31039248bdfbe57f980b3ae6a26a7de
ms.openlocfilehash: 3c722ac79fa124193655ca053c713f3d6edc7017


---

# <a name="set-up-cloud-discovery"></a>Configurar Cloud Discovery
Cloud Discovery analiza los registros de tráfico del catálogo de aplicaciones en la nube de Cloud App Security de más de 13 000 aplicaciones en la nube que se clasifican y se puntúan en función de más de 50 atributos, a fin de proporcionar visibilidad continua del uso de la nube, Shadow IT y el riesgo que Shadow IT supone para la organización.
El **catálogo de aplicaciones en la nube** evalúa el riesgo de las aplicaciones en la nube en función de certificaciones normativas, estándares del sector y procedimientos recomendados. En el catálogo de aplicaciones en la nube se ejecutan cuatro procesos complementarios para mantenerlo actualizado:
1.  Extracción de datos automatizada directamente desde la aplicación en la nube (para atributos como el cumplimiento de SOC 2).
2.  Extracción de datos automatizada avanzada mediante algoritmos de Cloud App Security (para atributos como encabezados de seguridad HTTP).
3.  Análisis continuo por parte del equipo de analistas de la nube de Cloud App Security (para atributos como el cifrado en reposo).
4.  Solicitudes de revisión de los clientes, según las solicitudes de envío de clientes para realizar cambios en el catálogo de aplicaciones en la nube. Todas las solicitudes se someten al examen del equipo de analistas de la nube y se actualizan en función de sus conclusiones.
  
## <a name="cloud-discovery-data-anonymization"></a>Anonimización de datos de Cloud Discovery

La anonimización de datos de Cloud Discovery le permite proteger la privacidad del usuario. Una vez que el registro de datos se ha cargado en el portal de Cloud App Security, se depura el registro y se reemplaza toda la información de nombres de usuario con nombres de usuario cifrados. De este modo, todas las actividades de la nube se mantienen anónimas. Para más información, vea [Cloud Discovery anonymization](cloud-discovery-anonymizer.md) (Anonimización de Cloud Discovery).

## <a name="snapshot-and-continuous-risk-assessment-reports"></a>Informes de instantáneas y de evaluación continua de riesgos 

Se pueden generar dos tipos de informes: 
- **Informes de instantáneas**: proporcionan visibilidad ad hoc de un conjunto de registros de tráfico que puede cargar manualmente desde los firewalls y los servidores proxy.
 
- **Informes continuos**: analizan todos los registros que se reenvían desde la red mediante el recopilador de registros de Cloud App Security. Proporcionan una mejor visibilidad de todos los datos e identifican automáticamente los usos erróneos, ya sea mediante el motor de detección de anomalías de aprendizaje automático o mediante las directivas personalizadas que haya definido.
 
## <a name="log-process-flow-from-raw-data-to-risk-assessment"></a>Flujo del proceso de registro: de datos sin procesar a evaluación de riesgos  
El proceso de generación de una evaluación de riesgos consta de los siguientes pasos y tarda entre unos minutos y varias horas en función de la cantidad de datos procesados.  
  
-   **Cargar**: se cargan los registros de tráfico web de la red en el portal.  
  
-   **Redistribuir**: Cloud App Security redistribuye y extrae datos de tráfico de los registros de tráfico con un analizador dedicado para cada origen de datos.  
  
-   **Analizar**: se analizan los datos de tráfico con el catálogo de aplicaciones en la nube para identificar más de 13.000 aplicaciones en la nube y evaluar su puntuación de riesgo. También se identifican los usuarios activos y las direcciones IP como parte del análisis.  
  
-   **Generar informe**: se genera un informe de evaluación de riesgos de los datos extraídos de los archivos de registro.   
 
 
>[!NOTE]
>Los datos de los informes continuos se analizan dos veces al día.
 
## <a name="using-traffic-logs-for--cloud-discovery"></a>Uso de registros de tráfico para Cloud Discovery
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
Por lo tanto, estos atributos se mostrarán en los datos de Cloud Discovery de estos registros y la visibilidad de las aplicaciones en la nube será limitada. En el caso de los firewalls de Cisco ASA, es necesario establecer el nivel de información en 6. 
 

Para generar correctamente un informe de Cloud Discovery, los registros de tráfico deben cumplir las condiciones siguientes:
1.  Se admite el origen de datos (consulte la lista siguiente).
2.  El formato de registro coincide con el formato estándar esperado (esto se comprobará después de la carga mediante la herramienta de registro).
3.  Los eventos no tienen más de 90 días.
4.  El archivo de registro es válido e incluye información sobre el tráfico saliente.
 
## <a name="supported-firewalls-and-proxies"></a>Firewalls y servidores proxy compatibles
- Blue Coat Proxy SG - registros de acceso (W3C)
- Check Point
- Firewall de Cisco ASA (en el caso de los firewalls de Cisco ASA, es necesario establecer el nivel de información en 6)
- Cisco IronPort WSA
- Cisco ScanSafe
- Cisco Merkai (registro de direcciones URL)
- Dell Sonicwall
- Fortiner Fortigate
- Juniper SRX
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


Si el registro no es compatible, seleccione **Otro** como **Origen de datos** y especifique el dispositivo y el registro que está intentando cargar. El equipo de analistas de la nube de Cloud App Security examinará el registro y se le notificará si se ha agregado compatibilidad con el tipo de registro. 


Atributos de datos (según la documentación del proveedor):

|Origen de datos|Dirección URL de la aplicación de destino|IP de la aplicación de destino|Nombre de usuario|IP de origen|Tráfico total|Bytes cargados|
|----|----|----|-----|----|----|----|
|Blue Coat|**Sí**|No|**Sí**|**Sí**|**Sí**|**Sí**|
|Checkpoint|No|**Sí**|No|**Sí**|No|No|
|Cisco ASA|No|**Sí**|No|**Sí**|**Sí**|No|
|Cisco FWSM|No|**Sí**|No|**Sí**|**Sí**|No|
|Cisco Ironport WSA|**Sí**|**Sí**|**Sí**|**Sí**|**Sí**|**Sí**|
|Cisco ScanSafe|**Sí**|No|**Sí**|**Sí**|**Sí**|**Sí**|
|Dell SonicWall|**Sí**|**Sí**|No|**Sí**|**Sí**|**Sí**|
|FortiGate|No|**Sí**|No|**Sí**|**Sí**|**Sí**|
|Juniper SRX|No|**Sí**|No|**Sí**\*|**Sí**|**Sí**|
|McAfee SWG|**Sí**|No|No|**Sí**|**Sí**|**Sí**|
|Meraki|**Sí**|**Sí**|No|**Sí**|No|No|
|MS TMG|**Sí**|No|**Sí**|**Sí**|**Sí**|**Sí**|
|Palo Alto Networks|**Sí**|**Sí**|**Sí**|**Sí**\*|**Sí**|**Sí**|
|Sophos|**Sí**|**Sí**|**Sí**|**Sí**|**Sí**|No|
|Websense: informe de detalle de investigación (CSV)|**Sí**|No|No|**Sí**|No|No|
|Websense: registro de actividad de Internet (CEF)|**Sí**|**Sí**|**Sí**|**Sí**|**Sí**|**Sí**|
|Zscaler|**Sí**|No|**Sí**|No|**Sí**|No|

\* Cloud Discovery es compatible con IPv6.

## <a name="see-also"></a>Vea también
 
[Crear informes de instantáneas de Cloud Discovery](create-snapshot-cloud-discovery-reports.md)

[Configurar la carga de registros automática para informes continuos](configure-automatic-log-upload-for-continuous-reports.md)

[Trabajar con datos de Cloud Discovery](working-with-cloud-discovery-data.md)
  
  


<!--HONumber=Jan17_HO2-->


