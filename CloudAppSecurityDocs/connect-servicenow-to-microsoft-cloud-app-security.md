---
title: Conectar ServiceNow con Microsoft Cloud App Security | Microsoft Docs
description: "En este tema se proporciona información sobre cómo conectar la aplicación ServiceNow con Cloud App Security mediante el conector de API."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 10/15/2016
ms.topic: get-started-article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: c626d94d-2ffd-4daf-8fa4-4b6d308cf012
ms.reviewer: reutam
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: ed4ea71b24767d3602d40894d1cbac7447bcd8a2
ms.openlocfilehash: 30ddba23a0c481cb434e9239950cce90c52efc4f


---

# <a name="connect-servicenow-to-microsoft-cloud-app-security"></a>Conectar ServiceNow con Microsoft Cloud App Security
En esta sección se proporcionan instrucciones para conectar Cloud App Security con una cuenta de ServiceNow existente mediante la API del conector de aplicaciones.  
  
## <a name="how-to-connect-servicenow-to-cloud-app-security"></a>Cómo conectar ServiceNow con Cloud App Security  
  
> [!NOTE]  
>  Cloud App Security admite las versiones de ServiceNow Eureka y Fiji. Para conectar ServiceNow con Cloud App Security, debe tener permisos de administrador y asegurarse de que la instancia de ServiceNow admite el acceso a la API.  
  
1.  Inicie sesión con una cuenta de administrador en la cuenta de ServiceNow.  
  
2.  Cree una nueva cuenta de servicio para Cloud App Security y asocie el rol de administrador a la cuenta recién creada.  
  
3.  Asegúrese de que el complemento de la API de REST está activado.  
  
     ![cuenta de ServiceNow](./media/servicenow-account.png "servicenow account")  
  
4.  En el portal de Cloud App Security, haga clic en **Investigar** y, después, en **Aplicaciones autorizadas**.  
  
5.  En la fila de ServiceNow, haga clic en **Conectar** en la columna **Estado del conector de aplicaciones** o haga clic en el botón **Conectar una aplicación** y luego en **ServiceNow**.  
  
     ![conectar ServiceNow](./media/connect-servicenow.png "connect servicenow")  
  
6.  En la página de configuración de ServiceNow, en la pestaña API, agregue el nombre de usuario, la contraseña y la dirección URL de la instancia de ServiceNow en los cuadros correspondientes.  
  
7.  Haga clic en **Conectar**.  
  
     ![actualizar contraseña de ServiceNow](./media/servicenow-update-password.png "servicenow update password")  
  
8.  Haga clic en **Probar API** para confirmar que la conexión se ha realizado correctamente.  
  
     La prueba puede tardar unos minutos. Cuando reciba la notificación de que se ha realizado correctamente, haga clic en **Cerrar**.  
  
Después de conectar ServiceNow, recibirá eventos de 60 días anteriores a la conexión.
  
## <a name="see-also"></a>Consulte también  
[Controlar las aplicaciones en la nube con directivas](control-cloud-apps-with-policies.md)   
[Para obtener soporte técnico, visite la página de soporte técnico asistido de Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Los clientes Premier también pueden elegir Cloud App Security directamente desde el Portal Premier.](https://premier.microsoft.com/)  
  
  


<!--HONumber=Oct16_HO4-->


