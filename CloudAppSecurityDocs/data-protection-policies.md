---
title: 'Supervisión y protección de archivos en aplicaciones en la nube: Cloud App Security'
description: En este artículo se describe el procedimiento para configurar una directiva de datos para supervisar y controlar los datos y los archivos durante el uso de aplicaciones en la nube de la organización.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 10/7/2019
ms.topic: how-to
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 6d2bcb47b7ac8876de1cceaba9b50c678925974f
ms.sourcegitcommit: 29a8e66c665f51d831516924ae4d9d8047b39276
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2020
ms.locfileid: "88780382"
---
# <a name="file-policies"></a>Directivas de archivos

*Se aplica a: Microsoft Cloud App Security*

Las directivas de archivo permiten aplicar una amplia gama de procesos automatizados mediante las API del proveedor de la nube. Las directivas se pueden establecer para proporcionar análisis de conformidad constantes, tareas de exhibición de documentos electrónicos legales, DLP para el contenido confidencial compartido públicamente y otros muchos casos de uso. Cloud App Security puede supervisar cualquier tipo de archivo basado en más de 20 filtros de metadatos (por ejemplo, nivel de acceso o tipo de archivo).

## <a name="supported-file-types"></a>Tipos de archivo admitidos

Los motores de DLP integrados de Cloud App Security realizan la inspección de contenido mediante la extracción de texto de todos los tipos de archivo comunes (más de 100), como Office, Open Office, archivos comprimidos, varios formatos de texto enriquecido, XML, HTML, etc.

## <a name="policies"></a>Directivas

El motor combina tres aspectos en cada directiva:

* Análisis de contenido basado en plantillas preestablecidas o expresiones personalizadas.

* Filtros de contexto, incluidos roles de usuario, metadatos de archivos, nivel de uso compartido, integración de grupos organizativos, contexto de colaboración y otros atributos personalizables.

* Acciones automatizadas de gobernanza y corrección. Para obtener más información, vea [Control](control.md).
    > [!NOTE]
    > Solo se garantiza que se aplique la acción de gobierno de la primera Directiva desencadenada. Por ejemplo, si una directiva de archivo ya ha aplicado una etiqueta de Azure Information Protection (AIP) a un archivo, una segunda Directiva de archivo no puede aplicarle otra etiqueta de AIP.

Una vez habilitada, la directiva analizará continuamente su entorno en la nube e identificará los archivos que coincidan con los filtros de contenido y el contexto y, después, aplicará las acciones automatizadas solicitadas. Estas directivas detectarán y corregirán cualquier infracción de la información en reposo o al crear contenido. Las directivas se pueden supervisar con alertas en tiempo real o con informes generados por la consola.

Estos son algunos ejemplos de las directivas de archivo que se pueden crear:

* **Archivos compartidos públicamente**: reciba una alerta sobre cualquier archivo en la nube que se comparta públicamente; para ello, seleccione todos los archivos cuyo nivel de uso compartido sea público.

* Nombre **de archivo compartido públicamente que contiene el nombre** de la organización: reciba una alerta sobre cualquier archivo que contenga el nombre de su organización y que se comparta públicamente. Seleccione los archivos compartidos públicamente cuyo nombre de archivo contenga el nombre de la organización.

* **Sharing with external domains** (Uso compartido con dominios externos): reciba una alerta sobre cualquier archivo compartido con cuentas propiedad de determinados dominios externos. Por ejemplo, los archivos compartidos con el dominio de un competidor. Seleccione el dominio externo con el que quiera limitar el uso compartido.

* **Quarantine shared files not modified during the last period** (Archivos compartidos en cuarentena no modificados durante el último período): reciba una alerta sobre los archivos compartidos que nadie haya modificado recientemente, para ponerlos en cuarentena u optar por activar una acción automatizada. Excluya todos los archivos privados que no se han modificado durante un intervalo de fechas especificado. En G Suite, puede poner en cuarentena estos archivos, mediante la casilla "archivo de cuarentena" de la página de creación de directivas.

* **Sharing with unauthorized users** (Uso compartido con usuarios no autorizados): reciba una alerta sobre los archivos que se comparten con un grupo de usuarios no autorizado de la organización. Seleccione los usuarios para los que el uso compartido no está autorizado.

