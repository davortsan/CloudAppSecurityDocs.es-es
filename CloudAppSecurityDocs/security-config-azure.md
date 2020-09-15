---
title: Obtención de recomendaciones de configuración de seguridad para Azure
description: En este artículo se proporciona información sobre cómo obtener recomendaciones de configuración de seguridad en Cloud App Security mediante la integración de con Azure Security Center.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 09/15/2020
ms.topic: how-to
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 31fb5ddc618ce1600e41a1437759b2558b3350c1
ms.sourcegitcommit: 7d05b81a839286d2afae4cdad2c2d59e7becc1f9
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/15/2020
ms.locfileid: "90524198"
---
# <a name="security-configuration-for-azure"></a>Configuración de seguridad para Azure

*Se aplica a: Microsoft Cloud App Security*

Microsoft Cloud App Security proporciona una evaluación de la configuración de seguridad del entorno de Azure. La evaluación, con tecnología de Azure Security Center, proporciona recomendaciones para los controles de seguridad y configuración que faltan.

## <a name="prerequisites"></a>Requisitos previos

Su organización debe tener Azure Security Center licencias para todas las suscripciones que desea que proporcionen evaluaciones de configuración de seguridad de Azure.

## <a name="how-to-enable-azure-security-recommendations"></a>Cómo habilitar las recomendaciones de seguridad de Azure

Para habilitar las recomendaciones de configuración de seguridad en Cloud App Security, active la suscripción de Azure Security Center navegando hasta el <a href="https://ms.portal.azure.com/#blade/Microsoft_Azure_Security/SecurityMenuBlade/0" target="_blank">portal</a>.

## <a name="how-to-view-azure-security-recommendations"></a>Visualización de las recomendaciones de seguridad de Azure

1. En Cloud App Security, vaya a **investigar**  >  **configuración de seguridad**y, a continuación, seleccione la pestaña **Azure** .

    > [!NOTE]
    > Es posible que los cambios tarden hasta 15 minutos en surtir efecto.

    ![menú de configuración de seguridad](media/security-configuration-menu.png)

1. Puede filtrar las recomendaciones por tipo, recurso y suscripción. Además, puede hacer clic en el icono de configuración de seguridad ![Icono de ASC](media/asc-icon.png) para abrir la recomendación en Azure Security Center, a fin de obtener más información y profundizar en la recomendación.

    > [!NOTE]
    > Para que la investigación sea incluso más sencilla, puede crear consultas personalizadas y guardarlas para usar más adelante. Una vez que haya terminado de compilar la consulta, haga clic en el botón **Guardar como** situado en la esquina superior derecha de los filtros.  En el elemento emergente **Guardar consulta** , asigne un nombre a la consulta.

    ![configuración de seguridad](media/security-configuration-azure.png)

Para información sobre cómo implementar las recomendaciones de seguridad, vea [Administración de recomendaciones de seguridad en Azure Security Center](/azure/security-center/security-center-recommendations).

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Controlar las aplicaciones en la nube con directivas](control-cloud-apps-with-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]