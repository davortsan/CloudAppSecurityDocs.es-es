---
title: Administración de alertas generadas en Cloud App Security
description: En este artículo se explica cómo trabajar con alertas generadas en el portal de Cloud App Security.
ms.date: 01/22/2020
ms.topic: how-to
ms.openlocfilehash: cef0c80ff1494d36ea216f8b3d6c4c588d7167db
ms.sourcegitcommit: d87372b47ca98e942c2bf94032a6a61902627d69
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/30/2020
ms.locfileid: "96314994"
---
# <a name="manage-alerts"></a>Administración de alertas

[!INCLUDE [Banner for top of topics](includes/banner.md)]

En este artículo se explica cómo trabajar con alertas generadas en el portal de Cloud App Security.

> [!NOTE]
> Las alertas se administran en sus respectivas directivas y se pueden configurar para enviarlas como correo electrónico, mensaje de texto o ambos.

## <a name="manage-your-alerts"></a>Administración de alertas

Las alertas son los puntos de entrada para comprender el entorno de nube en más profundidad. Es posible que quiera crear nuevas directivas según lo que encuentre. Por ejemplo, es posible que vea un administrador iniciando sesión desde Groenlandia y nadie en su organización nunca inició sesión desde Groenlandia antes. Puede crear una directiva que suspende automáticamente una cuenta de administrador cuando se usa para iniciar sesión desde esa ubicación.

Es buena idea revisar todas las alertas y usarlas como herramientas para modificar las directivas. Si hay eventos inofensivos que las directivas existentes consideran como infracciones, perfeccione las directivas para recibir menos alertas innecesarias.

1. En la página **Alertas** seleccione **Abierto** para el **Estado de resolución**.

    En esta sección del panel se proporciona visibilidad completa de cualquier actividad sospechosa o infracción de las políticas establecidas. Puede ayudarle a proteger la postura de seguridad que ha definido para su entorno de la nube.

    ![Página estado de resolución de alertas](media/alerts.png "alerts")

2. Debe investigar y determinar la naturaleza de la infracción y la respuesta necesaria en cada alerta.

    - Puede filtrar las alertas por Tipo de alerta o Gravedad para procesar primero las más importantes.

    - Seleccione una alerta específica. Según el tipo de alerta del que se trate, verá varias acciones que pueden realizarse antes de resolver la alerta.

    - Puede filtrar en función de la aplicación: las aplicaciones que se muestran son aquellas para las que Cloud App Security detectó actividades.

    - Hay tres tipos de infracciones con los que deberá tratar al investigar las alertas:

       - **Serious violations** (Infracciones graves): infracciones graves que exigen una respuesta inmediata.  
     *Ejemplos:*
         - En el caso de una alerta de actividad sospechosa, es posible que quiera suspender la cuenta hasta que el usuario cambie la contraseña.
         - En el caso de una filtración de datos, es posible que le interese restringir los permisos o poner el archivo en cuarentena.
         - Si se detecta una aplicación nueva, es posible que quiera bloquear el acceso al servicio en el servidor proxy o el firewall.

       - **Questionable violations** (Infracciones cuestionables): infracciones cuestionables que exigen más investigación.
         - Puede ponerse en contacto con el usuario o su administrador para hablar sobre la naturaleza de la actividad.
         - Deje la actividad abierta hasta que disponga de más información.

       - **Authorized violations or anomalous behavior** (Infracciones autorizadas o comportamientos anómalos): infracciones autorizadas o comportamientos anómalos que pueden deberse a un uso legítimo.
         - Puede descartar la alerta.

3. Es importante que, siempre que se descarte una alerta, envíe comentarios sobre por qué la descarta. El equipo de Cloud App Security usa estos comentarios como indicación de la precisión de la alerta. Esta información se usa después para ajustar los modelos de Machine Learning para futuras alertas. Puede seguir estas directrices para decidir cómo clasificar la alerta:
    - Si la alerta se ha desencadenado por un uso legítimo y no es un problema de seguridad, podría ser uno de los siguientes tipos:

      - Positivo benigno: la alerta es precisa pero la actividad es legítima. Puede descartar la alerta y establecer el motivo en **La gravedad real es inferior** o **No es interesante**.
      - Falso positivo: la alerta es inexacta. Descarte la alerta y establezca el motivo en **La alerta no es precisa**.
    - Si hay demasiado ruido para determinar la legitimidad y la precisión de una alerta, descártela y establezca el motivo en **Demasiadas alertas similares**.
    - Verdadero positivo: si la alerta está relacionada con un evento de riesgo real que realizó de forma malintencionada o involuntaria un usuario interno o externo, debe establecer el evento en **Resolver** después de que se hayan tomado las medidas adecuadas para corregir el evento.