* **Sensitive file extension** (Extensión de archivo confidencial): reciba una alerta sobre los archivos con extensiones específicas que puedan tener un nivel de exposición muy elevado. Seleccione el nombre de archivo o la extensión particular (por ejemplo, crt en el caso de los certificados) y excluya los archivos que tengan un nivel de uso compartido privado.

## <a name="create-a-new-file-policy"></a>Crear una directiva de archivo

Haga lo siguiente para crear una directiva de archivo:

1. En la consola, haga clic en **Control**, seguido de **Directivas**.

1. Haga clic en **crear Directiva** y seleccione Directiva de **archivo** .

1. Asigne un nombre y una descripción a la directiva. Si quiere, puede basarla en una plantilla. Para obtener más información sobre las plantillas de directiva, vea [Controlar aplicaciones en la nube con directivas](control-cloud-apps-with-policies.md).

1. Asigne a la directiva una **gravedad**. Si ha configurado Cloud App Security para que le envíe notificaciones cuando se producen coincidencias de directivas para un nivel de gravedad de política específico, este nivel se usará para determinar si la coincidencia de la directiva desencadenará una notificación o no.

1. Dentro de **Categoría**, vincule la directiva al tipo de riesgo más adecuado. Este campo es meramente informativo y solo sirve para encontrar más fácilmente directivas específicas y las consiguientes alertas, según el tipo de riesgo.  Puede que el riesgo ya esté seleccionado previamente según la categoría para la que eligió crear la directiva. Las directivas de archivo están configuradas como DLP de forma predeterminada.

1. **Cree un filtro para los archivos sobre los que esta directiva actuará** para definir qué aplicaciones activarán esta directiva. Limite los filtros de directiva hasta conseguir exactamente el conjunto de archivos sobre los que quiere actuar. Sea lo más restrictivo posible para evitar falsos positivos. Por ejemplo, si desea quitar permisos públicos, recuerde agregar el filtro **público** , si desea quitar un usuario externo, use el filtro "externo", etc.
   > [!NOTE]
   > Al usar filtros de directiva, **Contiene** solo buscará palabras completas separadas por comas, puntos, espacios o caracteres de subrayado. Por ejemplo, si busca **malware** o **virus**, encontrará virus_malware_file.exe, pero no encontrará malwarevirusfile.exe. Si busca **malware.exe**, encontrará todos los archivos con malware o exe en el nombre de archivo, mientras que si busca **"malware.exe"** (con las comillas) solo encontrará los archivos que contengan exactamente "malware.exe". **Es igual a** solo buscará la cadena completa. Por ejemplo, si busca **malware.exe**, encontrará malware.exe pero no malware.exe.txt.
1. En el primer filtro **Aplicar a**, seleccione **todos los archivos excepto las carpetas seleccionadas** o las **carpetas seleccionadas** para Box, SharePoint, Dropbox y OneDrive, donde puede aplicar la directiva en todos los archivos de la aplicación o en carpetas específicas. Se le redirigirá para que inicie sesión en la aplicación en la nube y agregue las carpetas relevantes.

1. En el segundo filtro **Aplicar a**, seleccione **todos los propietarios de archivos**, **los propietarios de archivos de los grupos seleccionados** o **todos los propietarios de archivos excepto los grupos seleccionados**. Después, seleccione los grupos de usuarios pertinentes para determinar qué usuarios y grupos deben incluirse en la directiva.

1. Seleccione el **método de inspección de contenido**. Puede seleccionar un [**DLP integrado**](content-inspection-built-in.md) o uno de los [**Servicios de clasificación de datos**](content-inspection.md). Se recomienda usar los **Servicios de clasificación de datos**.

    Una vez habilitada la inspección de contenido, puede optar entre usar expresiones preestablecidas o buscar otras expresiones personalizadas.

    Además, puede especificar una expresión regular para excluir un archivo de los resultados. Esta opción es muy útil si tiene un estándar de palabra clave de clasificación interna que quiera excluir de la directiva.

    También puede decidir cuál es el número mínimo de infracciones de contenido que debe producirse antes de que el archivo se considere una infracción. Por ejemplo, puede elegir 10 si quiere recibir alertas sobre archivos con al menos 10 números de tarjeta de crédito en su contenido.

    Cuando el contenido se compare con la expresión seleccionada, el texto de la infracción se reemplazará por caracteres "X". De manera predeterminada, las infracciones se enmascaran y se muestran en su contexto mostrando 100 caracteres antes y después de la infracción. Los números en el contexto de la expresión se reemplazan por caracteres "#" y nunca se almacenan dentro de Cloud App Security. Puede seleccionar la opción de **quitar la máscara de los últimos cuatro caracteres de una infracción** para mostrarlos. Es necesario establecer qué tipos de datos buscará la expresión regular: contenido, metadatos o nombre de archivo. De forma predeterminada, buscará el contenido y los metadatos.

