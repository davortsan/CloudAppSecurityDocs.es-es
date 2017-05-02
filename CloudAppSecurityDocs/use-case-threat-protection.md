---
title: "Información general sobre el escenario de protección contra amenazas | Microsoft Docs"
description: "En este tema se describe el escenario para proteger su organización contra amenazas en su entorno en la nube."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 4/30/2017
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: 0017be99-29c3-468e-a181-255e343ed4f5
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: fcc793f0fea71ef0666a7c99034185c5cd5fd894
ms.sourcegitcommit: 7e9ae94cb4f90fbccaa84f19bdebb4652a425e45
translationtype: HT
---
# <a name="controlling-and-protecting-your-files"></a>Control y protección de los archivos  

Identifique usos de alto riesgo y problemas relacionados con la seguridad en la nube, detecte comportamientos inusuales de los usuarios y evite amenazas en sus aplicaciones en la nube autorizadas. Supervise la actividad de los usuarios y los administradores, y defina directivas para recibir automáticamente alertas sobre comportamientos sospechosos o actividades de riesgo en sus entornos autorizados. Use la extensa base de datos sobre amenazas y los datos de investigación sobre seguridad de Microsoft. Las directivas de detección de amenazas le ayudan a asegurarse de que sus aplicaciones autorizadas cuenten con todos los controles de seguridad necesarios y a tenerlo todo bajo control.
 
## <a name="massive-quantities-of-files-are-being-downloaded-insider-data-exfiltration"></a>Descarga de grandes cantidades de archivos (filtración de datos internos)

Este caso de uso se aplica a Office 365, Google Apps, Box, Dropbox y Salesforce.

### <a name="the-threat"></a>LA AMENAZA
Un atacante con una cuenta en peligro puede extraer datos de Office 365 u otras aplicaciones en la nube descargando varios archivos o accediendo a estos.

### <a name="the-solution"></a>LA SOLUCIÓN
Detecte rápidamente si un usuario descarga un gran número de archivos o accede a estos.

#### <a name="prerequisites"></a>Requisitos previos

[Conecte](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md) al menos una aplicación en la nube a Cloud App Security.

#### <a name="setting-up-monitoring"></a>Configuración de la supervisión

1.    De forma predeterminada, Cloud App Security examina la red para establecer una base de referencia. Esto permite identificar los patrones de actividad habitual de sus usuarios en la nube, tanto el hecho en sí como el momento en el que actúen. 

2. Además, es importante comenzar a supervisar sus aplicaciones en la nube mediante la configuración de una directiva que detecte descargas masivas en sus aplicaciones en la nube y le avise si sucede algo inusual:

    1. En la página **Directivas**, haga clic en [**Crear directiva de actividad**](user-activity-policies.md). 
    ![crear directiva de actividad](./media/create-activity-policy.png)

    2. En el campo [**Plantilla de directiva**](policy-template-reference.md), elija **Descarga masiva por parte de un solo usuario**.
    
    3. Opcionalmente, puede ajustar el filtro de actividad repetida.
    
    4. Haga clic en **Aplicar plantilla**. 
    ![plantilla de directiva de actividad](./media/activity-policy-template.png)
     
2. Investigación de las coincidencias
    
    1. En la página **Directivas**, haga clic en el nombre de directiva para ir a **Informe la directiva** y revise las coincidencias que se activaron para la directiva.

    2. Puede investigar la coincidencia haciendo clic en una específica para abrir el cajón de actividad. En el cajón, puede ver las otras directivas que coinciden con esta actividad. 
     


#### <a name="validating-your-policy"></a>Validación de la directiva

1. Para simular una alerta, descargue varias veces y en un período corto unos cuantos documentos de sus aplicaciones en la nube conectadas, tal como se define en la configuración de la directiva (por ejemplo, 10 veces en menos de 30 minutos).
3. Vaya al informe de directiva. Al cabo de poco tiempo, debería mostrarse una coincidencia de directiva de actividad. 
4. Puede hacer clic en la coincidencia para ver qué archivos se han descargado. La propia coincidencia se enmascarará para proteger los datos confidenciales. 

#### <a name="removing-the-risk"></a>Eliminación del riesgo

Una vez validada y perfeccionada la directiva, quite posibles falsos positivos que puedan haber coincidido con la directiva. Luego, haga lo siguiente: 
  1. Puede tomar [acciones de gobierno](governance-actions.md) inmediatas haciendo clic en los tres puntos situados al final de la fila y seleccionando la acción de gobierno relevante, por ejemplo, **Poner en cuarentena de usuario**.

 ![autogobierno externo](./media/auto-gov-external.png)

   2. Después de que se valide por completo, puede establecerla para realizar acciones de gobierno automáticas. Por ejemplo, en SharePoint y OneDrive puede realizar las acciones **Quitar usuarios externos** o **Poner en cuarentena de usuario** y, para G Suite y Box, puede realizar las acciones **Quitar usuarios externos** y **Quitar el acceso público**.

  ![aplicación de acciones de gobierno automáticas](./media/apply-automatic-gov-actions.png)



## <a name="see-also"></a>Consulte también  
[Actividades diarias para proteger el entorno de nube](daily-activities-to-protect-your-cloud-environment.md)   
[Para obtener soporte técnico, visite la página de soporte técnico asistido de Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Los clientes Premier también pueden elegir Cloud App Security directamente desde el Portal Premier.](https://premier.microsoft.com/)  
  
  