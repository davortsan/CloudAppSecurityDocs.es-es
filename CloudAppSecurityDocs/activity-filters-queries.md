---
title: Trabajar con filtros y consultas de actividad Cloud App Security
description: En este artículo se proporciona una lista de Cloud App Security filtros y consultas de actividad y se explica cómo trabajar con ellos.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 12/10/2018
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: f37fab4f9d611577deecb4884838431144f1647d
ms.sourcegitcommit: 4f3883a9e85d0aaf2802b10433b221c3f1838d88
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/13/2020
ms.locfileid: "79285279"
---
# <a name="activity-filters-and-queries"></a>Consultas y filtros de actividad

*Se aplica a: Microsoft Cloud App Security*

En este artículo se proporcionan descripciones e instrucciones para Cloud App Security filtros de actividad y consultas.

## <a name="activity-filters"></a>Filtros de actividad

A continuación se muestra una lista de los filtros de actividad que se pueden aplicar. La mayoría de los filtros admiten varios valores y no proporcionan una herramienta eficaz para la creación de directivas.

- Identificador de actividad: busca solo actividades específicas por su identificador. Este filtro es útil cuando se conecta Microsoft Cloud App Security a su SIEM (mediante el agente SIEM) y desea investigar más las alertas en el portal de Cloud App Security.

- Objetos de actividad: busca los objetos en los que se realizó la actividad. Este filtro se aplica a los objetos de archivo, carpeta, usuario o aplicación.
  - IDENTIFICADOR de objeto de actividad: el identificador del objeto (archivo, carpeta, usuario o ID. de aplicación).
  <!-- - File, folder or site URL - Enables you to select files, folders and URLs that start with a specific string.-->
  <!-- - Target object (file/folder) - Enables you to select a specific file or folder. -->
  - Elemento: permite buscar por el nombre o por el identificador de cualquier objeto de actividad (por ejemplo, nombres de usuario, archivos, parámetros, sitios). Para el filtro **elemento de objeto de actividad** , puede seleccionar si desea filtrar los elementos que **contengan**, sean **iguales**o **comiencen con** el elemento específico.

- Tipo de actividad: busca la actividad de la aplicación.

- Actividad administrativa: busca solo actividades administrativas.

- Id. de alerta: busca por identificador de alerta.

- Aplicación: busca solo las actividades en aplicaciones específicas.

- Acción aplicada: busca por la acción de gobernanza aplicada: Bloqueado, No usar proxy, Descrifrado, Cifrado, Error de cifrado, Ninguna acción.

- Fecha: fecha en que se ha producido la actividad. El filtro admite fechas antes y después y un intervalo de fechas.

<!--- Description – Specific keyword in the activity description, for example, all activities that include the string **user** in their description.  -->

- Etiqueta de dispositivo: busca por dispositivo compatible, administrado o comprobado.

- Tipo de dispositivo: busca solo las actividades realizadas con un tipo de dispositivo específico. Por ejemplo, busque todas las actividades desde dispositivos móviles, PC o tabletas.

- Archivos y carpetas: busca archivos y carpetas en los que se realizó la actividad.
  - ID. de archivo: permite buscar por el ID. de archivo en el que se realizó la actividad.
  - Name: filtra por el nombre de los archivos o carpetas. Puede seleccionar si el nombre **termina con**, **es igual**a o **comienza con** el valor de búsqueda.
  - Archivos o carpetas específicos: permite incluir o excluir archivos o carpetas específicos. Al seleccionar archivos o carpetas, puede filtrar la lista por **aplicación**, **propietario**o nombre de **archivo**parcial.

