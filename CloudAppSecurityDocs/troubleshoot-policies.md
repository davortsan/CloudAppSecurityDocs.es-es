---
title: Solución de problemas de directivas de Cloud App Security
description: En este artículo se describe el proceso que hay que seguir para solucionar problemas relacionados con la creación de directivas en Cloud App Security.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: rkarlin
ms.date: 12/10/2018
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 828cc94a-248b-44f6-a1ba-c28c0a135f8c
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: bad9ddf835c4abd1dba339e8d413bd06097a5366
ms.sourcegitcommit: 9f0c562322394a3dfac7f1d84286e673276a28b1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/14/2019
ms.locfileid: "65568830"
---
# <a name="troubleshooting-microsoft-cloud-app-security-policies"></a>Solución de problemas de directivas de Microsoft Cloud App Security | Microsoft Docs

*Se aplica a: Microsoft Cloud App Security*

En este artículo se describe el proceso que hay que seguir para solucionar problemas relacionados con la creación de directivas en Cloud App Security.

## <a name="troubleshooting"></a>Solución de problemas

En el gráfico siguiente se incluyen la descripción y la solución de los errores que se le podrían mostrar para las directivas.

|Error|Descripción|Solución|
|----|----|----|
| **La directiva <*name*> se ha deshabilitado automáticamente debido a un error de configuración**|Si se le muestra este error en Microsoft Cloud App Security, significa que debe corregir la configuración de la directiva indicada. Al crear una directiva de Microsoft Cloud App Security, es frecuente usar otros objetos creados en Cloud App Security o en el Centro de seguridad y cumplimiento, como etiquetas IP o tipos confidenciales personalizados. Si la etiqueta IP o el tipo confidencial personalizado que se usa en la directiva se eliminan, la directiva se deshabilitará automáticamente y se le mostrará este error. Este mensaje también podría indicar un error de configuración más general, como un filtro que es demasiado complejo. |Para restaurar la directiva, modifíquela y corrija cada error de configuración mencionado. Normalmente, este error significa que debe quitar los objetos eliminados de los filtros de la directiva y guardarla.|

## <a name="next-steps"></a>Pasos siguientes

[Controlar las aplicaciones en la nube con directivas](control-cloud-apps-with-policies.md)

[Los clientes Premier también pueden elegir Cloud App Security directamente desde el Portal Premier](https://premier.microsoft.com/).

