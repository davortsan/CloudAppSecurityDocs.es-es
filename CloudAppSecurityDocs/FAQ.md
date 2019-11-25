---
title: 'Preguntas más frecuentes: Cloud App Security | Microsoft Docs'
description: Este artículo contiene las preguntas más frecuentes sobre Cloud App Security y sus respuestas.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
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
ms.openlocfilehash: 6e2464988eb075e3dd3bd345716b5ec71dec8ba6
ms.sourcegitcommit: 094bb42a198fe733cfd3aec79d74487672846dfa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/24/2019
ms.locfileid: "74460840"
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

 o

```powershell
 Add-MsolRoleMember -RoleName "Security Administrator" -RoleMemberEmailAddress “XX@XX.XX”
```

## <a name="next-steps"></a>Pasos siguientes  
Para obtener información sobre cómo usar y configurar directivas para controlar el uso de la aplicación de la nube, vea [Controlar las aplicaciones en la nube con directivas](control-cloud-apps-with-policies.md).   

[!INCLUDE [Open support ticket](includes/support.md)]  
