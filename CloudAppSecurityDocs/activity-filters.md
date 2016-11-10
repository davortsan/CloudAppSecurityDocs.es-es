---
title: Actividades | Microsoft Docs
description: "En este tema se proporciona una lista de actividades, filtros y parámetros de coincidencia que se pueden aplicar a directivas de actividad."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 10/15/2016
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: f3af2d25-9286-4e9b-b2ad-35653bec72ff
ms.reviewer: reutam
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: ed4ea71b24767d3602d40894d1cbac7447bcd8a2
ms.openlocfilehash: 401801da8a4439b3dc0cf5c2f150c72e169a6d16


---

# <a name="activities"></a>Actividades
A continuación se muestra una lista de los filtros de actividad que se pueden aplicar. La mayoría de los filtros admiten varios valores, así como NOT, para proporcionarle una herramienta muy eficaz para la creación de directivas.  
  
-   Actividad: busca solo determinadas actividades, por ejemplo, todas las cargas de archivos, inicios de sesión desde un nuevo dispositivo e inicios de sesión erróneos.  
  
-   Identificador de actividad: busca solo actividades específicas por su identificador. Este filtro es muy útil cuando se conecta MCAS con SIEM (mediante el agente SIEM) y se quiere investigar más las alertas del portal MCAS.  
  
-   Actividad administrativa: busca solo actividades administrativas.  
  
-   Actividad suplantada: busca solo las actividades realizadas en nombre de otro usuario.  
  
-   Aplicación: busca solo las actividades en aplicaciones específicas.  
  
-   Fecha: fecha en que se ha producido la actividad. El filtro admite fechas antes y después e intervalos de fechas.  
  
-   Usuario: usuario que ha realizado la actividad. Para filtrar las actividades sin un usuario específico, puede usar el operador 'no establecido'.  
  
     ![actividad, ref1](./media/activity-ref1.png "activity ref1")  
  
-   Dirección IP: dirección IP desde la que se ha realizado la actividad.  
  
-   Categoría IP: categoría de la dirección IP desde la que se ha realizado la actividad, por ejemplo, todas las actividades desde el intervalo administrativo de direcciones IP. Para obtener más información sobre las categorías IP, consulte [Organice los datos de acuerdo a las necesidades](general-setup.md#IPtagsandRanges).  
  
-   Etiqueta IP: etiqueta de la dirección IP desde la que se ha realizado la actividad, por ejemplo, todas las actividades desde direcciones IP de servidores proxy anónimos. Para obtener más información sobre las etiquetas IP, consulte [Organice los datos de acuerdo a las necesidades](general-setup.md#IPtagsandRanges).  
  
-   Ubicación: país desde el que se ha realizado la actividad.  
  
-   ISP registrado: ISP desde el que se ha realizado la actividad.  
  
     ![directiva de actividad, ref2](./media/activity-policy-ref2.png "activity policy ref2")  
  
-   Tipo de dispositivo: busca solo las actividades realizadas con un tipo de dispositivo concreto, por ejemplo, todas las actividades desde dispositivos móviles.  
  
-   Agente de usuario: agente de usuario desde el que se ha realizado la actividad.  
  
-   Etiqueta de agente de usuario: etiqueta de agente de usuario integrada, por ejemplo, todas las actividades desde exploradores o sistemas operativos obsoletos.  
  
-   Organización de usuario: unidad organizativa del usuario que ha realizado la actividad, por ejemplo, todas las actividades realizadas por usuarios de marketing o EMEA.  
  
- Objeto de destino: permite seleccionar un archivo específico. 

-   Grupo de usuarios: grupos de usuarios concretos importados automáticamente por MCAS desde la aplicación en la nube, por ejemplo, todas las actividades realizadas por los administradores de Office 365.  
  
-   Descripción: palabra clave concreta en la descripción de la actividad, por ejemplo, todas las actividades que contienen la cadena **usuario** en su descripción.  
  
-   Directiva coincidente: busca las actividades que coinciden con una directiva específica que se ha establecido en el portal.  
  
     ![directiva de actividad, ref3](./media/activity-policy-ref3.png "Activity policy ref3")  
  
## <a name="activity-match-parameters"></a>Parámetros de coincidencia de actividad  
Especifique la cantidad de repeticiones de la actividad necesarias para que haya coincidencia con la directiva, por ejemplo, el establecimiento de una directiva para alertar cuando un usuario realice diez intentos de inicio de sesión incorrectos en un período de tiempo de dos minutos.  
El valor predeterminado, **Parámetros de coincidencia de actividad**, genera una coincidencia para cada actividad única que cumple todos los filtros de la actividad.   
Con **Actividad repetida** puede establecer el número de actividades repetidas, la duración del período en el que se cuentan las actividades e incluso especificar que todas las actividades las debe realizar el mismo usuario y en la misma aplicación en la nube.  
  
### <a name="actions"></a>Acciones  
Notificaciones  
  
-   Alertas: las alertas pueden desencadenarse en el sistema y propagarse a través de mensajes de correo electrónico y de texto, según el nivel de gravedad.  
  
-   Notificación de correo electrónico de usuario: es posible personalizar los mensajes de correo electrónico y enviarlos a todos los propietarios de archivos infractores.  
  
-   Administrador de CC: según la integración de directorios del usuario, también se pueden enviar notificaciones de correo electrónico al administrador de la persona que haya infringido una directiva.  
  
-   Enviar una notificación a usuarios adicionales: lista específica de direcciones de correo electrónico que recibirán las notificaciones.  
  
Acciones de gobierno en aplicaciones  
  
-   Se pueden aplicar acciones granulares por aplicación. Las acciones específicas varían según la terminología de la aplicación.  
  
-   Suspender usuario: se suspende al usuario de la aplicación.  
  
-   Revocar contraseña: se revoca la contraseña del usuario y se le obliga a establecer una contraseña nueva en su siguiente inicio de sesión.  
  
     ![directiva de actividad, ref6](./media/activity-policy-ref6.png "activity policy ref6")  
  
## <a name="see-also"></a>Consulte también  
[Actividades diarias para proteger el entorno de nube](daily-activities-to-protect-your-cloud-environment.md)   
[Para obtener soporte técnico, visite la página de soporte técnico asistido de Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Los clientes Premier también pueden elegir Cloud App Security directamente desde el Portal Premier.](https://premier.microsoft.com/)  
  
  


<!--HONumber=Oct16_HO4-->


