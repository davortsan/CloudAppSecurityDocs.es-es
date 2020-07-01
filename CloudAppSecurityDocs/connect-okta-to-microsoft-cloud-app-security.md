---
title: Conexión de Okta con Cloud App Security
description: En este artículo se proporciona información sobre cómo conectar Okta con Cloud App Security mediante el conector de API para la visibilidad y el control del uso.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 9/1/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: f69522921f3bd9996e8a0146cdf6ea224691e1f8
ms.sourcegitcommit: b15034dd50142afd8e95de22a9232f711b1eae6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2020
ms.locfileid: "85623270"
---
# <a name="connect-okta-to-microsoft-cloud-app-security"></a>Conectar Okta con Microsoft Cloud App Security

*Se aplica a: Microsoft Cloud App Security*

En este artículo se ofrecen instrucciones para conectar Microsoft Cloud App Security con una cuenta de Okta existente mediante las API del conector. Esta conexión le ofrece visibilidad y control del uso de Okta. Para obtener información sobre cómo Cloud App Security protege Okta, consulte [protección de Okta](protect-okta.md).

## <a name="how-to-connect-okta-to-cloud-app-security"></a>Cómo conectar Okta con Cloud App Security

1. Se recomienda crear una cuenta de servicio de administrador en Okta para Cloud App Security.

    Asegúrese de usar una cuenta con permisos de superadministrador.

    Asegúrese de que la cuenta de Okta esté verificada.

1. En la consola de Okta, haga clic en **Administración**.

    - Haga clic en **Seguridad** y luego en **API**.

         ![API de Okta](media/okta-api.png "API de Okta")

    - Haga clic en **Crear token**.

         ![Okta crear token](media/okta-createtoken.jpg "Okta crear token")

    - En el menú emergente **crear token** , asigne un nombre al token Cloud App Security y haga clic en **crear token**.

         ![Elemento emergente de token de Okta](media/okta-token-pop-up.png)

    - En el elemento emergente **Token created successfully** (Token creado correctamente), copie el **Token value** (Valor de token).

         ![Valor de token de Okta](media/okta-token-value.png "Valor de token de Okta")

1. En la consola de Cloud App Security, haga clic en **Investigar** y, después, en **Aplicaciones conectadas**.

1. En la página **Conectores de aplicaciones**, haga clic en el botón del signo más y, después, en **Okta**.

    ![conectar Okta](media/connect-okta.png "conectar Okta")

1. En el menú emergente, en el campo **dominio** , escriba el dominio de Okta y pegue el token en el campo **token** .

1. Haga clic en **Conectar** para crear el token de Okta en Cloud App Security.

1. Haga clic en **Probar API** para confirmar que la conexión se ha realizado correctamente.

    La prueba puede tardar unos minutos. Cuando reciba la notificación de que se ha realizado correctamente, haga clic en **Cerrar**.

Después de conectar Okta, recibirá eventos de 60 días anteriores a la conexión.

Si tiene problemas para conectar la aplicación, consulte [solución de problemas de conectores de aplicaciones](troubleshooting-api-connectors-using-error-messages.md).

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Controlar las aplicaciones en la nube con directivas](control-cloud-apps-with-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]
