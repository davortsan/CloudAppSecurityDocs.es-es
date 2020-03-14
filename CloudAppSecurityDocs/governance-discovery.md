---
title: 'Bloqueo de aplicaciones detectadas: Cloud App Security | Microsoft Docs'
description: En este artículo se describe el procedimiento para exportar scripts de bloque para aplicaciones detectadas.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 12/12/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: bc95cb2272d996752c60c49c7f7402550325b208
ms.sourcegitcommit: 4f3883a9e85d0aaf2802b10433b221c3f1838d88
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/13/2020
ms.locfileid: "79285529"
---
# <a name="govern-discovered-apps"></a>Control de aplicaciones detectadas

*Se aplica a: Microsoft Cloud App Security*

Después de revisar la lista de aplicaciones detectadas en su entorno, puede proteger su entorno mediante la aprobación de aplicaciones seguras (**autorizadas**) o la prohibición de las aplicaciones no deseadas (no**autorizadas**) de las siguientes maneras.

## <a name="BKMK_SanctionApp"></a>Autorizar o no autorizar una aplicación

Puede no autorizar una aplicación de riesgo específica si hace clic en los tres puntos al final de la fila. Después, seleccione no **autorizar**. No autorizar una aplicación no bloquea el uso, pero le permite supervisar más fácilmente su uso con los filtros de Cloud Discovery. Después, puede notificar a los usuarios de la aplicación no autorizada y sugerir una aplicación segura alternativa para su uso.

![Etiquetar como no autorizada](media/tag-as-unsanctioned.png)

Si tiene una lista de aplicaciones que quiere autorizar o no autorizar, use la casilla para seleccionar las aplicaciones que quiere administrar y, después, seleccione la acción.

Para consultar una lista de aplicaciones no autorizadas, puede [generar un script de bloque mediante el Cloud App Security API](https://us.portal.cloudappsecurity.com/api-docs/#generate-block-script).

> [!NOTE]
> Si el inquilino usa protección contra amenazas avanzada (ATP) de Microsoft defender, Zscaler NSS o iboss, las aplicaciones marcadas como no autorizadas se bloquean automáticamente mediante Cloud App Security y las siguientes secciones sobre la creación de scripts de bloqueo son innecesarias. Para obtener más información, consulte [integración con Microsoft defender ATP](wdatp-integration.md), [integración con Zscaler](zscaler-integration.md)e [integración con iboss](iboss-integration.md) , respectivamente.

## <a name="export-a-block-script-to-govern-discovered-apps"></a>Exportar un script de bloque para controlar las aplicaciones detectadas

Cloud App Security permite bloquear el acceso a aplicaciones no autorizadas mediante el uso de los dispositivos de seguridad locales existentes. Puede generar un script de bloque dedicado e importarlo en el dispositivo. Esta solución no requiere la redirección de todo el tráfico web de la organización a un proxy.

1. En el panel de Cloud Discovery, etiquete las aplicaciones que quiera bloquear como no **autorizadas**.

    ![Etiquetar como no autorizada](media/tag-as-unsanctioned.png)

2. En la barra de título, haga clic en los tres puntos y seleccione **generar script de bloque..** ..

    ![Generar script de bloque](media/generate-block-script.png)

3. En **generar script de bloque**, seleccione el dispositivo para el que desea generar el script de bloque.

    ![Cuadro emergente generar script de bloque](media/generate-block-script-popup.png)

4. A continuación, haga clic en el botón generar script para crear un script de bloque para todas las aplicaciones no autorizadas. De forma predeterminada, el archivo se denominará con la fecha en la que se exportó y el tipo de dispositivo seleccionado. *2017-02-19_CAS_Fortigate_block_script. txt* sería un nombre de archivo de ejemplo

   ![Botón generar script de bloque](media/generate-block-script-button.png)

5. Importe el archivo creado en el dispositivo.

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Actividades diarias para proteger el entorno de nube](daily-activities-to-protect-your-cloud-environment.md)

[!INCLUDE [Open support ticket](includes/support.md)]
