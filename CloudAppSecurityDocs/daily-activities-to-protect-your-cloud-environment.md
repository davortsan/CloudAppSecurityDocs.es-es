---
title: Actividades diarias para proteger el entorno de nube | Microsoft Docs
description: "En este artículo se proporciona información básica sobre lo que debe hacer en Cloud App Security con regularidad a fin de usarlo para supervisar el uso de aplicaciones en la nube de la organización."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 10/15/2016
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: a835fa24-15c5-4bbb-a25a-688444040f1f
ms.reviewer: reutam
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: ed4ea71b24767d3602d40894d1cbac7447bcd8a2
ms.openlocfilehash: cc6a6e4b41b6660462c9c873469a1e8c9af97c4e


---

# <a name="daily-activities-to-protect-your-cloud-environment"></a>Actividades diarias para proteger el entorno de nube
Después de tener Cloud App Security configurado y en funcionamiento y de configurar secuencias de datos, autorice las aplicaciones que quiera permitir que empleen los usuarios y configure directivas para supervisar el entorno de nube. Es hora de usar Cloud App Security para controlar y proteger la nube y administrar el riesgo.  
  
En este tema se explica lo que hacer a diario.  
  
## <a name="check-the-dashboard"></a>Comprobar el panel  
Al abrir el portal de Cloud App Security, aparece una vista general de alertas abiertas, infracciones de actividad, infracciones de contenido, un mapa de actividad en el que se marca dónde se origina geográficamente la actividad de los usuarios y tendencias de uso de aplicaciones conectadas en el entorno de nube.  
  
Se recomienda comprobar el panel cada día para ver qué nuevas alertas se han activado y administrarlas. También es un buen lugar para vigilar el estado del entorno de nube para hacerse una idea de lo que está ocurriendo en él por encima.  
  
![panel](./media/dashboard.png "dashboard")  
  
## <a name="handle-your-alerts"></a>Administrar las alertas  
Las alertas son el punto de entrada para comprender el entorno de nube en más profundidad. Es posible que quiera crear nuevas directivas según lo que encuentre. Por ejemplo, es posible que vea que un administrador inicia sesión desde Groenlandia y decida que en el futuro quiere crear una directiva que suspenda automáticamente una cuenta de administrador cuando se use para iniciar sesión desde Groenlandia.  
  
Es buena idea revisar todas las alertas y usarlas como herramienta para modificar las directivas. Si hay eventos inofensivos que para las directivas existentes son infracciones, debería perfeccionar las directivas para recibir menos alertas innecesarias.  
  
-   En **Alertas abiertas**, haga clic en **Ver todas las alertas**.  
  
     Esto proporciona visibilidad completa de cualquier actividad sospechosa o infracción de las directivas establecidas y ayuda a salvaguardar la posición de seguridad definida para el entorno de nube.  
  
     ![alertas](./media/alerts.png "alerts")  
  
-   Debe investigar y determinar la naturaleza de la infracción y la respuesta necesaria en cada alerta.  
  
     Puede filtrar las alertas por **Tipo de alerta** o **Gravedad** para procesar primero las más importantes.  
  
     Haga clic en una alerta específica. Según el tipo de alerta del que se trate, recibirá varias acciones que pueden realizarse antes de resolver la alerta.  
  
     Hay tres tipos de infracciones con los que deberá tratar al investigar alertas:  
  
    -   **Infracciones graves** que exigen una respuesta inmediata  
  
         Ejemplos:  
  
         En el caso de una alerta de actividad sospechosa es posible que quiera suspender la cuenta hasta que el usuario cambie la contraseña.  
  
         En el caso de una filtración de datos, es posible que quiera restringir los permisos o poner el archivo en cuarentena.  
  
         Si se detecta un nuevo servicio sin autorización, es posible que quiera bloquear el acceso al servicio en el servidor proxy o el firewall.  
  
    -   **Infracciones cuestionables** que exigen más investigación  
  
         Puede ponerse en contacto con el usuario o su administrador para hablar sobre la naturaleza de la actividad.  
  
         Deje la actividad abierta hasta que disponga de más información.  
  
    -   **Infracciones autorizadas o comportamientos anómalos** debidos a un uso legítimo.  
  
         Descarte la alerta.  
  
-   Cuando finalice este proceso, marque la alerta como resuelta.  
  
En la tabla siguiente se proporciona una lista de los tipos de alertas que pueden activarse y formas recomendadas de resolverlas.  
  
