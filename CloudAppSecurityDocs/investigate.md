---
title: "Investigación | Microsoft Docs"
description: "En este tema se proporciona un esquema del proceso de investigación de alertas, problemas y actividades sospechosas mediante Cloud App Security."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 10/15/2016
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: a9b00c2a-2f71-499e-8f57-67e560daedc1
ms.reviewer: reutam
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: ed4ea71b24767d3602d40894d1cbac7447bcd8a2
ms.openlocfilehash: 186643ab8efa7391b06a09dd2cddbb22ba583e71


---

# <a name="investigate"></a>Investigar
Después de que Cloud App Security se ejecute en su entorno en la nube, será necesaria una fase de aprendizaje e investigación en la que deberán usarse las herramientas de Cloud App Security para adquirir un mayor conocimiento de lo que ocurre en su entorno en la nube. Luego, y según su entorno concreto y cómo se use, puede identificar los requisitos necesarios para proteger su organización de posibles riesgos.  
  
En esta sección se describe cómo realizar una investigación en profundidad para saber de mejor forma lo que está ocurriendo en su entorno en la nube.  
  
## <a name="dashboards"></a>Paneles  
Los siguientes paneles están disponibles para ayudarle a investigar lo que ocurre con las aplicaciones en su entorno en la nube:  
  
|Dashboard|Descripción|  
|---------------|-----------------|  
|Panel principal|Información general sobre el estado en la nube (usuarios, archivos, actividades), así como las acciones necesarias (alertas, infracciones de actividad e infracciones de contenido).|  
|Panel de la aplicación (general)|Información general sobre el uso de las aplicaciones por ubicación, gráficos de uso por número de usuarios.|  
|Panel de la aplicación (datos)|Análisis de los datos almacenados en la aplicación; desglose por tipo de archivos y por nivel de uso compartido de archivos.|  
|Panel de la aplicación (archivos)|Profundización en archivos, posibilidad de filtrar por propietario, nivel de uso compartido, etc., así como realización de acciones de gobierno (como poner en cuarentena).|  
|Panel de la aplicación (aplicaciones de terceros)|Profundización en las aplicaciones de terceros implementadas actualmente, como Google Apps, y establecimiento de directivas para esas aplicaciones.|  
|Panel del usuario|Información general completa del perfil de usuario en la nube, incluidos grupos, ubicaciones, actividades recientes, alertas relacionadas y exploradores usados.|  
  
##  <a name="a-namesanctionappa-sanction-or-unsanction-apps"></a> Autorizar o no autorizar aplicaciones  
El primer paso para comprender la nube consiste en autorizar aplicaciones. Después de autorizar una aplicación, puede filtrar por las aplicaciones que no estén autorizadas e iniciar la migración a las aplicaciones autorizadas que sean del mismo tipo.  
  
-   En la consola de Cloud App Security, haga clic en **Detectar** y, después, en **Panel de detección**.  
  
-   En la lista de aplicaciones detectadas, en la fila en la que esté la aplicación que quiera sancionar, haga clic en los tres puntos al final de dicha fila ![tres puntos para sancionar](./media/sanction-three-dots.png "Sanction three dots") y seleccione **Marcar como sancionada**.  
  
     ![marcar como sancionada](./media/mark-as-sanctioned.png "mark as sanctioned")  
  
> [!NOTE]  
>  Por cada aplicación que quiera supervisar con la integración de API de Cloud App Security, se recomienda crear una cuenta de servicio de administración dedicada a Cloud App Security.  
  
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
  
    -   ¿Con qué asociados comparte archivos? (Uso compartido externo)  
  
    -   ¿Existen archivos que contengan un nombre confidencial?  
  
    -   ¿Alguno de los archivos se comparte con la cuenta personal de alguien?  
  
3.  Vaya a **Investigar** y, luego, a **Cuentas** y compruebe lo siguiente:  
  
    -   ¿Hay cuentas que no hayan estado activas en un servicio determinado durante mucho tiempo? ¿Quizás se pueda revocar la licencia para ese usuario en ese servicio?  
  
    -   ¿Quiere saber qué usuarios tienen un rol específico?  
  
    -   ¿Alguien al que se ha despedido sigue teniendo acceso a una aplicación y puede usar ese acceso para robar información?  
  
    -   ¿Quiere revocar el permiso de un usuario en una aplicación concreta o requerir a un usuario específico que realice una autenticación multifactor?  
  
