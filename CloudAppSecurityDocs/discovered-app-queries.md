---
title: Cloud App Security filtros y consultas de aplicaciones detectados
description: En este artículo se proporciona una lista de Cloud App Security filtros y consultas de aplicaciones detectados y se explica cómo trabajar con ellos.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 12/10/2018
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: ba9848bf0f9cbcee326cdebfaed09b95f38fe267
ms.sourcegitcommit: 4f3883a9e85d0aaf2802b10433b221c3f1838d88
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/13/2020
ms.locfileid: "79285469"
---
# <a name="discovered-app-filters-and-queries"></a>Consultas y filtros de aplicaciones detectadas

*Se aplica a: Microsoft Cloud App Security*

Cuando tenga un gran número de aplicaciones detectadas, le resultará útil filtrarlas y consultarlas. En este artículo se describe qué filtros están disponibles y cómo consultar las aplicaciones detectadas.

## <a name="discovered-app-filters"></a>Filtros de aplicaciones detectadas

Hay filtros de aplicaciones detectadas básicos y avanzados. Para lograr un filtro complejo (como en el ejemplo anterior), use la opción avanzada, que incluye todos los filtros siguientes:

![Aplicaciones detectadas](media/discovered-apps.png)

- **Etiqueta de aplicación**: seleccione si la aplicación se ha autorizado o no y si no está etiquetada. Además, puede crear una etiqueta personalizada para la aplicación y usarla para filtrar tipos específicos de aplicaciones.
- **Aplicaciones y dominios**: permite buscar aplicaciones específicas o aplicaciones usadas en dominios concretos.
- **Categorías**: el filtro de categorías, situado a la izquierda de la página, permite buscar tipos de aplicaciones en función de categorías de aplicaciones. Las categorías de ejemplo incluyen aplicaciones de redes sociales, aplicaciones de almacenamiento en la nube y servicios de hospedaje. Puede seleccionar varias categorías a la vez o una sola categoría y, a continuación, aplicar los filtros básico y avanzado en la parte superior.
- **Factor de riesgo de cumplimiento**: permite buscar normas, certificaciones y cumplimiento específicos con los que puede cumplir la aplicación (HIPAA, ISO 27001, SOC 2, PCI-DSS, etc.).
- **Factor de riesgo general**: permite buscar factores de riesgo generales, como la popularidad del consumidor, la configuración regional del centro de datos, etc.
- **Puntuación de riesgo**: permite filtrar las aplicaciones por puntuación de riesgo para que pueda centrarse, por ejemplo, en la revisión de aplicaciones de gran riesgo. También puede reemplazar la puntuación de riesgo establecida por Cloud App Security. Para obtener más información, vea [trabajar con la puntuación de riesgo](risk-score.md).
- **Factor de riesgo para la seguridad**: permite filtrar en función de medidas de seguridad específicas (por ejemplo, cifrado en reposo, autenticación multifactor, etc.).
- **Uso**: permite filtrar en función de las estadísticas de uso de esta aplicación. Uso como aplicaciones con menos o más de un número especificado de cargas de **datos**, aplicaciones con más o menos de un número especificado de **usuarios**.
- **Factor de riesgo legal**: le permite filtrar en función de todas las regulaciones y directivas que están en contexto para garantizar la protección de los datos y la privacidad de los usuarios de la aplicación. Entre los ejemplos se incluyen aplicaciones en la nube, DMCA y Directiva de retención de datos lista para RGPD.

### <a name="creating-and-managing-custom-app-tags"></a>Crear y administrar etiquetas de aplicación personalizadas

Puede crear etiquetas de aplicación personalizadas.
Estas etiquetas pueden usarse como filtros para profundizar un poco más en los tipos de aplicaciones específicos que quiere investigar. Por ejemplo, lista de supervisión personalizada, asignación a una unidad de negocio específica o aprobaciones personalizadas (por ejemplo, "aprobado por el departamento legal").

Para crear una etiqueta de aplicación personalizada:

1. En el engranaje de **configuración** , seleccione **configuración de Cloud Discovery**, luego la pestaña Etiquetas de la **aplicación** . Haga clic en el icono de signo más. ![icono más](media/plus-icon.png)

   ![Crear una etiqueta de aplicación personalizada](media/create-app-tag.png)

2. Puede usar la tabla **etiquetas de aplicación** para ver qué aplicaciones están etiquetadas actualmente con cada etiqueta de aplicación y puede eliminar las etiquetas de aplicación que no se usan.

3. Para aplicar una etiqueta de aplicación, en la pestaña **aplicaciones detectadas** , haga clic en los tres puntos situados a la derecha del nombre de la aplicación. Seleccione la etiqueta de la aplicación que se va a aplicar.

