---
title: 'Controlar qué aplicaciones de OAuth de nube de terceros obtienen permisos: Cloud App Security | Microsoft Docs'
description: En este artículo se proporciona información sobre cómo puede controlar, prohibir y permitir aplicaciones de OAuth de terceros.
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
ms.openlocfilehash: 37b4f17539b0d160e8650f5478741f0941e50648
ms.sourcegitcommit: 4f3883a9e85d0aaf2802b10433b221c3f1838d88
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/13/2020
ms.locfileid: "79285289"
---
# <a name="manage-oauth-apps"></a>Administración de aplicaciones de OAuth

*Se aplica a: Microsoft Cloud App Security*

Muchas aplicaciones de productividad de terceros que pueden instalar los usuarios empresariales de su organización solicitan permiso para acceder a la información y los datos de los usuarios, e iniciar sesión en nombre del usuario en otras aplicaciones en la nube, como Office 365, G Suite y Salesforce. Cuando los usuarios instalan estas aplicaciones, suelen hacer clic en aceptar sin revisar atentamente los detalles en el símbolo del sistema, incluida la concesión de permisos a la aplicación. Este problema se agrava por el hecho de que puede que no tenga suficiente información para sopesar el riesgo de seguridad de una aplicación frente a la ventaja de productividad que proporciona. Dado que aceptar permisos de aplicación de terceros es un riesgo de seguridad potencial para su organización, la supervisión de los permisos de aplicación que conceden los usuarios le ofrece la visibilidad y el control necesarios para proteger a los usuarios y las aplicaciones. Los permisos de la aplicación Microsoft Cloud App Security permiten ver qué aplicaciones OAuth instaladas por el usuario tienen acceso a los datos de Office 365, G Suite y Salesforce. Cloud App Security le indica qué permisos tienen las aplicaciones y a qué usuarios se les concede acceso a sus cuentas de Office 365, G Suite y Salesforce. Los permisos de la aplicación le ayudan a decidir qué aplicaciones permiten a los usuarios tener acceso a las que desea prohibir.

Para obtener más información sobre cómo investigar aplicaciones OAuth, consulte [investigación de aplicaciones OAuth de riesgo](investigate-risky-oauth.md).

## <a name="working-with-the-oauth-apps-page"></a>Trabajar con la página de aplicaciones de OAuth

La página **OAuth** muestra información sobre los permisos de la aplicación en las aplicaciones conectadas.

Para tener acceso a la pestaña OAuth:

En el portal de Cloud App Security, haga clic en **investigar**y, a continuación, en **aplicaciones de OAuth**.

![permisos de aplicación](media/app-permissions.png)

La página de aplicaciones de OAuth proporciona la siguiente información sobre cada aplicación de OAuth a la que se concedieron permisos:

|Elemento|Significado|Se aplica a|
|-------|-------|-------|
|Icono básico en la barra de consulta de la aplicación  |Cambie a consulta en la vista básica.|Office 365, G Suite, Salesforce|
|Icono avanzado en la barra de consulta de la aplicación  |Cambie a consulta en la vista avanzada.|Office 365, G Suite, Salesforce|
|Icono abrir o cerrar todos los detalles de la lista de aplicaciones  |Vea más o menos detalles sobre cada aplicación.|
|Icono de exportación en la lista de aplicaciones  |Exporte un archivo CSV que contiene una lista de aplicaciones, el número de usuarios de cada aplicación, los permisos asociados a la aplicación, el nivel de permisos, el estado de la aplicación y el nivel de uso de la comunidad.|Office 365, G Suite, Salesforce|
|Aplicación|Nombre de la aplicación. Seleccione el nombre para ver más información, incluida la descripción, el publicador (para Office 365), el sitio web de la aplicación y el identificador.|Office 365, G Suite, Salesforce|
|Autorizado por|El número de usuarios que han autorizado esta aplicación para acceder a la cuenta de la aplicación y que han concedido los permisos de aplicación. Seleccione el número para ver más información, incluida una lista de correos electrónicos de usuario y si un administrador ha dado su consentimiento previamente a la aplicación.|Office 365, G Suite, Salesforce|
|Nivel de permisos  |Icono de nivel de permisos y texto que indica un valor alto, medio o bajo. El nivel indica la cantidad de acceso que tiene esta aplicación a los datos de la aplicación. Por ejemplo, bajo puede indicar que la aplicación solo tiene acceso al perfil y el nombre del usuario. Seleccione el nivel para ver más información, incluidos los permisos concedidos a la aplicación, el uso de la comunidad o la actividad relacionada en el [registro de gobierno](governance-actions.md).|Office 365, G Suite|
|Estado de la aplicación|Un administrador puede marcar una aplicación como aprobado, prohibido o salir es como indeterminada.|Office 365, G Suite, Salesforce|
|Uso de la comunidad|Muestra la popularidad de la aplicación entre todos los usuarios (común, inusual, poco frecuente)|Office 365, G Suite, Salesforce|
|Última autorización|Fecha más reciente en la que un usuario ha concedido permisos a esta aplicación.|Office 365, Salesforce|
|Editor|Nombre del proveedor que proporciona la aplicación.|Office 365|
|Usado por última vez|Fecha más reciente en la que cualquier usuario de la organización usó esta aplicación.|Salesforce|

## <a name="ban-or-approve-an-app"></a>Prohibir o aprobar una aplicación

1. En la página **aplicaciones de OAuth** , haga clic en la aplicación para abrir el cajón de la **aplicación** y ver más información sobre la aplicación y los permisos que se le han concedido.

    - Haga clic en el vínculo **permisos** para ver una lista completa de los permisos concedidos a la aplicación.
    - En **uso**de la comunidad, puede ver la frecuencia con que la aplicación se encuentra en otras organizaciones.
    - Haga clic en el vínculo **actividad relacionada** para ver las actividades que aparecen en el registro de gobierno relacionado con esta aplicación.

