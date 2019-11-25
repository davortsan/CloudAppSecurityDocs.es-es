---
title: 'Control de qué aplicaciones de OAuth en la nube de terceros obtienen permisos: Cloud App Security | Microsoft Docs'
description: Este artículo proporciona información sobre cómo puede controlar, prohibir y permitir aplicaciones de OAuth de terceros.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 9/1/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 4dd033c3cf181e2e18e8ab8e2fc1d48b62865901
ms.sourcegitcommit: 094bb42a198fe733cfd3aec79d74487672846dfa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/24/2019
ms.locfileid: "74461010"
---
# <a name="manage-oauth-apps"></a>Administrar aplicaciones de OAuth

*Se aplica a: Microsoft Cloud App Security*

Muchas aplicaciones de productividad de terceros que puedan instalar los usuarios profesionales de su organización solicitan permiso para acceder a datos e información del usuario e iniciar sesión en nombre de este o en otras aplicaciones en la nube, como Office 365, G Suite y Salesforce. Cuando los usuarios instalan estas aplicaciones, a menudo hacen clic en Aceptar sin revisar detenidamente los detalles en el mensaje, incluyendo la concesión de permisos a la aplicación. Este problema se agrava por el hecho de que es posible que el departamento de TI no tenga suficiente información para evaluar el riesgo de seguridad que supone una aplicación frente a la ventaja de productividad que ofrece. Dado que aceptar permisos de aplicación de terceros es un riesgo de seguridad potencial para la organización, supervisar los permisos de aplicación que conceden los usuarios le ofrece la visibilidad y el control necesarios para proteger a los usuarios y las aplicaciones. Los permisos de aplicación de Microsoft Cloud App Security le permiten ver qué aplicaciones de OAuth instaladas por el usuario tienen acceso a datos de Office 365, de G Suite y de Salesforce. Cloud App Security le indica qué permisos tienen las aplicaciones y qué usuarios les concedieron acceso a sus cuentas de Office 365, G Suite y Salesforce. Los permisos de aplicación le ayudan a decidir a qué aplicaciones permite que los usuarios tengan acceso y cuáles quiere prohibir.

For more information on investigating OAuth apps, see [Investigate risky OAuth apps](investigate-risky-oauth.md).

## <a name="working-with-the-oauth-apps-page"></a>Trabajar con la página de aplicaciones de OAuth

La página **OAuth** muestra información sobre los permisos de sus aplicaciones conectadas.

Para acceder a la pestaña de OAuth:

En el portal de Cloud App Security, haga clic en **Investigar** y después en **Aplicaciones de OAuth**.

![permisos de aplicación](./media/app-permissions.png)

La página Aplicaciones de OAuth de aplicación proporciona la siguiente información sobre cada aplicación de OAuth a la que se han concedido permisos:

|Elemento|Significado|Aplicable a|
|-------|-------|-------|
|Icono Básica en la barra de consulta de aplicación  |Cambie a consulta en la vista básica.|Office 365, G Suite y Salesforce|
|Icono Avanzada en la barra de consulta de aplicación  |Cambie a consulta en la vista avanzada.|Office 365, G Suite y Salesforce|
|Icono Abrir o cerrar todos los detalles en la lista de aplicaciones  |Vea más o menos detalles sobre cada aplicación.|
|Icono Exportar en la lista de aplicaciones  |Exporte un archivo CSV que contiene una lista de aplicaciones, el número de usuarios para cada aplicación, los permisos asociados a la aplicación, el nivel de permisos, el estado de la aplicación y el nivel de uso de la comunidad.|Office 365, G Suite y Salesforce|
|Aplicación|Nombre de la aplicación. Seleccione el nombre para ver más información, incluida la descripción, el publicador (para Office 365), el sitio web de la aplicación y el identificador.|Office 365, G Suite y Salesforce|
|Autorizado por|Número de usuarios que han autorizado esta aplicación para obtener acceso a sus cuentas de aplicación y han concedido permisos a la aplicación. Seleccione el número para ver más información, incluida una lista de correos electrónicos de usuario, y si un administrador ha aceptado previamente la aplicación.|Office 365, G Suite y Salesforce|
|Nivel de permisos  |El icono y texto de nivel de permisos que indica Alto, Medio o Bajo. El nivel indica el grado de acceso que tiene esta aplicación a sus datos. Por ejemplo, Bajo podría indicar que la aplicación solo tiene acceso a los perfiles y nombres de usuario. Seleccione el nivel para obtener más información, incluidos los permisos concedidos a la aplicación, el uso de la comunidad o actividad relacionada en el [registro de gobernanza](governance-actions.md).|Office 365 y G Suite|
|Estado de la aplicación|Un administrador puede marcar una aplicación como Aprobada, Prohibida, o dejarla como Sin determinar.|Office 365, G Suite y Salesforce|
|Uso de la comunidad|Muestra la popularidad de la aplicación entre los usuarios (conocida, poco conocida o desconocida)|Office 365, G Suite y Salesforce|
|Última autorización|Fecha más reciente en la que un usuario concedió permisos a esta aplicación.|Office 365 y Salesforce|
|Publisher|Nombre del proveedor que proporciona la aplicación.|Office 365|
|Último uso|Fecha más reciente en la que un miembro de la organización usó esta aplicación.|Salesforce|

## <a name="ban-or-approve-an-app"></a>Prohibir o aprobar una aplicación

