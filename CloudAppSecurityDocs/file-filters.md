---
title: Descripción de los datos y los filtros de archivo disponibles en Cloud App Security
description: En este artículo de referencia se proporciona información sobre los tipos de archivo y filtros de archivo que usa Cloud App Security.
ms.date: 01/11/2021
ms.topic: how-to
ms.openlocfilehash: 381710d324dcb3e118a729d7c78c852c61351fbd
ms.sourcegitcommit: 04d8731dce2a3b3b2d10bbfa27e5dc80b0a3e0f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/11/2021
ms.locfileid: "98062754"
---
# <a name="files"></a>Files

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Para proporcionar protección de datos, Microsoft Cloud App Security le ofrece visibilidad de todos los archivos de las aplicaciones conectadas. Después de conectar Microsoft Cloud App Security a una aplicación mediante el conector de aplicaciones, Microsoft Cloud App Security examina todos los archivos, como, por ejemplo, todos los archivos almacenados en OneDrive y Salesforce. A continuación, Cloud App Security vuelve a examinar cada archivo cada vez que se modifica: la modificación puede realizarse en el contenido, los metadatos o los permisos de uso compartido. Los tiempos de examen dependen del número de archivos almacenados en la aplicación. También puede usar la página **Archivos** para filtrar archivos e investigar qué tipo de datos se guarda en las aplicaciones en la nube.

## <a name="file-filter-examples"></a>Ejemplos de filtros de archivo

Por ejemplo, use la página **Archivos** para proteger de forma externa archivos compartidos etiquetados como **confidenciales** de la siguiente manera: después de conectar una aplicación a Cloud App Security, intégrela con Azure Information Protection. Luego, en la página **Archivos**, filtre los archivos etiquetados con **confidencial** y excluya su dominio en el filtro **Colaboradores**. Si ve que hay archivos confidenciales compartidos fuera de la organización, puede crear una directiva de archivo para detectarlos. Puede aplicar acciones de gobernanza automáticas a estos archivos, tales como **Quitar colaboradores externos** y **Enviar un resumen de coincidencias de directiva al propietario del archivo** para evitar la pérdida de datos a la organización.

![Filtro de archivos confidenciales](media/file-filter-confidential.png)

Este es otro ejemplo de cómo puede usar la página **Archivos**. Asegúrese de que nadie en la organización está compartiendo de forma pública o externa archivos que no se han modificado en los últimos seis meses: conecte una aplicación a Cloud App Security y vaya a la página **Archivos**. Filtre los archivos cuyo nivel de acceso es **Externo** o **Público**, y establezca la fecha de **Última modificación** en hace seis meses. Cree una directiva de archivo que detecte estos archivos obsoletos públicos haciendo clic en **Nueva directiva de búsqueda**. Aplique acciones de gobernanza automáticas, como **Quitar usuarios externos**, para evitar la pérdida de datos a la organización.

![Filtro de archivo obsoleto externo](media/file-example-stale-external.png)

El filtro básico proporciona excelentes herramientas para empezar a filtrar los archivos.

![filtro del registro de archivo básico](media/file-log-filter-basic-1.png)

Para profundizar en archivos más específicos, puede ampliar el filtro básico haciendo clic en Opciones avanzadas.

![filtro de registro de archivo avanzado](media/file-log-filter-advanced-1.png)

## <a name="file-filters"></a><a name="Filefilters"></a> Filtros de archivo

Cloud App Security puede supervisar cualquier tipo de archivo basado en más de 20 filtros de metadatos (por ejemplo, nivel de acceso o tipo de archivo).

Los motores DLP integrados de Cloud App Security inspeccionan el contenido mediante la extracción de texto de los tipos de archivo comunes. Algunos de los tipos de archivo incluidos son PDF, archivos de Office, RTF, HTML y archivos de código.

A continuación se muestra una lista de los filtros de archivo que se pueden aplicar. La mayoría de los filtros admiten varios valores, así como NOT, para proporcionar una herramienta eficaz para la creación de directivas.

