---
title: Crear directivas de sesión en Cloud App Security
description: En este artículo se describe el procedimiento para configurar una directiva de sesión de Cloud App Security Control de aplicaciones de acceso condicional obtener una visión profunda de las actividades de sesión de usuario y bloquear las descargas mediante capacidades de proxy inverso.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 11/14/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 06a9b0fc0a732f745d370fe28541b0a753bfe0cc
ms.sourcegitcommit: 4f3883a9e85d0aaf2802b10433b221c3f1838d88
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/13/2020
ms.locfileid: "79285729"
---
# <a name="session-policies"></a>Directivas de sesión

*Se aplica a: Microsoft Cloud App Security*

Microsoft Cloud App Security directivas de sesión permiten la supervisión en tiempo real en el nivel de sesión, lo que le ofrece visibilidad granular sobre las aplicaciones en la nube y la capacidad de realizar diferentes acciones en función de la directiva establecida para una sesión de usuario. En lugar de [permitir o bloquear el acceso por completo](access-policy-aad.md), con el control de sesión puede permitir el acceso mientras supervisa la sesión o limitar determinadas actividades de sesión mediante las capacidades del proxy inverso de control de aplicaciones de acceso condicional.

Por ejemplo, puede decidir que, desde dispositivos no administrados, o para sesiones procedentes de ubicaciones específicas, quiere permitir que el usuario tenga acceso a la aplicación, pero también limitar la descarga de archivos confidenciales o requerir que determinados documentos se protejan tras la descarga. Las directivas de sesión permiten establecer estos controles de sesión de usuario y permitir el acceso y permiten:

