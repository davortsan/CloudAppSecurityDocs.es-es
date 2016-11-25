---
title: "Notas de la versión | Microsoft Docs"
description: "Este tema se actualiza con frecuencia para informarle de las novedades de la versión más reciente de Cloud App Security."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 11/13/2016
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: d418ef3d-76ee-45d5-b5ae-21346e5239a3
ms.reviewer: reutam
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 759692e7b270d87dc1becf88453d095f2382c411
ms.openlocfilehash: 3161fd1c61779ba943d8269d2ec979050ee0ae1f


---

# <a name="release-notes"></a>Notas de la versión


## <a name="cloud-app-security-release-84"></a>Notas de la versión 84 de Cloud App Security
Publicado el 13 de noviembre de 2016

**Nuevas características**
-   Cloud App Security ahora admite Microsoft Azure Information Protection, que incluye una integración mejorada y autoaprovisionamiento. Puede filtrar los archivos y establecer directivas de archivo mediante la clasificación segura de etiquetas y, después, establecer la etiqueta de clasificación que quiere ver. Las etiquetas también indican si la clasificación la estableció alguien de su organización o un usuario de otro inquilino (externo). También puede establecer directivas de actividad, en función de las etiquetas de clasificación de Azure Information Protection y habilitar la detección automática de etiquetas de clasificación en Office 365. Para obtener más información acerca de cómo sacar partido a esta nueva característica increíble, consulte [Integración con Azure Information Protection](azip-integration.md).
 
**Mejoras**
-   Se realizaron mejoras en el registro de actividad de Cloud App Security: 
   -    Los eventos de Office 365 del Centro de seguridad y cumplimiento de Office 365 ahora se integran con Cloud App Security y se ven en el **Registro de actividades**.
   -    Toda la actividad de Cloud App Security se registra en el registro de actividades de Cloud App Security como actividad administrativa.
-   Para ayudarle a investigar alertas relacionadas con archivos, en cada alerta derivada de una directiva de archivo, ahora puede ver la lista de actividades que se realizaron en el archivo coincidente.
-   El algoritmo de viaje imposible del motor de detección de anomalías se ha mejorado para proporcionar una mayor compatibilidad para inquilinos pequeños. 
 
**Mejoras menores**
-   El **Activity export limit** (Límite de exportación de actividades) se elevó a 10 000. 
-   Al crear un **Informe de instantáneas** en el proceso de carga del registro manual de Cloud Discovery, ahora recibirá una estimación precisa de cuánto tardará el procesamiento del registro. 
-   En una directiva de archivo, la acción de gobierno **Remove collaborator** (Quitar colaborador) ahora funciona en grupos.
-   Se realizaron mejoras menores en la página **Permisos de la aplicación**. 
-   Si había más de 10 000 usuarios que disponían de permisos para una aplicación que se conectaba a Office 365, la lista se cargaba lentamente. Esto se ha solucionado.
-   Se han agregado atributos adicionales al **Catálogo de aplicaciones** con relación al sector de tarjetas de pago.


## <a name="cloud-app-security-release-83"></a>Notas de la versión 83 de Cloud App Security
Publicado el 30 de octubre de 2016

**Nuevas características**
-   Para simplificar el filtrado en el [registro de actividad](activity-filters.md) y en el [registro de archivo](file-filters.md), se han consolidado filtros similares. Utilice los filtros de actividad: Objeto de actividad, Dirección IP y Usuario. Utilice el filtro de archivos Colaboradores para encontrar exactamente lo que necesita.
-   Desde el cajón del registro de actividades, bajo **Origen**, puede hacer clic en el vínculo de **ver los datos sin procesar** para descargar los datos sin procesar usados para generar el registro de actividades, para explorar en profundidad en los eventos de la aplicación. 
-   Compatibilidad agregada para las actividades de inicio de sesión adicionales en Okta. [Versión preliminar privada]
-   Compatibilidad agregada para las actividades de inicio de sesión adicionales en Salesforce. 

**Mejoras**
-   Facilidad de uso mejorada para informes y solución de problemas de instantáneas de Cloud Discovery.
-   Visibilidad mejorada en la lista de alertas de varias aplicaciones.
-   Facilidad de uso mejorada al crear nuevos informes continuos de Cloud Discovery.
-   Facilidad de uso mejorada en el registro de gobierno.



