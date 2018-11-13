---
title: Conectar G Suite con Cloud App Security para la visibilidad y el control del uso | Microsoft Docs
description: En este tema se proporciona información sobre cómo conectar G Suite con Cloud App Security mediante el conector de API.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 11/08/2018
ms.topic: conceptual
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: b938e1e0-356d-4cc6-ba4a-862c0c59d709
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 834f444831e2024d9a29ace710e7e2c35fb6f1ce
ms.sourcegitcommit: b8e75cefeffe3ae160830f3bf384f05db985e0d3
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/08/2018
ms.locfileid: "51285850"
---
*Se aplica a: Microsoft Cloud App Security*

# <a name="connect-g-suite-to-microsoft-cloud-app-security"></a>Conectar G Suite con Microsoft Cloud App Security
En esta sección se ofrecen instrucciones para conectar Microsoft Cloud App Security con una cuenta de G Suite existente mediante las API del conector.
  
  
## <a name="configure-g-suite"></a>Configurar G Suite  
  
1. Como superadministrador de G Suite, inicie sesión en <a href="https://cloud.google.com/console/project" target="_blank">https://cloud.google.com/console/project</a>.  
  
2. Haga clic en **Crear un proyecto** para iniciar un nuevo proyecto.  
  
    ![google1](./media/google1.png "google1")  
  
3. En la pantalla **Nuevo proyecto**, asigne al proyecto el nombre siguiente:</br>
   **Microsoft Cloud App Security** y haga clic en **Crear**.  
          ![google2](./media/google2.png "google2")  
  
4. Una vez creado el proyecto, en la barra de herramientas, haga clic en **Google Cloud Platform**. Asegúrese de que el proyecto correcto está seleccionado en la lista desplegable en la parte superior.
       
      ![Proyecto de Google](./media/googleverify-project.png "Verificación de proyecto de Google")  

5. En **API** haga clic en **Go to APIs overview** (Ir a información general de las API).  
  
     ![google3](./media/google3.png "google3")  
   
7. Haga clic en **Biblioteca** y habilite estas API [use la línea de búsqueda si la API no figura en la lista **Popular APIs** (API populares)]:  
     
   -   Admin SDK  
  
   -   Audit API  
  
   -   API de Google Drive  
  
   -   SDK de G Suite Marketplace  
  
   -   Gmail API  
            
   ![API de Google](./media/google4.png "google4")  
  
   > [!NOTE]  
   >  Omita por ahora la advertencia sobre **credenciales**.  

8. Haga clic en Habilitar para cada API.
     ![Habilitar Google APPI](./media/google-api.png "google-api")  
9. Asegúrese de que las siguientes API están habilitadas:
  
     ![API de Google habilitadas](./media/google5.png "google5")  
  
10. Haga clic en **Credenciales** y, a continuación, seleccione la pestaña **OAuth consent screen** (Pantalla de consentimiento de OAuth).
  
    - En **Product name shown to users** (Nombre de producto mostrado a los usuarios), escriba **Microsoft Cloud App Security**.  
  
    - El resto de campos es opcional.  
  
    - Haga clic en **Guardar**.  
  
      ![Consentimiento de OAuth de Google](./media/google-oauth-consent.png "consentimiento de OAuth de Google")  
  
11. En la pestaña **Credenciales**, haga clic en la flecha situada junto a **Crear credenciales**.  
  
     ![Credenciales de Google](./media/google7.png "google7")  

12. Seleccione **Service account key** (Clave de la cuenta del servicio).

     ![Clave de cuenta de servicio de Google](./media/google8.png "google8")  
  
13. En **Crear clave de cuenta de servicio**, elija **Nueva cuenta de servicio** y escriba cualquier nombre (por ejemplo, **Cuenta de servicio 1**). En **Función**, elija **Project** (Proyecto) y después **Editor**. En **Tipo de clave**, elija **P12** y haga clic en **Crear**. Se guardará un archivo de certificado P12 en el equipo.
 
     ![Crear clave de la cuenta del servicio de Google en Google](./media/google9.png "google9")  
  
14. Copie el **identificador de la cuenta de servicio** asignado a su servicio, ya que lo necesitará más adelante.    
        
15. En la pantalla **Credenciales**, haga clic en **Manage service accounts** (Administrar las cuentas de servicio) en el extremo derecho.  
     
    ![credenciales de la cuenta de servicio de G Suite](./media/google10.png "credenciales de la cuenta de servicio de G Suite")  
  
