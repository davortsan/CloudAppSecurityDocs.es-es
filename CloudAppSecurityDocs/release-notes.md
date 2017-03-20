---
title: "Notas de la versión y versiones de Cloud App Security | Microsoft Docs"
description: "Este tema se actualiza con frecuencia para informarle de las novedades de la versión más reciente de Cloud App Security."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 3/5/2017
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: d418ef3d-76ee-45d5-b5ae-21346e5239a3
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 23870c7ba734acc3095f1dcd097f19954fee5e79
ms.sourcegitcommit: 064afc7148de42c0e81763f96ec13fb2c92f02a9
translationtype: HT
---
# <a name="release-notes"></a>Notas de la versión


## <a name="cloud-app-security-release-90-91-92"></a>Notas de la versión 90, 91 y 92 de Cloud App Security
Publicado en febrero de 2017

**Anuncio especial**

Cloud App Security ahora está certificada oficialmente con Microsoft Compliance para ISO, HIPAA, CSA STAR y cláusulas de modelo EU, entre otros. Para ver la lista completa de certificaciones, vaya a [Ofertas de Microsoft Compliance](https://www.microsoft.com/trustcenter/compliance/complianceofferings) y seleccione Cloud App Security.

**Nuevas características**

-  **Importar grupos de usuarios (versión preliminar)**   Al conectar aplicaciones mediante conectores de API, Cloud App Security ahora permite importar grupos de usuarios de Office 365 y Azure Active Directory. Puede aprovechar la existencia de grupos de usuarios importados para investigar qué documentos consulta el departamento de Recursos Humanos, para comprobar si sucede algo inusual en el grupo ejecutivo o para verificar si un miembro del grupo de administración ha llevado a cabo alguna actividad fuera del país. Para obtener más información e instrucciones, vea [Importar grupos de usuarios](user-groups.md).

-  En el registro de actividad, ahora puede filtrar los usuarios y los usuarios de grupos para mostrar las actividades realizadas por y en un usuario específico. Por ejemplo, puede investigar las actividades en las que el usuario ha suplantado a otras personas, así como las actividades en las que otras personas han suplantado a este usuario. Para obtener más información, vea [Actividades](activity-filters.md).

- Al investigar un archivo en la página **Archivos**, si explora en profundidad los **Colaboradores** de un archivo específico, ahora puede consultar más información sobre los colaboradores, incluido si son internos o externos, autores o lectores (permisos de archivo) y, cuando se comparte un archivo con un grupo, ahora puede ver todos los usuarios que son miembros del grupo. Esto le permite ver si los miembros del grupo son usuarios externos.

-  Ahora hay compatibilidad con IPv6 disponible para todos los dispositivos.

-    Cloud Discovery ahora admite dispositivos Barracuda.

-    Las alertas del sistema de Cloud App Security ahora incluyen errores de conectividad SIEM. Para obtener más información, vea [Integración de SIEM](siem.md).

-    Cloud App Security ahora es compatible con las actividades siguientes:

     **Office 365, SharePoint/OneDrive**: actualizar la configuración de aplicaciones, quitar el propietario del grupo, eliminar sitio, crear carpeta.

     **Dropbox**: agregar un miembro a un grupo, quitar un miembro de un grupo, crear grupo, cambiar el nombre de grupo, cambiar el nombre de un miembro de un equipo.

     **Box**: quitar un elemento de un grupo, actualizar un recurso compartido de elemento, agregar un usuario a un grupo, eliminar un usuario de un grupo.


## <a name="cloud-app-security-release-89"></a>Notas de la versión 89 de Cloud App Security
Publicado el 22 de enero de 2017

**Nuevas características**
-    Estamos empezando a implementar la capacidad de ver los eventos de DLP del Centro de seguridad y cumplimiento de Office 365 en Cloud App Security. Si configuró directivas DLP en el Centro de seguridad y cumplimiento de Office 365, cuando se detecten coincidencias de directiva, podrá verlas en el registro de actividades de Cloud App Security. La información del registro de actividades incluirá el archivo o el correo electrónico que desencadenó la coincidencia y la directiva o la alerta con la que coincide. La actividad "Evento de seguridad" permite ver las coincidencias de la directiva DLP de Office 365 en el registro de actividades de Cloud App Security. Con esta característica, puede hacer lo siguiente:
    -    Ver todas las coincidencias de DLP que proceden del motor DLP de Office&365;.
    -    Alertar sobre las coincidencias de la directiva DLP de Office 365 para un archivo específico, un sitio de SharePoint o una directiva.
    -    Investigar las coincidencias de DLP con un contexto más amplio, por ejemplo, los usuarios externos que han obtenido acceso a un archivo o que han descargado un archivo que desencadenó una coincidencia de la directiva DLP.
 
-    Se han mejorado las descripciones de las actividades para una mayor claridad y coherencia. Ahora, cada actividad incluye un botón de comentarios, por lo que si no entiende algo o tiene una pregunta, puede hacérnoslo saber. 
 
**Mejoras**  
-    Se ha agregado una nueva acción de gobierno para Office 365 que permite quitar todos los usuarios externos de un archivo. Por ejemplo, esto permite implementar directivas que **quitan recursos compartidos externos de los archivos que tienen una clasificación solo interna**.
-    Se ha mejorado la identificación de los usuarios externos en SharePoint Online. Cuando se filtra el grupo de "usuarios externos", no se muestra la cuenta del sistema app@sharepoint.



## <a name="cloud-app-security-release-88"></a>Notas de la versión 88 de Cloud App Security
Publicado el 8 de enero de 2017
 
**Nuevas características**
- Conecte su SIEM con Cloud App Security. Ahora puede enviar alertas y actividades automáticamente al SIEM de su elección mediante la configuración de agentes de SIEM. Ahora está disponible como versión preliminar pública.  Para obtener documentación completa y detalles, consulte la información relativa a la integración con SIEM.
- Ahora, Cloud Discovery es compatible con IPv6. Hemos incluido compatibilidad con Palo Alto y Juniper y en versiones futuras se incluirán más dispositivos.
 
**Mejoras**
- Hay un nuevo factor de riesgo en el catálogo de aplicaciones de nube. Ahora puede valorar una aplicación en función de si requiere autenticación de usuario. Las aplicaciones que exijan la autenticación y que no permitan el uso anónimo recibirán una mejor puntuación de riesgo.
- Estamos implementando nuevas descripciones de actividades para que sean más fáciles de usar y coherentes. La búsqueda de actividades no se verá afectada.
- Hemos incluido una identificación mejorada del dispositivo de usuario al permitir que Cloud App Security enriquezca más eventos con información del dispositivo.
 
## <a name="cloud-app-security-release-87"></a>Notas de la versión 87 de Cloud App Security
Fecha de publicación 25 de diciembre de 2016

**Nuevas características**
-    Estamos en proceso de lanzar la [anonimización de los datos](cloud-discovery-anonymizer.md) para que pueda disfrutar de Cloud Discovery a la vez que se protege la privacidad de los usuarios. La anonimización de los datos se realiza mediante el cifrado de la información del nombre de usuario.
-    Estamos en proceso de lanzar la capacidad de exportar un script de bloqueo desde Cloud App Security a dispositivos adicionales. El script le permitirá reducir fácilmente Shadow IT mediante el bloqueo del tráfico a aplicaciones no autorizadas. Esta opción ya está disponible para: 
    -    BlueCoat ProxySG
    -    Cisco ASA
    -    Fortinet
    -    Juniper SRX
    -    Palo Alto
    -    Websense
-    Se ha agregado una nueva acción de control de archivos que le permite forzar a un archivo heredar permisos del elemento principal, eliminando así los permisos únicos que se hayan configurado para el archivo o carpeta. Esta acción de control de archivos le permite cambiar los permisos de la carpeta o el archivo para que se hereden de la carpeta principal. 
-    Se ha agregado un nuevo grupo de usuarios con el nombre Externos. Es un grupo de usuarios predeterminado configurado previamente por Cloud App Security para incluir todos los usuarios que no forman parte de los dominios internos. Puede usar este grupo como filtro; por ejemplo, puede buscar actividades realizadas por los usuarios externos.
-    La característica Cloud Discovery ahora admite dispositivos Sophos Cyberoam.
 
**Correcciones de errores**
-    Los archivos de SharePoint Online y OneDrive para la Empresa se mostraban en el informe de directiva de archivo y en la página de archivos como para uso interno en lugar de privado. Esto se ha corregido.
 


## <a name="cloud-app-security-release-86"></a>Notas de la versión 86 de Cloud App Security
Fecha de publicación: 13 de diciembre de 2016

**Nuevas características**
- Todas las licencias independientes de Cloud App Security proporcionan la capacidad de habilitar el análisis de Azure Information Protection desde la configuración general (sin necesidad de crear una directiva). 
 
**Mejoras**
- Ahora puede usar "o" en el filtro de archivos para el nombre de archivo y en el filtro de tipo MIME para los archivos y directivas. Esto habilita escenarios como escribir la palabra "pasaporte" O "controlador" al crear una directiva con PII y coincidirá con cualquier archivo que contenga "pasaporte" o "controlador" en el nombre de archivo. 
- De forma predeterminada, cuando se ejecuta una directiva DLP de inspección de contenido, los datos de las infracciones resultantes se enmascaran. Ahora puede mostrar los últimos cuatro caracteres de la infracción. 

**Mejoras menores**
- Nuevos eventos relacionados con el buzón de Office 365 (Exchange) que tienen que ver con las reglas de reenvío y con agregar y quitar permisos de buzón delegados.
- Nuevo evento que audita la concesión de consentimiento para nuevas aplicaciones en Azure Active Directory. 




## <a name="cloud-app-security-release-85"></a>Notas de la versión 85 de Cloud App Security
Publicado el 27 de noviembre de 2016

**Nuevas características**
- Se ha creado una distinción entre las aplicaciones conectadas y las aplicaciones autorizadas. La autorización y la desautorización de aplicaciones funcionan ahora como etiquetas, de modo que se pueden aplicar a las aplicaciones detectadas o a cualquier aplicación del catálogo. Las aplicaciones conectadas son aplicaciones que ha conectado con el conector de la API para supervisarlas y controlarlas con mayor profundidad. Ahora puede etiquetar aplicaciones como autorizadas o no autorizadas, así como conectarlas mediante el conector de aplicaciones, en caso de que esté disponible. 
 
- Como parte de este cambio, se ha sustituido la página de aplicaciones autorizadas por la página **Aplicaciones conectadas**, que se ha rediseñado. Esta página externaliza los datos de estado de los conectores. 
 
- Se puede acceder más fácilmente a los recopiladores de registros desde el menú **Configuración**, en **Orígenes**. 
- Al crear un filtro de directiva de actividad, puede reducir el número de falsos positivos seleccionando la opción para ignorar las actividades repetidas cuando un mismo usuario las realiza de forma repetida en el mismo objeto. Este es el caso, por ejemplo, cuando una misma persona intenta descargar el mismo archivo varias veces, de modo que no se generará ninguna alerta. 
- Se han realizado mejoras en el cajón de actividades. Ahora, al hacer clic en un objeto de actividad, puede explorarlo en profundidad para obtener más información.

**Mejoras**
- Se han realizado mejoras en el motor de detección de anomalías, incluidas las alertas de desplazamiento imposible. Ahora, la información sobre la IP para este tipo de alertas está disponible en su descripción.
- También se han realizado mejoras en los filtros complejos, de modo que permitan agregar el mismo filtro más de una vez para ajustar los resultados que se filtran. 
- Se han separado las actividades de archivos y carpetas de Dropbox del resto para que se puedan consultar con mayor facilidad. 
  
**Correcciones de errores**
- Se ha corregido un error en el mecanismo del sistema de alertas que creaba falsos positivos.

## <a name="cloud-app-security-release-84"></a>Notas de la versión 84 de Cloud App Security
Publicado el 13 de noviembre de 2016

**Nuevas características**
-    Cloud App Security ahora admite Microsoft Azure Information Protection, que incluye una integración mejorada y autoaprovisionamiento. Puede filtrar los archivos y establecer directivas de archivo mediante la clasificación segura de etiquetas y, después, establecer la etiqueta de clasificación que quiere ver. Las etiquetas también indican si la clasificación la estableció alguien de su organización o un usuario de otro inquilino (externo). También puede establecer directivas de actividad, en función de las etiquetas de clasificación de Azure Information Protection y habilitar la detección automática de etiquetas de clasificación en Office 365. Para obtener más información acerca de cómo sacar partido a esta nueva característica increíble, consulte [Integración con Azure Information Protection](azip-integration.md).
 
**Mejoras**
-    Se realizaron mejoras en el registro de actividad de Cloud App Security: 
   -    Los eventos de Office 365 del Centro de seguridad y cumplimiento de Office 365 ahora se integran con Cloud App Security y se ven en el **Registro de actividades**.
   -    Toda la actividad de Cloud App Security se registra en el registro de actividades de Cloud App Security como actividad administrativa.
-    Para ayudarle a investigar alertas relacionadas con archivos, en cada alerta derivada de una directiva de archivo, ahora puede ver la lista de actividades que se realizaron en el archivo coincidente.
-    El algoritmo de viaje imposible del motor de detección de anomalías se ha mejorado para proporcionar una mayor compatibilidad para inquilinos pequeños. 
 
**Mejoras menores**
-    El **Activity export limit** (Límite de exportación de actividades) se elevó a 10 000. 
-    Al crear un **Informe de instantáneas** en el proceso de carga del registro manual de Cloud Discovery, ahora recibirá una estimación precisa de cuánto tardará el procesamiento del registro. 
-    En una directiva de archivo, la acción de gobierno **Remove collaborator** (Quitar colaborador) ahora funciona en grupos.
-    Se realizaron mejoras menores en la página **Permisos de la aplicación**. 
-    Si había más de 10 000 usuarios que disponían de permisos para una aplicación que se conectaba a Office 365, la lista se cargaba lentamente. Esto se ha solucionado.
-    Se han agregado atributos adicionales al **Catálogo de aplicaciones** con relación al sector de tarjetas de pago.


## <a name="cloud-app-security-release-83"></a>Notas de la versión 83 de Cloud App Security
Publicado el 30 de octubre de 2016

**Nuevas características**
-    Para simplificar el filtrado en el [registro de actividad](activity-filters.md) y en el [registro de archivo](file-filters.md), se han consolidado filtros similares. Utilice los filtros de actividad: Objeto de actividad, Dirección IP y Usuario. Utilice el filtro de archivos Colaboradores para encontrar exactamente lo que necesita.
-    Desde el cajón del registro de actividades, bajo **Origen**, puede hacer clic en el vínculo de **ver los datos sin procesar** para descargar los datos sin procesar usados para generar el registro de actividades, para explorar en profundidad en los eventos de la aplicación. 
-    Compatibilidad agregada para las actividades de inicio de sesión adicionales en Okta. [Versión preliminar privada]
-    Compatibilidad agregada para las actividades de inicio de sesión adicionales en Salesforce. 

**Mejoras**
-    Facilidad de uso mejorada para informes y solución de problemas de instantáneas de Cloud Discovery.
-    Visibilidad mejorada en la lista de alertas de varias aplicaciones.
-    Facilidad de uso mejorada al crear nuevos informes continuos de Cloud Discovery.
-    Facilidad de uso mejorada en el registro de gobierno.



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
  
  