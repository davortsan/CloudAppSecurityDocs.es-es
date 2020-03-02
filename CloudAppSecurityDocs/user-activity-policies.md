---
title: Crear directivas para controlar actividades en Cloud App Security
description: En este artículo se proporcionan instrucciones para crear y trabajar con directivas de actividad.
author: shsagir
ms.author: shsagir
ms.service: cloud-app-security
ms.topic: conceptual
ms.date: 03/01/2020
ms.collection: M365-security-compliance
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 87e25ce39cf7c3858db00af9dbe9d9141de2a48d
ms.sourcegitcommit: 828bbe923713b358fbd32f14e007bf7e5bccedbe
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/01/2020
ms.locfileid: "78207899"
---
# <a name="activity-policies"></a>Directivas de actividad

*Se aplica a: Microsoft Cloud App Security*

Las directivas de actividad permiten aplicar una amplia gama de procesos automatizados mediante las API del proveedor de la aplicación. Estas directivas permiten supervisar actividades específicas realizadas por varios usuarios o seguir tasas inesperadamente altas de un determinado tipo de actividad.

Después de establecer una directiva de detección de actividad, comienza a generar alertas: las alertas solo se generan en las actividades que se producen después de crear la Directiva.

> [!NOTE]
> Las directivas que desencadenan más de 50.000 coincidencias al día, durante 3 de los últimos 7 días, se deshabilitan automáticamente. Puede intentar refinar las directivas agregando filtros adicionales o, si usa directivas para la elaboración de informes, considere la posibilidad de [guardarlas como consultas](activity-filters-queries.md#activity-queries) en su lugar.

## <a name="custom-alerts"></a>Alertas personalizadas

Las directivas de actividad permiten el envío de alertas personalizadas o las acciones que se llevan a cabo cuando se detecta actividad del usuario. Por ejemplo, desea saber cada vez:

- Un usuario intenta iniciar sesión y produce un error 70 veces en un minuto
- Un usuario descarga 7.000 archivos
- Un usuario ha iniciado sesión desde Afganistán

Puede establecer alertas de actividad que se enviarán a usted mismo o al usuario cuando se produzcan estos eventos. Incluso puede suspender el usuario hasta que haya terminado de investigar lo que ha sucedido.

Para crear una nueva Directiva de actividad, siga este procedimiento:

1. En la consola de, haga clic en **control** y luego en **directivas**.

2. Haga clic en **crear Directiva** y seleccione **Directiva de actividad**.

     ![menú de directiva de actividad](media/activity-policy-menu.png)

3. Asigne un nombre y una descripción a la Directiva, si quiere basarla en una plantilla, para obtener más información sobre las plantillas de Directiva, vea [controlar aplicaciones en la nube con directivas](control-cloud-apps-with-policies.md).

4. Para establecer qué acciones u otras métricas van a activar esta Directiva, trabaje con los **filtros de actividad**.
    > [!NOTE]
    > Para asegurarse de que solo se incluyen los resultados en los que el campo de filtro especificado tiene un valor, se recomienda volver a agregar el mismo campo mediante la prueba **set** . Por ejemplo, si el filtrado por **Ubicación** *no es igual* a una lista especificada de países, agregue también un filtro para **Ubicación** *establecida*. También puede obtener una vista previa de los resultados del filtro seleccionando **Editar y vista previa de los resultados**.
    >
    > ![Captura de pantalla de la configuración del filtro, donde se muestra el campo Ubicación](media/activity-example-location-isset.png)

5. En **parámetros de coincidencia de actividad**, seleccione cuando se desencadenará una infracción de directiva. Elija desencadenador cuando una sola actividad coincida con los filtros o solo cuando se detecte un número especificado de **actividades repetidas** .
    - Si elige **actividad repetida**, puede establecer **en una sola aplicación**. Esta configuración desencadenará una coincidencia de directiva solo cuando se produzcan las actividades repetidas en la misma aplicación. Por ejemplo, cinco descargas en 30 minutos desde Box desencadenan una coincidencia de directiva.

6. Configure las **acciones** que deben realizarse cuando se encuentra una coincidencia.

Eche un vistazo a estos ejemplos:

- Varios inicios de sesión erróneos

    Puede establecer la Directiva de modo que reciba una alerta cuando se produzca un gran número de inicios de sesión erróneos durante un breve período de tiempo. Para configurar este tipo de Directiva, elija el filtro de actividad adecuado en la página **nueva Directiva de actividad** .

    Debajo del campo **filtros de actividad** , configure los parámetros para los que se desencadenará la alerta.

    ![Ejemplo de directiva de varios intentos de inicio de sesión erróneos](media/multiple-failed-log-on-attempts-policy-example.png "ejemplo de directiva de varios intentos de inicio de sesión erróneos")

- Alta tasa de descarga

    Puede establecer la Directiva de modo que reciba una alerta cuando se produzca un nivel de actividad de descarga inesperado o inesperado. Para configurar este tipo de Directiva, en parámetros de **frecuencia** , elija los parámetros para desencadenar la alerta.

    ![ejemplo de la frecuencia de descarga alta](media/high-download-rate-example.png "ejemplo de la frecuencia de descarga alta")

## <a name="activity-policy-reference"></a>Referencia de directiva de actividad

Esta sección contiene detalles de referencia sobre directivas, explicaciones para cada tipo de directiva y los campos que se pueden configurar para cada Directiva.

Una **Directiva de actividad** es una directiva basada en API que permite supervisar las actividades de la organización en la nube. La Directiva tiene en cuenta más de 20 filtros de metadatos de archivo, como el tipo de dispositivo y la ubicación. En función de los resultados de la Directiva, se pueden generar notificaciones y se pueden suspender los usuarios de la aplicación en la nube.
Cada Directiva se compone de las partes siguientes:

- Filtros de actividad: permiten crear condiciones granulares basadas en metadatos.

- Parámetros de coincidencia de actividad: permiten establecer un umbral para el número de veces que se repite una actividad para que se considere que coincide con la Directiva.  Especifique el número de actividades repetidas que deben coincidir con la Directiva. Por ejemplo, establezca una directiva para alertar cuando un usuario tenga 10 intentos de inicio de sesión incorrectos en un período de tiempo de dos minutos. De forma predeterminada, el parámetro * * coincidencia de actividad genera una coincidencia para cada actividad única que cumple todos los filtros de actividad.

  - Con la **actividad repetida** puede establecer el número de actividades repetidas, la duración del período de tiempo en el que se cuentan las actividades. También puede especificar que todas las actividades las debe realizar el mismo usuario y en la misma aplicación en la nube.

- Acciones: la Directiva proporciona un conjunto de acciones de gobierno que se pueden aplicar automáticamente cuando se detectan infracciones.

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Directivas de protección de datos](data-protection-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]