## <a name="alert-types"></a>Tipos de alerta

En la tabla siguiente se proporciona una lista de los tipos de alertas que pueden activarse y se recomiendan formas para resolverlas.

|Tipo de alerta|Description|Solución recomendada|
|----------------|-----------------|----------------------------|
|Infracción de directiva de actividad|Este tipo de alerta es el resultado de una directiva que ha creado.|Para trabajar con este tipo de alerta en masa, se recomienda que trabaje en el centro de directivas para mitigarlas.<br /><br /> Ajuste la directiva para excluir las entidades con ruido al agregar más filtros y controles más pormenorizados.<br /><br />Si la directiva es precisa, la alerta está garantizada y es una infracción que quiere detener inmediatamente, considere la posibilidad de agregar una corrección automática en la directiva.|
|Infracción de directiva de archivo|Este tipo de alerta es el resultado de una directiva que ha creado.| Para trabajar con este tipo de alerta en masa, se recomienda que trabaje en el centro de directivas para mitigarlas.<br /><br /> Ajuste la directiva para excluir las entidades con ruido al agregar más filtros y controles más pormenorizados.<br /><br />Si la directiva es precisa, la alerta está garantizada y es una infracción que quiere detener inmediatamente, considere la posibilidad de agregar una corrección automática en la directiva.|
|Cuenta en peligro|Este tipo de alerta se activa cuando Cloud App Security identifica una cuenta en peligro. Esto significa que hay una probabilidad muy alta de que la cuenta se usase de forma no autorizada.|Se recomienda suspender la cuenta hasta poder comunicarse con el usuario y asegurarse de que cambia la contraseña.|
|Cuenta inactiva|Esta alerta se activa cuando una cuenta no se ha usado en los últimos 60 días en ninguna de sus aplicaciones en la nube conectadas.|Póngase en contacto con el usuario y el administrador para determinar si la cuenta aún está activa. Si no es así, suspenda al usuario y finalice la licencia de la aplicación.|
|Nuevo usuario administrador|Advierte de cambios en las cuentas con privilegios de las aplicaciones conectadas.|Confirme que los nuevos permisos de administrador en realidad son necesarios para el usuario. Si no lo son, se recomienda revocar los privilegios de administrador para reducir la exposición.|
|Nueva ubicación de administrador|Advierte de cambios en las cuentas con privilegios de las aplicaciones conectadas.|Confirme que el inicio de sesión desde esta ubicación anómala era legítimo. Si no es así, se recomienda revocar los permisos de administrador o la suspensión de la cuenta para reducir la exposición.|
|Nueva ubicación|Una alerta informativa sobre el acceso a una aplicación conectada desde una nueva ubicación y se desencadena solo una vez por país o región.|Investigue la actividad del usuario concreto.|
|Nuevo servicio detectado|Esta es una alerta sobre Shadow IT. Cloud Discovery ha detectado una nueva aplicación.|<ul><li>Evalúe el riesgo del servicio según el catálogo de aplicaciones.</li><li>Explore la actividad en profundidad para entender los patrones de uso y la prevalencia.</li><li>Decida si quiere autorizar o no la aplicación.</li><br /></ul>En el caso de las aplicaciones sin autorización:<br /><br /><ul><li>Es posible que quiera bloquear el uso en el servidor proxy o el firewall.</li><li>Si tiene una aplicación sin autorización y una aplicación con autorización en la misma categoría, puede exportar una lista de usuarios de la aplicación sin autorización. Luego, póngase en contacto con ellos para migrarlos a la aplicación autorizada.</li></ul></li>|
|Actividad sospechosa|Esta alerta permite saber que se ha detectado actividad anómala no alineada con actividades o usuarios esperados de la organización.|Investigue el comportamiento y confírmelo con el usuario.<br /><br />Este tipo de alerta es un buen punto para empezar a aprender más sobre el entorno y a crear nuevas directivas con estas alertas. Por ejemplo, si alguien carga repentinamente una gran cantidad de datos en una de las aplicaciones conectadas, puede establecer una regla para controlar ese tipo de comportamiento anómalo.|
|Uso de cuenta personal|Esta alerta permite saber que una nueva cuenta personal tiene acceso a recursos de las aplicaciones conectadas.|Quite las colaboraciones del usuario en la cuenta externa.|

## <a name="next-steps"></a>Pasos siguientes

Para obtener más información acerca de la investigación de alertas, consulte [Investigar](investigate.md).

[!INCLUDE [Open support ticket](includes/support.md)]
