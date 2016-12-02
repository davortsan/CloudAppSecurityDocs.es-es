---
title: Directivas de actividad | Microsoft Docs
description: En este tema se proporcionan instrucciones para crear y trabajar con directivas de actividad.
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 11/27/2016
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: 99d5fd37-d922-4269-b557-86d7f84180eb
ms.reviewer: reutam
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 9565d8a51e4c06963861d9dfaef9595944bda1ff
ms.openlocfilehash: 68961bf66a0c0bb3b668e681502ccf10bc673197


---

# <a name="activity-policies"></a>Directivas de actividad
Las directivas de actividad permiten aplicar una amplia gama de procesos automatizados, con lo que se aprovechan las API del proveedor de aplicaciones. Estas directivas permiten supervisar actividades concretas realizadas por distintos usuarios o seguir niveles inesperadamente altos de un determinado tipo de actividad.  
  
Una vez que se ha establecido una directiva de detección de actividad, empieza a generar alertas, pero únicamente para las actividades que se producen después de haber creado la directiva.
  
  
## <a name="custom-alerts"></a>Alertas personalizadas  
Las directivas de actividad permiten establecer el envío de alertas personalizadas o la realización de acciones cuando se detecta actividad del usuario. Por ejemplo, si quiere que se le notifique si un usuario intenta iniciar sesión y se producen 70 errores en un minuto, o si un usuario descarga 7000 archivos o inicia sesión en Afganistán, puede establecer que se envíen alertas de actividad al usuario o a usted mismo cada vez que se produzcan estas situaciones. Incluso puede suspender el usuario hasta que tenga tiempo de investigar lo sucedido.  
  
Para crear una nueva directiva de actividad, siga este procedimiento:  
  
1.  En la consola, haga clic en **Control** seguido de **Directivas**.  
  
2.  Haga clic en **Crear directiva** y seleccione **Directiva de actividad**.  
  
     ![menú de directiva de actividad](./media/activity-policy-menu.png "activity policy menu")  
  
3.  Asigne un nombre y una descripción a la directiva. Si quiere, puede basarla en una plantilla. Para obtener más información sobre las plantillas de directiva, vea [Controlar aplicaciones en la nube con directivas](control-cloud-apps-with-policies.md).  
  
4.  Para establecer qué acciones o qué otras métricas desencadenan esta directiva, trabaje con **filtros de actividad**.  
  
5.  En **Parámetros de coincidencia de actividad**, seleccione si se desencadenará una infracción de directiva cuando una sola actividad coincida con los filtros o si solo se detectará una infracción cuando se detecte un número especificado de **actividades repetidas**.  
    Si elige **Actividad repetida**, puede establecer ** Actividades de grupo coincidentes por aplicación**. Esto desencadenará una coincidencia de directiva solo cuando se producen las actividades repetidas en la misma aplicación (por ejemplo, 5 descargas desde Box).  
  
6.  Configure las **acciones** que deben realizarse cuando se encuentra una coincidencia.  
  
Observe estos ejemplos:  
  
-   Varios inicios de sesión erróneos  
  
     Puede establecer la directiva de modo que reciba una alerta cuando se produzca un gran número de intentos de inicio de sesión erróneos durante un período de tiempo determinado relativamente corto. Para configurar una directiva de este tipo, elija el filtro de actividad apropiado en la página **Nueva directiva de actividad**.  
  
     Bajo el campo **Filtros de actividad**, configure los parámetros para los que se desencadenará la alerta.  
  
     ![ejemplo de directiva de varios intentos de inicio de sesión erróneos](./media/multiple-failed-log-on-attempts-policy-example.png "multiple failed log on attempts policy example")  
  
-   Frecuencia de descarga alta  
  
     Puede establecer la directiva de modo que reciba una alerta cuando se produzca un nivel de actividad de descarga inesperado o inusitado. Para configurar una directiva de este tipo, en el parámetro **Frecuencia**, elija los parámetros que desencadenen la alerta.  
  
     ![ejemplo de frecuencia de descarga alta](./media/high-download-rate-example.png "high download rate example")  
  
## <a name="anomaly-detection"></a>Detección de anomalías  
Cuando la organización está protegida mediante Cloud App Security, todas las actividades en la nube se puntúan según diversos factores de riesgo predefinidos. Cloud App Security examina todas las sesiones de los usuarios en la nube y toma en consideración los factores de riesgo que se establezcan aquí para emitir alertas cuando ocurra algo diferente de la línea de base de la organización o de la actividad normal del usuario. La página de la directiva de detección de anomalías permite configurar y personalizar qué familias de factores de riesgo se tendrán en cuenta en el proceso de puntuación de riesgo. Las directivas se pueden aplicar de manera diferente a distintos usuarios, ubicaciones y sectores de la organización. Por ejemplo, puede crear una directiva que le avise cuando los miembros del equipo de TI estén activos fuera de la oficina.  
  
Para configurar una directiva de detección de anomalías:  
  
1.  En la consola, haga clic en **Control**, seguido de **Directivas**.  
  
