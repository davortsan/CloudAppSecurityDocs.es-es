---
title: Obtención de recomendaciones de configuración de seguridad en Cloud App Security | Microsoft Docs
description: En este artículo se proporciona información sobre cómo obtener recomendaciones de configuración de seguridad en Cloud App Security mediante la integración con Azure Security Center.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 6/27/2018
ms.topic: article
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: c6d8f8af-867b-43ab-adee-f06520577fe7
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 0d21df4cac9ca31207b94061d5bb18ec857668ac
ms.sourcegitcommit: c7e4351345d55cfeb0517651446490ce5f208651
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2018
ms.locfileid: "37140778"
---
*Se aplica a: Microsoft Cloud App Security*


# <a name="security-configuration"></a>Configuración de seguridad

Microsoft Cloud App Security proporciona una evaluación de la configuración de seguridad del entorno de Azure, así como recomendaciones para el control de la seguridad y los valores de configuración que falten, con tecnología de Azure Security Center. 

Para poder usar esta característica, debe tener los permisos adecuados en Azure AD y en Azure Portal.
 
De forma predeterminada, el rol de administrador global de Azure AD no proporciona acceso a suscripciones de Azure. Por este motivo, deberá elevar sus permisos para poder concederse a sí mismo y a otros usuarios acceso a suscripciones de Azure. 

> [!NOTE]
> Se recomienda que deshabilite la elevación después de completar el proceso siguiente.

Para habilitar las recomendaciones de configuración de seguridad en Microsoft Cloud App Security:

1. <a href="https://docs.microsoft.com/azure/security-center/security-center-management-groups" target="_blank">Obtenga visibilidad de todos los inquilinos en Azure Security Center</a>. Para ello, concédase a usted mismo, así como a los demás administradores de Microsoft Cloud App Security a los que quiere dar acceso a esta página, el rol de lector para todas las suscripciones, asigne el rol en el grupo de administración raíz en Azure Security Center y eleve el administrador global de Azure AD para conceder acceso a suscripciones de Azure. 

   > [!NOTE]
   > En el artículo se describe el proceso para convertirse en un administrador de seguridad. Para que esta integración funcione, los permisos mínimos que necesita son de lector.

2. Asegúrese de abrir <a href="https://ms.portal.azure.com/#blade/Microsoft_Azure_Security/SecurityMenuBlade/0" target="_blank">Azure Security Center</a> para que los cambios surtan efecto.

3. En el portal de Microsoft Cloud App Security, vaya a **Investigar** y a **Configuración de seguridad**. 

   ![menú de configuración de seguridad](./media/security-configuration-menu.png)

   > [!NOTE]
   > Microsoft Cloud App Security proporciona recomendaciones únicamente para las 50 suscripciones principales.
   > Es posible que los cambios tarden hasta 15 minutos en surtir efecto.

5. Puede filtrar las recomendaciones por tipo, recurso y suscripción. Además, puede hacer clic en el icono de configuración de seguridad ![icono de ASC](./media/asc-icon.png) para abrir la recomendación en Azure Security Center, a fin de obtener más información y profundizar en la recomendación. <br></br><br></br>Para información sobre cómo implementar las recomendaciones de seguridad, vea [Administración de recomendaciones de seguridad en Azure Security Center](https://docs.microsoft.com/azure/security-center/security-center-recommendations).

 
   ![configuración de seguridad](./media/security-configuration1.png)

 

## <a name="see-also"></a>Consulte también  
[Controlar las aplicaciones en la nube con directivas](control-cloud-apps-with-policies.md)   

[Los clientes Premier también pueden elegir Cloud App Security directamente desde el Portal Premier.](https://premier.microsoft.com/)  
  
