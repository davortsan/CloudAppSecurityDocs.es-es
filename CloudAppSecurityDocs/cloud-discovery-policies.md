---
title: 'Crear directivas en Cloud Discovery aplicaciones: Cloud App Security | Microsoft Docs'
description: En este artículo se proporciona información sobre cómo trabajar con directivas de Cloud Discovery.
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
ms.openlocfilehash: d3b5b62664abc9e82ad726e60c5105ef29ae0b16
ms.sourcegitcommit: 4f3883a9e85d0aaf2802b10433b221c3f1838d88
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/13/2020
ms.locfileid: "79285489"
---
# <a name="cloud-discovery-policies"></a>Directivas de Cloud Discovery

*Se aplica a: Microsoft Cloud App Security*

Puede crear directivas de detección de aplicaciones para avisarle cuando se detecten nuevas aplicaciones. Cloud App Security también busca anomalías en todos los registros de la Cloud Discovery.

## <a name="creating-an-app-discovery-policy"></a>Creación de una directiva de detección de aplicaciones

Las directivas de detección permiten establecer alertas que le notifican cuando se detectan nuevas aplicaciones en la organización.

1. En la consola de, haga clic en **control** y luego en **directivas**.

2. Haga clic en **crear Directiva** y seleccione **Directiva de detección de aplicaciones**.

    ![menú de directiva de detección de aplicaciones](media/app-discovery-policy-menu.png "menú de directiva de detección de aplicaciones")

3. Asigne un nombre y una descripción a la Directiva. Si lo desea, puede basarla en una plantilla. Para obtener más información sobre las plantillas de Directiva, vea [controlar aplicaciones en la nube con directivas](control-cloud-apps-with-policies.md).

4. Establezca la **gravedad** de la Directiva.

5. Para establecer qué aplicaciones detectadas desencadenan esta Directiva, agregue filtros.

6. Puede establecer un umbral para el grado de confidencialidad de la Directiva. Habilitar **desencadenar una coincidencia de Directiva si se producen todas las acciones siguientes en el mismo día**. Puede establecer los criterios que la aplicación debe superar diariamente para que coincida con la Directiva. Seleccione uno de los siguientes criterios:
    - Tráfico diario
    - Datos descargados
    - Número de direcciones IP
    - Número de transacciones
    - Número de usuarios
    - Datos cargados

7. Establezca un **límite de alertas diarias** en **alertas**. Seleccione si la alerta se envía como correo electrónico, mensaje de texto o ambos. A continuación, proporcione los números de teléfono y las direcciones de correo electrónico según sea necesario.
    - Al hacer clic en **Guardar configuración de alertas como valor predeterminado para su organización,** se habilitan las directivas futuras para usar la configuración.
    - Si tiene una configuración predeterminada, puede seleccionar **usar la configuración predeterminada de su organización**.

8. Seleccione las acciones de **gobierno** que se aplicarán cuando una aplicación coincida con esta Directiva. Puede etiquetar directivas como **autorizadas**, no **autorizadas**o una etiqueta personalizada.

9. Haga clic en **Crear**.

Por ejemplo, si está interesado en detectar las aplicaciones de hospedaje de riesgo que se encuentran en el entorno de nube, establezca la Directiva de la siguiente manera:

Establezca los filtros de directiva para detectar los servicios que se encuentren en la categoría **servicios de hospedaje** y que tengan una puntuación de riesgo de 1, lo que indica que son muy arriesgados.

 Establezca los umbrales que deben desencadenar una alerta para una determinada aplicación detectada en la parte inferior. Por ejemplo, alertar solo si más de 100 usuarios del entorno usó la aplicación y si descargaron una determinada cantidad de datos del servicio.
Además, puede establecer el límite de alertas diarias que quiere recibir.

![ejemplo de directiva de detección de aplicaciones](media/app-discovery-policy-example.png "ejemplo de directiva de detección de aplicaciones")

## <a name="cloud-discovery-anomaly-detection"></a>Detección de anomalías Cloud Discovery

Cloud App Security busca anomalías en todos los registros de la Cloud Discovery. Por ejemplo, cuando un usuario, que nunca usaba Dropbox antes, carga repentinamente 600 GB en él, o cuando hay muchas más transacciones de las habituales en una aplicación determinada. La Directiva de detección de anomalías está habilitada de forma predeterminada. No es necesario configurar una nueva Directiva para que funcione. Sin embargo, puede ajustar los tipos de anomalías sobre los que desea recibir alertas en la directiva predeterminada.

1. En la consola de, haga clic en **control** y luego en **directivas**.

2. Haga clic en **crear Directiva** y seleccione **Cloud Discovery Directiva de detección de anomalías**.

    ![menú de directiva de detección de anomalías de Cloud Discovery](media/cloud-discovery-anomaly-detection-policy-menu.png "menú de directiva de detección de anomalías de Cloud Discovery")

3. Asigne un nombre y una descripción a la Directiva. Si lo desea, puede basarla en una plantilla. para obtener más información sobre las plantillas de Directiva, vea [controlar aplicaciones en la nube con directivas](control-cloud-apps-with-policies.md).

4. Para establecer qué aplicaciones detectadas desencadenan esta Directiva, haga clic en **Agregar filtros**.

    Los filtros se eligen en las listas desplegables. Para agregar filtros, haga clic en el botón más. Para quitar un filtro, haga clic en la "X".

5. En **aplicar a** , elija si esta directiva aplica **todos los informes continuos** o **informes continuos específicos**. Seleccione si la Directiva se aplica a **usuarios**, a **direcciones IP**o a ambos.

6. Seleccione las fechas en las que se produjo la actividad anómala para activar la alerta en **generar alertas solo para las actividades sospechosas que se produzcan después de la fecha.**

7. Establezca un **límite de alertas diarias** en **alertas**. Seleccione si la alerta se envía como correo electrónico, mensaje de texto o ambos. A continuación, proporcione los números de teléfono y las direcciones de correo electrónico según sea necesario.
    - Al hacer clic en **Guardar configuración de alertas como valor predeterminado para su organización,** se habilitan las directivas futuras para usar la configuración.
    - Si tiene una configuración predeterminada, puede seleccionar **usar la configuración predeterminada de su organización**.

8. Haga clic en **Crear**.

![nueva Directiva de anomalías de detección](media/new-discovery-anomaly-policy.png "nueva Directiva de anomalías de detección")

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Directivas de actividad de usuario](user-activity-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]
