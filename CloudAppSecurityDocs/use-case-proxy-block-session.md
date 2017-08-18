---
title: "Cómo bloquear las descargas de información confidencial desde dispositivos no administrados | Microsoft Docs"
description: "En este tema, se describe el escenario para proteger su organización contra descargas de información confidencial desde dispositivos no administrados."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 8/15/2017
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: d1861218-a16f-4058-bd0e-34cc4a9413d6
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 4936805c3777ce4ff82735637941cbe528315eb4
ms.sourcegitcommit: 84f358a5dd0ab7f362dd3a2cf9999a6184fba856
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/14/2017
---
# <a name="blocking-downloads-on-unmanaged-devices"></a>Bloquear descargas en dispositivos no administrados

Hoy en día, los administradores de TI se encuentran entre la espada y la pared: por una parte, quiere permitir que los empleados sean productivos, y eso significa tener el acceso y la capacidad de trabajar todo el tiempo, desde cualquier dispositivo. Por otra parte, quiere proteger los activos de la empresa, y eso incluye la información propietaria y con privilegios. ¿Cómo puede conceder acceso a sus empleados a las aplicaciones en la nube, pero proteger los datos? El proxy de Cloud App Security proporciona un alto nivel de control sobre lo que se permite y lo que no se permite en las aplicaciones en la nube. 

## <a name="how-does-cloud-app-security-detect-unmanaged-devices"></a>¿Cómo detecta Cloud App Security los dispositivos no administrados?
.

>[!NOTE]
> Este caso de uso se aplica a .

## <a name="the-threat"></a>LA AMENAZA
Un administrador de cuentas de su organización quiere comprobar algo en Salesforce desde casa durante el fin de semana, en su teléfono móvil personal. La cuenta incluye información que puede ser personal o de la tarjeta de crédito del cliente. El teléfono no está administrado, lo que significa que, si descarga los documentos de Salesforce en su teléfono, puede estar infectado con malware o, si el dispositivo se pierde o lo roban, puede no estar protegido por contraseña y cualquier persona que lo encuentre tendrá acceso a información confidencial.

## <a name="the-solution"></a>LA SOLUCIÓN
Proteja su organización mediante la supervisión del uso de aplicaciones en la nube en Cloud App Security y la creación de una directiva de proxy para controlar y bloquear actividades desde dispositivos no administrados.

## <a name="prerequisites"></a>Requisitos previos

[Implemente](proxy-deployment.md) el proxy de Cloud App Security para Salesforce.

## <a name="set-up-unmanaged-device-detection"></a>Configurar la detección de dispositivos no administrados


## <a name="create-a-session-policy"></a>Crear una directiva de sesión
Las directivas de sesión le permiten supervisar todo lo que hace un usuario en una sesión y le conceden capacidades de control, de modo que pueda bloquear y proteger la descarga de archivos.


1.  En la consola, haga clic en **Control**, seguido de **Directivas**.  
  
2.  Haga clic en **Crear directiva** y seleccione **Directiva de sesión**.  
  
3.  Asigne un nombre y una descripción a la directiva, por ejemplo, **Bloquear descargas de SF en dispositivos no administrados**.  
  
3. Asigne a la directiva una **gravedad**. Si ha configurado Cloud App Security para que le envíe notificaciones cuando se producen coincidencias de directivas para un nivel de gravedad de política específico, esto se usará para determinar si la coincidencia de la directiva desencadenará una notificación o no.

4.  Puede dejar la configuración **Categoría** como **DLP**.  
  
6. En **Tipo de control de sesión**, seleccione **Supervisión de todas las actividades y control de la descarga de archivos**. Esto le otorga la capacidad de supervisar todo lo que hacen los usuarios en una sesión de Salesforce y le proporcionará control para bloquear y proteger las descargas en tiempo real. También podrá filtrar el contenido del archivo en función de la DLP integrada de Cloud App Security o una DLP externa.
 
