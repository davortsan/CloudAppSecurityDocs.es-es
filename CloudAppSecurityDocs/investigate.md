---
title: Investigar los riesgos y las actividades sospechosas de las aplicaciones en la nube con Cloud App Security | Microsoft Docs
description: "En este tema se proporciona un esquema del proceso de investigación de alertas, problemas y actividades sospechosas mediante Cloud App Security."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 3/19/2017
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: a9b00c2a-2f71-499e-8f57-67e560daedc1
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 8e552aea95318288d329597ec2a0749535e06a52
ms.sourcegitcommit: 2f4474084c7e07ac4853945ab5aa1ea78950675d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/28/2017
---
# <a name="investigate"></a>Investigar
Después de que Cloud App Security se ejecute en su entorno en la nube, será necesaria una fase de aprendizaje e investigación sobre el uso de las herramientas de Cloud App Security para adquirir un mayor conocimiento de lo que ocurre en su entorno en la nube. Luego, y según su entorno concreto y su uso, puede identificar los requisitos para proteger su organización de posibles riesgos.

En este tema se describe cómo realizar una investigación para comprender mejor lo que está ocurriendo en su entorno en la nube.  

## <a name="dashboards"></a>Paneles  
Los siguientes paneles están disponibles para ayudarle a investigar las aplicaciones en su entorno en la nube:  

|Dashboard|Descripción|  
|---------------|-----------------|  
|Panel principal|Información general sobre el estado en la nube (usuarios, archivos y actividades), así como las acciones necesarias (alertas, infracciones de actividad e infracciones de contenido)|  
|Panel de la aplicación: general|Información general sobre el uso de las aplicaciones por ubicación, gráficos de uso por número de usuarios.|  
|Panel de la aplicación: datos|Análisis de los datos almacenados en la aplicación; desglose por tipo de archivo y por nivel de uso compartido de archivos|  
|Panel de la aplicación: archivos|Profundización en archivos, posibilidad de filtrar por propietario, nivel de uso compartido, etc., así como realización de acciones de gobierno (como poner en cuarentena)|  
|Panel de la aplicación: aplicaciones de terceros|Profundización en las aplicaciones de terceros implementadas actualmente, como G Suite, y definición de directivas para esas aplicaciones|  
|Panel del usuario|Información general completa del perfil de usuario en la nube, incluidos grupos, ubicaciones, actividades recientes, alertas relacionadas y exploradores usados|  

##  <a name="sanctionapp"></a> Marcar aplicaciones como autorizadas o no autorizadas  
Marcar aplicaciones como autorizadas o no autorizadas es un paso importante para comprender su entorno en la nube. Después de autorizar una aplicación, puede filtrar por las aplicaciones que no estén autorizadas e iniciar la migración a las aplicaciones autorizadas que sean del mismo tipo.  

-   En la consola de Cloud App Security, vaya a Catálogo de aplicaciones o Aplicaciones detectadas.  

-   En la lista de aplicaciones, en la fila que contenga la aplicación que quiera marcar como autorizada, elija los tres puntos al final de la fila ![Puntos para marcar como autorizada](./media/sanction-three-dots.png "Puntos para marcar como autorizada") y elija **Marcar como autorizada**.  

     ![Marcar como autorizada](./media/mark-as-sanctioned.png "Marcar como autorizada")  


## <a name="use-the-investigation-tools"></a>Usar las herramientas de investigación  

1.  En el portal de Cloud App Security, vaya a **Investigar** y, después, eche un vistazo al **Registro de actividades** y filtre por una aplicación específica. Compruebe lo siguiente:  

    -   ¿Quién tiene acceso a su entorno en la nube?  

    -   ¿Desde qué intervalos IP?  

    -   ¿Cuál es la actividad de administrador?  

    -   ¿Desde qué ubicaciones se conectan los administradores?  

    -   ¿Hay dispositivos obsoletos que se conectan a su entorno en la nube?  

    -   ¿Hay inicios de sesión erróneos procedentes de direcciones IP esperadas?  

2.  Vaya a **Investigar** y, luego, a **Archivos** y compruebe lo siguiente:  

    -   ¿Cuántos archivos se comparten públicamente para que nadie pueda tener acceso a ellos sin un vínculo?  

    -   ¿Con qué asociados comparte archivos (uso compartido externo)?  

    -   ¿Todos los archivos tienen un nombre confidencial?  

    -   ¿Alguno de los archivos se comparte con la cuenta personal de alguien?  

3.  Vaya a **Investigar** y, luego, a **Cuentas** y compruebe lo siguiente:  

    -   ¿Las cuentas han estado inactivas en un servicio determinado durante un largo periodo de tiempo? (Quizás pueda revocar la licencia para ese usuario a ese servicio)  

    -   ¿Quiere saber qué usuarios tienen un rol específico?  

    -   ¿Alguien al que se ha despedido sigue teniendo acceso a una aplicación y puede usar ese acceso para robar información?  

    -   ¿Quiere revocar el permiso de un usuario en una aplicación concreta o requerir a un usuario específico que realice una autenticación multifactor?  
    
    -   Puede también profundizar en la cuenta de usuario haciendo clic en el engranaje al final de la fila de cuenta de usuario y seleccionando la acción que realizar, como **Suspender usuario** o **Quitar las colaboraciones del usuario**. Si el usuario se ha importado desde Azure Active Directory, también puede hacer clic en **Configuración de la cuenta de Azure AD** para obtener acceso fácil a las características de administración de usuario avanzadas como la administración de grupos, MFA, detalles sobre inicios de sesión del usuario y la capacidad de bloquear el inicio de sesión.

