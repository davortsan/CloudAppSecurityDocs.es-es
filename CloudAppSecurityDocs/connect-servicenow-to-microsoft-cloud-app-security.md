---
title: Conectar ServiceNow con Cloud App Security para la visibilidad y el control del uso | Microsoft Docs
description: "En este tema se proporciona información sobre cómo conectar la aplicación ServiceNow con Cloud App Security mediante el conector de API."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 5/16/2017
ms.topic: get-started-article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: c626d94d-2ffd-4daf-8fa4-4b6d308cf012
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: a70e561150ef8d00a3815eb4332868f4c1fbeece
ms.sourcegitcommit: 2f4474084c7e07ac4853945ab5aa1ea78950675d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/28/2017
---
# <a name="connect-servicenow-to-microsoft-cloud-app-security"></a>Conectar ServiceNow con Microsoft Cloud App Security

En esta sección se proporcionan instrucciones para conectar Cloud App Security con una cuenta de ServiceNow existente mediante la API del conector de aplicaciones. 

 >  [!NOTE]
>  Se recomienda implementar ServiceNow mediante tokens de aplicación OAuth, que están disponibles para Fuji y versiones posteriores. Consulte la [documentación de ServiceNow](http://wiki.servicenow.com/index.php?title=OAuth_Applications#gsc.tab=0) correspondiente. En el caso de versiones anteriores, está disponible un [modo de conexiones heredadas](#legacy-servicenow-connection) según el usuario y la contraseña.

 > [!NOTE]  
>  Cloud App Security admite las versiones de ServiceNow Eureka, Fiji, Geneva, Helsinki e Istanbul. Para conectar ServiceNow con Cloud App Security, debe tener el rol de **administrador** y asegurarse de que la instancia de ServiceNow admite el acceso a la API.  Para obtener más información, consulte la [documentación del producto de ServiceNow](http://wiki.servicenow.com/index.php?title=Base_System_Roles#gsc.tab=0).
  
## <a name="how-to-connect-servicenow-to-cloud-app-security-using-oauth"></a>Cómo conectar ServiceNow con Cloud App Security mediante OAuth
  
  
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
  
8.  En el elemento emergente, agregue el id. de usuario de ServiceNow, la contraseña, la dirección URL de la instancia, el identificador de cliente y el secreto de cliente en los cuadros correspondientes. Para encontrar el identificador de usuario de ServiceNow, en el portal de ServiceNow, vaya a **Usuarios** y, luego, busque su nombre en la tabla (aparecerá junto a su identificador de usuario).

    ![Identificador de usuario de ServiceNow](./media/servicenow-userid.png)
  
9.  Haga clic en **Conectar**.  
  
     ![conectar ServiceNow con CAS](./media/servicenow-portal-connect.png "conectar ServiceNow en el portal")  
  
10.  Haga clic en **Probar ahora** para confirmar que la conexión se ha realizado correctamente.  
  
     La prueba puede tardar unos minutos. Cuando reciba la notificación de que se ha realizado correctamente, haga clic en **Cerrar**.  
  
Después de conectar ServiceNow, recibirá eventos de 60 días anteriores a la conexión.
  
## <a name="legacy-servicenow-connection"></a>Conexión de ServiceNow heredada

Para conectar ServiceNow con Cloud App Security, debe tener permisos de administrador y asegurarse de que la instancia de ServiceNow admite el acceso a la API.   

1.  Inicie sesión con una cuenta de administrador en la cuenta de ServiceNow.   

2.  Cree una nueva cuenta de servicio para Cloud App Security y asocie el rol de administrador a la cuenta recién creada.   

3.  Asegúrese de que el complemento de la API de REST está activado.   

    ![cuenta de servicenow](./media/servicenow-account.png "cuenta de servicenow")   

4.  En el portal de Cloud App Security, haga clic en **Investigar** y, después, en **Aplicaciones autorizadas**.   

5.  En la fila de ServiceNow, haga clic en **Conectar** en la columna **Estado del conector de aplicaciones** o haga clic en el botón **Conectar una aplicación** y luego en **ServiceNow**.   

    ![conectar ServiceNow](./media/connect-servicenow.png "conectar ServiceNow")   

6.  En la página de configuración de ServiceNow, en la pestaña API, agregue el id. de usuario, la contraseña y la dirección URL de la instancia de ServiceNow en los cuadros correspondientes.   

7.  Haga clic en **Conectar**.   

   ![actualizar la contraseña de servicenow](./media/servicenow-update-password.png "actualizar la contraseña de servicenow")   

8.  Haga clic en **Probar API** para confirmar que la conexión se ha realizado correctamente.   
  
   La prueba puede tardar unos minutos. Cuando reciba la notificación de que se ha realizado correctamente, haga clic en **Cerrar**.   
 Después de conectar ServiceNow, recibirá eventos de 60 días anteriores a la conexión. 


## <a name="see-also"></a>Consulte también  
[Controlar las aplicaciones en la nube con directivas](control-cloud-apps-with-policies.md)   
[Para obtener soporte técnico, visite la página de soporte técnico asistido de Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Los clientes Premier también pueden elegir Cloud App Security directamente desde el Portal Premier.](https://premier.microsoft.com/)  
  
