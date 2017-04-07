---
title: "Trabajo con la puntuación de riesgo | Microsoft Docs"
description: "En este tema se proporcionan instrucciones sobre cómo usar y personalizar la puntuación de riesgo de la aplicación de Cloud App Security."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 4/2/2017
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: 9cb3594e-5007-48be-9b4f-e1d23355d86e
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 2fcc085cc53d2d7580640022029b1a528bea416a
ms.sourcegitcommit: 661f4ce41262e8462c90fd2a4f1232e2154d5113
translationtype: HT
---
# <a name="working-with-the-risk-score"></a>Trabajo con la puntuación de riesgo  

## <a name="the-cloud-app-catalog"></a>El Catálogo de aplicaciones en la nube

Para entender mejor qué aplicaciones en la nube puede detectar Cloud Discovery de Cloud App Security, use el Catálogo de aplicaciones en la nube.

El Catálogo de aplicaciones en la nube contiene más de 14 000 aplicaciones SaaS que se pueden ver (filtrar) por nombre, dominio, puntuación de riesgo, categoría o características de seguridad disponibles.

![acceso al Catálogo de aplicaciones en la nube](./media/risk-cac-dropdown.png)

## <a name="discovery-requests"></a>Solicitudes de detección

La información y las puntuaciones de riesgo del Catálogo de aplicaciones en la nube se basan en diversos orígenes. Microsoft hace todo lo posible para mantener la información actualizada, pero no garantiza la exactitud de los orígenes de datos. 

Póngase en contacto con nosotros si cree que la información acerca de una aplicación está obsoleta.

-    Solicite una actualización de puntuación si desea que nuestro equipo vuelva a evaluar esta aplicación en la nube.
-    Informe de nuevos datos (por campo específico o general) si piensa que la información acerca de la aplicación está obsoleta.

![actualizar los datos de riesgo](./media/risk-cac-feedback.png)

Además, le recomendamos que sugiera la incorporación de las aplicaciones en la nube que usa la organización que actualmente Cloud Discovery no puede detectar.

![sugerir nuevas aplicaciones](./media/risk-suggest-app.png)


## <a name="customizing-the-risk-score"></a>Personalización de la puntuación de riesgo

Cloud Discovery proporciona datos importantes sobre la credibilidad y la confianza de las aplicaciones en la nube que se usan en el entorno. En el portal, cada aplicación detectada se muestra junto a una puntuación total que representa la evaluación de Cloud App Security de la madurez de uso de esta aplicación en concreto para las empresas. La puntuación total de cualquier aplicación es un promedio ponderado de tres subpuntuaciones relacionadas con las tres subcategorías que Cloud App Security tiene en cuenta al evaluar la confiabilidad:  
  
-   **General**: esta categoría se refiere a aspectos básicos sobre la empresa que produce la aplicación, incluidos su dominio, año de fundación y popularidad. Estos campos están diseñados para reflejar la estabilidad de la empresa en el nivel más básico.  
  
-   **Seguridad**: la categoría de seguridad tiene en cuenta todos los estándares relacionados con la seguridad física de los datos usados por la aplicación detectada. Esto incluye campos como autenticación multifactor, cifrado, clasificación de los datos y propiedad de los datos.  
  
-   **Cumplimiento normativo**: esta categoría muestra qué estándares comunes de cumplimiento de procedimientos recomendados cumple la empresa que produce la aplicación. La lista de especificaciones incluye estándares como HIPAA, CSA y PCI-DSS.  
  
Cada una de las categorías se compone de muchas propiedades específicas. Según el algoritmo de puntuación, cada propiedad recibe una puntuación preliminar de entre 0 y 10, en función del valor. En consecuencia, los valores True/False recibirán 10 o 0, mientras que propiedades continuas como la antigüedad del dominio recibirán un valor determinado del espectro. La puntuación de cada propiedad se pondera con todos los demás campos existentes en la categoría para crear la subpuntuación de esta. Si encuentra una aplicación sin puntuar, eso normalmente indica que sus propiedades son desconocidas y que, por lo tanto, no se ha puntuado.  
  
Es importante dedicar un minuto a revisar y modificar las ponderaciones predeterminadas otorgadas a la configuración de puntuación de Cloud Discovery. De forma predeterminada, todos los distintos parámetros evaluados tienen la misma ponderación. Si hay determinados parámetros que son más o menos importantes para la organización, es importante cambiarlos de la siguiente forma:  
  
1.  En el portal, en el icono de configuración, seleccione **Configuración de Cloud Discovery**.  
  
2.  En **Configurar métrica de puntuación**, deslice el valor **Importancia** para cambiar la ponderación del campo o la categoría de riesgo a **Omitido**, **Bajo**, **Medio**, **Alto** o **Muy alto**.  
  
3.  Además, puede establecer si determinados valores no están disponibles o no son aplicables en el cálculo de la puntuación. Cuando se incluyen, los valores no aplicables tienen una contribución negativa a la puntuación calculada.  
  
     ![puntuación](./media/score.png "puntuación")  

Toda la información necesaria para entender cómo se apilan nuestras puntuaciones de riesgo está disponible en el portal de Cloud App Security.
Para entender mejor el peso de un factor de riesgo en la categoría de riesgo específica, utilice el botón “i” situado a la derecha de cada nombre de campo en el perfil de la aplicación. Esto proporciona información sobre cómo Cloud App Security puntúa exactamente un factor de riesgo específico. La puntuación es el valor del factor de riesgo en una escala de 1 a 10 + su peso en la categoría de riesgo:

![cálculo del riesgo](./media/cac-weight.png)
  
Para comprender el peso de una categoría de riesgo en la puntuación total de una aplicación, mantenga el mouse sobre la puntuación de la categoría de riesgo:

![peso de la categoría de riesgo](./media/risk-category-weight.png)


 
## <a name="see-also"></a>Consulte también  
[Actividades diarias para proteger el entorno de nube](daily-activities-to-protect-your-cloud-environment.md)   
[Para obtener soporte técnico, visite la página de soporte técnico asistido de Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Los clientes Premier también pueden elegir Cloud App Security directamente desde el Portal Premier.](https://premier.microsoft.com/)  
  
  