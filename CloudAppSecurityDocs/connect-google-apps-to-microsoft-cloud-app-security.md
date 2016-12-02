---
title: Conectar Google Apps | Microsoft Docs
description: "En este tema se proporciona información sobre cómo conectar Google Apps con Cloud App Security mediante el conector de API."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 11/23/2016
ms.topic: get-started-article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: b938e1e0-356d-4cc6-ba4a-862c0c59d709
ms.reviewer: reutam
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 6beb9041b338406fb5b16f4bd045dbdc4592c6d9
ms.openlocfilehash: b28eaa521980cb7ec8eee94f0168ca07286533e7


---

# <a name="connect-google-apps-to-microsoft-cloud-app-security"></a>Conectar Google Apps con Microsoft Cloud App Security
En esta sección se proporcionan instrucciones para conectar Cloud App Security con una cuenta de Google Apps existente mediante las API del conector.

  
  
## <a name="configure-google-apps"></a>Configurar Google Apps  
  
1.  Inicie sesión en [https://cloud.google.com/console/project](https://cloud.google.com/console/project) como superadministrador de Google Apps.  
  
2.  Haga clic en **Crear un proyecto vacío** para iniciar un nuevo proyecto.  
  
     ![google1](./media/google1.png "google1")  
  
3.  En la pantalla **Nuevo proyecto**:  
  
    1.  Denomine el proyecto **Cloud App Security para Google**.  
  
    2.  Seleccione si quiere o no suscribirse a las actualizaciones.  
  
    3.  Revise y apruebe las condiciones del servicio.  
  
    4.  Haga clic en **Crear**.  
  
         ![google2](./media/google2.png "google2")  
  
4.  Una vez creado el proyecto, haga clic en **Habilitar y administrar APIs**.  
  
     ![google3](./media/google3.png "google3")  
  
5.  Haga clic en la pestaña **APIs habilitadas** y deshabilite todas las API que aparecen.  
  
     ![google5](./media/google5.png "google5")  
  
6.  Haga clic en la pestaña **Google APIs** (API de Google) y habilite las siguientes API (use la línea de búsqueda si la API no figura en la lista **Popular APIs** (API populares)):  
  
     ![google8](./media/google8.png "google8")  
  
    > [!NOTE]  
    >  Omita por ahora la advertencia sobre **credenciales**.  
  
    -   Admin SDK  
  
    -   Audit API  
  
    -   Drive API  
  
    -   Google Apps Marketplace SDK  
  
    -   Gmail API  
  
         ![advertencia google11](./media/google11-warning.png "google11 warning")  
  
7.  Debe tener cinco **APIs habilitadas**:  
  
     ![google15](./media/google15.png "google15")  
  
8.  Haga clic en **Credenciales** y, luego, en **Pantalla de autorización de OAuth**.  
  
    -   En **Nombre de producto mostrado a los usuarios**, escriba **Cloud App Security para Google**.  
  
    -   El resto de campos es opcional.  
  
    -   Haga clic en **Guardar**.  
  
     ![google16](./media/google16.png "google16")  
  
9. En la pestaña **Credenciales**, haga clic en la flecha de la opción **Crear credenciales** y seleccione **Clave de cuenta de servicio**.  
  
     ![google17](./media/google17.png "google17")  
  
10. En **Cuenta de servicio**, elija **Nueva cuenta de servicio** y escriba cualquier nombre (por ejemplo, **Cuenta de servicio 1**).  
  
     ![google19](./media/google19.png "google19")  
  
     En **Tipo de clave**, elija **P12** y haga clic en **Crear**.  
  
     Se descargará un archivo de certificado P12. Guarde el certificado para poder usarlo más adelante.  
  
     ![google20](./media/google20.png "google20")  
  
11. En la pestaña **Credenciales**, haga clic en la pestaña **Administra las cuentas de servicio** en el extremo derecho.  
  
     ![credenciales de la cuenta de servicio de Google Apps](./media/google-apps-credentials-service-account.png "google apps credentials service account")  
  
12. Haga clic en los tres puntos a la derecha de la cuenta de servicio que ha creado y seleccione **Editar**.  
  
     ![google22](./media/google22.png "google22")  
  
13. Active la casilla **Enable Google Apps Domain-wide Delegation** (Habilitar delegación de todo el dominio de Google Apps) y haga clic en **Guardar**.  
  
     ![google24](./media/google24.png "google24")  
  
14. Copie la **dirección de correo electrónico** asignada a su servicio (la necesitará más adelante).  
  
     ![google25](./media/google25.png "google25")  
  
15. Abra el menú de Google (para ello, haga clic en las tres líneas horizontales junto a Google Cloud Platform) y seleccione **Administrador de APIs**.  
  
     ![menú de Google](./media/google-menu.png "google menu")  
  
     Seleccione **APIs habilitadas**.  
  
     ![google27](./media/google27.png "google27")  
  
16. Haga clic en el engranaje de configuración junto a **Drive API** y, en **Integración con la interfaz de Drive**, rellene lo siguiente:  
  
    -   **Nombre de la aplicación**: Cloud App Security para Google.  
  
    -   **Descripción breve y Descripción larga**: Microsoft Cloud App Security proporciona visibilidad de las aplicaciones en la nube, lo que sirve para controlar, investigar y gobernar el uso de esas aplicaciones en la nube; para proteger los datos corporativos, y para detectar actividades sospechosas en cualquier aplicación en la nube.  
  
    -   En **Icono de la aplicación**, cargue las imágenes de 128x128 y 32x32.  
  
         Encontrará las imágenes en: [https://portal.cloudappsecurity.com/cas/static/files/MSLogos.zip](https://portal.cloudappsecurity.com/cas/static/files/MSLogos.zip)  
  
    -   Escriba lo siguiente en **URL de apertura**:  
  
         https://portal.cloudappsecurity.com/#/services/11770?tab=files  
  
    -   Haga clic en **Guardar cambios**.  
  
         ![google29](./media/google29.png "google29")  
  
17. En la lista **APIs habilitadas**, haga clic en el engranaje de configuración junto a **Google Apps Marketplace SDK** y seleccione la pestaña **Configuración**.  
  
    -   Copie el **Número de proyecto (id. de aplicación)** que aparece en la parte superior para usarlo más adelante.  
  
    -   **Nombre de la aplicación**: Cloud App Security para Google.  
  
         Rellene el campo **Descripción de la aplicación** con "Microsoft Cloud App Security proporciona visibilidad de las aplicaciones en la nube, lo que sirve para controlar, investigar y gobernar el uso de esas aplicaciones en la nube; para proteger los datos corporativos, y para detectar actividades sospechosas en cualquier aplicación en la nube".  
  
    -   Desactive la casilla **Habilitar la instalación individual**.  
  
    -   Configure las cuatro imágenes necesarias en **Iconos de la aplicación**.  
  
         Encontrará las imágenes en: [https://portal.cloudappsecurity.com/cas/static/files/MSLogos.zip](https://portal.cloudappsecurity.com/cas/static/files/MSLogos.zip)  
  
         ![google31](./media/google31.png "google31")  
  
    -   Rellene lo siguiente en **Admitir URLs**:  
  
        -   **URL de las condiciones del servicio**: http://go.microsoft.com/fwlink/?LinkID=733268  
  
        -   **URL de la política de privacidad**: http://go.microsoft.com/fwlink/?LinkId=512132  
  
    -   En **OAuth 2.0 scopes** (Ámbitos de OAuth 2.0) escriba lo siguiente (uno por línea y pulse Entrar para confirmar):  
  
        -   https://www.googleapis.com/auth/admin.reports.audit.readonly  
  
        -   https://www.googleapis.com/auth/admin.reports.usage.readonly  
  
        -   https://www.googleapis.com/auth/drive  
  
        -   https://www.googleapis.com/auth/drive.appdata  
  
        -   https://www.googleapis.com/auth/drive.apps.readonly  
  
        -   https://www.googleapis.com/auth/drive.file  
  
        -   https://www.googleapis.com/auth/drive.metadata.readonly  
  
        -   https://www.googleapis.com/auth/drive.readonly  
  
        -   https://www.googleapis.com/auth/drive.scripts  
  
        -   https://www.googleapis.com/auth/admin.directory.user.readonly  
  
        -   https://www.googleapis.com/auth/admin.directory.user.security  
  
        -   https://www.googleapis.com/auth/admin.directory.user.alias  
  
        -   https://www.googleapis.com/auth/admin.directory.orgunit  
  
        -   https://www.googleapis.com/auth/admin.directory.notifications  
  
        -   https://www.googleapis.com/auth/admin.directory.group.member  
  
        -   https://www.googleapis.com/auth/admin.directory.group  
  
        -   https://www.googleapis.com/auth/admin.directory.device.mobile.action  
  
        -   https://www.googleapis.com/auth/admin.directory.device.mobile  
  
        -   https://www.googleapis.com/auth/admin.directory.user  
  
    -   Haga clic en **Guardar cambios**.  
  
18. Seleccione **Seguridad** de la lista de controles. Si no ve esta opción, seleccione Más controles en la barra gris en la parte inferior de la página y, luego, seleccione **Seguridad**.  
  
     ![seguridad de Google Apps](./media/google-apps-security.png "google apps security")  
  
19. Seleccione **Referencia de API**.  
  
     ![referencia de API de Google](./media/google-api-ref.png "google api ref")  
  
20. Seleccione **Habilitar acceso de API** y haga clic en **Guardar cambios**.  
  
     ![acceso de API de Google](./media/google-api-access.png "google api access")  
  
## <a name="configure-cloud-app-security"></a>Configurar Cloud App Security  
  
1.  En el portal de Cloud App Security, haga clic en **Investigar** y, después, en **Aplicaciones conectadas**.  
  
2.  En la página **Conectores de aplicaciones**, haga clic en el botón del signo más y seleccione **Google Apps**.  
  
     ![conectar con Google Apps](./media/connect-google-apps.png "connect google apps")  
  
3.  En el elemento emergente, proporcione la información siguiente:  
  
     ![Configuración de Google Apps en Cloud App Security](./media/google-apps-configuration-in-cloud-app-security.png "Google Apps Configuration in Cloud App Security")  
  
    1.  **Dirección de correo electrónico de la cuenta del servicio de Google** que ha copiado en el paso 14.  
  
    2.  **Número de proyecto de Google (id. de la aplicación)** que ha copiado en el paso 17.  
  
    3.  Cargue el archivo P12 de **certificado de Google** que ha guardado en el paso 10.  
  
    4.  Escriba el **correo electrónico de administrador** del administrador de Google Apps.  
  
    5.  Active esta casilla si tiene una cuenta de Google Apps ilimitada. Para obtener información sobre qué características están disponibles en Cloud App Security para Google Apps Unlimited, vea [Enable instant visibility, protection and governance actions for your apps](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md) (Habilitar la visibilidad, la protección y las acciones de gobierno instantáneas para las aplicaciones).  
  
    6.  Haga clic en **Guardar configuración**.  
  
    7.  **Siga el vínculo** para conectarse a Google Apps. Esto abrirá Google Apps. Se le pedirá autorización de acceso para Cloud App Security.  
  
         ![Solicitud de autorización de Google Apps](./media/google-apps-authorization-request.png "Google Apps authorization request")  
  
    8.  Haga clic en **Probar API** para confirmar que la conexión se ha realizado correctamente.  
  
         La prueba puede tardar unos minutos.  
  
         Después de recibir una notificación de que todo se ha realizado correctamente, haga clic en **Listo** y cierre la página de Google Apps.  
  
  
Después de conectar Google Apps, recibirá eventos de 60 días anteriores a la conexión.
  
Después de conectar Google Apps, Cloud App Security realiza un examen completo. En función del número de archivos y los usuarios que tenga, el examen podría tardar en completarse. Para habilitar el examen prácticamente en tiempo real, los archivos en los que se detecta actividad se mueven al principio de la cola de examen. Por ejemplo, si un archivo se está editando, actualizando o compartiendo, se analiza de inmediato y no espera a que lo alcance el proceso de examen normal. Esto no se aplica a los archivos que no se modifican de forma intrínseca, por ejemplo, los archivos que se ven, se consultan en vista previa, se imprimen o se exportan.
  
  
## <a name="see-also"></a>Consulte también  
[Controlar las aplicaciones en la nube con directivas](control-cloud-apps-with-policies.md)   
[Para obtener soporte técnico, visite la página de soporte técnico asistido de Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Los clientes Premier también pueden elegir Cloud App Security directamente desde el Portal Premier.](https://premier.microsoft.com/)  
  
  


<!--HONumber=Nov16_HO5-->


