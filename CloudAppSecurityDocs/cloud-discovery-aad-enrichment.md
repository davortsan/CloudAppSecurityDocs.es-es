---
title: Enriquecimiento de los datos de Cloud App Security Discovery con nombres de usuario de Azure AD
description: En este artículo se proporciona información sobre cómo enriquecer los datos de Cloud App Security Discovery con nombres de usuario de Azure AD.
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
ms.assetid: 45295c2c-3e4d-4482-bf95-2e47072f9236
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: b3c595b1d45ee378eccace39ca4cf27f8a5f8867
ms.sourcegitcommit: c342abeec95359ddabdabcc3a081a0f91d52407c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72335426"
---
# <a name="cloud-discovery-enrichment"></a>Enriquecimiento de Cloud Discovery

*Se aplica a: Microsoft Cloud App Security*

Ahora es posible mejorar los datos de Cloud Discovery con datos de nombre de usuario de Azure Active Directory. Cuando se habilita esta característica, el nombre de usuario que se recibe en los registros de tráfico de detección se hace coincidir con el nombre de usuario de Azure AD y se reemplaza por este. Enriquecimiento de Cloud Discovery ofrece estas características:
- Puede investigar el uso de Shadow IT por parte del usuario de Azure Active Directory.
- Puede correlacionar el uso de las aplicaciones en la nube detectadas con las actividades de API recopiladas.
- Después, puede crear registros personalizados en función de los grupos de usuarios de Azure AD. Por ejemplo, un informe de Shadow IT para un departamento de marketing específico.


## <a name="prerequisites"></a>Requisitos previos:
- El origen de datos debe proporcionar información sobre el nombre de usuario.
- El conector de aplicaciones de Office 365 debe estar conectado.

## <a name="enabling-user-data-enrichment"></a>Habilitar el enriquecimiento de datos del usuario 
    
1. En el engranaje Configuración, seleccione **Configuración de Cloud Discovery**.
     
2. En la pestaña **Enriquecimiento de usuarios**, seleccione **Enriquezca los identificadores de los usuarios detectados con los nombres de usuario de Azure Active Directory**. Esta opción permite a Cloud App Security usar datos de Azure Active Directory para mejorar los nombres de usuarios de forma predeterminada.

3. Haga clic en **Guardar**.
 
![Enriquecer Cloud App Security Discovery con nombres de usuario de Azure AD](./media/discovery-enrichment.png)
  

  
      
## <a name="next-steps"></a>Pasos siguientes
  
[Controlar las aplicaciones en la nube con directivas](control-cloud-apps-with-policies.md)   

[Los clientes Premier también pueden crear una solicitud de soporte técnico directamente en el portal Premier.](https://premier.microsoft.com/)  
    
      
  
