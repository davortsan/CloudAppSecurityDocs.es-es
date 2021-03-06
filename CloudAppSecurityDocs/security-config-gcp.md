---
title: Obtener recomendaciones de configuración de seguridad para GCP
description: En este artículo se proporciona información sobre cómo obtener recomendaciones de configuración de seguridad en Cloud App Security mediante la integración de con Google Cloud Platform.
ms.date: 06/28/2020
ms.topic: how-to
ms.openlocfilehash: 15242c8a89aee5a9aa3edd1bf7a881f81734680a
ms.sourcegitcommit: d87372b47ca98e942c2bf94032a6a61902627d69
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/30/2020
ms.locfileid: "96315504"
---
# <a name="security-configuration-for-google-cloud-platform"></a>Configuración de seguridad para Google Cloud Platform

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Microsoft Cloud App Security proporciona una evaluación de la configuración de seguridad del entorno de Google Cloud Platform (GCP). Esta evaluación proporciona recomendaciones de seguridad fundamentales basadas en la [prueba comparativa de Center for Internet Security (CIS) para GCP](https://www.cisecurity.org/benchmark/google_cloud_computing_platform/), versión 1.1.0.

Esta evaluación proporciona una vista organizativa de las recomendaciones de configuración de seguridad de todos los proyectos de GCP y permite a los administradores de seguridad investigar los huecos de configuración de seguridad e iniciar la corrección de los propietarios de los recursos.

## <a name="prerequisites"></a>Requisitos previos

- Debe configurar el centro de comandos de seguridad de GCP con análisis de estado de seguridad para todos los proyectos de GCP de la organización. Para obtener más información, consulte [configuración del centro de comandos de seguridad de GCP](https://cloud.google.com/security-command-center/docs/quickstart-scc-setup) y [habilitación del análisis de estado de seguridad](https://cloud.google.com/security-command-center/docs/how-to-use-security-health-analytics).
- Los proyectos de GCP deben estar conectados a Cloud App Security. Para obtener más información, consulte [Connect GCP to Microsoft Cloud App Security](connect-google-gcp-to-microsoft-cloud-app-security.md).

## <a name="how-to-view-gcp-security-recommendations"></a>Cómo ver las recomendaciones de seguridad de GCP

1. En Cloud App Security, vaya a **investigar**  >  **configuración de seguridad** y, a continuación, seleccione la pestaña **Google Cloud Platform** .

    > [!NOTE]
    > Es posible que los cambios tarden hasta 15 minutos en surtir efecto.

    ![menú de configuración de seguridad](media/security-configuration-menu.png)

1. Puede filtrar las recomendaciones por tipo, recurso y suscripción. Además, puede hacer clic en el icono de configuración de seguridad ![Icono de ASC](media/asc-icon.png) para abrir la recomendación en centro de comandos de seguridad GCP para obtener más información y profundizar en la recomendación.

    > [!NOTE]
    > Para que la investigación sea incluso más sencilla, puede crear consultas personalizadas y guardarlas para usar más adelante. Una vez que haya terminado de compilar la consulta, haga clic en el botón **Guardar como** situado en la esquina superior derecha de los filtros. En el elemento emergente **Guardar consulta** , asigne un nombre a la consulta.

    ![configuración de seguridad](media/security-configuration-gcp.png)

1. Seleccione una recomendación para ver información adicional acerca de la recomendación, incluida una descripción y instrucciones de corrección detalladas.

    ![recomendación de configuración de seguridad](media/security-configuration-gcp-details.png)

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Controlar las aplicaciones en la nube con directivas](control-cloud-apps-with-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]
