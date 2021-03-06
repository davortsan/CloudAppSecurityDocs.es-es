---
title: Establecer preferencias de administrador
description: En este artículo se proporcionan instrucciones para configurar las preferencias de administración en Cloud App Security.
ms.date: 04/19/2020
ms.topic: how-to
ms.openlocfilehash: 18b5940ad4365a31b7e344860c0f791e306d8890
ms.sourcegitcommit: d87372b47ca98e942c2bf94032a6a61902627d69
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/30/2020
ms.locfileid: "96314790"
---
# <a name="admin-user-settings"></a>Configuración de usuario de administración

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Microsoft Cloud App Security permite personalizar la configuración de usuario de administrador. La configuración de notificaciones permite a los administradores especificar si quieren recibir notificaciones de alertas por correo electrónico o por mensajes de texto.

## <a name="customize-your-admin-settings"></a><a name="Adminsettings"></a>Personalizar la configuración de administración

Para configurar sus preferencias como un administrador de Microsoft Cloud App Security, haga clic en su nombre en la barra de menús del portal y seleccione **Configuración de usuario** para establecer lo siguiente:

1. Haga clic en **idioma**. Aquí puede elegir el idioma que desea usar en el portal de Cloud App Security.

    ![configuración de usuario personalizada](media/custom-language-settings.png)

2. Haga clic en **Notificaciones** y establezca las preferencias de notificación de texto y correo electrónico para los mensajes recibidos del sistema. Puede establecer la gravedad que determina para qué alertas e infracciones desea recibir correos electrónicos. La gravedad se establece por directiva, así que cuando se desencadenen infracciones, recibirá una notificación de correo según esta configuración y la configuración de gravedad de la directiva que se ha infringido. Los correos se envían al alias asociado con la cuenta de usuario de administrador que se ha usado para iniciar sesión en Cloud App Security. Escriba un número de teléfono para permitir que Cloud App Security le envíe mensajes de texto cuando se envíen alertas y notificaciones y establezca el nivel de gravedad a partir del cual quiera recibir notificaciones por mensaje de texto.

    > [!NOTE]
    >
    > - El número máximo de alertas que se enviarán por mensaje de texto es de diez al día por número de teléfono. El día se calcula según la zona horaria UTC.
    > - No se envían notificaciones para eventos IPC Azure Active Directory.

    ![configuración de notificaciones](media/notification-settings.png)

3. Cuando haya terminado, haga clic en **Guardar**.

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Configuración de Cloud Discovery](set-up-cloud-discovery.md)

[!INCLUDE [Open support ticket](includes/support.md)]
