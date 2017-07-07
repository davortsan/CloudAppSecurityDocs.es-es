---
title: "Proteger la organización frente a amenazas | Microsoft Docs"
description: "En este tema se describe el escenario para proteger su organización contra amenazas en su entorno en la nube."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 6/27/2017
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: 0017be99-29c3-468e-a181-255e343ed4f5
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 7bad1e1ae6196b684ac35d063558fad22bc3689f
ms.sourcegitcommit: 2f4474084c7e07ac4853945ab5aa1ea78950675d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/28/2017
---
# <a name="protecting-your-organization-against-threats"></a>Proteger la organización frente a amenazas  

Identifique usos de alto riesgo y problemas relacionados con la seguridad en la nube, detecte comportamientos inusuales de los usuarios y evite amenazas en sus aplicaciones en la nube conectadas. Supervise la actividad de los usuarios y los administradores, y defina directivas para recibir automáticamente alertas sobre comportamientos sospechosos o actividades de riesgo en sus entornos autorizados. Use la extensa base de datos sobre amenazas y los datos de investigación sobre seguridad de Microsoft. Las directivas de detección de amenazas le ayudan a asegurarse de que sus aplicaciones autorizadas cuenten con todos los controles de seguridad necesarios y a tenerlo todo bajo control.
 
## <a name="mass-download-by-a-single-user-data-exfiltration-by-an-insider"></a>Descarga masiva por parte de un solo usuario (filtración de datos internos)

Este caso de uso se aplica a Office 365, G Suite, Box, Dropbox y Salesforce.

### <a name="the-threat"></a>LA AMENAZA
Una persona interna malintencionada puede extraer datos de Office 365 u otras aplicaciones en la nube si descarga varios archivos u obtiene acceso a estos durante un breve período de tiempo.

### <a name="the-solution"></a>LA SOLUCIÓN
Detecte rápidamente si un usuario descarga un gran número de archivos o accede a estos.

#### <a name="prerequisites"></a>Requisitos previos

[Conecte](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md) al menos una aplicación en la nube a Cloud App Security.

#### <a name="setting-up-monitoring"></a>Configuración de la supervisión

1.  De forma predeterminada, Cloud App Security examina la red para establecer una base de referencia. Esto permite identificar los patrones de actividad habitual de sus usuarios en la nube, tanto el hecho en sí como el momento en el que actúen. 

2. Establezca una directiva que inspeccione las aplicaciones en la nube en caso de descargas masivas y alerte si se produce algo fuera de lo común:

    1. En la página **Directivas**, haga clic en [**Crear directiva de actividad**](user-activity-policies.md). 
   

    2. En el campo [**Plantilla de directiva**](policy-template-reference.md), elija **Descarga masiva por parte de un solo usuario**.
    
    3. Opcionalmente, puede ajustar el filtro de actividad repetida.
    
    4. Haga clic en **Crear**. 
   
     
2. Investigación de las coincidencias
    
    1. En la página **Directivas**, haga clic en el nombre de directiva para ir a **Informe la directiva** y revise las coincidencias que se activaron para la directiva.

    2. Puede investigar la coincidencia haciendo clic en una específica para abrir el cajón de actividad. En el cajón, puede ver las otras directivas que coinciden con esta actividad. 
    
    3. Puede comprobar los archivos que haya descargado el usuario. Para ello, haga clic en los objetos de actividad en el **Cajón de actividades** y, después, en el nombre del archivo. Esto le llevará al archivo en la tabla de archivos. Allí puede ver si los archivos son propiedad del usuario y con quién se comparten. De este modo, podrá determinar si se trata de archivos con los que el usuario suele trabajar o si son una dirección IP interna que no se debe descargar.
     


#### <a name="validating-your-policy"></a>Validación de la directiva

1. Para simular una alerta, descargue una cantidad de documentos (superior al umbral establecido) desde las aplicaciones conectadas en la nube en un breve período de tiempo, según el período establecido en la directiva (por ejemplo, 30 descargas en menos de 5 minutos).
3. Vaya al informe de directiva. Al cabo de poco tiempo, debería mostrarse una coincidencia de directiva de actividad. 
4. Puede hacer clic en la coincidencia para ver qué archivos se han descargado.  

#### <a name="removing-the-risk"></a>Eliminación del riesgo

Una vez validada y perfeccionada la directiva, quite los posibles falsos positivos que puedan haber coincidido con la directiva, como las cuentas de servicio que sincronizan archivos, las carpetas de imágenes de eventos de la empresa, etc. Luego, haga lo siguiente: 
  1. Puede realizar [acciones de gobierno](governance-actions.md). Para ello, abra la actividad en el cajón de actividades y haga clic en el nombre del archivo en **Objetos de actividad**.

  2. Póngase en contacto con los usuarios para descubrir por qué necesitan copias de tantos archivos corporativos en sus equipos.

 
