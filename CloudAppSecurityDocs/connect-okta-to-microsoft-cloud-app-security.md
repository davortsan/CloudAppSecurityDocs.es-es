---
title: Conectar Okta con Microsoft Cloud App Security | Microsoft Docs
description: "En este tema se proporciona información sobre cómo conectar la aplicación Okta con Cloud App Security mediante el conector de API."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 10/26/2016
ms.topic: get-started-article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: 9c3673b9-99bd-400c-9da1-5bf809ea5892
ms.reviewer: reutam
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: e41c04d25f12aa5207ef9ffbb6a22f4b894e92cb
ms.openlocfilehash: f5f355a42321e4467ce3ef487c48508522a286ab


---

# <a name="connect-okta-to-microsoft-cloud-app-security"></a>Conectar Okta con Microsoft Cloud App Security
En esta sección se proporcionan instrucciones para conectar Cloud App Security con una cuenta de Okta existente mediante las API del conector.  
  
## <a name="how-to-connect-okta-to-cloud-app-security"></a>Cómo conectar Okta con Cloud App Security  
  
1.  Se recomienda crear una cuenta de servicio de administrador en Okta para Cloud App Security.  
  
     Asegúrese de usar una cuenta con permisos de superadministrador.  
  
     Asegúrese de que la cuenta de Okta esté verificada.  
  
2.  En la consola de Okta, haga clic en **Administración**.  
  
    -   Haga clic en **Seguridad** y luego en **API**.  
  
         ![API de Okta](./media/okta-api.png "okta api")  
  
    -   Haga clic en **Crear token**.  
  
         ![crear token de Okta](./media/okta-createtoken.jpg "okta createtoken")  
  
    -   En el menú emergente **Crear token**, asigne un nombre al token de Cloud App Security y haga clic en **Crear token**.  
  
         ![menú emergente de token de Okta](./media/okta-token-popup.png "okta token popup")  
  
    -   En el elemento emergente **Token se ha creado correctamente**, copie el **Valor de token**.  
  
         ![valor de token de Okta](./media/okta-token-value.png "okta token value")  
  
3.  En la consola de Cloud App Security, haga clic en **Investigar** y, después, en **Aplicaciones conectadas**.  
  
4.  En la página **Conectores de aplicaciones**, haga clic en el botón **Conectar una aplicación** y, después, en **Okta**.  
  
     ![conectar Okta](./media/connect-okta.png "connect okta")  
  
5.  En el elemento emergente que se muestra, en el campo **Dominio**, escriba el dominio de Okta y pegue el token en el campo **Token**.  
  
6.  Haga clic en **Conectar** para crear el token de Okta en Cloud App Security.  
  
7.  Haga clic en **Probar API** para confirmar que la conexión se ha realizado correctamente.  
  
     La prueba puede tardar unos minutos. Cuando reciba la notificación de que se ha realizado correctamente, haga clic en **Cerrar**.  
  
Después de conectar Okta, recibirá eventos de 60 días anteriores a la conexión.
  
## <a name="see-also"></a>Consulte también  
[Controlar las aplicaciones en la nube con directivas](control-cloud-apps-with-policies.md)   
[Para obtener soporte técnico, visite la página de soporte técnico asistido de Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Los clientes Premier también pueden elegir Cloud App Security directamente desde el Portal Premier.](https://premier.microsoft.com/)  
  
  


<!--HONumber=Nov16_HO4-->


