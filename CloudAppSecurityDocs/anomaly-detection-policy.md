---
title: "Crear directivas de detección de anomalías en Cloud App Security | Microsoft Docs"
description: "En este tema se proporciona una descripción de las directivas de detección de anomalías, así como información de referencia sobre los bloques de creación de una directiva de detección de anomalías."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 9/24/2017
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: ab9bc377-d2f5-4f4c-a419-f1728a15d1c7
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 5ffc6d748e8a4050a40cfadc81d5b2267eae934d
ms.sourcegitcommit: 8759541301241e03784c5ac87b56986f22bd0561
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/28/2017
---
# <a name="anomaly-detection-policy"></a>Directiva de detección de anomalías
En este artículo se proporciona información de referencia sobre directivas, se ofrecen explicaciones sobre cada tipo de directiva y se detallan los campos que se pueden configurar para cada directiva.  

Cuando la organización está protegida mediante Cloud App Security, todas las actividades en la nube se puntúan según diversos factores de riesgo predefinidos. Cloud App Security examina todas las sesiones de los usuarios en la nube y toma en consideración los factores de riesgo que se establezcan aquí para emitir alertas cuando ocurra algo diferente de la línea de base de la organización o de la actividad normal del usuario. La página de la directiva de detección de anomalías permite configurar y personalizar qué familias de factores de riesgo se tendrán en cuenta en el proceso de puntuación de riesgo. Las directivas se pueden aplicar de manera diferente a distintos usuarios, ubicaciones y sectores de la organización. Por ejemplo, puede crear una directiva que le avise cuando los miembros del equipo de TI estén activos fuera de la oficina.  

Cloud App Security tiene un período de aprendizaje inicial de siete días, durante el cual no marca ningún usuario nuevo, actividad, dispositivos o ubicaciones como erróneos. Transcurrido este tiempo, cada sesión se compara con la actividad, los momentos en que los usuarios estaban activos, las direcciones IP, los dispositivos, etc., que se detectaron durante el mes anterior y la puntuación de riesgo de estas actividades. Use el control de sensibilidad de la directiva para establecer la puntuación de riesgo mínima a partir de la cual se desencadenarán las alertas. Se recomienda que, al crear una directiva de anomalías, se use el umbral de sensibilidad predeterminado durante una semana, antes de cambiarlo en función del número de alertas que se hayan recibido. Cloud App Security le enviará más o menos alertas para las diversas puntuaciones de riesgo cuando cambie la sensibilidad.
  
![control de sensibilidad](./media/sensitivity-slider.png)

Para configurar una directiva de detección de anomalías:  
  
1.  En la consola, haga clic en **Control**, seguido de **Directivas**.  
  
2.  Haga clic en **Crear directiva** y seleccione la directiva **Detección de anomalías**.  
  
     ![menú de la directiva de detección de anomalías](./media/anomaly-detection-policy-menu.png "menú de la directiva de detección de anomalías")  
  
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

    -   **Velocidad de la actividad**: ¿Repentinamente hay mucha actividad en una aplicación en concreto? ¿Hay descargas o eliminaciones grandes , se ha compartido un gran número de archivos o se ha producido un nivel elevado de actividad de administradores inesperada?
  
     Puede usar estos parámetros para definir escenarios complejos, por ejemplo, para excluir el intervalo IP de la oficina de los factores de riesgo considerados en la detección de anomalías, crear una etiqueta específica "office IP" (IP de la oficina) y filtrar el intervalo para que no se incluya entre los parámetros considerados. Después, para que el intervalo que ha creado se excluya de la detección de anomalías de la actividad de administración:  
  
    -   En **Tipo de riesgo**, busque **Actividad de administración**.  
  
    -   Cambie **Aplicar a** a **Actividad seleccionada**.  
  
    -   En **Filtros de actividad**, establezca **Aplicar a** en **Actividad seleccionada** y, en **Activities matching all of the following** (Actividades que coincidan con todo lo siguiente), establezca que la **Actividad administrativa** es **True**.  
  
    -   Haga clic en el icono **+**, seleccione **IP tag does not equal** (La etiqueta IP no es igual a) y seleccione la etiqueta "office IP".  
  
