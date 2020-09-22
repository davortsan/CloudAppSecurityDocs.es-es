---
title: Conexión de G Suite con Cloud App Security
description: En este artículo se proporciona información sobre cómo conectar G Suite con Cloud App Security mediante el conector de API para la visibilidad y el control del uso.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 11/27/2019
ms.topic: how-to
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 89342994a408ae1b03bd50c3c1fa4adc9dd12bc4
ms.sourcegitcommit: 575f2b2efa9ca4477d7e60271d21e225ef2c38ea
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/22/2020
ms.locfileid: "90881440"
---
# <a name="connect-g-suite-to-microsoft-cloud-app-security"></a>Conectar G Suite con Microsoft Cloud App Security

[!INCLUDE [Banner for top of topics](includes/banner.md)]

En este artículo se ofrecen instrucciones para conectar Microsoft Cloud App Security con una cuenta de G Suite existente mediante las API del conector. Esta conexión le ofrece visibilidad y control del uso de G Suite. Para obtener información sobre cómo Cloud App Security protege G Suite, consulte [Protect g Suite](protect-gsuite.md).

## <a name="configure-g-suite"></a>Configurar G Suite

1. Como superadministrador de G Suite, inicie sesión en <a href="https://cloud.google.com/console/project" target="_blank">https://cloud.google.com/console/project</a> .

1. Haga clic en **Crear un proyecto** para iniciar un nuevo proyecto.

    ![Crear proyecto de Google](media/google1.png)

1. En la pantalla **nuevo proyecto** , asigne al proyecto el nombre siguiente: **Cloud App Security** y haga clic en **crear**.

    ![Menú emergente de Google New Project](media/google2.png)

1. Una vez creado el proyecto, en la barra de herramientas, haga clic en **Google Cloud Platform**. Asegúrese de que el proyecto correcto está seleccionado en la lista desplegable en la parte superior.

    ![Haga clic en Google Cloud Platform en la barra de herramientas](media/googleverify-project.png)

1. Seleccione el menú, vaya a **API &**  >  **biblioteca Library** y habilite las siguientes API (use la línea de búsqueda si la API no aparece):

    * Admin SDK

    * Audit API

    * API de Google Drive

    * SDK de G Suite Marketplace  
![API de Google](media/google4.png)

    > [!NOTE]
    > Para cada API, haga clic en **Habilitar** para activarla.
    >
    > ![habilitación de Google APPI](media/google-api.png)
    >
    > Omita por ahora la advertencia sobre **credenciales**.

1. Seleccione menú, vaya a **API &**  >  **Panel**de servicios y asegúrese de que tiene habilitadas las siguientes API:

    ![API habilitadas para Google](media/google5.png)

1. Vaya a la pestaña **pantalla de consentimiento de OAuth** .

    * En **nombre**de la aplicación, escriba **Microsoft Cloud App Security**.

    * El resto de campos es opcional.

    * Haga clic en **Save**(Guardar).

    ![Consentimiento de OAuth de Google](media/google-oauth-consent.png)

1. En la pantalla **credenciales** , haga clic en la flecha situada junto a **crear credenciales**y seleccione **clave de cuenta de servicio**.

    ![Credenciales de Google](media/google7.png)

1. En **cuenta de servicio**, elija **nueva cuenta de servicio**y proporcione un nombre para la cuenta, por ejemplo, cuenta de **servicio 1**. En **Función**, elija **Project** (Proyecto) y después **Editor**. En **Tipo de clave**, elija **P12** y haga clic en **Crear**. Se guardará un archivo de certificado P12 en el equipo.

    ![Crear clave de cuenta de servicio en Google](media/google9.png)

1. En la pantalla **Credenciales**, haga clic en **Manage service accounts** (Administrar las cuentas de servicio) en el extremo derecho. Copie el **correo electrónico** asignado a su cuenta de servicio; lo necesitará más adelante.

    ![credenciales de la cuenta de servicio de G Suite](media/google10.png)

1. Haga clic en los tres puntos a la derecha de la cuenta de servicio que ha creado y seleccione **Editar**.

    ![edición de Google](media/google11.png "edición de Google")

