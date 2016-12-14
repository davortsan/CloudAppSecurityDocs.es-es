---
title: Conectar Salesforce | Microsoft Docs
description: "En este tema se proporciona información sobre cómo conectar la aplicación Salesforce con Cloud App Security mediante el conector de API."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 10/26/2016
ms.topic: get-started-article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: 776d7589-acdb-4cb6-99a0-3be2f7b6aab2
ms.reviewer: reutam
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 6beb9041b338406fb5b16f4bd045dbdc4592c6d9
ms.openlocfilehash: af663e48d24a869b8a30b429accf8001a8584bb1


---


# <a name="connect-salesforce-to-microsoft-cloud-app-security"></a>Conectar Salesforce con Microsoft Cloud App Security
En esta sección se proporcionan instrucciones para conectar Cloud App Security con una cuenta de Salesforce existente mediante la API del conector de aplicaciones.  
  
## <a name="how-to-connect-salesforce-to-cloud-app-security"></a>Cómo conectar Salesforce con Cloud App Security  
  
1.  Se recomienda tener una cuenta de administrador de servicio dedicada para Cloud App Security.  
  
2.  Confirme que la API de REST está habilitada en Salesforce.  
  
     La cuenta de Salesforce debe ser una de las siguientes ediciones que incluyen compatibilidad con la API de REST:  
  
     **Performance**, **Enterprise**, **Unlimited** o **Developer**.  
  
     La edición **Professional** no tiene la API de REST de forma predeterminada, pero se puede agregar a petición.  
  
     Compruebe que la edición tiene disponible la API de REST y que está habilitada de la manera siguiente:  
  
    -   Inicie sesión en su cuenta de Salesforce y vaya a la página **Configuración**.  
  
    -   En **Administrar usuarios**, vaya a la página **Perfiles**.  
  
         ![perfiles de Administrar usuarios en Salesforce](./media/salesforce-manageusers-profiles.png "salesforce manageusers profiles")  
  
    -   Elija el perfil que usa para implementar Cloud App Security y haga clic en **Editar**. Este es el perfil que se usará para la cuenta de servicio de Cloud App Security con la que se configurará el conector de aplicaciones.  
  
         ![editar perfil en Salesforce](./media/salesforce-edit-profile.png "salesforce edit profile")  
  
    -   Asegúrese de que está activada la casilla **API Enabled** (API habilitada). Si no está seleccionada, es posible que deba ponerse en contacto con Salesforce para agregarla a su cuenta.  
  
         ![API habilitada en Salesforce](./media/salesforce-api-enabled.png "salesforce api enabled")  
  
3.  Si su organización tiene habilitada la opción **Salesforce CRM Content** (Contenido CRM de Salesforce), asegúrese de que la cuenta administrativa actual también la tenga habilitada.  
  
    1.  Vaya a la página de configuración de Salesforce.  
  
         ![configuración de Salesforce](./media/salesforce-setup.png "salesforce setup")  
  
    2.  En el menú lateral, seleccione **Administrar usuarios** y haga clic en **Usuarios**.  
  
         ![menú de usuarios de Salesforce](./media/salesforce-menu-users.png "salesforce menu users")  
  
    3.  Seleccione el usuario administrativo actual de su usuario de Cloud App Security dedicado.  
  
    4.  Asegúrese de que está seleccionada la casilla **Salesforce CRM Content User** (Usuario de contenido CRM de Salesforce).  
  
         Si no está seleccionada, haga clic en **Editar** y después active la casilla.  
  
         ![usuario de contenido CRM de Salesforce](./media/salesforce-crm-content-user.png "salesforce crm content user")  
  
    5.  Haga clic en **Guardar**.  
  
4.  En la consola de Cloud App Security, haga clic en **Investigar** y, después, en **Aplicaciones conectadas**.  
  
5.  En la página **Conectores de aplicaciones**, haga clic en el botón del signo más y, después, en **Salesforce**.  
  
     ![conectarse a Salesforce](./media/connect-salesforce.png "connect salesforce")  
  
6.  En la página de configuración de Salesforce, en la pestaña API, haga clic en **Seguir vínculo**, en función de la instancia que vaya a instalar.  
  
7.  Se abrirá la página de inicio de sesión de Salesforce. Escriba sus credenciales para permitir que Cloud App Security tenga acceso a la aplicación de Salesforce de su equipo.  
  
     ![inicio de sesión en Salesforce](./media/salesforce-logon.png "salesforce logon")  
  
8.  Salesforce le preguntará si quiere permitir que Cloud App Security acceda a la información y el registro de actividad de su equipo y que realice actividades como cualquier miembro del equipo. Para continuar, haga clic en **Permitir**.  
  
9. En este momento recibirá una notificación que le indicará si la implementación se ha llevado a cabo correcta o incorrectamente. Cloud App Security ya está autorizado en Salesforce.com.  
  
10. Si vuelve a la consola de Cloud App Security, debería aparecer un mensaje que le indica que Salesforce se ha conectado correctamente.  
  
11. Haga clic en **Probar API** para confirmar que la conexión se ha realizado correctamente.  
  
     La prueba puede tardar unos minutos. Cuando reciba la notificación de que se ha realizado correctamente, haga clic en **Listo**.  
  
  
Después de conectarse a Salesforce, recibirá eventos como se indica a continuación: desencadenadores en el momento de la conexión, eventos de inicio de sesión y traza de auditoría de configuración de los 60 días anteriores a la conexión, y supervisión de eventos de los 30 días anteriores o del día anterior, en función de su licencia de supervisión de eventos de Salesforce.
  
## <a name="see-also"></a>Consulte también  
[Controlar las aplicaciones en la nube con directivas](control-cloud-apps-with-policies.md)   
[Para obtener soporte técnico, visite la página de soporte técnico asistido de Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Los clientes Premier también pueden elegir Cloud App Security directamente desde el Portal Premier.](https://premier.microsoft.com/)  
  
  


<!--HONumber=Nov16_HO5-->


