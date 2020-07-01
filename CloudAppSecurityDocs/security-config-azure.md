---
title: Obtención de recomendaciones de configuración de seguridad para Azure
description: En este artículo se proporciona información sobre cómo obtener recomendaciones de configuración de seguridad en Cloud App Security mediante la integración de con Azure Security Center.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 06/29/2020
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: dec6b720804716df8ac275b6f6f641832e4cec17
ms.sourcegitcommit: b15034dd50142afd8e95de22a9232f711b1eae6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2020
ms.locfileid: "85716502"
---
# <a name="security-configuration-for-azure"></a>Configuración de seguridad para Azure

*Se aplica a: Microsoft Cloud App Security*

Microsoft Cloud App Security proporciona una evaluación de la configuración de seguridad del entorno de Azure. La evaluación, con tecnología de Azure Security Center, proporciona recomendaciones para la configuración y el control de seguridad que faltan.

## <a name="enable-security-configuration-recommendations"></a>Habilitar las recomendaciones de configuración de seguridad

Para usar esta característica, debe tener los permisos adecuados en Azure AD y en Azure Portal. De forma predeterminada, el rol de administrador global de Azure AD no proporciona acceso a suscripciones de Azure. Eleve los permisos para conceder acceso a las suscripciones de Azure a otros usuarios y para usted.

> [!IMPORTANT]
> Se recomienda que deshabilite la elevación después de completar el proceso siguiente.

## <a name="how-to-enable-azure-security-recommendations"></a>Cómo habilitar las recomendaciones de seguridad de Azure

Para habilitar las recomendaciones de configuración de seguridad en Microsoft Cloud App Security:

1. <a href="https://docs.microsoft.com/azure/security-center/security-center-management-groups" target="_blank">Obtener visibilidad en todo el inquilino para Azure Security Center</a>. Este proceso incluye:

    - Concederse el rol lector para todas las suscripciones y también a los otros administradores de Microsoft Cloud App Security a los que quiere conceder acceso a esta página.
    - Asignar el rol en el grupo de administración raíz en Azure Security Center
    - Elevar el administrador Global de Azure AD para conceder acceso a las suscripciones de Azure.
    - En el artículo se describe el proceso para convertirse en un administrador de seguridad. Para que esta integración funcione, los permisos mínimos que necesita son **lector**.

1. Asegúrese de abrir <a href="https://ms.portal.azure.com/#blade/Microsoft_Azure_Security/SecurityMenuBlade/0" target="_blank">Azure Security Center</a> para que los cambios surtan efecto.

## <a name="how-to-view-azure-security-recommendations"></a>Visualización de las recomendaciones de seguridad de Azure

1. En Cloud App Security, vaya a **investigar**  >  **configuración de seguridad**y, a continuación, seleccione la pestaña **Azure** .

    > [!NOTE]
    > Es posible que los cambios tarden hasta 15 minutos en surtir efecto.

    ![menú de configuración de seguridad](media/security-configuration-menu.png)

1. Puede filtrar las recomendaciones por tipo, recurso y suscripción. Además, puede hacer clic en el icono de configuración de seguridad ![Icono de ASC](media/asc-icon.png) para abrir la recomendación en Azure Security Center, a fin de obtener más información y profundizar en la recomendación.

Para información sobre cómo implementar las recomendaciones de seguridad, vea [Administración de recomendaciones de seguridad en Azure Security Center](https://docs.microsoft.com/azure/security-center/security-center-recommendations).

![configuración de seguridad](media/security-configuration-azure.png)

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Controlar las aplicaciones en la nube con directivas](control-cloud-apps-with-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]
