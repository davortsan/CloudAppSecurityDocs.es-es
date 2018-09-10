---
title: Solución de problemas de directivas de Cloud App Security | Microsoft Docs
description: En este tema se describe el proceso de solución de problemas de creación de directivas en Cloud App Security.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 5/22/2018
ms.topic: conceptual
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 828cc94a-248b-44f6-a1ba-c28c0a135f8c
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: ca7d2187ebd83c352cbbcf92efb7a30adf8debcf
ms.sourcegitcommit: 0ac08ca7b3140b79f1d36ff7152476c188fa12b3
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/07/2018
ms.locfileid: "44142585"
---
*Se aplica a: Microsoft Cloud App Security*


# <a name="troubleshooting-microsoft-cloud-app-security-policies"></a>Solución de problemas de directivas de Microsoft Cloud App Security | Microsoft Docs

|Error|Descripción|Solución|
|----|----|----|
| **La directiva <policy name> se ha deshabilitado automáticamente debido a un error de configuración**|Si obtiene este error en Microsoft Cloud App Security, deberá corregir la configuración de la directiva que se indica. Al crear una directiva de Microsoft Cloud App Security, es frecuente usar otros objetos creados en Cloud App Security o en el Centro de seguridad y cumplimiento, como etiquetas IP o tipos confidenciales personalizados. Si la etiqueta IP o el tipo confidencial personalizado que se usa en la directiva se elimina posteriormente, la directiva se deshabilitará automáticamente y obtendrá este error. Esto también podría indicar un error de configuración más general, como un filtro que es demasiado complejo. |Para restaurar la directiva, modifíquela y corrija cada error de configuración mencionado. Normalmente, esto significa que debe quitar los objetos eliminados de los filtros de directiva y guardar la directiva.|



## <a name="see-also"></a>Consulte también
[Controlar las aplicaciones en la nube con directivas](control-cloud-apps-with-policies.md)

[Los clientes Premier también pueden elegir Cloud App Security directamente desde el Portal Premier](https://premier.microsoft.com/)

