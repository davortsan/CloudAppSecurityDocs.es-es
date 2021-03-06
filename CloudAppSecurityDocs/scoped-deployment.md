---
title: Establecimiento del ámbito de la implementación de Microsoft Cloud App Security
description: En este artículo se proporciona información acerca de cómo definir el ámbito de la implementación de Cloud App Security, incluyendo o excluyendo usuarios o grupos específicos.
ms.date: 8/25/2019
ms.topic: how-to
ms.openlocfilehash: 94aec27172d83c2884ea91c944ecd80898ae0381
ms.sourcegitcommit: d87372b47ca98e942c2bf94032a6a61902627d69
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/30/2020
ms.locfileid: "96315572"
---
# <a name="scoped-deployment"></a>Implementación con ámbito <a name="scoped-deployment"></a> 

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Microsoft Cloud App Security permite definir el ámbito de la implementación. Establecer el ámbito le permite seleccionar determinados grupos de usuarios que se van a supervisar o excluir de la supervisión para las aplicaciones.

## <a name="include-or-exclude-user-groups"></a>Incluir o excluir grupos de usuarios

Es posible que no desee usar Microsoft Cloud App Security para todos los usuarios de su organización. Establecer el ámbito es especialmente útil cuando quiera limitar la implementación debido a restricciones de licencia. Es posible que también necesite limitar debido a las regulaciones de cumplimiento que requieren que no supervise usuarios de determinados países o regiones. Por ejemplo, puede usar la implementación con ámbito para supervisar solo los empleados en Estados Unidos. Como alternativa, puede evitar que se muestren las actividades de los usuarios que se encuentran en Alemania.

- Para establecer el ámbito de la implementación, primero debe [importar grupos de usuarios](user-groups.md) con Microsoft Cloud App Security. De forma predeterminada, verá los siguientes grupos:

  - Grupo de usuarios **Aplicación**: un grupo integrado que le permite ver las actividades realizadas por las aplicaciones de Office 365 y Azure AD.

  - Grupo de **usuarios externos** : todos los usuarios que no son miembros de ninguno de los dominios administrados que configuró para su organización.

- El establecimiento de una regla de inclusión excluirá automáticamente a todos los grupos que no estén dentro del grupo incluido. Por ejemplo, si establece una regla para incluir a todos los miembros de los grupos de oficinas de EE. UU., no se supervisarán los grupos que no formen parte de ese grupo.

- Los grupos de usuarios excluidos invalidan los grupos de usuarios incluidos. Esto significa que si incluye el grupo de usuarios "Empleados del Reino Unido" pero excluye "Marketing", los miembros de marketing del Reino Unido no se supervisarán incluso si forman parte del grupo **Empleados del Reino Unido**.

1. En la barra de menús, haga clic en el engranaje de configuración y seleccione **Implementación con ámbito**.

    ![icono de configuración](media/settings-icon.png "icono de configuración")

2. Para establecer el ámbito de la implementación a fin de incluir o excluir grupos específicos, primero debe [importar grupos de usuarios](user-groups.md) en Microsoft Cloud App Security.

3. Para establecer que los grupos específicos se supervisan mediante Microsoft Cloud App Security, en la pestaña **incluir** , haga clic en el icono del signo más.
    ![icon](media/plus-icon.png)

4. En el cuadro de diálogo **Crear nueva regla de inclusión**, haga lo siguiente:

    1. En **Escriba el nombre de la regla**, asigne un nombre descriptivo a la regla.
    2. En **Seleccionar grupos de usuarios**, seleccione todos los grupos que desea supervisar con Cloud App Security.
    3. Seleccione si desea aplicar esta regla a todas las aplicaciones conectadas o solo a **aplicaciones específicas**. Si selecciona **aplicaciones específicas**, la regla solo afectará a la supervisión de las aplicaciones que seleccione. Por ejemplo, si selecciona el grupo **Usuarios del equipo de UI** y **Box**, Cloud App Security solo supervisará la actividad de Box para los miembros del grupo de usuarios del equipo de UI y, en el resto de aplicaciones, Cloud App Security supervisará todas las actividades para todos los usuarios.

        ![regla de inclusión](media/include-rule.png)

5. Si quiere establecer determinados grupos para excluirlos de la supervisión, en la pestaña **Excluir**, haga clic en el icono de signo más.

   ![icon](media/plus-icon.png)

6. En el cuadro de diálogo **Crear nueva regla de exclusión**, establezca los parámetros siguientes:

    1. En **Escriba el nombre de la regla**, asigne un nombre descriptivo a la regla.
    En **Seleccionar grupos de usuarios**, seleccione todos los grupos que no quiere que supervise Cloud App Security.
    2. Seleccione si desea aplicar esta regla a todas las aplicaciones conectadas o solo a **aplicaciones específicas**. Si selecciona **aplicaciones específicas**, Cloud App Security dejará de supervisar el grupo seleccionado solo para las aplicaciones que seleccione. Esto significa que si selecciona la interfaz de usuario del grupo **usuarios del equipo** y **Active Directory**, Cloud App Security supervisará toda la actividad de los usuarios excepto Active Directory actividades realizadas por los usuarios del equipo de la interfaz de usuario.

       ![regla de exclusión](media/exclude-rule.png)

## <a name="example-results-for-include-and-exclude-rules"></a>Resultados de ejemplo para las reglas de inclusión y exclusión

Las reglas de inclusión y exclusión que cree funcionan en conjunto para definir el ámbito de la supervisión general realizada por Microsoft Cloud App Security. Este es un ejemplo de reglas de inclusión y exclusión que puede crear, y el resultado final de lo que Microsoft Cloud App Security supervisa después de que estas reglas se ejecuten.

Si crea las reglas siguientes:

- Excluir el grupo de usuarios "Todos los usuarios de Alemania"
- Incluir para el grupo de usuarios "Ventas globales" solo las actividades de Office 365
- Incluir para el grupo de usuarios "Directores de ventas" solo las actividades de Power BI
- Salesforce está conectado con Microsoft Cloud App Security, y no se establece ninguna regla para dicha plataforma.

Se supervisan las actividades de usuario siguientes:

|Usuario|Pertenencia a grupos|Actividades supervisadas|
|----|----|----|
|Adriana|Todos los usuarios de Alemania<br />Ventas globales<br />Directores de ventas|None|
|Alain|Ventas globales|Office 365 y todas las subaplicaciones, a excepción de Power BI|
|Cornel|Ventas globales<br />Directores de ventas|Office 365 y todas las subaplicaciones|
|Raymond|Directores de ventas|Solo Power BI|

> [!NOTE]
> Las otras aplicaciones no se verán afectadas por el ámbito de los grupos con estas reglas.
> En el ejemplo, para Salesforce, se supervisan todas las actividades de todos los grupos de usuarios.

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Configuración de Cloud Discovery](set-up-cloud-discovery.md)

[!INCLUDE [Open support ticket](includes/support.md)]  
