---
title: Archivos | Microsoft Docs
description: "En este tema de referencia se proporciona información sobre los tipos de archivo y filtros de archivo que usa Cloud App Security."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 10/26/2016
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: cadcd6db-05b2-4974-91fe-cfac3d57aecd
ms.reviewer: reutam
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 400741713d40422a3b1c7680663a572d18e9c692
ms.openlocfilehash: 95dab01c101b6e6171c7985b6571ddb6b4ff5923


---

# <a name="files"></a>Archivos

Se puede filtrar el registro de archivos para que pueda buscar archivos específicos. El filtro básico proporciona excelentes herramientas para empezar a filtrar los archivos.

 ![filtro del registro de archivo básico](media/file-log-filter-basic.png)

Para profundizar en archivos más específicos, puede ampliar el filtro básico haciendo clic en Opciones avanzadas.

 ![filtro de registro de archivo avanzado](media/file-log-filter-advanced.png)
 
###  <a name="a-namefilefiltersa-file-filters"></a><a name="Filefilters"></a> Filtros de archivo 
 
Cloud App Security puede supervisar cualquier tipo de archivo basado en más de 20 filtros de metadatos (por ejemplo, nivel de acceso o tipo de archivo). 
 
Los motores DLP integrados de Cloud App Security inspeccionan el contenido mediante la extracción de texto de los tipos de archivo comunes (PDF, archivos de Office, RTF, HTML, archivos de código, etc.).

A continuación se muestra una lista de los filtros de archivo que se pueden aplicar. La mayoría de los filtros admiten varios valores, así como NOT, para proporcionarle una herramienta muy eficaz para la creación de directivas.  
> [!NOTE] 
> Al usar filtros de directiva, **Contiene** solo buscará palabras completas separadas por comas, puntos, espacios o caracteres de subrayado. Por ejemplo, si busca **malware** o **virus**, encontrará virus_malware_file.exe, pero no encontrará malwarevirusfile.exe. Si busca **malware.exe**, encontrará TODOS los archivos que contengan malware o exe en el nombre de archivo, mientras que si busca **"malware.exe"** (con comillas) solo encontrará los archivos que contengan exactamente "malware.exe".  **Es igual a** solo buscará la cadena completa. Por ejemplo, si busca **malware.exe**, encontrará malware.exe pero no malware.exe.txt. 

-   Nivel de acceso: nivel de acceso de recursos compartidos (público, externo, interno o privado).  Para obtener más información sobre los archivos externos, consulte [General Setup, Set up the portal](getting-started-with-cloud-app-security.md) (Configuración general, Configurar el portal). Los archivos internos son los que se encuentran dentro de los dominios internos que haya establecido en [General setup](General-setup.md) (Configuración general). Los archivos externos son los que están guardados en ubicaciones que no se encuentran dentro de los dominios internos que haya establecido. Los archivos compartidos son los que tienen un nivel de uso compartido superior a privado. Esto incluye uso compartido interno (archivos compartidos dentro de los dominios internos), uso compartido externo (archivos compartidos en dominios que no se muestran en los dominios internos), público con un vínculo (archivos que se pueden compartir con cualquier usuario a través de un vínculo) y público (archivos que se pueden encontrar al realizar búsquedas en Internet). 

> [!NOTE]
>  Cloud App Security controla los archivos compartidos en las aplicaciones de almacenamiento conectadas a usuarios externos de la forma siguiente:
> - **OneDrive:** OneDrive asigna un usuario interno como propietario de cualquier archivo colocado en su OneDrive por un usuario externo. Dado que, a partir de ese momento, se considera que estos archivos pertenecen a la organización, Cloud App Security los examina y les aplica directivas, tal como hace con cualquier otro archivo de OneDrive.
> - **Google Drive:** Google Drive considera que pertenecen al usuario externo y, debido a las restricciones legales relativas a los archivos y los datos que no pertenecen a la organización, Cloud App Security no tiene acceso a estos archivos.
> - **Box:** dado que Box considera que los archivos de propiedad externa son información privada, los administradores globales de Box no pueden ver el contenido de los archivos. Por este motivo, Cloud App Security no tiene acceso a estos archivos. 
> - **Dropbox:** dado que Dropbox considera que los archivos de propiedad externa son información privada, los administradores globales de Dropbox no pueden ver el contenido de los archivos. Por este motivo, Cloud App Security no tiene acceso a estos archivos.

-   Aplicación: solo busca archivos dentro de estas aplicaciones.  
  
-   Colaboradores: incluye/excluye grupos de colaboradores específicos.  
  
    -   Cualquiera del dominio: indica si algún usuario de este dominio tiene acceso al archivo.  
  
    -   Dominio completo: indica si el dominio completo tiene acceso al archivo.  
  
    -   Grupos: indica si un grupo específico tiene acceso al archivo. Se pueden importar grupos de Active Directory o de aplicaciones en la nube, o bien crearse manualmente en el servicio.  
  
    -   Usuarios: conjunto determinado de usuarios que pueden tener acceso al archivo.  
  
-   Creado: hora de creación de archivo. El filtro admite fechas antes y después e intervalos de fechas.  
  
-   Extensión: se centra en extensiones de archivo específicas, por ejemplo, todos los archivos que son ejecutables (exe).  
  
