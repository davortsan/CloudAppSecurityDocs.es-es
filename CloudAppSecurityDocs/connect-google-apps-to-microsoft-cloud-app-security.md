---
title: Conexión de G Suite con Cloud App Security
description: En este artículo se proporciona información sobre cómo conectar G Suite con Cloud App Security mediante el conector de API para la visibilidad y el control del uso.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 6/17/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: b938e1e0-356d-4cc6-ba4a-862c0c59d709
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: c8381ef44b428994fca0ac4e71cef2deae8cf3c0
ms.sourcegitcommit: b592226ec8a07b4bc87720ea8611cd6edc8d7f8c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/04/2019
ms.locfileid: "73463648"
---
# <a name="connect-g-suite-to-microsoft-cloud-app-security"></a>Conectar G Suite con Microsoft Cloud App Security

*Se aplica a: Microsoft Cloud App Security*

En este artículo se ofrecen instrucciones para conectar Microsoft Cloud App Security con una cuenta de G Suite existente mediante las API del conector. Esta conexión le ofrece visibilidad y control del uso de G Suite.

## <a name="configure-g-suite"></a>Configurar G Suite

1. Como superadministrador de G Suite, inicie sesión en <a href="https://cloud.google.com/console/project" target="_blank">https://cloud.google.com/console/project</a>.

1. Haga clic en **Crear un proyecto** para iniciar un nuevo proyecto.

    ![google1](media/google1.png)

1. En la pantalla **Nuevo proyecto**, asigne al proyecto el nombre siguiente:  
**Cloud App Security** and click **Create**.
    ![google2](media/google2.png)

1. Una vez creado el proyecto, en la barra de herramientas, haga clic en **Google Cloud Platform**. Asegúrese de que el proyecto correcto está seleccionado en la lista desplegable en la parte superior.

    ![google project](media/googleverify-project.png)

1. Under **APIs**, click **Go to API's overview**.

    ![google3](media/google3.png)