4.  Vaya a **Investigar** y, luego, seleccione una aplicación. El panel de la aplicación se abre y le presenta información y datos. Puede usar las fichas de la parte superior para comprobar lo siguiente:  

     ![Panel de la aplicación](./media/investigate-app.png "Investigar aplicación")  

    -   ¿Qué tipo de dispositivos usan los usuarios para conectarse a la aplicación?  

    -   ¿Qué tipos de archivos guardan en la nube?  

    -   ¿Qué actividad está teniendo lugar ahora mismo en la aplicación?  

    -   ¿Hay aplicaciones de terceros conectadas a su entorno?  

    -   ¿Conoce estas aplicaciones?  

    -   ¿Tienen autorización para el nivel de acceso para el que tienen permiso?  

    -   ¿Cuántos usuarios las han implementado? ¿Cómo son de comunes estas aplicaciones en general?  

5.  Vaya al **panel de Cloud Discovery** y compruebe lo siguiente:  

    -   ¿Qué aplicaciones en la nube se están utilizando, en qué medida y quién las está utilizando?  

    -   ¿Con qué fines se usan?  

    -   ¿Qué cantidad de datos se está cargando en estas aplicaciones en la nube?  

    -   ¿En qué categorías tiene aplicaciones en la nube autorizadas y, aún así, los usuarios emplean soluciones alternativas?  

    -   Para soluciones alternativas, ¿quiere no autorizar algunas aplicaciones en su organización?  

    -   ¿Hay aplicaciones en la nube que se usan, pero no en conformidad con la directiva de su organización?  

## <a name="use-reports-to-investigate-risk"></a>Utilizar los informes para investigar riesgos  
Cuando se empieza a tener control sobre el entorno de nube, se realizan determinadas suposiciones en función de lo que se espera encontrar. Realmente, aún no conoce la nube. Y, según esas suposiciones, se crean directivas.

Después de que Cloud App Security se ejecute en su entorno de nube, utilice los informes integrados (y los informes personalizados) para ver qué está ocurriendo en la nube. Atendiendo a ello, ajuste las directivas de nuevo para incluir las excepciones; de tal modo que la directiva detecta finalmente muy pocos falsos positivos.  

Los informes integrados proporcionan vistas agregadas de cara a la investigación. Para utilizar los informes integrados, vaya a **Investigar** y, luego, a **Informes integrados**. Para obtener más información sobre los distintos informes integrados, consulte [Referencia de informes integrados](built-in-report-reference.md).  

## <a name="sample-investigation"></a>Ejemplo de investigación  
Imaginemos que, en teoría, ninguna dirección IP de riesgo puede tener acceso a su entorno en la nube (por ejemplo, servidores proxy anónimos y Tor). Pero crearemos una directiva para las IP de riesgo solo para asegurarnos de ello:  

1.  En el portal, vaya a **Control** y elija **Directivas**.  

2.  En el **Centro de directivas**, elija la pestaña **Plantillas**.  

3.  Al final de la fila **Inicio de sesión de usuario desde una dirección IP no categorizada**, elija el signo más (**+**) para crear una directiva nueva.  

4.  Cambie el nombre de la directiva para que sea fácil de identificar.  

5.  En **Filtros de actividad**, elija **+** para agregar un filtro. Desplácese hasta **Etiqueta IP** y, luego, elija **Anónimo** y **Tor**.  

     ![Ejemplo de directiva de IP de riesgo](./media/example-policy-risky-ips.png "Ejemplo de directiva de IP de riesgo")  

Con la directiva en marcha, le sorprenderá ver que recibe una alerta que indica que la directiva se ha infringido.  

1.  Vaya a la página **Alertas** y vea la alerta sobre esta infracción de directiva.  

2.  Si ve que parece una infracción real, lo más conveniente será contener el riesgo o corregir.  

     Para contener el riesgo, puede enviar una notificación al usuario para preguntarle si la infracción ha sido intencionada y si el usuario era consciente de ello.  

     También puede profundizar en la alerta y suspender al usuario hasta averiguar qué hay que hacer.  

3.  Si es un evento permitido que no es probable que se repita, puede descartar la alerta.  

     Si es un evento permitido y se espera que se repita, puede cambiar la directiva para evitar que este tipo de evento se considere una infracción en el futuro.  

## <a name="see-also"></a>Vea también  
Para obtener información sobre cómo controlar la aplicación de la nube de su organización, consulte [Control](control.md).   
Para obtener soporte técnico, visite la página de [soporte técnico asistido de Cloud App Security](http://support.microsoft.com/oas/default.aspx?prid=16031).  
Los clientes Premier también pueden elegir Cloud App Security directamente desde el [Portal Premier](https://premier.microsoft.com/).  
