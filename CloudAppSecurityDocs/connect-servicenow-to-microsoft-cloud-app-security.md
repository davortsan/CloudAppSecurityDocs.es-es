---
title: Conectar ServiceNow a Cloud App Security
description: En este artículo se proporciona información sobre cómo conectar la aplicación de ServiceNow a Cloud App Security mediante el conector de API para la visibilidad y el control del uso.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 6/24/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: a1214e0067d5c83ff001ff6c0e8a27fb227bc7e9
ms.sourcegitcommit: 9fe879ce7f07933866191724de5f108f43e3f923
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/24/2020
ms.locfileid: "77566831"
---
# <a name="connect-servicenow-to-microsoft-cloud-app-security"></a>Conectar ServiceNow a Microsoft Cloud App Security

*Se aplica a: Microsoft Cloud App Security*

En este artículo se proporcionan instrucciones para conectar Microsoft Cloud App Security a su cuenta de ServiceNow existente mediante la API del conector de aplicaciones. Esta conexión le proporciona visibilidad y control sobre el uso de ServiceNow. Para obtener información sobre cómo Cloud App Security protege ServiceNow, consulte [protección](protect-servicenow.md)de servicenow.

> [!NOTE]
> Se recomienda implementar ServiceNow mediante tokens de aplicación de OAuth, disponibles para Fuji y versiones posteriores (consulte la [documentación de ServiceNow](https://wiki.servicenow.com/index.php?title=OAuth_Applications#gsc.tab=0)pertinente.
> En las versiones anteriores, un [modo de conexión heredado](#legacy-servicenow-connection) está disponible en función del usuario o la contraseña. El nombre de usuario y la contraseña proporcionados solo se usan para la generación de tokens de API y no se guardan después del proceso de conexión inicial.

> [!NOTE]
> Cloud App Security admite las versiones de ServiceNow de Yakarta, Kingston, Eureka, Fiji, Geneva, Helsinki, Estambul, Londres y Madrid. Para conectar ServiceNow con Cloud App Security, debe tener el **Administrador** de roles y asegurarse de que la instancia de servicenow admite el acceso a la API.  Para obtener más información, consulte la [documentación del producto de ServiceNow](https://wiki.servicenow.com/index.php?title=Base_System_Roles#gsc.tab=0).

## <a name="how-to-connect-servicenow-to-cloud-app-security-using-oauth"></a>Cómo conectar ServiceNow a Cloud App Security mediante OAuth

1. Inicie sesión con una cuenta de administrador en su cuenta de ServiceNow.

    > [!NOTE]
    > El nombre de usuario y la contraseña proporcionados solo se usan para la generación de tokens de API y no se guardan después del proceso de conexión inicial.

2. En la barra de búsqueda del **navegador de filtros** , escriba **OAuth** y seleccione **registro de aplicaciones**.

3. En la barra de menús **registros de aplicación** , haga clic en **nuevo** para crear un nuevo perfil de OAuth.

    ![Nuevo perfil de OAuth de ServiceNow](media/servicenow-app-registry.png)

4. En **¿Qué tipo de aplicación de OAuth?**, haga clic en **crear un punto de conexión de API de OAuth para clientes externos**.

    ![Tipo OAuth de ServiceNow](media/servicenow-oauth-app-type.png)

5. En registros de **aplicación nuevo** , rellene los siguientes campos:

    - **Nombre** campo, asigne al nuevo perfil de OAuth el nombre, por ejemplo, CloudAppSecurity.

    - El **identificador de cliente** se genera automáticamente. Copie este identificador, ya que deberá pegarlo en Cloud App Security para completar la conexión.

    - En el campo **secreto de cliente** , escriba una cadena. Si se deja vacío, se genera automáticamente un secreto aleatorio. Cópielo y guárdelo para más adelante.

    - Aumente la **duración del token de acceso** al menos 3.600.

    - Haz clic en **Enviar**.

    ![ID. de Perfil de ServiceNow](media/servicenow-profile-ids.png)

6. En el portal de Cloud App Security, haga clic en **investigar** y, a continuación, en **aplicaciones conectadas**.

7. En la página **conectores de aplicaciones** , haga clic en el botón más y, a continuación, en **ServiceNow**.

    ![conectar ServiceNow](media/connect-servicenow.png "conectar ServiceNow")

8. En el menú emergente, agregue el identificador de usuario de ServiceNow, la contraseña, la dirección URL de la instancia, el identificador de cliente y el secreto de cliente en los cuadros correspondientes. Para buscar el identificador de usuario de ServiceNow, en el portal de ServiceNow, vaya a **usuarios** y, a continuación, busque su nombre en la tabla.

    ![IDENTIFICADOR de usuario de ServiceNow](media/servicenow-userid.png)

9. Haga clic en **Conectar**.

    ![Conexión de ServiceNow a CAS](media/servicenow-portal-connect.png "Conexión de ServiceNow en el portal")

10. Haga clic en **probar ahora**para asegurarse de que la conexión se ha realizado correctamente.

    La prueba puede tardar unos minutos. Después de recibir un aviso de éxito, haga clic en **cerrar**.

Después de conectar ServiceNow, recibirá eventos durante 7 días antes de la conexión.

## <a name="legacy-servicenow-connection"></a>Conexión de ServiceNow heredada

Para conectar ServiceNow con Cloud App Security, debe tener permisos de nivel de administrador y asegurarse de que la instancia de ServiceNow admite el acceso a la API.

1. Inicie sesión con una cuenta de administrador en su cuenta de ServiceNow.

2. Cree una nueva cuenta de servicio para Cloud App Security y adjunte el rol de administrador a la cuenta recién creada.

3. Asegúrese de que el complemento de la API de REST está activado.

    ![Cuenta de ServiceNow](media/servicenow-account.png "Cuenta de ServiceNow")

4. En el portal de Cloud App Security, haga clic en **investigar** y después en **aplicaciones autorizadas**.

5. En la fila de ServiceNow, haga clic en **conectar** en la columna **Estado del conector de aplicaciones** o haga clic en el botón **conectar una aplicación** y luego en **ServiceNow**.

   ![conectar ServiceNow](media/connect-servicenow.png "conectar ServiceNow")

6. En la página Configuración de ServiceNow, en la pestaña API, agregue el identificador de usuario, la contraseña y la dirección URL de la instancia de ServiceNow en los cuadros correspondientes.

7. Haga clic en **Conectar**.

    ![Contraseña de actualización de ServiceNow](media/servicenow-update-password.png "Contraseña de actualización de ServiceNow")

8. Haga clic en **Probar API** para confirmar que la conexión se ha realizado correctamente.

    La prueba puede tardar unos minutos. Después de recibir un aviso de éxito, haga clic en **cerrar**.

Después de conectar ServiceNow, recibirá eventos de 7 días antes de la conexión.

Si tiene problemas para conectar la aplicación, consulte [solución de problemas de conectores de aplicaciones](troubleshooting-api-connectors-using-error-messages.md).

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Controlar las aplicaciones en la nube con directivas](control-cloud-apps-with-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]
