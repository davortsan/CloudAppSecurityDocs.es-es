---
title: Conexión de WorkDay a Cloud App Security (versión preliminar)
description: En este artículo se proporciona información sobre cómo conectar la aplicación WorkDay a Cloud App Security mediante el conector de API para la visibilidad y el control del uso.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 11/10/2020
ms.topic: how-to
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: c849aace75d1d4268a44e02feaecdcd032a53888
ms.sourcegitcommit: 98f1b892294beb74157cb3452aa5d489e78bbef4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/10/2020
ms.locfileid: "94424544"
---
# <a name="connect-workday-to-microsoft-cloud-app-security"></a>Conexión de WorkDay a Microsoft Cloud App Security

[!INCLUDE [Banner for top of topics](includes/banner.md)]

En este artículo se proporcionan instrucciones para conectar Microsoft Cloud App Security a su cuenta de WorkDay existente mediante la API del conector de aplicaciones. Esta conexión le proporciona visibilidad y control sobre el uso de WorkDay. Para obtener información sobre cómo Cloud App Security protege WorkDay, consulte [protección de WorkDay](protect-workday.md).

## <a name="quick-start"></a>Inicio rápido

Vea nuestro vídeo de inicio rápido que muestra cómo configurar los requisitos previos y realizar los pasos de WorkDay. Una vez que haya completado los pasos del vídeo, puede continuar para [Agregar el conector de WorkDay](#add-connector).

<br />

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4n1ZO]

## <a name="prerequisites"></a>Requisitos previos

La cuenta de WorkDay usada para conectarse a Cloud App Security debe ser miembro de un grupo de seguridad (nuevo o existente). Se recomienda usar un usuario del sistema de integración de WorkDay. El grupo de seguridad debe tener los siguientes permisos seleccionados para las siguientes directivas de seguridad de dominio:

| Área funcional | Directiva de seguridad de dominio | Directiva de seguridad de subdominio | Permisos de informe/tarea | Permisos de integración |
| --- | --- | --- | --- | --- |
| Sistema | Configuración: configuración de inquilinos: General | Configuración: configuración de inquilinos: seguridad | Ver, modificar | Get, Put |
| Sistema | Administración de seguridad | | Ver, modificar | Get, Put |
| Sistema | Auditoría del sistema | | Ver | Obtener |
| Personal | Datos de trabajo: personal | Worker Data: Public Worker Reports (Datos de empleado: informes de trabajadores públicos) | Ver | Obtener |

> [!NOTE]
>
> * La cuenta que se usa para configurar permisos para el grupo de seguridad debe ser un administrador de WorkDay.
> * Para establecer permisos, busque "directivas de seguridad de dominio para área funcional" y, a continuación, busque cada área funcional ("sistema"/"personal") y conceda los permisos que se muestran en la tabla.
> * Una vez que se han establecido todos los permisos, busque "activar cambios en la Directiva de seguridad pendiente" y apruebe los cambios.

Para obtener más información sobre la configuración de usuarios, grupos de seguridad y permisos de la integración de WorkDay, consulte los pasos del 1 al 4 de la guía de [concesión de acceso a la integración o el extremo externo a WorkDay](https://go.microsoft.com/fwlink/?linkid=2103212) (accesible con las credenciales de la comunidad o la documentación de WorkDay).

## <a name="how-to-connect-workday-to-cloud-app-security-using-oauth"></a>Cómo conectar WorkDay a Cloud App Security mediante OAuth

1. Inicie sesión en WorkDay con una cuenta que sea miembro del grupo de seguridad mencionado en los requisitos previos.

1. Busque "Editar configuración de inquilino – sistema" y, en **registro de actividad de usuario** , seleccione **Habilitar registro de actividad de usuario**.

    ![Captura de pantalla para permitir el registro de actividad de usuario](media/connect-workday-enable-logging.png)

1. Busque "Editar configuración de inquilino – seguridad" y, en **configuración de oauth 2,0** , seleccione **clientes de OAuth 2,0 habilitados**.

1. Busque "registrar el cliente de API" y seleccione **registrar API Client – tarea**.

1. En la página **registrar el cliente de API** , rellene la información siguiente y, a continuación, haga clic en **Aceptar**.

    | Nombre del campo | Valor |
    | ---- | ---- |
    | Nombre de cliente | Microsoft Cloud App Security |
    | Tipo de concesión de cliente | Concesión de código de autorización |
    | Tipo de token de acceso | Portador |
    | URI de redireccionamiento | `https://portal.cloudappsecurity.com/api/oauth/connect`<br /><br />**Nota** : para clientes de la administración pública de Estados Unidos GCC, escriba el siguiente valor: `https://portal.cloudappsecurity.us/api/oauth/connect` |
    | Tokens de actualización que no son de expiración | Sí |
    | Ámbitos de OAuth2 | **Personal** y **sistema** |
    | Ámbito (áreas funcionales) | **Personal** y **sistema** |

    ![Captura de pantalla del registro del cliente de API](media/connect-workday-register-api-client.png)

1. Una vez registrado, tome nota de los siguientes parámetros y, a continuación, haga clic en **listo**.

    * Id. de cliente
    * Secreto del cliente
    * Punto de conexión de API de REST de WorkDay
    * Extremo de token
    * Extremo de autorización

    ![Captura de pantalla de la confirmación del registro del cliente de API](media/connect-workday-register-api-client-confirm.png)

1. <a name="add-connector"></a>En el portal de Cloud App Security, haga clic en **investigar** y, a continuación, en **aplicaciones conectadas**.

1. En la página **conectores de aplicaciones** , haga clic en el botón más y, a continuación, en **WorkDay**.

    ![Captura de pantalla de la adición del conector de aplicaciones](media/connect-workday-add-app.png)

1. En el elemento emergente, agregue el nombre de instancia y, a continuación, haga clic en **conectar WorkDay**.

    ![Captura de pantalla de la adición de nombre de instancia](media/connect-workday-add-app-connect.png)

1. En la página siguiente, rellene los detalles con la información anotada anteriormente y, a continuación, haga clic en **conectar en WorkDay**.

    ![Captura de pantalla del rellenado de detalles de la aplicación](media/connect-workday-add-app-connect-details.png)

1. En WorkDay, aparece una ventana emergente en la que se le pregunta si desea permitir el acceso Cloud App Security a su cuenta de WorkDay. Para continuar, haga clic en **Permitir**.

    ![Captura de pantalla sobre cómo autorizar el acceso a la aplicación](media/connect-workday-add-app-allow.png)

1. De vuelta en el portal de Cloud App Security, debería ver un mensaje que le indica que WorkDay se conectó correctamente. Haga clic en **Probar API** para confirmar que la conexión se ha realizado correctamente.

    La prueba puede tardar unos minutos. Cuando reciba la notificación de que se ha realizado correctamente, haga clic en **Cerrar**.

> [!NOTE]
> Después de conectar WorkDay, recibirá eventos durante siete días antes de la conexión.

Si tiene problemas para conectar la aplicación, consulte [solución de problemas de conectores de aplicaciones](troubleshooting-api-connectors-using-error-messages.md).

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Controlar las aplicaciones en la nube con directivas](control-cloud-apps-with-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]
