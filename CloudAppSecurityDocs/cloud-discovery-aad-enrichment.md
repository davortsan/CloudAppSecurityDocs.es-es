---
title: Enriquecer los datos de Cloud App Security Discovery con nombres de usuario de Azure AD | Microsoft Docs
description: "En este artículo se proporciona información sobre cómo enriquecer los datos de Cloud App Security Discovery con nombres de usuario de Azure AD."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 6/19/2017
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: 45295c2c-3e4d-4482-bf95-2e47072f9236
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 909fa75c48fb9c698d083f2fb85f5f53bfadf76c
ms.sourcegitcommit: 2f4474084c7e07ac4853945ab5aa1ea78950675d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/28/2017
---
# <a name="cloud-discovery-enrichment"></a>Enriquecimiento de Cloud Discovery

Ahora es posible mejorar los datos de Cloud Discovery con datos de nombre de usuario de Azure Active Directory. Cuando se habilita esta característica, el nombre de usuario que se recibe en los registros de tráfico de detección se hace coincidir con el nombre de usuario de Azure AD y se reemplaza por este, con lo que se habilitan las siguientes características nuevas:
-   Puede investigar el uso de Shadow IT por parte del usuario de Azure Active Directory.
-   Puede correlacionar el uso de las aplicaciones en la nube detectadas con las actividades de API recopiladas.
-   Después, puede crear registros personalizados en función de los grupos de usuarios de Azure AD. Por ejemplo, un informe de Shadow IT para un departamento de marketing específico.


## <a name="prerequisites"></a>Requisitos previos:
- El origen de datos debe proporcionar información sobre el nombre de usuario.
- El conector de aplicaciones de Office 365 debe estar conectado.

## <a name="enabling-user-data-enrichment"></a>Habilitar el enriquecimiento de datos del usuario 
    
1. En el engranaje Configuración, seleccione **Configuración de Cloud Discovery**.
     
2. Para permitir que Cloud App Security use datos de Azure Active Directory para enriquecer los nombres de usuario de forma predeterminada, en la pestaña **Enriquecimiento de usuarios**, seleccione **Enriquezca los identificadores de los usuarios detectados con los nombres de usuario de Azure Active Directory.**.

3. Haga clic en **Guardar**.
 
![Enriquecer Cloud App Security Discovery con nombres de usuario de Azure AD](./media/discovery-enrichment.png)
  

  
      
## <a name="see-also"></a>Consulte también  
[Controlar las aplicaciones en la nube con directivas](control-cloud-apps-with-policies.md)   
[Para obtener soporte técnico, visite la página de soporte técnico asistido de Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Los clientes Premier también pueden elegir Cloud App Security directamente desde el Portal Premier.](https://premier.microsoft.com/)  
    
      
  