---
title: Conectar Dropbox con Microsoft Cloud App Security | Microsoft Docs
description: "En este tema se proporciona información sobre cómo conectar la aplicación Dropbox con Cloud App Security mediante el conector de API."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 10/15/2016
ms.topic: get-started-article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: 4acd93f4-b885-4e1f-a385-43b5db02a3ee
ms.reviewer: reutam
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: e41c04d25f12aa5207ef9ffbb6a22f4b894e92cb
ms.openlocfilehash: e6c450215330f2b4cb1f52156aa5f80653d522fc


---

# <a name="connect-dropbox-to-microsoft-cloud-app-security"></a>Conectar Dropbox con Microsoft Cloud App Security
En esta sección se proporcionan instrucciones para conectar Cloud App Security con una cuenta de Dropbox existente mediante las API del conector.  
 
 
Dado que Dropbox permite el acceso a archivos desde vínculos compartidos sin iniciar sesión, Cloud App Security registra estos usuarios como usuarios no autenticados. Si ve usuarios de Dropbox no autenticados, puede tratarse de usuarios ajenos a la organización, o bien pueden ser usuarios reconocidos de la organización que no han iniciado sesión.

## <a name="how-to-connect-dropbox-to-cloud-app-security"></a>Cómo conectar Dropbox con Cloud App Security  
  
1.  En la consola de Cloud App Security, haga clic en **Investigar** y, después, en **Aplicaciones conectadas**.  
  
2.  En la página **Conectores de aplicaciones**, haga clic en el botón **Conectar una aplicación** y, después, en **Dropbox**.  
  
     ![conectar Dropbox](./media/connect-dropbox.png "connect dropbox")  
  
3.  En el elemento emergente, escriba la dirección de correo electrónico de la cuenta de administrador.  
  
4.  Haga clic en **Generar vínculo**.  
  
5.  Haga clic en **Siga este vínculo**.  
  
     Esto hace que se abra la página de inicio de sesión de Dropbox. Escriba sus credenciales para permitir que Cloud App Security tenga acceso a la instancia de Dropbox de su equipo.  
  
6.  Dropbox le preguntará si quiere permitir que Cloud App Security acceda a la información y el registro de actividad de su equipo y que realice actividades como cualquier miembro del equipo. Para continuar, haga clic en **Permitir**.  
  
7.  De vuelta en la consola de Cloud App Security, debería recibir un mensaje que indica que Dropbox se ha conectado correctamente.  
  
8.  Haga clic en **Probar API** para confirmar que la conexión se ha realizado correctamente.  
  
     La prueba puede tardar unos minutos. Cuando reciba la notificación de que se ha realizado correctamente, haga clic en **Cerrar**.  
  
Después de conectar Dropbox, recibirá eventos de 60 días anteriores a la conexión.

> [!NOTE] 
> Los eventos de Dropbox para agregar un archivo se mostrarán en Cloud App Security como Cargar archivo para alinearse con las demás aplicaciones conectadas a Cloud App Security. 
 
## <a name="see-also"></a>Consulte también  
[Controlar las aplicaciones en la nube con directivas](control-cloud-apps-with-policies.md)   
[Para obtener soporte técnico, visite la página de soporte técnico asistido de Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Los clientes Premier también pueden elegir Cloud App Security directamente desde el Portal Premier.](https://premier.microsoft.com/)  
  
  


<!--HONumber=Nov16_HO4-->