> [!NOTE]
> Al usar filtros de directiva de archivo, **Contiene** solo buscará **palabras completas** separadas por comas, puntos, espacios o caracteres de subrayado.
>
> - Los espacios entre palabras funcionan como el operador OR. Por ejemplo, si busca **malware** **virus**, se encontrarán todos los archivos con la palabra malware o virus en el nombre, como malware-virus.exe o virus.exe.
> - Si quiere buscar una cadena, escriba las palabras entre comillas. Se tratarán como si usaran el operador AND. Por ejemplo, si busca **"malware"** **"virus"**, se encontrará virus_malware_file.exe, pero no se encontrarán ni malwarevirus.exe ni malware.exe. En cambio, buscará la cadena exacta. Si busca **"malware virus"** no encontrará **"virus"** ni **"virus_malware"**.
>
> **Es igual a** solo buscará la cadena completa. Por ejemplo, si busca **malware.exe**, encontrará malware.exe pero no malware.exe.txt.

- **Nivel de acceso** : nivel de acceso de uso compartido; público, externo, interno o privado.  Para obtener más información sobre los archivos externos, consulte el tema sobre la [configuración general del portal](getting-started-with-cloud-app-security.md).

    - **Interno**: cualquier archivo de los dominios internos que haya definido en [Configuración general](General-setup.md).
    - **Externo**: cualquier archivo guardado en ubicaciones que no se encuentran dentro de los dominios internos que haya establecido.
    - **Compartido**: los archivos que tienen un uso compartido de nivel por encima de privado. Compartido incluye:
        - Uso compartido interno: archivos compartidos dentro de los dominios internos.
        - Uso compartido externo: archivos compartidos en dominios que no aparecen en los dominios internos.
        - Público con un vínculo: archivos que pueden compartirse con cualquier persona a través de un vínculo.
        - Público: archivos que pueden encontrarse al realizar búsquedas en Internet.

      > [!NOTE]
      > Cloud App Security controla los archivos compartidos en las aplicaciones de almacenamiento conectadas a usuarios externos de la forma siguiente:
      >
      > - **OneDrive:** OneDrive asigna un usuario interno como propietario de cualquier archivo colocado en su OneDrive por un usuario externo. Dado que, a partir de ese momento, se considera que estos archivos pertenecen a la organización, Cloud App Security los examina y les aplica directivas, tal como hace con cualquier otro archivo de OneDrive.
      > - **Google Drive:** Google Drive considera que pertenecen al usuario externo y, debido a las restricciones legales relativas a los archivos y los datos que no pertenecen a la organización, Cloud App Security no tiene acceso a estos archivos.
      > - **Box:** dado que Box considera que los archivos de propiedad externa son información privada, los administradores globales de Box no pueden ver el contenido de los archivos. Por este motivo, Cloud App Security no tiene acceso a estos archivos.
      > - **Dropbox:** dado que Dropbox considera que los archivos de propiedad externa son información privada, los administradores globales de Dropbox no pueden ver el contenido de los archivos. Por este motivo, Cloud App Security no tiene acceso a estos archivos.

- **Aplicación** : busca solo archivos dentro de estas aplicaciones.

- **Colaboradores** : incluye o excluye grupos de colaboradores específicos.

    - **Cualquiera del dominio** : Si algún usuario de este dominio tiene acceso al archivo.

    - **Toda la organización** : si toda la organización tiene acceso al archivo.

    - **Grupos** : Si un grupo específico tiene acceso al archivo. Se pueden importar grupos de Active Directory o de aplicaciones en la nube, o bien crearse manualmente en el servicio.

    - **Usuarios** : cierto conjunto de usuarios que pueden tener acceso al archivo.

- **Creado** : hora de creación del archivo. El filtro admite fechas antes o después, e intervalos de fechas.

- **Extensión**: se centra en extensiones de archivo específicas. Por ejemplo, todos los archivos que son ejecutables (exe).

- **Id. de archivo**: busca identificadores de archivo específicos. Se trata de una característica avanzada que permite hacer un seguimiento de determinados archivos de gran valor sin depender de su propietario, ubicación o nombre.

- **Nombre de archivo** : nombre de archivo o subcadena del nombre tal como se define en la aplicación en la nube, por ejemplo, todos los archivos con una contraseña en su nombre.

