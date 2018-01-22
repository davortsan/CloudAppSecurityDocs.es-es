---
title: Bloqueo de aplicaciones detectadas | Documentos de Microsoft
description: En este tema se describe el procedimiento para exportar scripts de bloqueo para aplicaciones detectadas.
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 1/15/2018
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: e451031e-4764-411a-b366-73a49d4f25df
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 702c91ea2c1c57dc8d095697498bc75066df05b4
ms.sourcegitcommit: 458e936e1ac548eda37e9bf955b439199bbdd018
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/16/2018
---
## <a name="govern-discovered-apps"></a>Controlar las aplicaciones detectadas

Después de revisar la lista de aplicaciones detectadas en el entorno, puede protegerlo contra el uso de aplicaciones no deseadas de las maneras que se indican a continuación.

### <a name="sanctioningunsanctioning-an-app"></a>Autorizar o no autorizar una aplicación 

Puede no autorizar una aplicación de riesgo específica. Para ello, haga clic en los tres puntos situados al final de la fila y seleccione **No autorizar**.
El hecho de no autorizar una aplicación no impide que se use, pero le permite supervisar más fácilmente su uso con los filtros de Cloud Discovery. Después, puede notificar a los usuarios que la aplicación no está autorizada y sugerir una aplicación segura alternativa.

![Etiquetar como no autorizada](./media/tag-as-unsanctioned.png)  


Si tiene una lista de aplicaciones que quiere autorizar o no autorizar, puede activar la casilla de todas las aplicaciones que quiere administrar y, después, seleccionar la acción.


## <a name="export-a-block-script-to-govern-discovered-apps"></a>Exportar un script de bloque para controlar aplicaciones detectadas

Cloud App Security permite bloquear el acceso a aplicaciones no autorizadas con el uso de sus aplicaciones locales de seguridad. Puede generar un script de bloqueo dedicado e importarlo en su aplicación.
Esta solución no requiere redireccionar todo el tráfico web de la organización a un proxy.

1. En el panel de Cloud Discovery, etiquete las aplicaciones que quiere bloquear como **No autorizada**.

   ![Etiquetar como no autorizada](./media/tag-as-unsanctioned.png)  

2. En la barra de título, haga clic en los tres puntos y seleccione **Generar script de bloque...**. 

   ![Generar script de bloque](./media/generate-block-script.png)  

3. En **Generar script de bloque**, seleccione la aplicación para la que quiere generar el script de bloque. 

   ![Ventana emergente de Generar script de bloque](./media/generate-block-script-popup.png)  

4. A continuación, haga clic en el botón Generar script. Esto creará un script de bloque para todas sus aplicaciones no autorizadas. De forma predeterminada, se asignará un nombre al archivo con la fecha en la que se haya exportado y el tipo de aplicación que haya seleccionado, por ejemplo *2017-02-19_CAS_Fortigate_block_script.txt* 

   ![Botón Generar script de bloque](./media/generate-block-script-button.png)  

5. Importe el archivo que ha creado en la aplicación.



## <a name="see-also"></a>Consulte también  
[Actividades diarias para proteger el entorno de nube](daily-activities-to-protect-your-cloud-environment.md)   

[Los clientes Premier también pueden elegir Cloud App Security directamente desde el Portal Premier.](https://premier.microsoft.com/)  
  
  