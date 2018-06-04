---
title: Trabajo con la puntuación de riesgo | Microsoft Docs
description: En este tema se proporcionan instrucciones sobre cómo usar y personalizar la puntuación de riesgo de la aplicación de Cloud App Security.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 5/27/2018
ms.topic: article
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 9cb3594e-5007-48be-9b4f-e1d23355d86e
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: ed1896655c6d94eb134c3dd0aa0bac345f08aa89
ms.sourcegitcommit: af8fad9709171b200699ca1ed513e2831826ed7e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/04/2018
ms.locfileid: "34567683"
---
*Se aplica a: Microsoft Cloud App Security*


# <a name="working-with-the-risk-score"></a>Trabajo con la puntuación de riesgo  

## <a name="the-cloud-app-catalog"></a>El Catálogo de aplicaciones en la nube

El Catálogo de aplicaciones en la nube proporciona una imagen completa de todo lo que puede identificar Cloud Discovery. Cloud Discovery analiza los registros de tráfico del catálogo de aplicaciones en la nube de Microsoft Cloud App Security de más de 16 000 aplicaciones en la nube que se clasifican y se puntúan en función de más de 70 factores de riesgo, a fin de proporcionar visibilidad continua del uso de la nube, Shadow IT y el riesgo que Shadow IT supone para la organización.
El **catálogo de aplicaciones en la nube** evalúa el riesgo de las aplicaciones en la nube en función de certificaciones normativas, estándares del sector y procedimientos recomendados. En el catálogo de aplicaciones en la nube se ejecutan cuatro procesos complementarios para mantenerlo actualizado:
1.  Extracción de datos automatizada directamente desde la aplicación en la nube (para atributos como el cumplimiento de SOC 2, los términos de servicio, la dirección URL de inicio de sesión, la directiva de privacidad y la ubicación de la sede central).
2.  Extracción de datos automatizada avanzada mediante algoritmos de Cloud App Security (para atributos como encabezados de seguridad HTTP).
3.  Análisis continuo por parte del equipo de analistas de la nube de Cloud App Security (para atributos como el cifrado en reposo).
4.  Solicitudes de revisión de los clientes, según las solicitudes de envío de clientes para realizar cambios en el catálogo de aplicaciones en la nube. Todas las solicitudes se someten al examen del equipo de analistas de la nube y se actualizan en función de sus conclusiones.
  
![El Catálogo de aplicaciones en la nube](./media/cloud-app-catalog.png)  

Cada vez es mayor la demanda de aplicaciones en la nube por parte de las unidades de negocio, como solución para sus necesidades en constante evolución. El Catálogo de aplicaciones en la nube permite elegir con criterio qué aplicaciones se adaptan mejor a los requisitos de seguridad de la organización y a la necesidad de mantenerse al día de los estándares de seguridad, las vulnerabilidades y las infracciones más recientes. Por ejemplo, si quiere comparar las aplicaciones CRM y asegurarse de que están bien protegidas, puede usar la página del Catálogo de aplicaciones en la nube para filtrar las aplicaciones que le interesan. En la página del **Catálogo de aplicaciones en la nube**, en **Buscar por categoría**, seleccione **CRM**. 

Después, use los filtros **Avanzados** y establezca **Factor de riesgo de cumplimiento** > **SOC 2** en igual a **True**; **Factor de riesgo de cumplimiento** > **ISO 27001** en igual a **True**; **Factor de riesgo para la seguridad** > **Cifrado de datos en reposo** en igual a **True**; **Factor de riesgo para la seguridad** > **Cifrado de datos en reposo** en igual a **True**; **Factor de riesgo para la seguridad** > **Pista de auditoría de administración** en igual a **True**; y **Factor de riesgo para la seguridad** > **Pista de auditoría de usuario** en igual a **True**.

![Filtros del Catálogo de aplicaciones en la nube](./media/cloud-app-catalog-filters.png)

Una vez que se hayan filtrado los resultados, puede revisar las aplicaciones correspondientes y buscar la que mejor se adapte a sus necesidades.

## <a name="cloud-app-catalog-filters"></a>Filtros del Catálogo de aplicaciones en la nube

Hay filtros básicos y avanzados en el Catálogo de aplicaciones en la nube. Para aplicar un filtro complejo, use la opción avanzada, que incluye lo siguiente:

