---
title: Conectar el área de trabajo de Google a Cloud App Security
description: En este artículo se proporciona información sobre cómo conectar el área de trabajo de Google a Cloud App Security mediante el conector de API para la visibilidad y el control del uso.
ms.date: 11/27/2019
ms.topic: how-to
ms.openlocfilehash: 0d9d99d650ab0d68f8bd6dd129f6b01c78fb2cc5
ms.sourcegitcommit: 16a65ab2c8ca778d0b3cfa97b847af4c812363b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/03/2021
ms.locfileid: "97855598"
---
# <a name="connect-google-workspace-to-microsoft-cloud-app-security"></a>Conectar el área de trabajo de Google a Microsoft Cloud App Security

[!INCLUDE [Banner for top of topics](includes/banner.md)]

En este artículo se proporcionan instrucciones para conectar Microsoft Cloud App Security a su cuenta de Google Workspace existente mediante las API del conector. Esta conexión le proporciona visibilidad y control sobre el uso del área de trabajo de Google. Para obtener información sobre cómo Cloud App Security protege Google Workspace, consulte [proteger el área de trabajo de Google](protect-google-workspace.md).

## <a name="configure-google-workspace"></a>Configuración del área de trabajo de Google

1. Como súper administrador del área de trabajo de Google, inicie sesión en <a href="https://cloud.google.com/console/project" target="_blank">https://cloud.google.com/console/project</a> .

1. Haga clic en **Crear un proyecto** para iniciar un nuevo proyecto.

    ![Crear proyecto de Google](media/connect-google-workspace/google-workspace-create-new-project.png)

1. En la página **nuevo proyecto** , asigne al proyecto el nombre siguiente: **Cloud App Security** y haga clic en **crear**.

    ![Menú emergente de Google New Project](media/connect-google-workspace/google-workspace-create-new-project-popup.png)

1. Una vez creado el proyecto, en la barra de herramientas, haga clic en **Google Cloud Platform**. Asegúrese de que el proyecto correcto está seleccionado en la lista desplegable en la parte superior.

    ![Haga clic en Google Cloud Platform en la barra de herramientas](media/connect-google-workspace/google-workspace-verify-project.png)

1. Seleccione el menú, vaya a **API &**  >  **biblioteca Library** y habilite las siguientes API (use la línea de búsqueda si la API no aparece):

    - API del SDK de administración

    - Audit API
    - API de Google Drive
    - SDK de Marketplace de Google Workspace

    > [!NOTE]
    > Para cada API, haga clic en **Habilitar** para activarla.
    >
    > ![habilitación de Google APPI](media/connect-google-workspace/google-workspace-api.png)
    >
    > Omita por ahora la advertencia sobre **credenciales**.

1. Seleccione menú, vaya a **API &**  >  **Panel** de servicios y asegúrese de que tiene habilitadas las siguientes API:

    - API del SDK de administración

    - Audit API
    - API de Google Drive
    - SDK de Marketplace de Google Workspace

1. En la página de la **Página de consentimiento de OAuth** , haga lo siguiente:
    1. En **tipo de usuario**, seleccione **externo** y, a continuación, haga clic en **crear**.

        ![Tipo de usuario de consentimiento de Google OAuth](media/connect-google-workspace/google-workspace-oauth-consent-user-type.png)

    1. Rellene la siguiente información y, a continuación, haga clic en **Guardar**.

        | Nombre del campo | Valor |
        | --- | --- |
        | Tipo de aplicación | Público |
        | Nombre de la aplicación | Microsoft Cloud App Security |
        | Correo electrónico de soporte técnico | `<your_email_address>` |

        El resto de campos es opcional.

        ![Tipo de aplicación de consentimiento de OAuth de Google](media/connect-google-workspace/google-workspace-oauth-consent-app-type.png)

1. En la página **credenciales** , haga lo siguiente:
    1. Seleccione **crear credenciales** y, a continuación, seleccione **cuenta de servicio**.
    1. En **detalles** de la cuenta de servicio, proporcione un nombre y una descripción y, a continuación, haga clic en **crear**.
    1. En **conceder a esta cuenta de servicio acceso a proyecto**, en **rol** , seleccione **proyecto**, seleccione **Editor** y, a continuación, haga clic en **listo**.

    ![Cuenta de servicio de creación de Google](media/connect-google-workspace/google-workspace-create-service-account.png)

1. En la página **cuenta de servicio** , haga lo siguiente:
    1. En **cuentas de servicio**, busque y edite la cuenta de servicio que creó anteriormente.

        ![Cuenta de servicio de edición de Google](media/connect-google-workspace/google-workspace-edit-service-account.png)

    1. Realice una copia de la dirección de correo electrónico. Lo necesitará más adelante.
    1. En **claves**, en el menú **Agregar clave** , seleccione **crear nueva clave**, seleccione **P12** y, a continuación, haga clic en **crear**. Guarde el archivo que se ha descargado, lo necesitará más adelante.
    1. En **Estado** de la cuenta de servicio, seleccione **Habilitar delegación de todo el dominio de G Suite** y, a continuación, haga clic en **Guardar**.

    ![Cuenta de servicio de actualización de Google](media/connect-google-workspace/google-workspace-update-service-account.png)

