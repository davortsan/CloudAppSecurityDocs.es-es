---
title: Trabajar con filtros y consultas de actividad de Cloud App Security | Microsoft Docs
description: "En este tema, se proporciona una lista de filtros y consultas de actividad de Cloud App Security y se explica cómo trabajar con ellos."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 1/3/2018
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: 9ba5c7d3-c733-4048-9b99-bf41a0f46695
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 72674e6cdc1b2ed96aa14a21090d1fee4296b426
ms.sourcegitcommit: bbf4a2715d1ea3fd21c1a1b87c7f5a2947d2ca68
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/04/2018
---
# <a name="activity-filters-and-queries"></a>Filtros y consultas de actividad

## <a name="activity-filters"></a>Filtros de actividad

A continuación se muestra una lista de los filtros de actividad que se pueden aplicar. La mayoría de los filtros admiten varios valores, así como NOT, para proporcionarle una herramienta muy eficaz para la creación de directivas.  
  
-   Identificador de actividad: busca solo actividades específicas por su identificador. Este filtro es muy útil cuando se conecta Cloud App Security con SIEM (mediante el agente SIEM) y se quiere investigar más las alertas del portal Cloud App Security.  
  
-   Objetos de actividad: busca los objetos en los que se ha realizado la actividad. Este filtro se aplica a objetos de archivo, carpeta, usuario o aplicación. 
    - Identificador de objeto de actividad: el identificador del objeto (identificador del archivo, carpeta, usuario o aplicación).
    - URL del archivo, carpeta o sitio: permite seleccionar direcciones URL de archivos, carpetas y direcciones que comienzan con una cadena específica.
    - Objeto de destino (archivo/carpeta): permite seleccionar un archivo o carpeta específicos. 
    - Elemento: permite buscar por el nombre o por el identificador de cualquier objeto de actividad (por ejemplo, nombres de usuario, archivos, parámetros, sitios). Para el filtro **Elemento de objetos de actividad**, puede seleccionar filtrar elementos que **contengan**, **sean iguales** o **comiencen por** el elemento específico.
    
-   Tipo de actividad: busca la actividad de la aplicación.

-   Actividad administrativa: busca solo actividades administrativas.  
  
-   Id. de alerta: busca por identificador de alerta.

-   Aplicación: busca solo las actividades en aplicaciones específicas.  
  
-   Acción aplicada: busca por la acción de control aplicada: Bloqueado, No usar proxy, Descrifrado, Cifrado, Error de cifrado, Ninguna acción.

-   Fecha: fecha en que se ha producido la actividad. El filtro admite fechas antes y después e intervalos de fechas.  
  
-   Descripción: palabra clave concreta en la descripción de la actividad, por ejemplo, todas las actividades que contienen la cadena **usuario** en su descripción.  
  
-   Etiqueta de dispositivo: busca por dispositivo compatible, administrado o comprobado.

-   Tipo de dispositivo: busca solo las actividades realizadas con un tipo de dispositivo concreto, por ejemplo, todas las actividades desde dispositivos móviles, PC o tabletas.  
  
-   Dirección IP: dirección IP sin procesar, categoría o etiqueta desde la que se ha realizado la actividad.  
    - Dirección IP sin procesar: le permite realizar búsquedas de actividades que se realizaron en direcciones IP sin formato, o por dichas direcciones, que sean iguales, diferentes o que comiencen con o no por una secuencia determinada o por direcciones IP sin procesar que están o no establecidas. 
    - Categoría IP: categoría de la dirección IP desde la que se ha realizado la actividad, por ejemplo, todas las actividades desde el intervalo administrativo de direcciones IP. Las categorías deben configurarse para incluir las direcciones IP correspondientes, excepto para la categoría de "De riesgo" que está preconfigurada e incluye dos etiquetas IP: proxy anónimo y Tor. Para más información sobre cómo configurar las categorías IP, vea [Organizar los datos de acuerdo a las necesidades](ip-tags.md).  
    - Etiqueta IP: etiqueta de la dirección IP desde la que se ha realizado la actividad, por ejemplo, todas las actividades desde direcciones IP de servidores proxy anónimos. Cloud App Security crea un conjunto de etiquetas IP integradas que no son configurables. Además, puede configurar sus propias etiquetas IP. Para más información sobre cómo configurar sus propias etiquetas IP, vea [Organizar los datos de acuerdo a las necesidades](ip-tags.md).
   Las etiquetas IP integradas incluyen:
    - Aplicaciones de Microsoft (14)
    - Proxy anónimo
    - Botnet (verá que una red de robots (botnet) ha realizado la actividad, con un vínculo para obtener más información sobre el botnet específico)
    - IP de análisis de Darknet
    - Servidor de malware C&C
    - Analizador de conectividad remota
    - Proveedores de satélite
    - Proxy inteligente y proxy de acceso (excluido a propósito)
    - Nodos de salida tor
    - Zscaler


-   Actividad suplantada: busca solo las actividades realizadas en nombre de otro usuario.  

-   Ubicación: país desde el que se ha realizado la actividad.  

-   Directiva coincidente: busca las actividades que coinciden con una directiva específica que se ha establecido en el portal.  

-   ISP registrado: ISP desde el que se ha realizado la actividad.   

-  Origen: busque el origen desde el que se detectó la actividad. El origen podría ser cualquiera de los siguientes:
  - Conector de aplicaciones: los registros provienen directamente del conector de la API de la aplicación.
  - Análisis del conector de aplicaciones: enriquecimientos de Cloud App Security basados en la obtención de información del conector de la API.
  

