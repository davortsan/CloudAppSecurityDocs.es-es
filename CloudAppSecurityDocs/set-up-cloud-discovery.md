---
title: Implementar Cloud Discovery con Microsoft Cloud App Security | Microsoft Docs
description: En este tema se describe el procedimiento de configuración de Cloud Discovery para que entre en funcionamiento.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 10/14/2018
ms.topic: conceptual
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: a9b5bd8d-305b-4e93-9a4c-a4683ea09080
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: c63379dd19c8e3a62c63d4f6ace5d35478a45ff6
ms.sourcegitcommit: 82052a88acbc33893f7b9e0d10cc2e8c652ef003
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/16/2018
ms.locfileid: "49349623"
---
*Se aplica a: Microsoft Cloud App Security*


# <a name="set-up-cloud-discovery"></a>Configurar Cloud Discovery
Cloud Discovery analiza los registros de tráfico del catálogo de aplicaciones en la nube de Microsoft Cloud App Security de más de 16 000 aplicaciones en la nube que se clasifican y se puntúan en función de más de 70 factores de riesgo, a fin de proporcionar visibilidad continua del uso de la nube, Shadow IT y el riesgo que Shadow IT supone para la organización.

## <a name="snapshot-and-continuous-risk-assessment-reports"></a>Informes de instantáneas y de evaluación continua de riesgos 

Se pueden generar dos tipos de informes: 
- **Informes de instantáneas**: proporcionan visibilidad ad hoc de un conjunto de registros de tráfico que puede cargar manualmente desde los firewalls y los servidores proxy.

- **Informes continuos**: analizan todos los registros que se reenvían desde la red mediante Cloud App Security. Proporcionan una mejor visibilidad de todos los datos e identifican automáticamente los usos erróneos, ya sea mediante el motor de detección de anomalías de aprendizaje automático o mediante las directivas personalizadas que haya definido. Estos informes pueden crearse conectándose de varias maneras:
  - [Integración de ATP de Windows Defender](wdatp-integration.md): Cloud App Security se integra con Protección contra amenazas avanzada de Windows Defender (ATP) de forma nativa, para simplificar la implementación de Cloud Discovery, ampliar las capacidades de Cloud Discovery más allá de la red corporativa, y habilitar la investigación en el equipo.
  - [Recopilador de registros](discovery-docker.md): los recopiladores de registros permiten automatizar fácilmente la carga de registros desde la red. El recopilador de registros se ejecuta en la red y recibe los registros a través de Syslog o FTP.
  - [Integración de Zscaler](zscaler-integration.md): si trabaja con Cloud App Security y Zscaler, puede integrar los dos productos para mejorar la seguridad de la experiencia de Cloud Discovery. Juntos, Cloud App Security y Zscaler proporcionan una implementación fluida de Cloud Discovery, bloqueo automático de aplicaciones no autorizadas y evaluación de riesgos directamente en el portal de Zscaler.

## <a name="log-process-flow-from-raw-data-to-risk-assessment"></a>Flujo del proceso de registro: de datos sin procesar a evaluación de riesgos  
El proceso de generación de una evaluación de riesgos consta de los siguientes pasos y tarda entre unos minutos y varias horas en función de la cantidad de datos procesados.  

-   **Cargar**: se cargan los registros de tráfico web de la red en el portal.  

-   **Redistribuir**: Cloud App Security redistribuye y extrae datos de tráfico de los registros de tráfico con un analizador dedicado para cada origen de datos.  

-   **Analizar**: se analizan los datos de tráfico con el catálogo de aplicaciones en la nube para identificar más de 16 000 aplicaciones en la nube y evaluar su puntuación de riesgo. También se identifican los usuarios activos y las direcciones IP como parte del análisis.  

-   **Generar informe**: se genera un informe de evaluación de riesgos de los datos extraídos de los archivos de registro.   


>[!NOTE]
>- Los datos de los informes continuos se analizan dos veces al día.
> 


## <a name="see-also"></a>Consulta también

[Crear informes de instantáneas de Cloud Discovery](create-snapshot-cloud-discovery-reports.md)

[Configurar la carga de registros automática para informes continuos](configure-automatic-log-upload-for-continuous-reports.md)

[Trabajar con datos de Cloud Discovery](working-with-cloud-discovery-data.md)