---
title: "Controlar qué aplicaciones en la nube de terceros obtienen permisos | Microsoft Docs"
description: "Este artículo proporciona información sobre cómo puede controlar, prohibir y permitir permisos de aplicación de terceros."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 3/19/2017
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: 137e0630-5440-4c49-bfe4-48bbc64575e2
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 5205f05b470ed61d09a70e5be066e02f4f02a9cf
ms.sourcegitcommit: 0d4748ea2a71e6ee2b0fa1c0498d9219bfbda29a
translationtype: HT
---
# <a name="manage-app-permissions"></a>Administrar permisos de aplicación
Muchas aplicaciones de productividad de terceros que puedan instalar los usuarios profesionales de su organización solicitan permiso para acceder a datos e información de usuario e iniciar sesión en nombre del usuario en otras aplicaciones de nube, como Office 365.  Cuando los usuarios instalan estas aplicaciones, a menudo hacen clic en Aceptar sin revisar detenidamente los detalles en el mensaje, incluyendo la concesión de permisos a la aplicación.  Este problema se agrava por el hecho de que es posible que el departamento de TI no tenga suficiente información para evaluar el riesgo de seguridad que supone una aplicación frente a la ventaja de productividad que ofrece. Dado que aceptar permisos de aplicación de terceros es un riesgo de seguridad potencial para la organización, supervisar los permisos de aplicación que conceden los usuarios le ofrece la visibilidad y el control necesarios para proteger a los usuarios y las aplicaciones. Los permisos de aplicación de Cloud App Security le permiten ver qué aplicaciones instaladas por el usuario tienen acceso a los datos de Office 365, los permisos que tienen y qué usuarios les concedieron acceso a sus cuentas de Office 365. Los permisos de aplicación le ayudan a decidir a qué aplicaciones permite que los usuarios tengan acceso y cuáles quiere prohibir.


## <a name="working-with-the-app-permissions-page"></a>Trabajar con la página de permisos de aplicación

La pestaña **Permisos de aplicación** muestra información sobre los permisos de aplicación en el inquilino de Office 365.

Para obtener acceso a la pestaña Permisos de aplicación:

1. En el portal Cloud App Security, haga clic en **Investigar** y, en **Aplicaciones conectadas**, seleccione **Office 365**. 
> [!Note]
> Primero tiene que conectar Cloud App Security a Office 365 para trabajar con los permisos de aplicación.

2. Después, en el panel de Office 365, haga clic en la pestaña **Permisos de aplicación**.


 ![permisos de aplicación](./media/app-permissions.png)

La página Permisos de aplicación proporciona la siguiente información sobre cada aplicación de terceros a la que se han concedido permisos:

|Elemento|Significado|
|-------|----------------|
|Icono Básica en la barra de consulta de aplicación  |Seleccione esta opción para cambiar a la consulta en la vista básica.|
|Icono Avanzada en la barra de consulta de aplicación  |Seleccione esta opción para cambiar a la consulta en la vista avanzada.|
|Icono Abrir o cerrar todos los detalles en la lista de aplicaciones  |Seleccione este icono para ver más o menos detalles sobre cada aplicación.|
|Icono Exportar en la lista de aplicaciones  |Seleccione este icono para exportar un archivo CSV que contiene una lista de aplicaciones, el número de usuarios para cada aplicación, los permisos asociados a la aplicación, el nivel de permisos, el estado de la aplicación y el nivel de uso de la comunidad.|
|Aplicación|Nombre de la aplicación. Seleccione el nombre para ver más información, incluida la descripción, el publicador, el sitio web de la aplicación y el id.|
|Autorizado por|El número de usuarios que han autorizado esta aplicación para obtener acceso a su cuenta de Office 365 y han concedido permisos a la aplicación. Seleccione el número para ver más información, incluida una lista de correos electrónicos de usuario, y si un administrador ha aceptado previamente la aplicación.|
|Nivel de permisos  |El icono y texto de nivel de permisos y que indica Alto, Medio o Bajo. El nivel indica el nivel de acceso que tiene esta aplicación a los datos de Office 365. Por ejemplo, Bajo podría indicar que la aplicación solo tiene acceso a los perfiles y nombres de usuario. Seleccione el nivel para obtener más información, incluidos los permisos concedidos a la aplicación, el uso de la comunidad o actividad relacionada en el [Registro de gobierno](governance-actions.md).|
|Estado de la aplicación, ya sea Prohibida, Aprobada o Sin determinar.  |Un administrador puede marcar una aplicación como Aprobada, Prohibida, o dejarla como Sin determinar.|


