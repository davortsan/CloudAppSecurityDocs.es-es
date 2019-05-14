---
title: 'Preguntas más frecuentes: Cloud App Security | Microsoft Docs'
description: Este artículo contiene las preguntas más frecuentes sobre Cloud App Security y sus respuestas.
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
ms.assetid: 081c2cf4-2750-4546-9490-4b65e87ae48c
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: a172853944dc5ee468a0e17fffedb9bf15523a77
ms.sourcegitcommit: 9f0c562322394a3dfac7f1d84286e673276a28b1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/14/2019
ms.locfileid: "65565851"
---
# <a name="frequently-asked-questions"></a>Preguntas más frecuentes

*Se aplica a: Microsoft Cloud App Security*

Este artículo contiene las preguntas más frecuentes sobre Cloud App Security y sus respuestas.

## <a name="what-kind-of-permissions-do-i-need-to-access-cloud-app-security"></a>¿Qué tipo de permisos necesito para poder acceder a Cloud App Security?

Debe ser un administrador global, un administrador de cumplimiento o un administrador de seguridad de Azure Active Directory. No basta con tener estos roles en el Centro de seguridad y cumplimiento de Office 365. Puede usar PowerShell para establecer un usuario como un administrador global, un administrador de cumplimiento o un administrador de seguridad de Azure Active Directory. Ejecute los siguientes cmdlets:

```powershell

 $cred = Get-Credential
 Connect-MsolService -credential $cred
 Add-MsolRoleMember -RoleName "Compliance Administrator" -RoleMemberEmailAddress "XX@XX.XX"
```

 O

```powershell
 Add-MsolRoleMember -RoleName "Security Administrator" -RoleMemberEmailAddress “XX@XX.XX”
```

## <a name="next-steps"></a>Pasos siguientes  
Para obtener información sobre cómo usar y configurar directivas para controlar el uso de la aplicación de la nube, vea [Controlar las aplicaciones en la nube con directivas](control-cloud-apps-with-policies.md).   

Los clientes Premier también pueden elegir Cloud App Security directamente desde el [Portal Premier](https://premier.microsoft.com/).  
