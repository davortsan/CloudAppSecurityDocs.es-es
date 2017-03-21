---
title: "Crear una directiva de detección de anomalías de Cloud Discovery en Cloud App Security | Microsoft Docs"
description: "En este tema se proporciona información sobre cómo trabajar con directivas de detección de anomalías de Cloud Discovery."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 1/23/2017
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: eaf73af0-7610-4903-b656-8d90b1d2b18c
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 5c5d77a83d3eba40250ece02cfce4aa8f80d345d
ms.sourcegitcommit: 355226ee21981563066d637e7db0bff0d53c2da6
translationtype: HT
---
# <a name="cloud-discovery-anomaly-detection-policy"></a>Directiva de detección de anomalías de Cloud Discovery
En este artículo se proporciona información de referencia sobre directivas, se ofrecen explicaciones sobre cada tipo de directiva y se detallan los campos que se pueden configurar para cada directiva.  
  
## <a name="cloud-discovery-anomaly-detection-policy-reference"></a>Referencia de directiva de detección de anomalías de Cloud Discovery  
Una directiva de detección de anomalías de Cloud Discovery permite instalar y configurar la supervisión continua de incrementos poco habituales en el uso de la aplicación en la nube. Para ello, se tienen en cuenta los aumentos de datos descargados, los datos cargados, el número de transacciones y el número de usuarios de cada aplicación en la nube. Cada incremento se compara con el patrón de uso normal de la aplicación, según se desprende de usos anteriores. Los aumentos más acusados desencadenan alertas de seguridad.  
  
Para cada directiva puede establecer filtros que permitan supervisar selectivamente el uso de la aplicación según un filtro de aplicación, las vistas de datos seleccionadas y una fecha de inicio seleccionada. También puede establecer la sensibilidad, que le permite establecer cuántas alertas debe activar la directiva.  

Para cada directiva, establezca lo siguiente:

1. Decida si quiere basar la directiva en una plantilla, las plantillas de directiva correspondientes son la plantilla **Comportamiento anómalo de los usuarios detectados**, que envía una alerta cuando se detectan comportamientos anómalos en los usuarios y aplicaciones detectados, como grandes cantidades de datos cargados en comparación con otros usuarios, grandes transacciones de usuario en comparación con el historial del usuario. También puede seleccionar la plantilla **Comportamiento erróneo de direcciones IP detectadas**, que envía una alerta cuando se detectan comportamientos anómalos en las direcciones IP y las aplicaciones detectadas, como grandes cantidades de datos cargados en comparación con otras direcciones IP, grandes transacciones de aplicaciones en comparación con el historial de la dirección IP. 
 
2. Proporcione un **Nombre de la directiva** y una **Descripción**.  

3. Cree un filtro para las aplicaciones que quiere supervisar haciendo clic en **Agregar filtro**. Puede seleccionar una aplicación específica, una **Categoría** de aplicación o filtrar por **Nombre**, **Dominio** y **Factor de riesgo**, y hacer clic en **Guardar**.

4. En **Apply to** (Aplicar a), establezca cómo quiere que se filtre el uso. El uso que se está supervisando se puede filtrar de dos maneras diferentes:  
  
    -   Informes continuados: seleccione si quiere supervisar **All continuous reports** (Todos los informes continuados), el valor predeterminado, o elija **Specific continuous reports** (Informes continuados específicos) para supervisar.  
  
        -   Al seleccionar **All continuous reports** (Todos los informes continuados), cada aumento del uso se compara con el patrón de uso normal, según se desprende de todas las vistas de datos.  
  
        -   Al seleccionar **Specific continuous reports** (Informes continuados específicos), cada aumento del uso se compara con el patrón de uso normal, según se desprende de la misma vista de datos en la que se ha observado el aumento.  
  
    -   **Usuarios y direcciones IP**: cada uso de la aplicación en la nube está asociado con un usuario, con una dirección IP o con ambos.  
  
        -   Si se selecciona **Usuarios**, se omitirá la asociación de uso de la aplicación con direcciones IP, si la hay.  
  
        -   Si se selecciona **Direcciones IP**, se omitirá la asociación de uso de la aplicación con usuarios, si la hay.  
  
        -   Si se selecciona **Usuarios y direcciones IP** (el valor predeterminado), se tendrán en cuenta ambas asociaciones, pero se pueden generar alertas duplicadas cuando haya una correspondencia estricta entre usuarios y direcciones IP.
    -   Desencadenar alertas solo para detectar actividades sospechosas ocurridas tras una fecha: se omitirá cualquier aumento en el uso de la aplicación antes de la fecha seleccionada. En cambio, la actividad previa a la fecha seleccionada se tendrá en cuenta a efectos de establecer el patrón de uso normal.  
  
5. En **Alertas** puede establecer la sensibilidad de la alerta. Hay varias formas de controlar el número de alertas activadas por la directiva:  
  
    -   El control deslizante **Select anomaly detection sensitivity** (Seleccionar la sensibilidad de la detección de anomalías): desencadena alertas para las X actividades anómalas superiores por cada 1.000 usuarios por semana. Se activarán las alertas de las actividades con el riesgo más alto.  
  
    -   **Límite de alertas diarias**: restrinja el número de alertas activadas en un solo día. Puede seleccionar si quiere **Enviar alerta por correo electrónico**, **Enviar alerta como mensaje de texto** o ambas opciones. Los mensajes enviados por mensaje de texto se limitarán a 10 por día para la zona horaria UTC, lo que significa que el límite de 10 mensajes se restablece a medianoche en la zona horaria UTC.

    - También puede seleccionar la opción de **Usar la configuración predeterminada de la organización**, que rellena el correo electrónico **Límite de alertas diarias**, y la configuración de mensajes de texto de la configuración predeterminada de la organización. Para establecer el valor predeterminado, rellene la **Configuración de alerta** y haga clic en **Guardar esta configuración de alerta como el valor predeterminado para su organización**.

6. Haga clic en **Crear**.

7. Como con todas las directivas, puede **Editar**, **Deshabilitar** y **Habilitar** la directiva haciendo clic en los tres puntos al final de la fila en la página **Directivas**. De forma predeterminada, la directiva está habilitada después de crearla.

## <a name="see-also"></a>Consulte también  
[Actividades diarias para proteger el entorno de nube](daily-activities-to-protect-your-cloud-environment.md)   
[Para obtener soporte técnico, visite la página de soporte técnico asistido de Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Los clientes Premier también pueden elegir Cloud App Security directamente desde el Portal Premier.](https://premier.microsoft.com/)  
  
  