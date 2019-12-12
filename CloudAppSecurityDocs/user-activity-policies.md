---
title: Creación de directivas para controlar actividades en Cloud App Security
description: En este artículo se proporcionan instrucciones para crear directivas de actividad y trabajar con ellas.
author: shsagir
ms.author: shsagir
ms.service: cloud-app-security
ms.topic: conceptual
ms.date: 8/15/2019
ms.collection: M365-security-compliance
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 5272eec53b28fd55886586d06a035f36f70e6e8f
ms.sourcegitcommit: 6eff466c7a6817b14a60d8c3b2c201c7ae4c2e2c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "74720442"
---
# <a name="activity-policies"></a>Directivas de actividad

*Se aplica a: Microsoft Cloud App Security*

Las directivas de actividad permiten aplicar toda una variedad de procesos automatizados usando las API del proveedor de aplicaciones. Estas directivas permiten supervisar actividades concretas realizadas por distintos usuarios o seguir niveles inesperadamente altos de un determinado tipo de actividad.

Una vez que se ha establecido una directiva de detección de actividad, empieza a generar alertas, pero únicamente para las actividades que se producen después de haber creado la directiva.

## <a name="custom-alerts"></a>Alertas personalizadas

Las directivas de actividad permiten enviar alertas personalizadas o realizar acciones cuando se detecta actividad del usuario. Por ejemplo, quiere saber cada vez que ocurre lo siguiente:

- Un usuario intenta iniciar sesión y se produce un error 70 veces durante un minuto.
- Un usuario descarga 7000 archivos.
- Un usuario inicia sesión desde Afganistán.

Puede establecer que se le envíen alertas de actividad a usted o al usuario cuando se producen estos eventos. Incluso puede suspender el usuario hasta que haya terminado de investigar lo sucedido.

Para crear una nueva directiva de actividad, siga este procedimiento:

1. En la consola, haga clic en **Control**, seguido de **Directivas**.

2. Haga clic en **Crear directiva** y seleccione **Directiva de actividad**.

     ![menú de directiva de actividad](media/activity-policy-menu.png)

3. Asigne un nombre y una descripción a la directiva. Si quiere, puede basarla en una plantilla. Para obtener más información sobre las plantillas de directiva, vea [Controlar aplicaciones en la nube con directivas](control-cloud-apps-with-policies.md).

4. Para establecer qué acciones o qué otras métricas desencadenan esta directiva, trabaje con **filtros de actividad**.
    > [!NOTE]
    > Para asegurarse de que solo se incluyen los resultados en los que el campo de filtro especificado tiene un valor, se recomienda volver a agregar el mismo campo mediante la prueba **set** . Por ejemplo, si el filtrado por **Ubicación** *no es igual* a una lista especificada de países, agregue también un filtro para **Ubicación** *establecida*. También puede obtener una vista previa de los resultados del filtro seleccionando **Editar y vista previa de los resultados**.
    >
    > ![Captura de pantalla de la configuración del filtro, donde se muestra el campo Ubicación](media/activity-example-location-isset.png)

5. En **Activity match parameters** (Parámetros de coincidencia de actividad), seleccione cuándo se desencadenará una infracción de la directiva. Elija que se desencadene cuando una única actividad coincida con los filtros o solo cuando se detecte un número especificado de **actividades repetidas**.
    - Si elige **Actividad repetida**, puede establecer **En una única aplicación**. Esta configuración desencadenará una coincidencia de directiva solo cuando se producen las actividades repetidas en la misma aplicación. Por ejemplo, cinco descargas en 30 minutos desde Box desencadenan una coincidencia de directiva.

6. Configure las **acciones** que deben realizarse cuando se encuentra una coincidencia.

Observe estos ejemplos:

- Varios inicios de sesión erróneos

    Puede establecer la directiva de forma que reciba una alerta cuando se produce un gran número de inicios de sesión erróneos durante un breve período de tiempo. Para configurar este tipo de directiva, elija el filtro de actividad adecuado en la página **New Activity Policy** (Nueva directiva de actividad).

    Bajo el campo **Filtros de actividad**, configure los parámetros para los que se desencadenará la alerta.

    ![Ejemplo de directiva de varios intentos de inicio de sesión erróneos](media/multiple-failed-log-on-attempts-policy-example.png "ejemplo de directiva de varios intentos de inicio de sesión erróneos")

- Frecuencia de descarga alta

    Puede establecer la directiva de modo que reciba una alerta cuando se produzca un nivel de actividad de descarga inesperado o inusitado. Para configurar este tipo de directiva, en el parámetro **Frecuencia**, elija los parámetros que desencadenen la alerta.

    ![ejemplo de la frecuencia de descarga alta](media/high-download-rate-example.png "ejemplo de frecuencia de descarga alta")

## <a name="activity-policy-reference"></a>Referencia de directiva de actividad

En esta sección se proporciona información de referencia sobre directivas, se ofrecen explicaciones sobre cada tipo de directiva y se detallan los campos que se pueden configurar en cada directiva.

Una **directiva de actividad** es una directiva basada en API que le permite supervisar las actividades de la organización en la nube. La directiva tiene en cuenta más de 20 filtros de metadatos de archivo, incluidos el tipo de dispositivo y la ubicación. Basándose en los resultados de la directiva, se pueden generar notificaciones y se puede suspender a usuarios de la aplicación en la nube.
Cada directiva se compone de las siguientes partes:

- Filtros de actividad: permiten crear condiciones pormenorizadas basadas en metadatos.

- Parámetros de coincidencia de actividad: permiten establecer un umbral de número de veces que se repite una actividad para que se considere que coincide con la directiva.  Especifique el número de actividades repetidas necesarias para que coincida con la directiva. Por ejemplo, establezca una directiva para que alerte cuando un usuario intente iniciar sesión incorrectamente diez veces en un período de tiempo de dos minutos. De forma predeterminada, **Activity match parameter (Parámetro de coincidencia de actividad) genera una coincidencia para cada actividad única que cumple todos los filtros de la actividad.

  - Si usa **Actividad repetida**, puede establecer el número de actividades repetidas y el período de tiempo durante el que se cuentan las actividades. También puede especificar que todas las actividades debe realizarlas el mismo usuario y en la misma aplicación en la nube.

- Acciones: la directiva proporciona un conjunto de acciones de gobernanza que se pueden aplicar automáticamente cuando se detectan infracciones.

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Directivas de protección de datos](data-protection-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]
