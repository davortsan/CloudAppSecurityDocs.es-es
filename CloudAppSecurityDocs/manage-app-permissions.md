---
title: Controlar qué aplicaciones de OAuth de nube de terceros obtienen permisos
description: Este artículo proporciona información sobre cómo puede controlar, prohibir y permitir aplicaciones de OAuth de terceros.
ms.date: 08/05/2020
ms.topic: how-to
ms.openlocfilehash: 9a28932b04e0d2e30a0017a59dd25348e7a11270
ms.sourcegitcommit: 72ddcd0f9a83251d588009abf506676612c50267
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/13/2020
ms.locfileid: "97369504"
---
# <a name="manage-oauth-apps"></a>Administración de aplicaciones de OAuth

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Muchas aplicaciones de productividad de terceros que pueden instalar los usuarios empresariales de su organización solicitan permiso para acceder a la información y los datos de los usuarios, e iniciar sesión en nombre del usuario en otras aplicaciones en la nube, como Office 365, Google Workspace y Salesforce. Cuando los usuarios instalan estas aplicaciones, a menudo hacen clic en Aceptar sin revisar detenidamente los detalles en el mensaje, incluyendo la concesión de permisos a la aplicación. Este problema se agrava por el hecho de que es posible que el departamento de TI no tenga suficiente información para evaluar el riesgo de seguridad que supone una aplicación frente a la ventaja de productividad que ofrece. Dado que aceptar permisos de aplicación de terceros es un riesgo de seguridad potencial para la organización, supervisar los permisos de aplicación que conceden los usuarios le ofrece la visibilidad y el control necesarios para proteger a los usuarios y las aplicaciones. Los permisos de aplicación Microsoft Cloud App Security permiten ver qué aplicaciones OAuth instaladas por el usuario tienen acceso a los datos de Office 365, los datos del área de trabajo de Google y los datos de Salesforce. Cloud App Security le indica qué permisos tienen las aplicaciones y a qué usuarios se les concede acceso a sus cuentas de Office 365, Google Workspace y Salesforce. Los permisos de aplicación le ayudan a decidir a qué aplicaciones permite que los usuarios tengan acceso y cuáles quiere prohibir.

Para obtener más información sobre cómo investigar aplicaciones OAuth, consulte [investigación de aplicaciones OAuth de riesgo](investigate-risky-oauth.md).

