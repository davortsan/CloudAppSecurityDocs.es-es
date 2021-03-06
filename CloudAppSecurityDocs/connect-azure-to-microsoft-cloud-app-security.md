---
title: Conexión de Azure con Cloud App Security
description: En este artículo se proporciona información sobre cómo conectar Azure con Cloud App Security mediante el conector de API para la visibilidad y el control del uso.
ms.date: 12/27/2020
ms.topic: how-to
ms.openlocfilehash: eb95630ac08763fa6b87a6fab410ec3629010ec8
ms.sourcegitcommit: 40d17309b8729eb914ea91ba5fa7017340231488
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/29/2020
ms.locfileid: "97808919"
---
# <a name="connect-azure-to-microsoft-cloud-app-security"></a>Conectar Azure con Microsoft Cloud App Security

[!INCLUDE [Banner for top of topics](includes/banner.md)]

En este artículo se ofrecen instrucciones para conectar Microsoft Cloud App Security con una cuenta de Azure existente mediante la API del conector de aplicaciones. Esta conexión le ofrece visibilidad y control del uso de Azure. Para obtener información sobre cómo Cloud App Security protege Azure, consulte [protección de Azure](protect-azure.md).

## <a name="how-to-connect-azure-to-cloud-app-security"></a>Cómo conectar Azure con Cloud App Security

> [!NOTE]
>
> - El usuario debe ser un administrador global o de seguridad en Azure AD para conectar Azure a Microsoft Cloud App Security.
> - Cloud App Security muestra las actividades de **todas** las suscripciones.
> - La información de la cuenta de usuario se rellena en Cloud App Security a medida que los usuarios realizan actividades en Azure.
> - Actualmente, Cloud App Security solo supervisa las actividades ARM.

1. En la página **aplicaciones conectadas** , haga clic en el botón de signo más y seleccione **Microsoft Azure**.

    ![elemento de menú conectar de Azure](media/connect-azure-menu.png)

2. En el menú emergente de Azure, haga clic en **Conectar con Microsoft Azure**.

    ![Conectar Azure](media/connect-azure.png)

> [!NOTE]
> Se extraerán los datos una vez que conecte Azure. Verá los datos correspondientes a partir de ese momento.

Si tiene problemas para conectar la aplicación, consulte [solución de problemas de conectores de aplicaciones](troubleshooting-api-connectors-using-error-messages.md).

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Controlar las aplicaciones en la nube con directivas](control-cloud-apps-with-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]
