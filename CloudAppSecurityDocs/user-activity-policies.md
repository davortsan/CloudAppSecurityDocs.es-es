---
title: Crear directivas para controlar actividades en Cloud App Security | Microsoft Docs
description: En este tema se proporcionan instrucciones para crear y trabajar con directivas de actividad.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 4/22/2018
ms.topic: article
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 99d5fd37-d922-4269-b557-86d7f84180eb
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 87e05e1b28ef469b6f180fbd4479ac6727b22f3b
ms.sourcegitcommit: 45311f2cafef79483e40d971a4c61c7673834d96
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2018
---
*Se aplica a: Microsoft Cloud App Security*


# <a name="activity-policies"></a>Directivas de actividad
Las directivas de actividad permiten aplicar una amplia gama de procesos automatizados, con lo que se aprovechan las API del proveedor de aplicaciones. Estas directivas permiten supervisar actividades concretas realizadas por distintos usuarios o seguir niveles inesperadamente altos de un determinado tipo de actividad.  
  
Una vez que se ha establecido una directiva de detección de actividad, empieza a generar alertas, pero únicamente para las actividades que se producen después de haber creado la directiva.
  
  
## <a name="custom-alerts"></a>Alertas personalizadas  
Las directivas de actividad permiten establecer el envío de alertas personalizadas o la realización de acciones cuando se detecta actividad del usuario. Por ejemplo, si quiere que se le notifique si un usuario intenta iniciar sesión y se producen 70 errores en un minuto, o si un usuario descarga 7000 archivos o inicia sesión en Afganistán, puede establecer que se envíen alertas de actividad al usuario o a usted mismo cada vez que se produzcan estas situaciones. Incluso puede suspender el usuario hasta que tenga tiempo de investigar lo sucedido.  
  
Para crear una nueva directiva de actividad, siga este procedimiento:  
  
1.  En la consola, haga clic en **Control** seguido de **Directivas**.  
  
2.  Haga clic en **Crear directiva** y seleccione **Directiva de actividad**.  
  
     ![menú de directiva de actividad](./media/activity-policy-menu.png "menú de directiva de actividad")  
  
3.  Asigne un nombre y una descripción a la directiva. Si quiere, puede basarla en una plantilla. Para obtener más información sobre las plantillas de directiva, vea [Controlar aplicaciones en la nube con directivas](control-cloud-apps-with-policies.md).  
  
4.  Para establecer qué acciones o qué otras métricas desencadenan esta directiva, trabaje con **filtros de actividad**.  
  
5.  En **Parámetros de coincidencia de actividad**, seleccione si se desencadenará una infracción de directiva cuando una sola actividad coincida con los filtros o si solo se detectará una infracción cuando se detecte un número especificado de **actividades repetidas**.  
    Si elige **Actividad repetida**, puede establecer  **Actividades de grupo coincidentes por aplicación**. Esto desencadenará una coincidencia de directiva solo cuando se producen las actividades repetidas en la misma aplicación (por ejemplo, 5 descargas desde Box).  
  
6.  Configure las **acciones** que deben realizarse cuando se encuentra una coincidencia.  
  
Observe estos ejemplos:  
  
-   Varios inicios de sesión erróneos  
  
     Puede establecer la directiva de modo que reciba una alerta cuando se produzca un gran número de intentos de inicio de sesión erróneos durante un período de tiempo determinado relativamente corto. Para configurar una directiva de este tipo, elija el filtro de actividad apropiado en la página **Nueva directiva de actividad**.  
  
     Bajo el campo **Filtros de actividad**, configure los parámetros para los que se desencadenará la alerta.  
  
     ![ejemplo de directiva de varios intentos de inicio de sesión erróneos](./media/multiple-failed-log-on-attempts-policy-example.png "ejemplo de directiva de varios intentos de inicio de sesión erróneos")  
  
-   Frecuencia de descarga alta  
  
     Puede establecer la directiva de modo que reciba una alerta cuando se produzca un nivel de actividad de descarga inesperado o inusitado. Para configurar una directiva de este tipo, en el parámetro **Frecuencia**, elija los parámetros que desencadenen la alerta.  
  
     ![ejemplo de frecuencia de descarga alta](./media/high-download-rate-example.png "ejemplo de frecuencia de descarga alta")  
  
  
## <a name="activity-policy-reference"></a>Referencia de directiva de actividad  
En esta sección se proporciona información de referencia sobre directivas, se ofrecen explicaciones sobre cada tipo de directiva y se detallan los campos que se pueden configurar para cada directiva.  
  
Una **directiva de actividad** es una directiva basada en API que permite supervisar las actividades de la organización en la nube en función de más de 20 filtros de metadatos de archivo (incluidos el tipo de dispositivo y la ubicación). Basándose en los resultados de la directiva, se pueden generar notificaciones y se puede suspender a usuarios de la aplicación en la nube.   
Cada directiva se compone de las siguientes partes:  
  
- Filtros de actividad: permiten crear condiciones muy granulares basadas en metadatos.  
  
- Parámetros de coincidencia de actividad: permiten establecer un umbral de número de veces que se repite una actividad para que se considere que coincide con la directiva.  Especifique el número de actividades repetidas necesarias para que haya coincidencia con la directiva, por ejemplo, el establecimiento de una directiva para alertar cuando un usuario realice diez intentos de inicio de sesión incorrectos en un período de tiempo de dos minutos.  De forma predeterminada, **Parámetros de coincidencia de actividad**, genera una coincidencia para cada actividad única que cumple todos los filtros de la actividad.   
  Con **Actividad repetida** puede establecer el número de actividades repetidas, la duración del período en el que se cuentan las actividades e incluso especificar que todas las actividades las debe realizar el mismo usuario y en la misma aplicación en la nube.  
  
  
- Acciones: la directiva proporciona un conjunto de acciones de gobierno que se pueden aplicar automáticamente cuando se detectan infracciones.  
  ## <a name="see-also"></a>Consulte también  
  [Directivas de protección de datos](data-protection-policies.md)   

[Los clientes Premier también pueden elegir Cloud App Security directamente desde el Portal Premier.](https://premier.microsoft.com/)  
  
  