---
title: 'Supervisar y proteger archivos en aplicaciones en la nube: Cloud App Security | Microsoft Docs'
description: En este artículo se describe el procedimiento para configurar una directiva de datos para supervisar y controlar los datos y los archivos del uso de aplicaciones en la nube de la organización.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 10/7/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 7c309455b6c7c5a1d46421316eb589038f162726
ms.sourcegitcommit: 288c279a0d2dd62a8ad8d7425c3e9e98857bf5f4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/05/2020
ms.locfileid: "80666485"
---
# <a name="file-policies"></a>Directivas de archivos

*Se aplica a: Microsoft Cloud App Security*

Las directivas de archivo permiten aplicar una amplia gama de procesos automatizados mediante las API del proveedor de la nube. Las directivas se pueden establecer para proporcionar exámenes de cumplimiento continuos, tareas de eDiscovery legales, DLP para el contenido confidencial compartido públicamente y muchos otros casos de uso. Cloud App Security puede supervisar cualquier tipo de archivo en función de más de 20 filtros de metadatos (por ejemplo, el nivel de acceso, el tipo de archivo).

## <a name="supported-file-types"></a>Tipos de archivo compatibles

Los motores de DLP integrados de Cloud App Security realizan la inspección de contenido mediante la extracción de texto de todos los tipos de archivo comunes (más de 100), como Office, Open Office, archivos comprimidos, varios formatos de texto enriquecido, XML, HTML, etc.

## <a name="policies"></a>Directivas

El motor combina tres aspectos en cada directiva:

* Examen de contenido basado en plantillas preestablecidas o expresiones personalizadas.

* Filtros de contexto, incluidos roles de usuario, metadatos de archivos, nivel de uso compartido, integración de grupos organizativos, contexto de colaboración y otros atributos personalizables.

* Acciones automatizadas para el gobierno y la corrección. Para obtener más información, vea [control](control.md).
    > [!NOTE]
    > Solo se garantiza que se aplique la acción de gobierno de la primera Directiva desencadenada. Por ejemplo, si una directiva de archivo ya ha aplicado una etiqueta de AIP a un archivo, una segunda Directiva de archivo no puede aplicarle otra etiqueta de AIP.

Una vez habilitada, la Directiva examina continuamente su entorno en la nube e identifica los archivos que coinciden con el contenido y los filtros de contexto, y aplica las acciones automatizadas solicitadas. Estas directivas detectan y corrigen cualquier infracción de la información en reposo o cuando se crea contenido nuevo. Las directivas se pueden supervisar con alertas en tiempo real o con informes generados por la consola.

A continuación se muestran ejemplos de directivas de archivo que se pueden crear:

* **Archivos compartidos públicamente** : reciba una alerta sobre cualquier archivo en la nube que se comparta públicamente; para ello, seleccione todos los archivos cuyo nivel de uso compartido sea público.

* Nombre **de archivo compartido públicamente que contiene el nombre** de la organización: reciba una alerta sobre cualquier archivo que contenga el nombre de su organización y que se comparta públicamente. Seleccione archivos con un nombre de archivo que contenga el nombre de su organización y que estén compartidos públicamente.

* **Uso compartido con dominios externos** : reciba una alerta sobre cualquier archivo compartido con cuentas que pertenezcan a dominios externos específicos. Por ejemplo, los archivos compartidos con el dominio de un competidor. Seleccione el dominio externo con el que desea limitar el uso compartido.

* **Poner en cuarentena archivos compartidos no modificados durante el último período** : reciba una alerta sobre los archivos compartidos que no se modificaron recientemente para ponerlos en cuarentena o elegir activar una acción automatizada. Excluya todos los archivos privados que no se han modificado durante un intervalo de fechas especificado. En G Suite, puede poner en cuarentena estos archivos, mediante la casilla "archivo de cuarentena" de la página de creación de directivas.

* **Compartir con usuarios no autorizados** : reciba una alerta sobre los archivos compartidos con un grupo de usuarios no autorizado de la organización. Seleccione los usuarios para los que el uso compartido no está autorizado.

* **Extensión de archivo confidencial** : reciba una alerta sobre los archivos con extensiones específicas que puedan ser muy expuestas. Seleccione la extensión específica (por ejemplo, CRT para certificados) o nombre de archivo y excluya los archivos con el nivel de uso compartido privado.

