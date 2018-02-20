---
title: Conectar Dropbox con Cloud App Security para la visibilidad y el control del uso | Microsoft Docs
description: "En este tema se proporciona información sobre cómo conectar la aplicación Dropbox con Cloud App Security mediante el conector de API."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 1/15/2018
ms.topic: get-started-article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: 4acd93f4-b885-4e1f-a385-43b5db02a3ee
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: bf26515a37f4471b03235df63eef564326976229
ms.sourcegitcommit: 458e936e1ac548eda37e9bf955b439199bbdd018
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/16/2018
---
# <a name="connect-dropbox-to-microsoft-cloud-app-security"></a>Conectar Dropbox con Microsoft Cloud App Security
En esta sección se proporcionan instrucciones para conectar Cloud App Security con una cuenta de Dropbox existente mediante las API del conector.  
 
 
Dado que Dropbox permite el acceso a archivos desde vínculos compartidos sin iniciar sesión, Cloud App Security registra estos usuarios como usuarios no autenticados. Si ve usuarios de Dropbox no autenticados, puede tratarse de usuarios ajenos a la organización, o bien pueden ser usuarios reconocidos de la organización que no han iniciado sesión.

## <a name="how-to-connect-dropbox-to-cloud-app-security"></a>Cómo conectar Dropbox con Cloud App Security  
  
1.  En la consola de Cloud App Security, haga clic en **Investigar** y, después, en **Aplicaciones conectadas**.  
  
2.  En la página **Conectores de aplicaciones**, haga clic en el botón del signo más y, después, en **Dropbox**.  
  
     ![conectar Dropbox](./media/connect-dropbox.png "conectar Dropbox")  
  
3.  En el elemento emergente, escriba la dirección de correo electrónico de la cuenta de administrador.  
  
4.  Haga clic en **Generar vínculo**.  
  
5.  Haga clic en **Siga este vínculo**.  
  
     Se abre la página de inicio de sesión de Dropbox. Escriba sus credenciales para permitir que Cloud App Security tenga acceso a la instancia de Dropbox de su equipo.  
  
6.  Dropbox le pregunta si quiere permitir que Cloud App Security acceda a la información y el registro de actividad de su equipo y que realice actividades como cualquier miembro del equipo. Para continuar, haga clic en **Permitir**.  
  
7.  De vuelta en la consola de Cloud App Security, debería recibir un mensaje que indica que Dropbox se ha conectado correctamente.  
  
8.  Haga clic en **Probar API** para confirmar que la conexión se ha realizado correctamente.  
  
     La prueba puede tardar unos minutos. Cuando reciba la notificación de que se ha realizado correctamente, haga clic en **Cerrar**.  
  
Después de conectar Dropbox, recibirá eventos de 60 días anteriores a la conexión.

> [!NOTE] 
> Los eventos de Dropbox para agregar un archivo se mostrarán en Cloud App Security como Cargar archivo para alinearse con las demás aplicaciones conectadas a Cloud App Security. 
 
## <a name="see-also"></a>Consulte también  
[Controlar las aplicaciones en la nube con directivas](control-cloud-apps-with-policies.md)   

[Los clientes Premier también pueden elegir Cloud App Security directamente desde el Portal Premier.](https://premier.microsoft.com/)  
  
  