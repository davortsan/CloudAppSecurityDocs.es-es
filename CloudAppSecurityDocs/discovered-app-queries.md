---
title: Filtros y consultas de aplicaciones detectadas de Cloud App Security
description: En este artículo se proporciona una lista de filtros y consultas de aplicaciones detectadas de Cloud App Security y se explica cómo trabajar con ellos.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 07/07/2020
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: ff18286f75a3f5a306f7ac1c08ecff3ad98a01a5
ms.sourcegitcommit: 15d80cde40df8a8d3a156764a6a99fad0e62a422
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/07/2020
ms.locfileid: "86046069"
---
# <a name="discovered-app-filters-and-queries"></a>Consultas y filtros de aplicaciones detectadas

*Se aplica a: Microsoft Cloud App Security*

Cuando haya un gran número de aplicaciones detectadas, le resultará útil filtrarlas y realizar consultas en ellas. En este artículo se describe qué filtros están disponibles y cómo realizar consultas en las aplicaciones detectadas.

## <a name="discovered-app-filters"></a>Filtros de aplicaciones detectadas

Hay filtros de aplicaciones detectadas básicos y avanzados. Para aplicar un filtro complejo, como en el ejemplo anterior, use la opción avanzada, que incluye los siguientes filtros:

![Aplicaciones detectadas](media/discovered-apps.png)

- **Etiqueta de aplicación**: seleccione si la aplicación se ha autorizado o no y si no está etiquetada. Además, puede crear una etiqueta personalizada para la aplicación y usarla para filtrar tipos específicos de aplicaciones.
- **Aplicaciones y dominios**: permite buscar aplicaciones específicas o aplicaciones usadas en dominios concretos.
- **Categorías**: el filtro de categorías, que se encuentra a la izquierda de la página, permite buscar tipos de aplicaciones en función de categorías de aplicaciones. Las categorías de ejemplo incluyen aplicaciones de redes sociales, aplicaciones de almacenamiento en la nube y servicios de hospedaje. Puede seleccionar varias categorías a la vez o una sola categoría y, después, aplicarles los filtros básicos y avanzados.
- **Factor de riesgo de cumplimiento**: permite buscar normas, certificaciones y elementos de conformidad específicos que puede cumplir la aplicación (HIPAA, ISO 27001, SOC 2, PCI-DSS, entre otros).
- **Factor de riesgo general**: permite buscar factores de riesgo generales, como la popularidad entre los consumidores, la configuración regional del centro de datos y muchos más.
- **Puntuación de riesgo**: permite filtrar las aplicaciones según su puntuación de riesgo, de modo que pueda centrarse, por ejemplo, en revisar únicamente las aplicaciones de mucho riesgo. También puede reemplazar la puntuación de riesgo establecida por Cloud App Security. Para obtener más información, vea [trabajar con la puntuación de riesgo](risk-score.md).
- **Factor de riesgo para la seguridad**: permite filtrar en función de medidas de seguridad específicas (por ejemplo, cifrado en reposo, autenticación multifactor, etc.).
- **Uso**: permite filtrar en función de las estadísticas de uso de esta aplicación. Uso, como por ejemplo, como aplicaciones con menos o más **cargas de datos** de las especificadas, o aplicaciones con menos o más **usuarios** de los especificados.
- **Factor de riesgo legal**: permite filtrar en función de las regulaciones y directivas en vigor para garantizar la protección y la privacidad de los datos de los usuarios de la aplicación. Algunos ejemplos son las aplicaciones en la nube preparadas para el RGPD, DMCA y la directiva de retención de datos.

### <a name="creating-and-managing-custom-app-tags"></a>Crear y administrar etiquetas de aplicación personalizadas

Puede crear etiquetas de aplicación personalizadas. Estas etiquetas pueden usarse como filtros para profundizar un poco más en los tipos de aplicaciones específicos que quiere investigar. Por ejemplo, lista de supervisión personalizada, asignación a una unidad de negocio específica o aprobaciones personalizadas, como "aprobada por legal". Las etiquetas de aplicación también se pueden usar en directivas de detección de aplicaciones en filtros o mediante la aplicación de etiquetas a las aplicaciones como parte de las acciones de gobierno de directivas.

Para crear una etiqueta de aplicación personalizada:

1. En el engranaje de **configuración** , seleccione **configuración de Cloud Discovery**, luego la pestaña Etiquetas de la **aplicación** . Haga clic en el icono de signo más. ![icono de signo más](media/plus-icon.png)

   ![Crear una etiqueta de aplicación personalizada](media/create-app-tag.png)

2. Puede usar la tabla **Etiquetas de aplicación** para ver qué aplicaciones están etiquetadas con cada etiqueta de aplicación y puede eliminar las etiquetas de aplicación que no se usan.

