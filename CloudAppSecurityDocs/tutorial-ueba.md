---
title: Investigación de usuarios de riesgo| Microsoft Docs
description: En este tutorial se describe el proceso para investigar los usuarios de riesgo en Microsoft Cloud App Security, en entornos híbridos, mediante la integración con Azure ATP.
keywords: ''
author: shsagir
ms.author: shsagir
ms.date: 12/03/2019
ms.topic: tutorial
ms.collection: M365-security-compliance
ms.service: cloud-app-security
ms.reviewer: dannyk
ms.suite: ems
ms.openlocfilehash: cafb971ae16b0c5bd48e041d36c16521b6e7e5d3
ms.sourcegitcommit: 6eff466c7a6817b14a60d8c3b2c201c7ae4c2e2c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "74733701"
---
# <a name="tutorial-investigate-risky-users"></a>Tutorial: Investigación de usuarios de riesgo

*Se aplica a: Microsoft Cloud App Security*

Los equipos de operaciones de seguridad se enfrentan al desafío de supervisar la actividad del usuario, sospechosa o de otro tipo, en todas las dimensiones de la superficie expuesta a los ataques de identidad, mediante varias soluciones de seguridad que a menudo no están conectadas. Aunque muchas empresas disponen actualmente de equipos de búsqueda para identificar de forma proactiva las amenazas en sus entornos, saber qué buscar en la ingente cantidad de datos puede ser un desafío. Microsoft Cloud App Security simplifica ahora esta tarea, ya que elimina la necesidad de crear reglas de correlación complejas y le permite buscar ataques que se distribuyen entre la nube y la red local.

Para ayudarle a centrarse en la identidad de los usuarios, Microsoft Cloud App Security proporciona análisis del comportamiento de los usuarios y las entidades (UEBA) en la nube. Esto se puede ampliar a su entorno local mediante la integración con Azure Advanced Threat Protection (ATP). Tras la integración con Azure ATP, también obtendrá contexto relacionado con la identidad del usuario a partir de su integración nativa con Active Directory.

Tanto si su desencadenador es una alerta visible en el panel de Cloud App Security como si tiene información de un servicio de seguridad de terceros, comience su investigación en el panel de Cloud App Security para profundizar en los usuarios de riesgo.

En este tutorial se proporcionan instrucciones para el uso de Cloud App Security para investigar a los usuarios de riesgo.