## <a name="ban-or-approve-an-app"></a>Prohibir o aprobar una aplicación
1. En la página Permisos de aplicación, haga clic en la aplicación para abrir el cajón de la aplicación y obtener más información sobre ella y los permisos que se le han concedido. Puede hacer clic en el vínculo Permisos para ver una lista completa de los permisos concedidos a la aplicación. En Uso de la comunidad, puede ver la frecuencia de uso de la aplicación entre otras organizaciones. También puede hacer clic en el vínculo Actividad relacionada para ver las actividades que se muestran en el registro de gobierno relacionadas con esta aplicación.
2. Para prohibir la aplicación, haga clic en el icono Prohibir al final de la fila de la aplicación en la tabla. <br></br>
 ![icono Prohibir aplicación](./media/ban-app-icon.png) <br></br>
Cuando prohíbe una aplicación, puede elegir si quiere que los usuarios sepan que la aplicación que han instalado y autorizado anteriormente ha sido prohibida, estará deshabilitada y no tendrá acceso a Office 365. Si no quiere que lo sepan, anule la selección de Enviar una notificación a los usuarios que hayan concedido permiso a esta aplicación prohibida en el cuadro de diálogo Prohibir la aplicación.

    ![prohibir aplicación](./media/ban-app.png)
> [!Note]
> Se recomienda permitir que los usuarios de la aplicación sepan que se ha prohibido el uso de la aplicación.

3. Para aprobar la aplicación, haga clic en el icono Aprobar al final de la fila en la tabla. <br></br>
 ![Aprobar aplicación](./media/approve-app.png) <br></br>
El icono se vuelve verde y se aprueba la aplicación para todos los usuarios de Office 365.
> [!Note]
> Marcar una aplicación como aprobada no tiene efecto para el usuario final. Solo sirve para ayudarle a marcar visualmente las aplicaciones que se han aprobado y distinguirlas de las que todavía no se han revisado.

3. Escriba el mensaje que quiere enviar a los usuarios de la aplicación en el cuadro Escriba un mensaje de notificación personalizado y actualice la dirección de respuesta del correo electrónico de notificación si es necesario. 
 Haga clic en **Prohibir aplicación** para enviar el correo y prohibir que los usuarios de Office 365 la usen.


## <a name="query-app-permissions"></a>Permisos de aplicación de consulta

### <a name="query-in-the-advanced-view"></a>Consulta en la vista Avanzada 
1. En la vista avanzada, use la lista desplegable **Seleccionar un filtro** para restringir la búsqueda. Agregue "operadores", "es igual a" o "no es igual a" a un valor seleccionado para completar la consulta.
2. Elija el icono **Agregar un filtro** para agregar filtros adicionales para refinar la consulta. Los filtros se aplicarán automáticamente y se actualizará la lista de aplicaciones.
3. Elija el icono **Quitar un filtro** junto al filtro para quitar los filtros.
Los filtros que puede elegir son:
- Aplicación: muestra aplicaciones de terceros con los nombres seleccionados a las que se ha concedido acceso a Office 365.

- Usuario: muestra aplicaciones que ha autorizado este usuario.

- Permisos: muestra aplicaciones que requieren los permisos seleccionados.

- Estado de la aplicación: muestra aplicaciones según su estado, aprobada, prohibida o sin determinar.

- Nivel de permiso: muestra aplicaciones basándose en los niveles de permiso seleccionados.

- Uso de la comunidad: muestra aplicaciones basándose en el nivel de uso de la comunidad, ya sea poco frecuente, raro o común.

### <a name="query-in-the-basic-view"></a>Consulta en la vista básica 
En la vista básica, seleccione valores de las listas desplegables para mostrar las aplicaciones específicas. Puede seleccionar varios valores en las listas desplegables. Los menús desplegables que puede usar para realizar consultas son: 
- Aplicación: muestra aplicaciones de terceros con los nombres seleccionados a las que se ha concedido acceso a Office 365.

- Usuario: muestra aplicaciones que ha autorizado este usuario.

- Permisos: muestra aplicaciones que requieren los permisos seleccionados.

- Estado de la aplicación: muestra aplicaciones según su estado, aprobada, prohibida o sin determinar.

- Nivel de permiso: muestra aplicaciones basándose en los niveles de permiso seleccionados.

- Uso de la comunidad: muestra aplicaciones basándose en el nivel de uso de la comunidad, ya sea poco frecuente, raro o común.
Los filtros se aplicarán automáticamente y se actualizará la lista de aplicaciones. 

## <a name="see-also"></a>Consulte también  
[Controlar las aplicaciones en la nube con directivas](control-cloud-apps-with-policies.md)   
[Para obtener soporte técnico, visite la página de soporte técnico asistido de Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Los clientes Premier también pueden elegir Cloud App Security directamente desde el Portal Premier.](https://premier.microsoft.com/)  
  
  