7. En **Origen de la actividad**, haga clic en **Seleccione aplicaciones de la lista siguiente** y seleccione **Salesforce**.

8. En la sección de filtros de actividad, seleccione **Tipo de dispositivo** y, después, **no es igual a** y seleccione **Conforme**, **Unido a dominio** y **Certificado de cliente válido**.
  
8. Establezca Cloud App Security para que reconozca qué archivos y datos considera privados:

    - En la sección de filtros de archivo, seleccione los archivos confidenciales. Si trabaja con Azure Information Protection, puede seleccionar **Etiqueta de clasificación** y, después, seleccionar las etiquetas que usa para archivos clasificados.
    
    -  Habilite la **Inspección de contenido** para permitir que Cloud App Security examine de forma interna los archivos en busca de contenido clasificado. Por ejemplo, puede seleccionar **Incluir archivos que coincidan con una expresión preestablecida** y, después, seleccionar **Todos los países: finanzas, número de tarjeta de crédito**.

10. En esta fase, en **Acciones** que se llevarán a cabo cuando coincida la directiva, seleccione:
    - Permitir: Si selecciona Permitir, los usuarios podrán descargar los archivos. 
    o
    - Proteger: Si selecciona **Proteger**, el usuario podrá descargar los archivos, pero se cifrarán con Azure RMS. También puede establecer una acción predeterminada que se realizará si no se puede realizar el cifrado (bloquear o permitir la descarga).
 
 >[!WARNING]
 >Se recomienda encarecidamente no **Bloquear** las descargas antes de ejecutar la directiva en primer lugar en modo **Permitir** y comprobar que los resultados son como se esperaba. Después de determinar que la directiva no bloquea a ningún usuario sin querer, cambie la directiva para **Bloquear** las descargas.
 
 9. Establezca las alertas que quiera recibir cuando coincida la directiva. Puede establecer un límite para no recibir demasiadas alertas y puede seleccionar si quiere recibir las alertas como un mensaje de correo electrónico, un mensaje de texto o ambos.

10. Para ver las coincidencias de la directiva de sesión, haga clic en **Control** y, después, en **Directivas**. Filtre los resultados para mostrar solo las directivas de sesión con el filtro **Tipo** en la parte superior. Para obtener más información sobre las coincidencias de cada directiva, haga clic en una directiva. Haga clic en la pestaña **Historial** para ver el historial de los 6 meses anteriores con las coincidencias de directiva.     
  
## <a name="validate-your-policy"></a>Validar la directiva

1. Para simular una alerta, desde un dispositivo no administrado, inicie sesión en Salesforce e intente descargar un archivo.
3. Vaya al informe de directiva. Una coincidencia de directiva de sesión debe aparecer en breve. 
4. Puede hacer clic en la coincidencia para ver qué archivos se han descargado. La propia coincidencia se enmascarará para proteger los datos confidenciales. 

## <a name="blocking-and-protecting-your-sensitive-information"></a>Bloquear y proteger información confidencial

Una vez validada y perfeccionada la directiva, quite posibles falsos positivos que puedan haber coincidido con la directiva. Luego, haga lo siguiente: 

1. Cuando se produce una coincidencia con una directiva de sesión, puede corregirlo al establecer [acciones de gobierno](governance-actions.md) automatizadas.

2. Para ello, edite la directiva que ha creado antes y establezca **Acciones** en **Bloquear** descargas cuando coincida con la directiva. El usuario no podrá descargar los archivos y recibirá un mensaje que indica que no tiene permiso para descargar los archivos.
  
 
 ## <a name="see-also"></a>Consulte también  
[Actividades diarias para proteger el entorno de nube](daily-activities-to-protect-your-cloud-environment.md)   
[Para obtener soporte técnico, visite la página de soporte técnico asistido de Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Los clientes Premier también pueden elegir Cloud App Security directamente desde el Portal Premier.](https://premier.microsoft.com/)  
  
  