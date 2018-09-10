---
title: Preguntas más frecuentes sobre Cloud App Security | Microsoft Docs
description: Este artículo contiene las preguntas más frecuentes sobre Cloud App Security y sus respuestas.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 4/22/2018
ms.topic: conceptual
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 081c2cf4-2750-4546-9490-4b65e87ae48c
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: b53a360b743e80c85dcced8dd2bef7eae8c60f36
ms.sourcegitcommit: 0ac08ca7b3140b79f1d36ff7152476c188fa12b3
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/07/2018
ms.locfileid: "44144013"
---
*Se aplica a: Microsoft Cloud App Security*


# <a name="frequently-asked-questions"></a>Preguntas más frecuentes

## <a name="what-kind-of-permissions-do-i-need-to-have-in-order-to-access-cloud-app-security"></a>¿Qué tipo de permisos es necesario tener para poder obtener acceso a Cloud App Security?

Debe ser un administrador global, un administrador de cumplimiento o un administrador de seguridad de Azure Active Directory. No basta con tener estos roles en el Centro de seguridad y cumplimiento de Office 365.
Para establecer un usuario como administrador global, administrador de cumplimiento o administrador de seguridad de Azure Active Directory, ejecute lo siguiente en Windows PowerShell:

        $cred = Get-Credential
        Connect-MsolService -credential $cred
        Add-MsolRoleMember -RoleName "Compliance Administrator" -RoleMemberEmailAddress "XX@XX.XX"
 O bien, Add-MsolRoleMember -RoleName "Security Administrator" -RoleMemberEmailAddress "XX@XX.XX".

## <a name="see-also"></a>Consulta también  
Para obtener información sobre cómo usar y configurar directivas para controlar el uso de la aplicación de la nube, consulte [Controlar las aplicaciones en la nube con directivas](control-cloud-apps-with-policies.md).   

Los clientes Premier también pueden elegir Cloud App Security directamente desde el [Portal Premier](https://premier.microsoft.com/).  
