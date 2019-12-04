---
title: 'Establecimiento de las preferencias de administración: Cloud App Security | Microsoft Docs'
description: En este artículo se proporcionan instrucciones para configurar las preferencias de administración en Cloud App Security.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 12/10/2018
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 9f687be6ba51bf7d1fb64803aaabd8397de02db7
ms.sourcegitcommit: 7c93b6f93d2699d466b172590710ed01697bbdad
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74720822"
---
# <a name="admin-user-settings"></a>Configuración de usuario de administración

*Se aplica a: Microsoft Cloud App Security*

Microsoft Cloud App Security permite personalizar la configuración de usuario de administrador. La configuración de notificaciones permite a los administradores especificar si quieren recibir notificaciones de alertas por correo electrónico o por mensajes de texto.

## <a name="Adminsettings"></a>Personalizar la configuración de administración

Para configurar sus preferencias como un administrador de Microsoft Cloud App Security, haga clic en su nombre en la barra de menús del portal y seleccione **Configuración de usuario** para establecer lo siguiente:

1. Haga clic en **Configuración de la cuenta**. Aquí puede configurar y renovar la contraseña para acceder al portal de Cloud App Security.

    ![configuración de usuario personalizada](media/custom-user-settings.png "configuración de usuario personalizada")

2. Haga clic en **Notificaciones** y establezca las preferencias de notificación de texto y correo electrónico para los mensajes recibidos del sistema.  Puede establecer la gravedad que determina para qué alertas e infracciones desea recibir correos electrónicos. La gravedad se establece por directiva, así que cuando se desencadenen infracciones, recibirá una notificación de correo según esta configuración y la configuración de gravedad de la directiva que se ha infringido. Los correos se envían al alias asociado con la cuenta de usuario de administrador que se ha usado para iniciar sesión en Cloud App Security. Escriba un número de teléfono para permitir que Cloud App Security le envíe mensajes de texto cuando se envíen alertas y notificaciones y establezca el nivel de gravedad a partir del cual quiera recibir notificaciones por mensaje de texto.

    > [!NOTE]
    > El número máximo de alertas que se enviarán por mensaje de texto es de diez al día por número de teléfono. El día se calcula según la zona horaria UTC.

    ![configuración de notificaciones](media/notification-settings.png "configuración de notificación")

3. Cuando termine, haga clic en **Guardar**.

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Configurar Cloud Discovery](set-up-cloud-discovery.md)

[!INCLUDE [Open support ticket](includes/support.md)]
