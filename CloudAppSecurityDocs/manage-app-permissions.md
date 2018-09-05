---
title: Controlar qué aplicaciones en la nube de terceros obtienen permisos | Microsoft Docs
description: Este artículo proporciona información sobre cómo puede controlar, prohibir y permitir permisos de aplicación de terceros.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 8/22/2018
ms.topic: article
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 137e0630-5440-4c49-bfe4-48bbc64575e2
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: f391b886783934a07aa295e882ec845fdf74f149
ms.sourcegitcommit: b439f29dc1d0aa8eec783ba45e3d517722a5ebe0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/27/2018
ms.locfileid: "43016996"
---
*Se aplica a: Microsoft Cloud App Security*


# <a name="manage-app-permissions"></a>Administrar permisos de aplicación
Muchas aplicaciones de productividad de terceros que puedan instalar los usuarios profesionales de su organización solicitan permiso para acceder a datos e información del usuario e iniciar sesión en nombre de este o en otras aplicaciones en la nube, como Office 365, G Suite y Salesforce.  Cuando los usuarios instalan estas aplicaciones, a menudo hacen clic en Aceptar sin revisar detenidamente los detalles en el mensaje, incluyendo la concesión de permisos a la aplicación.  Este problema se agrava por el hecho de que es posible que el departamento de TI no tenga suficiente información para evaluar el riesgo de seguridad que supone una aplicación frente a la ventaja de productividad que ofrece. Dado que aceptar permisos de aplicación de terceros es un riesgo de seguridad potencial para la organización, supervisar los permisos de aplicación que conceden los usuarios le ofrece la visibilidad y el control necesarios para proteger a los usuarios y las aplicaciones. Los permisos de aplicación de Microsoft Cloud App Security le permiten ver qué aplicaciones que han instalado los usuarios tienen acceso a los datos de Office 365, de G Suite y de Salesforce, los permisos que tienen y qué usuarios les concedieron acceso a sus cuentas de Office 365, G Suite y Salesforce. Los permisos de aplicación le ayudan a decidir a qué aplicaciones permite que los usuarios tengan acceso y cuáles quiere prohibir.


## <a name="working-with-the-app-permissions-page"></a>Trabajar con la página de permisos de aplicación

La página **Permisos de aplicación** muestra información sobre los permisos de sus aplicaciones conectadas.

Para obtener acceso a la pestaña Permisos de aplicación:

En el portal de Cloud App Security, haga clic en **Investigar** y, después, en **Permisos de aplicación**.


 ![permisos de aplicación](./media/app-permissions.png)

La página Permisos de aplicación proporciona la siguiente información sobre cada aplicación de terceros a la que se han concedido permisos:

|Elemento|Significado|Aplicable a|
|-------|-------|-------|
|Icono Básica en la barra de consulta de aplicación  |Seleccione esta opción para cambiar a la consulta en la vista básica.|Office 365, G Suite y Salesforce|
|Icono Avanzada en la barra de consulta de aplicación  |Seleccione esta opción para cambiar a la consulta en la vista avanzada.|Office 365, G Suite y Salesforce|
|Icono Abrir o cerrar todos los detalles en la lista de aplicaciones  |Seleccione este icono para ver más o menos detalles sobre cada aplicación.|
|Icono Exportar en la lista de aplicaciones  |Seleccione este icono para exportar un archivo CSV que contiene una lista de aplicaciones, el número de usuarios para cada aplicación, los permisos asociados a la aplicación, el nivel de permisos, el estado de la aplicación y el nivel de uso de la comunidad.|Office 365, G Suite y Salesforce|
|Aplicación|Nombre de la aplicación. Seleccione el nombre para ver más información, incluida la descripción, el publicador (para Office 365), el sitio web de la aplicación y el identificador.|Office 365, G Suite y Salesforce|
|Autorizado por|Número de usuarios que han autorizado esta aplicación para obtener acceso a sus cuentas de aplicación y han concedido permisos a la aplicación. Seleccione el número para ver más información, incluida una lista de correos electrónicos de usuario, y si un administrador ha aceptado previamente la aplicación.|Office 365, G Suite y Salesforce|
|Nivel de permisos  |El icono y texto de nivel de permisos y que indica Alto, Medio o Bajo. El nivel indica el grado de acceso que tiene esta aplicación a sus datos. Por ejemplo, Bajo podría indicar que la aplicación solo tiene acceso a los perfiles y nombres de usuario. Seleccione el nivel para obtener más información, incluidos los permisos concedidos a la aplicación, el uso de la comunidad o actividad relacionada en el [registro de gobierno](governance-actions.md).|Office 365 y G Suite|
|Estado de la aplicación|Un administrador puede marcar una aplicación como Aprobada, Prohibida, o dejarla como Sin determinar.|Office 365, G Suite y Salesforce|
|Uso de la comunidad|Seleccione esta opción si quiere conocer la popularidad de la aplicación entre los usuarios (conocida, poco conocida o desconocida).|Office 365, G Suite y Salesforce|
|Última autorización|Fecha más reciente en la que un usuario concedió permisos a esta aplicación.|Office 365 y Salesforce|
|Publicador|Nombre del proveedor que proporciona la aplicación.|Office 365|
|Último uso|Fecha más reciente en la que un miembro de la organización usó esta aplicación.|Salesforce|


