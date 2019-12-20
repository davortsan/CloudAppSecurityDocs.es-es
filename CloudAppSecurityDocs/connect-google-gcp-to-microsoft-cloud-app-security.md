---
title: Conectar Google Cloud Platform a Cloud App Security
description: En este artículo se proporciona información sobre cómo conectar el Google Cloud Platform a Cloud App Security mediante el conector de API para la visibilidad y el control del uso.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 10/16/2019
ms.topic: conceptual
ms.service: cloud-app-security
ms.collection: M365-security-compliance
ms.openlocfilehash: e03f24023968d9e3169aef8636061b8adf05d646
ms.sourcegitcommit: db5ec79d219dd6674939c872ace7cd2ca80860a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/19/2019
ms.locfileid: "75189747"
---
# <a name="connect-google-cloud-platform-to-microsoft-cloud-app-security-preview"></a>Conectar Google Cloud Platform a Microsoft Cloud App Security (versión preliminar)

*Se aplica a: Microsoft Cloud App Security*

En este artículo se proporcionan instrucciones para conectar Microsoft Cloud App Security a su cuenta de Google Cloud Platform (GCP) existente mediante las API del conector. Esta conexión le proporciona visibilidad y control sobre el uso de GCP. Para obtener información sobre cómo Cloud App Security protege GCP, consulte [protección](protect-gcp.md)de GCP.

