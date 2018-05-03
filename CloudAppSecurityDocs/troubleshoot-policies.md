---
title: Solución de problemas de directivas de Cloud App Security | Microsoft Docs
description: En este tema se describe el proceso de solución de problemas de creación de directivas en Cloud App Security.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 4/22/2018
ms.topic: get-started-article
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 828cc94a-248b-44f6-a1ba-c28c0a135f8c
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 9bfc880cdaa0bf87abfd2b3b34cdf647a4aa1aaf
ms.sourcegitcommit: 45311f2cafef79483e40d971a4c61c7673834d96
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2018
---
*Se aplica a: Microsoft Cloud App Security*


# <a name="troubleshooting-microsoft-cloud-app-security-policies"></a>Solución de problemas de directivas de Microsoft Cloud App Security | Microsoft Docs

|Error|Descripción|Solución|
|----|----|----|
| **La directiva <policy name> se ha deshabilitado automáticamente debido a un error de configuración.**|Si obtiene este error en Microsoft Cloud App Security, deberá corregir la configuración de la directiva afectada. Al crear una directiva de Microsoft Cloud App Security, es frecuente usar otros objetos creados en Cloud App Security, como etiquetas y filtros de intervalos IP. Si la etiqueta o el intervalo IP que se usa en la directiva se elimina posteriormente, la directiva se deshabilitará automáticamente y obtendrá este error. |Para restaurar la directiva, deberá editarla, quitar los objetos eliminados de sus filtros y guardarla.|



## <a name="see-also"></a>Consulte también
[Controlar las aplicaciones en la nube con directivas](control-cloud-apps-with-policies.md)

[Los clientes Premier también pueden elegir Cloud App Security directamente desde el Portal Premier](https://premier.microsoft.com/)

