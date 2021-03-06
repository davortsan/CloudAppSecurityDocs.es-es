---
title: Bloqueo de aplicaciones detectadas
description: En este artículo se describe el procedimiento para exportar scripts de bloqueo para aplicaciones detectadas.
ms.date: 12/12/2019
ms.topic: how-to
ms.openlocfilehash: ee1deba23e7f2eb8ae002af414094b8912a03ac8
ms.sourcegitcommit: d87372b47ca98e942c2bf94032a6a61902627d69
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/30/2020
ms.locfileid: "96314858"
---
# <a name="govern-discovered-apps"></a>Control de aplicaciones detectadas

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Después de revisar la lista de aplicaciones detectadas en su entorno, puede proteger su entorno mediante la aprobación de aplicaciones seguras (**autorizadas**) o la prohibición de las aplicaciones no deseadas (no **autorizadas**) de las siguientes maneras.

## <a name="sanctioningunsanctioning-an-app"></a><a name="BKMK_SanctionApp"></a> Autorizar o no autorizar una aplicación

Puede no autorizar una aplicación de riesgo específica. Para ello, haga clic en los tres puntos situados al final de la fila. Después seleccione **No autorizar**. El hecho de no autorizar una aplicación no impide que se use, pero le permite supervisar más fácilmente su uso con los filtros de Cloud Discovery. Después, puede notificar a los usuarios de la aplicación que no está autorizada y sugerir una aplicación segura alternativa.

![Etiquetar como no autorizada](media/tag-as-unsanctioned.png)

Si tiene una lista de aplicaciones que quiere autorizar o no autorizar, active la casilla de todas las aplicaciones que quiere administrar y después seleccione la acción.

Para consultar una lista de las aplicaciones no autorizadas, puede [generar un script de bloque mediante las API de Cloud App Security](api-discovery-script.md).

> [!NOTE]
> Si el inquilino usa Microsoft defender para el punto de conexión, Zscaler NSS o iboss, las aplicaciones marcadas como no autorizadas se bloquean automáticamente mediante Cloud App Security y las siguientes secciones sobre la creación de scripts de bloqueo son innecesarias. Para obtener más información, consulte [integración con Microsoft defender para el punto de conexión](mde-integration.md), [integración con Zscaler](zscaler-integration.md)e [integración con iboss](iboss-integration.md) , respectivamente.

## <a name="export-a-block-script-to-govern-discovered-apps"></a>Exportar un script de bloque para controlar aplicaciones detectadas

Cloud App Security permite bloquear el acceso a aplicaciones no autorizadas con el uso de sus aplicaciones locales de seguridad. Puede generar un script de bloqueo dedicado e importarlo al la aplicación. Esta solución no requiere redireccionar todo el tráfico web de la organización a un proxy.

1. En el panel de Cloud Discovery, etiquete las aplicaciones que quiere bloquear como **No autorizada**.

    ![Etiquetar como no autorizada](media/tag-as-unsanctioned.png)

2. En la barra de título, haga clic en los tres puntos y seleccione **Generar script de bloque...**.

    ![Generación de scripts de bloques](media/generate-block-script.png)

3. En **Generar script de bloque**, seleccione la aplicación para la que quiere generar el script de bloque.

    ![Ventana emergente de Generar script de bloqueo](media/generate-block-script-pop-up.png)

4. Después, haga clic en el botón Generar script para crear un script de bloqueo para todas las aplicaciones no autorizadas. De forma predeterminada, se asignará un nombre al archivo con la fecha en la que se haya exportado y el tipo de aplicación que haya seleccionado. *2017-02-19_CAS_Fortigate_block_script.txt* sería un nombre de archivo de ejemplo

   ![Botón Generar script de bloque](media/generate-block-script-button.png)

5. Importe el archivo que ha creado en la aplicación.

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Actividades diarias para proteger el entorno de nube](daily-activities-to-protect-your-cloud-environment.md)

[!INCLUDE [Open support ticket](includes/support.md)]