1. En la página **credenciales** , en ID. de **cliente de OAuth 2,0**, copie el **identificador de cliente** asignado a su cuenta de servicio; lo necesitará más adelante.

    ![Cuenta de servicio de credenciales del área de trabajo de Google](media/connect-google-workspace/google-workspace-copy-service-account-client-id.png)

1. Vaya a [admin.Google.com](https://admin.google.com/) y navegue hasta controles de la API de **seguridad**  >    >  **administrar delegación en todo el dominio**, haga clic en **Agregar nuevo** y realice lo siguiente:

    1. En el cuadro ID. de **cliente** , escriba el **identificador de cliente** que copió anteriormente.
    1. En el cuadro **ámbitos de OAuth** , escriba la siguiente lista de ámbitos necesarios (Copie el texto y péguelo en el cuadro):  
    `https://www.googleapis.com/auth/admin.reports.audit.readonly,https://www.googleapis.com/auth/admin.reports.usage.readonly,https://www.googleapis.com/auth/drive,https://www.googleapis.com/auth/drive.appdata,https://www.googleapis.com/auth/drive.apps.readonly,https://www.googleapis.com/auth/drive.file,https://www.googleapis.com/auth/drive.metadata.readonly,https://www.googleapis.com/auth/drive.readonly,https://www.googleapis.com/auth/drive.scripts,https://www.googleapis.com/auth/admin.directory.user.readonly,https://www.googleapis.com/auth/admin.directory.user.security,https://www.googleapis.com/auth/admin.directory.user.alias,https://www.googleapis.com/auth/admin.directory.orgunit,https://www.googleapis.com/auth/admin.directory.notifications,https://www.googleapis.com/auth/admin.directory.group.member,https://www.googleapis.com/auth/admin.directory.group,https://www.googleapis.com/auth/admin.directory.device.mobile.action,https://www.googleapis.com/auth/admin.directory.device.mobile,https://www.googleapis.com/auth/admin.directory.user`

    1. Haga clic en **autorizar**.

    ![Agregar nuevo ID. de cliente del área de trabajo de Google](media/connect-google-workspace/google-workspace-add-new-client-id.png)

## <a name="configure-cloud-app-security"></a>Configurar Cloud App Security

1. En el portal de Cloud App Security, haga clic en **Investigar** y, después, en **Aplicaciones conectadas**.

1. Para proporcionar los detalles de conexión del área de trabajo de Google, en **conectores de aplicaciones**, realice una de las acciones siguientes:

    **Para una organización del área de trabajo de Google que ya tiene una instancia conectada de GCP**

    - En la lista de conectores, al final de la fila en la que aparece la instancia de GCP, haga clic en los tres puntos y, a continuación, haga clic en **Agregar área de trabajo de Google**.

    **Para una organización de área de trabajo de Google que aún no tiene una instancia conectada de GCP**

    - En la página **aplicaciones conectadas** , haga clic en el signo más ( **+** ) y seleccione el **área de trabajo de Google**.

1. En el elemento emergente, proporcione la información siguiente:

    ![Configuración del área de trabajo de Google en Cloud App Security](media/connect-google-workspace/cas-config-google-workspace.png "Configuración del área de trabajo de Google en Cloud App Security")

    1. Escriba el **identificador** de la cuenta de servicio, el **correo electrónico** que copió anteriormente.

    1. Escriba el **número de proyecto (ID. de aplicación)** que copió anteriormente.

    1. Cargue el archivo de **certificado** P12 que guardó anteriormente.

    1. Escriba el **correo electrónico** de la cuenta de administrador del administrador del área de trabajo de Google.

    1. Si tiene una cuenta de empresa o empresarial de Google Workspace, Active esta casilla. Para obtener información sobre qué características están disponibles en Cloud App Security para el negocio o la empresa de Google Workspace, consulte [habilitación de la visibilidad, la protección y las acciones de gobierno instantáneas para las aplicaciones](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md).

    1. Haga clic en **Save settings** (Guardar configuración).

    1. **Siga el vínculo** para conectarse al área de trabajo de Google. Se abrirá el área de trabajo de Google y se le pedirá que autorice el acceso para Cloud App Security.

    1. Haga clic en **Probar ahora** para confirmar que la conexión se ha realizado correctamente.  
    La prueba puede tardar unos minutos.  
    Después de recibir un aviso de éxito, haga clic en **listo** y cierre la página del área de trabajo de Google.

Después de conectar el área de trabajo de Google, recibirá eventos de 60 días antes de la conexión.

Después de conectar el área de trabajo de Google, Cloud App Security realiza un examen completo. En función del número de archivos y los usuarios que tenga, el examen podría tardar en completarse. Para habilitar el análisis casi en tiempo real, los archivos en los que se detecta actividad se mueven al principio de la cola de análisis. Por ejemplo, una archivo editado, actualizado o compartido se analiza inmediatamente. Esto no se aplica a los archivos que no se modifican de forma inherente. Por ejemplo, los archivos que se visualizan, previsualizan, imprimen o exportan se analizan durante un análisis normal.

Si tiene problemas para conectar la aplicación, consulte [solución de problemas de conectores de aplicaciones](troubleshooting-api-connectors-using-error-messages.md).

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Controlar las aplicaciones en la nube con directivas](control-cloud-apps-with-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]
