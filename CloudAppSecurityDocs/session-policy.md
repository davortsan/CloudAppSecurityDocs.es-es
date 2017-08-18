---
title: "Crear directivas de sesión para obtener visibilidad detallada de las actividades de la sesión del usuario y bloquear las descargas | Microsoft Docs"
description: "En este tema, se describe el procedimiento para configurar una directiva de sesión del proxy de Cloud App Security para obtener visibilidad detallada de las actividades de la sesión del usuario y bloquear las descargas."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 8/8/2017
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: 745df28a-654c-4abf-9c90-203841169f90
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 4b12d52703aa6b81a76e54626f06e5732fb3a6bf
ms.sourcegitcommit: 84f358a5dd0ab7f362dd3a2cf9999a6184fba856
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/14/2017
---
# <a name="session-policies"></a>Directivas de sesión  
Las directivas de sesión le permiten supervisar todo lo que hace un usuario en una sesión y le proporciona capacidades de control para bloquear actividades específicas que realizan los usuarios en esas sesiones, como la descarga de archivos.

Para poder crear una directiva de sesión, es necesario [implementar el proxy](proxy-deployment.md). Las directivas de sesión le permiten establecer reglas que definen la forma en que controla y supervisa las sesiones de los usuarios.
Por ejemplo, puede establecer una directiva para:
- Bloquear las descargas de cualquier archivo con la etiqueta de clasificación de Azure Information Protection "clasificado" desde dispositivos no administrados.
- Proteger las descargas de todos los archivos en los dispositivos no administrados, mediante el cifrado de Azure RMS.
- 

Haga lo siguiente para crear una directiva de sesión:  
  
1.  En la consola, haga clic en **Control**, seguido de **Directivas**.  
  
2.  Haga clic en **Crear directiva** y seleccione **Directiva de sesión**.  
  
3.  Asigne un nombre y una descripción a la directiva. Si quiere, puede basarla en una plantilla. Para obtener más información sobre las plantillas de directiva, vea [Controlar aplicaciones en la nube con directivas](control-cloud-apps-with-policies.md).  
  
3. Asigne a la directiva una **gravedad**. Si ha configurado Cloud App Security para que le envíe notificaciones cuando se producen coincidencias de directivas para un nivel de gravedad de política específico, esto se usará para determinar si la coincidencia de la directiva desencadenará una notificación o no.

4.  Dentro de **Categoría**, vincule la directiva al tipo de riesgo más adecuado. Este campo es meramente informativo y solo sirve para encontrar más fácilmente directivas específicas y las consiguientes alertas, según el tipo de riesgo.  Puede que el riesgo ya esté seleccionado previamente según la categoría para la que eligió crear la directiva. Las directivas de sesión están configuradas como **DLP** de forma predeterminada.  
  
5.  Para definir qué aplicaciones van a activar esta directiva, **cree un filtro para los archivos sobre los que esta directiva actuará**. 

 > [!NOTE] 
 > Al usar filtros de directiva, **Contiene** solo buscará palabras completas separadas por comas, puntos, espacios o caracteres de subrayado. Por ejemplo, si busca **malware** o **virus**, encontrará virus_malware_file.exe, pero no encontrará malwarevirusfile.exe. Si busca **malware.exe**, encontrará TODOS los archivos que contengan malware o exe en el nombre de archivo, mientras que si busca **"malware.exe"** (con comillas) solo encontrará los archivos que contengan exactamente "malware.exe". **Es igual a** solo buscará la cadena completa. Por ejemplo, si busca **malware.exe**, encontrará malware.exe pero no malware.exe.txt.  

