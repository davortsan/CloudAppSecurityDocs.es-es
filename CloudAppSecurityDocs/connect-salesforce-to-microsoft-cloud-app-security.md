---
title: Conectar Salesforce con Cloud App Security para la visibilidad y el control del uso | Microsoft Docs
description: En este artículo se proporciona información sobre cómo conectar la aplicación Salesforce con Cloud App Security mediante el conector de API.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 11/13/2018
ms.topic: conceptual
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 776d7589-acdb-4cb6-99a0-3be2f7b6aab2
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: acac9a56ec2ecd55206c7e3cd6ccb743c3c1a65b
ms.sourcegitcommit: 77850c6777504c2478611cb71a387e7fcc5f2551
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/13/2018
ms.locfileid: "51597041"
---
# <a name="connect-salesforce-to-microsoft-cloud-app-security"></a>Conectar Salesforce con Microsoft Cloud App Security

*Se aplica a: Microsoft Cloud App Security*

En este artículo se ofrecen instrucciones para conectar Microsoft Cloud App Security con una cuenta de Salesforce existente mediante la API del conector de aplicaciones.  
  
## <a name="how-to-connect-salesforce-to-cloud-app-security"></a>Cómo conectar Salesforce con Cloud App Security  
  
1.  Se recomienda tener una cuenta de administrador de servicio dedicada para Cloud App Security.  
  
2.  Confirme que la API de REST está habilitada en Salesforce.  
  
     La cuenta de Salesforce debe ser una de las siguientes ediciones que incluyen compatibilidad con la API de REST:  
  
     **Performance**, **Enterprise**, **Unlimited** o **Developer**.  
  
     La edición **Professional** no tiene la API REST de forma predeterminada, pero se puede agregar a petición.  
  
     Compruebe que la edición tiene disponible la API de REST y que está habilitada de la manera siguiente:  
  
    -   Inicie sesión en su cuenta de Salesforce y vaya a la página **Configuración**.  
  
    -   En **Administrar usuarios**, vaya a la página **Perfiles de usuario**.  
  
         ![Salesforce administra perfiles de usuarios](./media/salesforce-manageusers-profiles.png "Salesforce administra perfiles de usuarios")  
  
    -   Haga clic en **Nuevo** para crear un perfil nuevo. 
    - Elija el perfil que acaba de crear para implementar Cloud App Security y haga clic en **Editar**.  Este es el perfil que se usará para la cuenta de servicio de Cloud App Security con la que se configurará el conector de aplicaciones.  
  
         ![editar perfil en Salesforce](./media/salesforce-edit-profile.png "editar perfil en Salesforce")  
  
    -   Asegúrese de que las siguientes casillas están activadas:   
        - **API Enabled** (API habilitada)
        - **Ver todos los datos** 
        - **Manage Salesforce CRM Content** (Administrar contenido CRM de Salesforce)
        - **Administrar usuarios**
        
        Si estas casillas no están activadas, es posible que deba ponerse en contacto con Salesforce para agregarlas a su cuenta.  
             
3.  Si su organización tiene habilitada la opción **Salesforce CRM Content** (Contenido CRM de Salesforce), asegúrese de que la cuenta administrativa actual también la tenga habilitada.  
  
    1.  Vaya a la página de configuración de Salesforce.  
  
         ![configuración de Salesforce](./media/salesforce-setup.png "configuración de Salesforce")  
  
    2.  En el menú lateral, seleccione **Administrar usuarios** y haga clic en **Usuarios**.  
  
         ![menú de usuarios de Salesforce](./media/salesforce-menu-users.png "menú de usuarios de Salesforce")  
  
    3.  Seleccione el usuario administrativo actual de su usuario de Cloud App Security dedicado.  
  
    4.  Asegúrese de que está seleccionada la casilla **Salesforce CRM Content User** (Usuario de contenido CRM de Salesforce).  
  
         Si no está activada, haga clic en **Editar** y después active la casilla.  
  
         ![usuario de contenido CRM de Salesforce](./media/salesforce-crm-content-user.png "usuario de contenido CRM de Salesforce")  
  
    5.  Haga clic en **Guardar**.  
  