|Tipo de alerta|Descripción|Solución recomendada|  
|----------------|-----------------|----------------------------|  
|Infracción de directiva de actividad|Este tipo de alerta es el resultado de una directiva que ha creado.|- Para trabajar con este tipo de alerta en masa, se recomienda hacerlo directamente desde dentro del centro de directivas para mitigarlas.<br />- Ajuste la directiva para excluir las entidades con ruido al agregar más filtros y controles más pormenorizados.<br />- Si la directiva es muy precisa y la alerta está garantizada y es una infracción que quiere detener inmediatamente, considere la posibilidad de pasar a una respuesta automatizada, al agregar una corrección automática en la directiva.|  
|Infracción de directiva de archivo|Este tipo de alerta es el resultado de una directiva que ha creado.|- Para trabajar con este tipo de alerta en masa, se recomienda hacerlo directamente desde dentro del centro de directivas para mitigarlas.<br />- Ajuste la directiva para excluir las entidades con ruido al agregar más filtros y controles más pormenorizados.<br />- Si la directiva es muy precisa y la alerta está garantizada y es una infracción que quiere detener inmediatamente, considere la posibilidad de pasar a una respuesta automatizada, al agregar una corrección automática en la directiva.|  
|Cuenta en peligro|Este tipo de alerta se activa cuando Cloud App Security identifica una cuenta en peligro con una (probabilidad muy alta de que la cuenta se usara de forma no autorizada).|Se recomienda suspender la cuenta hasta poder comunicarse con el usuario y asegurarse de que cambia la contraseña.|  
|Cuenta inactiva|Esta alerta se activa cuando una cuenta ya no se usa en una de las aplicaciones conectadas en la nube.|Póngase en contacto con el usuario y el administrador para determinar si la cuenta aún está activa. Si no es así, suspenda al usuario y finalice la licencia de la aplicación.|  
|Nuevo usuario administrador|Advierte de cambios en las cuentas con privilegios de las aplicaciones conectadas.|Confirme que los nuevos permisos de administrador en realidad son necesarios para el usuario y, si no es así, recomiende revocar los privilegios de administrador para reducir la exposición.|  
|Nueva ubicación de administrador|Advierte de cambios en las cuentas con privilegios de las aplicaciones conectadas.|Confirme que el inicio de sesión desde esta ubicación anómala fue legítimo y, si no es así, recomiende revocar los permisos de administrador o suspender la cuenta para reducir la exposición.|  
|Nueva ubicación|Esta es una alerta informativa sobre el acceso a una aplicación conectada desde una nueva ubicación y solo se activa una vez por país.|Investigue la actividad del usuario concreto.|  
|Nuevo servicio detectado|Se trata de una alerta sobre Shadow IT: Cloud Discovery ha detectado una nueva aplicación.|<ul><li>Evalúe el riesgo del servicio según el catálogo de aplicaciones.</li><li>Explore la actividad en profundidad para entender los patrones de uso y la prevalencia.</li><li>Decida si quiere autorizar o no la aplicación.<br /><br />     En el caso de las aplicaciones sin autorización:<br /><br /> <ul><li>Es posible que quiera bloquear el uso en el servidor proxy o el firewall.</li><li>Si no tiene autorización y hay una aplicación con autorización en la misma categoría, puede explorar en profundidad y exportar una lista de usuarios de la aplicación sin autorización y luego ponerse en contacto con ellos para migrarlos a la aplicación autorizada.</li></ul></li></ul>|  
|Actividad sospechosa|Esta alerta permite saber que se ha detectado actividad anómala no alineada con actividades o usuarios esperados de la organización.|Investigue el comportamiento y confírmelo con el usuario.<br /><br /> Este tipo de alerta es un buen punto para empezar a aprender más sobre el entorno y a usar estas alertas para crear nuevas directivas. Por ejemplo, si alguien carga repentinamente una gran cantidad de datos en una de las aplicaciones conectadas, puede establecer una regla para controlar ese tipo de comportamiento anómalo.|  
|Uso sospechoso de la nube|Esta alerta permite saber que se ha detectado actividad anómala no alineada con actividades o usuarios esperados de la organización.|Investigue el comportamiento y confírmelo con el usuario.<br /><br /> Este tipo de alerta es un buen punto para empezar a aprender más sobre el entorno y a usar estas alertas para crear nuevas directivas. Por ejemplo, si alguien carga repentinamente una gran cantidad de datos en una de las aplicaciones conectadas, puede establecer una regla para controlar ese tipo de comportamiento anómalo.|  
|Uso de cuenta personal|Esta alerta permite saber que una nueva cuenta personal tiene acceso a recursos de las aplicaciones conectadas.|En la cuenta externa, quite las colaboraciones del usuario.|  
  
## <a name="use-policies-to-assess-risk"></a>Usar directivas para evaluar el riesgo  
Después de echar un vistazo a las alertas abiertas, vaya al **centro de directivas** para revisar las infracciones de directivas que no han activado alertas.  
  
-   En el portal de Cloud App Security, haga clic en **Control** y, luego, en **Directivas**.  
  
-   Haga clic en una directiva específica para ver la lista **Infringiendo ahora** de coincidencias de directivas que no han activado alertas.  
  
-   Haga clic en las infracciones de una en una y decida qué hacer con cada una. Para obtener más información sobre las acciones de gobierno, consulte la sección siguiente.  
  
     Por ejemplo, si la directiva está establecida para detectar infracciones de cumplimiento normativo y alguien guarda números de tarjetas de crédito en archivos en OneDrive, tendrá una coincidencia en la directiva.  
  
     ![coincidencias de PCI](./media/pci-matches.png "pci matches")  
  
-   Haga clic en la coincidencia para ver los archivos reales que han infringido la directiva.  
  
     ![coincidencias de contenido de PCI](./media/pci-content-matches.png "pci content matches")  
  
     Puede hacer clic en el propio archivo para obtener información sobre los archivos.  
  
     Puede hacer clic en **Colaboradores** para ver quién tiene acceso a este archivo.  
  
     Puede hacer clic en **Coincidencias** para ver los números de tarjeta de crédito reales.  
  
     ![coincidencias de contenido de números de tarjetas de crédito](./media/content-matches-ccn.png "content matches ccn")  
  
## <a name="see-also"></a>Consulte también  
[Investigación](investigate.md)   
[Para obtener soporte técnico, visite la página de soporte técnico asistido de Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Los clientes Premier también pueden elegir Cloud App Security directamente desde el Portal Premier.](https://premier.microsoft.com/)  
  
  


<!--HONumber=Oct16_HO4-->


