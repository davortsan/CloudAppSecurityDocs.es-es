---
title: Creación de directivas de sesión en Cloud App Security
description: En este artículo se describe el procedimiento para configurar una directiva de sesión de control de aplicaciones de acceso condicional de Cloud App Security para obtener visibilidad detallada de las actividades de la sesión del usuario y bloquear descargas por medio de las funciones de proxy inverso.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 03/31/2020
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 47aa53855f83a2898616d17e6d4b12786bc7d893
ms.sourcegitcommit: 6886d285601955f0efc7acf980c9d4740ff873fe
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/01/2020
ms.locfileid: "84250679"
---
# <a name="session-policies"></a>Directivas de sesión

*Se aplica a: Microsoft Cloud App Security*

Las directivas de sesión de Microsoft Cloud App Security permiten las supervisiones en tiempo real y en el nivel de sesión, lo que le proporciona una visibilidad granular de las aplicaciones en la nube, así como la posibilidad de realizar distintas acciones según la directiva establecida para una sesión de usuario. En lugar de [permitir o bloquear el acceso por completo](access-policy-aad.md), con el control de sesión, puede permitir el acceso mientras supervisa la sesión o limita determinadas actividades de la sesión usando las funciones de proxy inverso de control de aplicaciones de acceso condicional.

Por ejemplo, puede decidir que, desde cualquier dispositivo no administrado o en sesiones que provienen de ubicaciones específicas, quiere permitir el acceso del usuario a la aplicación, pero también limitar la descarga de archivos confidenciales o requerir que algunos documentos estén protegidos al descargarse. Las directivas de sesión permiten establecer estos controles de sesión de usuario, ademas del acceso, y le permite realizar lo siguiente:

* [Supervisar todas las actividades](#monitor-session)
* [Bloqueo de todas las descargas](#block-download)
* [Bloqueo de actividades específicas](#block-activities)
* [Protección de archivos en la descarga](#protect-download)
* [Proteger cargas de archivos confidenciales](#protect-upload)
* [Instruya a los usuarios para proteger archivos confidenciales](#educate-protect)

## <a name="prerequisites-to-using-session-policies"></a>Requisitos previos para usar directivas de sesión

* Azure AD Premium licencia P1 o la licencia requerida por su solución de proveedor de identidades (IdP)
* Las aplicaciones en cuestión deben estar [implementadas con control de aplicaciones de acceso condicional](proxy-deployment-aad.md).
* Asegúrese de que ha configurado la solución IdP para que funcione con Cloud App Security, como se indica a continuación:
  * En el caso del [acceso condicional de Azure AD](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal), consulte [Configuración de la integración con Azure AD](proxy-deployment-aad.md#configure-integration-with-azure-ad).
  * Para información sobre otras soluciones IdP, consulte [Configuración de la integración con otras soluciones IdP](proxy-deployment-aad.md#configure-integration-with-other-idp-solutions).

## <a name="create-a-cloud-app-security-session-policy"></a>Crear una directiva de sesión de Cloud App Security

Haga lo siguiente para crear una directiva de sesión:

1. En el portal, seleccione **Control** y, después, **Directivas**.
1. En la página **Directivas**, haga clic en **Crear directiva** y seleccione **Directiva de sesión**.
1. En la ventana **Directiva de sesión**, especifique un nombre para la directiva, como *Bloquear descarga de documentos confidenciales en Box de usuarios de marketing*.
1. En el campo **Tipo de control de sesión**, haga lo siguiente:

    1. Seleccione **Monitor only** (Solo supervisar) si solo quiere supervisar las actividades de los usuarios. Esta selección creará una directiva de solo supervisión para las aplicaciones que seleccionó en la que, todos los inicios de sesión, descargas heurísticas y tipos de actividad, se descargarán.

    1. Seleccione **Controlar la descarga de archivos (con DLP)** si quiere supervisar las actividades del usuario. Puede realizar acciones adicionales como bloquear o proteger las descargas para los usuarios.
    1. Seleccione **Bloquear actividades** para bloquear actividades específicas que se pueden seleccionar con el filtro **Tipo de actividad**. Todas las actividades de las aplicaciones seleccionadas se supervisarán (y notificarán en el registro de actividad). Las actividades específicas que seleccione se bloquearán si selecciona la acción **Bloquear**. Las actividades específicas que seleccione generarán alertas si selecciona la acción **Probar** y hay alertas activadas.
1. En la sección **Actividades que coinciden con todo lo siguiente** de **Origen de la actividad**, seleccione más filtros de actividad para aplicarlos a la directiva. Los filtros incluyen las siguientes opciones:

    * **Etiqueta de dispositivo**: use este filtro para identificar los dispositivos no administrados.

    * **Ubicación**: use este filtro para identificar las ubicaciones desconocidas (por tanto, que entrañan riesgo).

    * **Dirección IP**: use este filtro para filtrar por direcciones IP o usar las etiquetas de dirección IP previamente asignadas.

    * **Etiqueta de agente de usuario**: use este filtro para habilitar la heurística que permite identificar las aplicaciones de escritorio y móviles. Este filtro se puede establecer en "igual a" o "no es igual a" **Cliente nativo**. Este filtro se debe probar con las aplicaciones de escritorio y móviles para cada aplicación en la nube.

    >[!NOTE]
    >Las directivas de sesión no admiten aplicaciones móviles y de escritorio. Las aplicaciones móviles y de escritorio también pueden bloquearse o permitirse con la creación de una directiva de acceso.

1. Si ha seleccionado la opción **Controlar la descarga de archivos (con DLP)**:

    1. En la sección **Archivos que coinciden con todo lo siguiente** de **Origen de la actividad**, seleccione más filtros de archivo para aplicarlos a la directiva. Los filtros incluyen las siguientes opciones:

        * **Etiqueta de clasificación** : Use este filtro si la organización usa Azure Information Protection y los datos están protegidos por sus etiquetas de clasificación. Podrá filtrar los archivos por la etiqueta de clasificación que tengan aplicada. Para obtener más información sobre la integración con Azure Information Protection, vea [Integración de Azure Information Protection](azip-integration.md).

        * **Nombre de archivo**: use este filtro para aplicar la directiva a archivos concretos.
        * **Tipo de archivo**: use este filtro para aplicar la directiva a tipos de archivo concretos, por ejemplo, para bloquear la descarga de cualquier archivo .xls.
    2. En la sección **Inspección de contenido**, establezca si quiere permitir que el motor DLP examine documentos y el contenido de los archivos.

    3. En **Acciones**, seleccione uno de los siguientes elementos:

        * **Test (Monitor all activities)** (Probar [supervisar todas las actividades]): establezca esta acción para permitir expresamente las descargas según los filtros de directiva que haya establecido.

        * **Block (Block file download and monitor all activities)** (Bloquear [bloquear descargas de archivos y supervisar todas las actividades]): establezca esta acción para bloquear expresamente las descargas según los filtros de directiva que haya establecido. Para más información, vea [Cómo funciona el bloqueo de descargas](#block-download).

        * **Protect (Apply classification label to download and monitor all activities)** (Proteger [aplicar etiqueta de clasificación para descargar y supervisar todas las actividades]): esta opción solo está disponible si seleccionó **Controlar la descarga de archivos (con DLP)** en **Directiva de sesión**. Si la organización usa Azure Information Protection, puede establecer una **acción** que aplique al archivo una etiqueta de clasificación establecida en Azure Information Protection. Para más información, vea [Cómo funciona la protección de descargas](#protect-download).

1. Puede **Crear una alerta para cada evento coincidente con la gravedad de la directiva** y establecer un límite de alerta. Seleccione si quiere que la alerta se envíe como mensaje de correo electrónico, de texto o ambos.

## <a name="monitor-all-activities"></a><a name="monitor-session"></a>Supervisar todas las actividades

Cuando se crea una directiva de sesión, cada sesión de usuario que coincida con la directiva se redirige al control de sesión, y no directamente a la aplicación. El usuario verá una notificación de supervisión que le avisa de que sus sesiones se están supervisando.

Si prefiere no avisar al usuario de que se le está supervisando, puede deshabilitar el mensaje de notificación.

1. En el engranaje Configuración, seleccione **Configuración general**.

2. Después, en **Control de aplicación de acceso condicional**, active **Supervisión de usuarios** y desactive la casilla **Notificar a los usuarios**.

Para mantener al usuario dentro de la sesión, el control de aplicaciones de acceso condicional reemplaza todas las direcciones URL, scripts de Java y cookies pertinentes de la sesión de aplicación por direcciones URL de Microsoft Cloud App Security. Por ejemplo, si la aplicación devuelve una página con vínculos cuyos dominios finalizan con myapp.com, Control de aplicaciones de acceso condicional reemplaza los vínculos con dominios que terminan con algo parecido a `myapp.com.mcas.ms` . De esta forma, la sesión completa se supervisa por medio de Microsoft Cloud App Security.

El control de aplicaciones de acceso condicional crea registros de tráfico de cada sesión de usuario que pasa a través de él. Los registros de tráfico reflejan la hora, la dirección IP, los agentes de usuario, las direcciones URL visitadas y el número de bytes cargados y descargados. Estos registros se analizan, mientras que un informe constantemente activo denominado **Cloud App Security Conditional Access App Control** (Control de aplicaciones de acceso condicional de Cloud App Security) se agrega a la lista de informes de Cloud Discovery en el panel de Cloud Discovery.

Para exportar estos registros, haga lo siguiente:

1. Vaya al engranaje Configuración y haga clic en **Conditional Access App Control** (Control de aplicaciones de acceso condicional).
2. En el lado derecho de la tabla, haga clic en el botón de exportación.

    ![botón Exportar](./media/export-button.png)
3. Seleccione el intervalo del informe y haga clic en **Exportar**. Este proceso puede tardar algún tiempo.

Para descargar el registro exportado:

1. Una vez que el informe esté listo, vaya a **Configuración** y después a **Informes exportados**.
2. En la tabla, seleccione el informe que proceda en la lista de **registros de tráfico del control de aplicaciones de acceso condicional** y haga clic en el botón de descarga.

    ![botón descargar](./media/download-button.png)

## <a name="block-all-downloads"></a><a name="block-download"></a>Bloqueo de todas las descargas

Cuando **bloquear** está establecido como la **acción** que desea realizar en la directiva de sesión de Cloud App Security, control de aplicaciones de acceso condicional impide que un usuario descargue un archivo según los filtros de archivo de la Directiva. Microsoft Cloud App Security reconoce un evento de descarga para cada aplicación cuando un usuario inicia una descarga. El Control de aplicaciones de acceso condicional interviene en tiempo real para evitar que se ejecute. Cuando se recibe la señal de que un usuario ha iniciado una descarga, el control de aplicaciones de acceso condicional devuelve al usuario un mensaje que indica que la **descarga está restringida** y reemplaza el archivo descargado por un archivo de texto. El mensaje de dicho archivo se puede configurar y personalizar para el usuario en la directiva de sesión.

## <a name="block-specific-activities"></a><a name="block-activities"></a>Bloqueo de actividades específicas

Cuando **Bloquear actividades** se establece como **Tipo de actividad**, pueden seleccionarse determinadas actividades para bloquear aplicaciones específicas. Todas las actividades de las aplicaciones seleccionadas se supervisarán y notificarán en el registro de actividad. Las actividades específicas que seleccione se bloquearán si selecciona la acción **Bloquear**. Las actividades específicas que seleccione generarán alertas si selecciona la acción **Probar** y hay alertas activadas.

**Bloquee actividades específicas** y aplíquelo a grupos específicos para crear un modo de solo lectura completo para la organización.

## <a name="protect-files-on-download"></a><a name="protect-download"></a>Protección de archivos en la descarga

Seleccione **Bloquear actividades** para bloquear actividades específicas que se pueden buscar con el filtro **Tipo de actividad**. Todas las actividades de las aplicaciones seleccionadas se supervisarán (y notificarán en el registro de actividad). Las actividades específicas que seleccione se bloquearán si selecciona la acción **Bloquear**. Las actividades específicas que seleccione generarán alertas si selecciona la acción **Probar** y hay alertas activadas.

Cuando **proteger** se establece como la **acción** que se va a realizar en la directiva de sesión de Cloud App Security, control de aplicaciones de acceso condicional aplica el etiquetado y la protección posterior de un archivo según los filtros de archivo de la Directiva. Las etiquetas se configuran en la consola de Azure Information Protection y **Proteger** debe estar seleccionado en la etiqueta para que aparezca como una opción en la directiva de Cloud App Security. Cuando se selecciona una etiqueta y se descarga un archivo que cumple los criterios de la directiva de Cloud App Security, tanto la etiqueta como la protección correspondiente (con permisos) se aplican al archivo de descarga. El archivo original permanece tal cual en la aplicación en la nube, mientras que el archivo descargado ahora está protegido. Los usuarios que intenten acceder al archivo deben cumplir los requisitos de permiso establecidos por la protección aplicada.

Actualmente, Cloud App Security admite aplicar [etiquetas de clasificación de Azure Information Protection](azip-integration.md) para los siguientes tipos de archivo:

* Word: docm, docx, dotm, dotx
* Excel: xlam, xlsm, xlsx, xltx
* PowerPoint: potm, potx, ppsx, ppsm, pptm, pptx
* PDF
  > [!NOTE]
  > En el caso de PDF, debe usar etiquetas unificadas.

## <a name="protect-uploads-of-sensitive-files"></a><a name="protect-upload"></a>Proteger cargas de archivos confidenciales

Cuando **controlar la carga de archivos (con DLP)** se establece como el **tipo de control de sesión** en la directiva de sesión de Cloud App Security, control de aplicaciones de acceso condicional impide que un usuario cargue un archivo por los filtros de archivos de la Directiva. Cuando se reconoce un evento de carga, Control de aplicaciones de acceso condicional interviene en tiempo real para determinar si el archivo es sensible y necesita protección. Si el archivo tiene datos confidenciales y no tiene una etiqueta adecuada, se bloquea la carga de archivos.

Por ejemplo, puede crear una directiva que examine el contenido de un archivo para determinar si contiene una coincidencia de contenido confidencial, como un número de la seguridad social. Si contiene contenido confidencial y no se etiqueta con una Azure Information Protection etiqueta confidencial, la carga de archivos se bloquea. Cuando el archivo está bloqueado, puede [Mostrar un mensaje personalizado al usuario para](#educate-protect) indicarle cómo etiquetar el archivo para cargarlo. Al hacerlo, se asegura de que los archivos almacenados en las aplicaciones en la nube cumplan las directivas.

## <a name="educate-users-to-protect-sensitive-files"></a><a name="educate-protect"></a>Instruya a los usuarios para proteger archivos confidenciales

Es importante formar a los usuarios cuando infrinjan una directiva, para que aprendan a cumplir las directivas de la organización. Como cada empresa tiene necesidades y directivas exclusivas, Cloud App Security le permite personalizar los filtros de una directiva y el mensaje que se muestra al usuario cuando se detecta una infracción. Puede proporcionar instrucciones específicas a los usuarios, como proporcionar instrucciones sobre cómo etiquetar correctamente un archivo o cómo inscribir un dispositivo no administrado, para asegurarse de que los archivos se cargan correctamente.

Por ejemplo, si un usuario carga un archivo sin una etiqueta de Azure Information Protection, se puede mostrar un mensaje que explica que el archivo contiene contenido confidencial que requiere una etiqueta adecuada. De forma similar, si un usuario intenta cargar un documento desde un dispositivo no administrado, se puede mostrar un mensaje con instrucciones sobre cómo inscribir el dispositivo o uno que proporciona una explicación más detallada de por qué se debe inscribir el dispositivo.

## <a name="next-steps"></a>Pasos siguientes

>[!div class="nextstepaction"]
> [«ANTERIOR: incorporación e implementación de Control de aplicaciones de acceso condicional para cualquier aplicación»](proxy-deployment-any-app.md)

>[!div class="nextstepaction"]
> [SIGUIENTE: Cómo crear una directiva de acceso »](access-policy-aad.md)

## <a name="see-also"></a>Consulta también

> [!div class="nextstepaction"]
> [Bloqueo de descargas en dispositivos no administrados mediante Azure AD Control de aplicaciones de acceso condicional](use-case-proxy-block-session-aad.md)

[!INCLUDE [Open support ticket](includes/support.md)]  