- **Etiqueta de clasificación** : busca archivos con etiquetas específicas establecidas. Las etiquetas son las siguientes:
    - **Etiquetas de Azure Information Protection**: requiere la integración con Azure Integration Protection.
    - **Etiquetas de Cloud App Security**: proporciona más información sobre los archivos que examina. Para cada archivo examinado por la DLP de Cloud App Security, puede saber si ha bloqueado la inspección porque el archivo está dañado o cifrado. Por ejemplo, puede configurar directivas para que le alerten y pongan en cuarentena archivos protegidos con contraseña que se comparten externamente.
        - **Cifrado con Azure RMS**: archivos cuyo contenido no se ha inspeccionado porque tienen establecido un cifrado de Azure RMS.
        - **Contraseña cifrada** : archivos cuyo contenido no se ha inspeccionado porque están protegidos por contraseña por el usuario.
        - **Archivo dañado**: archivos cuyo contenido no se ha inspeccionado porque no se ha podido leer su contenido.

- **Tipo de archivo** : Cloud App Security toma el tipo MIME recibido (vea la tabla) del servicio y examina el archivo para determinar el tipo de archivo real. Este examen se aplica a archivos pertinentes para el examen de datos (documentos, imágenes, presentaciones, hojas de cálculo, texto y archivos de almacenamiento o ZIP). El filtro funciona por tipo de archivo o carpeta. Por ejemplo, Todas las carpetas que son… o Todos los archivos de hoja de cálculo que son...

    | Tipo de MIME | Tipo de archivo |
    |--|--|
    | -Application/vnd.openxmlformats-officedocument.wordprocessingml.document<br />-Application/vnd.ms-word.document. macroEnabled. 12<br />-Application/MSWord<br />-Application/vnd. oasis. opendocument. Text<br />-Application/vnd. stardivision. Writer<br />-Application/vnd. stardivision. Writer-global<br />-Application/vnd.sun.xml. Writer<br />-Application/vnd. stardivision. Math<br />-Application/vnd. stardivision. Chart<br />-application/x-StarWriter<br />-application/x-stardraw<br />-application/x-starmath<br />-application/x-StarChart<br />-Application/vnd.google-apps.document<br />-Application/vnd. Google-Apps. Kix<br />-application/pdf<br />-application/x-pdf<br />-Application/vnd. Box. webdoc<br />-Application/vnd. Box. boxnote<br />-Application/vnd.jive.document<br />-texto/RTF<br />-Application/RTF | Documento |
    | -Application/vnd. oasis. opendocument. Image<br />-Application/vnd. Google-Apps. Photo<br />- **empieza por:** imagen/ | Imagen |
    | -Application/vnd. openxmlformats. presentationml. Presentation<br />-Application/vnd. MS-PowerPoint. template. macroEnabled. 12<br />-Application/MSPowerPoint<br />-aplicación/PowerPoint<br />-Application/vnd. MS-PowerPoint<br />-application/x-MSPowerPoint<br />-Application/MSPowerPoint<br />-Application/vnd. MS-PowerPoint<br />-Application/vnd. oasis. opendocument. Presentation<br />-Application/vnd.sun.xml. impress<br />-Application/vnd. stardivision. impress<br />-application/x-starimpress<br />-Application/vnd. Google-Apps. Presentation | Presentación |
    | -Application/vnd. openxmlformats. SpreadsheetML. sheet<br />-Application/vnd. ms. sheet. macroEnabled. 12<br />-aplicación/Excel<br />-Application/vnd. ms<br />-application/x-Excel<br />-application/x-MSExcel<br />-Application/vnd. oasis. opendocument. Spreadsheet<br />-Application/vnd.sun.xml. Calc<br />-Application/vnd. stardivision. Calc<br />-application/x-StarCalc<br />-Application/vnd. Google-Apps. Spreadsheet | Hoja de cálculo |
    | - **empieza por:** texto/ | Texto |
    | Todos los demás tipos MIME de archivo | Otros |

    ![policy_file tipo de filtros](media/policy_file-filters-type.png)

- **En la papelera** : incluir o excluir archivos en la carpeta de la papelera. Estos archivos siguen pudiendo compartirse y suponen un riesgo.

    ![filtros en papelera de archivo de directiva](media/policy_file-filters-trash.png)

- **Última** modificación: hora de modificación del archivo. El filtro admite fechas anteriores y posteriores, intervalos de fechas y expresiones de tiempo relativo. Por ejemplo, todos los archivos que no se han modificado en los últimos seis meses.

- **Directiva coincidente** : archivos que coinciden con una directiva de Cloud App Security activa.

- **Tipo MIME** : comprobación del tipo MIME del archivo, acepta texto libre.

