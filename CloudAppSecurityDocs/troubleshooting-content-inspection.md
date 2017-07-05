---
title: "Solución de errores de inspección de contenido en Cloud App Security | Microsoft Docs"
description: "En este tema se proporciona una lista de los estados de inspección de contenido, así como el significado de estos."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 5/10/2017
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: 359eb77f-e719-4c50-9b62-6ef64149a5a5
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 40f759d58fe26776c0738271c0112d00bb52bf5a
ms.sourcegitcommit: 2f4474084c7e07ac4853945ab5aa1ea78950675d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/28/2017
---
# <a name="troubleshooting-content-inspection"></a>Solucionar problemas relacionados con la inspección de contenido
|Estado de la inspección de contenido|Descripción|
|----|----|
|Completed|La inspección de contenido se completó correctamente.|
|No disponible|La inspección de contenido no es aplicable para este archivo. Esto podría pasar porque no hay ninguna directiva que requiera la inspección de contenido de este archivo o porque no se admite el tipo de archivo.|
|Pending|El archivo está actualmente en la cola de inspección de contenido.|
|Error: Error de descarga|Cloud App Security no pudo descargar el archivo para la inspección.|
|Error: Archivo cifrado|El archivo no se pudo descifrar.|
|Error: El archivo está dañado|El archivo está dañado de algún modo y no se pudo inspeccionar.|
|Error: Error interno.|Se produjo un problema indeterminado al intentar inspeccionar el archivo.|
|Error: Error de DLP externo|Se produjo un error en la DLP externa y Cloud App Security no pudo inspeccionar el contenido.|
|Error: Se ha excedido el tamaño de archivo|El límite de archivo varía según el tamaño del archivo y el número de caracteres.|
|Error: Acceso denegado al archivo|El archivo es externo a la nube y Cloud App Security no pudo acceder a él.|
|Error: Archivo eliminado|El archivo ya no existe en la nube y no se pudo inspeccionar.|
|Error: Tipo de archivo no admitido|Cloud App Security no puede inspeccionar el contenido de este tipo de archivo. Esto puede deberse a que no se admite el tipo de archivo o a que el archivo no se encuentra realmente en el formato del tipo de archivo esperado.|

> [!NOTE]
> Si observa un guión en el estado del examen, significará que el archivo no está en la cola de examen. Consulte las [directivas de archivos](data-protection-policies.md) para obtener más información sobre cómo establecer directivas de inspección de contenido.

## <a name="see-also"></a>Consulte también  
[Actividades diarias para proteger el entorno de nube](daily-activities-to-protect-your-cloud-environment.md)   
[Para obtener soporte técnico, visite la página de soporte técnico asistido de Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Los clientes Premier también pueden elegir Cloud App Security directamente desde el Portal Premier.](https://premier.microsoft.com/)  
  
  