---
title: 'Preguntas más frecuentes: Cloud App Security'
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
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 072a4205c62158f73922d4648d5d10890d73b82c
ms.sourcegitcommit: b15034dd50142afd8e95de22a9232f711b1eae6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2020
ms.locfileid: "85624482"
---
# <a name="frequently-asked-questions"></a>Preguntas más frecuentes

*Se aplica a: Microsoft Cloud App Security*

Este artículo contiene las preguntas más frecuentes sobre Cloud App Security y sus respuestas.

## <a name="what-kind-of-permissions-do-i-need-to-access-cloud-app-security"></a>¿Qué tipo de permisos necesito para poder acceder a Cloud App Security?

Debe ser un administrador global, un administrador de cumplimiento o un administrador de seguridad de Azure Active Directory. No basta con tener estos roles en el Centro de seguridad y cumplimiento de Office 365. Puede usar PowerShell para establecer un usuario como un administrador global, un administrador de cumplimiento o un administrador de seguridad de Azure Active Directory. Ejecute los siguientes cmdlets:

```powershell

 $cred = Get-Credential
 Connect-MsolService -credential $cred
 Add-MsolRoleMember -RoleName "Compliance Administrator" -RoleMemberEmailAddress "XX@XX.XX"
```

 O BIEN

```powershell
 Add-MsolRoleMember -RoleName "Security Administrator" -RoleMemberEmailAddress “XX@XX.XX”
```

## <a name="next-steps"></a>Pasos siguientes

Para obtener información sobre cómo usar y configurar directivas para controlar el uso de la aplicación de la nube, vea [Controlar las aplicaciones en la nube con directivas](control-cloud-apps-with-policies.md).

[!INCLUDE [Open support ticket](includes/support.md)]
