---
title: 'Bloqueo de aplicaciones detectadas: Cloud App Security | Microsoft Docs'
description: En este artículo se describe el procedimiento para exportar scripts de bloqueo para aplicaciones detectadas.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: barbkess
ms.date: 12/10/2018
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: e451031e-4764-411a-b366-73a49d4f25df
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 902b919a801a6c3b077e930593ba74023efded9f
ms.sourcegitcommit: 8ef0438fa35916c48625ff750cb85e9628d202f2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/15/2019
ms.locfileid: "56281056"
---
# <a name="govern-discovered-apps"></a>Controlar las aplicaciones detectadas

*Se aplica a: Microsoft Cloud App Security*

Después de revisar la lista de aplicaciones detectadas en el entorno, puede protegerlo contra el uso de aplicaciones no deseadas de las maneras que se indican a continuación.


## <a name="BKMK_SanctionApp"></a> Autorizar o no autorizar una aplicación 

Puede no autorizar una aplicación de riesgo específica. Para ello, haga clic en los tres puntos situados al final de la fila. Después seleccione **No autorizar**. El hecho de no autorizar una aplicación no impide que se use, pero le permite supervisar más fácilmente su uso con los filtros de Cloud Discovery. Después, puede notificar a los usuarios de la aplicación que no está autorizada y sugerir una aplicación segura alternativa.

![Etiquetar como no autorizada](./media/tag-as-unsanctioned.png)  

Si tiene una lista de aplicaciones que quiere autorizar o no autorizar, active la casilla de todas las aplicaciones que quiere administrar y después seleccione la acción.

Para consultar una lista de las aplicaciones no autorizadas, puede [generar un script de bloque mediante las API de Cloud App Security](https://us.portal.cloudappsecurity.com/api-docs/#generate-block-script).

> [!NOTE]
> Si su inquilino usa Zscaler NSS, Cloud App Security bloquea cualquier aplicación que usted marque como no autorizada y las siguientes secciones relacionadas con la creación de scripts de bloqueo son innecesarias. Para obtener más información, consulte [Integrate Cloud App Security with Zscaler](zscaler-integration.md) (Integración de Cloud App Security con Zscaler).

## <a name="export-a-block-script-to-govern-discovered-apps"></a>Exportar un script de bloque para controlar aplicaciones detectadas

Cloud App Security permite bloquear el acceso a aplicaciones no autorizadas con el uso de sus aplicaciones locales de seguridad. Puede generar un script de bloqueo dedicado e importarlo al la aplicación. Esta solución no requiere redireccionar todo el tráfico web de la organización a un proxy.

1. En el panel de Cloud Discovery, etiquete las aplicaciones que quiere bloquear como **No autorizada**.

   ![Etiquetar como no autorizada](./media/tag-as-unsanctioned.png)  

2. En la barra de título, haga clic en los tres puntos y seleccione **Generar script de bloque...**. 

   ![Generar script de bloque](./media/generate-block-script.png)  

3. En **Generar script de bloque**, seleccione la aplicación para la que quiere generar el script de bloque. 

   ![Ventana emergente de Generar script de bloqueo](./media/generate-block-script-popup.png)  

4. Después, haga clic en el botón Generar script para crear un script de bloqueo para todas las aplicaciones no autorizadas. De forma predeterminada, se asignará un nombre al archivo con la fecha en la que se haya exportado y el tipo de aplicación que haya seleccionado. *2017-02-19_CAS_Fortigate_block_script.txt* sería un nombre de archivo de ejemplo 

   ![Botón Generar script de bloque](./media/generate-block-script-button.png)  

5. Importe el archivo que ha creado en la aplicación.



## <a name="next-steps"></a>Pasos siguientes  
[Actividades diarias para proteger el entorno de nube](daily-activities-to-protect-your-cloud-environment.md)   

[Los clientes Premier también pueden crear una solicitud de soporte técnico directamente en el portal Premier.](https://premier.microsoft.com/)  
  
  
