---
title: Bloqueo de aplicaciones detectadas | Documentos de Microsoft
description: En este tema se describe el procedimiento para exportar scripts de bloqueo para aplicaciones detectadas.
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 2/21/2017
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: e451031e-4764-411a-b366-73a49d4f25df
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: ca4a10f64429c481f49c75740f651302b1c7d1ef
ms.sourcegitcommit: 7493d88e4fe7c827f870b81e2090ffcc77f1408a
translationtype: HT
---
# <a name="governing-discovered-apps"></a>Control de aplicaciones detectadas
Cloud App Security permite bloquear el acceso a aplicaciones no autorizadas con el uso de sus aplicaciones locales de seguridad. Puede generar un script de bloqueo dedicado e importarlo en su aplicación.
Esta solución no requiere redireccionar todo el tráfico web de la organización a un proxy.


## <a name="export-a-block-script-to-govern-discovered-apps"></a>Exportar un script de bloque para controlar aplicaciones detectadas

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
[Para obtener soporte técnico, visite la página de soporte técnico asistido de Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Los clientes Premier también pueden elegir Cloud App Security directamente desde el Portal Premier.](https://premier.microsoft.com/)  
  
  