> [!NOTE]
> Cloud App Security solo identifica las aplicaciones que solicitan permisos "delegados". Para obtener más información, consulte [permisos de aplicación cliente](/azure/active-directory/develop/developer-glossary#permissions).

## <a name="working-with-the-oauth-apps-page"></a>Trabajar con la página de aplicaciones de OAuth

La página **OAuth** muestra información sobre los permisos de sus aplicaciones conectadas.

Para acceder a la pestaña de OAuth:

En el portal de Cloud App Security, haga clic en **Investigar** y después en **Aplicaciones de OAuth**.

![permisos de aplicación](media/app-permissions.png)

La página Aplicaciones de OAuth de aplicación proporciona la siguiente información sobre cada aplicación de OAuth a la que se han concedido permisos:

|Elemento|Qué significa|Se aplica a|
|-------|-------|-------|
|Icono Básica en la barra de consulta de aplicación  |Cambie a consulta en la vista básica.|Office 365, área de trabajo de Google, Salesforce|
|Icono Avanzada en la barra de consulta de aplicación  |Cambie a consulta en la vista avanzada.|Office 365, área de trabajo de Google, Salesforce|
|Icono Abrir o cerrar todos los detalles en la lista de aplicaciones  |Vea más o menos detalles sobre cada aplicación.|
|Icono Exportar en la lista de aplicaciones  |Exporte un archivo CSV que contiene una lista de aplicaciones, el número de usuarios para cada aplicación, los permisos asociados a la aplicación, el nivel de permisos, el estado de la aplicación y el nivel de uso de la comunidad.|Office 365, área de trabajo de Google, Salesforce|
|Aplicación|Nombre de la aplicación. Seleccione el nombre para ver más información, incluida la descripción, el publicador (para Office 365), el sitio web de la aplicación y el identificador.|Office 365, área de trabajo de Google, Salesforce|
|Autorizado por|Número de usuarios que han autorizado esta aplicación para obtener acceso a sus cuentas de aplicación y han concedido permisos a la aplicación. Seleccione el número para ver más información, incluida una lista de correos electrónicos de usuario, y si un administrador ha aceptado previamente la aplicación.|Office 365, área de trabajo de Google, Salesforce|
|Nivel de permisos  |El icono y texto de nivel de permisos que indica Alto, Medio o Bajo. El nivel indica el grado de acceso que tiene esta aplicación a sus datos. Por ejemplo, Bajo podría indicar que la aplicación solo tiene acceso a los perfiles y nombres de usuario. Seleccione el nivel para obtener más información, incluidos los permisos concedidos a la aplicación, el uso de la comunidad o actividad relacionada en el [registro de gobernanza](governance-actions.md).|Office 365, área de trabajo de Google|
|Estado de la aplicación|Un administrador puede marcar una aplicación como Aprobada, Prohibida, o dejarla como Sin determinar.|Office 365, área de trabajo de Google, Salesforce|
|Uso de la comunidad|Muestra la popularidad de la aplicación entre los usuarios (conocida, poco conocida o desconocida)|Office 365, área de trabajo de Google, Salesforce|
|Última autorización|Fecha más reciente en la que un usuario concedió permisos a esta aplicación.|Office 365 y Salesforce|
|Publisher|Nombre del proveedor que proporciona la aplicación.|Office 365|
|Último uso|Fecha más reciente en la que un miembro de la organización usó esta aplicación.|Salesforce|

## <a name="ban-or-approve-an-app"></a>Prohibir o aprobar una aplicación

1. En la página **Aplicación de OAuth**, haga clic en la aplicación para abrir el **Cajón de la aplicación** y obtener más información sobre ella y los permisos que se le han concedido.

    - Haga clic en **permisos** para ver una lista completa de los permisos concedidos a la aplicación.
    - En **uso** de la comunidad, puede ver la frecuencia con que la aplicación se encuentra en otras organizaciones.
    - Haga clic en **actividad relacionada** para ver las actividades que aparecen en el registro de actividades relacionadas con esta aplicación.

2. Para prohibir la aplicación, haga clic en el icono Prohibir al final de la fila de la aplicación en la tabla.

    ![Icono prohibir una aplicación](media/ban-app-icon.png)

    - Puede elegir si quiere indicar a los usuarios que se ha prohibido la aplicación que han instalado y autorizado. La notificación informa a los usuarios de que la aplicación estará deshabilitada y no tendrán acceso a la aplicación conectada. Si no quiere que lo sepan, anule la selección de **Enviar una notificación a los usuarios que hayan concedido permiso a esta aplicación prohibida** en el cuadro de diálogo.
    - Se recomienda permitir que los usuarios de la aplicación sepan que se ha prohibido el uso de la aplicación.

    ![prohibir aplicación](media/ban-app.png)

3. Escriba el mensaje que quiere enviar a los usuarios de la aplicación en el cuadro Escriba un mensaje de notificación personalizado. Haga clic en **Prohibir aplicación** para enviar el correo y prohibir que los usuarios de la aplicación conectada la usen.

4. Para aprobar la aplicación, haga clic en el icono Aprobar al final de la fila en la tabla.

    ![aprobar aplicación](media/approve-app.png)

    - El icono se vuelve verde y se aprueba la aplicación para todos los usuarios de la aplicación conectada.
    - Marcar una aplicación como aprobada no tiene efecto para el usuario final. Este cambio de color sirve para ayudarle a ver las aplicaciones que se han aprobado y distinguirlas de las que todavía no se han revisado.

## <a name="revoke-app-and-notify-user"></a>Revocar la aplicación y enviar una notificación al usuario

En el caso de Google Workspace y Salesforce, es posible revocar el permiso a una aplicación o notificar al usuario que debe cambiar el permiso. Al revocar el permiso, se quitan todos los permisos concedidos a la aplicación en "aplicaciones empresariales" en Azure AD.

1. En la página **Aplicaciones de OAuth**, haga clic en los tres puntos situados al final de la fila de la aplicación y seleccione **Enviar notificación al usuario**. De forma predeterminada, se notificará al usuario de la manera siguiente: *ha autorizado la aplicación para tener acceso a su cuenta de Google Workspace. Esta aplicación entra en conflicto con la Directiva de seguridad de su organización. Considere la posibilidad de conceder o revocar los permisos que asignó a esta aplicación en su cuenta de Google Workspace. Para revocar el acceso a la aplicación, vaya a: https://security.google.com/settings/security/permissions?hl=en&pli=1  Seleccione la aplicación y haga clic en "revocar acceso" en la barra de menús derecha.* Puede personalizar el mensaje que se envía.
2. También puede revocar permisos para usar la aplicación para el usuario. Haga clic en el icono al final de la fila de la aplicación en la tabla y seleccione **Revocar aplicación**.

    ![revocar aplicación](media/revoke-app.png)

## <a name="query-oauth-apps"></a>Consultar aplicaciones de OAuth

Puede consultar aplicaciones de OAuth en la vista **Básica** o la vista **Avanzada**. Seleccione valores de las listas desplegables para mostrar las aplicaciones específicas en la vista Básica. En la vista avanzada, use la lista desplegable **Seleccionar un filtro** para restringir la búsqueda. Agregue "operadores", "es igual a" o "no es igual a" a un valor seleccionado para completar la consulta.

- Elija el icono **Agregar un filtro** para agregar filtros adicionales para refinar la consulta. Los filtros se aplicarán automáticamente y se actualizará la lista de aplicaciones.

- Elija el icono **Quitar un filtro** junto al filtro para quitar los filtros.

## <a name="oauth-app-auditing"></a>Auditoría de la aplicación OAuth

Cloud App Security audita todas las actividades de autorización OAuth para ofrecerle funciones completas de supervisión e investigación de las actividades realizadas. También puede exportar los detalles de los usuarios que autorizaron una aplicación de OAuth específica, lo que le proporciona información adicional sobre los usuarios, que puede usar para realizar un análisis más exhaustivo.

Para exportar el registro, realice los pasos siguientes:

1. En la página **aplicaciones de OAuth** , en la fila en la que aparece la aplicación correspondiente, en **autorizado por**, haga clic en el vínculo que muestra el número de usuarios que han autorizado la aplicación.

1. En el elemento emergente, haga clic en **exportar**.

    ![Captura de pantalla que muestra la exportación de la auditoría de la aplicación OAuth](media/oauth-export-users.png)

## <a name="send-feedback"></a>Envío de comentarios

Si hay una aplicación de OAuth detectada en la organización que parece malintencionada, puede enviar la Cloud App Security comentarios del equipo para que podamos saberlo. Esta característica le permite formar parte de nuestra comunidad de seguridad y mejorar el análisis y la puntuación de riesgo de las aplicaciones OAuth.

1. En la página **Aplicaciones de OAuth**, haga clic en los tres puntos situados al final de la fila de la aplicación y seleccione **Informar sobre aplicación**.

    ![informar de aplicación](media/report-app.png)
2. En la pantalla **Informar sobre esta aplicación**, puede seleccionar si va a informar sobre la aplicación como malintencionada o va a notificar algún otro problema con la manera con la que Cloud App Security percibe la aplicación. Por ejemplo, **Publicador incorrecto**, **Permisos incorrectos** u **Otros**. Los datos que envíe se usarán para actualizar la puntuación de riesgo de la aplicación, así como otros análisis sobre la aplicación.

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Controlar las aplicaciones en la nube con directivas](control-cloud-apps-with-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]