- **Etiquetas de aplicación**: las etiquetas le permiten personalizar el Catálogo de aplicaciones en la nube. 
  Puede seleccionar la etiqueta **Autorizada** o **No autorizada**, o bien puede crear etiquetas personalizadas para las aplicaciones. Estas etiquetas pueden usarse como filtros para profundizar un poco más en los tipos de aplicaciones específicos que quiere investigar. 
- **Aplicaciones y dominios**: permite buscar aplicaciones específicas o aplicaciones usadas en dominios concretos. 
- **Categorías**: el filtro de categorías, que se encuentra a la izquierda de la página, permite buscar tipos de aplicaciones en función de categorías de aplicaciones, como aplicaciones de redes sociales, aplicaciones de almacenamiento en la nube, etc. Puede seleccionar varias categorías a la vez o una sola categoría y, después, aplicarles los filtros básicos y avanzados.
- **Factor de riesgo de cumplimiento**: permite buscar normas, certificaciones y compatibilidades específicas que puede cumplir la aplicación (HIPAA, ISO 27001, SOC 2, PCI-DSS, etc.).
- **Factor de riesgo general**: permite buscar factores de riesgo generales, como la popularidad entre los consumidores, la configuración regional del centro de datos, etc.
- **Puntuación de riesgo**: permite filtrar las aplicaciones según su puntuación de riesgo, de modo que pueda centrarse, por ejemplo, en revisar únicamente las aplicaciones de mucho riesgo.
- **Factor de riesgo para la seguridad**: permite filtrar en función de medidas de seguridad específicas (por ejemplo, cifrado en reposo, autenticación multifactor, etc.).

## <a name="suggesting-a-change"></a>Sugerir un cambio

Si encuentra una nueva aplicación en el entorno que Cloud App Security todavía no ha puntuado, un nuevo factor de riesgo, una actualización de puntuación o datos de la aplicación que no están actualizados, puede solicitar una revisión de la aplicación:

**Para sugerir una nueva aplicación:**
1. En la parte superior de la página **Aplicaciones detectadas**, haga clic en los tres puntos y seleccione **Sugerir nueva aplicación**. 

   ![Sugerir una aplicación a Cloud App Security](./media/suggest-new-app.png)

2. En la ventana emergente **Sugerir nueva aplicación de nube**, rellene la información relativa a la nueva aplicación, incluidos el nombre y el dominio de la aplicación. 

   ![Ventana emergente para sugerir una aplicación a Cloud App Security](./media/suggest-new-app-popup.png)

3. Se recomienda activar la casilla para permitir que los analistas de Cloud App Security se pongan en contacto con usted en caso de que necesiten más información sobre la aplicación. De este modo, también podrán avisarle cuando se haya completado el análisis.

**Para actualizar un factor de riesgo, puntuación o datos de la aplicación:**

1. En la página **Catálogo de aplicaciones en la nube**, en la fila de la aplicación que quiere actualizar, haga clic en los tres puntos que aparecen al final de la fila y seleccione **Solicitar actualización de puntuación**.

   ![Solicitar actualización de puntuación](./media/request-score-update.png)

2. En la ventana emergente **Sugerencia de mejora**, seleccione si quiere solicitar una actualización de puntuación, sugerir un nuevo factor de riesgo o actualizar los datos de una aplicación.

   ![Sugerencia de mejora a Cloud App Security](./media/suggest-improvement-popup.png)

3. Se recomienda activar la casilla para permitir que los analistas de Cloud App Security se pongan en contacto con usted en caso de que necesiten más información sobre la aplicación. De este modo, también podrán avisarle cuando se haya completado el análisis.
 


## <a name="customizing-the-risk-score"></a>Personalización de la puntuación de riesgo

Cloud Discovery proporciona datos importantes sobre la credibilidad y la confianza de las aplicaciones en la nube que se usan en el entorno. En el portal, cada aplicación detectada se muestra junto a una puntuación total que representa la evaluación de Cloud App Security de la madurez de uso de esta aplicación en concreto para las empresas. La puntuación total de cualquier aplicación es un promedio ponderado de tres subpuntuaciones relacionadas con las tres subcategorías que Cloud App Security tiene en cuenta al evaluar la confiabilidad:  
  
-   **General**: esta categoría se refiere a aspectos básicos sobre la compañía que produce la aplicación, incluidos su dominio, año de fundación y popularidad. Estos campos están diseñados para reflejar la estabilidad de la empresa en el nivel más básico.  
  