16. Haga clic en los tres puntos a la derecha de la cuenta de servicio que ha creado y seleccione **Editar**.  
  
     ![edición de Google](./media/google11.png "edición de Google")  
  
17. Active la casilla **Enable G Suite Domain-wide Delegation** (Habilitar delegación de todo el dominio de G Suite) y haga clic en **Guardar**.  
  
     ![identificador de la cuenta del servicio de Google](./media/google12.png "google12")  
  
18. Abra el menú de Google; para ello, haga clic en las tres líneas horizontales junto a Google Cloud Platform en la barra de título. Haga clic en **Google Cloud Platform** y, a continuación, haga clic en la pestaña **APIs and services** (API y servicios) del menú izquierdo.  
    
19. En el panel que se abre, desplácese a la lista de API habilitadas y haga clic en **API de Google Drive**.   
       ![Seleccionar Google Drive](./media/google14.png "google14")  

20. Haga clic en la pestaña **Drive UI Integration** (Integración de la IU de la unidad) y complete la información siguiente:

    - **Nombre de la aplicación**: Microsoft Cloud App Security.  
  
    - **Descripción breve y Descripción larga** (opcional): Microsoft Cloud App Security proporciona visibilidad de las aplicaciones en la nube, lo que sirve para controlar, investigar y gobernar el uso de esas aplicaciones en la nube, para proteger los datos corporativos y para detectar actividades sospechosas en cualquier aplicación en la nube.  
  
    - Google requiere que se cargue al menos un icono de aplicación. Vaya a [https://go.microsoft.com/fwlink/?linkid=862826](https://go.microsoft.com/fwlink/?linkid=862826) para descargar un archivo ZIP que contiene los iconos de Cloud App Security. A continuación, debajo del **icono Aplicación**, haga clic en **Seleccionar**, junto a la imagen de 128 x 128, y arrastre el archivo a la ventana emergente. Haga clic en **Seleccionar**, junto a la imagen de 32 x 32, y arrastre el archivo a la ventana emergente.  
  
    - Desplácese hacia abajo y, en la sección **Drive Integration** (Integración de unidades), escriba la siguiente dirección URL en **Abrir dirección URL:**  
  
       https://portal.cloudappsecurity.com/#/services/11770?tab=files  
    
      ![Editar Google Drive](./media/google15.png "google15")  

21. Haga clic en **Guardar cambios**.

22. Vuelva a la lista **Enabled APIs** (API habilitadas). Haga clic en **SDK de G Suite Marketplace**. 
      
23. Seleccione la pestaña **Configuración**. 
  
    -   Copie el **Número de proyecto (id. de aplicación)** que aparece en la parte superior para usarlo más adelante.  
  
    -   En **Nombre de la aplicación**, escriba **Microsoft Cloud App Security**.
  
         En **Descripción de la aplicación**, escriba "Microsoft Cloud App Security proporciona visibilidad de las aplicaciones en la nube, lo que sirve para controlar, investigar y gobernar el uso de esas aplicaciones en la nube; para proteger los datos corporativos, y para detectar actividades sospechosas en cualquier aplicación en la nube". 
    - Asegúrese de hacer clic en **Listo** en la ventana **Nuevo elemento**.      
     
       ![nuevo elemento de Google](./media/google-new-item.png "nuevo elemento de Google")  

    -   Desactive la casilla **Enable individual install** (Habilitar la instalación individual).  
  
    -   Configure las cuatro imágenes necesarias en **Iconos de la aplicación**.  
  
         Las imágenes se encuentran en: [https://go.microsoft.com/fwlink/?linkid=862826](https://go.microsoft.com/fwlink/?linkid=862826)  
  
    -   Rellene lo siguiente en **Admitir URLs**:  
  
        -   **URL de las condiciones del servicio**: http://go.microsoft.com/fwlink/?LinkID=733268  
  
        -   **URL de la directiva de privacidad**: http://go.microsoft.com/fwlink/?LinkId=512132  
  
    -   En **OAuth 2.0 scopes** (Ámbitos de OAuth 2.0), copie y pegue las siguientes direcciones URL (cópielas una a una y presione ENTRAR después de cada una):  
  
           https://www.googleapis.com/auth/admin.reports.audit.readonly  
  
           https://www.googleapis.com/auth/admin.reports.usage.readonly  
  
           https://www.googleapis.com/auth/drive  
  
           https://www.googleapis.com/auth/drive.appdata  
  
           https://www.googleapis.com/auth/drive.apps.readonly  
  
           https://www.googleapis.com/auth/drive.file  
  
           https://www.googleapis.com/auth/drive.metadata.readonly  
  
           https://www.googleapis.com/auth/drive.readonly  
  
           https://www.googleapis.com/auth/drive.scripts  
  
           https://www.googleapis.com/auth/admin.directory.user.readonly  
  
           https://www.googleapis.com/auth/admin.directory.user.security  
  
           https://www.googleapis.com/auth/admin.directory.user.alias  
  
           https://www.googleapis.com/auth/admin.directory.orgunit  
  
           https://www.googleapis.com/auth/admin.directory.notifications  
  
           https://www.googleapis.com/auth/admin.directory.group.member  
  
           https://www.googleapis.com/auth/admin.directory.group  
  
           https://www.googleapis.com/auth/admin.directory.device.mobile.action  
  
           https://www.googleapis.com/auth/admin.directory.device.mobile  
  
           https://www.googleapis.com/auth/admin.directory.user  

    -   En **Visibilidad**, seleccione **Mi dominio** (no público). 
    -   Haga clic en **Guardar cambios**.  
        ![Visibilidad de Google](./media/google-visibility.png "google visibility")  
24. Vaya a [admin.google.com](https://admin.google.com/) y haga clic en **Seguridad**. 
   
      ![seguridad de google](./media/googlesec.png "seguridad de google")  
 
25. Seleccione **Referencia de API**.  
       ![habilitación de la API de google](./media/googleapi.png "api de google")  
      
26. Seleccione **Habilitar acceso de API** y haga clic en **Guardar cambios**.  
  
    ![referencia de API de Google](./media/googleapiref.png "google8")  

  
## <a name="configure-cloud-app-security"></a>Configurar Cloud App Security  
  
1.  En el portal de Cloud App Security, haga clic en **Investigar** y, después, en **Aplicaciones conectadas**.  
  
2.  En la página **Aplicaciones conectadas**, haga clic en el signo más y seleccione **G Suite**.  
       
  
3.  En el elemento emergente, proporcione la información siguiente:  
  
     ![Configuración de G Suite en Cloud App Security](./media/gsuite-config-cas.png "Configuración de G Suite en Cloud App Security")  
  
    1.  **Id. de la cuenta de servicio** que ha copiado en el paso 13.  
  
    2.  **Número de proyecto (identificador de la aplicación)** que ha copiado en el paso 21.  
  
    3.  Cargue el archivo P12 de **certificado** que ha guardado en el paso 12. Para hacerlo, necesita la contraseña que ha guardado.  
  
    4.  Escriba un **correo electrónico de la cuenta de administrador** de su administrador de G Suite.  
  
    5.  Si tiene una cuenta G Suite Business o Enterprise, active esta casilla. Para obtener información sobre las características que están disponibles en Cloud App Security para G Suite Business o Enterprise, vea [Enable instant visibility, protection and governance actions for your apps](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md) (Habilitar la visibilidad, la protección y las acciones de gobierno instantáneas para las aplicaciones).  
  
    6.  Haga clic en **Guardar configuración**.  
  
    7.  **Siga el vínculo** para conectarse a G Suite. Esto abrirá G Suite. Se le pedirá autorización de acceso para Cloud App Security.  
         
    8.  Haga clic en **Probar ahora** para confirmar que la conexión se ha realizado correctamente.  
  
         La prueba puede tardar unos minutos.  
  
         Después de recibir una notificación de que todo se ha realizado correctamente, haga clic en **Listo** y cierre la página de G Suite.  
  
  
Después de conectar G Suite, recibirá eventos de 60 días anteriores a la conexión.
  
Después de conectar G Suite, Cloud App Security realiza un examen completo. En función del número de archivos y los usuarios que tenga, el examen podría tardar en completarse. Para habilitar el análisis casi en tiempo real, los archivos en los que se detecta actividad se mueven al principio de la cola de análisis. Por ejemplo, una archivo editado, actualizado o compartido se analiza inmediatamente. Esto no se aplica a los archivos que no se modifican de forma inherente. Por ejemplo, los archivos que se visualizan, previsualizan, imprimen o exportan se analizan durante un análisis normal.
  
  
## <a name="next-steps"></a>Pasos siguientes 
[Controlar las aplicaciones en la nube con directivas](control-cloud-apps-with-policies.md)   

[Los clientes Premier también pueden elegir Cloud App Security directamente desde el Portal Premier.](https://premier.microsoft.com/)  
  
  