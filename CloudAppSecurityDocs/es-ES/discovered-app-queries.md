---
title: Trabajar con filtros y consultas de aplicaciones detectadas de Cloud App Security | Microsoft Docs
description: En este tema, se proporciona una lista de filtros y consultas de aplicaciones detectadas de Cloud App Security y se explica cómo trabajar con ellos.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 4/29/2018
ms.topic: get-started-article
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 1a2d3aeb-4e28-4c73-804b-95e862b08e43
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 8306912fcf0c7a5049c4683b75be9009181d101b
ms.sourcegitcommit: c5dbeb75e409518feaa26200e9a02c59accc8dcc
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/30/2018
---
*Se aplica a: Microsoft Cloud App Security*

# <a name="discovered-app-filters-and-queries"></a>Filtros y consultas de aplicaciones detectadas

## <a name="discovered-app-filters"></a>Filtros de aplicaciones detectadas

Hay filtros de aplicaciones detectadas básicos y avanzados. Para aplicar un filtro complejo (como en el ejemplo anterior), use la opción avanzada, que incluye lo siguiente:

![Aplicaciones detectadas](./media/discovered-apps.png)  


- **Etiqueta de aplicación**: seleccione si la aplicación se ha autorizado o no y si no está etiquetada. Además, puede crear una etiqueta personalizada para la aplicación y usarla para filtrar tipos específicos de aplicaciones. 
- **Aplicaciones y dominios**: permite buscar aplicaciones específicas o aplicaciones usadas en dominios concretos. 
- **Categorías**: el filtro de categorías, que se encuentra a la izquierda de la página, permite buscar tipos de aplicaciones en función de categorías de aplicaciones, como aplicaciones de redes sociales, aplicaciones de almacenamiento en la nube, etc. Puede seleccionar varias categorías a la vez o una sola categoría y, después, aplicarles los filtros básicos y avanzados.
- **Factor de riesgo de cumplimiento**: permite buscar normas, certificaciones y compatibilidades específicas que puede cumplir la aplicación (HIPAA, ISO 27001, SOC 2, PCI-DSS, etc.).
- **Factor de riesgo general**: permite buscar factores de riesgo generales, como la popularidad entre los consumidores, la configuración regional del centro de datos, etc.
- **Puntuación de riesgo**: permite filtrar las aplicaciones según su puntuación de riesgo, de modo que pueda centrarse, por ejemplo, en revisar únicamente las aplicaciones de mucho riesgo. También puede reemplazar la puntuación de riesgo establecida por Cloud App Security. Para obtener más información, vea [Trabajo con la puntuación de riesgo](risk-score.md).
- **Factor de riesgo para la seguridad**: permite filtrar en función de medidas de seguridad específicas (por ejemplo, cifrado en reposo, autenticación multifactor, etc.).
- **Uso**: permite filtrar en función de las estadísticas de uso de la aplicación, como aplicaciones con menos o más **cargas de datos** que la cantidad especificada, o aplicaciones con menos o más de un número específico de **usuarios**.

### <a name="creating-and-managing-custom-app-tags"></a>Crear y administrar etiquetas de aplicación personalizadas

Puede crear etiquetas de aplicación personalizadas. Estas etiquetas pueden usarse como filtros para profundizar un poco más en los tipos de aplicaciones específicos que quiere investigar. Por ejemplo, lista de supervisión personalizada, asignación a una unidad de negocio específica o aprobaciones personalizadas (por ejemplo, "aprobado por el departamento legal").

Para crear una etiqueta de aplicación personalizada:

1. En el engranaje de **Configuración** seleccione **Cloud Discovery** y en la pestaña **Manage app tags** (Administrar etiquetas de aplicación) haga clic en el icono ![icono más](./media/plus-icon.png). 

![Crear una etiqueta de aplicación personalizada](./media/create-app-tag.png)

2. Puede usar la tabla **Manage app tags** (Administrar etiquetas de aplicación) para ver qué aplicaciones están etiquetadas con cada etiqueta de aplicación y puede eliminar las etiquetas de aplicación que no se usan.

3. Para aplicar una etiqueta de aplicación, en la pestaña **Aplicaciones detectadas**, haga clic en los tres puntos situados a la derecha de la tabla y seleccione la etiqueta de aplicación que quiere aplicar. 

