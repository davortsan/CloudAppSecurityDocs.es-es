---
title: 'Investigación de los riesgos y las actividades sospechosas de las aplicaciones en la nube: Cloud App Security | Microsoft Docs'
description: En este artículo se proporciona un esquema del proceso de investigación de alertas, problemas y actividades sospechosas mediante Cloud App Security.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: barbkess
ms.date: 12/10/2018
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: a9b00c2a-2f71-499e-8f57-67e560daedc1
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 7d6aaf79cca92da7e82d59c9f05049e77e406071
ms.sourcegitcommit: 8ef0438fa35916c48625ff750cb85e9628d202f2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/15/2019
ms.locfileid: "56281634"
---
# <a name="investigate"></a>Investigar

*Se aplica a: Microsoft Cloud App Security*

Después de que Microsoft Cloud App Security se ejecute en el entorno de nube, necesitará una fase de aprendizaje e investigación. Aprenda a usar las herramientas de Microsoft Cloud App Security para mejorar su comprensión de lo que sucede en el entorno de nube. Según su entorno concreto y su uso, puede identificar los requisitos para proteger su organización de posibles riesgos. En este artículo se describe cómo realizar una investigación para comprender mejor lo que está ocurriendo en su entorno en la nube.  

## <a name="dashboards"></a>Paneles  
Los siguientes paneles están disponibles para ayudarle a investigar las aplicaciones en su entorno en la nube:  

|Dashboard|Descripción|  
|---------------|-----------------|  
|Panel principal|Información general sobre el estado en la nube (usuarios, archivos y actividades), así como las acciones necesarias (alertas, infracciones de actividad e infracciones de contenido)|  
|Panel de la aplicación: general|Información general sobre el uso de las aplicaciones por ubicación, gráficos de uso por número de usuarios.|  
|Panel de la aplicación: datos|Análisis de los datos almacenados en la aplicación; desglose por tipo de archivo y por nivel de uso compartido de archivos|  
|Panel de la aplicación: archivos|Profundización en archivos, posibilidad de filtrar por propietario, nivel de uso compartido, y más, así como realización de acciones de gobierno como poner en cuarentena.|  
|Panel de la aplicación: aplicaciones de terceros|Profundización en las aplicaciones de terceros implementadas actualmente, como G Suite, y definición de directivas para esas aplicaciones|  
|Panel del usuario|Información general completa del perfil de usuario en la nube, incluidos grupos, ubicaciones, actividades recientes, alertas relacionadas y exploradores usados|  

##  <a name="sanctionapp"></a> Marcar aplicaciones como autorizadas o no autorizadas  
Marcar aplicaciones como autorizadas o no autorizadas es un paso importante para comprender su entorno en la nube. Después de autorizar una aplicación, puede filtrar por las aplicaciones que no estén autorizadas e iniciar la migración a las aplicaciones autorizadas que sean del mismo tipo.  

- En la consola de Cloud App Security, vaya a Catálogo de aplicaciones o Aplicaciones detectadas.  

- En la lista de aplicaciones, en la fila que contenga la aplicación que quiera marcar como autorizada, elija los tres puntos al final de la fila ![Puntos para marcar como autorizada](./media/sanction-three-dots.png "Puntos para marcar como autorizada") y elija **Marcar como autorizada**.  

     ![Marcar como autorizada](./media/mark-as-sanctioned.png "Marcar como autorizada")  


## <a name="use-the-investigation-tools"></a>Usar las herramientas de investigación  

1. En el portal de Cloud App Security, vaya a **Investigar** y, después, eche un vistazo al **Registro de actividades** y filtre por una aplicación específica. Compruebe los siguientes elementos:  

    - ¿Quién tiene acceso a su entorno en la nube?  

    - ¿Desde qué intervalos IP?  

    - ¿Cuál es la actividad de administrador?  

    - ¿Desde qué ubicaciones se conectan los administradores?  

    - ¿Hay dispositivos obsoletos que se conectan a su entorno en la nube?  

    - ¿Hay inicios de sesión erróneos procedentes de direcciones IP esperadas?  

2. Vaya a **Investigar** y luego a **Archivos**, y compruebe los siguientes elementos:  

    - ¿Cuántos archivos se comparten públicamente para que nadie pueda tener acceso a ellos sin un vínculo?  

    - ¿Con qué asociados comparte archivos (uso compartido externo)?  

    - ¿Todos los archivos tienen un nombre confidencial?  

    - ¿Alguno de los archivos se comparte con la cuenta personal de alguien?  