* [Supervisar todas las actividades](#monitor-session)
* [Bloquear todas las descargas](#block-download)
* [Bloquear actividades específicas](#block-activities)
* [Proteger archivos durante la descarga](#protect-download)
* [Proteger cargas de archivos confidenciales](#protect-upload)
* [Instruya a los usuarios para proteger archivos confidenciales](#educate-protect)

## <a name="prerequisites-to-using-session-policies"></a>Requisitos previos para el uso de directivas de sesión

* Licencia de Azure AD Premium P1
* Las aplicaciones pertinentes deben [implementarse con control de aplicaciones de acceso condicional](proxy-deployment-aad.md)
* Debe haber una [Directiva de acceso condicional Azure ad](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal) que redirija a los usuarios a Microsoft Cloud App Security, como se describe a continuación.

> [!NOTE]
> Las directivas de sesión también admiten las aplicaciones configuradas con proveedores de identidades distintos de Azure AD. Para obtener más información acerca de este escenario, envíe un correo electrónico a mcaspreview@microsoft.com.

## <a name="create-an-azure-ad-conditional-access-policy"></a>Creación de una directiva de acceso condicional Azure AD

Azure Active Directory las directivas de acceso condicional y las directivas de sesión de Cloud App Security funcionan conjuntamente para examinar cada sesión de usuario y tomar decisiones de directiva para cada aplicación. Para configurar una directiva de acceso condicional en Azure AD, siga este procedimiento:

1. Configure una [Azure ad Directiva de acceso condicional](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal) con asignaciones para un usuario o grupo de usuarios y la aplicación que desea controlar con el control de aplicaciones de acceso condicional.

    > [!NOTE]
    > Esta directiva afectará solo a las aplicaciones que se [implementaron con control de aplicaciones de acceso condicional](proxy-deployment-aad.md) .

2. Para enrutar a los usuarios a Microsoft Cloud App Security, seleccione el **uso de restricciones control de aplicaciones de acceso condicional aplicadas** en la página de la **sesión** .

## <a name="create-a-cloud-app-security-session-policy"></a>Crear una directiva de sesión de Cloud App Security

Para crear una nueva Directiva de sesión, siga este procedimiento:

1. En el portal, seleccione **control** y, después, **directivas**.
1. En la página **directivas** , haga clic en **crear Directiva** y seleccione **Directiva de sesión**.
1. En la ventana **Directiva de sesión** , asigne un nombre a la Directiva, como *bloquear la descarga de documentos confidenciales en Box para usuarios de marketing*.
1. En el campo **tipo de control de sesión** :

    1. Seleccione **supervisar solo** si solo desea supervisar las actividades de los usuarios. Esta selección creará una directiva de monitor solo para las aplicaciones seleccionadas donde se descargarán todos los inicios de sesión, las descargas heurísticas y los tipos de actividad.

    1. Seleccione **controlar la descarga de archivos (con DLP)** si desea supervisar las actividades de los usuarios. Puede realizar acciones adicionales, como bloquear o proteger las descargas de los usuarios.
    1. Seleccione **bloquear actividades** para bloquear actividades específicas, que puede seleccionar mediante el filtro **tipo de actividad** . Todas las actividades de las aplicaciones seleccionadas se supervisarán (y se mostrarán en el registro de actividad). Las actividades específicas que seleccione se bloquearán si selecciona la acción **bloquear** . Las actividades específicas que seleccione generarán alertas si selecciona la acción **probar** y se activan las alertas.
1. En **origen** de la actividad, en la sección **actividades que coinciden con todo lo siguiente** , seleccione los filtros de actividad adicionales que se van a aplicar a la Directiva. Estos filtros pueden incluir las siguientes opciones:

    * **Etiquetas de dispositivo**: Use este filtro para identificar los dispositivos no administrados.

    * **Ubicación**: Use este filtro para identificar ubicaciones desconocidas (y, por tanto, arriesgadas).

    * **Dirección IP**: Use este filtro para filtrar por direcciones IP o usar etiquetas de dirección IP asignadas previamente.

    * **Etiqueta de agente de usuario**: Use este filtro para habilitar la heurística a fin de identificar aplicaciones móviles y de escritorio. Este filtro se puede establecer en es igual a o no es el **cliente nativo**. Este filtro se debe probar con las aplicaciones móviles y de escritorio de cada aplicación en la nube.

    >[!NOTE]
    >Las directivas de sesión no admiten aplicaciones móviles y de escritorio. Las aplicaciones móviles y las aplicaciones de escritorio también pueden bloquearse o permitirse mediante la creación de una directiva de acceso.

1. Si ha seleccionado la opción para **controlar la descarga de archivos (con DLP)** :

    1. En **origen** de la actividad, en la sección **archivos que coinciden con todo lo siguiente** , seleccione los filtros de archivo adicionales que se aplicarán a la Directiva. Estos filtros pueden incluir las siguientes opciones:

        * **Etiqueta de clasificación** : Use este filtro si la organización usa Azure Information Protection y los datos están protegidos por sus etiquetas de clasificación. Puede filtrar los archivos en función de la etiqueta de clasificación que les haya aplicado. Para obtener más información sobre la integración con Azure Information Protection, vea [integración de Azure Information Protection](azip-integration.md).

        * **Nombre de archivo** : Use este filtro para aplicar la Directiva a archivos específicos.
        * **Tipo de archivo** : Use este filtro para aplicar la Directiva a tipos de archivo específicos, por ejemplo, bloquear la descarga de todos los archivos. xls.
    2. En la sección **inspección de contenido** , establezca si desea permitir que el motor DLP examine documentos y contenido de archivos.

    3. En **acciones**, seleccione uno de los siguientes elementos:

        * **Prueba (supervisar todas las actividades)** : establezca esta acción para permitir la descarga explícitamente según los filtros de directiva que haya establecido.

        * **Bloquear (bloquear la descarga de archivos y supervisar todas las actividades)** : establezca esta acción para bloquear explícitamente la descarga según los filtros de directiva que haya establecido. Para obtener más información, consulte [Cómo funciona Block download](#block-download).

        * **Proteger (aplicar etiqueta de clasificación para descargar y supervisar todas las actividades)** : esta opción solo está disponible si seleccionó **controlar la descarga de archivos (con DLP)** en **Directiva de sesión**. Si su organización usa Azure Information Protection, puede establecer una **acción** para aplicar un conjunto de etiquetas de clasificación en Azure Information Protection al archivo. Para obtener más información, vea [Cómo funciona la protección de descargas](#protect-download).

1. Puede **crear una alerta para cada evento coincidente con la gravedad de la Directiva** y establecer un límite de alertas. Seleccione si desea que la alerta sea un correo electrónico, un mensaje de texto o ambos.

## <a name="monitor-session"></a>Supervisar todas las actividades

Cuando se crea una directiva de sesión, cada sesión de usuario que coincida con la Directiva se redirige al control de sesión en lugar de a la aplicación directamente. El usuario verá un aviso de supervisión para indicarle que sus sesiones se están supervisando.

Si no desea que se notifique al usuario que se está supervisando, puede deshabilitar el mensaje de notificación.

1. En el engranaje de configuración, seleccione **Configuración general**.

2. A continuación, en **control de aplicaciones de acceso condicional** seleccione **supervisión** de usuarios y desactive la casilla **notificar a los usuarios** .

Para mantener al usuario dentro de la sesión, Control de aplicaciones de acceso condicional reemplaza todas las direcciones URL pertinentes, scripts de Java y cookies dentro de la sesión de la aplicación con Microsoft Cloud App Security direcciones URL. Por ejemplo, si la aplicación devuelve una página con vínculos cuyos dominios finalizan con myapp.com, Control de aplicaciones de acceso condicional reemplaza los vínculos con dominios que terminan por algo como myapp.com.us.cas.ms. De esta forma, la sesión completa se supervisa mediante Microsoft Cloud App Security.

Control de aplicaciones de acceso condicional registra los registros de tráfico de cada sesión de usuario que se enruta a través de él. Los registros de tráfico incluyen el tiempo, la dirección IP, el agente de usuario, las direcciones URL visitadas y el número de bytes cargados y descargados. Estos registros se analizan y se agrega un informe continuo, **Cloud App Security control de aplicaciones de acceso condicional**, a la lista de Cloud Discovery informes en el panel de Cloud Discovery.

Para exportar estos registros:

1. Vaya al engranaje configuración y haga clic en **control de aplicaciones de acceso condicional**.
2. En el lado derecho de la tabla, haga clic en el botón exportar.

    ![botón exportar](./media/export-button.png)
3. Seleccione el intervalo del informe y haga clic en **exportar**. Este proceso puede tardar algún tiempo.

Para descargar el registro exportado:

1. Cuando el informe esté listo, vaya a **configuración** y después a **informes exportados**.
2. En la tabla, seleccione el informe correspondiente en la lista de **control de aplicaciones de acceso condicional registros de tráfico** y haga clic en descargar.

    ![botón Descargar](./media/download-button.png)

## <a name="block-download"></a>Bloquear todas las descargas

Cuando **bloquear** está establecido como la **acción** que desea realizar en la directiva de sesión de Cloud App Security, control de aplicaciones de acceso condicional impide que un usuario descargue un archivo según los filtros de archivo de la Directiva. Un evento de descarga es reconocido por Microsoft Cloud App Security para cada aplicación cuando un usuario inicia una descarga. Control de aplicaciones de acceso condicional intervienen en tiempo real para evitar que se ejecute. Cuando se recibe la señal de que un usuario ha iniciado una descarga, Control de aplicaciones de acceso condicional devuelve al usuario un mensaje de **descarga restringida** y reemplaza el archivo descargado por un archivo de texto. El mensaje del archivo de texto al usuario se puede configurar y personalizar desde la Directiva de sesión.

## <a name="block-activities"></a>Bloquear actividades específicas

Cuando se establece **actividades de bloqueo** como el **tipo de actividad**, puede seleccionar actividades específicas para bloquearlas en aplicaciones específicas. Todas las actividades de las aplicaciones seleccionadas se supervisarán y se mostrarán en el registro de actividad. Las actividades específicas que seleccione se bloquearán si selecciona la acción **bloquear** . Las actividades específicas que seleccione generarán alertas si selecciona la acción **probar** y se activan las alertas.

**Bloquear actividades específicas** y aplicarlas a grupos específicos para crear un modo completo de solo lectura para su organización.

## <a name="protect-download"></a>Proteger archivos durante la descarga

Seleccione **bloquear actividades** para bloquear actividades específicas, que puede encontrar mediante el filtro **tipo de actividad** . Todas las actividades de las aplicaciones seleccionadas se supervisarán (y se mostrarán en el registro de actividad). Las actividades específicas que seleccione se bloquearán si selecciona la acción **bloquear** . Las actividades específicas que seleccione generarán alertas si selecciona la acción **probar** y se activan las alertas.

Cuando **proteger** se establece como la **acción** que se va a realizar en la directiva de sesión de Cloud App Security, control de aplicaciones de acceso condicional aplica el etiquetado y la protección posterior de un archivo según los filtros de archivo de la Directiva. Las etiquetas se configuran en la consola de **Azure Information Protection y se** debe seleccionar en la etiqueta para que aparezca como una opción en la directiva de Cloud App Security. Cuando se selecciona una etiqueta y se descarga un archivo que cumple los criterios de la Directiva de Cloud App Security, la etiqueta y la protección correspondiente (con permisos) se aplican al archivo durante la descarga. El archivo original permanece tal cual en la aplicación en la nube, mientras que el archivo descargado ahora está protegido. Los usuarios que intenten acceder al archivo deben cumplir los requisitos de permisos determinados por la protección aplicada.

Actualmente, Cloud App Security admite aplicar [etiquetas de clasificación de Azure Information Protection](azip-integration.md) para los siguientes tipos de archivo:

* Word: docm, docx, dotm, dotx
* Excel: XLAM, xlsm, xlsx, xltx
* PowerPoint: potm, potx, ppsx, ppsm, pptm, pptx
* PDF
  > [!NOTE]
  > En el caso de PDF, debe usar etiquetas unificadas.

## <a name="protect-upload"></a>Proteger cargas de archivos confidenciales

Cuando **controlar la carga de archivos (con DLP)** se establece como el **tipo de control de sesión** en la directiva de sesión de Cloud App Security, control de aplicaciones de acceso condicional impide que un usuario cargue un archivo por los filtros de archivos de la Directiva. Cuando se reconoce un evento de carga, Control de aplicaciones de acceso condicional interviene en tiempo real para determinar si el archivo es sensible y necesita protección. Si el archivo tiene datos confidenciales y no tiene una etiqueta adecuada, se bloquea la carga de archivos.

Por ejemplo, puede crear una directiva que examine el contenido de un archivo para determinar si contiene una coincidencia de contenido confidencial, como un número de la seguridad social. Si contiene contenido confidencial y no se etiqueta con una Azure Information Protection etiqueta confidencial, la carga de archivos se bloquea. Cuando el archivo está bloqueado, puede [Mostrar un mensaje personalizado al usuario para](#educate-protect) indicarle cómo etiquetar el archivo para cargarlo. Al hacerlo, se asegura de que los archivos almacenados en las aplicaciones en la nube cumplan las directivas.

## <a name="educate-protect"></a>Instruya a los usuarios para proteger archivos confidenciales

Es importante formar a los usuarios cuando infrinjan una directiva, para que aprendan a cumplir las directivas de la organización. Como cada empresa tiene necesidades y directivas exclusivas, Cloud App Security le permite personalizar los filtros de una directiva y el mensaje que se muestra al usuario cuando se detecta una infracción. Puede proporcionar instrucciones específicas a los usuarios, como proporcionar instrucciones sobre cómo etiquetar correctamente un archivo o cómo inscribir un dispositivo no administrado, para asegurarse de que los archivos se cargan correctamente.

Por ejemplo, si un usuario carga un archivo sin una etiqueta de Azure Information Protection, se puede mostrar un mensaje que explica que el archivo contiene contenido confidencial que requiere una etiqueta adecuada. De forma similar, si un usuario intenta cargar un documento desde un dispositivo no administrado, se puede mostrar un mensaje con instrucciones sobre cómo inscribir el dispositivo o uno que proporciona una explicación más detallada de por qué se debe inscribir el dispositivo.

## <a name="next-steps"></a>Pasos siguientes

>[!div class="nextstepaction"]
> [«ANTERIOR: incorporación e implementación de Control de aplicaciones de acceso condicional para cualquier aplicación»](proxy-deployment-any-app.md)

>[!div class="nextstepaction"]
> [SIGUIENTE: Cómo crear una directiva de acceso»](access-policy-aad.md)

## <a name="see-also"></a>Vea también

> [!div class="nextstepaction"]
> [Bloqueo de descargas en dispositivos no administrados mediante Azure AD Control de aplicaciones de acceso condicional](use-case-proxy-block-session-aad.md)

[!INCLUDE [Open support ticket](includes/support.md)]  