> [!NOTE]
> Las instrucciones para conectar el entorno de GCP siguen las [recomendaciones de Google](https://cloud.google.com/blog/products/gcp/best-practices-for-working-with-google-cloud-audit-logging) para consumir registros agregados. La integración utiliza Google StackDriver y consumirá recursos adicionales que podrían afectar a la facturación. Los recursos consumidos son:
>
> * [Receptor de exportación agregado: nivel de organización](https://cloud.google.com/logging/docs/export/aggregated_exports#concept)
> * [Tema pub/sub: nivel de proyecto GCP](https://cloud.google.com/logging/docs/export/using_exported_logs#pubsub-overview)
> * [Suscripción pub/sub: nivel de proyecto de GCP](https://cloud.google.com/logging/docs/export/using_exported_logs#pubsub-overview)
>
> Actualmente, Cloud App Security solo importa los registros de auditoría de la actividad de administración; No se importan los registros de auditoría de eventos del sistema y de acceso a datos. Para obtener más información sobre los registros de GCP, consulte [registros de auditoría en la nube](https://go.microsoft.com/fwlink/?linkid=2109230).

Se recomienda usar un proyecto dedicado para la integración y restringir el acceso al proyecto para mantener la integración estable y evitar las eliminaciones o modificaciones del proceso de instalación. Además, si la instancia de GCP es parte de una instancia de G Suite que ya está conectada a Cloud App Security, se recomienda seguir el **para una instancia de GCP que forme parte de los pasos de una organización de g Suite conectada** al agregar los detalles de conexión de GCP.

## <a name="prerequisites"></a>Requisitos previos

El usuario que integra GCP debe tener los permisos siguientes:

* **IAM y edición de administración** : nivel de organización
* **Creación y edición de proyectos**

## <a name="configure-google-cloud-platform"></a>Configurar Google Cloud Platform

* Inicie sesión en el portal de GCP mediante su cuenta de usuario de integración de GCP.

### <a name="create-a-dedicated-project"></a>Crear un proyecto dedicado

Cree un proyecto dedicado en GCP en su organización para habilitar la estabilidad y el aislamiento de la integración

1. Haga clic en **crear proyecto** para iniciar un nuevo.
1. En la pantalla **nuevo proyecto** , asigne un nombre al proyecto y haga clic en **crear**.

    ![Captura de pantalla que muestra el cuadro de diálogo crear proyecto de GCP](media/connect-gcp-create-project.png)

### <a name="enable-the-pubsub-api"></a>Habilitación de la API pub/sub

1. Cambie al proyecto dedicado.
1. Vaya a la pestaña pub/sub. Debería aparecer un mensaje de activación de servicio.

### <a name="create-a-dedicated-service-account-for-the-integration"></a>Crear una cuenta de servicio dedicada para la integración

1. En **IAM & admin**, haga clic en **cuentas de servicio**.
1. Haga clic en **crear cuenta de servicio** para crear una cuenta de servicio dedicada.
1. Escriba un nombre de cuenta y, a continuación, haga clic en **crear**.
1. Especifique el **rol** como **Administrador de pub/sub** y, a continuación, haga clic en **Guardar**.

    ![Captura de pantalla que muestra GCP agregar rol IAM](media/connect-gcp-iam-role.PNG)

1. Copie el valor de **correo electrónico** , lo necesitará más adelante.

    ![Captura de pantalla que muestra el cuadro de diálogo cuenta de servicio GCP](media/connect-gcp-create-service-account.png)

1. En **iam & admin**, haga clic en **IAM**.

    1. Cambie al nivel de organización.
    1. Haga clic en **Agregar**.
    1. En el cuadro **nuevos miembros** , pegue el valor de **correo electrónico** que copió anteriormente.
    1. Especifique el **rol** como **escritor de configuración de registros** y, a continuación, haga clic en **Guardar**.

        ![Captura de pantalla que muestra el cuadro de diálogo Agregar miembro](media/connect-gcp-add-member.png)

### <a name="create-a-private-key-for-the-dedicated-service-account"></a>Crear una clave privada para la cuenta de servicio dedicada

1. Cambiar a nivel de proyecto.
1. En **IAM & admin**, haga clic en **cuentas de servicio**.
1. Abra la cuenta de servicio dedicada y haga clic en **Editar**.
1. Haga clic en **crear clave**.
1. En la pantalla **crear clave privada** , seleccione **JSON**y, a continuación, haga clic en **crear**.

    ![Captura de pantalla que muestra el cuadro de diálogo crear clave privada](media/connect-gcp-create-private-key.png)

    > [!NOTE]
    > Necesitará el archivo JSON que se descarga en el equipo más adelante.

### <a name="retrieve-your-organization-id"></a>Recuperar el identificador de la organización

Tome nota del identificador de la **organización**, lo necesitará más adelante. Para obtener más información, consulte [obtención del identificador de la organización](https://cloud.google.com/resource-manager/docs/creating-managing-organization#retrieving_your_organization_id).
    ![captura de pantalla que muestra el cuadro de diálogo ID. de organización](media/connect-gcp-org-id.png)

## <a name="configure-cloud-app-security"></a>Configurar Cloud App Security

* En el portal de Cloud App Security, haga clic en **Investigar** y, después, en **Aplicaciones conectadas**.

### <a name="add-the-gcp-connection-details"></a>Agregar los detalles de la conexión GCP

Para proporcionar los detalles de la conexión GCP, en **conectores de aplicaciones**, realice una de las acciones siguientes:

**Para una instancia de GCP que no forma parte de una organización conectada de G Suite**

1. Haga clic en el signo más seguido de **Google Cloud Platform**.

    ![Captura de pantalla que muestra el menú Agregar GCP](media/connect-gcp-add.png)

1. En el elemento emergente, proporcione un nombre para el conector y, a continuación, haga clic en **conectar Google Cloud Platform**.

1. En la Página Google Cloud Platform, haga lo siguiente:
    1. En el cuadro ID. de la **organización** , escriba la organización que anotó anteriormente.
    1. En el cuadro **archivo de clave privada** , busque el archivo JSON que descargó anteriormente.
    1. Haga clic en **conectar Google Cloud Platform**.

    > [!NOTE]
    > Se recomienda conectar la instancia de G Suite para obtener administración unificada de usuarios y gobernanza. Este es el recomendado incluso si no usa ningún producto G Suite y los usuarios de GCP se administran a través del sistema de administración de usuarios de G Suite.

**Para una instancia de GCP que forme parte de una organización conectada de G Suite**

1. En la lista de instancias conectadas, al final de la fila en la que aparece el conector G Suite, haga clic en los tres puntos y, a continuación, haga clic en **agregar Google Cloud Platform**.

1. En la Página Google Cloud Platform, haga lo siguiente:
    1. En el cuadro ID. de la **organización** , escriba la organización que anotó anteriormente.
    1. En el cuadro **archivo de clave privada** , busque el archivo JSON que descargó anteriormente.
    1. Haga clic en **conectar Google Cloud Platform**.

    > [!NOTE]
    > Esto permite la administración y el gobierno de usuarios unificados a través del dominio de identidad de usuario de G Suite.

### <a name="test-the-connection"></a>Prueba de la conexión

Haga clic en **Probar API** para asegurarse de que la conexión se ha realizado correctamente.

La prueba puede tardar unos minutos. Cuando haya finalizado, recibirá una notificación que le indicará si se ha realizado correcta o incorrectamente. Cuando reciba la notificación de que se ha realizado correctamente, haga clic en **Listo**.

## <a name="aggregated-export-sink"></a>Receptor de exportación agregado

La deshabilitación del receptor de exportación agregado solo es posible a través de Google Cloud Shell.

### <a name="to-disable-aggregated-export-sink"></a>Para deshabilitar el receptor de exportación agregado

| Paso | Script | Para obtener más información |
|-|-|-|
| 1. Inicie una sesión de Google Cloud Shell. | | [Usar Cloud Shell](https://cloud.google.com/shell/docs/using-cloud-shell) |
| 2. establezca el proyecto actual. | `gcloud config set project {PROJECT_ID}` | [conjunto de configuración de gcloud](https://cloud.google.com/sdk/gcloud/reference/config/set) |
| 3. Enumere los receptores en el nivel de la organización. | `gcloud logging sinks list --organization={ORGANIZATION_ID}` | [gcloud lista de receptores de registro](https://cloud.google.com/sdk/gcloud/reference/logging/sinks/list) |
| 4. Elimine el receptor pertinente. | `gcloud logging sinks delete {SINK_NAME} --organization={ORGANIZATION_ID}` | [gcloud eliminación de receptores de registro](https://cloud.google.com/sdk/gcloud/reference/logging/sinks/delete) |

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Controlar las aplicaciones en la nube con directivas](control-cloud-apps-with-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]