- **Propietario**: incluye o excluye propietarios de archivos específicos. Por ejemplo, realizar el seguimiento de todos los archivos compartidos por empleado_rebelde_ #100.

- **UO del propietario**: incluye o excluye los propietarios de archivos que pertenecen a determinados grupos organizativos. Por ejemplo, todos los archivos públicos excepto los archivos compartidos por EMEA_marketing. Solo se aplica a los archivos almacenados en Google Drive.

- **Carpeta primaria**: incluye o excluye en función de la carpeta principal. Por ejemplo, todos los archivos compartidos públicamente excepto los archivos de esta carpeta.

- **En cuarentena** : es el archivo en cuarentena por el servicio; por ejemplo, se muestran todos los archivos que están en cuarentena.

También puede establecer la directiva para que se ejecute en determinados archivos estableciendo el filtro **Se aplica a**. Filtre por **Todos los archivos**, **Carpetas seleccionadas**, o bien **Todos los archivos excepto las carpetas seleccionadas**. Después, seleccione los archivos o carpetas que son relevantes.

![filtro Aplicar a](media/apply-to-filter.png "filtro Aplicar a")
<!--
>[!NOTE]
> If at any point you want to clear the filters, you can do so by clicking the clear filters icon ![clear filters icon](media/clear-filters.png).
-->

## <a name="authorizing-files"></a>Autorización de archivos

Una vez que Cloud App Security ha identificado los archivos como un riesgo de malware o DLP, recomendamos que investigue los archivos. Si determina que los archivos son seguros, puede autorizarlos. La autorización de un archivo quita el informe de detección de malware y suprime futuras coincidencias en este archivo.

### <a name="to-authorize-files"></a>Para autorizar archivos

1. En Cloud App Security, haga clic en **control** y luego en **directivas**.
1. En la lista de directivas, en la fila en la que aparece la Directiva que desencadenó la investigación, en la columna **recuento** , haga clic en el vínculo coincidencias.

    > [!TIP]
    > Puede filtrar la lista de directivas por tipo. En la tabla siguiente se enumeran, por tipo de riesgo, el tipo de filtro que se va a usar:
    >
    > | Tipo de riesgo | Tipo de filtro |
    > | --- | --- |
    > | DLP | Directiva de archivo |
    > | Malware | Directiva de detección de malware |

1. En la lista de archivos coincidentes, en la fila en la que aparece el archivo en investigación, haga clic en **autorizar**.

## <a name="working-with-the-file-drawer"></a>Uso del cajón de archivos

Puede ver más información sobre un archivo si hace clic en él en el registro de archivos. Al hacer clic en se abre el **cajón de archivos** que proporciona las siguientes acciones adicionales que puede realizar en el archivo:

- **Dirección URL**: le lleva a la ubicación del archivo.
- **Identificadores de archivos**: abre una ventana emergente con los datos sin procesar sobre el archivo, como su id. o las claves de cifrado.
- **Propietario**: vea la página de usuario del propietario del archivo.
- **Directivas con coincidencias**: vea una lista de las directivas que coinciden con el archivo.
- **Etiqueta de clasificación**: vea una lista de etiquetas de clasificación de Azure Information Protection que se hayan encontrado en este archivo. A continuación, podrá filtrar todos los archivos que coincidan con esta etiqueta.

Los campos del cajón de archivos proporcionan vínculos contextuales a archivos adicionales y exploran en profundidad lo que desea realizar desde el cajón directamente. Por ejemplo, si mueve el cursor junto al campo **propietario** , puede usar el icono "Agregar a filtro" ![ Agregar a filtro ](media/add-to-filter-icon.png) para agregar el propietario inmediatamente al filtro de la página actual. También puede utilizar el icono de engranaje de configuración ![icono de configuración](media/contextual-settings-icon.png) que aparece para llegar directamente a la página de configuración necesaria para modificar la configuración de uno de los campos, como **Etiquetas de clasificación**.

![Cajón de archivos](media/file-drawer.png "Cajón de archivos")

Para obtener una lista de las acciones de gobernanza disponibles, consulte [Acciones de gobernanza de archivos](governance-actions.md#file-governance-actions).

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Actividades diarias para proteger el entorno de nube](daily-activities-to-protect-your-cloud-environment.md)

[!INCLUDE [Open support ticket](includes/support.md)]