4.  En la consola de Cloud App Security, haga clic en **Investigar** y, después, en **Aplicaciones conectadas**.  
  
5.  En la página **Conectores de aplicaciones**, haga clic en el botón del signo más y, después, en **Salesforce**.  
  
     ![conectarse a Salesforce](./media/connect-salesforce.png "conectarse a Salesforce")  
  
6.  En la página de configuración de Salesforce, en la pestaña API, haga clic en **Seguir vínculo**, en función de la instancia que vaya a instalar.  
  
7.  Se abrirá la página de inicio de sesión de Salesforce. Escriba sus credenciales para permitir que Cloud App Security tenga acceso a la aplicación de Salesforce de su equipo.  
  
     ![inicio de sesión en Salesforce](./media/salesforce-logon.png "inicio de sesión en Salesforce")  
  
8.  Salesforce le preguntará si quiere permitir que Cloud App Security acceda a la información y el registro de actividad de su equipo y que realice actividades como cualquier miembro del equipo. Para continuar, haga clic en **Permitir**.  
  
9. En este momento recibirá una notificación que le indicará si la implementación se ha llevado a cabo correcta o incorrectamente. Cloud App Security ya está autorizado en Salesforce.com.  
  
10. Si vuelve a la consola de Cloud App Security, debería aparecer un mensaje que le indica que Salesforce se ha conectado correctamente.  
  
11. Haga clic en **Probar API** para confirmar que la conexión se ha realizado correctamente.  
  
     La prueba puede tardar unos minutos. Cuando reciba la notificación de que se ha realizado correctamente, haga clic en **Listo**.  
  
  
Después de conectarse a Salesforce, recibirá eventos de este modo: desencadenadores en el momento de la conexión, eventos de inicio de sesión y traza de auditoría de configuración de los 60 días anteriores a la conexión, y supervisión de eventos de los 30 días anteriores o del día anterior, en función de su licencia de supervisión de eventos de Salesforce. La API de Cloud App Security se comunica directamente con las API disponibles de Salesforce. Dado que Salesforce limita el número de llamadas API que puede recibir, Cloud App Security lo tiene en cuenta y respeta la limitación. Las API de Salesforce envían cada respuesta con un campo para los contadores de API, incluido el total disponible y restante. Cloud App Security lo calcula como un porcentaje y siempre se asegura de que quede como restante un 10 % de las llamadas de API disponibles. 

> [!NOTE]
> La limitación de Cloud App Security se calcula únicamente según sus propias llamadas API con Salesforce, no según las de otras aplicaciones que realizan llamadas API con Salesforce.
> La restricción de las llamadas API debido a la limitación puede reducir la velocidad a la que se ingieren los datos en Cloud App Security, pero normalmente se pone al día por la noche.


Cloud App Security procesa los eventos de Salesforce de la manera siguiente: 
  
- Eventos de inicio de sesión cada 15 minutos
- Configuración de registros de auditoría cada 15 minutos
- Salesforce registra la actividad de uso durante un período de 24 horas, desde las 12:00 a.m. a las 11:59 p.m. hora UTC. Los eventos de Salesforce generan datos de registro en tiempo real. Sin embargo, Salesforce genera archivos de registro el día después de un evento, fuera de horas punta. Por lo tanto, los datos de archivos de registro no están disponibles durante al menos un día después de un evento. Para más información sobre los eventos de Salesforce, consulte el artículo sobre el [uso de supervisión de eventos](https://developer.salesforce.com/docs/atlas.en-us.api_rest.meta/api_rest/using_resources_event_log_files.htm).


## <a name="next-steps"></a>Pasos siguientes  
[Controlar las aplicaciones en la nube con directivas](control-cloud-apps-with-policies.md)   

[Los clientes Premier también pueden elegir Cloud App Security directamente desde el Portal Premier.](https://premier.microsoft.com/)  
  
  