3. Para aplicar una etiqueta de aplicación, en la pestaña **Aplicaciones detectadas**, haga clic en los tres puntos situados a la derecha del nombre de aplicación. Seleccione la etiqueta de aplicación que se aplicará.

> [!NOTE]
>También puede crear una etiqueta de aplicación directamente en la tabla **Aplicaciones detectadas**. Para ello, haga clic en **Create app tag** (Crear etiqueta de aplicación) después de seleccionar los tres puntos situados a la derecha de cualquier aplicación seleccionada. Cuando se crea la etiqueta desde la aplicación detectada, se puede aplicar a la aplicación. También puede acceder a la pantalla **Etiquetas de aplicación**si hace clic en el vínculo **Administrar etiquetas** de la esquina.
> ![Crear una etiqueta de aplicación desde la aplicación](media/create-app-tag-from-app.png)

## <a name="discovered-app-queries"></a>Consultas de aplicaciones detectadas

Para que una investigación sea aún más sencilla, puede crear consultas personalizadas y guardarlas para su uso posterior.

1. En la página **Aplicaciones detectadas**, use los filtros como se ha descrito anteriormente para explorar las aplicaciones en profundidad según sea necesario.

2. Una vez que haya conseguido los resultados que buscaba, haga clic en el botón **Guardar como** situado en la esquina superior derecha de los filtros.

3. En el elemento emergente **Guardar consulta** , asigne un nombre a la consulta.

    ![nueva consulta](media/new-query.png)

4. Para volver a usar esta consulta en el futuro, en **Consultas**, desplácese hacia abajo hasta **Consultas guardadas** y seleccione la consulta.

    ![abrir consulta](media/discovered-app-query.png)

Cloud App Security también le proporciona **consultas sugeridas** y le permite guardar las consultas personalizadas que usa a menudo. Las consultas sugeridas le proporcionan vías de investigación recomendadas que filtran las aplicaciones detectadas mediante las siguientes consultas sugeridas opcionales:

- **Aplicaciones en la nube que permiten el uso anónimo** : filtra todas las aplicaciones detectadas para mostrar solo las aplicaciones que son riesgos de seguridad porque no requieren la autenticación del usuario y permiten a los usuarios cargar datos.

- **Aplicaciones en la nube con certificación CSA Star** : filtra todas las aplicaciones detectadas para mostrar solo las aplicaciones que tienen la certificación CSA Star mediante autoevaluación, certificación, atestación o supervisión continua.

- **Aplicaciones en la nube que son compatibles con FedRAMP** : filtra todas las aplicaciones detectadas para mostrar solo las aplicaciones cuyo factor de riesgo de cumplimiento de FedRAMP sea alto, medio o bajo.

- **Aplicaciones de colaboración y almacenamiento en la nube que tienen datos de usuario**: filtra todas las aplicaciones detectadas para mostrar solo aquellas que implican un riesgo porque no le permiten ser el propietario de los datos, a pesar de que sí los conservan.

- **Aplicaciones de almacenamiento en la nube que implican un riesgo y no son conformes**: filtra todas las aplicaciones detectadas para mostrar solo aquellas que no cumplen las normativas SOC 2 o HIPAA, no admiten la versión de PCI DSS y tienen una puntuación de riesgo de 5 o inferior.

- **Aplicaciones de nube de empresa con autenticación débil** : filtra todas las aplicaciones detectadas para mostrar solo las aplicaciones que no son compatibles con SAML, no tienen ninguna directiva de contraseñas y no habilitan MFA.

- **Aplicaciones empresariales en la nube con cifrado débil** : filtra todas las aplicaciones detectadas para mostrar solo las aplicaciones que son arriesgadas porque no cifran los datos en reposo y no admiten ningún protocolo de cifrado.

- **Aplicaciones en la nube preparadas para el RGPD**: filtra todas las aplicaciones detectadas para mostrar solo las que estén preparadas para el RGPD. Dado que el cumplimiento de RGPD es una prioridad máxima, esta consulta le ayuda a identificar fácilmente las aplicaciones que están listas para RGPD y a mitigar la amenaza mediante la evaluación del riesgo de las que no lo son.

![consultar aplicaciones detectadas](media/queries-discovered-apps.png)

Además, puede usar las consultas sugeridas como punto de partida para una nueva consulta. En primer lugar, seleccione una de las consultas sugeridas. Después, realice los cambios necesarios y, por último, haga clic en **Guardar como** para crear una **Consulta guardada**.

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Crear informes de instantáneas de Cloud Discovery](create-snapshot-cloud-discovery-reports.md)

> [!div class="nextstepaction"]
> [Configurar la carga de registros automática para informes continuos](configure-automatic-log-upload-for-continuous-reports.md)

> [!div class="nextstepaction"]
> [Trabajo con datos de Cloud Discovery](working-with-cloud-discovery-data.md)