1. Haga clic en **Biblioteca** y habilite estas API [use la línea de búsqueda si la API no figura en la lista **Popular APIs** (API populares)]:

    * Admin SDK

    * Audit API

    * API de Google Drive

    * SDK de G Suite Marketplace

    ![google apis](media/google4.png

    > [!NOTE]
    > Omita por ahora la advertencia sobre **credenciales**.

1. Haga clic en Habilitar para cada API.
    ![enable Google APPI](media/google-api.png)
1. Asegúrese de que las siguientes API están habilitadas:

    ![google enabled apis](media/google5.png)

1. Haga clic en **Credenciales** y, a continuación, seleccione la pestaña **OAuth consent screen** (Pantalla de consentimiento de OAuth).

    * En **Product name shown to users** (Nombre de producto mostrado a los usuarios), escriba **Microsoft Cloud App Security**.

    * El resto de campos es opcional.

    * Haga clic en **Guardar**.

    ![Google oauth consent](media/google-oauth-consent.png)

1. En la pestaña **Credenciales**, haga clic en la flecha situada junto a **Crear credenciales**.

    ![Google credentials](media/google7.png)

1. Seleccione **Service account key** (Clave de la cuenta del servicio).

    ![Google service account key](media/google8.png)

1. En **Crear clave de cuenta de servicio**, elija **Nueva cuenta de servicio** y escriba cualquier nombre (por ejemplo, **Cuenta de servicio 1**). En **Función**, elija **Project** (Proyecto) y después **Editor**. En **Tipo de clave**, elija **P12** y haga clic en **Crear**. Se guardará un archivo de certificado P12 en el equipo.

    ![Create service account key in Google](media/google9.png)

1. Copie el **identificador de la cuenta de servicio** asignado a su servicio, ya que lo necesitará más adelante.

1. En la pantalla **Credenciales**, haga clic en **Manage service accounts** (Administrar las cuentas de servicio) en el extremo derecho.

    ![credenciales de la cuenta de servicio de G Suite](media/google10.png "G Suite credentials service account")

1. Haga clic en los tres puntos a la derecha de la cuenta de servicio que ha creado y seleccione **Editar**.

    ![google edit](media/google11.png "google edit")

1. Click **VIEW DOMAIN WIDE DELEGATION CLIENT ID**.

    ![google client ID](media/google12.png "google12")

    * Copy the **Client ID** - you need it later.

    * Vaya a [admin.google.com](https://admin.google.com/) y haga clic en **Seguridad**.

    * Select **Show more** and then choose **Advanced settings**.

    * In the **Authentication** section, select **Manage API client access**.

    * In the **Client Name** box, enter the **Client ID** that you copied earlier.

    ![manage api client access](media/google12-2.png "google12-2")

    * In the **One or More API Scopes** box, enter the following list of required scopes (copy the text and paste it in the box):

            `https://www.googleapis.com/auth/admin.reports.audit.readonly,https://www.googleapis.com/auth/admin.reports.usage.readonly,https://www.googleapis.com/auth/drive,https://www.googleapis.com/auth/drive.appdata,https://www.googleapis.com/auth/drive.apps.readonly,https://www.googleapis.com/auth/drive.file,https://www.googleapis.com/auth/drive.metadata.readonly,https://www.googleapis.com/auth/drive.readonly,https://www.googleapis.com/auth/drive.scripts,https://www.googleapis.com/auth/admin.directory.user.readonly,https://www.googleapis.com/auth/admin.directory.user.security,https://www.googleapis.com/auth/admin.directory.user.alias,https://www.googleapis.com/auth/admin.directory.orgunit,https://www.googleapis.com/auth/admin.directory.notifications,https://www.googleapis.com/auth/admin.directory.group.member,https://www.googleapis.com/auth/admin.directory.group,https://www.googleapis.com/auth/admin.directory.device.mobile.action,https://www.googleapis.com/auth/admin.directory.device.mobile,https://www.googleapis.com/auth/admin.directory.user`

    * Click **Authorize**.

1. Abra el menú de Google; para ello, haga clic en las tres líneas horizontales junto a Google Cloud Platform en la barra de título. Haga clic en **Google Cloud Platform** y, a continuación, haga clic en la pestaña **APIs and services** (API y servicios) del menú izquierdo.

1. En el panel que se abre, desplácese a la lista de API habilitadas y haga clic en **API de Google Drive**.
    ![Select Google Drive](media/google14.png

1. Haga clic en la pestaña **Drive UI Integration** (Integración de la IU de la unidad) y complete la información siguiente:

    * **Nombre de la aplicación**: Microsoft Cloud App Security.

    * **Descripción breve y Descripción larga** (opcional): Microsoft Cloud App Security proporciona visibilidad de las aplicaciones en la nube, lo que sirve para controlar, investigar y gobernar el uso de esas aplicaciones en la nube, para proteger los datos corporativos y para detectar actividades sospechosas en cualquier aplicación en la nube.

    * Google requiere que se cargue al menos un icono de aplicación. Vaya a [https://go.microsoft.com/fwlink/?linkid=862826](https://go.microsoft.com/fwlink/?linkid=862826) para descargar un archivo ZIP que contiene los iconos de Cloud App Security. A continuación, debajo del **icono Aplicación**, haga clic en **Seleccionar**, junto a la imagen de 128 x 128, y arrastre el archivo a la ventana emergente. Haga clic en **Seleccionar**, junto a la imagen de 32 x 32, y arrastre el archivo a la ventana emergente.

    * Desplácese hacia abajo y, en la sección **Drive Integration** (Integración de unidades), escriba la siguiente dirección URL en **Abrir dirección URL:**  
    `https://portal.cloudappsecurity.com/#/services/11770?tab=files`

    ![Edit Google Drive](media/google15.png)

1. Haga clic en **Guardar cambios**.

1. Vuelva a la lista **Enabled APIs** (API habilitadas). Haga clic en **SDK de G Suite Marketplace**.

1. Seleccione la pestaña **Configuración**.

    * Copie el **Número de proyecto (id. de aplicación)** que aparece en la parte superior para usarlo más adelante.

    * En **Nombre de la aplicación**, escriba **Microsoft Cloud App Security**.

         En **Descripción de la aplicación**, escriba "Microsoft Cloud App Security proporciona visibilidad de las aplicaciones en la nube, lo que sirve para controlar, investigar y gobernar el uso de esas aplicaciones en la nube; para proteger los datos corporativos, y para detectar actividades sospechosas en cualquier aplicación en la nube".

    * Asegúrese de hacer clic en **Listo** en la ventana **Nuevo elemento**.

    ![google new item](media/google-new-item.png)

    * Clear the **Enable individual install** check box.

    * Configure las cuatro imágenes necesarias en **Iconos de la aplicación**.

    Las imágenes se encuentran en: [https://go.microsoft.com/fwlink/?linkid=862826](https://go.microsoft.com/fwlink/?linkid=862826)

    * Rellene lo siguiente en **Admitir URLs**:

    * **URL de las condiciones del servicio**: https://go.microsoft.com/fwlink/?LinkID=733268

    * **URL de la directiva de privacidad**: https://go.microsoft.com/fwlink/?LinkId=512132

    * En **OAuth 2.0 scopes** (Ámbitos de OAuth 2.0), copie y pegue las siguientes direcciones URL (cópielas una a una y presione ENTRAR después de cada una):

            `https://www.googleapis.com/auth/admin.reports.audit.readonly`

            `https://www.googleapis.com/auth/admin.reports.usage.readonly`

            `https://www.googleapis.com/auth/drive`

            `https://www.googleapis.com/auth/drive.appdata`

            `https://www.googleapis.com/auth/drive.apps.readonly`

            `https://www.googleapis.com/auth/drive.file`

            `https://www.googleapis.com/auth/drive.metadata.readonly`

            `https://www.googleapis.com/auth/drive.readonly`

            `https://www.googleapis.com/auth/drive.scripts`

            `https://www.googleapis.com/auth/admin.directory.user.readonly`

            `https://www.googleapis.com/auth/admin.directory.user.security`

            `https://www.googleapis.com/auth/admin.directory.user.alias`

            `https://www.googleapis.com/auth/admin.directory.orgunit`

            `https://www.googleapis.com/auth/admin.directory.notifications`

            `https://www.googleapis.com/auth/admin.directory.group.member`

            `https://www.googleapis.com/auth/admin.directory.group`

            `https://www.googleapis.com/auth/admin.directory.device.mobile.action`

            `https://www.googleapis.com/auth/admin.directory.device.mobile`

            `https://www.googleapis.com/auth/admin.directory.user`

    * En **Visibilidad**, seleccione **Mi dominio** (no público).
    * Haga clic en **Guardar cambios**.
        ![google visibility](media/google-visibility.png)
1. Vaya a [admin.google.com](https://admin.google.com/) y haga clic en **Seguridad**.

    ![google security](media/googlesec.png)

1. Seleccione **Referencia de API**.

    ![google api enable](media/googleapi.png)

1. Seleccione **Habilitar acceso de API** y haga clic en **Guardar cambios**.

    ![google api reference](media/googleapiref.png)

## <a name="configure-cloud-app-security"></a>Configurar Cloud App Security

1. En el portal de Cloud App Security, haga clic en **Investigar** y, después, en **Aplicaciones conectadas**.

1. To provide the G Suite connection details, under **App connectors**, do one of the following:

    **For a G Suite organization that already has a connected GCP instance**

    * In the list of connectors, at the end of row in which the GCP instance appears, click the three dots and then click **Add G Suite**.

    **For a G Suite organization that does not already have a connected GCP instance**

    * En la página **Aplicaciones conectadas**, haga clic en el signo más y seleccione **G Suite**.

3. En el elemento emergente, proporcione la información siguiente:

    ![G Suite Configuration in Cloud App Security](media/gsuite-config-cas.png "G Suite Configuration in Cloud App Security")

    1. **Id. de la cuenta de servicio** que ha copiado en el paso 13.

    1. **Project number (App ID)** that you copied in step 22.

    1. Cargue el archivo P12 de **certificado** que ha guardado en el paso 12. Para hacerlo, necesita la contraseña que ha guardado.

    1. Escriba un **correo electrónico de la cuenta de administrador** de su administrador de G Suite.

    1. Si tiene una cuenta G Suite Business o Enterprise, active esta casilla. Para obtener información sobre las características que están disponibles en Cloud App Security para G Suite Business o Enterprise, vea [Enable instant visibility, protection and governance actions for your apps](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md) (Habilitar la visibilidad, la protección y las acciones de gobernanza instantáneas para las aplicaciones).

    1. Haga clic en **Guardar configuración**.

    1. **Siga el vínculo** para conectarse a G Suite. Esto abrirá G Suite. Se le pedirá autorización de acceso para Cloud App Security.

    1. Haga clic en **Probar ahora** para confirmar que la conexión se ha realizado correctamente.

            Testing may take a couple of minutes.
    
            After receiving a success notice, click **Done** and close the G Suite page.

Después de conectar G Suite, recibirá eventos de 60 días anteriores a la conexión.

Después de conectar G Suite, Cloud App Security realiza un examen completo. En función del número de archivos y los usuarios que tenga, el examen podría tardar en completarse. Para habilitar el análisis casi en tiempo real, los archivos en los que se detecta actividad se mueven al principio de la cola de análisis. Por ejemplo, una archivo editado, actualizado o compartido se analiza inmediatamente. Esto no se aplica a los archivos que no se modifican de forma inherente. Por ejemplo, los archivos que se visualizan, previsualizan, imprimen o exportan se analizan durante un análisis normal.

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Controlar las aplicaciones en la nube con directivas](control-cloud-apps-with-policies.md)

[Los clientes Premier también pueden crear una solicitud de soporte técnico directamente en el portal Premier.](https://premier.microsoft.com/)