## <a name="cloud-app-security-release-82"></a>Notas de la versión 82 de Cloud App Security
Publicado el 9 de octubre de 2016

**Mejoras**

- Las actividades **Cambiar correo electrónico** y **Cambiar contraseña** ahora son independientes de la actividad genérica **Administrar usuarios** en Salesforce.
- Se ha agregado una aclaración sobre el límite de alertas diarias por SMS. Se envía un máximo de 10 mensajes por número de teléfono y por día (UTC).
- Se ha agregado un nuevo certificado a los atributos de Cloud Discovery para Privacy Shield que reemplaza Safe Harbor (relevante solo para proveedores de EE. UU.).
- Se ha agregado un proceso de solución de problemas a los mensajes de error del conector de API para que sea más fácil solucionar los problemas.
- Mejora de la frecuencia de actualización del examen de aplicaciones de terceros de Office 365.
- Mejoras en el panel de Cloud Discovery.
- Se ha mejorado el analizador de Syslog de punto de control.
- Mejoras en el registro de gobierno para prohibir aplicaciones de terceros y para eliminar la prohibición.
 
**Correcciones de errores**
 
- Mejora del proceso para cargar un logotipo.
 
## <a name="cloud-app-security-release-81"></a>Notas de la versión 81 de Cloud App Security
Publicado el 18 de septiembre de 2016

**Mejoras**
- Cloud App Security ya es una aplicación de origen en Office 365. De ahora en adelante, puede conectar Office 365 con Cloud App Security con un solo clic.

- Nuevo aspecto del registro de gobierno: se ha actualizado para que tenga el mismo aspecto útil que el registro de actividad y la tabla de archivos. Use los nuevos filtros para encontrar fácilmente lo que necesita y supervisar las acciones de gobierno. 
- Se han realizado mejoras en el motor de detección de anomalías en lo que respecta a varios inicios de sesión erróneos y otros factores de riesgo.
- Se han realizado mejoras en los informes de instantáneas de Cloud Discovery.
- Se han realizado mejoras en las actividades administrativas del registro de actividades. Ahora, en Cambiar contraseña, Actualizar usuario y Restablecer contraseña se muestra si la actividad se realizó como una actividad administrativa.
- Se han mejorado los filtros de alerta para las alertas del sistema. 
- Ahora, la etiqueta de la directiva de una alerta contiene un vínculo al informe de directiva.
- Si no hay ningún propietario especificado para un archivo de Dropbox, los mensajes de correo electrónico de notificación se envían al destinatario que establezca. 
- Cloud App Security admite 24 idiomas más, con lo que la compatibilidad se amplía a un total de 41 idiomas.  


## <a name="cloud-app-security-release-80"></a>Notas de la versión 80 de Cloud App Security
Publicado el 4 de septiembre de 2016 

