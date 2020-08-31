---
title: Conectar Google Cloud Platform a Cloud App Security
description: En este artículo se proporciona información sobre cómo conectar el Google Cloud Platform a Cloud App Security mediante el conector de API para la visibilidad y el control del uso.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 06/28/2020
ms.topic: how-to
ms.service: cloud-app-security
ms.collection: M365-security-compliance
ms.openlocfilehash: 60710c450515b6cf7cf355b3dc370798df24cbe8
ms.sourcegitcommit: c174a7ada5c6a14f0fea9870672898c54e5e3b52
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/30/2020
ms.locfileid: "89149897"
---
# <a name="connect-google-cloud-platform-to-microsoft-cloud-app-security"></a>Conectar Google Cloud Platform a Microsoft Cloud App Security

*Se aplica a: Microsoft Cloud App Security*

En este artículo se proporcionan instrucciones para conectar Microsoft Cloud App Security a su cuenta de Google Cloud Platform (GCP) existente mediante las API del conector. Esta conexión le proporciona visibilidad y control sobre el uso de GCP. Para obtener información sobre cómo Cloud App Security protege GCP, consulte [protección](protect-gcp.md)de GCP.

Se recomienda usar un proyecto dedicado para la integración y restringir el acceso al proyecto para mantener la integración estable y evitar las eliminaciones o modificaciones del proceso de instalación. Además, si la instancia de GCP es parte de una instancia de G Suite que ya está conectada a Cloud App Security, se recomienda seguir el **para una instancia de GCP que forme parte de los pasos de una organización de g Suite conectada** al agregar los detalles de conexión de GCP.

## <a name="prerequisites"></a>Requisitos previos

El usuario que integra GCP debe tener los permisos siguientes:

- **IAM y edición de administración** : nivel de organización
- **Creación y edición de proyectos**

Puede conectar uno o ambos de los siguientes GCP a Cloud App Security conexiones:

- **Auditoría de seguridad**: esta conexión le proporciona visibilidad y control sobre el uso de aplicaciones de GCP.
- **Configuración de seguridad**: esta conexión ofrece recomendaciones de seguridad fundamentales basadas en el criterio de referencia del centro de seguridad de Internet (CIS) para GCP.

Dado que puede Agregar una o ambas conexiones, los pasos de este artículo se escriben como instrucciones independientes. Si ya ha agregado una de las conexiones, si procede, edite las configuraciones existentes.

## <a name="how-to-connect-gcp-security-auditing-to-cloud-app-security"></a>Cómo conectar la auditoría de seguridad de GCP a Cloud App Security

La conexión de la auditoría de seguridad GCP proporciona visibilidad y control sobre el uso de la aplicación de GCP.

Siga estos pasos para conectar la auditoría de seguridad de GCP a Cloud App Security.