1. Elija las acciones de **gobernanza** que quiera que Cloud App Security lleve a cabo cuando detecte una coincidencia.

1. Una vez creada la Directiva, puede verla en la pestaña Directiva de **archivo** . Siempre puede modificar una directiva, calibrar sus filtros o cambiar las acciones automatizadas. La directiva se habilita automáticamente tras crearse e iniciará inmediatamente el análisis de los archivos en la nube.  Tenga especial cuidado al definir acciones de gobernanza, ya que podrían provocar la pérdida irreversible de permisos de acceso a los archivos. Se recomienda restringir los filtros para representar exactamente los archivos en los que quiere actuar por medio de varios campos de búsqueda. Cuanto más restringidos sean los filtros, mejor. Para obtener orientación, puede utilizar el botón **Editar y obtener vista previa de resultados** de la sección Filtros.

    ![editar la directiva de archivo y obtener una vista previa de resultados](media/file-policy-edit-and-preview-results.png)

1. Para ver coincidencias con la directiva de archivo, es decir, archivos sospechosos de infringir la directiva, haga clic en **Control** y, después, en **Directivas**. Filtre los resultados para mostrar solo las directivas de archivo con el filtro **Tipo** en la parte superior. Para obtener más información sobre las coincidencias de cada directiva, haga clic en una directiva. De este modo, se muestran los archivos que "coinciden ahora" con la directiva. Haga clic en la pestaña **Historial** para ver el historial de los seis meses anteriores con los archivos que coincidieron con la directiva.

## <a name="file-policy-reference"></a>Referencia de directiva de archivo

En esta sección se proporciona información de referencia sobre directivas, se ofrecen explicaciones sobre cada tipo de directiva y se detallan los campos que se pueden configurar para cada directiva.

Una **directiva de archivo** es una directiva basada en API que permite controlar contenido en la nube de la organización. Para ello, se tienen en cuenta más de 20 filtros de metadatos de archivo (incluido el nivel de propietario y de uso compartido) y los resultados de inspección de contenido. En función de los resultados de la directiva, se pueden aplicar acciones de gobernanza. El motor de inspección de contenido puede ampliarse mediante motores de DLP de terceros, así como soluciones antimalware.

Cada directiva se compone de las siguientes partes:

* **Filtros de archivo** : permiten crear condiciones granulares basadas en metadatos.

* **Inspección del contenido**: permite restringir la directiva en función de los resultados del motor DLP. Puede incluir una expresión personalizada o una expresión preestablecida. Se pueden establecer exclusiones y puede elegir el número de coincidencias. También puede usar el anonimato para enmascarar el nombre de usuario.

* **Acciones**: la directiva proporciona un conjunto de acciones de gobernanza que se pueden aplicar automáticamente cuando se detectan infracciones.  Estas acciones se dividen en acciones de colaboración, de seguridad y de investigación.

* **Extensiones**: es posible realizar una inspección del contenido mediante motores de terceros para DLP mejorada o funcionalidades antimalware.

## <a name="file-queries"></a>Consultas de archivo

Para que la investigación sea incluso más sencilla, ahora puede crear consultas personalizadas y guardarlas para usar más adelante.

1. En la página **archivo** , use los filtros como se describió anteriormente para explorar en profundidad las aplicaciones según sea necesario.

1. Una vez que haya terminado de compilar la consulta, haga clic en el botón **Guardar como** situado en la esquina superior derecha de los filtros.

1. En el elemento emergente **Guardar consulta** , asigne un nombre a la consulta.

1. Para volver a usar esta consulta en el futuro, en **Consultas**, desplácese hacia abajo hasta **Consultas guardadas** y seleccione la consulta.

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Actividades diarias para proteger el entorno de nube](daily-activities-to-protect-your-cloud-environment.md)

[!INCLUDE [Open support ticket](includes/support.md)]
