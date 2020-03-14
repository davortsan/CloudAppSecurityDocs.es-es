---
title: 'Acciones de gobierno para controlar las aplicaciones conectadas: Cloud App Security | Microsoft Docs'
description: En este artículo se enumeran y se describen todas las acciones de gobierno que se pueden realizar en Cloud App Security y los mensajes de registro que realizan el seguimiento.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 12/03/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 5ae82c1acddf3bbf1ee711a108234d6b69cd8ee4
ms.sourcegitcommit: 4f3883a9e85d0aaf2802b10433b221c3f1838d88
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/13/2020
ms.locfileid: "79285339"
---
# <a name="governing-connected-apps"></a>Control de aplicaciones conectadas

*Se aplica a: Microsoft Cloud App Security*

La gobernanza le permite controlar qué hacen los usuarios en tiempo real en varias aplicaciones. Para las aplicaciones conectadas, puede aplicar acciones de gobernanza a archivos o actividades. Las acciones de gobierno son acciones integradas que se pueden ejecutar en archivos o actividades directamente desde Microsoft Cloud App Security. Las acciones de gobierno controlan lo que hacen los usuarios en tiempo real en las aplicaciones conectadas.

> [!NOTE]
> Cuando Microsoft Cloud App Security intenta ejecutar una acción de gobierno en un archivo pero se produce un error porque el archivo está bloqueado, se reintentará automáticamente la acción de gobierno.

## <a name="file-governance-actions"></a>Acciones de gobernanza relacionadas con archivos

Las siguientes acciones de gobernanza pueden realizarse para aplicaciones conectadas en un archivo o usuario específico o bien desde una directiva concreta.

- **Notificaciones**

  - **Alertas** : las alertas se pueden desencadenar en el sistema y propagarse por correo electrónico y mensaje de texto, según el nivel de gravedad.

  - **Notificación de correo electrónico de usuario** : los mensajes de correo electrónico se pueden personalizar y se enviarán a todos los propietarios de archivos infractores.

  - **Notificar a usuarios específicos** : lista específica de direcciones de correo electrónico que recibirán estas notificaciones.

  - **Notificar al último editor de archivos** : envía notificaciones a la última persona que modificó el archivo.

- **Acciones de gobierno en aplicaciones** : se pueden aplicar acciones granulares por aplicación. las acciones específicas varían según la terminología de la aplicación.

  - **Etiquetado**
    - **Aplicar etiqueta** : capacidad para agregar una etiqueta de clasificación Azure Information Protection.
    - **Quitar etiqueta** : capacidad para quitar una etiqueta de clasificación Azure Information Protection.
  - **Cambiar el uso compartido**

    - **Quitar el uso compartido público** : permite el acceso únicamente a los colaboradores con nombre, por ejemplo: quitar el acceso público para G Suite y quitar el vínculo compartido directo para Box.

    - **Quitar usuarios externos** : permite el acceso únicamente a los usuarios de la empresa.

    - **Hacer privado** : solo los administradores del sitio pueden tener acceso al archivo, se quitan todos los recursos compartidos.

    - **Quitar un colaborador** : quita un colaborador específico del archivo.

    - **Reducir el acceso público** : establezca que los archivos disponibles públicamente solo estén disponibles con un vínculo compartido. Google

    - **Vínculo de expiración compartido** : capacidad de establecer una fecha de Experation para un vínculo compartido después del cual ya no estará activo. Cuadro

    - **Cambiar el nivel de acceso del vínculo de uso compartido** : capacidad de cambiar el nivel de acceso del vínculo compartido entre solo la empresa, solo colaboradores y público. Cuadro

  - **Cuarentena**

    - **Poner en cuarentena de usuario** : permite el autoservicio moviendo el archivo a una carpeta de cuarentena controlada por el usuario.

    - **Poner en cuarentena de administrador** : el archivo se mueve a la cuarentena en la unidad de administración y el administrador tiene que aprobarlo.

  - **Heredar permisos del elemento primario** : esta acción de gobierno permite quitar permisos concretos establecidos para un archivo o carpeta en Office 365. A continuación, vuelva a los permisos establecidos para la carpeta principal.

  - **Trash** : mueva el archivo a la carpeta de la papelera. (Box, Dropbox, Google Drive, OneDrive, SharePoint)

   ![policy_create de alertas](media/policy_create-alerts.png "policy_create de alertas")