**Mejoras**
- Cuando se produce un error en el examen de DLP, ahora se proporciona una explicación de por qué Cloud App Security no pudo examinar el archivo. Para obtener más información, consulte [Content Inspection](https://aka.ms/aka.ms/cas-contentinspection) (Inspección de contenido).
- Se han realizado mejoras en los motores de detección de anomalías, incluido en las alertas de viaje imposible.
- Se han realizado mejoras en la experiencia para descartar alertas. También se pueden agregar comentarios para que el equipo de Cloud App Security sepa si la alerta era interesante y por qué razón, de modo que la información se pueda usar para mejorar las detecciones de Cloud App Security.
- Se han mejorado los analizadores de Cloud Discovery de Cisco ASA.
- Ahora recibirá una notificación por correo electrónico cuando se complete la carga manual de registros de Cloud Discovery.
   



## <a name="cloud-app-security-release-79"></a>Notas de la versión 79 de Cloud App Security
Publicado el 21 de agosto de 2016 

**Nuevas características**

- **Nuevo panel de Cloud Discovery**  
Ahora hay disponible un nuevo panel de Cloud Discovery, diseñado para proporcionar más información sobre cómo se usan las aplicaciones de nube en la organización. Proporciona una visión general a simple vista sobre los tipos de aplicaciones que se usan, las alertas abiertas y los niveles de riesgo de las aplicaciones de la organización. También permite saber quiénes son los usuarios de la organización que más usan las aplicaciones y proporciona un mapa de ubicación de la sede central de la aplicación.
El nuevo panel tiene más opciones para filtrar los datos, de modo que pueda generar vistas específicas en función de lo que más le interese y gráficos fáciles de entender para que se haga una idea general de un vistazo.

- **Nuevos informes de Cloud Discovery** Para ver los resultados de Cloud Discovery, ahora puede generar dos tipos de informes: informes de instantáneas e informes continuos.
Los informes de instantáneas proporcionan visibilidad ad hoc de un conjunto de registros de tráfico que puede cargar manualmente desde los firewalls y los servidores proxy. Los informes continuos muestran los resultados de todos los registros que se reenvían desde la red mediante los recopiladores de registros de Cloud App Security. Estos nuevos informes proporcionan una mejor visibilidad de todos los datos, la identificación automática de un uso anómalo según lo defina el motor de detección de anomalías de aprendizaje automático de Cloud App Security y la identificación de un uso anómalo según lo defina usted mediante el motor de directivas pormenorizadas y sólidas. Para obtener más información, consulte [Set up Cloud Discovery](set-up-cloud-discovery.md) (Configurar Cloud Discovery).
 
**Mejoras**
- Mejoras generales en la facilidad de uso de las páginas siguientes: páginas de directivas, configuración general y configuración de correo electrónico.
- En la tabla de alertas, es más fácil distinguir las alertas leídas de las no leídas. Las alertas leídas tienen una línea azul a la izquierda y aparecen atenuadas para indicar que ya se han leído.
- Se han actualizado los parámetros de **Actividad repetida** de la directiva de actividad. 
- En la página de cuentas, se ha agregado la columna **Tipo** de usuario, por lo que ahora puede ver qué tipo de cuenta de usuario tiene cada usuario. Los tipos de usuario son específicos de la aplicación. 
- Se ha agregado soporte prácticamente en tiempo real para las actividades relacionadas con archivos en OneDrive y SharePoint. Cuando un archivo cambia, Cloud App Security desencadena un examen casi de inmediato.


## <a name="cloud-app-security-release-78"></a>Notas de la versión 78 de Cloud App Security
Publicado el 7 de agosto de 2016

**Mejoras**
- Ahora puede hacer clic con el botón derecho en un archivo específico y **Buscar relacionados**. En el registro de actividades, puede usar el filtro del objeto de destino y seleccionar el archivo específico.

- Se han mejorado los analizadores de archivos de registro de Cloud Discovery, incluida la adición de Juniper y Cisco ASA.
- Cloud App Security ahora permite proporcionar comentarios para la mejora de las alertas cuando se descarta una alerta. Puede ayudar a mejorar la calidad de la característica de alertas de Cloud App Security. Para ello, infórmenos del motivo por el que descarta la alerta, por ejemplo: no es interesante, ha recibido demasiadas alertas similares, la gravedad real debe ser inferior o la alerta no es precisa.
- En la vista de la directiva de archivo o al ver un archivo, cuando se abre el cajón de archivos, se ha agregado un vínculo nuevo a las directivas coincidentes. Al hacer clic en él, puede ver todas las coincidencias y ahora puede descartarlas todas. 
- Ahora se ha agregado en todas las alertas correspondientes la unidad organizativa a la que pertenece un usuario.
- Ahora se envía una notificación por correo electrónico para informarle de que se ha completado el procesamiento de los registros cargados manualmente.


## <a name="cloud-app-security-release-77"></a>Notas de la versión 77 de Cloud App Security
Publicado el 24 de julio de 2016

**Mejoras**
- El icono del botón Exportar de Cloud Discovery se ha mejorado para una mayor facilidad de uso.
- Al investigar una actividad, si no se ha analizado el agente de usuario, ahora se pueden ver los datos sin procesar.
- Se han agregado dos nuevos factores de riesgo al motor de detección de anomalías: 
    - Cloud App Security ahora usa las etiquetas de direcciones IP que están asociadas a una red de robots (botnet) y direcciones IP anónimas como parte del cálculo de riesgo. 
    - La actividad de Office 365 ahora se supervisa para detectar frecuencias de descarga alta. Si la frecuencia de descarga de Office 365 es mucho mayor que la frecuencia de descarga normal de la organización o de un usuario específico, se desencadenará una alerta de detección de anomalías. 
- Ahora Cloud App Security es compatible con la nueva API de [función de uso compartido seguro](https://blogs.dropbox.com/dropbox/2016/06/new-dropbox-productivity-tools/) de Dropbox. 
- Se han realizado mejoras para agregar detalles en los errores de análisis de registro de Discovery, por ejemplo, para indicar que no hay transacciones relacionadas con la nube, todos los eventos están obsoletos, el archivo está dañado o el formato del registro no coincide.
- Se ha mejorado el filtro de fecha del registro de actividad y ahora incluye la capacidad de filtrar por hora.
- La página de intervalos de direcciones IP se ha mejorado para una mayor facilidad de uso.
- Ahora Cloud App Security incluye compatibilidad con Microsoft Azure Information Protection (versión preliminar). Puede filtrar los archivos y establecer directivas de archivo mediante la clasificación segura de etiquetas y, después, establecer el nivel de la etiqueta de clasificación que quiere ver. Las etiquetas también indicarán si la clasificación la estableció alguien de su organización o un usuario de otro inquilino (externo). 



## <a name="cloud-app-security-release-76"></a>Notas de la versión 76 de Cloud App Security
Publicado el 10 de julio de 2016

**Mejoras**

- Ahora se pueden exportar listas con los usuarios de los informes integrados.
- Se ha mejorado la facilidad de uso de la directiva de actividad agregada.
- Se ha mejorado la compatibilidad con el analizador de mensajes de registro de firewall de W3C de TMG.
- Se ha mejorado la facilidad de uso del menú desplegable de la acción de gobierno de archivos, que ahora se divide en acciones de colaboración, seguridad e investigación.
- Se ha mejorado la detección de viaje imposible de la actividad Enviar correo de Exchange Online.
- Se ha agregado una nueva lista de títulos (rutas de navegación) en la parte superior de las páginas de alertas y de directiva para facilitar la navegación.

**Correcciones de errores**
- La expresión preestablecida para la tarjeta de crédito de la configuración de DLP para las directivas de archivo se ha cambiado a Todos: Finanzas: Número de tarjeta de crédito.


## <a name="cloud-app-security-release-75"></a>Notas de la versión 75 de Cloud App Security
Publicado el 27 de junio de 2016


**Nuevas características**
* Se han agregado nuevos elementos a nuestra lista creciente de eventos compatibles con Salesforce, incluidos eventos que proporcionan información sobre informes, vínculos compartidos, distribución de contenido, inicio de sesión suplantado y mucho más.
* Los iconos de las aplicaciones conectadas del panel de Cloud App Security se han alineado con el estado de las aplicaciones tal como se muestra en el panel para reflejar los últimos 30 días.
* Compatibilidad con pantallas de ancho completo.


**Correcciones de errores**
* Los números de teléfono de alerta por SMS ahora se validan tras la inserción.

## <a name="cloud-app-security-release-74"></a>Notas de la versión 74 de Cloud App Security
Fecha de publicación: 13 de junio de 2016
* Se ha actualizado la pantalla Alerta para proporcionar más información de un vistazo, lo que incluye la posibilidad de ver todas las actividades del usuario con una sola mirada, un mapa de actividades, registros de gobierno de usuarios relacionados, una descripción del motivo por el que se ha desencadenado la alerta y gráficos adicionales y mapas de la página del usuario. 
* Los eventos generados por Cloud App Security ahora incluyen el tipo de evento, el formato, grupos de directivas, objetos relacionados y una descripción.
* Se han agregado nuevas etiquetas de direcciones IP para Office 365 ProPlus, OneNote, Office Online y Exchange Online Protection.
* Ahora tiene la opción de cargar registros desde el menú de detección principal.
* Se ha mejorado el filtro de categoría de direcciones IP. La categoría de dirección IP Nula ahora se denomina Sin categoría y se ha agregado una nueva categoría denominada Sin valor para incluir todas las actividades que no tienen datos de dirección IP.
* Los grupos de seguridad de Cloud App Security ahora se denominan grupos de usuarios para evitar la confusión con los grupos de seguridad de Active Directory.
* Ahora es posible filtrar por dirección IP y dejar fuera los eventos sin una dirección IP. 
* Se han realizado cambios en la configuración de los correos electrónicos de notificación cuando se detectan coincidencias en las directivas de actividad y de archivo. Ahora se pueden agregar direcciones de correo electrónico de destinatarios a CC con la notificación.


## <a name="cloud-app-security-release-73"></a>Notas de la versión 73 de Cloud App Security
Fecha de publicación: 29 de mayo de 2016

* Funciones de alerta actualizadas: ahora las alertas por directiva se pueden configurar para enviarse por correo o como mensaje de texto.
* Página de alertas: diseño mejorado para habilitar opciones de resolución avanzadas y la administración de incidentes.
* Ajuste de directiva: ahora es posible desplazarse desde las opciones de resolución de alertas directamente a la página de configuración de directiva y, así, permitir un mejor ajuste basado en alertas.
* Mejoras en el cálculo de la puntuación de riesgo de detección de anomalías y un menor índice de falsos positivos gracias a los comentarios de los clientes.
* Ahora la exportación del registro de actividades incluye el identificador de evento, la categoría de evento y el nombre del tipo de evento.
* Mejor apariencia y facilidad de uso de las acciones de gobierno de creación de directivas.
* Investigación y control simplificados para Office 365: con la selección de Office 365 se seleccionan automáticamente todas las aplicaciones que forman parte del conjunto de aplicaciones de Office 365.
* Ahora las notificaciones se envían a la dirección de correo configurada en la aplicación conectada. 
* Tras un error de conexión, ahora la aplicación de nube proporciona una descripción detallada de ese error.
* Cuando un archivo coincide con una directiva, ahora el cajón de archivos proporciona una dirección URL para tener acceso a ese archivo.
* Cuando se desencadena una alerta a raíz de una directiva de actividad o de una directiva de detección de anomalías, se envía una nueva notificación detallada que proporciona información sobre la coincidencia. 
* Cuando un conector de aplicaciones se desconecta, se desencadena una alerta del sistema automatizada.
* Ahora puede descartar y resolver una sola alerta o una selección masiva de alertas desde la página de alertas.

## <a name="cloud-app-security-release-72"></a>Notas de la versión 72 de Cloud App Security
Fecha de publicación: 15 de mayo de 2016

*  Mejoras generales en la infraestructura y apariencia:
    * Nuevo diagrama que proporciona más ayuda en el proceso de carga de registro manual de Cloud Discovery.
    * Proceso mejorado de actualización de archivos de registro no reconocidos (“Otros”), incluido un mensaje emergente que le avisa de que el archivo requiere revisión adicional y se le notificará cuando los datos estén disponibles.
    * Se destacan más infracciones de actividad y de archivo al investigar un registro de actividad y de archivo en busca de sistemas operativos y exploradores obsoletos.
* Mejores analizadores de archivos de registro de Cloud Discovery, incluida la adición de Cisco ASA, Cisco FWSM, Cisco Meraki y W3C.
* Mejoras en los problemas conocidos de Cloud Discovery.
* Nuevos filtros de actividad agregados para la afiliación interna/externa y de dominio del propietario.
* Se agregó un nuevo filtro que permite buscar cualquier objeto de Office 365 (archivos, carpetas, direcciones URL).
* Se agregó la capacidad de configurar una puntuación de riesgo mínima para las directivas de detección de anomalías.
* Al configurar una alerta para que se envíe cuando se infrinja una directiva, ahora se puede establecer un nivel de gravedad mínimo a partir del cual se recibirán las alertas. Puede elegir usar la configuración predeterminada de la organización para esto o establecer una configuración de alerta específica como valor predeterminado de la organización.

## <a name="see-also"></a>Consulte también  
[Para obtener soporte técnico, visite la página de soporte técnico asistido de Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Los clientes Premier también pueden elegir Cloud App Security directamente desde el Portal Premier.](https://premier.microsoft.com/)  
  
  


<!--HONumber=Nov16_HO3-->


