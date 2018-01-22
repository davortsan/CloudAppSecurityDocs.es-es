---
title: "Solución de problemas de directivas de Cloud App Security | Microsoft Docs"
description: "En este tema se describe el proceso de solución de problemas de creación de directivas en Cloud App Security."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 1/15/2018
ms.topic: get-started-article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: 828cc94a-248b-44f6-a1ba-c28c0a135f8c
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: ccd15579fd18616dccd663947d6513c21e1e1527
ms.sourcegitcommit: 458e936e1ac548eda37e9bf955b439199bbdd018
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/16/2018
---
# <a name="troubleshooting-cloud-app-security-policies"></a>Solución de problemas de directivas de Cloud App Security

|Error|Descripción|Solución|
|----|----|----|
| **La directiva <policy name> se ha deshabilitado automáticamente debido a un error de configuración.**|Si obtiene este error en Cloud App Security, deberá corregir la configuración de la directiva afectada. Al crear una directiva de Cloud App Security, es frecuente usar otros objetos creados en Cloud App Security, como etiquetas y filtros de intervalos IP. Si la etiqueta o el intervalo IP que se usa en la directiva se elimina posteriormente, la directiva se deshabilitará automáticamente y obtendrá este error. |Para restaurar la directiva, deberá editarla, quitar los objetos eliminados de sus filtros y guardarla.|



## <a name="see-also"></a>Consulte también
[Controlar las aplicaciones en la nube con directivas](control-cloud-apps-with-policies.md)

[Los clientes Premier también pueden elegir Cloud App Security directamente desde el Portal Premier](https://premier.microsoft.com/)

