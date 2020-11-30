---
title: Obtención de recomendaciones de configuración de seguridad para AWS
description: En este artículo se proporciona información sobre cómo obtener recomendaciones de configuración de seguridad en Cloud App Security mediante la integración de con Amazon Web Services.
ms.date: 06/28/2020
ms.topic: how-to
ms.openlocfilehash: 3d35ffdaeaf858407fd324464383faa2a343f301
ms.sourcegitcommit: d87372b47ca98e942c2bf94032a6a61902627d69
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/30/2020
ms.locfileid: "96315538"
---
# <a name="security-configuration-for-aws"></a>Configuración de seguridad para AWS

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Microsoft Cloud App Security proporciona una evaluación de la configuración de seguridad de su entorno de Amazon Web Services. Esta evaluación proporciona recomendaciones de seguridad fundamentales basadas en la prueba comparativa de Center for Internet Security (CIS) para AWS.

## <a name="prerequisites"></a>Requisitos previos

- La central de seguridad de AWS debe estar configurada para todas las regiones de la cuenta de AWS. Para obtener más información, consulte [configuración del centro de seguridad de AWS](https://go.microsoft.com/fwlink/?linkid=2100208).
    > [!NOTE]
    > Si es la primera vez que habilita el centro de seguridad, puede tardar varias horas para que los datos iniciales estén disponibles.
- El Amazon Web Services debe estar conectado a Cloud App Security. Para obtener más información, consulte [Connect AWS to Microsoft Cloud App Security](connect-aws-to-microsoft-cloud-app-security.md).

## <a name="how-to-view-aws-security-recommendations"></a>Cómo ver las recomendaciones de seguridad de AWS

1. En Cloud App Security, vaya a **investigar**  >  **configuración de seguridad** y, a continuación, seleccione la pestaña **Amazon Web Services** .

    > [!NOTE]
    > Es posible que los cambios tarden hasta 15 minutos en surtir efecto.

    ![menú de configuración de seguridad](media/security-configuration-menu.png)

1. Puede filtrar las recomendaciones por tipo, por recurso y por cuentas. Además, puede hacer clic en el icono de configuración de seguridad ![Icono de ASC](media/asc-icon.png) para abrir la recomendación en Amazon Security hub para obtener más información y profundizar en la recomendación.

    > [!NOTE]
    > Para que la investigación sea incluso más sencilla, puede crear consultas personalizadas y guardarlas para usar más adelante. Una vez que haya terminado de compilar la consulta, haga clic en el botón **Guardar como** situado en la esquina superior derecha de los filtros. En el elemento emergente **Guardar consulta** , asigne un nombre a la consulta.

    ![configuración de seguridad](media/security-configuration-aws.png)

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Controlar las aplicaciones en la nube con directivas](control-cloud-apps-with-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]
