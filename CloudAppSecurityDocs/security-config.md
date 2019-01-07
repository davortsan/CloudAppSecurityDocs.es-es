---
title: 'Obtención de recomendaciones de configuración de seguridad: Cloud App Security | Microsoft Docs'
description: En este artículo se proporciona información sobre cómo obtener recomendaciones de configuración de seguridad en Cloud App Security mediante la integración con Azure Security Center.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 12/10/2018
ms.topic: conceptual
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: c6d8f8af-867b-43ab-adee-f06520577fe7
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 0cd5567c1f89375109a97be00c1053fe0da64833
ms.sourcegitcommit: b86c3afd1093fbc825fec5ba4103e3a95f65758e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/10/2018
ms.locfileid: "53175744"
---
# <a name="security-configuration"></a>Configuración de seguridad

*Se aplica a: Microsoft Cloud App Security*

Microsoft Cloud App Security proporciona una evaluación de la configuración de seguridad del entorno de Azure. La evaluación, con tecnología de Azure Security Center, proporciona recomendaciones para la configuración y el control de seguridad que faltan.

## <a name="enable-security-configuration-recommendations"></a>Habilitar las recomendaciones de configuración de seguridad

Para usar esta característica, debe tener los permisos adecuados en Azure AD y en Azure Portal. De forma predeterminada, el rol de administrador global de Azure AD no proporciona acceso a suscripciones de Azure. Eleve los permisos para conceder acceso a las suscripciones de Azure a otros usuarios y para usted.

> [!IMPORTANT]
> Se recomienda que deshabilite la elevación después de completar el proceso siguiente.

Para habilitar las recomendaciones de configuración de seguridad en Microsoft Cloud App Security:

1. <a href="https://docs.microsoft.com/azure/security-center/security-center-management-groups" target="_blank">Obtenga visibilidad de todos los inquilinos en Azure Security Center</a>. Este proceso incluye:
   - Concederse el rol lector para todas las suscripciones y también a los otros administradores de Microsoft Cloud App Security a los que quiere conceder acceso a esta página.
   - Asignar el rol en el grupo de administración raíz en Azure Security Center
   - Elevar el administrador Global de Azure AD para conceder acceso a las suscripciones de Azure.
   - En el artículo se describe el proceso para convertirse en un administrador de seguridad. Para que esta integración funcione, los permisos mínimos que necesita son de **lector**.

2. Asegúrese de abrir <a href="https://ms.portal.azure.com/#blade/Microsoft_Azure_Security/SecurityMenuBlade/0" target="_blank">Azure Security Center</a> para que los cambios surtan efecto.

3. En el portal de Microsoft Cloud App Security, vaya a **Investigar** y a **Configuración de seguridad**. 
    - Microsoft Cloud App Security proporciona recomendaciones únicamente para las 50 suscripciones principales. 
    - Es posible que los cambios tarden hasta 15 minutos en surtir efecto.

     ![menú de configuración de seguridad](./media/security-configuration-menu.png)

4. Puede filtrar las recomendaciones por tipo, recurso y suscripción. Además, puede hacer clic en el icono de configuración de seguridad ![Icono de ASC](./media/asc-icon.png) para abrir la recomendación en Azure Security Center, a fin de obtener más información y profundizar en la recomendación. 

Para información sobre cómo implementar las recomendaciones de seguridad, vea [Administración de recomendaciones de seguridad en Azure Security Center](https://docs.microsoft.com/azure/security-center/security-center-recommendations).

   ![configuración de seguridad](./media/security-configuration1.png)

## <a name="next-steps"></a>Pasos siguientes 
[Controlar las aplicaciones en la nube con directivas](control-cloud-apps-with-policies.md)

[Los clientes Premier también pueden crear una solicitud de soporte técnico directamente en el portal Premier.](https://premier.microsoft.com/)  
  