- Dirección IP: dirección IP sin procesar, categoría o etiqueta desde la que se realizó la actividad.
  - Dirección IP sin procesar: permite buscar actividades que se realizaron en o por direcciones IP sin procesar. Las IP sin procesar pueden ser iguales, no iguales, empezar por o no comenzar con una secuencia determinada.
  - Categoría IP: categoría de la dirección IP desde la que se ha realizado la actividad, por ejemplo, todas las actividades desde el intervalo administrativo de direcciones IP. Las categorías deben configurarse para incluir las direcciones IP correspondientes, excepto para la categoría "arriesgada", que está preconfigurada e incluye dos etiquetas IP: proxy anónimo y Tor. Para más información sobre cómo configurar las categorías IP, vea [Organizar los datos de acuerdo a las necesidades](ip-tags.md).
  - Etiqueta IP: etiqueta de la dirección IP desde la que se ha realizado la actividad, por ejemplo, todas las actividades desde direcciones IP de servidores proxy anónimos. Cloud App Security crea un conjunto de etiquetas IP integradas que no son configurables. Además, puede configurar sus propias etiquetas IP. Para más información sobre cómo configurar sus propias etiquetas IP, vea [Organizar los datos de acuerdo a las necesidades](ip-tags.md).
  Las etiquetas IP integradas incluyen:
    - Aplicaciones de Microsoft (14)
    - Proxy anónimo
    - Botnets (puede ver que la actividad se realizó mediante una zombi con un vínculo para obtener más información sobre la zombi específica)
    - IP de análisis de Darknet
    - Servidor de malware C&C
    - Analizador de conectividad remota
    - Proveedores de satélite
    - Proxy inteligente y proxy de acceso (excluido a propósito)
    - Nodos de salida tor
    - Zscaler

- Actividad suplantada: busca solo las actividades realizadas en nombre de otro usuario.

- Instancia: la instancia de la aplicación en la que se ha realizado o no la actividad.

- Ubicación: país desde el que se ha realizado la actividad.

- Directiva coincidente: busca las actividades que coinciden con una directiva específica que se ha establecido en el portal.

- ISP registrado: ISP desde el que se ha realizado la actividad.

- Origen: busque el origen desde el que se detectó la actividad. El origen podría ser cualquiera de los siguientes:
  - Conector de aplicaciones: los registros provienen directamente del conector de la API de la aplicación.
  - Análisis del conector de aplicaciones: enriquecimientos de Cloud App Security basados en la obtención de información del conector de la API.

- Usuario: el usuario que realizó la actividad, que se puede filtrar por dominio, grupo, nombre u organización. Para filtrar las actividades sin un usuario específico, puede usar el operador 'no establecido'.
  - Dominio del usuario: busca un dominio de usuario específico.
  - Organización de usuario: unidad organizativa del usuario que ha realizado la actividad, por ejemplo, todas las actividades realizadas por usuarios de marketing o EMEA. Esto solo es relevante para las instancias conectadas de G Suite mediante unidades organizativas.
  - Grupo de usuarios: grupos de usuarios específicos que puede importar de aplicaciones conectadas, como administradores de Office 365.
  - Nombre de usuario: busca por un nombre de usuario específico. Para ver una lista de los usuarios de un grupo de usuarios específico, en el **Cajón de actividades**, haga clic en el nombre del grupo de usuarios. Al hacer clic, se le dirigirá a la página cuentas en la que se enumeran todos los usuarios del grupo. Desde allí, puede explorar en profundidad los detalles de las cuentas de usuarios específicos del grupo.
  - Los filtros **Grupo de usuarios** y **Nombre de usuario** se pueden filtrar aún más si se usa el filtro **Como** y se selecciona el rol del usuario, que puede ser uno de los siguientes:
    - Solo objeto de actividad, lo que significa que el usuario o grupo de usuarios seleccionado no ha realizado la actividad en cuestión, sino el objeto de la actividad.
    - Solo actor: Esto significa que el usuario o grupo de usuarios realizó la actividad.
    - Cualquier rol, lo que significa que el usuario o grupo de usuarios estaba implicado en la actividad, ya sea como la persona que realizó la actividad o como el objeto de la actividad.