1. En la página **Aplicación de OAuth**, haga clic en la aplicación para abrir el **Cajón de la aplicación** y obtener más información sobre ella y los permisos que se le han concedido.

   - Haga clic en el vínculo **Permisos** para ver una lista completa de los permisos concedidos a la aplicación.
   - En **Uso de la comunidad**, puede ver la frecuencia de uso de la aplicación entre otras organizaciones.
   - Haga clic en el vínculo **Actividad relacionada** para ver las actividades que se muestran en el registro de gobernanza relacionadas con esta aplicación.

2. Para prohibir la aplicación, haga clic en el icono Prohibir al final de la fila de la aplicación en la tabla.

     ![Icono prohibir una aplicación](./media/ban-app-icon.png)

    - Puede elegir si quiere indicar a los usuarios que se ha prohibido la aplicación que han instalado y autorizado. La notificación informa a los usuarios de que la aplicación estará deshabilitada y no tendrán acceso a la aplicación conectada. Si no quiere que lo sepan, anule la selección de **Enviar una notificación a los usuarios que hayan concedido permiso a esta aplicación prohibida** en el cuadro de diálogo.
    - Se recomienda permitir que los usuarios de la aplicación sepan que se ha prohibido el uso de la aplicación.

      ![prohibir aplicación](./media/ban-app.png)

3. Escriba el mensaje que quiere enviar a los usuarios de la aplicación en el cuadro Escriba un mensaje de notificación personalizado. Haga clic en **Prohibir aplicación** para enviar el correo y prohibir que los usuarios de la aplicación conectada la usen.

4. Para aprobar la aplicación, haga clic en el icono Aprobar al final de la fila en la tabla.

   ![aprobar aplicación](./media/approve-app.png)

   - El icono se vuelve verde y se aprueba la aplicación para todos los usuarios de la aplicación conectada.
   - Marcar una aplicación como aprobada no tiene efecto para el usuario final. Este cambio de color sirve para ayudarle a ver las aplicaciones que se han aprobado y distinguirlas de las que todavía no se han revisado.

## <a name="revoke-app-and-notify-user"></a>Revocar la aplicación y enviar una notificación al usuario

En el caso de G Suite y Salesforce, es posible revocar el permiso de una aplicación o notificarle al usuario que deberían cambiar el permiso. When you revoke permission it removes all permissions that were granted to the application under “Enterprise Applications” in Azure AD.

1. En la página **Aplicaciones de OAuth**, haga clic en los tres puntos situados al final de la fila de la aplicación y seleccione **Enviar notificación al usuario**. By default, the user will be notified as follows: *You authorized the app to access your G Suite account. This app conflicts with your organization's security policy. Reconsider giving or revoking the permissions you gave this app in your G Suite account. To revoke app access, go to: https://security.google.com/settings/security/permissions?hl=en&pli=1  Select the app and click 'Revoke access' on the right menu bar.* Puede personalizar el mensaje que se envía.
2. También puede revocar permisos para usar la aplicación para el usuario. Haga clic en el icono al final de la fila de la aplicación en la tabla y seleccione **Revocar aplicación**.

    ![revocar aplicación](./media/revoke-app.png)

## <a name="query-oauth-apps"></a>Consultar aplicaciones de OAuth

Puede consultar aplicaciones de OAuth en la vista **Básica** o la vista **Avanzada**. Seleccione valores de las listas desplegables para mostrar las aplicaciones específicas en la vista Básica. En la vista avanzada, use la lista desplegable **Seleccionar un filtro** para restringir la búsqueda. Agregue "operadores", "es igual a" o "no es igual a" a un valor seleccionado para completar la consulta.

- Haga clic en el icono **Agregar un filtro** para agregar filtros adicionales para refinar la consulta. Los filtros se aplicarán automáticamente y se actualizará la lista de aplicaciones.

- Elija el icono **Quitar un filtro** junto al filtro para quitar los filtros.

## <a name="oauth-app-auditing"></a>OAuth app auditing

Cloud App Security audita todas las actividades de autorización OAuth para ofrecerle funciones completas de supervisión e investigación de las actividades realizadas. You can also export the details of users that authorized a specific OAuth app, providing you with additional information on the users, which you can then use for further analysis.

To export the log, perform the following steps:

1. On the **OAuth apps** page, on the row where the relevant app appears, under **Authorized by**, click the link showing the number of users that authorized the app.

1. In the pop-up window, click **Export**.

    ![Screenshot showing export of OAuth app auditing](media/oauth-export-users.png)

## <a name="send-feedback"></a>Enviar comentarios

Si se detecta una aplicación OAuth en su organización que parece malintencionada, puede enviar comentarios al equipo de Cloud App Security para hacérnoslo saber. Esta característica le permite formar parte de nuestra comunidad de seguridad y mejorar el análisis y la puntuación de riesgo de las aplicaciones OAuth.

1. En la página **Aplicaciones de OAuth**, haga clic en los tres puntos situados al final de la fila de la aplicación y seleccione **Informar sobre aplicación**.

    ![informar de aplicación](./media/report-app.png)
2. En la pantalla **Informar sobre esta aplicación**, puede seleccionar si va a informar sobre la aplicación como malintencionada o va a notificar algún otro problema con la manera con la que Cloud App Security percibe la aplicación. Por ejemplo, **Publicador incorrecto**, **Permisos incorrectos** u **Otros**. Los datos que envíe se usarán para actualizar la puntuación de riesgo de la aplicación, así como otros análisis sobre la aplicación.

## <a name="next-steps"></a>Pasos siguientes

[Controlar las aplicaciones en la nube con directivas](control-cloud-apps-with-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]