2. Para prohibir la aplicación, haga clic en el icono de veto al final de la fila de la aplicación en la tabla.

    ![icono de prohibición de aplicación](media/ban-app-icon.png)

    - Puede elegir si desea indicar a los usuarios que la aplicación que ha instalado y autorizado se ha prohibido. La notificación permite que los usuarios sepan que la aplicación se deshabilitará y no tendrán acceso a la aplicación conectada. Si no quiere que sepan, anule la selección de **notificar a los usuarios que concedieron el acceso a esta aplicación prohibida** en el cuadro de diálogo.
    - Se recomienda permitir que los usuarios de la aplicación sepan que su aplicación está a punto de prohibirse su uso.

    ![vetar aplicación](media/ban-app.png)

3. Escriba el mensaje que desea enviar a los usuarios de la aplicación en el cuadro Escriba un mensaje de notificación personalizado. Haga clic en **prohibir aplicación** para enviar el correo y prohibir la aplicación a los usuarios de la aplicación conectada.

4. Para aprobar la aplicación, haga clic en el icono aprobar al final de la fila en la tabla.

    ![aprobar aplicación](media/approve-app.png)

    - El icono se vuelve verde y se aprueba la aplicación para todos los usuarios de la aplicación conectada.
    - Al marcar una aplicación como aprobada, no hay ningún efecto en el usuario final. Este cambio de color está pensado para ayudarle a ver las aplicaciones que ha aprobado para separarlas de las que todavía no ha revisado.

## <a name="revoke-app-and-notify-user"></a>Revocar aplicación y notificar al usuario

Para G Suite y Salesforce, es posible revocar el permiso a una aplicación o notificar al usuario que debe cambiar el permiso. Al revocar el permiso, se quitan todos los permisos concedidos a la aplicación en "aplicaciones empresariales" en Azure AD.

1. En la página **aplicaciones de OAuth** , haga clic en tres puntos al final de la fila de la aplicación y seleccione **notificar al usuario**. De forma predeterminada, se notificará al usuario de la manera siguiente: *ha autorizado la aplicación para tener acceso a su cuenta de G Suite. Esta aplicación entra en conflicto con la Directiva de seguridad de su organización. Considere la posibilidad de conceder o revocar los permisos que asignó a esta aplicación en su cuenta de G Suite. Para revocar el acceso a la aplicación, vaya a: https://security.google.com/settings/security/permissions?hl=en&pli=1 seleccione la aplicación y haga clic en "revocar acceso" en la barra de menús derecha.* Puede personalizar el mensaje que se envía.
2. También puede revocar los permisos para usar la aplicación para el usuario. Haga clic en el icono situado al final de la fila de la aplicación en la tabla y seleccione **revocar aplicación**.

    ![revocar aplicación](media/revoke-app.png)

## <a name="query-oauth-apps"></a>Consulta de aplicaciones de OAuth

Puede consultar aplicaciones de OAuth en la vista **básica** o en la vista **avanzada** . Seleccione los valores de una o varias listas desplegables para mostrar las aplicaciones específicas en la vista básica. En la vista avanzada, use la lista desplegable **seleccionar un filtro** para restringir la búsqueda. Agregue operadores, es igual a o no es igual a un valor seleccionado para completar la consulta.

- Elija el icono **Agregar un filtro** para agregar filtros adicionales para refinar la consulta. Los filtros se aplican automáticamente y se actualiza la lista de aplicaciones.

- Elija el icono **quitar un filtro** situado junto al filtro para quitar los filtros.

## <a name="oauth-app-auditing"></a>Auditoría de la aplicación OAuth

Cloud App Security audita todas las actividades de autorización OAuth para ofrecerle funciones completas de supervisión e investigación de las actividades realizadas. También puede exportar los detalles de los usuarios que autorizaron una aplicación de OAuth específica, lo que le proporciona información adicional sobre los usuarios, que puede usar para realizar un análisis más exhaustivo.

Para exportar el registro, realice los pasos siguientes:

1. En la página **aplicaciones de OAuth** , en la fila en la que aparece la aplicación correspondiente, en **autorizado por**, haga clic en el vínculo que muestra el número de usuarios que han autorizado la aplicación.

1. En la ventana emergente, haga clic en **exportar**.

    ![Captura de pantalla que muestra la exportación de la auditoría de la aplicación OAuth](media/oauth-export-users.png)

## <a name="send-feedback"></a>Enviar comentarios

Si hay una aplicación de OAuth detectada en la organización que parece malintencionada, puede enviar la Cloud App Security comentarios del equipo para que podamos saberlo. Esta característica le permite formar parte de nuestra comunidad de seguridad y mejorar el análisis y la puntuación de riesgo de las aplicaciones de OAuth.

1. En la página **aplicaciones de OAuth** , haga clic en tres puntos al final de la fila de la aplicación y seleccione aplicación de **informes**.

    ![aplicación de informes](media/report-app.png)
2. En la pantalla **Informe de esta aplicación** , puede seleccionar si desea notificar la aplicación como malintencionada o notificar otro problema con la forma en que Cloud App Security percibe la aplicación. Por ejemplo, podría usar un **publicador incorrecto**, **permisos incorrectos**u **otros**. Los datos que envíe se usarán para actualizar la puntuación de riesgo de la aplicación y otros análisis sobre la aplicación.

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Controlar las aplicaciones en la nube con directivas](control-cloud-apps-with-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]