> [!div class="checklist"]
>
> * 1: [Conexión a las aplicaciones que se quiere proteger](#connect-apps-protect)
> * 2: [Identificación de los usuarios de riesgo principales](#identify)
> * 3: [Investigación en profundidad de los usuarios](#investigate)
> * 4: [Protección de la organización](#protect)

## Comprender la puntuación de prioridad de investigación<a name="risk-score"></a>

La puntuación de prioridad de investigación es una puntuación que proporciona Cloud App Security a cada usuario para informarle de su nivel de riesgo con respecto a otros usuarios de la organización.

Use **Puntuación de prioridad de la investigación** para determinar los usuarios que desea investigar en primer lugar. Cloud App Security crea perfiles de usuario para cada usuario en función de los análisis, que tienen en cuenta el tiempo, los grupos de personas del mismo nivel y la actividad esperada del usuario. La actividad que resulta anómala para la línea de base de un usuario se evalúa y puntúa. Una vez que se completa la puntuación, se ejecutan el aprendizaje automático y los cálculos dinámicos del mismo nivel, que son propiedad de Microsoft, en las actividades de usuario para calcular la prioridad de investigación para cada usuario.

La opción **Puntuación de prioridad de la investigación** le proporciona la capacidad de detectar tanto personal interno malintencionado como atacantes externos que se mueven lateralmente en las organizaciones, sin tener que depender de detecciones deterministas estándar.

La prioridad de la investigación se basa en las alertas de seguridad, las actividades anómalas y el posible impacto en los negocios y los recursos relacionados con cada usuario para ayudarle a evaluar la urgencia de la investigación de cada usuario específico.

Si hace clic en el valor de la puntuación para una alerta o una actividad, puede ver las evidencias que explican cómo Cloud App Security puntuó la actividad.

Cada usuario de Azure AD tiene una puntuación de prioridad de la investigación dinámica, que se actualiza constantemente en función del comportamiento reciente y el impacto, creada a partir de datos que se evalúan desde Azure ATP, Microsoft Cloud App Security y Azure AD Identity Protection. Ahora puede saber de inmediato quiénes son los principales usuarios de riesgo filtrando por la **Puntuación de prioridad de la investigación**, comprobando directamente su impacto en el negocio e investigando todas las actividades relacionadas, independientemente de si están comprometidas, extrayendo datos o actuando como amenazas internas.

Cloud App Security usa lo siguiente para medir el riesgo:

* **Puntuación de las alertas**  
La puntuación de alertas representa el posible impacto de una alerta específica en cada usuario. La puntuación de alertas se basa en la gravedad, el impacto en el usuario y la popularidad de las alertas en todos los usuarios y en todas las entidades de la organización.

* **Puntuación de las actividades**  
La puntuación de las actividades determina la probabilidad de que un usuario específico realice una actividad específica, en función del aprendizaje de comportamiento del usuario y las personas del mismo nivel. Las actividades identificadas como las más anómalas reciben las puntuaciones más altas.

## Fase 1: Conexión a las aplicaciones que se quiere proteger<a name="connect-apps-protect"></a>

1. Conecte al menos una aplicación a Microsoft Cloud App Security mediante los [conectores de API](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md). Es recomendable que comience estableciendo la conexión a [Office 365](connect-office-365-to-microsoft-cloud-app-security.md).
1. Conecte más aplicaciones mediante [proxy para lograr el control de las aplicaciones de acceso condicional](proxy-deployment-aad.md).
1. Para habilitar las conclusiones en un entorno local, configure Cloud App Security para la [integración con su entorno de Azure ATP](aatp-integration.md).

## Fase 2: Identificación de los usuarios de riesgo principales<a name="identify"></a>

Para identificar quiénes son los usuarios de más riesgo en Cloud App Security:

1. Vaya al panel de Cloud App Security y examine las personas identificadas en el icono **Usuarios principales por prioridad de investigación**. Luego, uno por uno, vaya a su página de usuario para investigarlos.  
El **número de prioridad de investigación**, que se encuentra junto al nombre de usuario, es la suma de todas las actividades de riesgo del usuario durante la última semana.

   ![Panel Usuarios principales](./media/dashboard-top-users.png)

1. Haga clic en un usuario determinado para llegar a la página **Usuario**.
    ![Página Usuario](./media/user-page.png)

1. Revise la información de la página Usuario para obtener información general sobre el usuario y ver si hay puntos en los que dicho usuario haya realizado actividades inusuales para él o se hayan ejecutado a una hora inusual. **Puntuación del usuario en comparación con la de la organización** representa en qué percentil se encuentra el usuario según la clasificación de la organización: en qué puesto está en la lista de usuarios que debe investigar respecto a otros usuarios de la organización. El número aparecerá en color rojo si un usuario está en el percentil 90 de los usuarios de riesgo de toda la organización o por encima de dicho percentil.  
La página Usuario le ayuda a responder a las siguientes preguntas:
    * ¿Quién es el usuario?  
    Fíjese en el panel izquierdo para obtener información sobre quién es el usuario y qué información se tiene de él. Este panel proporciona información sobre el rol del usuario en la empresa y el departamento. ¿Es el usuario un ingeniero de DevOps que a menudo realiza actividades inusuales como parte de su trabajo? ¿Es el usuario un empleado descontento que ha sido descartado para un ascenso?

    * ¿Es un usuario de riesgo?  
    Consulte la parte superior del panel derecho para saber si merece la pena investigar al usuario. ¿Qué es la [puntuación de riesgo](#risk-score) del empleado?
    * ¿Qué riesgo representa el usuario para la organización?  
    Examine la lista que se encuentra en el panel inferior, que proporciona cada actividad y cada alerta relacionadas con el usuario, para ayudarlo a empezar a entender qué tipo de riesgo representa. En la escala de tiempo, haga clic en cada línea para que pueda explorar en profundidad la actividad o alerta propiamente dichas. También puede hacer clic en el número que aparece junto a la actividad para comprender la evidencia que ha influido en la propia puntuación.

  >[!NOTE]
  >Es importante recordar que, mientras que la página Usuario proporciona información sobre los dispositivos, los recursos y las cuentas de todas las actividades, la puntuación de prioridad de investigación es la suma de todas las actividades de riesgo y las alertas de los últimos siete días.

## Fase 3: Investigación en profundidad de los usuarios<a name="investigate"></a>

Al investigar un usuario en función de una alerta o si vio una alerta en un sistema externo, puede haber actividades que por sí solas no puedan ocasionar alarma, pero cuando Cloud App Security las agrega junto con otras actividades, la alerta puede ser indicio de un evento sospechoso.

Al investigar a un usuario, se formulará estas preguntas sobre las actividades y alertas que observa:

* ¿Hay una justificación comercial para que este empleado realice estas actividades? Por ejemplo, si alguien de marketing accede a la base de código o alguien de desarrollo accede a la base de datos de finanzas, debe realizar un seguimiento con el empleado para asegurarse de que se trata de una actividad intencionada y justificada.

* Vaya al **registro de actividad** para comprender por qué esta actividad recibió una puntuación alta y otras no. Puede establecer la opción **Prioridad de investigación** en **Se ha establecido** para comprender qué actividades son sospechosas. Por ejemplo, puede filtrar por la prioridad de investigación de todas las actividades que se produjeron en Ucrania. Así, puede ver si hubo otras actividades de riesgo, desde dónde se conectó el usuario, y puede pasar fácilmente a otras exploraciones en profundidad, como actividades locales y en la nube no anómalas recientes, para continuar con la investigación.

## Fase 4: Protección de la organización<a name="protect"></a>

Si su investigación indica que un usuario está en peligro, siga estos pasos para mitigar el riesgo.

* Póngase en contacto con el usuario: con la información de contacto del usuario integrada en Cloud App Security desde Active Directory, puede profundizar en cada actividad y alerta para resolver la identidad del usuario. Asegúrese de que el usuario esté familiarizado con las actividades.

* Directamente desde el portal de Cloud App Security, haga clic en el control **Acciones de usuario** y elija si se requiere que el usuario vuelva a iniciar sesión, se suspende al usuario o se confirma la vulneración de identidad de usuario.

* En el caso de una identidad en peligro, puede pedir al usuario que restablezca su contraseña; asegúrese de que la contraseña cumpla con las directrices de prácticas recomendadas relativas a la longitud y la complejidad.
* Si explora en profundidad una alerta y determina que la actividad no debe haber desencadenado dicha alerta, en el [cajón de actividades](activity-filters.md), haga clic en el vínculo **Envíenos comentarios** para que podamos estar seguros de ajustar nuestro sistema de alertas teniendo en cuenta la organización.
* Después de corregir el problema, cierre la alerta.

## <a name="see-also"></a>Consulte también

> [!div class="nextstepaction"]
> [Actividades diarias para proteger el entorno de nube](daily-activities-to-protect-your-cloud-environment.md)

[!INCLUDE [Open support ticket](includes/support.md)]
