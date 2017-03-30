---
title: "Preguntas más frecuentes sobre Cloud App Security | Microsoft Docs"
description: "Este artículo contiene las preguntas más frecuentes sobre Cloud App Security y sus respuestas."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 1/23/2017
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: 081c2cf4-2750-4546-9490-4b65e87ae48c
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 92ad2a378b0ab0f127ef22c9746f2957f43576a8
ms.sourcegitcommit: 355226ee21981563066d637e7db0bff0d53c2da6
translationtype: HT
---
# <a name="frequently-asked-questions"></a>Preguntas más frecuentes

## <a name="what-kind-of-permissions-do-i-need-to-have-in-order-to-access-cloud-app-security"></a>¿Qué tipo de permisos es necesario tener para poder obtener acceso a Cloud App Security?

Debe ser un administrador global, un administrador de cumplimiento o un administrador de seguridad de Azure Active Directory. No basta con tener estos roles en el Centro de seguridad y cumplimiento de Office 365.
Para establecer un usuario como administrador global, administrador de cumplimiento o administrador de seguridad de Azure Active Directory, ejecute lo siguiente en Windows PowerShell:

        $cred = Get-Credential
        Connect-MsolService -credential $cred
        Add-MsolRoleMember -RoleName "Compliance Administrator" -RoleMemberEmailAddress "XX@XX.XX"
 O bien, Add-MsolRoleMember -RoleName "Security Administrator" -RoleMemberEmailAddress “XX@XX.XX”.

## <a name="see-also"></a>Vea también  
Para obtener información sobre cómo usar y configurar directivas para controlar el uso de la aplicación de la nube, consulte [Controlar las aplicaciones en la nube con directivas](control-cloud-apps-with-policies.md).   
Para obtener soporte técnico, visite la página de [soporte técnico asistido de Cloud App Security](http://support.microsoft.com/oas/default.aspx?prid=16031).   
Los clientes Premier también pueden elegir Cloud App Security directamente desde el [Portal Premier](https://premier.microsoft.com/).  