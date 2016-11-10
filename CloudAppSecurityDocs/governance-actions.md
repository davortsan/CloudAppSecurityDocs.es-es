---
title: Registro de gobierno | Microsoft Docs
description: En este tema se enumeran y se describen todas las acciones de gobierno que se pueden realizar en Cloud App Security.
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 10/15/2016
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: 3536c0a5-fa56-4931-9534-cc7cc4b4dfb0
ms.reviewer: reutam
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: ed4ea71b24767d3602d40894d1cbac7447bcd8a2
ms.openlocfilehash: 052ca8e20e75fcae7687d17687d7dd1a645ae5e6


---

# <a name="governance-log"></a>Registro de gobierno
El registro de gobierno proporciona un registro del estado de cada tarea que Cloud App Security deba ejecutar, incluidas las tareas manuales y automáticas. Entre estas tareas se incluyen las tareas definidas en las directivas, las acciones de gobierno establecidas en los archivos y los usuarios, y cualquier otra acción que haya determinado que debe realizar Cloud App Security. El registro de gobierno también proporciona información sobre el resultado correcto o incorrecto de estas acciones. Puede volver a intentar o revertir algunas de las acciones de gobierno en el registro de gobierno. 

A continuación se muestra una lista completa de las acciones que Cloud App Security permite realizar. Estas acciones se habilitarán en varios lugares de la consola, según se desprende de la columna **Ubicación**. Cada acción de gobierno realizada se incluye en el registro de gobierno.
Para obtener información sobre cómo se tratan las acciones de gobierno cuando hay conflictos de directivas, consulte [Policy Conflicts](control-cloud-apps-with-policies.md) (Conflictos de directivas). 