7.  En **Sensibilidad**, seleccione la frecuencia con la que quiere recibir alertas.  
  
     El valor de sensibilidad determina cuántas alertas semanales se desencadenan por término medio por cada mil usuarios.  
  
     ![IP de detección de anomalías](./media/anomaly-detection-ips.png "IP de detección de anomalías")  
  
8.  Haga clic en **Crear**.  
 

## <a name="anomaly-detection-policy-reference"></a>Referencia de directivas de detección de anomalías  
Una directiva de detección de anomalías permite preparar y configurar la supervisión continua de la actividad de los usuarios para detectar anomalías de comportamiento. Las anomalías se detectan mediante el examen de la actividad del usuario. El riesgo se evalúa mediante el análisis de más de 30 indicadores de riesgo distintos agrupados en seis factores de riesgo. Basándose en los resultados de la directiva, se activan alertas de seguridad.   
Cada directiva se compone de las siguientes partes:  
  
-   Filtros de actividad: permiten analizar de forma selectiva únicamente la actividad de usuario filtrada para detectar anomalías.  
  
-   Factores de riesgo: permiten seleccionar qué factores de riesgo se incluyen al evaluar el riesgo.  
  
-   Sensibilidad: permite establecer cuántas alertas debe activar la directiva.  
  
### <a name="activity-filters"></a>Filtros de actividad  
Para obtener una lista de filtros de actividad, consulte [escribir aquí la descripción del vínculo](activity-filters.md).  
  
### <a name="risk-factors"></a>Factores de riesgo  
A continuación, se proporciona una lista de los factores de riesgo que se tienen en cuenta a la hora de evaluar el riesgo de la actividad del usuario. Cada factor de riesgo se puede activar o desactivar. En el campo **Aplicar a** de cada factor de riesgo hay dos opciones que determinan si se incluye en la evaluación del riesgo de la actividad del usuario:  
  
-   Toda la actividad supervisada: se incluye para toda la actividad de usuario que pasa el filtro de actividad de directiva.  
  
-   Actividad seleccionada: se incluye para la actividad de usuario que pasa tanto los filtros de actividad de directiva como los filtros de actividad que aparecen en este factor de riesgo. Cuando esta opción está seleccionada, aparece un selector de filtro de actividad en el factor de riesgo que funciona exactamente igual que el filtro de actividad de directiva.  
  
Cada factor de riesgo, cuando se incluye en la evaluación del riesgo, tiene sus propios desencadenadores que provocan un aumento del riesgo evaluado de actividad de usuario:  
  
-   Errores de inicio de sesión: un gran número de errores de inicio de sesión o una actividad que consta únicamente de errores de inicio de sesión.  
  
-   Actividad de administración: actividad administrativa realizada por un usuario inesperado o desde una IP, un ISP o una ubicación que son nuevos o que ningún otro usuario de la organización ha usado.  
  
-   Cuentas inactivas: actividad realizada por un usuario que no ha estado activo durante mucho tiempo.  
  
-   Ubicación: actividad realizada desde una IP, un ISP o una ubicación que nunca ha usado otro usuario, este usuario concreto nunca ha usado, nunca se ha usado en absoluto o solo se ha usado para errores de inicio de sesión en el pasado.  
  
-   Viaje imposible: actividad desde ubicaciones remotas en un breve lapso de tiempo.  
  
-   Agente de usuario y dispositivo: actividad realizada por un usuario mediante un agente de usuario o dispositivo que nunca ha usado otro usuario, este usuario concreto nunca ha usado o nunca se ha usado en absoluto.  
  
-   Tasa de actividad: actividades repetidas que realiza un usuario durante un breve período. 

### <a name="sensitivity"></a>Sensibilidad  
Hay dos formas de controlar el número de alertas activadas por la directiva:  
  
-   Control de sensibilidad: seleccione cuántas alertas se activan por cada 1 000 usuarios a la semana. Se activarán las alertas de las actividades con el riesgo más alto.  
  
-   Límite de alertas diarias: restrinja el número de alertas activadas en un solo día.  
  
## <a name="see-also"></a>Consulte también  
[Actividades diarias para proteger el entorno de nube](daily-activities-to-protect-your-cloud-environment.md)   
[Para obtener soporte técnico, visite la página de soporte técnico asistido de Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Los clientes Premier también pueden elegir Cloud App Security directamente desde el Portal Premier.](https://premier.microsoft.com/)  
  
  
