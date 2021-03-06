---
title: Crear directivas en Cloud Discovery aplicaciones
description: En este artículo se proporciona información sobre cómo trabajar con directivas de Cloud Discovery.
ms.date: 01/05/2021
ms.topic: how-to
ms.openlocfilehash: 9c892eed6b1200fb658a9ea03a77eeb0a98078f8
ms.sourcegitcommit: ee66e70f711aa11501e308e53b1a4b46f2175e4e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/05/2021
ms.locfileid: "97894712"
---
# <a name="create-cloud-discovery-policies"></a>Crear directivas de Cloud Discovery

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Puede crear directivas de detección de aplicaciones para que se le envíen alertas cuando se detecten nuevas aplicaciones. Cloud App Security también busca en todos los registros de Cloud Discovery para comprobar si hay anomalías.

## <a name="creating-an-app-discovery-policy"></a>Crear una directiva de detección de aplicaciones

Las directivas de detección permiten establecer alertas que avisan cuando se detectan nuevas aplicaciones en la organización.

1. Vaya a **control**  >  **directivas**  >  **Shadow it**.

1. Haga clic en **Crear directiva** y seleccione **Directiva de detección de aplicaciones**.

    ![Creación de una directiva de Cloud Discovery](media/create-policy-from-shadow-it-tab.png)

1. Proporcione un nombre y una descripción para la directiva. Si quiere, puede basarse en una plantilla. Para obtener más información sobre las plantillas de directiva, vea [Controlar las aplicaciones en la nube con directivas](control-cloud-apps-with-policies.md).

1. Establezca la **gravedad** de la directiva.

1. Agregue filtros para definir qué aplicaciones detectadas van a activar esta directiva.

1. Puede establecer el umbral de sensibilidad de la directiva. Habilite la opción **Desencadenar una coincidencia de directiva si todo lo siguiente sucede en el mismo día**. Puede establecer los criterios que la aplicación debe superar diariamente para que coincida con la directiva. Seleccione uno de estos criterios:
    - Tráfico diario
    - Datos descargados
    - Número de direcciones IP
    - Número de transacciones
    - Número de usuarios
    - Datos cargados

1. Establezca un **límite de alertas diarias** en **Alertas**. Seleccione si quiere que la alerta se envíe como mensaje de correo electrónico, de texto o ambos. A continuación, proporcione números de teléfono y direcciones de correo electrónico según sea necesario.
    - Al hacer clic en **Guardar configuración de alertas como valor predeterminado para la organización**, permitirá que se use la configuración para futuras directivas.
    - Si tiene una configuración predeterminada, puede seleccionar **Usar la configuración predeterminada de la organización**.

1. Seleccione las acciones de **gobernanza** que se aplicarán cuando una aplicación coincida con esta directiva. Es posible etiquetar las directivas como **autorizadas** o **no autorizadas**, o bien una etiqueta personalizada.

1. Haga clic en **Crear**.

> [!NOTE]
>
> - Las directivas de detección creadas recientemente (o las directivas con informes continuos actualizados) desencadenan una alerta una vez en 90 días por cada aplicación de informe continuo, independientemente de si hay alertas existentes para la misma aplicación. Por lo tanto, por ejemplo, si crea una directiva para la detección de nuevas aplicaciones populares, puede desencadenar alertas adicionales para las aplicaciones que ya se han detectado y alertar.
> - Los datos de los **informes de instantáneas** no desencadenan alertas en las directivas de detección de aplicaciones.

Si, por ejemplo, le interesa detectar las aplicaciones de hospedaje de riesgo que hay en su entorno en la nube, establezca la directiva de la siguiente forma:

Establezca los filtros de directiva para detectar los servicios que se encuentren en la categoría **Servicios de hospedaje** y que tengan una puntuación de riesgo de 1, lo que indica un riesgo elevado.

Establezca los umbrales que deben desencadenar una alerta para una determinada aplicación detectada en la parte inferior. Por ejemplo, defina que se envíe una alerta solo si más de 100 usuarios del entorno han usado la aplicación y si han descargado una cantidad determinada de datos del servicio. También puede establecer el límite de alertas diarias que quiere recibir.

![ejemplo de directiva de detección de aplicaciones](media/app-discovery-policy-example.png "ejemplo de directiva de detección de aplicaciones")

## <a name="cloud-discovery-anomaly-detection"></a>Detección de anomalías de Cloud Discovery

Cloud App Security busca en todos los registros de Cloud Discovery para encontrar anomalías. Por ejemplo, cuando un usuario que nunca ha usado Dropbox de repente carga 600 GB o cuando hay muchas más transacciones de lo habitual en una aplicación determinada. La directiva de detección de anomalías está habilitada de forma predeterminada. No es necesario configurar ninguna directiva nueva para que funcione. Pero puede ajustar los tipos de anomalías sobre los que quiere que se le envíen alertas en la directiva predeterminada.

1. En la consola, haga clic en **Control**, seguido de **Directivas**.

1. Haga clic en **Crear directiva** y seleccione la directiva **Detección de anomalías de Cloud Discovery**.

    ![menú de directiva de detección de anomalías de Cloud Discovery](media/cloud-discovery-anomaly-detection-policy-menu.png "menú de directiva de detección de anomalías de Cloud Discovery")

1. Proporcione un nombre y una descripción para la directiva. Si quiere, puede basarse en una plantilla. Para obtener más información sobre las plantillas de directiva, vea [Controlar aplicaciones en la nube con directivas](control-cloud-apps-with-policies.md).

1. Haga clic en **Agregar filtros** para definir qué aplicaciones detectadas van a activar esta directiva.

    Los filtros se eligen en las listas desplegables. Para agregar filtros, haga clic en el botón del signo más. Para quitar un filtro, haga clic en la "X".

1. En **Aplicar a**, elija si esta directiva se aplica a **Todos los informes continuos** o a **Informes continuos específicos**. Seleccione si la directiva se aplica a **Usuarios**, **Direcciones IP** o a ambos.

1. Seleccione las fechas en las que se ha producido la actividad anómala para activar la alerta en **Generar alertas solo para las actividades sospechosas que se produzcan después de la fecha**.

1. Establezca un **límite de alertas diarias** en **Alertas**. Seleccione si quiere que la alerta se envíe como mensaje de correo electrónico, de texto o ambos. A continuación, proporcione números de teléfono y direcciones de correo electrónico según sea necesario.
    - Al hacer clic en **Guardar configuración de alertas como valor predeterminado para la organización**, permitirá que se use la configuración para futuras directivas.
    - Si tiene una configuración predeterminada, puede seleccionar **Usar la configuración predeterminada de la organización**.

1. Haga clic en **Crear**.

    ![nueva directiva de detección de anomalías](media/new-discovery-anomaly-policy.png "nueva directiva de detección de anomalías")

## <a name="related-videos"></a>Vídeos relacionados

> [!div class="nextstepaction"]
> [Seminario Web de configuración del recopilador de registros y de detección de aplicaciones](webinars.md#on-demand-webinars)

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Directivas de actividad de usuario](user-activity-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]
