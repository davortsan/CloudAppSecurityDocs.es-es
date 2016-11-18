---
title: "Directiva de detección de anomalías de Cloud Discovery | Microsoft Docs"
description: "En este tema se proporciona información sobre cómo trabajar con directivas de detección de anomalías de Cloud Discovery."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 10/15/2016
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: eaf73af0-7610-4903-b656-8d90b1d2b18c
ms.reviewer: reutam
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 400741713d40422a3b1c7680663a572d18e9c692
ms.openlocfilehash: 132b4d296b26dd187418734b40d08ecb243692da


---

# <a name="cloud-discovery-anomaly-detection-policy"></a>Directiva de detección de anomalías de Cloud Discovery
En este artículo se proporciona información de referencia sobre directivas, se ofrecen explicaciones sobre cada tipo de directiva y se detallan los campos que se pueden configurar para cada directiva.  
  
## <a name="cloud-discovery-anomaly-detection-policy-reference"></a>Referencia de directiva de detección de anomalías de Cloud Discovery  
Una directiva de detección de anomalías de Cloud Discovery permite instalar y configurar la supervisión continua de incrementos poco habituales en el uso de la aplicación en la nube. Para ello, se tienen en cuenta los aumentos de datos descargados, los datos cargados, el número de transacciones y el número de usuarios de cada aplicación en la nube. Cada incremento se compara con el patrón de uso normal de la aplicación, según se desprende de usos anteriores. Los aumentos más acusados desencadenan alertas de seguridad.  
  
Cada directiva se compone de las siguientes partes:  
  
-   Filtros: permiten supervisar selectivamente el uso de la aplicación según un filtro de aplicación, las vistas de datos seleccionadas y una fecha de inicio seleccionada.  
  
-   Sensibilidad: permite establecer cuántas alertas debe activar la directiva.  
  
### <a name="activity-filters"></a>Filtros de actividad  
Para obtener una lista de filtros de actividad, consulte [Actividades](activity-filters.md).  
  
### <a name="apply-to"></a>Aplicar a  
El uso que se está supervisando se puede filtrar de dos maneras diferentes:  
  
-   Vistas de datos: seleccione si quiere supervisar todas las vistas de datos (valor predeterminado) o elija vistas de datos concretas para supervisarlas.  
  
    -   Al seleccionar **Todas las vistas de datos**, cada aumento del uso se compara con el patrón de uso normal, según se desprende de todas las vistas de datos.  
  
    -   Al seleccionar vistas de datos específicas, cada aumento del uso se compara con el patrón de uso normal, según se desprende de las mismas vistas de datos en las que se ha observado el aumento.  
  
-   Usuarios y direcciones IP: cada uso de la aplicación en la nube está asociado con un usuario, con una dirección IP o con ambos.  
  
    -   Si se selecciona **Usuarios**, se omitirá la asociación de uso de la aplicación con direcciones IP, si la hay.  
  
    -   Si se selecciona **Direcciones IP**, se omitirá la asociación de uso de la aplicación con usuarios, si la hay.  
  
    -   Si se selecciona **Usuarios y direcciones IP**, se tendrán en cuenta ambas asociaciones, pero se pueden generar alertas duplicadas cuando haya una correspondencia estricta entre usuarios y direcciones IP.  
  
Generar alertas solo para detectar actividades sospechosas ocurridas tras una fecha: se omitirá cualquier aumento en el uso de la aplicación antes de la fecha seleccionada. En cambio, la actividad previa a la fecha seleccionada se tendrá en cuenta a efectos de establecer el patrón de uso normal.  
  
### <a name="sensitivity"></a>Sensibilidad  
Hay dos formas de controlar el número de alertas activadas por la directiva:  
  
-   Control de sensibilidad: seleccione cuántas alertas se activan por cada 1 000 usuarios a la semana. Se activarán las alertas de las actividades con el riesgo más alto.  
  
-   Límite de alertas diarias: restrinja el número de alertas activadas en un solo día.  
  
## <a name="see-also"></a>Consulte también  
[Actividades diarias para proteger el entorno de nube](daily-activities-to-protect-your-cloud-environment.md)   
[Para obtener soporte técnico, visite la página de soporte técnico asistido de Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Los clientes Premier también pueden elegir Cloud App Security directamente desde el Portal Premier.](https://premier.microsoft.com/)  
  
  


<!--HONumber=Oct16_HO5-->


