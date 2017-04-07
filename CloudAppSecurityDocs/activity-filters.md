---
title: Visibilidad de las actividades de aplicaciones en la nube | Microsoft Docs
description: "En este tema se proporciona una lista de actividades, filtros y parámetros de coincidencia que se pueden aplicar a directivas de actividad."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 4/2/2016
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: f3af2d25-9286-4e9b-b2ad-35653bec72ff
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: c8f22fc1c949a265b3a53cc4a534550be9601d10
ms.sourcegitcommit: 661f4ce41262e8462c90fd2a4f1232e2154d5113
translationtype: HT
---
# <a name="activities"></a>Actividades
Cloud App Security le ofrece visibilidad en todas las actividades de las aplicaciones conectadas. Después de conectar Cloud App Security con una aplicación mediante el conector de aplicaciones, Cloud App Security examina todas las actividades que se han producido (el período de tiempo de examen retroactivo varía según la aplicación) y después se actualiza constantemente con nuevas actividades. 

> [!NOTE] 
> Para obtener una lista completa de las actividades de Office 365 supervisadas por Cloud App Security, consulte [Buscar en el registro de auditoría del Centro de seguridad y cumplimiento de Office 365](https://support.office.com/article/Search-the-audit-log-in-the-Office-365-Security-Compliance-Center-0d4d0f35-390b-4518-800e-0c7ec95e946c?ui=en-US&rs=en-US&ad=US#ID0EABAAA=Audited_activities).

Se puede filtrar el **registro de actividades** para que pueda buscar actividades específicas. Puede crear directivas basadas en las actividades y después definir sobre qué quiere recibir alertas y actuar en consecuencia. También puede buscar actividades realizadas en determinados archivos. El tipo de actividades y la información que obtenemos de cada actividad dependen de la aplicación y de qué tipo de datos puede proporcionar la aplicación. 

Por ejemplo, puede usar el **registro de actividades** para buscar usuarios de la organización que usan sistemas operativos o exploradores que no están actualizados de la siguiente forma: después de conectar una aplicación a Cloud App Security en la página del **registro de actividades**, use el filtro avanzado y seleccione **User agent tag** (Etiqueta de agente de usuario). Después, seleccione **Outdated browser** (Explorador obsoleto) u **Outdated operating system** (Sistema operativo obsoleto).

 ![Ejemplo de actividad de explorador obsoleto](media/activity-example-outdated.png)

Si quiere comprobar si se tiene acceso a archivos **confidenciales** fuera de su organización, establezca el filtro **Objeto de actividad** para buscar **Etiqueta de clasificación** y seleccione la etiqueta **Confidencial**. Establezca el filtro **Dirección IP** para buscar **Categoría** y excluir las direcciones IP de la oficina (en el menú **Configuración** se pueden configurar categorías IP). Puede hacer clic en **New policy from search** (Nueva directiva de búsqueda) para crear una directiva de actividad basada en los filtros definidos y notificar automáticamente a los usuarios.

 ![Ejemplo de archivos confidenciales de actividad externos](media/activity-example-ip.png)

 
El filtro básico proporciona excelentes herramientas para empezar a filtrar sus actividades.

 ![filtro de registro de actividad básica](media/activity-log-filter-basic.png)

Para profundizar en actividades más específicas, puede ampliar el filtro básico haciendo clic en Opciones avanzadas.

 ![filtro de registro de actividad avanzada](media/activity-log-filter-advanced.png)

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
    - Categoría IP: categoría de la dirección IP desde la que se ha realizado la actividad, por ejemplo, todas las actividades desde el intervalo administrativo de direcciones IP. Las categorías deben configurarse para incluir las direcciones IP correspondientes, excepto para la categoría de "De riesgo" que está preconfigurada e incluye dos etiquetas IP: proxy anónimo y Tor. Para más información sobre cómo configurar las categorías IP, vea [Organizar los datos de acuerdo a las necesidades](general-setup.md#IPtagsandRanges).  
    - Etiqueta IP: etiqueta de la dirección IP desde la que se ha realizado la actividad, por ejemplo, todas las actividades desde direcciones IP de servidores proxy anónimos. Cloud App Security crea un conjunto de etiquetas IP integradas que no son configurables. Además, puede configurar sus propias etiquetas IP. Para más información sobre cómo configurar sus propias etiquetas IP, vea [Organizar los datos de acuerdo a las necesidades](general-setup.md#IPtagsandRanges).
   Las etiquetas IP integradas incluyen:
    - Aplicaciones de Microsoft (14)
    - Proxy anónimo
    - Red de robots (botnet)
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
  -    Conector de aplicaciones: los registros provienen directamente del conector de la API de la aplicación.
  -    Análisis del conector de aplicaciones: enriquecimientos de Cloud App Security basados en la obtención de información del conector de la API.
  

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
    
  
## <a name="working-with-the-activity-drawer"></a>Trabajo con el cajón de actividades

Para ver más información sobre cada actividad, haga clic en la misma actividad en el registro de actividades. Se abrirá el cajón de actividades que proporciona las siguientes acciones adicionales que puede realizar en el archivo:

- Directivas coincidentes: haga clic en el vínculo Directivas coincidentes para ver una lista de las directivas con las que coincide esta actividad.
- Ver datos sin procesar: haga clic en la opción para ver los datos sin procesar para ver los datos reales recibidos desde la aplicación.
- Usuario: haga clic en el usuario para ver la página correspondiente al usuario que realizó la actividad. 
- Tipo de dispositivo: haga clic en el tipo de dispositivo para ver los datos sin procesar del agente de usuario. 
- Ubicación: haga clic en la ubicación para ver la ubicación en los mapas de Bing.
- Categoría y etiquetas de la dirección IP: haga clic en la etiqueta IP para ver la lista de etiquetas IP que se encuentran en esta actividad. Después, puede filtrar por todas las actividades que coinciden con esta etiqueta.    

Los campos del cajón de actividades proporcionan vínculos contextuales a actividades adicionales y exploran en profundidad lo que desea realizar desde el cajón directamente. Por ejemplo, si mueve el cursor junto a la categoría de dirección IP, puede utilizar el icono Filtrar ![Agregar a filtro](./media/add-to-filter-icon.png) para agregar la dirección IP inmediatamente al filtro de la página actual. También puede utilizar el icono de engranaje de configuración ![icono de configuración](./media/contextual-settings-icon.png) que aparece para llegar directamente a la página de configuración necesaria para modificar la configuración de uno de los campos, como **Grupos de usuarios**.


![cajón de actividades](./media/activity-drawer.png "cajón de actividades")  
  
Para obtener una lista de las acciones de control disponibles, vea [Acciones de control de actividades](governance-actions.md#activity-governance-actions).


## <a name="see-also"></a>Consulte también  
[Actividades diarias para proteger el entorno de nube](daily-activities-to-protect-your-cloud-environment.md)   
[Para obtener soporte técnico, visite la página de soporte técnico asistido de Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Los clientes Premier también pueden elegir Cloud App Security directamente desde el Portal Premier.](https://premier.microsoft.com/)  
  
  