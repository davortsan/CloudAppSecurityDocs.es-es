---
title: Crear directivas de acceso para supervisar y bloquear el acceso a las aplicaciones en la nube | Microsoft Docs
description: En este tema, se describe el procedimiento para configurar una directiva de acceso para supervisar y bloquear el acceso a las aplicaciones en la nube.
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 8/8/2017
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: ddeabd1d-f017-4756-94b2-194292e60c07
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: b070c4f6364f8beccd397102fa00642560414326
ms.sourcegitcommit: 4cf65f627f2d370ee4a4decae1acbb9658874056
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/13/2017
---
# <a name="access-policies"></a>Directivas de acceso  
Las directivas de acceso le permiten supervisar y bloquear el acceso a aplicaciones específicas en función del usuario, la ubicación o el dispositivo.

Para poder crear una directiva de acceso, es necesario [implementar el proxy](proxy-deployment.md). Las directivas de acceso le permiten establecer reglas que definen la forma en que administra y supervisa el acceso de los usuarios a las aplicaciones en la nube.
Por ejemplo, puede establecer una directiva para:
- Bloquear el acceso a todas las aplicaciones en la nube desde dispositivos no administrados.
- Bloquear el acceso desde países específicos, por ejemplo, todos los países que no sean Inglaterra.
- Bloquear el acceso a todos los grupos de usuarios que no sean Ventas y Administradores a Salesforce.
- Permitir el acceso pero supervisar todos los intentos de inicio de sesión y enviar una alerta cuando intenta iniciar sesión un usuario que no pertenece a un grupo de usuarios específico.

Para crear una directiva de acceso, siga este procedimiento:  
  
1.  En la consola, haga clic en **Control**, seguido de **Directivas**.  
  
2.  Haga clic en **Crear directiva** y seleccione **Directiva de acceso**.  
  
3.  Asigne un nombre y una descripción a la directiva. Si quiere, puede basarla en una plantilla. Para obtener más información sobre las plantillas de directiva, vea [Controlar aplicaciones en la nube con directivas](control-cloud-apps-with-policies.md).  
  
3. Asigne a la directiva una **gravedad**. Si ha configurado Cloud App Security para que le envíe notificaciones cuando se producen coincidencias de directivas para un nivel de gravedad de política específico, esto se usará para determinar si la coincidencia de la directiva desencadenará una notificación o no.

4.  Dentro de **Categoría**, vincule la directiva al tipo de riesgo más adecuado. Este campo es meramente informativo y solo sirve para encontrar más fácilmente directivas específicas y las consiguientes alertas, según el tipo de riesgo.  Puede que el riesgo ya esté seleccionado previamente según la categoría para la que eligió crear la directiva. De forma predeterminada, las directivas de acceso se establecen en **Control de acceso**.  
  
5.  Para definir qué aplicaciones van a activar esta directiva, **cree un filtro para los archivos sobre los que esta directiva actuará**. 

 > [!NOTE] 
 > Al usar filtros de directiva, **Contiene** solo buscará palabras completas separadas por comas, puntos, espacios o caracteres de subrayado. Por ejemplo, si busca **malware** o **virus**, encontrará virus_malware_file.exe, pero no encontrará malwarevirusfile.exe. Si busca **malware.exe**, encontrará TODOS los archivos que contengan malware o exe en el nombre de archivo, mientras que si busca **"malware.exe"** (con comillas) solo encontrará los archivos que contengan exactamente "malware.exe". **Es igual a** solo buscará la cadena completa. Por ejemplo, si busca **malware.exe**, encontrará malware.exe pero no malware.exe.txt.  

6.   En **Origen de la actividad**, seleccione a qué aplicaciones se aplicará la directiva, ya sea todas las aplicaciones o aplicaciones específicas.

7. Use los filtros para seleccionar qué usuarios, aplicaciones y dispositivos quiere que desencadenen una coincidencia de directiva. Para obtener una lista completa de filtros, consulte los [filtros de la directiva de acceso](#access-policy-filters).

8.  Elija las **Acciones** que quiera que Cloud App Security lleve a cabo cuando detecte una coincidencia:
    - Permitir y alertar: si selecciona Permitir, el acceso a las aplicaciones se supervisará, pero no se bloqueará. De forma predeterminada, si está seleccionado **Permitir**, las alertas se envían automáticamente al portal de Cloud App Security. 
    - Bloquear: Si selecciona **Bloquear**, cuando coincidan los requisitos de la directiva, el usuario o dispositivo no podrá acceder a la aplicación en la nube. El usuario recibirá un mensaje que indica que no tiene acceso a la aplicación.
  
>[!WARNING]
>Se recomienda encarecidamente crear primero la directiva con la acción **Permitir** y comprobar los resultados y, solo después de haber determinado que la directiva no bloquea a ningún usuario que no quiera, cambie la directiva a **Bloquear** acceso.
  
9. Establezca las alertas que quiera recibir cuando coincida la directiva. Puede establecer un límite para no recibir demasiadas alertas y puede seleccionar si quiere recibir las alertas como un mensaje de correo electrónico, un mensaje de texto o ambos.

10. Para ver las coincidencias de la directiva de acceso, haga clic en **Control** y, después, en **Directivas**. Filtre los resultados para mostrar solo las directivas de acceso con el filtro **Tipo** en la parte superior. Para obtener más información sobre las coincidencias de cada directiva, haga clic en una directiva. Haga clic en la pestaña **Historial** para ver el historial de los 6 meses anteriores con las coincidencias de directiva.     
  
## Referencia de directiva de acceso <a name="access-policy-filters"></a>

En esta sección, se proporciona información de referencia sobre los filtros de directiva de acceso. 

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
    
>[!NOTE]
> Para borrar los filtros, haga clic en el icono de borrar filtros ![icono de borrar filtros](./media/clear-filters.png).


## <a name="see-also"></a>Consulte también  
[Actividades diarias para proteger el entorno de nube](daily-activities-to-protect-your-cloud-environment.md)   
[Para obtener soporte técnico, visite la página de soporte técnico asistido de Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Los clientes Premier también pueden elegir Cloud App Security directamente desde el Portal Premier.](https://premier.microsoft.com/)  
  
  