> [!NOTE]
>También puede crear una etiqueta de aplicación directamente en la tabla **Aplicaciones detectadas**. Para ello, haga clic en **Create app tag** (Crear etiqueta de aplicación) después de seleccionar los tres puntos situados a la derecha de cualquier aplicación seleccionada. También puede tener acceso a la pantalla **Manage app tags** (Administrar etiquetas de aplicación). Para ello, haga clic en el vínculo situado en la esquina de la ventana emergente **Create app tag** (Crear etiqueta de aplicación).

## <a name="discovered-app-queries"></a>Consultas de aplicaciones detectadas

Para que la investigación sea incluso más sencilla, ahora puede crear consultas personalizadas y guardarlas para usar más adelante. 

1. En la página **Aplicaciones detectadas**, use los filtros como se ha descrito anteriormente para explorar las aplicaciones en profundidad según sea necesario. 

2. Una vez que haya conseguido los resultados deseados, haga clic en el botón **Guardar como** situado en la esquina superior derecha de los filtros. 

3. En la ventana emergente **Guardar consulta**, escriba el nombre de la consulta.

   ![nueva consulta](./media/new-query.png)

4. Para volver a usar esta consulta en el futuro, en **Consultas**, desplácese hacia abajo hasta **Consultas guardadas** y seleccione la consulta. 

   ![abrir consulta](./media/open-query.png)


Cloud App Security también le proporciona **consultas sugeridas** y le permite guardar las consultas personalizadas que usa a menudo. Las consultas sugeridas le proporcionan vías de investigación recomendadas que filtran las aplicaciones detectadas mediante las siguientes consultas sugeridas opcionales:

 - Aplicaciones en la nube que permiten el uso anónimo: filtra todas las aplicaciones detectadas para mostrar solo aquellas que implican riesgos de seguridad porque no requieren la autenticación del usuario y permiten que los usuarios carguen datos.

 - Aplicaciones en la nube que tienen el certificado CSA STAR: filtra todas las aplicaciones detectadas para mostrar solo aquellas que tienen la certificación CSA STAR, ya sea por evaluación automática, certificación, autenticación o supervisión continua.

 - Aplicaciones en la nube que cumplen el programa FedRAMP: filtra todas las aplicaciones detectadas para mostrar solo aquellas cuyo factor de riesgo de cumplimiento de FedRAMP es alto, medio o bajo. 

 - Aplicaciones de colaboración y almacenamiento en la nube que tienen datos de usuario: filtra todas las aplicaciones detectadas para mostrar solo aquellas que implican un riesgo porque no le permiten ser el propietario de los datos, a pesar de que sí los conservan.

 - Aplicaciones de almacenamiento en la nube que implican un riesgo y no son conformes: filtra todas las aplicaciones detectadas para mostrar solo aquellas que no cumplen las normativas SOC 2 o HIPAA, no admiten la versión de PCI DSS y tienen una puntuación de riesgo de 5 o inferior.

 - Aplicaciones en la nube de la empresa que tienen una autenticación débil: filtra todas las aplicaciones detectadas para mostrar solo aquellas que no son compatibles con SAML, no tienen ninguna directiva de contraseñas y no habilitan MFA.

 - Aplicaciones en la nube de la empresa que tienen un cifrado débil: filtra todas las aplicaciones detectadas para mostrar solo aquellas que implican un riesgo porque no cifran datos en reposo y no admiten ningún protocolo de cifrado.

![consultar aplicaciones detectadas](./media/queries-discovered-apps.png)

 
Además, puede usar las consultas sugeridas como punto de partida para una nueva consulta. En primer lugar, seleccione una de las consultas sugeridas. Después, realice los cambios necesarios y, por último, haga clic en **Guardar como** para crear una **Consulta guardada**.


## <a name="see-also"></a>Consulta también
 
[Crear informes de instantáneas de Cloud Discovery](create-snapshot-cloud-discovery-reports.md)

[Configurar la carga de registros automática para informes continuos](configure-automatic-log-upload-for-continuous-reports.md)

[Trabajar con datos de Cloud Discovery](working-with-cloud-discovery-data.md)