-   **Seguridad**: la categoría de seguridad tiene en cuenta todos los estándares relacionados con la seguridad física de los datos usados por la aplicación detectada. Esto incluye campos tales como autenticación multifactor, cifrado, clasificación de los datos y propiedad de los datos.  
  
-   **Cumplimiento normativo**: esta categoría muestra qué estándares comunes de cumplimiento de procedimientos recomendados cumple la empresa que produce la aplicación. La lista de especificaciones incluye estándares tales como HIPAA, CSA y PCI-DSS.  
  
Cada una de las categorías se compone de muchas propiedades específicas. Según el algoritmo de puntuación de Cloud App Security, cada propiedad recibe una puntuación preliminar de entre 0 y 10, en función del valor. En consecuencia, los valores True/False recibirán 10 o 0, mientras que propiedades continuas como la antigüedad del dominio recibirán un valor determinado del espectro. La puntuación de cada propiedad se pondera con todos los demás campos existentes en la categoría para crear la subpuntuación de esta. Si encuentra una aplicación sin puntuar, eso normalmente indica que sus propiedades son desconocidas y que, por lo tanto, no se ha puntuado.  
  
Es importante dedicar un minuto a revisar y modificar las ponderaciones predeterminadas otorgadas a la configuración de puntuación de Cloud Discovery. De forma predeterminada, todos los distintos parámetros evaluados tienen la misma ponderación. Si hay determinados parámetros que son más o menos importantes para la organización, es importante cambiarlos de la siguiente forma:  
  
1. En el portal, en el icono de configuración, seleccione **Configuración de Cloud Discovery**.  
  
2. En **Configurar métrica de puntuación**, deslice el valor **Importancia** para cambiar la ponderación del campo o la categoría de riesgo a **Omitido**, **Bajo**, **Medio**, **Alto** o **Muy alto**.  
  
3. Además, puede establecer si determinados valores no están disponibles o no son aplicables en el cálculo de la puntuación. Cuando se incluyen, los valores no aplicables tienen una contribución negativa a la puntuación calculada.  
  
   ![puntuación](./media/score.png "puntuación")  

Toda la información necesaria para entender cómo se apilan nuestras puntuaciones de riesgo de Cloud App Security está disponible en el portal de Cloud App Security.
Para entender mejor el peso de un factor de riesgo en la categoría de riesgo específica, utilice el botón “i” situado a la derecha de cada nombre de campo en el perfil de la aplicación. Esto proporciona información sobre cómo Cloud App Security puntúa exactamente un factor de riesgo específico. La puntuación es el valor del factor de riesgo en una escala de 1 a 10 + su peso en la categoría de riesgo:

![cálculo del riesgo](./media/cac-weight.png)
  
Para comprender el peso de una categoría de riesgo en la puntuación total de una aplicación, mantenga el mouse sobre la puntuación de la categoría de riesgo:

![peso de la categoría de riesgo](./media/risk-category-weight.png)

## <a name="overriding-the-risk-score"></a>Reemplazar la puntuación de riesgo
Puede reemplazar la puntuación de riesgo de una aplicación sin cambiar la forma en que se pondera, para obtener resultados inmediatos para la organización. Por ejemplo, si la puntuación de riesgo de una aplicación de LOB que usa es 8 y la organización la ha autorizado y la recomienda, podría interesarle cambiar la puntuación de riesgo a 10. 

Para reemplazar la puntuación de riesgo, en la tabla **Aplicaciones detectadas** o en el **Catálogo de aplicaciones en la nube**, haga clic en los tres puntos que aparecen a la derecha de cualquier aplicación y seleccione **Override risk score** (Reemplazar la puntuación de riesgo).

![reemplazar la puntuación de riesgo de una aplicación detectada de Cloud App Security](./media/override-risk-score.png)

Después de actualizar la puntuación, puede incluir notas en la aplicación en las que explique a los demás administradores las razones empresariales por las que ha modificado la puntuación de la aplicación. 

También puede agregar notas para que el motivo de este cambio le quede claro a los usuarios que revisen la aplicación.


 
## <a name="see-also"></a>Consulte también  
[Actividades diarias para proteger el entorno de nube](daily-activities-to-protect-your-cloud-environment.md)   

[Los clientes Premier también pueden elegir Cloud App Security directamente desde el Portal Premier.](https://premier.microsoft.com/)  
  
  