## <a name="activity-governance-actions"></a>Acciones de gobernanza de actividades

- **Notificaciones**

  - **Alertas** : las alertas se pueden desencadenar en el sistema y propagarse por correo electrónico y mensaje de texto, según el nivel de gravedad.

  - **Notificación de correo electrónico de usuario** : los mensajes de correo electrónico se pueden personalizar y se enviarán a todos los propietarios de archivos infractores.

  - **Enviar una notificación a usuarios adicionales** : lista específica de direcciones de correo electrónico que recibirán estas notificaciones.

- **Acciones de gobierno en aplicaciones** : se pueden aplicar acciones granulares por aplicación. las acciones específicas varían según la terminología de la aplicación.

  - **Suspender usuario** : suspende al usuario de la aplicación.
    > [!NOTE]
    > Si el Azure Active Directory (Azure AD) está establecido para que se sincronice automáticamente con los usuarios de su Active Directory entorno local, la configuración del entorno local invalidará la configuración de Azure AD y esta acción de gobierno se revertirá.

  - **Requerir al usuario que vuelva a iniciar sesión** : cierra la sesión del usuario y requiere que inicie sesión de nuevo.

  - **Confirmar usuario comprometido** : establezca el nivel de riesgo del usuario en alto. Esto hace que se apliquen las acciones de directiva relevantes definidas en Azure AD. Para obtener más información sobre cómo funciona Azure AD con los niveles de riesgo, consulte [¿Cómo usa Azure ad mis comentarios de riesgo](https://docs.microsoft.com/azure/active-directory/identity-protection/howto-identity-protection-risk-feedback#how-does-azure-ad-use-my-risk-feedback)?

  ![Acciones de gobierno de directiva de actividad de Cloud App Security](media/activity-policy-ref6.png ", ref6 de directiva de actividad")

## <a name="governance-conflicts"></a>Conflictos de gobernanza

Después de crear varias directivas, puede darse el caso de que sus acciones de gobernanza se superpongan. Si es así, Cloud App Security procesará las acciones de gobernanza de la manera siguiente:

### <a name="conflicts-between-policies"></a>Conflictos entre directivas

- Si dos directivas contienen acciones que forman parte de la otra directiva (por ejemplo, **Quitar recursos compartidos externos** se incluye en **Hacer privado**), Cloud App Security resolverá el conflicto y se aplicará la acción más restrictiva.
- Si las acciones no están relacionadas (por ejemplo, **enviar una notificación al propietario** y **hacer privado**). se llevarán a cabo ambas acciones.
- Si las acciones entran en conflicto (por ejemplo, **cambiar el propietario al usuario** a y **cambiar el propietario al usuario B**), pueden producirse resultados diferentes en cada coincidencia. Es importante cambiar las directivas para evitar conflictos, ya que pueden dar lugar a cambios no deseados en la unidad que serán difíciles de detectar.

### <a name="conflicts-in-user-sync"></a>Conflictos en la sincronización de usuarios

- Si el Azure AD está establecido para que se sincronice automáticamente con los usuarios de su Active Directory entorno local, la configuración del entorno local invalidará la configuración de Azure AD y esta acción de gobierno se revertirá.

## <a name="governance-log"></a>Registro de gobernanza

El registro de gobernanza proporciona un registro del estado de cada tarea que Cloud App Security deba ejecutar, incluidas las tareas manuales y automáticas. Estas tareas incluyen las que se establecen en las directivas, las acciones de gobierno establecidas en los archivos y los usuarios, y cualquier otra acción que se establezca Cloud App Security tomar. El registro de gobernanza también proporciona información sobre el resultado correcto o incorrecto de estas acciones. Puede volver a intentar o revertir algunas de las acciones de gobernanza en el registro de gobernanza.

En la tabla siguiente se muestra una lista completa de las acciones que puede realizar en el portal de Cloud App Security. Estas acciones se habilitan en varios lugares de la consola, tal como se describe en la columna **Ubicación** . Cada acción de gobernanza realizada se incluye en el registro de gobernanza.
Para obtener información sobre cómo se tratan las acciones de gobernanza cuando hay conflictos de directivas, vea [Policy Conflicts](control-cloud-apps-with-policies.md) (Conflictos de directivas).

| Location | Tipo de objeto de destino | Acción de gobernanza |Descripción| Conectores relacionados|
|-------------------|---------|-----|--------|-------|
|Accounts |Archivo |Quitar las colaboraciones del usuario | Se quitan todas las colaboraciones de un usuario específico en cualquiera de los archivos. Resulta conveniente cuando las personas dejan la empresa. |Box, G Suite|
|Accounts | Cuenta | Anular la suspensión del usuario |Se anula la suspensión del usuario. |G Suite, Box, Office, Salesforce|
|Accounts | Cuenta |Configuración de la cuenta | Le lleva a la página de configuración de la cuenta de la aplicación específica (por ejemplo, Salesforce). | Todas las aplicaciones (la configuración de One Drive y SharePoint se establece en Office). |
|Accounts |Archivo |Transferir la propiedad de todos los archivos | En una cuenta, todos los archivos de un usuario se transfieren para pasar a pertenecer a una nueva persona de su elección. El propietario anterior se convierte en un editor y ya no puede cambiar la configuración de uso compartido. El nuevo propietario recibirá una notificación por correo relativa al cambio de propiedad. | G Suite|
|Cuentas, Directiva de actividad | Cuenta | Suspender usuario| Establece que el usuario no tenga acceso y no pueda iniciar sesión. Si ha iniciado sesión al establecer esta acción, se le bloqueará inmediatamente. |G Suite, Box, Office, Salesforce|
|Directiva de actividad, Cuentas | Cuenta |Requerir que el usuario vuelva a iniciar sesión|Revoca todos los tokens de actualización y los problemas de cookies de sesión a las aplicaciones del usuario. Esta acción impedirá el acceso a los datos de la organización y obligará al usuario a volver a iniciar sesión en todas las aplicaciones.| G Suite, Office|
|Directiva de actividad, Cuentas | Cuenta |Confirmar que el usuario está comprometido|Establezca el nivel de riesgo del usuario en alto. Esto hace que se apliquen las acciones de directiva relevantes definidas en Azure AD. | Office |
|Directiva de actividad, Cuentas | Cuenta | Revocar privilegios de administrador |Revoca los privilegios de una cuenta de administrador. Por ejemplo, establecer una directiva de actividad que revoca los privilegios de administrador tras 10 intentos de inicio de sesión incorrectos. | G Suite|
|Panel de la aplicación > Permisos de aplicación |Permisos|Aplicación unban| En Google y Salesforce: Quite la prohibición de la aplicación y permita que los usuarios concedan permisos a la aplicación de terceros con Google o Salesforce. En Office 365: restaura los permisos de la aplicación de terceros en Office. |G Suite, Salesforce, Office |
|Panel de la aplicación > Permisos de aplicación |Permisos| Deshabilitar permisos de aplicación | Revocar los permisos de una aplicación de terceros para Google, Salesforce u Office. Se trata de una acción única que se producirá en todos los permisos existentes, pero no impedirá las conexiones futuras.|G Suite, Salesforce, Office |
|Panel de la aplicación > Permisos de aplicación |Permisos| Habilitar permisos de aplicación |Conceda permisos de aplicación de terceros a Google, Salesforce u Office. Se trata de una acción única que se producirá en todos los permisos existentes, pero no impedirá las conexiones futuras.|G Suite, Salesforce, Office |
|Panel de la aplicación > Permisos de aplicación |Permisos| Prohibir una aplicación | En Google y Salesforce: revoque los permisos que tiene una aplicación de terceros en Google o Salesforce y prohíba que reciba permisos en el futuro. En Office 365: no permite el permiso de aplicaciones de terceros para tener acceso a Office, pero no los revoca. |G Suite, Salesforce, Office |
|Panel de la aplicación > Permisos de aplicación |Permisos|Revocar aplicación|Revoque los permisos de una aplicación de terceros para acceder a Google o Salesforce. Se trata de una acción única que se producirá en todos los permisos existentes, pero no impedirá las conexiones futuras. | G Suite, Salesforce|
|Panel de la aplicación > Permisos de aplicación | Cuenta | Revocar usuario de la aplicación|Se pueden revocar usuarios específicos al hacer clic en el número bajo Usuarios. La pantalla mostrará los usuarios específicos y puede usar la X para eliminar los permisos de cualquier usuario.| G Suite, Salesforce|
|Detectar > Aplicaciones detectadas/Direcciones IP/Usuarios| Cloud Discovery | Exportar datos de detección | Se crea un archivo CSV a partir de los datos de detección. | Detección |
|Directiva de archivo|Archivo |Enviar a la papelera|Mueve el archivo en la papelera del usuario.| Box, Dropbox, Google Drive, OneDrive, SharePoint |
|Directiva de archivo|Archivo | Enviar una notificación al último editor del archivo |Se envía un correo para informar a la última persona que editó el archivo de que este infringe una directiva. |G Suite, Box|
|Directiva de archivo|Archivo |Enviar una notificación al propietario del archivo|Envía un correo electrónico al propietario del archivo cuando un archivo infringe una directiva. En Dropbox, si no hay ningún propietario asociado a un archivo, la notificación se enviará al usuario específico que establezca. | Todas las aplicaciones |
|Directiva de archivo, Directiva de actividad | Archivo, Actividad | Enviar una notificación a usuarios concretos |Se envía un correo para informar a determinados usuarios de que un archivo infringe una directiva.| Todas las aplicaciones |
|Directiva de archivo y Directiva de actividad | Archivo, Actividad |Enviar notificación al usuario|Se envía un correo a los usuarios para informarles de que algo que han hecho o un archivo que poseen infringe una directiva. Se puede agregar una notificación personalizada que indique en qué consistió la infracción. |Todos |
|Directiva de archivo y archivos|Archivo | Quitar la capacidad de compartir de los editores|En Google Drive, los permisos de editor predeterminados de un archivo permiten también compartir ese archivo. Esta acción de gobernanza restringe esta opción y limita el uso compartido del archivo al propietario.| G Suite|
|Directiva de archivo y archivos|Archivo | [Poner en cuarentena de administrador](use-case-admin-quarantine.md) |Quita todos los permisos del archivo y mueve el archivo a una carpeta de cuarentena en una ubicación para el administrador. Esta acción permite al administrador revisar el archivo y quitarlo.| Office 365 SharePoint, OneDrive para la Empresa, Box|
|Directiva de archivo y archivos|Archivo | Aplicar etiqueta de clasificación|Aplica una etiqueta de clasificación de Azure Information Protection a los archivos de forma automática en función de las condiciones establecidas en la Directiva.| Box, una unidad, G Suite, SharePoint |
|Directiva de archivo y archivos|Archivo | Quitar etiqueta de clasificación | Quita una etiqueta de clasificación de Azure Information Protection de los archivos de forma automática en función de las condiciones establecidas en la Directiva. Solo puede quitar etiquetas si no incluyen protección y se aplicaron desde dentro de Cloud App Security, no etiquetas aplicadas directamente en Information Protection.| Box, una unidad, G Suite, SharePoint |
|Directiva de archivo, Directiva de actividad, Alertas | Aplicación |Requerir a los usuarios que inicien sesión de nuevo| Puede requerir a los usuarios que inicien sesión de nuevo en todas las aplicaciones de Office 365 y Azure AD como una solución rápida y eficaz en el caso de alertas de actividad sospechosa del usuario y cuentas en peligro. Encontrará la nueva acción de gobernanza en la configuración de directiva y las páginas de alertas, junto a la opción Suspender usuario. | Office 365, Azure AD |
|Files |Archivo |Restaurar de la cuarentena de usuario |Se restaura un usuario que estaba en cuarentena. |Box |
|Files |Archivo | Concederme permisos de lectura| Se concede permisos de lectura para el archivo a sí mismo con el fin de tener acceso al archivo y saber si existe o no una infracción en él.| G Suite|
|Files |Archivo | Permitir que los editores compartan | En Google Drive, el permiso predeterminado del editor de un archivo también permite el uso compartido. Esta acción de gobernanza hace lo contrario de “Quitar la capacidad de compartir de los editores” y permite que el editor comparta el archivo. | G Suite|
|Files |Archivo | Proteger | Proteja un archivo con Azure Information Protection aplicando una plantilla de la organización. | Office 365 (SharePoint y OneDrive) |
|Files |Archivo | Revocar mis propios permisos de lectura | Se revocan los permisos de lectura para el archivo de uno mismo. Esto es útil después de haberse concedido permisos manualmente para saber si un archivo tiene o no una infracción.| G Suite|
|Archivos, Directiva de archivo|Archivo | Transferir la propiedad de los archivos | Se cambia el propietario: en la directiva se elige un propietario específico. | G Suite|
|Archivos, Directiva de archivo|Archivo | Reducir el acceso público|Esta acción le permite establecer que los archivos disponibles públicamente solo estén disponibles con un vínculo compartido.| G Suite|
|Archivos, Directiva de archivo|Archivo | Quitar un colaborador | Se quita un colaborador específico de un archivo. | G Suite, Box, One Drive, SharePoint|
|Archivos, Directiva de archivo|Archivo | Convertir en privado| Solo los administradores del sitio pueden tener acceso al archivo, se quitan todos los recursos compartidos. | G Suite, One Drive, SharePoint |
|Archivos, Directiva de archivo|Archivo | Quitar usuarios externos | Se quitan todos los colaboradores externos de los dominios configurados como internos en la configuración. |G Suite, Box, One Drive, SharePoint|
|Archivos, Directiva de archivo|Archivo |Conceder permisos de lectura para el dominio|Se conceden permisos de lectura para el archivo en el dominio especificado, ya sea en todo el dominio o en un dominio específico. Esta acción es útil si desea quitar el acceso público después de conceder acceso al dominio de las personas que necesitan trabajar en él.| G Suite|
|Archivos, Directiva de archivo|Archivo | Poner en cuarentena de usuario | Se quitan todos los permisos del archivo y el archivo se mueve a una carpeta de cuarentena en la unidad raíz del usuario. Esta acción permite al usuario revisar el archivo y moverlo. Si se mueve de vuelta manualmente, no se restaura el uso compartido de archivos. | Box, One Drive, SharePoint |
|Files|Archivo|Vínculo de expiración compartido| Establezca una fecha de expiración para un vínculo compartido después de lo cual dejará de estar activo.|Box|
|Files|Archivo|Cambiar el nivel de acceso del vínculo de uso compartido|Cambia el nivel de acceso del vínculo compartido entre solo la empresa, solo colaboradores y público.| Box|
|Archivos, Directiva de archivo|Archivo | Quitar el acceso público| Si un archivo es suyo y lo pone en el acceso público, se vuelve accesible para cualquier persona configurada con acceso al archivo (dependiendo del tipo de acceso que tuviera el archivo). | G Suite|
|Archivos, Directiva de archivo|Archivo |Quitar el vínculo compartido directo| Quita un vínculo creado para el archivo que es público, pero que solo se comparte con personas específicas.|Box |
|Configuración > Configuración de Cloud Discovery| Cloud Discovery | Recalcular puntuaciones de Cloud Discovery |Se recalculan las puntuaciones en el catálogo de aplicaciones de Cloud tras un cambio en la métrica de puntuación.| Detección |
|Configuración > Configuración de Cloud Discovery > Administrar vistas de datos| Cloud Discovery | Crear vista de datos de filtro personalizado de Cloud Discovery|Se crea una vista de datos para obtener una vista más detallada de los resultados de la detección. Por ejemplo, intervalos de IP específicos. | Detección |
|Configuración > Configuración de Cloud Discovery > Eliminar datos| Cloud Discovery | Eliminar datos de Cloud Discovery |Se eliminan todos los datos recopilados de los orígenes de detección.| Detección |
|Configuración > Configuración de Cloud Discovery > Cargar registros manualmente/Cargar registros automáticamente | Cloud Discovery | Analizar datos de Cloud Discovery| Notificación de que todos los datos de registro se han analizado. | Detección |

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Actividades diarias para proteger el entorno de nube](daily-activities-to-protect-your-cloud-environment.md)

[!INCLUDE [Open support ticket](includes/support.md)]