1. Haga clic en **Mostrar delegación en todo el dominio**y seleccione **Habilitar delegación de todo el dominio de G Suite**.

    ![ID. de cliente de Google](media/google12.png "google12")

    1. Copie el **ID** . de cliente (lo necesitará más adelante).
    ![administrar el acceso de cliente de API](media/google12-2.png "google12-2")

    1. Haga clic en **GUARDAR**

    1. Vaya a [admin.google.com](https://admin.google.com/) y haga clic en **Seguridad**.

    1. Expanda **Configuración avanzada**y, a continuación, en **autenticación**, seleccione **administrar acceso de cliente de API**.

    1. En el cuadro **nombre de cliente** , escriba el identificador de **cliente** que copió anteriormente.  

    1. En el cuadro **uno o más ámbitos** de la API, escriba la siguiente lista de ámbitos necesarios (Copie el texto y péguelo en el cuadro):  
`https://www.googleapis.com/auth/admin.reports.audit.readonly,https://www.googleapis.com/auth/admin.reports.usage.readonly,https://www.googleapis.com/auth/drive,https://www.googleapis.com/auth/drive.appdata,https://www.googleapis.com/auth/drive.apps.readonly,https://www.googleapis.com/auth/drive.file,https://www.googleapis.com/auth/drive.metadata.readonly,https://www.googleapis.com/auth/drive.readonly,https://www.googleapis.com/auth/drive.scripts,https://www.googleapis.com/auth/admin.directory.user.readonly,https://www.googleapis.com/auth/admin.directory.user.security,https://www.googleapis.com/auth/admin.directory.user.alias,https://www.googleapis.com/auth/admin.directory.orgunit,https://www.googleapis.com/auth/admin.directory.notifications,https://www.googleapis.com/auth/admin.directory.group.member,https://www.googleapis.com/auth/admin.directory.group,https://www.googleapis.com/auth/admin.directory.device.mobile.action,https://www.googleapis.com/auth/admin.directory.device.mobile,https://www.googleapis.com/auth/admin.directory.user`

    1. Haga clic en **Autorizar**.

1. En el [Google Cloud Platform](https://console.cloud.google.com/), seleccione menú y vaya al panel de **API y servicios**  >  **Dashboard**.

1. En el panel, desplácese hacia abajo hasta la lista de API habilitadas y haga clic en **API de Google Drive**.
    ![Seleccione Google Drive](media/google14.png)

1. Haga clic en la pestaña **Drive UI Integration** (Integración de la IU de la unidad) y complete la información siguiente:

    * **Nombre de la aplicación**: Microsoft Cloud App Security.

    * **Descripción breve & Descripción larga** (opcional): Microsoft Cloud App Security proporciona visibilidad de las aplicaciones en la nube, lo que ayuda a controlar, investigar y controlar el uso de aplicaciones en la nube. proteger los datos corporativos; y detecte actividades sospechosas en cualquier aplicación en la nube.

    * Google requiere que se cargue al menos un icono de aplicación. Vaya a [https://go.microsoft.com/fwlink/?linkid=862826](https://go.microsoft.com/fwlink/?linkid=862826) para descargar un archivo zip que contiene iconos de Cloud App Security. A continuación, en el icono de la **aplicación**, haga clic en **seleccionar** junto a la imagen 128x128 y arrástrela a la pantalla emergente. Haga clic en **seleccionar** junto a la imagen 32x32 y arrástrela a la pantalla emergente.

    * Desplácese hacia abajo y, en la sección **integración de unidad** , escriba la siguiente dirección URL en **dirección URL abierta:**
    `https://portal.cloudappsecurity.com/#/services/11770?tab=files`

    ![Editar Google Drive](media/google15.png)

1. Haga clic en **Enviar**.

1. Vuelva a la lista **Enabled APIs** (API habilitadas). Haga clic en **SDK de G Suite Marketplace**.

1. Seleccione la pestaña **Configuración**.

    1. Copie el **Número de proyecto (id. de aplicación)** que aparece en la parte superior para usarlo más adelante.

    1. En **Nombre de la aplicación**, escriba **Microsoft Cloud App Security**.  
En **Descripción de la aplicación**, escriba "Microsoft Cloud App Security proporciona visibilidad de las aplicaciones en la nube, lo que sirve para controlar, investigar y gobernar el uso de esas aplicaciones en la nube; para proteger los datos corporativos, y para detectar actividades sospechosas en cualquier aplicación en la nube".

    1. Asegúrese de hacer clic en **Listo** en la ventana **Nuevo elemento**.

    ![nuevo elemento de Google](media/google-new-item.png)

    * Desactive la casilla **Habilitar instalación individual** .

    * Configure las cuatro imágenes necesarias en **Iconos de la aplicación**.

    Las imágenes se pueden encontrar en:  [https://go.microsoft.com/fwlink/?linkid=862826](https://go.microsoft.com/fwlink/?linkid=862826)

    * Rellene lo siguiente en **Admitir URLs**:

    * **Dirección URL de los términos de servicio**: https://go.microsoft.com/fwlink/?LinkID=733268

    * **Dirección URL**de la Directiva de privacidad: https://go.microsoft.com/fwlink/?LinkId=512132

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
        ![visibilidad de Google](media/google-visibility.png)
1. En la consola de administración de Google, vaya a [administrar App Access Control](https://admin.google.com/). Busque la fila de **Administrador de G Suite** y compruebe que tiene acceso **sin restricciones** .

    ![seguridad de Google](media/googlesec.png)

## <a name="configure-cloud-app-security"></a>Configurar Cloud App Security

1. En el portal de Cloud App Security, haga clic en **Investigar** y, después, en **Aplicaciones conectadas**.

1. Para proporcionar los detalles de conexión de G Suite, en **conectores de aplicaciones**, realice una de las acciones siguientes:

    **Para una organización de G Suite que ya tiene una instancia conectada de GCP**

    * En la lista de conectores, al final de la fila en la que aparece la instancia de GCP, haga clic en los tres puntos y, a continuación, haga clic en **Agregar G Suite**.

    **Para una organización de G Suite que aún no tiene una instancia conectada de GCP**

    * En la página **Aplicaciones conectadas**, haga clic en el signo más y seleccione **G Suite**.

1. En el elemento emergente, proporcione la información siguiente:

    ![Configuración de G Suite en Cloud App Security](media/gsuite-config-cas.png "Configuración de G Suite en Cloud App Security")

    1. Escriba el **identificador**de la cuenta de servicio, el **correo electrónico** que copió anteriormente.

    1. Escriba el **número de proyecto (ID. de aplicación)** que copió anteriormente.

    1. Cargue el archivo de **certificado** P12 que guardó anteriormente.

    1. Escriba un **correo electrónico de la cuenta de administrador** de su administrador de G Suite.

    1. Si tiene una cuenta G Suite Business o Enterprise, active esta casilla. Para obtener información sobre las características que están disponibles en Cloud App Security para G Suite Business o Enterprise, vea [Enable instant visibility, protection and governance actions for your apps](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md) (Habilitar la visibilidad, la protección y las acciones de gobernanza instantáneas para las aplicaciones).

    1. Haga clic en **Save settings** (Guardar configuración).

    1. **Siga el vínculo** para conectarse a G Suite. Esto abrirá G Suite. Se le pedirá autorización de acceso para Cloud App Security.

    1. Haga clic en **Probar ahora** para confirmar que la conexión se ha realizado correctamente.  
    La prueba puede tardar unos minutos.  
    Después de recibir una notificación de que todo se ha realizado correctamente, haga clic en **Listo** y cierre la página de G Suite.

Después de conectar G Suite, recibirá eventos de 60 días anteriores a la conexión.

Después de conectar G Suite, Cloud App Security realiza un examen completo. En función del número de archivos y los usuarios que tenga, el examen podría tardar en completarse. Para habilitar el análisis casi en tiempo real, los archivos en los que se detecta actividad se mueven al principio de la cola de análisis. Por ejemplo, una archivo editado, actualizado o compartido se analiza inmediatamente. Esto no se aplica a los archivos que no se modifican de forma inherente. Por ejemplo, los archivos que se visualizan, previsualizan, imprimen o exportan se analizan durante un análisis normal.

Si tiene problemas para conectar la aplicación, consulte [solución de problemas de conectores de aplicaciones](troubleshooting-api-connectors-using-error-messages.md).

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Controlar las aplicaciones en la nube con directivas](control-cloud-apps-with-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]
