---
title: "Preguntas más frecuentes sobre Cloud App Security | Microsoft Docs"
description: "Este artículo contiene las preguntas más frecuentes sobre Cloud App Security y sus respuestas."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 5/10/2017
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: 081c2cf4-2750-4546-9490-4b65e87ae48c
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 3e0c14d142f9154b5e986105899c9445667518c6
ms.sourcegitcommit: 50fac1cec86dfb8170ba9c63a8f58a4bf24e3c5b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/10/2017
---
# <a name="frequently-asked-questions"></a>Preguntas más frecuentes

## <a name="what-kind-of-permissions-do-i-need-to-have-in-order-to-access-cloud-app-security"></a>¿Qué tipo de permisos es necesario tener para poder obtener acceso a Cloud App Security?

Debe ser un administrador global, un administrador de cumplimiento o un administrador de seguridad de Azure Active Directory. No basta con tener estos roles en el Centro de seguridad y cumplimiento de Office 365.
Para establecer un usuario como administrador global, administrador de cumplimiento o administrador de seguridad de Azure Active Directory, ejecute lo siguiente en Windows PowerShell:

        $cred = Get-Credential
        Connect-MsolService -credential $cred
        Add-MsolRoleMember -RoleName "Compliance Administrator" -RoleMemberEmailAddress "XX@XX.XX"
 O bien, Add-MsolRoleMember -RoleName "Security Administrator" -RoleMemberEmailAddress "XX@XX.XX".

## <a name="see-also"></a>Vea también  
Para obtener información sobre cómo usar y configurar directivas para controlar el uso de la aplicación de la nube, consulte [Controlar las aplicaciones en la nube con directivas](control-cloud-apps-with-policies.md).   
Para obtener soporte técnico, visite la página de [soporte técnico asistido de Cloud App Security](http://support.microsoft.com/oas/default.aspx?prid=16031).   
Los clientes Premier también pueden elegir Cloud App Security directamente desde el [Portal Premier](https://premier.microsoft.com/).  