6. Seleccione el **Tipo de control de sesión**.
    - Supervisión de todas las actividades: si selecciona Supervisar, se supervisarán las actividades de la sesión de las aplicaciones, pero no se bloquearán. Podrá supervisar todas las páginas internas específicas de la aplicación en la nube a la que se ha accedido y todas las descargas realizadas en cada aplicación específica. De forma predeterminada, las alertas se envían automáticamente al portal de Cloud App Security. Esto también le permite [exportar el registro de auditoría completo](#export-the-audit-log) de las actividades de sesión desde la pestaña Proxy.
    - Supervisión de todas las actividades y control de la descarga de archivos: si selecciona la opción de supervisar y controlar, tendrá todas las capacidades mencionadas anteriormente en **Supervisar todas las actividades** con el nivel adicional de control que le permite bloquear actividades específicas, como la descarga de archivos, en tiempo real. También podrá filtrar el contenido del archivo en función de la DLP integrada de Cloud App Security o una DLP externa.
 
7. En **Origen de la actividad**, seleccione a qué aplicaciones se aplicará la directiva, ya sea todas las aplicaciones o aplicaciones específicas.

8. Use los filtros para seleccionar qué usuarios, aplicaciones y dispositivos quiere que desencadenen una coincidencia de directiva. Para obtener una lista completa de filtros, consulte los [filtros de la directiva de sesión](#session-policy-filters).
  
9. Si elige la opción **Supervisión de todas las actividades y control de la descarga de archivos**, también puede establecer [filtros de archivos](#session-file-filters)

10. Si elige la opción **Supervisión de todas las actividades y control de la descarga de archivos**, también puede establecer opciones de **Inspección de contenido**. El DLP integrado permite filtrar archivos por su contenido. Para examinar archivos en busca de contenido, seleccione DLP integrado. Una vez habilitada la inspección de contenido, puede optar entre usar expresiones preestablecidas o buscar otras expresiones personalizadas, como una subcadena o una expresión regular propias.
Además, puede especificar una expresión regular para excluir un archivo de los resultados. Esto es muy útil si tiene un estándar de palabra clave de clasificación interna que quiera excluir de la directiva.
También puede decidir cuál es el número mínimo de infracciones de contenido que debe producirse antes de que el archivo se considere una infracción. Por ejemplo, puede elegir 10 si quiere recibir alertas sobre archivos con al menos 10 números de tarjeta de crédito en su contenido.
Cuando el contenido se compara con la expresión seleccionada, el texto de la infracción se reemplazará por caracteres "X". De manera predeterminada, las infracciones se enmascaran completamente y se muestran en su contexto mostrando 40 caracteres antes y después de la infracción. Los números del contexto de la expresión se reemplazan por caracteres "#" y nunca se almacenan en Cloud App Security. Puede seleccionar la opción Desenmascarar los últimos cuatro caracteres de una infracción para mostrarlos.

10. Si elige la opción **Supervisión de todas las actividades y control de la descarga de archivos**, también puede establecer **Acciones** que se llevarán a cabo cuando coincida la directiva:
    - Permitir: Si selecciona Permitir, los usuarios podrán descargar los archivos. 
    - Bloquear: Si selecciona **Bloquear**, cuando coincidan los requisitos de la directiva, el usuario no podrá descargar los archivos. El usuario recibirá un mensaje que indica que no tiene permiso para descargar los archivos.
    - Proteger: Si selecciona **Proteger**, el usuario podrá descargar los archivos, pero se cifrarán con Azure RMS. También puede establecer una acción predeterminada que se realizará si no se puede realizar el cifrado (bloquear o permitir la descarga).
 >[!WARNING]
 >Se recomienda encarecidamente crear primero la directiva con la acción **Permitir** y comprobar los resultados y, solo después de haber determinado que la directiva no bloquea a ningún usuario que no quiera, cambie la directiva a **Bloquear** las descargas.
 
 9. Establezca las alertas que quiera recibir cuando coincida la directiva. Puede establecer un límite para no recibir demasiadas alertas y puede seleccionar si quiere recibir las alertas como un mensaje de correo electrónico, un mensaje de texto o ambos.

10. Para ver las coincidencias de la directiva de sesión, haga clic en **Control** y, después, en **Directivas**. Filtre los resultados para mostrar solo las directivas de sesión con el filtro **Tipo** en la parte superior. Para obtener más información sobre las coincidencias de cada directiva, haga clic en una directiva. Haga clic en la pestaña **Historial** para ver el historial de los 6 meses anteriores con las coincidencias de directiva.     
  
## <a name="session-policy-reference"></a>Referencia de directiva de sesión  

En esta sección, se proporciona información de referencia sobre los filtros de directiva de sesión. 

### Filtros de sesión <a name="session-policy-filters"></a>

- Etiqueta de dispositivo: le permite excluir los dispositivos administrados al seleccionar **Conforme**, **Unido a dominio** y **Certificado de cliente válido**.
- Tipo de dispositivo: ningún valor, PC, móvil, tableta, otros
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

-   Ubicación: país desde el que se ha realizado la solicitud de acceso.    

- ISP registrado: 

-   Usuario: el usuario que realizó la actividad, que se puede filtrar en el dominio, grupo, nombre u organización. Para filtrar las actividades sin un usuario específico, puede usar el operador 'no establecido'.  
    -   Organización de usuario: unidad organizativa del usuario que ha realizado la actividad, por ejemplo, todas las actividades realizadas por usuarios de marketing o EMEA.  
    -   Grupo de usuarios: grupos de usuarios específicos que puede importar de aplicaciones conectadas, como administradores de Office 365.  
    -   Nombre de usuario: busca por un nombre de usuario específico. Para ver una lista de los usuarios de un grupo de usuarios específico, en el **Cajón de actividades**, haga clic en el nombre del grupo de usuarios. Esto le llevará a la página de cuentas, en la que se enumeran todos los usuarios del grupo. Desde ahí puede profundizar en los detalles de las cuentas de usuarios específicos del grupo.
       -  Los filtros **Grupo de usuarios** y **Nombre de usuario** se pueden filtrar aún más si se usa el filtro **Como** y se selecciona el rol del usuario, que puede ser uno de los siguientes:
            - Objeto de actividad solo: esto significa que el usuario o grupo de usuarios seleccionado no ha realizado la actividad en cuestión, sino que era el objeto de la actividad.
            - Solo actor: esto significa que el usuario o grupo de usuarios ha realizado la actividad.
            - Cualquier rol: esto significa que el usuario o grupo de usuarios ha participado en la actividad, como la persona que ha realizado la actividad o como objeto de la actividad.

-   Agente de usuario: agente de usuario desde el que se ha realizado la actividad.  
  
-   Etiqueta de agente de usuario: etiqueta de agente de usuario integrada, por ejemplo, todas las actividades desde exploradores o sistemas operativos obsoletos.  

### Filtros de archivo de sesión <a name="session-file-filters"></a>

-   Etiqueta de clasificación: busca archivos con etiquetas específicas. Son las siguientes:
    - Etiquetas de Azure Information Protection. Esto requiere la integración con Azure Integration Protection.
    - Etiquetas de Cloud App Security. proporciona actualmente más información sobre los archivos que examina. Ahora ya puede saber si se ha impedido que la DLP de Cloud App Security inspeccione los archivos porque estaban dañados o cifrados. Por ejemplo, puede configurar directivas para que le alerten y pongan en cuarentena archivos protegidos con contraseña que se comparten externamente de la manera que se indica a continuación: 
        - Cifrado con Azure RMS: archivos cuyo contenido no se ha inspeccionado porque tienen establecido un cifrado de Azure RMS.
        - Cifrado con contraseña: archivos cuyo contenido no se ha inspeccionado porque el usuario los ha protegido con una contraseña.
        - Archivo dañado: archivos cuyo contenido no se ha inspeccionado porque no se ha podido leer su contenido.

-   Tipo de archivo: Cloud App Security toma el tipo MIME recibido del servicio y examina el archivo para determinar el tipo de archivo real. Tenga en cuenta que este examen se aplica a archivos pertinentes para el examen de datos (documentos, imágenes, presentaciones, hojas de cálculo, archivos de texto y archivos de almacenamiento o ZIP). El filtro funciona por tipo de archivo/carpeta, por ejemplo, Todas las carpetas que son… o Todos los archivos de hoja de cálculo que son...
-   Extensión: se centra en extensiones de archivo específicas, por ejemplo, todos los archivos que son ejecutables (exe).  
  
-   Nombre de archivo: nombre de archivo o subcadena del nombre tal como se define en la aplicación en la nube, por ejemplo, Todos los archivos con una contraseña en su nombre.   
  
-   Tamaño de archivo: tamaño de archivo en MB, mayor que un tamaño determinado, inferior a un tamaño determinado o entre un intervalo.    


>[!NOTE]
> Para borrar los filtros, haga clic en el icono de borrar filtros ![icono de borrar filtros](./media/clear-filters.png).

  
## <a name="see-also"></a>Consulte también  
[Actividades diarias para proteger el entorno de nube](daily-activities-to-protect-your-cloud-environment.md)   
[Para obtener soporte técnico, visite la página de soporte técnico asistido de Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Los clientes Premier también pueden elegir Cloud App Security directamente desde el Portal Premier.](https://premier.microsoft.com/)  
  
  