> [!NOTE]
>También puede crear una etiqueta de aplicación directamente en la tabla **Aplicaciones detectadas**. Para ello, haga clic en **Create app tag** (Crear etiqueta de aplicación) después de seleccionar los tres puntos situados a la derecha de cualquier aplicación seleccionada. Al crear la etiqueta desde la aplicación detectada, puede aplicarla a la aplicación. También puede acceder a la pantalla etiquetas de la **aplicación** haciendo clic en el vínculo **administrar etiquetas** en la esquina.
> ![crear una etiqueta de aplicación personalizada desde la aplicación](media/create-app-tag-from-app.png)

## <a name="discovered-app-queries"></a>Consultas de aplicaciones detectadas

Para simplificar aún más la investigación, puede crear consultas personalizadas y guardarlas para su uso posterior.

1. En la página **aplicaciones detectadas** , use los filtros como se describió anteriormente para explorar en profundidad las aplicaciones según sea necesario.

2. Una vez que haya obtenido los resultados deseados, haga clic en el botón **Guardar como** situado en la esquina superior derecha de los filtros.

3. En el menú emergente **Guardar consulta** , asigne un nombre a la consulta.

    ![nueva consulta](media/new-query.png)

4. Para volver a usar esta consulta en el futuro, en **consultas**, desplácese hacia abajo hasta **consultas guardadas** y seleccione la consulta.

    ![abrir consulta](media/discovered-app-query.png)

Cloud App Security también proporciona **consultas sugeridas** y permite guardar las consultas personalizadas que se usan con frecuencia. Las consultas sugeridas le proporcionan vías de investigación recomendadas que filtran las aplicaciones detectadas mediante las siguientes consultas sugeridas opcionales:

- **Aplicaciones en la nube que permiten el uso anónimo** : filtra todas las aplicaciones detectadas para mostrar solo las aplicaciones que son riesgos de seguridad porque no requieren la autenticación del usuario y permiten a los usuarios cargar datos.

- **Aplicaciones en la nube con certificación CSA Star** : filtra todas las aplicaciones detectadas para mostrar solo las aplicaciones que tienen la certificación CSA Star mediante autoevaluación, certificación, atestación o supervisión continua.

- **Aplicaciones en la nube que son compatibles con FedRAMP** : filtra todas las aplicaciones detectadas para mostrar solo las aplicaciones cuyo factor de riesgo de cumplimiento de FedRAMP sea alto, medio o bajo.

- **Aplicaciones de almacenamiento en la nube y de colaboración que poseen datos de usuario** : filtra todas las aplicaciones detectadas para mostrar solo las aplicaciones que son arriesgadas porque no permiten tener la propiedad de los datos, pero conservan los datos.

- **Aplicaciones de almacenamiento en la nube que son arriesgadas y no compatibles** : filtra todas las aplicaciones detectadas para mostrar solo las aplicaciones en las que no cumplen los requisitos de SOC 2 o HIPAA, no admiten PCI DSS versión y tienen una puntuación de riesgo de 5 o inferior.

- **Aplicaciones de nube de empresa con autenticación débil** : filtra todas las aplicaciones detectadas para mostrar solo las aplicaciones que no son compatibles con SAML, no tienen ninguna directiva de contraseñas y no habilitan MFA.

- **Aplicaciones empresariales en la nube con cifrado débil** : filtra todas las aplicaciones detectadas para mostrar solo las aplicaciones que son arriesgadas porque no cifran los datos en reposo y no admiten ningún protocolo de cifrado.

- **RGPD Ready Cloud apps** : filtra todas las aplicaciones detectadas para mostrar solo las aplicaciones que están listas para RGPD. Dado que el cumplimiento de RGPD es una prioridad máxima, esta consulta le ayuda a identificar fácilmente las aplicaciones que están listas para RGPD y a mitigar la amenaza mediante la evaluación del riesgo de las que no lo son.

![consulta de aplicaciones detectadas](media/queries-discovered-apps.png)

Además, puede usar las consultas sugeridas como punto de partida para una nueva consulta. En primer lugar, seleccione una de las consultas sugeridas. A continuación, realice los cambios necesarios y, por último, haga clic en **Guardar como** para crear una nueva **consulta guardada**.

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Crear informes de instantáneas de Cloud Discovery](create-snapshot-cloud-discovery-reports.md)

> [!div class="nextstepaction"]
> [Configurar la carga de registros automática para informes continuos](configure-automatic-log-upload-for-continuous-reports.md)

> [!div class="nextstepaction"]
> [Trabajar con datos de Cloud Discovery](working-with-cloud-discovery-data.md)
