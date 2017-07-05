---
title: "Administración de alertas activadas en el portal de Cloud App Security | Microsoft Docs"
description: "En este artículo se explica cómo trabajar con alertas generadas en el portal de Cloud App Security."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 5/23/2017
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: 1b1dbcc6-472f-43ea-af59-2aa926e3e5a9
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: c4134370302fe8d35e6a3e2232d6ff8a65ad96f6
ms.sourcegitcommit: 2f4474084c7e07ac4853945ab5aa1ea78950675d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/28/2017
---
## <a name="manage-your-alerts"></a>Administración de alertas  
Las alertas son los puntos de entrada para comprender el entorno de nube en más profundidad. Es posible que quiera crear nuevas directivas según lo que encuentre. Por ejemplo, es posible que vea un administrador iniciando sesión desde Groenlandia y nadie en su organización nunca inició sesión desde Groenlandia antes. Puede crear una directiva que suspende automáticamente una cuenta de administrador cuando se utiliza para iniciar sesión desde esa ubicación.  

Es buena idea revisar todas las alertas y usarlas como herramientas para modificar las directivas. Si hay eventos inofensivos que las directivas existentes consideran como infracciones, perfeccione las directivas para recibir menos alertas innecesarias.  

1.   En **Alertas abiertas**, haga clic en **Ver todas las alertas**.  

     En esta sección del panel se proporciona visibilidad completa de cualquier actividad sospechosa o infracción de las políticas establecidas. A continuación, le ayuda a proteger la postura de seguridad que ha definido para su entorno de la nube.  

     ![Alertas](./media/alerts.png "Alertas")  

2.   Debe investigar y determinar la naturaleza de la infracción y la respuesta necesaria en cada alerta.  

     Puede filtrar las alertas por Tipo de alerta o Gravedad para procesar primero las más importantes.  

     Seleccione una alerta específica. Según el tipo de alerta del que se trate, verá varias acciones que pueden realizarse antes de resolver la alerta.  

     Hay tres tipos de infracciones con los que deberá tratar al investigar alertas:  

    #### <a name="serious-violations"></a>Infracciones graves
     Infracciones graves que exigen una respuesta inmediata.

         Examples:  

         For a suspicious activity alert, you might want to suspend the account until the user changes their password.  

         For a data leak you might want to restrict permissions or quarantine the file.  

         If a new app is discovered, you might want to block access to the service on your proxy or firewall.  

    #### <a name="questionable-violations"></a>Infracciones cuestionables
    Infracciones cuestionables que exigen más investigación.  

         You can contact the  user or the user's manager about the nature of the activity.  

         Leave the activity open until you have more information.  

 #### <a name="authorized-violations-or-anomalous-behavior"></a>Infracciones autorizadas o comportamientos anómalos
 Infracciones autorizadas o comportamientos anómalos que pueden deberse a un uso legítimo.  

         Dismiss the alert.  

3.   Cuando finalice este proceso, marque la alerta como resuelta.  

En la tabla siguiente se proporciona una lista de los tipos de alertas que pueden activarse y se recomiendan formas para resolverlas.  

