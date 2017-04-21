---
title: Conectar ServiceNow con Cloud App Security para la visibilidad y el control del uso | Microsoft Docs
description: "En este tema se proporciona información sobre cómo conectar la aplicación ServiceNow con Cloud App Security mediante el conector de API."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 3/21/2017
ms.topic: get-started-article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: c626d94d-2ffd-4daf-8fa4-4b6d308cf012
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 1f4fd428f762bcbe1fb2a26bf44268cf985fbd4f
ms.sourcegitcommit: c79c405a1277c5fcebbc245fa12ff8feb53248d5
translationtype: HT
---
# <a name="connect-servicenow-to-microsoft-cloud-app-security"></a>Conectar ServiceNow con Microsoft Cloud App Security
En esta sección se proporcionan instrucciones para conectar Cloud App Security con una cuenta de ServiceNow existente mediante la API del conector de aplicaciones.  
  
## <a name="how-to-connect-servicenow-to-cloud-app-security"></a>Cómo conectar ServiceNow con Cloud App Security  
  
> [!NOTE]  
>  Cloud App Security admite las versiones de ServiceNow Eureka, Fiji, Geneva, Helsinki e Istanbul. Para conectar ServiceNow con Cloud App Security, debe tener el rol de **administrador** y asegurarse de que la instancia de ServiceNow admite el acceso a la API.  Para obtener más información, consulte la [documentación del producto de ServiceNow](http://wiki.servicenow.com/index.php?title=Base_System_Roles#gsc.tab=0).
  
1.  Inicie sesión con una cuenta de administrador en la cuenta de ServiceNow.  
  
2.  En la barra de búsqueda del **navegador de filtros**, escriba **OAuth** y seleccione **Registro de aplicación**.

3. En la barra de menús **Registros de aplicación**, haga clic en **Nuevo** para crear un perfil de OAuth.

   ![Nuevo perfil de OAuth de ServiceNow](./media/servicenow-app-registry.png)

4. En **¿Qué tipo de aplicación de OAuth?**, haga clic en **Crear un punto de conexión de la API de OAuth para clientes externos**.

   ![Tipo de OAuth de ServiceNow](./media/servicenow-oauth-app-type.png)

5. En **Nuevo registro de registros de aplicación**, proporcione la información siguiente:
    
    - En el campo **Nombre** escriba el nombre del nuevo perfil de OAuth, por ejemplo, CloudAppSecurity. 
    
    - El **identificador de cliente** se generará automáticamente. Copie este identificador, ya que deberá pegarlo en Cloud App Security para completar la conexión.
    
    - En el campo **Secreto de cliente**, escriba una cadena. Si lo deja vacío, se generará automáticamente un secreto aleatorio. Cópielo y guárdelo para más adelante. 
    
    - Aumente **Duración del token de acceso** como mínimo a 3600.
    
    - Haz clic en **Enviar**.

   ![Identificadores de perfil de ServiceNow](./media/servicenow-profile-ids.png)

6.  En el portal de Cloud App Security, haga clic en **Investigar** y, después, en **Aplicaciones conectadas**.  
  
7.  En la página **Conectores de aplicaciones**, haga clic en el botón del signo más y, después, en **ServiceNow**.  
  
     ![conectar ServiceNow](./media/connect-servicenow.png "conectar ServiceNow")  
  
8.  En el elemento emergente, agregue el nombre de usuario de ServiceNow, la contraseña, la dirección URL de la instancia, el identificador de cliente y el secreto de cliente en los cuadros correspondientes.  
  
9.  Haga clic en **Conectar**.  
  
     ![conectar ServiceNow con CAS](./media/servicenow-portal-connect.png "conectar ServiceNow en el portal")  
  
10.  Haga clic en **Probar ahora** para confirmar que la conexión se ha realizado correctamente.  
  
     La prueba puede tardar unos minutos. Cuando reciba la notificación de que se ha realizado correctamente, haga clic en **Cerrar**.  
  
Después de conectar ServiceNow, recibirá eventos de 60 días anteriores a la conexión.
  
## <a name="see-also"></a>Consulte también  
[Controlar las aplicaciones en la nube con directivas](control-cloud-apps-with-policies.md)   
[Para obtener soporte técnico, visite la página de soporte técnico asistido de Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Los clientes Premier también pueden elegir Cloud App Security directamente desde el Portal Premier.](https://premier.microsoft.com/)  
  
