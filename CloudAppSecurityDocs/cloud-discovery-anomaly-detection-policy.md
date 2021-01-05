---
title: Creación de una directiva de detección de anomalías de Cloud Discovery en Cloud App Security
description: En este tema se proporciona información sobre cómo trabajar con directivas de detección de anomalías de Cloud Discovery.
ms.date: 01/03/2021
ms.topic: how-to
ms.openlocfilehash: 355512b116850d28beb2953315d30260ed0596d2
ms.sourcegitcommit: 16a65ab2c8ca778d0b3cfa97b847af4c812363b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/03/2021
ms.locfileid: "97855717"
---
# <a name="cloud-discovery-anomaly-detection-policy"></a>Directiva de detección de anomalías de Cloud Discovery

[!INCLUDE [Banner for top of topics](includes/banner.md)]

En este artículo se proporciona información de referencia sobre las directivas. Se muestran las explicaciones de cada tipo de directiva y los campos que se pueden configurar para cada directiva.

## <a name="cloud-discovery-anomaly-detection-policy-reference"></a>Referencia de directiva de detección de anomalías de Cloud Discovery

Una Cloud Discovery Directiva de detección de anomalías permite configurar y configurar la supervisión continua de aumentos inusuales en el uso de aplicaciones en la nube. Para ello, se tienen en cuenta los aumentos de datos descargados, los datos cargados, las transacciones y el número de usuarios de cada aplicación en la nube. Cada incremento se compara con el patrón de uso normal de la aplicación, según se desprende de usos anteriores. Los aumentos más acusados desencadenan alertas de seguridad.

Para cada directiva, se establecen filtros que permiten supervisar selectivamente el uso de la aplicación. Los filtros incluyen un filtro de aplicación, vistas de datos seleccionadas y una fecha de inicio seleccionada. También puede establecer la sensibilidad, que le permite establecer cuántas alertas debe activar la directiva.

1. Vaya a **control**  >  **directivas**  >  **Shadow it**.

1. Haga clic en **Crear directiva** y seleccione la directiva **Detección de anomalías de Cloud Discovery**.

    ![Creación de una directiva de Cloud Discovery](media/create-policy-from-shadow-it-tab.png)

Para cada directiva, establezca los siguientes parámetros:

1. Decida si quiere basar la directiva en una plantilla. Una plantilla de directiva relevante es **Comportamiento anómalo en usuarios detectados**. Alerta cuando se detecta un comportamiento anómalo en los usuarios y aplicaciones detectados, como grandes cantidades de datos cargados en comparación con otros usuarios o grandes transacciones del usuario en comparación con su historial. También puede seleccionar la plantilla **Comportamiento anómalo de direcciones IP detectadas**. Esta plantilla alerta cuando se detecta un comportamiento anómalo en las direcciones IP y las aplicaciones detectadas, como grandes cantidades de datos cargados en comparación con otras direcciones IP o grandes transacciones de aplicaciones en comparación con el historial de la dirección IP.

1. Proporcione un **Nombre de la directiva** y una **Descripción**.

1. Cree un filtro para las aplicaciones que quiere supervisar haciendo clic en **Agregar filtro**.
   Puede seleccionar una aplicación específica, una **categoría** de aplicación o filtrar por **nombre**, **dominio** y **factor de riesgo**, y hacer clic en **Guardar**.

1. En **Apply to** (Aplicar a), establezca cómo quiere que se filtre el uso. El uso que se está supervisando se puede filtrar de dos maneras diferentes:

    - **Informes continuados**: seleccione si quiere supervisar **Todos los informes continuados**, el valor predeterminado, o elija **Informes continuados específicos** para supervisar.

        - Al seleccionar **All continuous reports** (Todos los informes continuados), cada aumento del uso se compara con el patrón de uso normal, según se desprende de todas las vistas de datos.
        - Al seleccionar **Informes continuados específicos**, cada aumento del uso se compara con el patrón de uso normal. El patrón se desprende de la misma vista de datos en la que se ha observado el aumento.

    - **Usuarios y direcciones IP**: cada uso de la aplicación en la nube está asociado con un usuario, con una dirección IP o con ambos.

        - Si se selecciona **Usuarios**, se ignora la asociación de uso de la aplicación con direcciones IP.

        - Si se selecciona **Direcciones IP**, se ignora la asociación de uso de la aplicación con usuarios.

        - Si se selecciona **Usuarios y direcciones IP** (el valor predeterminado), se tienen en cuenta ambas asociaciones, pero se pueden generar alertas duplicadas cuando haya una correspondencia estricta entre usuarios y direcciones IP.

    - **Desencadenar alertas solo para detectar actividades sospechosas ocurridas tras una fecha**: se ignora cualquier aumento en el uso de la aplicación antes de la fecha seleccionada. En cambio, la actividad previa a la fecha seleccionada se tiene en cuenta para establecer el patrón de uso normal.

1. En **Alertas** puede establecer la sensibilidad de la alerta. Hay varias formas de controlar el número de alertas activadas por la directiva:

    - El control deslizante **Select anomaly detection sensitivity** (Seleccionar la sensibilidad de la detección de anomalías): desencadena alertas para las X actividades anómalas superiores por cada 1.000 usuarios por semana. Se activarán las alertas de las actividades con el riesgo más alto.

    - **Límite de alertas diarias**: restrinja el número de alertas activadas en un solo día. Puede seleccionar si quiere **Enviar alerta por correo electrónico**, **Enviar alerta como mensaje de texto** o ambas opciones. Los mensajes enviados por mensaje de texto se limitan a diez por día para la zona horaria UTC, lo que significa que el límite de diez mensajes se restablece a medianoche en la zona horaria UTC.

    - También puede seleccionar la opción de **Usar configuración predeterminada de la organización**. Esta opción rellena la configuración de **Límite de alertas diarias**, correo electrónico y mensaje de texto de la configuración predeterminada de la organización. Para establecer el valor predeterminado, rellene la **Configuración de alerta** y haga clic en **Guardar esta configuración de alerta como el valor predeterminado para su organización**.

1. Haga clic en **Crear**.

1. Como con todas las directivas, puede **Editar**, **Deshabilitar** y **Habilitar** la directiva haciendo clic en los tres puntos al final de la fila en la página **Directivas**. De forma predeterminada, la directiva está habilitada después de crearla.

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Actividades diarias para proteger el entorno de nube](daily-activities-to-protect-your-cloud-environment.md)

[!INCLUDE [Open support ticket](includes/support.md)]
