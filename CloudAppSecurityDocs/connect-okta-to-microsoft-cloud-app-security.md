---
title: Conexión de Okta con Cloud App Security
description: En este artículo se proporciona información sobre cómo conectar Okta con Cloud App Security mediante el conector de API para la visibilidad y el control del uso.
keywords: ''
author: ShlomoSagir-MS
ms.author: ShlomoSagir-MS
manager: ShlomoSagir-MS
ms.date: 06/04/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 9c3673b9-99bd-400c-9da1-5bf809ea5892
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: ff6e44681deeb0d2666c0614b1b554e5911f2fa3
ms.sourcegitcommit: 0303627fb0ceb460c50071d0b20e33aa94ccff8d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/04/2019
ms.locfileid: "66491564"
---
# <a name="connect-okta-to-microsoft-cloud-app-security"></a>Conectar Okta con Microsoft Cloud App Security

*Se aplica a: Microsoft Cloud App Security*

En este artículo se ofrecen instrucciones para conectar Microsoft Cloud App Security con una cuenta de Okta existente mediante las API del conector. Esta conexión le ofrece visibilidad y control del uso de Okta.

>[!NOTE]
>El conector de Cloud App Security solo admite implementaciones de Okta que se establecieron antes del 7 de enero de 2019.
  
## <a name="how-to-connect-okta-to-cloud-app-security"></a>Cómo conectar Okta con Cloud App Security  
  
1.  Se recomienda crear una cuenta de servicio de administrador en Okta para Cloud App Security.  
  
     Asegúrese de usar una cuenta con permisos de superadministrador.  
  
     Asegúrese de que la cuenta de Okta esté verificada.  
  
2.  En la consola de Okta, haga clic en **Administración**.  
  
    -   Haga clic en **Seguridad** y luego en **API**.  
  
         ![API de Okta](./media/okta-api.png "API de Okta")  
  
    -   Haga clic en **Crear token**.  
  
         ![Crear token de Okta](./media/okta-createtoken.jpg "Crear token de Okta")  
  
    -   En el menú emergente **Crear token**, asigne un nombre al token de Cloud App Security y haga clic en **Crear token**.  
  
         ![Menú emergente de token de Okta](./media/okta-token-popup.png "Menú emergente de token de Okta")  
  
    -   En el elemento emergente **Token created successfully** (Token creado correctamente), copie el **Token value** (Valor de token).  
  
         ![Valor de token de Okta](./media/okta-token-value.png "Valor de token de Okta")  
  
3.  En la consola de Cloud App Security, haga clic en **Investigar** y, después, en **Aplicaciones conectadas**.  
  
4.  En la página **Conectores de aplicaciones**, haga clic en el botón del signo más y, después, en **Okta**.  
  
     ![Conectar Okta](./media/connect-okta.png "Conectar Okta")  
  
5.  En el elemento emergente que se muestra, en el campo **Dominio**, escriba el dominio de Okta y pegue el token en el campo **Token**.  
  
6.  Haga clic en **Conectar** para crear el token de Okta en Cloud App Security.  
  
7.  Haga clic en **Probar API** para confirmar que la conexión se ha realizado correctamente.  
  
     La prueba puede tardar unos minutos. Cuando reciba la notificación de que se ha realizado correctamente, haga clic en **Cerrar**.  
  
Después de conectar Okta, recibirá eventos de 60 días anteriores a la conexión.
  
## <a name="next-steps"></a>Pasos siguientes  
[Controlar las aplicaciones en la nube con directivas](control-cloud-apps-with-policies.md)   

[Los clientes Premier también pueden crear una solicitud de soporte técnico directamente en el portal Premier.](https://premier.microsoft.com/)  
  