## <a name="create-a-new-file-policy"></a>Crear una nueva Directiva de archivo

Para crear una nueva Directiva de archivo, siga este procedimiento:

1. En la consola de, haga clic en **control** y luego en **directivas**.

1. Haga clic en **crear Directiva** y seleccione Directiva de **archivo** .

1. Asigne un nombre y una descripción a la Directiva, si quiere basarla en una plantilla, para obtener más información sobre las plantillas de Directiva, vea [controlar aplicaciones en la nube con directivas](control-cloud-apps-with-policies.md).

1. Asigne a la Directiva una **gravedad de directiva**. Si ha establecido Cloud App Security para enviarle notificaciones sobre las coincidencias de directivas para un nivel de gravedad de directiva específico, este nivel se usa para determinar si las coincidencias de la Directiva desencadenan una notificación.

1. Dentro de **categoría**, vincule la Directiva al tipo de riesgo más adecuado. Este campo es meramente informativo y ayuda a buscar directivas y alertas específicas más adelante, en función del tipo de riesgo.  Es posible que el riesgo ya esté seleccionado previamente según la categoría para la que eligió crear la Directiva. De forma predeterminada, las directivas de archivo se establecen en DLP.

1. **Cree un filtro para los archivos en los que esta directiva actuará** para establecer qué aplicaciones detectadas desencadenan esta Directiva. Restrinja los filtros de la Directiva hasta que llegue a un conjunto preciso de archivos sobre los que desea actuar. Sea lo más restrictivo posible para evitar falsos positivos. Por ejemplo, si desea quitar permisos públicos, recuerde agregar el filtro **público** , si desea quitar un usuario externo, use el filtro "externo", etc.
   > [!NOTE]
   > Al usar los filtros de Directiva, **contiene** solo búsquedas de palabras completas separadas por comass, puntos, espacios o guiones bajos. Por ejemplo, si busca **malware** o **virus**, busca virus_malware_file. exe, pero no encuentra malwarevirusfile. exe. Si busca **malware. exe**, encontrará todos los archivos con malware o exe en el nombre de archivo, mientras que si busca **"malware. exe"** (con comillas) solo encontrará los archivos que contengan exactamente "malware. exe". **Equals** busca solo la cadena completa, por ejemplo, si busca malware. **exe** , encontrará malware. exe pero no malware. exe. txt.
1. En el primer filtro **aplicar a** , seleccione **todos los archivos excepto las carpetas seleccionadas** o **las carpetas seleccionadas** para Box, SharePoint, Dropbox, OneDrive, donde puede aplicar la Directiva de archivo en todos los archivos de la aplicación o en carpetas específicas. Se le redirigirá para que inicie sesión en la aplicación en la nube y, después, agregue las carpetas correspondientes.

1. En el segundo filtro **aplicar a** , seleccione **todos los propietarios de archivos**, **propietarios de archivos de grupos de usuarios seleccionados** o **todos los propietarios de archivos excepto los grupos seleccionados**. A continuación, seleccione los grupos de usuarios pertinentes para determinar qué usuarios y grupos deben incluirse en la Directiva.

1. Seleccione el **método de inspección de contenido**. Puede seleccionar DLP o [**servicios de clasificación de datos**](content-inspection.md) [**integrados**](content-inspection-built-in.md) . Se recomienda usar los **servicios de clasificación de datos**.

    Una vez habilitada la inspección de contenido, puede optar por usar expresiones preestablecidas o buscar otras expresiones personalizadas.

    Además, puede especificar una expresión regular para excluir un archivo de los resultados. Esta opción es muy útil si tiene un estándar de palabra clave de clasificación interna que desea excluir de la Directiva.

    Puede decidir establecer el número mínimo de infracciones de contenido que desea que coincidan antes de que el archivo se considere una infracción. Por ejemplo, puede elegir 10 Si desea recibir alertas sobre archivos con al menos 10 números de tarjeta de crédito en su contenido.

    Cuando el contenido se compara con la expresión seleccionada, el texto de la infracción se reemplaza por caracteres "X". De forma predeterminada, las infracciones se enmascaran y se muestran en su contexto mostrando 100 caracteres antes y después de la infracción. Los números en el contexto de la expresión se reemplazan por caracteres "#" y nunca se almacenan dentro de Cloud App Security. Puede seleccionar la opción de **desenmascarar los últimos cuatro caracteres de una infracción** para desenmascarar los últimos cuatro caracteres de la infracción. Es necesario establecer qué tipos de datos busca la expresión regular: contenido, metadatos o nombre de archivo. De forma predeterminada, busca en el contenido y los metadatos.

