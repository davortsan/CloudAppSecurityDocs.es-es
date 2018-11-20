---
title: Establecer las preferencias de administración | Microsoft Docs
description: En este artículo se proporcionan instrucciones para configurar las preferencias de administración en Cloud App Security.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 11/13/2018
ms.topic: conceptual
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 85cae50d-f571-4907-9600-da4cc187b43b
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 191f575964eeaa55bbbb1ad0ea8d955f8243b9b0
ms.sourcegitcommit: 77850c6777504c2478611cb71a387e7fcc5f2551
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/13/2018
ms.locfileid: "51596683"
---
# <a name="admin-user-settings"></a>Configuración de usuario de administración

*Se aplica a: Microsoft Cloud App Security*

Microsoft Cloud App Security permite personalizar la configuración de usuario de administrador. La configuración de notificaciones permite a los administradores especificar si quieren recibir notificaciones de alertas por correo electrónico o por mensajes de texto. 

##  <a name="Adminsettings"></a> Personalizar la configuración de administración  
Para configurar sus preferencias como un administrador de Microsoft Cloud App Security, haga clic en su nombre en la barra de menús del portal y seleccione **Configuración de usuario** para establecer lo siguiente:  
  
1.  Haga clic en **Configuración de la cuenta**. Aquí puede configurar y renovar la contraseña para acceder al portal de Cloud App Security.  
  
     ![configuración de usuario personalizada](./media/custom-user-settings.png "configuración de usuario personalizada")  
  
2.  Haga clic en **Notificaciones** y establezca las preferencias de notificación de texto y correo electrónico para los mensajes recibidos del sistema.  Puede establecer la gravedad que determina para qué alertas e infracciones desea recibir correos electrónicos. La gravedad se establece por directiva, así que cuando se desencadenen infracciones, recibirá una notificación de correo según esta configuración y la configuración de gravedad de la directiva que se ha infringido. Los correos se envían al alias asociado con la cuenta de usuario de administrador que se ha usado para iniciar sesión en Cloud App Security. Escriba un número de teléfono para permitir que Cloud App Security le envíe mensajes de texto cuando se envíen alertas y notificaciones y establezca el nivel de gravedad a partir del cual quiera recibir notificaciones por mensaje de texto.  
  
    > [!NOTE] 
    > El número máximo de alertas que se enviarán por mensaje de texto es de diez al día por número de teléfono. El día se calcula según la zona horaria UTC. 
  
    ![configuración de notificación](./media/notification-settings.png "configuración de notificación")  
  
3. Cuando termine, haga clic en **Guardar**.  
  
  
 
  
    
## <a name="next-steps"></a>Pasos siguientes  
[Configurar Cloud Discovery](set-up-cloud-discovery.md)   

[Los clientes Premier también pueden elegir Cloud App Security directamente desde el Portal Premier.](https://premier.microsoft.com/)  
  
  