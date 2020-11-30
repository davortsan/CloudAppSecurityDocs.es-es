---
title: Conexión de Dropbox con Cloud App Security
description: En este artículo se proporciona información sobre cómo conectar la aplicación de Dropbox con Cloud App Security mediante el conector de API para la visibilidad y el control del uso.
ms.date: 12/10/2018
ms.topic: how-to
ms.openlocfilehash: adff9a8dc891fa40fb48c739b06a06980d985530
ms.sourcegitcommit: d87372b47ca98e942c2bf94032a6a61902627d69
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/30/2020
ms.locfileid: "96312869"
---
# <a name="connect-dropbox-to-microsoft-cloud-app-security"></a>Conectar Dropbox con Microsoft Cloud App Security

[!INCLUDE [Banner for top of topics](includes/banner.md)]

En este artículo se proporcionan instrucciones para conectar Microsoft Cloud App Security con una cuenta de Dropbox existente mediante las API del conector. Esta conexión le ofrece visibilidad y control del uso de Dropbox. Para obtener información sobre cómo Cloud App Security protege Dropbox, consulte [protección de Dropbox](protect-dropbox.md).

Dado que Dropbox permite el acceso a archivos desde vínculos compartidos sin iniciar sesión, Cloud App Security registra estos usuarios como usuarios no autenticados. Si ve usuarios de Dropbox no autenticados, puede tratarse de usuarios ajenos a la organización, o bien pueden ser usuarios reconocidos de la organización que no han iniciado sesión.

## <a name="how-to-connect-dropbox-to-cloud-app-security"></a>Cómo conectar Dropbox con Cloud App Security

1. En la consola de Cloud App Security, haga clic en **Investigar** y, después, en **Aplicaciones conectadas**.

2. En la página **conectores de aplicaciones** , haga clic en el botón de signo más seguido de **Dropbox**.

    ![conectar Dropbox](media/connect-dropbox.png "conectar Dropbox")

3. En el elemento emergente, escriba la dirección de correo electrónico de la cuenta de administrador.

4. Haga clic en **Generar vínculo**.

5. Haga clic en **Siga este vínculo**.

    Se abre la página de inicio de sesión de Dropbox. Escriba sus credenciales para permitir que Cloud App Security tenga acceso a la instancia de Dropbox de su equipo.

6. Dropbox le pregunta si quiere permitir que Cloud App Security acceda a la información y el registro de actividad de su equipo y que realice actividades como cualquier miembro del equipo. Para continuar, haga clic en **Permitir**.

7. De vuelta en la consola de Cloud App Security, debería recibir un mensaje que indica que Dropbox se ha conectado correctamente.

8. Haga clic en **Probar API** para confirmar que la conexión se ha realizado correctamente.

    La prueba puede tardar unos minutos. Cuando reciba la notificación de que se ha realizado correctamente, haga clic en **Cerrar**.

Después de conectar Dropbox, recibirá eventos de 60 días anteriores a la conexión.

> [!NOTE]
> Los eventos de Dropbox para agregar un archivo se mostrarán en Cloud App Security como Cargar archivo para alinearse con las demás aplicaciones conectadas a Cloud App Security.

Si tiene problemas para conectar la aplicación, consulte [solución de problemas de conectores de aplicaciones](troubleshooting-api-connectors-using-error-messages.md).

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Controlar las aplicaciones en la nube con directivas](control-cloud-apps-with-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]