1. Elija las acciones de **gobierno** que quiera que Cloud App Security realizar cuando se detecte una coincidencia.

1. Una vez creada la Directiva, puede verla en la pestaña Directiva de **archivo** . Siempre puede modificar una directiva, calibrar sus filtros o cambiar las acciones automatizadas. La Directiva se habilita automáticamente tras la creación e inicia el análisis de los archivos en la nube inmediatamente.  Tenga especial cuidado cuando establezca acciones de gobierno, lo que podría provocar la pérdida irreversible de permisos de acceso a los archivos. Se recomienda restringir los filtros para representar exactamente los archivos en los que desea actuar y usar varios campos de búsqueda. Cuanto más estrecho sea el filtro, mejor. Para obtener orientación, puede usar el botón **Editar y obtener vista previa de resultados** de la sección filtros.

    ![resultados de edición y vista previa de la Directiva de archivo](media/file-policy-edit-and-preview-results.png)

1. Para ver las coincidencias de la Directiva de archivos, los archivos sospechosos de infringir la Directiva, haga clic en **control** y luego en **directivas**. Filtre los resultados para mostrar solo las directivas de archivo con el filtro de **tipo** en la parte superior. Para obtener más información acerca de las coincidencias de cada Directiva, haga clic en una directiva. Esto muestra los archivos que coinciden ahora con la Directiva. Haga clic en la pestaña **historial** para ver un historial de hasta seis meses de archivos que coincidan con la Directiva.

## <a name="file-policy-reference"></a>Referencia de directiva de archivo

En esta sección se proporcionan detalles de referencia sobre las directivas de, que proporcionan explicaciones para cada tipo de directiva y los campos que se pueden configurar para cada Directiva.

Una **Directiva de archivo** es una directiva basada en API que permite controlar el contenido de la organización en la nube, teniendo en cuenta más de 20 filtros de metadatos de archivo (incluidos el nivel de propietario y de uso compartido) y los resultados de la inspección de contenido. En función de los resultados de la Directiva, se pueden aplicar acciones de gobierno. El motor de inspección de contenido puede ampliarse mediante motores de DLP de terceros, así como soluciones antimalware.

Cada Directiva se compone de las partes siguientes:

* **Filtros de archivo** : permiten crear condiciones granulares basadas en metadatos.

* **Inspección del contenido** : permite restringir la Directiva en función de los resultados del motor DLP. Puede incluir una expresión personalizada o una expresión preestablecida. Las exclusiones se pueden establecer y puede elegir el número de coincidencias. También puede usar anonimización para enmascarar el nombre de usuario.

* **Acciones** : la Directiva proporciona un conjunto de acciones de gobierno que se pueden aplicar automáticamente cuando se encuentran infracciones.  Estas acciones se dividen en acciones de colaboración, acciones de seguridad y acciones de investigación.

* **Extensiones** : la inspección de contenido se puede realizar a través de motores de terceros para mejorar las capacidades de DLP o antimalware.

## <a name="file-queries"></a>Consultas de archivo

Para simplificar aún más la investigación, ahora puede crear consultas personalizadas y guardarlas para su uso posterior.

1. En la página **archivo** , use los filtros como se describió anteriormente para explorar en profundidad las aplicaciones según sea necesario.

1. Una vez que haya terminado de crear la consulta, haga clic en el botón **Guardar como** situado en la esquina superior derecha de los filtros.

1. En el menú emergente **Guardar consulta** , asigne un nombre a la consulta.

1. Para volver a usar esta consulta en el futuro, en **consultas**, desplácese hacia abajo hasta **consultas guardadas** y seleccione la consulta.

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Actividades diarias para proteger el entorno de nube](daily-activities-to-protect-your-cloud-environment.md)

[!INCLUDE [Open support ticket](includes/support.md)]