- Agente de usuario: agente de usuario desde el que se ha realizado la actividad.

- Etiqueta de agente de usuario: etiqueta de agente de usuario integrada, por ejemplo, todas las actividades desde exploradores o sistemas operativos obsoletos.

<!--
>[!NOTE]
> If at any point you want to clear the filters, you can do so by clicking the clear filters icon ![clear filters icon](media/clear-filters.png). -->

## <a name="activity-queries"></a>Consultas de actividad

Para simplificar aún más la investigación, ahora puede crear consultas personalizadas y guardarlas para su uso posterior.

1. En la página **registro de actividad** , use los filtros como se describió anteriormente para explorar en profundidad las aplicaciones según sea necesario.

2. Una vez que haya terminado de crear la consulta, haga clic en el botón **Guardar como** situado en la esquina superior derecha de los filtros.

3. En el menú emergente **Guardar consulta** , asigne un nombre a la consulta.

   ![nueva consulta](media/new-activity-query.png)

4. Para volver a usar esta consulta en el futuro, en **consultas**, desplácese hacia abajo hasta **consultas guardadas** y seleccione la consulta.

   ![abrir consulta](media/select-activity-query.png)

Cloud App Security también proporciona **consultas sugeridas**. Las consultas sugeridas le proporcionan vías de investigación recomendadas que filtran las actividades. Puede editar estas consultas y guardar las como consultas personalizadas. Las siguientes son consultas sugeridas opcionales:

- Actividades de administración: filtra todas las actividades para mostrar solo las actividades que implican a los administradores.

- Descargar actividades: filtra todas las actividades para mostrar solo aquellas que eran actividades de descarga, incluida la descarga de la lista de usuarios como un archivo. csv archivo, la descarga de contenido compartido y la descarga de una carpeta.

- Error de inicio de sesión: filtra todas las actividades para mostrar solo los inicios de sesión erróneos y el inicio de sesión con error mediante SSO

- Actividades de archivos y carpetas: filtra todas las actividades para mostrar solo aquellas que implican archivos y carpetas. El filtro incluye la carga, la descarga y el acceso a las carpetas, así como la creación, eliminación, carga, descarga, puesta en cuarentena y acceso a archivos, y transferencia de contenido.

- Actividades de suplantación: filtra todas las actividades para mostrar solo las actividades de suplantación.

- Actividades de buzón: filtra todas las actividades para mostrar solo las actividades de Microsoft Exchange Online, como crear elemento, purgar mensajes del buzón, actualizar mensaje y enviar un mensaje mediante permisos de envío como (suplantación).

- Cambios de contraseña y solicitudes de restablecimiento: filtra todas las actividades para mostrar solo aquellas que implican el restablecimiento de contraseña, cambiar la contraseña y forzar al usuario a cambiar la contraseña en el siguiente inicio de sesión.

- Riesgos de seguridad: filtra todas las actividades para mostrar solo las actividades que coinciden con las directivas de DLP.

- Actividades compartidas: filtra todas las actividades para mostrar solo aquellas que implican compartir carpetas y archivos, incluida la creación de un vínculo de empresa, la creación de un vínculo anónimo y la concesión de permisos de lectura y escritura.

- Inicio de sesión correcto: filtra todas las actividades para mostrar solo las actividades que implican inicios de sesión correctos, incluida la acción Impersonate, suplantar el inicio de sesión, Inicio de sesión único e iniciar sesión desde un dispositivo nuevo.

![actividades de consulta](media/queries-activity.png)

Además, puede usar las consultas sugeridas como punto de partida para una nueva consulta. En primer lugar, seleccione una de las consultas sugeridas. A continuación, realice los cambios necesarios y, por último, haga clic en **Guardar como** para crear una nueva **consulta guardada**.

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Actividades diarias para proteger el entorno de nube](daily-activities-to-protect-your-cloud-environment.md)