-   Id. de archivo: busca identificadores de archivo específicos. Se trata de una característica avanzada que permite hacer un seguimiento de determinados archivos de gran valor sin depender de su propietario/ubicación/nombre.  
  
-   Nombre de archivo: nombre de archivo o subcadena del nombre tal como se define en la aplicación en la nube, por ejemplo, Todos los archivos con una contraseña en su nombre.  
  
-   Etiqueta de archivo: busca archivos con etiquetas específicas establecidas por Azure Information Protection. Esto requiere la integración con Azure Integration Protection.

-   Tipo de archivo: Cloud App Security toma el tipo MIME recibido del servicio y examina el archivo para determinar el tipo de archivo real. Tenga en cuenta que este examen se aplica a archivos pertinentes para el examen de datos (documentos, imágenes, presentaciones, hojas de cálculo, archivos de texto y archivos de almacenamiento o ZIP). El filtro funciona por tipo de archivo/carpeta, por ejemplo, Todas las carpetas que son… o Todos los archivos de hoja de cálculo que son...


 ![filtros en papelera de archivo de directiva](./media/policy_file-filters-trash.png "policy_file filters trash")  

  
-   En la papelera: excluye/incluye archivos que se encuentran en la carpeta de la papelera. Estos archivos siguen pudiendo compartirse y suponen un riesgo.  
  
-   Última modificación: hora de modificación del archivo. El filtro admite valores de fecha Antes de/Después de, intervalos de fechas y expresiones de tiempo relativo, por ejemplo, Todos los archivos que no se han modificado en los últimos 6 meses.  

-   Directiva coincidente: archivos que coinciden gracias a una directiva de Cloud App Security.

-   Tipo MIME: comprobación del tipo MIME del archivo. Acepta el texto sin formato.  
  
-   Propietario: incluye/excluye propietarios de archivo específicos, por ejemplo, Realizar un seguimiento de todos los archivos compartidos por rogue_employee_#100.  
  
-   UO del propietario: incluye/excluye los propietarios de archivos que pertenecen a determinado grupo de la organización, por ejemplo, Todos los archivos públicos excepto los compartidos por EMEA_marketing.  
  
-   Carpeta principal: incluye/excluye en función de la carpeta principal, por ejemplo, Todos los archivos compartidos públicamente excepto los archivos de esta carpeta.  
  
-   En cuarentena: indica si el servicio ha puesto el archivo en cuarentena, por ejemplo, Mostrar todos los archivos que estén en cuarentena.  
  
También puede establecer que la directiva se ejecute en archivos específicos. Para ello, establezca el filtro **Aplicar a** en Todos los archivos, Carpetas seleccionadas o Todos los archivos excepto las carpetas seleccionadas y, después, seleccione los archivos o las carpetas pertinentes.  
  
![filtro Aplicar a](./media/apply-to-filter.png "apply to filter")  
  
### <a name="governance-actions"></a>Acciones de gobierno  
  
-   Notificaciones  
  
    -   Alertas: las alertas pueden desencadenarse en el sistema y propagarse a través de mensajes de correo electrónico y de texto, según el nivel de gravedad.  
  
    -   Notificación de correo electrónico de usuario: es posible personalizar los mensajes de correo electrónico y enviarlos a todos los propietarios de archivos infractores.  
  
    -   Administrador de CC: según la integración de directorios del usuario, también se pueden enviar notificaciones de correo electrónico al administrador de la persona que haya infringido una directiva.  
  
-   Enviar una notificación a usuarios concretos: lista específica de direcciones de correo electrónico que recibirán las notificaciones.  
  
-   Enviar una notificación al último editor del archivo: se envían notificaciones a la última persona que ha modificado el archivo.  
  
-   Acciones de gobierno en aplicaciones  
  
     Se pueden aplicar acciones pormenorizadas por aplicación. Las acciones específicas varían según la terminología de la aplicación.  
  
    -   Cambio del uso compartido  
  
        -   Quitar el uso compartido público: permite el acceso únicamente a los colaboradores con nombre, por ejemplo, Quitar el acceso público a Google Apps y Quitar el vínculo compartido directo a Box.  
  
        -   Quitar usuarios externos: permite el acceso únicamente a los usuarios de la empresa.  
  
        -   Convertir en privado: solo el propietario puede tener acceso al archivo. Se quitan todos los recursos compartidos.  
  
        -   Quitar un colaborador: quita un colaborador específico del archivo.  
  
    -   Cuarentena  
  
        -   Poner en cuarentena de usuario: permite el autoservicio moviendo el archivo a una carpeta de cuarentena controlada por el usuario.  
  
        -   Poner en cuarentena de administrador: el archivo se pone en cuarentena en la unidad del administrador y este tiene que aprobarlo.  
  
-   Enviar a la papelera: el archivo se mueve a la carpeta de la papelera.
  
![alertas de crear directiva](./media/policy_create-alerts.png "policy_create alerts")  
  
 
## <a name="see-also"></a>Consulte también  
[Actividades diarias para proteger el entorno de nube](daily-activities-to-protect-your-cloud-environment.md)   
[Para obtener soporte técnico, visite la página de soporte técnico asistido de Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Los clientes Premier también pueden elegir Cloud App Security directamente desde el Portal Premier.](https://premier.microsoft.com/)  
  
  


<!--HONumber=Oct16_HO5-->