> [!div class="checklist"]
>
> - [Configurar Google Cloud Platform](#configure-google-cloud-platform)
> - [Conectar Google Cloud Platform auditoría a Cloud App Security](#connect-google-cloud-platform-auditing-to-cloud-app-security)
> - [Receptor de exportación agregado](#aggregated-export-sink)

### <a name="configure-google-cloud-platform"></a>Configurar Google Cloud Platform

> [!NOTE]
> Las instrucciones para conectar el entorno de GCP para la auditoría siguen las [recomendaciones de Google](https://cloud.google.com/blog/products/gcp/best-practices-for-working-with-google-cloud-audit-logging) para consumir registros agregados. La integración utiliza Google StackDriver y consumirá recursos adicionales que podrían afectar a la facturación. Los recursos consumidos son:
>
> - [Receptor de exportación agregado: nivel de organización](https://cloud.google.com/logging/docs/export/aggregated_exports#concept)
> - [Tema pub/sub: nivel de proyecto GCP](https://cloud.google.com/logging/docs/export/using_exported_logs#pubsub-overview)
> - [Suscripción pub/sub: nivel de proyecto de GCP](https://cloud.google.com/logging/docs/export/using_exported_logs#pubsub-overview)
>
> La conexión de auditoría de Cloud App Security solo importa los registros de auditoría de la actividad de administración; No se importan los registros de auditoría de eventos del sistema y de acceso a datos. Para obtener más información sobre los registros de GCP, consulte [registros de auditoría en la nube](https://go.microsoft.com/fwlink/?linkid=2109230).

#### <a name="create-a-dedicated-project"></a>Crear un proyecto dedicado

Cree un proyecto dedicado en GCP en su organización para habilitar la estabilidad y el aislamiento de la integración

1. Inicie sesión en el portal de GCP mediante su cuenta de usuario de integración de GCP.
1. Haga clic en **crear proyecto** para iniciar un nuevo.
1. En la pantalla **nuevo proyecto** , asigne un nombre al proyecto y haga clic en **crear**.

    ![Captura de pantalla que muestra el cuadro de diálogo crear proyecto de GCP](media/connect-gcp-create-project.png)

#### <a name="enable-required-apis"></a>Habilitación de las API necesarias

1. Cambie al proyecto dedicado.
1. Vaya a la pestaña **biblioteca** .
1. Busque y seleccione **API de registro**en la nube y, a continuación, en la página API, haga clic en **Habilitar**.
1. Busque y seleccione **API pub/sub**en la nube y, a continuación, en la página API, haga clic en **Habilitar**.

    > [!NOTE]
    > Asegúrese de que no selecciona la **API pub/sub Lite**.

#### <a name="create-a-dedicated-service-account-for-the-security-auditing-integration"></a>Crear una cuenta de servicio dedicada para la integración de auditoría de seguridad

1. En **IAM & admin**, haga clic en **cuentas de servicio**.
1. Haga clic en **crear cuenta de servicio** para crear una cuenta de servicio dedicada.
1. Escriba un nombre de cuenta y, a continuación, haga clic en **crear**.
1. Especifique el **rol** como **Administrador de pub/sub** y, a continuación, haga clic en **Guardar**.

    ![Captura de pantalla que muestra GCP agregar rol IAM](media/connect-gcp-iam-role.PNG)

1. Copie el valor de **correo electrónico** , lo necesitará más adelante.

    ![Captura de pantalla que muestra el cuadro de diálogo cuenta de servicio GCP](media/connect-gcp-create-service-account.png)

1. En **iam & admin**, haga clic en **IAM**.

    1. Cambie al nivel de organización.
    1. Haga clic en **AGREGAR**.
    1. En el cuadro **nuevos miembros** , pegue el valor de **correo electrónico** que copió anteriormente.
    1. Especifique el **rol** como **escritor de configuración de registros** y, a continuación, haga clic en **Guardar**.

        ![Captura de pantalla que muestra el cuadro de diálogo Agregar miembro](media/connect-gcp-add-member.png)

#### <a name="create-a-private-key-for-the-dedicated-service-account"></a>Crear una clave privada para la cuenta de servicio dedicada

1. Cambiar a nivel de proyecto.
1. En **IAM & admin**, haga clic en **cuentas de servicio**.
1. Abra la cuenta de servicio dedicada y haga clic en **Editar**.
1. Haga clic en **crear clave**.
1. En la pantalla **crear clave privada** , seleccione **JSON**y, a continuación, haga clic en **crear**.

    ![Captura de pantalla que muestra el cuadro de diálogo crear clave privada](media/connect-gcp-create-private-key.png)

    > [!NOTE]
    > Necesitará el archivo JSON que se descarga en el equipo más adelante.

#### <a name="retrieve-your-organization-id"></a>Recuperar el identificador de la organización

Tome nota del identificador de la **organización**, lo necesitará más adelante. Para obtener más información, consulte [obtención del identificador de la organización](https://cloud.google.com/resource-manager/docs/creating-managing-organization#retrieving_your_organization_id).

![Captura de pantalla que muestra el cuadro de diálogo identificador de organización](media/connect-gcp-org-id.png)

### <a name="connect-google-cloud-platform-auditing-to-cloud-app-security"></a>Conectar Google Cloud Platform auditoría a Cloud App Security

#### <a name="add-the-gcp-connection-details"></a>Agregar los detalles de la conexión GCP

1. En el portal de Cloud App Security, haga clic en **Investigar** y, después, en **Aplicaciones conectadas**.

1. En la página **conectores de aplicaciones** , para proporcionar las credenciales del conector de AWS, realice una de las acciones siguientes:

    > [!NOTE]
    > Se recomienda conectar la instancia de G Suite para obtener administración unificada de usuarios y gobernanza. Este es el recomendado incluso si no usa ningún producto G Suite y los usuarios de GCP se administran a través del sistema de administración de usuarios de G Suite.

    **Para un nuevo conector**

    1. Haga clic en el signo más seguido de **Google Cloud Platform**.

        ![conectar GCP](media/connect-gcp-add.png)

    1. En el elemento emergente, proporcione un nombre para el conector y, a continuación, haga clic en **conectar Google Cloud Platform**.

        ![Nombre del conector de GCP](media/connect-gcp-name.png)

    1. En la página **detalles del proyecto** , realice lo siguiente y, a continuación, haga clic en **conectar Google Cloud Platform**.
        1. En el cuadro ID. de la **organización** , escriba la organización que anotó anteriormente.
        1. En el cuadro **archivo de clave privada** , busque el archivo JSON que descargó anteriormente.

        ![Conectar la auditoría de seguridad de aplicaciones GCP para el nuevo conector](media/connect-gcp-app-audit.png)

    **Para un conector existente**

    1. En la lista de conectores, en la fila en la que aparece el conector de AWS, haga clic en **conectar auditoría de seguridad**.

        ![Captura de pantalla de la página aplicaciones conectadas, donde se muestra el vínculo editar auditoría de seguridad](media/connect-gcp-app-edit-audit.png)

    1. En la página **detalles del proyecto** , realice lo siguiente y, a continuación, haga clic en **conectar Google Cloud Platform**.
        1. En el cuadro ID. de la **organización** , escriba la organización que anotó anteriormente.
        1. En el cuadro **archivo de clave privada** , busque el archivo JSON que descargó anteriormente.

        ![Conectar la auditoría de seguridad de aplicaciones GCP para el conector existente](media/connect-gcp-app-edit-audit-creds.png)

1. Haga clic en **probar API** para asegurarse de que la conexión se ha realizado correctamente.

    La prueba puede tardar unos minutos. Cuando haya terminado, recibirá una notificación de éxito o de error. Cuando reciba la notificación de que se ha realizado correctamente, haga clic en **Listo**.

Si tiene problemas para conectar la aplicación, consulte [solución de problemas de conectores de aplicaciones](troubleshooting-api-connectors-using-error-messages.md).

### <a name="aggregated-export-sink"></a>Receptor de exportación agregado

La deshabilitación del receptor de exportación agregado solo es posible a través de Google Cloud Shell.

#### <a name="to-disable-aggregated-export-sink"></a>Para deshabilitar el receptor de exportación agregado

| Paso | Script | Para obtener más información |
|-|-|-|
| 1. Inicie una sesión de Google Cloud Shell. | | [Usar Cloud Shell](https://cloud.google.com/shell/docs/using-cloud-shell) |
| 2. establezca el proyecto actual. | `gcloud config set project {PROJECT_ID}` | [conjunto de configuración de gcloud](https://cloud.google.com/sdk/gcloud/reference/config/set) |
| 3. Enumere los receptores en el nivel de la organización. | `gcloud logging sinks list --organization={ORGANIZATION_ID}` | [gcloud lista de receptores de registro](https://cloud.google.com/sdk/gcloud/reference/logging/sinks/list) |
| 4. Elimine el receptor pertinente. | `gcloud logging sinks delete {SINK_NAME} --organization={ORGANIZATION_ID}` | [gcloud eliminación de receptores de registro](https://cloud.google.com/sdk/gcloud/reference/logging/sinks/delete) |

## <a name="how-to-connect-gcp-security-configuration-to-cloud-app-security"></a>Cómo conectar la configuración de seguridad de GCP a Cloud App Security

La conexión de la configuración de seguridad GCP ofrece información sobre las recomendaciones de seguridad fundamentales basadas en la prueba comparativa de Center for Internet Security (CIS) para GCP.

Siga estos pasos para conectar la configuración de seguridad de GCP a Cloud App Security.

> [!div class="checklist"]
>
> - [Configuración del centro de comandos de seguridad GCP con el análisis de estado de seguridad](#set-up-gcp-security-command-center-with-security-health-analytics)
> - [Habilitar API del centro de comandos de seguridad](#enable-security-command-center-api)
> - [Crear una cuenta de servicio dedicada para la integración de la configuración de seguridad](#create-a-dedicated-service-account-for-the-security-configuration-integration)
> - [Conecte Google Cloud Platform configuración de seguridad a Cloud App Security](#connect-google-cloud-platform-security-configuration-to-cloud-app-security)

### <a name="set-up-gcp-security-command-center-with-security-health-analytics"></a>Configuración del centro de comandos de seguridad GCP con el análisis de estado de seguridad

1. Configurar el [centro de comandos de seguridad](https://cloud.google.com/security-command-center/docs/quickstart-security-command-center).
1. [Habilite el análisis de estado de seguridad de GCP](https://cloud.google.com/security-command-center/docs/how-to-use-security-health-analytics).
1. Compruebe que hay datos que fluyen al centro de comandos de seguridad.

    > [!NOTE]
    >
    > - Las instrucciones para conectar el entorno GCP para la configuración de seguridad siguen las [recomendaciones de Google](https://cloud.google.com/security-command-center/docs/how-to-notifications#enable-scc-api) para consumir recomendaciones de configuración de seguridad. La integración aprovecha el centro de comandos de seguridad de Google y consumirá recursos adicionales que podrían afectar a la facturación.
    > - La primera vez que se habilita el análisis de estado de seguridad, los datos pueden tardar varias horas en estar disponibles.

### <a name="enable-security-command-center-api"></a>Habilitar API del centro de comandos de seguridad

1. En la biblioteca Cloud Console API, seleccione el proyecto al que desea conectarse Cloud App Security.
1. En la biblioteca de API, busque y seleccione la "API del centro de comandos de seguridad".
1. En la página API, haga clic en **Habilitar**.

### <a name="create-a-dedicated-service-account-for-the-security-configuration-integration"></a>Crear una cuenta de servicio dedicada para la integración de la configuración de seguridad

1. En centro de comandos de seguridad GCP, seleccione el proyecto al que desea conectarse Cloud App Security.
1. En **IAM & admin**, haga clic en **cuentas de servicio**.
1. Haga clic en **crear cuenta de servicio** para crear una cuenta de servicio dedicada.
1. Escriba un nombre de cuenta y, a continuación, haga clic en **crear**.
1. Especifique el **rol** como **Security Center visor de administración** y, a continuación, haga clic en **Guardar**.

    ![Captura de pantalla que muestra el elemento de menú Agregar GCP para Security Center visor de administración](media/connect-gcp-security-configuration-1.png)

1. Copie el valor de **correo electrónico** , lo necesitará más adelante.

    ![Captura de pantalla que muestra la cuenta de servicio de copia de GCP](media/connect-gcp-security-configuration-2.png)

1. En **iam & admin**, haga clic en **IAM**.

    1. Cambie al nivel de organización.
    1. Haga clic en **AGREGAR**.
    1. En el cuadro **nuevos miembros** , pegue el valor de **correo electrónico** que copió anteriormente.
    1. Especifique el **rol** como **Security Center visor de administración** y, a continuación, haga clic en **Guardar**.

        ![Captura de pantalla que muestra el cuadro de diálogo Agregar miembro al proyecto](media/connect-gcp-security-configuration-3.png)

#### <a name="create-a-private-key-for-the-dedicated-service-account"></a>Crear una clave privada para la cuenta de servicio dedicada

1. Cambiar a nivel de proyecto.
1. En **IAM & admin**, haga clic en **cuentas de servicio**.
1. Abra la cuenta de servicio dedicada y haga clic en **Editar**.
1. Haga clic en **crear clave**.
1. En la pantalla **crear clave privada** , seleccione **JSON**y, a continuación, haga clic en **crear**.

    ![Captura de pantalla que muestra el cuadro de diálogo crear clave privada para una cuenta de servicio dedicada](media/connect-gcp-security-configuration-4.png)

    > [!NOTE]
    > Necesitará el archivo JSON que se descarga en el equipo más adelante.

#### <a name="retrieve-your-organization-id"></a>Recuperar el identificador de la organización

Tome nota del identificador de la **organización**, lo necesitará más adelante. Para obtener más información, consulte [obtención del identificador de la organización](https://cloud.google.com/resource-manager/docs/creating-managing-organization#retrieving_your_organization_id).
    ![Captura de pantalla que muestra el cuadro de diálogo identificador de organización](media/connect-gcp-org-id.png)

### <a name="connect-google-cloud-platform-security-configuration-to-cloud-app-security"></a>Conecte Google Cloud Platform configuración de seguridad a Cloud App Security

1. En Cloud App Security, haga clic en **investigar**y, a continuación, seleccione **aplicaciones conectadas**.

1. En la pestaña **aplicaciones de configuración de seguridad** , haga clic en el botón más y, a continuación, seleccione **Google Cloud Platform**.

    ![Captura de pantalla que muestra la opción de menú Agregar GCP](media/connect-gcp-security-configuration-5.png)

1. En la página **nombre de instancia** , elija el tipo de instancia y, a continuación, haga clic en **siguiente**.

    - Para un conector existente, elija la instancia pertinente.

        ![Selección de instancia de GCP](media/connect-gcp-existing-instance.png)

    - Para un nuevo conector, proporcione un nombre para la instancia.

        ![Nuevo nombre de conector de GCP](media/connect-gcp-new-instance.png)

1. En la página **detalles del proyecto** , realice lo siguiente y, a continuación, haga clic en **siguiente**.
    1. En el cuadro ID. de la **organización** , escriba la organización que anotó anteriormente.
    1. En el cuadro **archivo de clave privada** , busque el archivo JSON que descargó anteriormente.

    ![Agregar detalles del proyecto GCP](media/connect-gcp-security-configuration-6.png)

1. En la página **finalizado** , asegúrese de que la conexión se ha realizado correctamente y, a continuación, haga clic en **finalizado**.

Si tiene problemas para conectar la aplicación, consulte [solución de problemas de conectores de aplicaciones](troubleshooting-api-connectors-using-error-messages.md).

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Controlar las aplicaciones en la nube con directivas](control-cloud-apps-with-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]
