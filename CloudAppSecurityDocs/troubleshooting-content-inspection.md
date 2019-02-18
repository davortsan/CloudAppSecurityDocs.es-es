---
title: 'Solución de errores de inspección de contenido: Cloud App Security | Microsoft Docs'
description: En este artículo se proporciona una lista de los estados de inspección de contenido, así como el significado de estos.
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
ms.assetid: 359eb77f-e719-4c50-9b62-6ef64149a5a5
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: b3e3866b8cef8ae5b711145ffa104de88aed419e
ms.sourcegitcommit: 8ef0438fa35916c48625ff750cb85e9628d202f2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/15/2019
ms.locfileid: "56281379"
---
# <a name="troubleshooting-content-inspection"></a>Solucionar problemas relacionados con la inspección de contenido

*Se aplica a: Microsoft Cloud App Security*

En este artículo se proporciona una lista de los estados de inspección de contenido, así como el significado de estos.

## <a name="content-inspection-status"></a>Estado de la inspección de contenido

En la tabla se enumera cada estado de inspección de contenido y su descripción.

|Estado de la inspección de contenido|Descripción|
|----|----|
|Completed|La inspección de contenido se completó correctamente.|
|No disponible|La inspección de contenido no es aplicable para este archivo. Puede ser que este estado aparezca porque no hay ninguna directiva que requiera la inspección de contenido de este archivo o porque no se admite el tipo de archivo.|
|Pending|El archivo está actualmente en la cola de inspección de contenido.|
|Error: Error de descarga|Microsoft Cloud App Security no ha podido descargar el archivo para la inspección.|
|Error: Archivo cifrado|El archivo no se ha podido descifrar.|
|Error: Archivo dañado|El archivo está dañado de algún modo y no se ha podido inspeccionar.|
|Error: Error interno.|Se produjo un problema indeterminado al intentar inspeccionar el archivo.|
|Error: Error de DLP externo|Se produjo un error en la DLP externa y Cloud App Security no pudo inspeccionar el contenido.|
|Error: Se ha excedido el tamaño de archivo|El límite de archivo varía según el tamaño del archivo y el número de caracteres.|
|Error: Acceso denegado al archivo|El archivo es externo a la nube y Cloud App Security no ha podido acceder a él.|
|Error: Archivo eliminado|El archivo ya no existe en la nube y no se ha podido inspeccionar.|
|Error: Tipo de archivo no admitido|Cloud App Security no puede inspeccionar el contenido de este tipo de archivo. Puede que este estado aparezca porque no se admite el tipo de archivo o porque el archivo no se encuentra realmente en el formato del tipo de archivo esperado.|

> [!NOTE]
> Si observa un guión en el estado del examen, significará que el archivo no está en la cola de examen. Consulte las [directivas de archivos](data-protection-policies.md) para obtener más información sobre cómo establecer directivas de inspección de contenido.

## <a name="see-also"></a>Consulte también  
[Actividades diarias para proteger el entorno de nube](daily-activities-to-protect-your-cloud-environment.md)   

[Los clientes Premier también pueden crear una solicitud de soporte técnico directamente en el portal Premier.](https://premier.microsoft.com/)  

## <a name="next-steps"></a>Pasos siguientes
 
[Actividades diarias para proteger el entorno de nube](daily-activities-to-protect-your-cloud-environment.md)