4.  Vaya a **Investigar** y, luego, seleccione una aplicación. Se le llevará al panel de la aplicación, que proporciona información y datos con los que poder usar las pestañas de la parte superior para comprobar lo siguiente:  
  
     ![investigar aplicación](./media/investigate-app.png "investigate app")  
  
    -   ¿Qué tipo de dispositivos usan los usuarios para conectarse a la aplicación?  
  
    -   ¿Qué tipos de archivos guardan en la nube?  
  
    -   ¿Qué actividad está teniendo lugar ahora mismo en la aplicación?  
  
    -   ¿Hay aplicaciones de terceros conectadas a su entorno?  
  
    -   ¿Conoce estas aplicaciones?  
  
    -   ¿Tienen autorización para el nivel de acceso para el que tienen permiso?  
  
    -   ¿Cuántos usuarios las han implementado? ¿Cómo son de comunes estas aplicaciones en general?  
  
5.  Vaya al **panel de Cloud Discovery** y compruebe lo siguiente:  
  
    -   ¿Qué aplicaciones en la nube se están usando, en qué medida y por quién?  
  
    -   ¿Con qué fines se usan?  
  
    -   ¿Qué cantidad de datos se está cargando en estas aplicaciones en la nube?  
  
    -   ¿En qué categorías tiene aplicaciones en la nube autorizadas y, aún así, los usuarios emplean soluciones alternativas?  
  
    -   Para la solución alternativa, ¿existen aplicaciones en la nube que quiera no autorizar en su organización?  
  
    -   ¿Hay aplicaciones en la nube que se usan, pero no en conformidad con la directiva de su organización?  
  
## <a name="how-to-use-reports-to-investigate-risk"></a>Cómo usar los informes para investigar riesgos  
Cuando se empieza a tener control sobre el entorno de nube, se realizan determinadas suposiciones en función de lo que se espera encontrar. Realmente, aún no conoce la nube. Y, según esas suposiciones, se crean directivas. Luego, una vez que Cloud App Security se ejecute en el entorno en la nube, puede usar informes integrados (así como informes personalizados) para ver lo que realmente está ocurriendo en la nube y, a partir de ahí, ajustar las directivas para incluir las excepciones de forma que la directiva detecte en última instancia el menor número de falsos positivos.  
  
Los informes integrados proporcionan vistas agregadas de cara a la investigación.  
  
Para usar los informes integrados, vaya a **Investigar** y, luego, a **Informes integrados**. Para obtener más información sobre los distintos informes integrados, consulte [Built-in report reference](built-in-report-reference.md) (Referencia de informes integrados).  
  
## <a name="sample-investigation"></a>Ejemplo de investigación  
Imaginemos que, en teoría, ninguna dirección IP de riesgo puede tener acceso a su entorno en la nube (por ejemplo, servidores proxy anónimos y Tor). Pero crearemos una directiva de IP de riesgo solo para asegurarnos de ello:  
  
1.  En el portal, vaya a **Control** y seleccione **Directivas**.  
  
2.  En el **Centro de directivas**, haga clic en la pestaña **Plantillas**.  
  
3.  Al final de la fila **Inicio de sesión de usuario desde una dirección IP no categorizada**, haga clic en **+** para crear una directiva.  
  
4.  Cambie el nombre de la directiva para que sea fácil de identificar.  
  
5.  En **Filtros de actividad**, haga clic en **+** para agregar un filtro. Desplácese hasta **Etiqueta IP** y, luego, seleccione **Anónimo** y **Tor**.  
  
     ![ejemplo de directiva de IP de riesgo](./media/example-policy-risky-ips.png "example policy risky ips")  
  
Con la directiva en marcha, le sorprenderá ver que recibe una alerta que indica que la directiva se ha infringido.  
  
1.  Vaya a la página **Alertas** y vea la alerta sobre esta infracción de directiva.  
  
2.  Si ve que parece una infracción real, lo más conveniente será contener el riesgo o corregir.  
  
     Para contener el riesgo, puede enviar una notificación al usuario para preguntarle si la infracción ha sido intencionada y si el usuario era consciente de ello.  
  
     También puede profundizar en la alerta y suspender al usuario hasta averiguar qué hay que hacer.  
  
3.  Si es un evento permitido que no es probable que se repita, puede descartar la alerta.  
  
     Si es un evento permitido y se espera que se repita, puede modificar la directiva para evitar que este tipo de evento se considere una infracción en el futuro.  
  
## <a name="see-also"></a>Consulte también  
[Control](control.md)   
[Para obtener soporte técnico, visite la página de soporte técnico asistido de Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Los clientes Premier también pueden elegir Cloud App Security directamente desde el Portal Premier.](https://premier.microsoft.com/)  
  
  


<!--HONumber=Oct16_HO4-->