2.  Haga clic en **Crear directiva** y seleccione la directiva **Detección de anomalías**.  
  
     ![menú de la directiva de detección de anomalías](./media/anomaly-detection-policy-menu.png "Anomaly detection policy menu")  
  
3.  Rellene el nombre y la descripción de la directiva y vaya al campo **Filtros de actividad**, donde puede elegir la actividad a la que quiere aplicar la directiva.  
  
4.  Asigne un nombre y una descripción a la directiva. Si quiere, puede basarla en una plantilla. Para obtener más información sobre las plantillas de directiva, vea [Controlar aplicaciones en la nube con directivas](control-cloud-apps-with-policies.md).  
  
5.  Para aplicar la directiva a todas las actividades del entorno en la nube, seleccione **Toda la actividad supervisada**. Para limitar la directiva a tipos específicos de actividades, elija **Actividad seleccionada**. Haga clic en **Agregar filtros** y establezca los parámetros adecuados por los que se filtrará la actividad. Por ejemplo, para aplicar la directiva solo en las actividades realizadas por los administradores de Salesforce, puede elegir esta etiqueta de usuario.  
  
6.  Debajo de este campo, establezca los **Factores de riesgo**. Puede elegir qué familias de riesgos quiere que se tengan en cuenta al calcular la puntuación de riesgo. Puede usar el botón Activar/Desactivar situado a la derecha de la fila para habilitar y deshabilitar los distintos riesgos. Además, para una mayor granularidad, puede elegir la actividad en la que quiere habilitar cada familia de riesgos.  
  
     Los factores de riesgo son los siguientes:  
  
    -   **Errores de inicio de sesión**: ¿intentan los usuarios iniciar sesión y se producen varios errores en un período de tiempo breve?  
  
    -   **Actividad de administración**: ¿usan los administradores sus cuentas con privilegios para iniciar sesión desde ubicaciones inusuales o a horas extrañas?  
  
    -   **Cuentas inactivas**: ¿hay repentinamente actividad en una cuenta que no se ha usado durante un tiempo?  
  
    -   **Ubicación**: ¿hay actividad en una ubicación nueva, sospechosa o inusual?  
  
    -   **Viaje imposible**: ¿ha iniciado sesión un usuario en Denver y diez minutos después en París?  
  
    -   **Agente de usuario y dispositivo**: ¿hay actividad en un dispositivo desconocido o no administrado?  
  
     Puede usar estos parámetros para definir escenarios complejos, por ejemplo, para excluir el intervalo IP de la oficina de los factores de riesgo considerados en la detección de anomalías, crear una etiqueta específica "office IP" (IP de la oficina) y filtrar el intervalo para que no se incluya entre los parámetros considerados. Después, para que el intervalo que ha creado se excluya de la detección de anomalías de la actividad de administración:  
  
    -   En **Tipo de riesgo**, busque **Actividad de administración**.  
  
    -   Cambie **Aplicar a** a **Actividad seleccionada**.  
  
    -   En **Filtros de actividad**, establezca **Aplicar a** en **Actividad seleccionada** y, en **Activities matching all of the following** (Actividades que coincidan con todo lo siguiente), establezca que la **Actividad administrativa** es **True**.  
  
    -   Haga clic en el icono **+**, seleccione **IP tag does not equal** (La etiqueta IP no es igual a) y seleccione la etiqueta "office IP".  
  
7.  En **Sensibilidad**, seleccione la frecuencia con la que quiere recibir alertas.  
  
     El valor de sensibilidad determinará cuántas alertas semanales se desencadenarán por término medio por cada 1000 usuarios.  
  
     ![IP de detección de anomalías](./media/anomaly-detection-ips.png "anomaly detection IPs")  
  
8.  Haga clic en **Crear**.  
 
  
## <a name="activity-policy-reference"></a>Referencia de directiva de actividad  
En esta sección se proporciona información de referencia sobre directivas, se ofrecen explicaciones sobre cada tipo de directiva y se detallan los campos que se pueden configurar para cada directiva.  
  
Una **directiva de actividad** es una directiva basada en API que permite supervisar las actividades de la organización en la nube en función de más de 20 filtros de metadatos de archivo (incluidos el tipo de dispositivo y la ubicación). Basándose en los resultados de la directiva, se pueden generar notificaciones y se puede suspender a usuarios de la aplicación en la nube.   
Cada directiva se compone de las siguientes partes:  
  
-   Filtros de actividad: permiten crear condiciones muy granulares basadas en metadatos.  
  
-   Parámetros de coincidencia de actividad: permiten establecer un umbral de número de veces que se repite una actividad para que se considere que coincide con la directiva.  
  
-   Acciones: la directiva proporciona un conjunto de acciones de gobierno que se pueden aplicar automáticamente cuando se detectan infracciones.  
## <a name="see-also"></a>Consulte también  
[Directivas de protección de datos](data-protection-policies.md)   
[Para obtener soporte técnico, visite la página de soporte técnico asistido de Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Los clientes Premier también pueden elegir Cloud App Security directamente desde el Portal Premier.](https://premier.microsoft.com/)  
  
  


<!--HONumber=Nov16_HO5-->


