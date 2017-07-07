---
title: "Información general sobre el escenario de protección contra amenazas | Microsoft Docs"
description: "En este tema se describe el escenario para proteger su organización contra amenazas en su entorno en la nube."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 5/21/2017
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: 7a06a243-9ec2-4a11-8db2-bc065cdfef64
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 9359935410495345820bb509984d8533cb6fa070
ms.sourcegitcommit: 2f4474084c7e07ac4853945ab5aa1ea78950675d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/28/2017
---
# <a name="protecting-your-organization-from-ransomware"></a>Proteger la organización frente a ransomware

En el ataque de ransomware masivo más reciente, WannaCry asestó un duro golpe al mundo cibernético, ya que infectó aproximadamente 200 000 equipos en 150 países. Con el aumento de los ataques de ransomware en los últimos años, con una media de 25 000 ataques al mes en 2015 y 56 000 en 2016, es imprescindible para la ciberseguridad ser proactivos a la hora de asegurarse de que la red y la nube no están en peligro. En este artículo se explica cómo se puede usar Cloud App Security para supervisar la nube, detectar y mitigar las amenazas y aplicar los procedimientos recomendados para proteger el entorno contra el ransomware.

## <a name="what-is-ransomware"></a>¿Qué es el ransomware?
El ransomware es un ataque cibernético en el que el atacante envía un archivo que puede bloquear el acceso al equipo y cifrar los archivos. A menudo, el atacante conserva los archivos para pedir un rescate y no los descifra hasta que recibe el pago, tras lo cual restaura el acceso al equipo, los archivos o aplicaciones LOB críticas. Los ataques de ransomware pueden afectar a cualquier equipo, hogar, oficina, red o servidor. De hecho, dado que las grandes organizaciones están integradas por numerosos usuarios que pueden abrir accidentalmente un archivo que libera ransomware en la red, son estas las que corren un mayor riesgo de tener que pagar al atacante para detener el ransomware y restaurar el acceso a los archivos o los equipos.

>[!NOTE]
> Este caso de uso se aplica a Office 365, G Suite, Box y Dropbox.

## <a name="the-threat"></a>LA AMENAZA
Un usuario de la organización es víctima de un ataque de ransomware. Es posible que, sin saberlo, el usuario haya abierto un correo electrónico infectado y haya ejecutado ransomware que infecta todos sus archivos, incluidos los archivos sincronizados en la nube.

## <a name="the-solution"></a>LA SOLUCIÓN
Detecte el posible ransomware en el entorno en la nube. Para ello, cree una directiva para notificarle en caso de que detecte actividad sospechosa y configure acciones automatizadas para impedir que los archivos de ransomware se guarden en la nube.

## <a name="prerequisites"></a>Requisitos previos

[Conecte](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md) al menos una aplicación en la nube (Office 365, G Suite, Box y Dropbox) con Cloud App Security.

## <a name="setting-up-monitoring"></a>Configuración de la supervisión

1.  De forma predeterminada, Cloud App Security examina la red para establecer una base de referencia. Esto permite identificar los patrones de actividad habitual de sus usuarios en la nube, tanto el hecho en sí como el momento en el que actúen. 

2. Además, es importante empezar a supervisar las aplicaciones en la nube mediante la configuración de una directiva que detecte descargas masivas en las aplicaciones en la nube y le avise si sucede algo inusual:

    1. En la pestaña **Control**, haga clic en [**Plantillas**](policy-template-reference.md). 
   
    2. En la lista [**Plantilla de directiva**](policy-template-reference.md), seleccione **Actividad potencial de ransomware**. 
       ![plantilla de ransomware](./media/ransomware-template.png)
    3. Esta plantilla está diseñada para que busque de forma predeterminada la actividad típica de los ataques de ransomware, así como los archivos y las carpetas asociados al ransomware conocido. Opcionalmente, puede establecer el tipo de alerta que recibirá (correo electrónico y mensaje de texto) cuando se produce una coincidencia con la directiva.
        ![plantilla de ransomware](./media/ransomware-template-fields.png)
    4. Haga clic en **Crear**. 
   
     
2. Investigación de las coincidencias
    
    1. En la página **Directivas**, haga clic en el nombre de directiva para ir a **Informe la directiva** y revise las coincidencias que se activaron para la directiva.

    2. Puede investigar la coincidencia haciendo clic en una específica para abrir el cajón de actividad. En el cajón, puede ver las otras directivas que coinciden con esta actividad. 
     
## <a name="validating-your-policy"></a>Validación de la directiva

1. Para simular una alerta, cambie la extensión de 30 archivos a .wncry y cárguelos en el sitio de SharePoint.
3. Vaya al informe de directiva. Al cabo de poco tiempo, debería mostrarse una coincidencia de directiva de actividad. 
4. Puede hacer clic en la coincidencia para ver qué archivos se han descargado. La propia coincidencia se enmascarará para proteger los datos confidenciales. 

## <a name="remediating-attacks-and-preventing-risk"></a>Corregir ataques y evitar el riesgo

Una vez validada y perfeccionada la directiva, quite posibles falsos positivos que puedan haber coincidido con la directiva. Luego, haga lo siguiente: 
1. Cuando se produce una coincidencia con una directiva de ransomware, puede corregirlo mediante el establecimiento de [acciones de gobierno](governance-actions.md) automatizadas.

2. Para evitar ataques futuros, establezca la directiva de modo que realice acciones de gobierno automáticas. Por ejemplo, en SharePoint y OneDrive, puede establecer la directiva de modo que se **suspenda el usuario** automáticamente.

 ## <a name="see-also"></a>Consulte también  
[Actividades diarias para proteger el entorno de nube](daily-activities-to-protect-your-cloud-environment.md)   
[Para obtener soporte técnico, visite la página de soporte técnico asistido de Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Los clientes Premier también pueden elegir Cloud App Security directamente desde el Portal Premier.](https://premier.microsoft.com/)  
  
  