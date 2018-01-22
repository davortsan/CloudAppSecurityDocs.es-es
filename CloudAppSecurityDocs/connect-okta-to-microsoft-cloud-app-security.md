---
title: Conectar Okta con Cloud App Security para la visibilidad y el control del uso | Microsoft Docs
description: "En este tema se proporciona información sobre cómo conectar la aplicación Okta con Cloud App Security mediante el conector de API."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 1/15/2018
ms.topic: get-started-article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: 9c3673b9-99bd-400c-9da1-5bf809ea5892
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: a7aa0ffc06f46307154baf2d6998c6425719097a
ms.sourcegitcommit: 458e936e1ac548eda37e9bf955b439199bbdd018
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/16/2018
---
# <a name="connect-okta-to-microsoft-cloud-app-security"></a>Conectar Okta con Microsoft Cloud App Security
En esta sección se proporcionan instrucciones para conectar Cloud App Security con una cuenta de Okta existente mediante las API del conector.  
  
## <a name="how-to-connect-okta-to-cloud-app-security"></a>Cómo conectar Okta con Cloud App Security  
  
1.  Se recomienda crear una cuenta de servicio de administrador en Okta para Cloud App Security.  
  
     Asegúrese de usar una cuenta con permisos de superadministrador.  
  
     Asegúrese de que la cuenta de Okta esté verificada.  
  
2.  En la consola de Okta, haga clic en **Administración**.  
  
    -   Haga clic en **Seguridad** y luego en **API**.  
  
         ![API de Okta](./media/okta-api.png "API de Okta")  
  
    -   Haga clic en **Crear token**.  
  
         ![crear token de Okta](./media/okta-createtoken.jpg "crear token de Okta")  
  
    -   En el menú emergente **Crear token**, asigne un nombre al token de Cloud App Security y haga clic en **Crear token**.  
  
         ![menú emergente de token de Okta](./media/okta-token-popup.png "menú emergente de token de Okta")  
  
    -   En el elemento emergente **Token created successfully** (Token creado correctamente), copie el **Token value** (Valor de token).  
  
         ![valor de token de Okta](./media/okta-token-value.png "valor de token de Okta")  
  
3.  En la consola de Cloud App Security, haga clic en **Investigar** y, después, en **Aplicaciones conectadas**.  
  
4.  En la página **Conectores de aplicaciones**, haga clic en el botón del signo más y, después, en **Okta**.  
  
     ![conectar Okta](./media/connect-okta.png "conectar Okta")  
  
5.  En el elemento emergente que se muestra, en el campo **Dominio**, escriba el dominio de Okta y pegue el token en el campo **Token**.  
  
6.  Haga clic en **Conectar** para crear el token de Okta en Cloud App Security.  
  
7.  Haga clic en **Probar API** para confirmar que la conexión se ha realizado correctamente.  
  
     La prueba puede tardar unos minutos. Cuando reciba la notificación de que se ha realizado correctamente, haga clic en **Cerrar**.  
  
Después de conectar Okta, recibirá eventos de 60 días anteriores a la conexión.
  
## <a name="see-also"></a>Consulte también  
[Controlar las aplicaciones en la nube con directivas](control-cloud-apps-with-policies.md)   

[Los clientes Premier también pueden elegir Cloud App Security directamente desde el Portal Premier.](https://premier.microsoft.com/)  
  
  