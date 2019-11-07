---
title: 'Bloqueo de aplicaciones detectadas: Cloud App Security | Microsoft Docs'
description: En este artículo se describe el procedimiento para exportar scripts de bloqueo para aplicaciones detectadas.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 11/06/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 49fb3555da13a013655850b089f590821e3e7cb3
ms.sourcegitcommit: 2a52a0f00d2c8317964d4e15aca8925ccd107a38
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/06/2019
ms.locfileid: "73650916"
---
# <a name="govern-discovered-apps"></a>Controlar las aplicaciones detectadas

*Se aplica a: Microsoft Cloud App Security*

Después de revisar la lista de aplicaciones detectadas en su entorno, puede proteger su entorno mediante la aprobación de aplicaciones seguras (**autorizadas**) o la prohibición de las aplicaciones no deseadas (no**autorizadas**) de las siguientes maneras.

## <a name="BKMK_SanctionApp"></a> Autorizar o no autorizar una aplicación

Puede no autorizar una aplicación de riesgo específica. Para ello, haga clic en los tres puntos situados al final de la fila. Después seleccione **No autorizar**. El hecho de no autorizar una aplicación no impide que se use, pero le permite supervisar más fácilmente su uso con los filtros de Cloud Discovery. Después, puede notificar a los usuarios de la aplicación que no está autorizada y sugerir una aplicación segura alternativa.

![Etiquetar como no autorizada](./media/tag-as-unsanctioned.png)

Si tiene una lista de aplicaciones que quiere autorizar o no autorizar, active la casilla de todas las aplicaciones que quiere administrar y después seleccione la acción.

Para consultar una lista de las aplicaciones no autorizadas, puede [generar un script de bloque mediante las API de Cloud App Security](https://us.portal.cloudappsecurity.com/api-docs/#generate-block-script).

> [!NOTE]
> Si el inquilino usa Zscaler NSS o iboss, las aplicaciones marcadas como no autorizadas se bloquean automáticamente mediante Cloud App Security y las siguientes secciones sobre la creación de scripts de bloqueo son innecesarias. Para obtener más información, vea [integrar con Zscaler](zscaler-integration.md) e [integrar Cloud App Security con iboss](iboss-integration.md) , respectivamente.

## <a name="export-a-block-script-to-govern-discovered-apps"></a>Exportar un script de bloque para controlar aplicaciones detectadas

Cloud App Security permite bloquear el acceso a aplicaciones no autorizadas con el uso de sus aplicaciones locales de seguridad. Puede generar un script de bloqueo dedicado e importarlo al la aplicación. Esta solución no requiere redireccionar todo el tráfico web de la organización a un proxy.

1. En el panel de Cloud Discovery, etiquete las aplicaciones que quiere bloquear como **No autorizada**.

    ![Etiquetar como no autorizada](./media/tag-as-unsanctioned.png)

2. En la barra de título, haga clic en los tres puntos y seleccione **Generar script de bloque...** .

    ![Generar script de bloque](./media/generate-block-script.png)

3. En **Generar script de bloque**, seleccione la aplicación para la que quiere generar el script de bloque.

    ![Ventana emergente de Generar script de bloqueo](./media/generate-block-script-popup.png)

4. Después, haga clic en el botón Generar script para crear un script de bloqueo para todas las aplicaciones no autorizadas. De forma predeterminada, se asignará un nombre al archivo con la fecha en la que se haya exportado y el tipo de aplicación que haya seleccionado. *2017-02-19_CAS_Fortigate_block_script.txt* sería un nombre de archivo de ejemplo

   ![Botón Generar script de bloque](./media/generate-block-script-button.png)

5. Importe el archivo que ha creado en la aplicación.

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Actividades diarias para proteger el entorno de nube](daily-activities-to-protect-your-cloud-environment.md)

[Los clientes Premier también pueden crear una solicitud de soporte técnico directamente en el portal Premier.](https://premier.microsoft.com/)