-   Usuario: el usuario que realizó la actividad, que se puede filtrar en el dominio, grupo, nombre u organización. Para filtrar las actividades sin un usuario específico, puede usar el operador 'no establecido'.  
    -   Dominio del usuario: busca un dominio de usuario específico.
    -   Organización de usuario: unidad organizativa del usuario que ha realizado la actividad, por ejemplo, todas las actividades realizadas por usuarios de marketing o EMEA.  
    -   Grupo de usuarios: grupos de usuarios específicos que puede importar de aplicaciones conectadas, como administradores de Office 365.  
    -   Nombre de usuario: busca por un nombre de usuario específico. Para ver una lista de los usuarios de un grupo de usuarios específico, en el **Cajón de actividades**, haga clic en el nombre del grupo de usuarios. Esto le llevará a la página de cuentas, en la que se enumeran todos los usuarios del grupo. Desde ahí puede profundizar en los detalles de las cuentas de usuarios específicos del grupo.
       -  Los filtros **Grupo de usuarios** y **Nombre de usuario** se pueden filtrar aún más si se usa el filtro **Como** y se selecciona el rol del usuario, que puede ser uno de los siguientes:
            - Objeto de actividad solo: esto significa que el usuario o grupo de usuarios seleccionado no ha realizado la actividad en cuestión, sino que era el objeto de la actividad.
            - Solo actor: esto significa que el usuario o grupo de usuarios ha realizado la actividad.
            - Cualquier rol: esto significa que el usuario o grupo de usuarios ha participado en la actividad, como la persona que ha realizado la actividad o como objeto de la actividad.

-   Agente de usuario: agente de usuario desde el que se ha realizado la actividad.  
  
-   Etiqueta de agente de usuario: etiqueta de agente de usuario integrada, por ejemplo, todas las actividades desde exploradores o sistemas operativos obsoletos.  
    
>[!NOTE]
> Para borrar los filtros, haga clic en el icono de borrar filtros ![icono de borrar filtros](./media/clear-filters.png).


## <a name="activity-queries"></a>Consultas de actividad

Para que la investigación sea incluso más sencilla, ahora puede crear consultas personalizadas y guardarlas para usar más adelante. 

1. En la página **Registro de actividad**, use los filtros como se ha descrito anteriormente para explorar las aplicaciones en profundidad según sea necesario. 

2. Una vez que haya conseguido los resultados deseados, haga clic en el botón **Guardar como** situado en la esquina superior derecha de los filtros. 

3. En la ventana emergente **Guardar consulta**, escriba el nombre de la consulta.

 ![nueva consulta](./media/new-activity-query.png)

4. Para volver a usar esta consulta en el futuro, en **Consultas**, desplácese hacia abajo hasta **Consultas guardadas** y seleccione la consulta. 

 ![abrir consulta](./media/select-activity-query.png)


Cloud App Security también le proporciona **consultas sugeridas** y le permite guardar las consultas personalizadas que usa a menudo. Las consultas sugeridas le proporcionan vías de investigación recomendadas que filtran las actividades mediante las siguientes consultas sugeridas opcionales:

 - Actividades administrativas: filtra todas las actividades para mostrar solo aquellas que implican a administradores.

 - Actividades de descarga: filtra todas las actividades para mostrar solo aquellas que fueron actividades de descarga, incluida la descarga de la lista de usuarios como un archivo .csv, la descarga de contenido compartido y la descarga de una carpeta.

 - Error al iniciar sesión: filtra todas las actividades para mostrar solo los errores al iniciar sesión a través de SSO. 

 - Actividades de archivo y carpeta: filtra todas las actividades para mostrar solo aquellas que implicaron archivos y carpetas, entre las que se incluyen las siguientes: cargar y descargar carpetas, obtener acceso a carpetas; crear, eliminar, cargar, descargar, poner en cuarentena y obtener acceso a archivos; y transferir contenido. 

 - Actividades de suplantación: filtra todas las actividades para mostrar solo las de suplantación.

 - Actividades de buzón: filtra todas las actividades para mostrar solo las actividades de Microsoft Exchange Online, por ejemplo, crear un elemento, purgar mensajes del buzón, actualizar el mensaje y enviar el mensaje con permisos de Enviar como (suplantación).

 - Cambios de contraseña y solicitudes de restablecimiento: filtra todas las actividades para mostrar solo aquellas relacionadas con el restablecimiento de contraseña, cambiar la contraseña y forzar al usuario para que cambie la contraseña al iniciar sesión la próxima vez.

 - Riesgos de seguridad: filtra todas las actividades para mostrar solo aquellas que coinciden con directivas DLP.

 - Actividades de uso compartido: filtra todas las actividades para mostrar solo aquellas que implican compartir carpetas y archivos, incluidas la creación de un vínculo de la empresa, la creación de un vínculo anónimo y la concesión de permisos de lectura y escritura.

 - Inicio de sesión correcto: filtra todas las actividades para mostrar solo aquellas que implican inicios de sesión correctos, entre los que se incluyen la acción de suplantar, el inicio de sesión de suplantación, el inicio de sesión único y el inicio de sesión desde un nuevo dispositivo.

![consultar actividades](./media/queries-activity.png)
 
Además, puede usar las consultas sugeridas como punto de partida para una nueva consulta. En primer lugar, seleccione una de las consultas sugeridas. Después, realice los cambios necesarios y, por último, haga clic en **Guardar como** para crear una **Consulta guardada**.


## <a name="see-also"></a>Consulte también  
[Actividades diarias para proteger el entorno de nube](daily-activities-to-protect-your-cloud-environment.md)   
[Para obtener soporte técnico, visite la página de soporte técnico asistido de Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Los clientes Premier también pueden elegir Cloud App Security directamente desde el Portal Premier.](https://premier.microsoft.com/)  
  
  