---
title: Actividades | Microsoft Docs
description: "En este tema se proporciona una lista de actividades, filtros y parámetros de coincidencia que se pueden aplicar a directivas de actividad."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 10/26/2016
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: f3af2d25-9286-4e9b-b2ad-35653bec72ff
ms.reviewer: reutam
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 52f2245779568abbf41d47c4b45cdcced302529b
ms.openlocfilehash: 40fd28f568aa9af32f9e2399435f48372ea62413


---
# <a name="activities"></a>Actividades
Se puede filtrar el registro de actividad para que pueda buscar actividades específicas. El filtro básico proporciona excelentes herramientas para empezar a filtrar sus actividades.

 ![filtro de registro de actividad básica](media/activity-log-filter-basic.png)

Para profundizar en actividades más específicas, puede ampliar el filtro básico haciendo clic en Opciones avanzadas.

 ![filtro de registro de actividad avanzada](media/activity-log-filter-advanced.png)

## <a name="activity-filters"></a>Filtros de actividad
A continuación se muestra una lista de los filtros de actividad que se pueden aplicar. La mayoría de los filtros admiten varios valores, así como NOT, para proporcionarle una herramienta muy eficaz para la creación de directivas.  
  
-   Identificador de actividad: busca solo actividades específicas por su identificador. Este filtro es muy útil cuando se conecta MCAS con SIEM (mediante el agente SIEM) y se quiere investigar más las alertas del portal MCAS.  
  
-   Objetos de actividad: buscar direcciones URL de archivo, carpeta o sitio o los objetos de destino (archivo o carpeta).
    - URL del archivo, carpeta o sitio: permite seleccionar direcciones URL de archivos, carpetas y direcciones que comienzan con una cadena específica.
    - Objeto de destino (archivo/carpeta): permite seleccionar un archivo o carpeta específicos. 
    
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
    - Categoría IP: categoría de la dirección IP desde la que se ha realizado la actividad, por ejemplo, todas las actividades desde el intervalo administrativo de direcciones IP. Para obtener más información sobre las categorías IP, consulte [Organice los datos de acuerdo a las necesidades](general-setup.md#IPtagsandRanges).  
    - Etiqueta IP: etiqueta de la dirección IP desde la que se ha realizado la actividad, por ejemplo, todas las actividades desde direcciones IP de servidores proxy anónimos. Para obtener más información sobre las etiquetas IP, consulte [Organice los datos de acuerdo a las necesidades](general-setup.md#IPtagsandRanges).
  
-   Actividad suplantada: busca solo las actividades realizadas en nombre de otro usuario.  

-   Ubicación: país desde el que se ha realizado la actividad.  

-   Directiva coincidente: busca las actividades que coinciden con una directiva específica que se ha establecido en el portal.  

-   ISP registrado: ISP desde el que se ha realizado la actividad.   

-  Origen: busque el origen desde el que se detectó la actividad. El origen podría ser cualquiera de los siguientes:
  - Conector de aplicaciones: los registros provienen directamente del conector de la API de la aplicación.
  - Análisis del conector de aplicaciones: enriquecimientos de Cloud App Security basados en la obtención de información del conector de la API.
  

-   Usuario: el usuario que realizó la actividad, que se puede filtrar en el dominio, grupo, nombre u organización. Para filtrar las actividades sin un usuario específico, puede usar el operador 'no establecido'.  
    -   Dominio del usuario: busca un dominio de usuario específico.
    -   Grupo de usuarios: grupos de usuarios concretos importados automáticamente por Cloud App Security desde la aplicación en la nube, por ejemplo, todas las actividades realizadas por los administradores de Office 365.
    -   Nombre de usuario: busca por un nombre de usuario específico.
    -   Organización de usuario: unidad organizativa del usuario que ha realizado la actividad, por ejemplo, todas las actividades realizadas por usuarios de marketing o EMEA.  

-   Agente de usuario: agente de usuario desde el que se ha realizado la actividad.  
  
-   Etiqueta de agente de usuario: etiqueta de agente de usuario integrada, por ejemplo, todas las actividades desde exploradores o sistemas operativos obsoletos.  
    
  
## <a name="working-with-the-activity-drawer"></a>Trabajo con el cajón de actividades

Para ver más información sobre cada actividad, haga clic en la misma actividad en el registro de actividades. Se abrirá el cajón de actividades que proporciona las siguientes acciones adicionales que puede realizar en el archivo:

- Directivas coincidentes: haga clic en el vínculo Directivas coincidentes para ver una lista de las directivas con las que coincide esta actividad.
- Ver datos sin procesar: haga clic en la opción para ver los datos sin procesar para ver los datos reales recibidos desde la aplicación.
- Usuario: haga clic en el usuario para ver la página correspondiente al usuario que realizó la actividad. 
- Tipo de dispositivo: haga clic en el tipo de dispositivo para ver los datos sin procesar del agente de usuario. 
- Ubicación: haga clic en la ubicación para ver la ubicación en los mapas de Bing.
- Categoría y etiquetas de la dirección IP: haga clic en la etiqueta IP para ver la lista de etiquetas IP que se encuentran en esta actividad. Después, puede filtrar por todas las actividades que coinciden con esta etiqueta.    

![cajón de actividades](./media/activity-drawer.png "activity drawer")  
  
Para obtener una lista de acciones de gobierno disponibles, consulte [Parámetros de coincidencia de actividad](governance-actions.md#activity-match-parameters).


## <a name="see-also"></a>Consulte también  
[Actividades diarias para proteger el entorno de nube](daily-activities-to-protect-your-cloud-environment.md)   
[Para obtener soporte técnico, visite la página de soporte técnico asistido de Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Los clientes Premier también pueden elegir Cloud App Security directamente desde el Portal Premier.](https://premier.microsoft.com/)  
  
  


<!--HONumber=Dec16_HO1-->


