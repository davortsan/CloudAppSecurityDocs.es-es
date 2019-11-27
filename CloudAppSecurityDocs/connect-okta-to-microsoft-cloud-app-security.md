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
ms.openlocfilehash: c51cbcb3d8f08fb7b1fc1fc4668905ae11eaeed0
ms.sourcegitcommit: 094bb42a198fe733cfd3aec79d74487672846dfa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/24/2019
ms.locfileid: "74461093"
---
# <a name="connect-okta-to-microsoft-cloud-app-security"></a>Conectar Okta con Microsoft Cloud App Security

*Se aplica a: Microsoft Cloud App Security*

En este artículo se ofrecen instrucciones para conectar Microsoft Cloud App Security con una cuenta de Okta existente mediante las API del conector. Esta conexión le ofrece visibilidad y control del uso de Okta.

## <a name="how-to-connect-okta-to-cloud-app-security"></a>Cómo conectar Okta con Cloud App Security

1. Se recomienda crear una cuenta de servicio de administrador en Okta para Cloud App Security.

    Asegúrese de usar una cuenta con permisos de superadministrador.

    Asegúrese de que la cuenta de Okta esté verificada.

1. En la consola de Okta, haga clic en **Administración**.

    - Haga clic en **Seguridad** y luego en **API**.

         ![API de Okta](./media/okta-api.png "API de Okta")

    - Haga clic en **Crear token**.

         ![Okta crear token](./media/okta-createtoken.jpg "Okta crear token")

    - En el menú emergente **Crear token**, asigne un nombre al token de Cloud App Security y haga clic en **Crear token**.

         ![Emergente de token de Okta](./media/okta-token-popup.png "Emergente de token de Okta")

    - En el elemento emergente **Token created successfully** (Token creado correctamente), copie el **Token value** (Valor de token).

         ![Valor de token de Okta](./media/okta-token-value.png "Valor de token de Okta")

1. En la consola de Cloud App Security, haga clic en **Investigar** y, después, en **Aplicaciones conectadas**.

1. En la página **Conectores de aplicaciones**, haga clic en el botón del signo más y, después, en **Okta**.

    ![conectar Okta](./media/connect-okta.png "conectar Okta")

1. En el elemento emergente que se muestra, en el campo **Dominio**, escriba el dominio de Okta y pegue el token en el campo **Token**.

1. Haga clic en **Conectar** para crear el token de Okta en Cloud App Security.

1. Haga clic en **Probar API** para asegurarse de que la conexión se ha realizado correctamente.

    La prueba puede tardar unos minutos. Cuando reciba la notificación de que se ha realizado correctamente, haga clic en **Cerrar**.

Después de conectar Okta, recibirá eventos de 60 días anteriores a la conexión.

## <a name="next-steps"></a>Pasos siguientes

[Controlar las aplicaciones en la nube con directivas](control-cloud-apps-with-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]
