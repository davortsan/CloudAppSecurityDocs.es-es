---
title: Privacidad de las actividades
description: En este artículo se proporciona información sobre cómo configurar la supervisión de la actividad para que cumpla con la Directiva de privacidad del usuario.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 05/27/2020
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 6de413cc6067ea43f5c2d677e421c09ffddcd94d
ms.sourcegitcommit: 3464ce8ed73d1bfaf02e4e78007766ea18350d9f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/15/2020
ms.locfileid: "86402668"
---
# <a name="activity-privacy"></a>Privacidad de las actividades

*Se aplica a: Microsoft Cloud App Security*

Microsoft Cloud App Security proporciona a las empresas la capacidad de determinar con detalle qué usuarios desean supervisar en función de la pertenencia a grupos. La privacidad de la actividad agrega la capacidad de cumplir las normas de cumplimiento de su organización sin poner en peligro la privacidad del usuario. Esto se consigue permitiendo supervisar a los usuarios manteniendo su privacidad ocultando sus actividades en el registro de actividad. Solo los administradores autorizados tienen la opción de elegir la opción de ver estas actividades privadas, con la auditoría de cada instancia en el registro de gobernanza.

## <a name="configure-activity-privacy-user-groups"></a>Configurar grupos de usuarios de privacidad de actividad

Puede tener usuarios en Cloud App Security que desee supervisar pero, debido a las regulaciones de cumplimiento, debe limitar las personas que pueden hacerlo. La privacidad de la actividad permite definir un grupo de usuarios para el que se ocultarán las actividades de forma predeterminada.

Para configurar los grupos de privacidad de usuario, primero debe [importar los grupos de usuarios](user-groups.md) a Cloud App Security. De forma predeterminada, verá los siguientes grupos:

- Grupo de usuarios **Aplicación**: un grupo integrado que le permite ver las actividades realizadas por las aplicaciones de Office 365 y Azure AD.

- Grupo de **usuarios externos** : todos los usuarios que no son miembros de ninguno de los dominios administrados que configuró para su organización.

1. En la barra de menús, haga clic en el engranaje de configuración y seleccione **implementación de ámbito y privacidad**.

    ![icono de configuración](media/settings-icon.png)

1. Para establecer que los grupos específicos se supervisan mediante Cloud App Security, en la pestaña privacidad de la **actividad** , haga clic en el icono del signo más.
    ![icon](media/plus-icon.png)

1. En el cuadro de diálogo **agregar grupos de usuarios** , en **seleccionar grupos de usuarios**, seleccione todos los grupos que desea convertir en privados en Cloud App Security y, a continuación, haga clic en **Agregar**.

    ![Captura de pantalla que muestra el cuadro de diálogo agregar grupos de usuarios](media/activity-privacy-add-user-groups.png)

    > [!NOTE]
    > Una vez que se agrega un grupo de usuarios, todas las actividades realizadas por los usuarios del grupo se convertirán en privadas desde entonces. Las actividades existentes no se ven afectadas.

## <a name="assign-admins-permission-to-view-private-activities"></a>Asignación de permisos de administradores para ver actividades privadas

1. En la barra de menús, haga clic en el engranaje de configuración y seleccione **administrar acceso de administrador**.

    ![icono de configuración](media/settings-icon.png)

1. Para conceder a los administradores específicos permiso para ver actividades privadas, en la pestaña **permisos de privacidad** de la actividad, haga clic en el icono de signo más.
    ![icon](media/plus-icon.png)

1. En el cuadro de diálogo **Agregar permiso de administrador** , escriba el UPN o la dirección de correo electrónico del administrador y, a continuación, haga clic en **Agregar permiso**.

    ![Captura de pantalla que muestra el cuadro de diálogo Agregar permiso de administrador](media/activity-privacy-add-admin-permission.png)

    > [!NOTE]
    > Solo se puede conceder permiso a los administradores para ver actividades privadas.

## <a name="viewing-private-activities"></a>Ver actividades privadas

Una vez que un administrador ha concedido el permiso adecuado para ver actividades privadas, tiene la opción de elegir ver estas actividades en el registro de actividad.

### <a name="to-view-private-activities"></a>Para ver actividades privadas

1. En la página **registro de actividad** , a la derecha de la tabla de actividad, haga clic en el icono de configuración y, a continuación, seleccione **Mostrar actividades privadas**.

    ![Captura de pantalla que muestra el icono de configuración del registro de actividad](media/activity-privacy-view-settings-icon.png)

1. En el cuadro de diálogo **Mostrar actividades privadas** , haga clic en **Aceptar** para confirmar que entiende que la acción se está auditando. Una vez confirmadas, las actividades privadas se muestran en el registro de actividad y la acción se registra en el registro de gobierno.

[!INCLUDE [Open support ticket](includes/support.md)]
