---
title: Solucionar errores de inspección de contenido
description: En este artículo se proporciona una lista de los estados de inspección de contenido, así como el significado de estos.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 05/25/2020
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 50c240d70492b9db22e584a1fdc2c438e982bb01
ms.sourcegitcommit: a0a8e25bda77fb21f280a0e504896be85b89ed6f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/25/2020
ms.locfileid: "96034099"
---
# <a name="troubleshooting-content-inspection"></a>Solución de problemas relacionados con la inspección de contenido

[!INCLUDE [Banner for top of topics](includes/banner.md)]

En este artículo se proporciona una lista de los estados de inspección de contenido, así como el significado de estos.

## <a name="content-inspection-status"></a>Estado de la inspección de contenido

En la tabla se enumera cada estado de inspección de contenido y su descripción.

|Estado de la inspección de contenido|Descripción|
|---|---|
|Completed|La inspección de contenido se completó correctamente.|
|No aplicable|La inspección de contenido no es aplicable para este archivo. Puede ser que este estado aparezca porque no hay ninguna directiva que requiera la inspección de contenido de este archivo o porque no se admite el tipo de archivo.|
|Pending|El archivo está actualmente en la cola de inspección de contenido.|
|Error: Error de descarga|Microsoft Cloud App Security no ha podido descargar el archivo para la inspección.|
|Error: Archivo cifrado|El archivo no se ha podido descifrar.|
|Error: El archivo está dañado|El archivo está dañado de algún modo y no se ha podido inspeccionar.|
|Error: Error interno.|Se produjo un problema indeterminado al intentar inspeccionar el archivo.|
|Error: Error de DLP externo|Se produjo un error en la DLP externa y Cloud App Security no pudo inspeccionar el contenido.|
|Error: Se ha excedido el tamaño de archivo|El archivo supera el tamaño máximo de archivo de 50 MB.|
|Error: el archivo es demasiado largo y se examinó parcialmente|El archivo superó el máximo de 1 millón caracteres. Para la parte del contenido que se examinó, se aplicaron las coincidencias de directiva relevantes.|
|Error: Acceso denegado al archivo|El archivo es externo a la nube y Cloud App Security no ha podido acceder a él.|
|Error: Archivo eliminado|El archivo ya no existe en la nube y no se ha podido inspeccionar.|
|Error: Tipo de archivo no admitido|Cloud App Security no puede inspeccionar el contenido de este tipo de archivo. Puede que este estado aparezca porque no se admite el tipo de archivo o porque el archivo no se encuentra realmente en el formato del tipo de archivo esperado.|

> [!NOTE]
> Si observa un guión en el estado del examen, significará que el archivo no está en la cola de examen. Consulte las [directivas de archivos](data-protection-policies.md) para obtener más información sobre cómo establecer directivas de inspección de contenido.

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Actividades diarias para proteger el entorno de nube](daily-activities-to-protect-your-cloud-environment.md)

[!INCLUDE [Open support ticket](includes/support.md)]