## <a name="ban-or-approve-an-app"></a>Prohibir o aprobar una aplicación
1. En la página Permisos de aplicación, haga clic en la aplicación para abrir el cajón de la aplicación y obtener más información sobre ella y los permisos que se le han concedido. Puede hacer clic en el vínculo Permisos para ver una lista completa de los permisos concedidos a la aplicación. En Uso de la comunidad, puede ver la frecuencia de uso de la aplicación entre otras organizaciones. También puede hacer clic en el vínculo Actividad relacionada para ver las actividades que se muestran en el registro de gobierno relacionadas con esta aplicación.
2. Para prohibir la aplicación, haga clic en el icono Prohibir al final de la fila de la aplicación en la tabla. <br></br>
   ![Icono Prohibir una aplicación](./media/ban-app-icon.png) <br></br>
   Cuando prohíbe una aplicación, puede elegir si quiere que los usuarios sepan que la aplicación que han instalado y autorizado anteriormente se ha prohibido, que estará deshabilitada y que no tendrán acceso a la aplicación conectada. Si no quiere que lo sepan, anule la selección de Enviar una notificación a los usuarios que hayan concedido permiso a esta aplicación prohibida en el cuadro de diálogo Prohibir la aplicación.

    ![prohibir aplicación](./media/ban-app.png)
   > [!Note]
   > Se recomienda permitir que los usuarios de la aplicación sepan que se ha prohibido el uso de la aplicación.

3. Para aprobar la aplicación, haga clic en el icono Aprobar al final de la fila en la tabla. <br></br>
   ![Aprobar aplicación](./media/approve-app.png) <br></br>
   El icono se vuelve verde y se aprueba la aplicación para todos los usuarios de la aplicación conectada.
   > [!Note]
   > Marcar una aplicación como aprobada no tiene efecto para el usuario final. Solo sirve para ayudarle a marcar visualmente las aplicaciones que se han aprobado y distinguirlas de las que todavía no se han revisado.

4. Escriba el mensaje que quiere enviar a los usuarios de la aplicación en el cuadro Escriba un mensaje de notificación personalizado y actualice la dirección de respuesta del correo electrónico de notificación si es necesario. 
   Haga clic en **Prohibir aplicación** para enviar el correo y prohibir que los usuarios de la aplicación conectada la usen.

## <a name="revoke-app-and-notify-user"></a>Revocar la aplicación y enviar una notificación al usuario

En el caso de G Suite y Salesforce, es posible revocar el permiso de una aplicación o notificarle al usuario que debería hacerlo. 

1. En la página **Permisos de aplicación**, haga clic en los tres puntos situados al final de la fila de la aplicación y seleccione **Enviar notificación al usuario**. De forma predeterminada, se enviará la siguiente notificación al usuario: *Autorizó que la aplicación Adallom Google Protector accediera a su cuenta de G Suite. Esta aplicación está en conflicto con la directiva de seguridad de la organización. Vuelva a considerar la posibilidad de conceder o revocar los permisos que otorgó a esta aplicación en su cuenta de G Suite. Para revocar el acceso, vaya a: https://security.google.com/settings/security/permissions?hl=en&pli=1: seleccione la aplicación y haga clic en "Revocar aplicación" en la barra de menús de la derecha.* Puede personalizar el mensaje que se envía.
2. También puede revocar permisos para usar la aplicación para el usuario. Para ello, haga clic en el icono situado al final de la fila de la aplicación en la tabla y seleccione **Revocar aplicación**. 

   ![revocar aplicación](./media/revoke-app.png)

## <a name="query-app-permissions"></a>Permisos de aplicación de consulta

Puede consultar los permisos de la aplicación en la vista **Básica** o la vista **Avanzada**. En la vista Básica, seleccione valores de las listas desplegables para mostrar las aplicaciones específicas. En la vista avanzada, use la lista desplegable **Seleccionar un filtro** para restringir la búsqueda. Agregue "operadores", "es igual a" o "no es igual a" a un valor seleccionado para completar la consulta.

- Elija el icono **Agregar un filtro** para agregar filtros adicionales para refinar la consulta. Los filtros se aplicarán automáticamente y se actualizará la lista de aplicaciones.

- Elija el icono **Quitar un filtro** junto al filtro para quitar los filtros.

## <a name="send-feedback"></a>Enviar comentarios

Si se detecta una aplicación OAuth en su organización que parece malintencionada, puede enviar comentarios al equipo de Cloud App Security para hacérnoslo saber. Esta nueva característica le permite formar parte de nuestra comunidad de seguridad y mejorar el análisis y la puntuación de riesgo de las aplicaciones OAuth.
1. En la página **Permisos de aplicación**, haga clic en los tres puntos situados al final de la fila de la aplicación y seleccione **Informar de aplicación**.  

   ![informar de aplicación](./media/report-app.png)
2. En la pantalla **Informar de esta aplicación**, puede seleccionar si va a informar de la aplicación como malintencionada o va a notificar algún otro problema con la manera con la que Cloud App Security percibe la aplicación, por ejemplo, **Publicador incorrecto** o **Permisos incorrectos**. Los datos que envíe se usarán para actualizar la puntuación de riesgo de la aplicación, así como otros análisis acerca de la aplicación.

 
## <a name="see-also"></a>Consulte también  
[Controlar las aplicaciones en la nube con directivas](control-cloud-apps-with-policies.md)   

[Los clientes Premier también pueden elegir Cloud App Security directamente desde el Portal Premier.](https://premier.microsoft.com/)  
  
  