## <a name="admin-activity-from-outside-your-organizations-network"></a>Actividad de administración desde fuera de la red de la organización

Este caso de uso se aplica a Office 365, G Suite, Box, Dropbox, Salesforce y Okta.

### <a name="the-threat"></a>LA AMENAZA
Un atacante externo ha puesto en peligro una cuenta de administrador. Las cuentas de administrador son las más confidenciales de la organización, ya que tienen los privilegios más elevados y pueden obtener acceso a toda la información de la organización. Por lo general, la actividad administrativa debe realizarse desde la oficina como parte del trabajo del administrador, y no desde ubicaciones remotas o dispositivos no reconocidos.

### <a name="the-solution"></a>LA SOLUCIÓN
Detecte en qué momento las personas que se hacen pasar por administradores se conectan a la aplicación en la nube desde direcciones IP externas y realizan la actividad de administración.

#### <a name="prerequisites"></a>Requisitos previos

- [Conecte](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md) al menos una aplicación en la nube a Cloud App Security.

- Vaya a **Configuración** > **Intervalos de direcciones IP**. Agregue los intervalos de direcciones IP de ambas subredes internas y sus direcciones IP públicas de salida y etiquételas como **Corporativas**.

#### <a name="setting-up-monitoring"></a>Configuración de la supervisión

1.  Empiece a supervisar sus aplicaciones en la nube mediante la configuración de una directiva que detecte la actividad de administración fuera de la red en sus aplicaciones en la nube y le avise si sucede algo inusual:

    1. En la página **Directivas**, haga clic en [**Crear directiva de actividad**](user-activity-policies.md). 
   

    2. En el campo [**Plantilla de directiva**](policy-template-reference.md), seleccione **Actividad administrativa desde una dirección IP no corporativa** y establezca el **Tipo de actividad** en **inicio de sesión**. Después, seleccione **Usuario** y **Desde el grupo** y elija el grupo al que pertenecen los administradores.
    
    3. Puede ajustar la directiva para establecer el número de actividades repetidas que quiere que se considere sospechoso.
    
    4. Haga clic en **Crear**. 
   
     
2. Investigación de las coincidencias
    
    1. En la página **Directivas**, haga clic en el nombre de directiva para ir a **Informe la directiva** y revise las coincidencias que se activaron para la directiva.

    2. Puede investigar la coincidencia haciendo clic en una específica para abrir el cajón de actividad. En el cajón, puede ver las otras directivas que coinciden con esta actividad. 
     
#### <a name="validating-your-policy"></a>Validación de la directiva

1. Para simular una alerta, desde un equipo con una dirección IP que no forme parte de la red corporativa, realice una cantidad de actividades de administración superior al umbral establecido durante un breve período de tiempo, en función del período que haya establecido en la directiva (por ejemplo, 10 actividades en menos de cinco minutos).
3. Vaya al informe de directiva. Al cabo de poco tiempo, debería mostrarse una coincidencia de directiva de actividad. 
4. Puede hacer clic en la coincidencia para ver qué actividades se han realizado. 

#### <a name="removing-the-risk"></a>Eliminación del riesgo

Una vez validada y perfeccionada la directiva, quite posibles falsos positivos que puedan haber coincidido con la directiva. Luego, haga lo siguiente: 
  1. Puede realizar [acciones de gobierno](governance-actions.md). Para ello, abra la actividad en el cajón de actividades y haga clic en el nombre del **Usuario**.

  2. En la página de usuario que se abre, verá un gráfico de la actividad del usuario durante el último mes y las ubicaciones en las que se ha detectado actividad del usuario durante el último mes, así como las pertenencias a grupos, la actividad de la aplicación y las cuentas. 
  
  3. Si es necesario, haga clic en **contacto** para enviar un mensaje de correo electrónico al usuario para avisarle de que se ha infringido la seguridad de su cuenta.

 ![autogobierno externo](./media/auto-gov-external.png)

   2. Después de que se valide por completo, puede establecerla para realizar acciones de gobierno automáticas. Por ejemplo, puede **suspender el usuario** o **quitar las colaboraciones del usuario**.


## <a name="see-also"></a>Consulte también  
[Actividades diarias para proteger el entorno de nube](daily-activities-to-protect-your-cloud-environment.md)   
[Para obtener soporte técnico, visite la página de soporte técnico asistido de Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Los clientes Premier también pueden elegir Cloud App Security directamente desde el Portal Premier.](https://premier.microsoft.com/)  
  
  