**Ubicación**|**Tipo de objeto de destino**|**Acción de gobierno**|**Descripción**|**Conectores relacionados** 
---------|---------|---------|---------|---------
|Directiva de archivo|Archivo|Restringir solo para colaboradores|Únicamente los colaboradores designados pueden tener acceso al archivo.|Cuadro|
|Configuración > Configuración de Cloud Discovery |Cloud Discovery|Recalcular las puntuaciones de Cloud Discovery|Se recalculan las puntuaciones en el catálogo de aplicaciones de Cloud tras un cambio en la métrica de puntuación.|Detección|
|Configuración > Configuración de Cloud Discovery > Administrar vistas de datos|Cloud Discovery|Crear vista de datos de filtro personalizado de Cloud Discovery|Se crea una vista de datos para obtener una vista más detallada de los resultados de la detección. Por ejemplo, intervalos de IP específicos.|Detección|
|Detectar > Aplicaciones detectadas/Direcciones IP/Usuarios|Cloud Discovery|Exportar datos de detección|Se crea un archivo CSV a partir de los datos de detección.|Detección|
|Configuración > Configuración de Cloud Discovery > Eliminar datos|Cloud Discovery|Eliminar datos de Cloud Discovery|Se eliminan todos los datos recopilados de los orígenes de detección.|Detección|
|Configuración > Configuración de Cloud Discovery > Cargar registros manualmente/Cargar registros automáticamente|Cloud Discovery|Analizar datos de Cloud Discovery|Notificación de que todos los datos de registro se han analizado.|Detección|
|Investigar > Archivos y Directiva de archivo|Archivo|Conceder permisos de lectura para el dominio|Se conceden permisos de lectura para el archivo en el dominio especificado, ya sea en todo el dominio o en un dominio específico. Esto podría ser útil si quiere quitar el acceso público tras conceder acceso al dominio a personas que necesitan trabajar en él.|Google Apps|
|Investigar > Archivos|Archivo|Concederme permisos de lectura|Se concede permisos de lectura para el archivo a sí mismo con el fin de tener acceso al archivo y saber si existe o no una infracción en él.|Google Apps|
|Directiva de archivo y Directiva de actividad|Archivo, Actividad|Enviar notificación al usuario|Se envía un correo a los usuarios para informarles de que algo que han hecho o un archivo que poseen infringe una directiva. Se puede agregar una notificación personalizada que indique en qué consistió la infracción.|Todos|
|Directiva de archivo e Investigar > Archivos|Archivo|Quitar la capacidad de compartir de los editores|En Google Drive, los permisos de editor predeterminados de un archivo permiten también compartir ese archivo. Esta acción de gobierno restringe esta opción y limita el uso compartido del archivo al propietario.|Google Apps|
|Investigar > Archivos y Directiva de archivo|Archivo|Poner en cuarentena de usuario|Se quitan todos los permisos del archivo y el archivo se mueve a una carpeta de cuarentena en la unidad raíz del usuario. De este modo, el usuario puede revisar el archivo y moverlo. Si se mueve de vuelta manualmente, no se restaura el uso compartido de archivos.|Box, One Drive, SharePoint|
|Directiva de archivo e Investigar > Archivos|Archivo|Poner en cuarentena de administrador|Se quitan todos los permisos del archivo y el archivo se mueve a una carpeta de cuarentena en la unidad raíz del usuario. De este modo, el administrador puede revisar el archivo y moverlo.|Cuadro|
|Investigar > Archivos y Directiva de archivo|Archivo|Quitar un colaborador|Se quita un colaborador específico de un archivo.|Google Apps, Box, One Drive, SharePoint|
|Investigar > Archivos y Directiva de archivo|Archivo|Convertir en privado|El archivo se convierte en privado: no hay más colaboradores ni vínculos públicos, ni se comparte con nadie.|Google Apps, One Drive, SharePoint|
|Investigar > Archivos y Directiva de archivo|Archivo|Quitar usuarios externos|Se quitan todos los colaboradores externos de los dominios configurados como internos en la configuración.|Google Apps, Box |
|Cuentas|Archivo|Quitar las colaboraciones del usuario|Se quitan todas las colaboraciones de un usuario específico en cualquiera de los archivos. Resulta conveniente cuando las personas dejan la empresa.|Box, Google Apps|
|Investigar > Archivos y Directiva de archivo|Archivo|Quitar el acceso público|Si pone un archivo suyo como de acceso público, pasa a ser accesible solo para quien esté configurado para tener acceso a él, según el tipo de acceso tuviera el archivo. |Google Apps|
|Investigar > Archivos y Directiva de archivo|Archivo|Quitar el vínculo compartido directo|Se quita un vínculo creado para un archivo que es público, pero que solo se comparte con personas específicas.|Cuadro|
|Panel de la aplicación > Permisos de aplicación|Permisos|Prohibir una aplicación|En Google y Salesforce: revoque los permisos que tiene una aplicación de terceros en Google o Salesforce y prohíba que reciba permisos en el futuro. En Office 365: no se puede conceder permiso a aplicaciones de terceros para que accedan a Office, pero no se pueden revocar.|Google Apps, Salesforce, Office|
|Panel de la aplicación > Permisos de aplicación|Permisos|Eliminar la prohibición de una aplicación|En Google y Salesforce: quite la prohibición de una aplicación y permita que los usuarios concedan permisos a la aplicación de terceros con Google o Salesforce. En Office 365: se restauran los permisos de la aplicación de terceros para acceder a Office.|Google Apps, Salesforce, Office|
|Panel de la aplicación > Permisos de aplicación|Permisos|Revocar aplicación|Revoque los permisos de una aplicación de terceros para acceder a Google, Salesforce u Office. Se trata de una acción única que se producirá en todos los permisos existentes, pero no impedirá las conexiones futuras. |Google Apps, Salesforce, Office|
|Panel de la aplicación > Permisos de aplicación|Cuenta|Revocar usuario de la aplicación|Se pueden revocar usuarios específicos al hacer clic en el número bajo Usuarios. La pantalla mostrará los usuarios específicos y puede usar la X para eliminar los permisos para cualquiera de ellos.|Google Apps, Salesforce, Office|
|Directiva de actividad e Investigar > Cuentas|Archivo|Revocar contraseña|Se revoca la contraseña de una cuenta de usuario; por ejemplo, establecer una directiva de actividad que revoca una contraseña tras 10 intentos de inicio de sesión infructuosos.|Google Apps|
|Directiva de actividad e Investigar > Cuentas|Archivo|Revocar privilegios de administrador|Se revocan los privilegios de una cuenta de administrador; por ejemplo, establecer una directiva de actividad que revoca los privilegios de administrador tras 10 intentos de inicio de sesión infructuosos.|Google Apps|
|Investigar > Archivos|Archivo|Revocar mis propios permisos de lectura|Se revocan los permisos de lectura para el archivo de uno mismo. Esto es útil después de haberse concedido permisos manualmente para saber si un archivo tiene o no una infracción.|Google Apps|
|Investigar > Cuentas y Directivas|Cuenta|Suspender usuario|El usuario se configura de forma que no tiene acceso ni la posibilidad de iniciar sesión. Si este usuario ya ha iniciado sesión cuando define esta opción, se le bloqueará inmediatamente.|Google Apps, Box, Office|
|Página Archivos y Directivas|Archivo|Transferir la propiedad de los archivos|Se cambia el propietario: en la directiva se elige un propietario específico.|Google Apps|
|Investigar > Cuentas |Archivo|Transferir la propiedad de todos los archivos|En una cuenta, todos los archivos de un usuario se transfieren para pasar a pertenecer a una nueva persona de su elección. El propietario anterior se convierte en editor. Después de transferir la propiedad, admin@gtest1.adallom.com se convertirá en editor y ya no podrá cambiar la configuración de uso compartido. El nuevo propietario recibirá una notificación por correo relativa al cambio de propiedad.|Google Apps|
|Directiva de archivo|Archivo|Enviar a la papelera|Coloca el archivo en la papelera del usuario.|One Drive, SharePoint|
|Investigar > Cuentas|Cuenta|Anular la suspensión del usuario|Se anula la suspensión del usuario.|Google Apps, Box, Office|
|Investigar > Archivos|Archivo|Restaurar de la cuarentena de usuario|Se restaura un usuario que estaba en cuarentena.|Cuadro|
|Investigar > Cuentas|Cuenta|Configuración de la cuenta|Le lleva a la página de configuración de la cuenta de la aplicación específica (por ejemplo, Salesforce).|Todas las aplicaciones (la configuración de One Drive y SharePoint se establece en Office).|
|Investigar > Archivos|Archivo|Permitir que los editores compartan|En Google Drive, los permisos de editor predeterminados de un archivo permiten también compartir ese archivo. Esta acción de gobierno hace lo contrario de “Quitar la capacidad de compartir de los editores” y permite que el editor comparta el archivo.|Google Apps|
|Directiva de archivo, Directiva de actividad|Archivo, Actividad|Enviar una notificación al último editor del archivo|Se envía un correo para informar a la última persona que editó el archivo de que este infringe una directiva.|Google Apps, Box|
|Directiva de archivo, Directiva de actividad|Archivo, Actividad|Enviar una notificación al propietario del archivo|Se envía un correo al propietario del archivo (con la posibilidad de agregar en copia a su administrador) cuando un archivo infringe una directiva. En Dropbox, si no hay ningún propietario asociado a un archivo, la notificación se enviará al usuario específico que establezca.|Todas las aplicaciones|
|Directiva de archivo, Directiva de actividad|Archivo, Actividad|Agregar en copia al administrador del propietario|Cuando el propietario del archivo recibe una notificación por correo en la que se le informa de que su archivo infringe una directiva, opcionalmente se notifica también al administrador del propietario del archivo.|Todas las aplicaciones excepto ServiceNow|
|Directiva de archivo, Directiva de actividad|Archivo, Actividad|Enviar una notificación a usuarios concretos|Se envía un correo para informar a determinados usuarios de que un archivo infringe una directiva.|Todas las aplicaciones|

## <a name="see-also"></a>Consulte también  
[Actividades diarias para proteger el entorno de nube](daily-activities-to-protect-your-cloud-environment.md)   
[Para obtener soporte técnico, visite la página de soporte técnico asistido de Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Los clientes Premier también pueden elegir Cloud App Security directamente desde el Portal Premier.](https://premier.microsoft.com/)  
  
  


<!--HONumber=Oct16_HO4-->