3. Vaya a **Investigar** y luego a **Usuarios y cuentas**, y compruebe los siguientes elementos:  

    - ¿Las cuentas han estado inactivas en un servicio determinado durante un largo periodo de tiempo? Quizás pueda revocar la licencia para ese usuario a ese servicio.  

    - ¿Quiere saber qué usuarios tienen un rol específico?  

    - ¿Alguien al que se ha despedido sigue teniendo acceso a una aplicación y puede usar ese acceso para robar información?  

    - ¿Quiere revocar el permiso de un usuario en una aplicación concreta o requerir a un usuario específico que use la autenticación multifactor?  

    - Puede profundizar en la cuenta de usuario si hace clic en los tres puntos al final de la fila de cuenta de usuario y selecciona la acción que realizar. Realice una acción como **Suspender usuario** o **Quitar las colaboraciones del usuario**. Si el usuario se ha importado desde Azure Active Directory, también puede hacer clic en **Configuración de la cuenta de Azure AD** para obtener acceso fácil a las características de administración de usuario avanzadas. Los ejemplos de características de administración incluyen la administración de grupos, MFA, detalles sobre inicios de sesión del usuario y la capacidad de bloquear el inicio de sesión.

4. Vaya a **Investigar**, seguido de **Aplicaciones conectadas** y seleccione una aplicación. El panel de la aplicación se abre y le presenta información y datos. Puede usar las pestañas de la parte superior para comprobar:  

    - ¿Qué tipo de dispositivos usan los usuarios para conectarse a la aplicación?  

    - ¿Qué tipos de archivos guardan en la nube?  

    - ¿Qué actividad está teniendo lugar ahora mismo en la aplicación?  

    - ¿Hay aplicaciones de terceros conectadas a su entorno?  

    - ¿Conoce estas aplicaciones?  

    - ¿Tienen autorización para el nivel de acceso para el que tienen permiso?  

    - ¿Cuántos usuarios las han implementado? ¿Cómo son de comunes estas aplicaciones en general?  
 
    ![Panel de la aplicación](./media/investigate-app.png "Investigar aplicación")  

5. Vaya al **panel de Cloud Discovery** y compruebe los siguientes elementos:  

    - ¿Qué aplicaciones en la nube se están utilizando, en qué medida y qué usuarios las están utilizando?  

    - ¿Con qué fines se usan?  

    - ¿Qué cantidad de datos se está cargando en estas aplicaciones en la nube?  

    - ¿En qué categorías tiene aplicaciones en la nube autorizadas y, aún así, los usuarios emplean soluciones alternativas?  

    - Para soluciones alternativas, ¿quiere no autorizar algunas aplicaciones en su organización?  

    - ¿Hay aplicaciones en la nube que se usan, pero no en conformidad con la directiva de su organización?  

## <a name="sample-investigation"></a>Ejemplo de investigación
  
Imaginemos que, en teoría, ninguna dirección IP de riesgo puede tener acceso a su entorno en la nube. Por ejemplo, supongamos que Tor. Pero crearemos una directiva para las IP de riesgo solo para asegurarnos de ello:  

1. En el portal, vaya a **Control** y elija **Plantilla**.  

2. Elija la **Directiva de actividad** para el **Tipo**.  

3. Al final de la fila **Inicio de sesión desde una dirección IP de riesgo**, haga clic en el signo más (**+**) para crear una directiva.  

4. Cambie el nombre de la directiva para que pueda identificarla.  

5. En **Actividades que coinciden con todas las opciones siguientes**, haga clic en **+** para agregar un filtro. Desplácese hasta **Etiqueta IP** y luego elija **Tor**.  

     ![Ejemplo de directiva de IP de riesgo](./media/example-policy-risky-ips.png "Ejemplo de directiva de IP de riesgo")  

Con la directiva en marcha, le sorprenderá ver que recibe una alerta que indica que la directiva se ha infringido.  

1. Vaya a la página **Alertas** y vea la alerta sobre esta infracción de directiva.  

2. Si ve que parece una infracción real, lo más conveniente será contener el riesgo o corregirlo.  

     Para contener el riesgo, puede enviar una notificación al usuario para preguntarle si la infracción ha sido intencionada y si el usuario era consciente de ello.  

     También puede profundizar en la alerta y suspender al usuario hasta averiguar qué hay que hacer.  

3. Si es un evento permitido que no es probable que se repita, puede descartar la alerta.  

     Si es un evento permitido y se espera que se repita, puede cambiar la directiva para evitar que este tipo de evento se considere una infracción en el futuro.  

## <a name="next-steps"></a>Pasos siguientes
 
Para obtener información sobre cómo controlar la aplicación de la nube de su organización, consulte [Control](control.md).   

[Los clientes Premier también pueden crear una nueva solicitud de soporte técnico directamente en el portal Premier.](https://premier.microsoft.com/)  
