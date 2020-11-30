---
title: Solución de problemas de directivas de Cloud App Security
description: En este artículo se describe el proceso que hay que seguir para solucionar problemas relacionados con la creación de directivas en Cloud App Security.
ms.date: 12/10/2018
ms.topic: conceptual
ms.openlocfilehash: 80d7501dcc97c3697f0d4a98286ba72637cd051d
ms.sourcegitcommit: d87372b47ca98e942c2bf94032a6a61902627d69
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/30/2020
ms.locfileid: "96315980"
---
# <a name="troubleshooting-microsoft-cloud-app-security-policies"></a>Solución de problemas de directivas de Microsoft Cloud App Security | Microsoft Docs

[!INCLUDE [Banner for top of topics](includes/banner.md)]

En este artículo se describe el proceso que hay que seguir para solucionar problemas relacionados con la creación de directivas en Cloud App Security.

## <a name="troubleshooting"></a>Solución de problemas

En el gráfico siguiente se incluyen la descripción y la solución de los errores que se le podrían mostrar para las directivas.

|Error|Descripción|Solución|
|----|----|----|
| **La directiva <*name*> se ha deshabilitado automáticamente debido a un error de configuración**|Si se le muestra este error en Microsoft Cloud App Security, significa que debe corregir la configuración de la directiva indicada. Al crear una directiva de Microsoft Cloud App Security, es frecuente usar otros objetos creados en Cloud App Security o en el Centro de seguridad y cumplimiento, como etiquetas IP o tipos confidenciales personalizados. Si la etiqueta IP o el tipo confidencial personalizado que se usa en la directiva se eliminan, la directiva se deshabilitará automáticamente y se le mostrará este error. Este mensaje también podría indicar un error de configuración más general, como un filtro que es demasiado complejo. |Para restaurar la directiva, modifíquela y corrija cada error de configuración mencionado. Normalmente, este error significa que debe quitar los objetos eliminados de los filtros de la directiva y guardarla.|

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Controlar las aplicaciones en la nube con directivas](control-cloud-apps-with-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]