|Tipo de alerta|Descripción|Solución recomendada|  
|----------------|-----------------|----------------------------|  
|Infracción de directiva de actividad|Este tipo de alerta es el resultado de una directiva que ha creado.|Para trabajar con este tipo de alerta en masa, se recomienda que trabaje en el centro de directivas para mitigarlas.<br /><br /> Ajuste la directiva para excluir las entidades con ruido al agregar más filtros y controles más pormenorizados.<br /><br /> Si la directiva es precisa, la alerta está garantizada y es una infracción que quiere detener inmediatamente, considere la posibilidad de agregar una corrección automática en la directiva.|  
|Infracción de directiva de archivo|Este tipo de alerta es el resultado de una directiva que ha creado.| Para trabajar con este tipo de alerta en masa, se recomienda que trabaje en el centro de directivas para mitigarlas.<br /><br /> Ajuste la directiva para excluir las entidades con ruido al agregar más filtros y controles más pormenorizados.<br /><br /> Si la directiva es precisa, la alerta está garantizada y es una infracción que quiere detener inmediatamente, considere la posibilidad de agregar una corrección automática en la directiva.|  
|Cuenta en peligro|Este tipo de alerta se activa cuando Cloud App Security identifica una cuenta en peligro, lo cual significa que tiene una probabilidad muy alta de que la cuenta se usara de forma no autorizada.|Se recomienda suspender la cuenta hasta poder comunicarse con el usuario y asegurarse de que cambia la contraseña.|  
|Cuenta inactiva|Esta alerta se activa cuando una cuenta no se ha usado en los últimos 60 días en ninguna de sus aplicaciones en la nube conectadas.|Póngase en contacto con el usuario y el administrador para determinar si la cuenta aún está activa. Si no es así, suspenda al usuario y finalice la licencia de la aplicación.|  
|Nuevo usuario administrador|Advierte de cambios en las cuentas con privilegios de las aplicaciones conectadas.|Confirme que los nuevos permisos de administrador en realidad son necesarios para el usuario. Si no lo son, se recomienda revocar los privilegios de administrador para reducir la exposición.|  
|Nueva ubicación de administrador|Advierte de cambios en las cuentas con privilegios de las aplicaciones conectadas.|Confirme que el inicio de sesión desde esta ubicación anómala era legítimo. Si no es así, se recomienda revocar los permisos de administrador o la suspensión de la cuenta para reducir la exposición.|  
|Nueva ubicación|Esta es una alerta informativa sobre el acceso a una aplicación conectada desde una nueva ubicación y solo se activa una vez por país.|Investigue la actividad del usuario concreto.|  
|Nuevo servicio detectado|Se trata de una alerta sobre Shadow IT: Cloud Discovery ha detectado una nueva aplicación.|<ul><li>Evalúe el riesgo del servicio según el catálogo de aplicaciones.</li><li>Explore la actividad en profundidad para entender los patrones de uso y la prevalencia.</li><li>Decida si quiere autorizar o no la aplicación.</li><br /></ul>En el caso de las aplicaciones sin autorización:<br /><br /><ul><li>Es posible que quiera bloquear el uso en el servidor proxy o el firewall.</li><li>Si tiene una aplicación sin autorización y una aplicación con autorización en la misma categoría, puede exportar una lista de usuarios de la aplicación sin autorización y luego ponerse en contacto con ellos para migrarlos a la aplicación autorizada.</li></ul></li>|  
|Actividad sospechosa|Esta alerta permite saber que se ha detectado actividad anómala no alineada con actividades o usuarios esperados de la organización.|Investigue el comportamiento y confírmelo con el usuario.<br /><br /> Este tipo de alerta es un buen punto para empezar a aprender más sobre el entorno y a crear nuevas directivas con estas alertas. Por ejemplo, si alguien carga repentinamente una gran cantidad de datos en una de las aplicaciones conectadas, puede establecer una regla para controlar ese tipo de comportamiento anómalo.|  
|Uso sospechoso de la nube|Esta alerta permite saber que se ha detectado actividad anómala no alineada con actividades o usuarios esperados de la organización.|Investigue el comportamiento y confírmelo con el usuario.<br /><br /> Este tipo de alerta es un buen punto para empezar a aprender más sobre el entorno y a crear nuevas directivas con estas alertas. Por ejemplo, si alguien carga repentinamente una gran cantidad de datos en una de las aplicaciones conectadas, puede establecer una regla para controlar ese tipo de comportamiento anómalo.|  
|Uso de cuenta personal|Esta alerta permite saber que una nueva cuenta personal tiene acceso a recursos de las aplicaciones conectadas.|Quite las colaboraciones del usuario en la cuenta externa.|  


## <a name="next-steps"></a>Pasos siguientes  
Para obtener más información acerca de la investigación de alertas, consulte [Investigar](investigate.md).  
Para obtener soporte técnico, visite [la página de soporte técnico asistido de Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
Los clientes Premier también pueden elegir Cloud App Security directamente desde el [Portal Premier](https://premier.microsoft.com/).  
