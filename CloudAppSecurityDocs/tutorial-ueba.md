---
title: Investigación de usuarios de riesgo| Microsoft Docs
description: En este tutorial se describe el proceso para investigar los usuarios de riesgo en Microsoft Cloud App Security, en entornos híbridos, mediante la integración con Azure ATP.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: rkarlin
ms.date: 06/11/2019
ms.topic: tutorial
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: eac0b192-98d7-4939-9a07-1d4a7f8c39c3
ms.reviewer: dannyk
ms.suite: ems
ms.openlocfilehash: 80ef10622093523c92547de4bb52538b705ce168
ms.sourcegitcommit: 917d8cf85ac0b58a3b1788067c2ff92101eb3ccf
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2019
ms.locfileid: "67237247"
---
# <a name="tutorial-investigate-risky-users"></a>Tutorial: Investigación de usuarios de riesgo

*Se aplica a: Microsoft Cloud App Security*

Microsoft Cloud App Security se integra con Azure Advanced Threat Protection para proporcionar análisis de comportamiento de usuarios y entidades (UEBA) para posibilitar una investigación en profundidad en el entorno híbrido en las aplicaciones en la nube y en las actividades locales. 

En un único portal, Cloud App Security ahora ofrece toda la información que necesita para tomar mejores decisiones sobre los riesgos en toda la organización y corregir activamente las amenazas. Mediante la combinación de las alertas y el análisis de los datos en estos sistemas, Cloud App Security es el primer lugar para comenzar a investigar a los usuarios para obtener información basada en identidades en un entorno híbrido:
- Microsoft Cloud App Security, que identifica ataques dentro de una sesión en la nube, no solo cubre los productos de Microsoft, sino también las aplicaciones de terceros
- Azure Advanced Threat Protection, que usa el análisis de comportamiento para identificar los ataques a través de la red local
- Azure Active Directory Identity Protection, que detecta e impide proactivamente los riesgos de usuario e inicio de sesión para las identidades de la nube

Tanto si inicia la investigación de un usuario basándose en algún indicio de riesgo que ve en el panel de Cloud App Security, como si está investigando a un usuario del que es posible que sepa que tiene un motivo que el sistema desconoce, empiece desde el panel de Cloud App Security para analizar en profundidad los usuarios de riesgo.  



En este tutorial se proporcionan instrucciones para el uso de Cloud Discovery para investigar a los usuarios de riesgo.

> [!div class="checklist"]
> * Requisitos previos
> * Identificación de los usuarios de riesgo principales
> * Investigación de un usuario
> * Comprensión del riesgo de los usuarios
> * Protección de la organización


## <a name="prerequisites"></a>Requisitos previos

Para realizar una investigación completa de los usuarios en un entorno híbrido, debe tener:

- Una licencia válida para Microsoft Cloud App Security
- Una licencia válida de Azure ATP conectada a la instancia de Active Directory
- Habilitar Cloud App Security para [integrar con el entorno de Azure ATP](aatp-integration.md) 

>[!NOTE]
>Si no tiene una suscripción para Azure ATP, todavía podrá usar el portal de Cloud App Security para investigar a los usuarios, pero no recibirá información del entorno local. También puede ver información de Azure ATP en el portal de Cloud App Security si tiene una licencia de Azure ATP pero no tiene una licencia de Microsoft Cloud App Security.


## <a name="identify-top-risky-users"></a>Identificación de los usuarios de riesgo principales

Para identificar quiénes son los usuarios de más riesgo en Cloud App Security:

1. Vaya al panel de Cloud App Security y examine las personas identificadas en el icono **Usuarios principales por prioridad de investigación**. Luego, uno por uno, vaya a su página de usuario para investigarlos. <br>El **número de prioridad de investigación**, que se encuentra junto al nombre de usuario, es la suma de todas las actividades de riesgo del usuario durante la última semana. 

   ![Panel Usuarios principales](./media/dashboard-top-users.png) 

2. Haga clic en un usuario determinado para llegar a la página **Usuario**. 
   ![Página Usuario](./media/user-page.png) 

3. Haga clic en **Puntuación de prioridad de la investigación** para ver una lista de todas las actividades de riesgo que se produjeron durante la última semana para dar al usuario esta puntuación determinada. 
4. Revise la información de la página **Usuario** para obtener información general sobre el usuario y ver si hay puntos en los que dicho usuario realizó actividades inusuales para él o se ejecutaron en una hora inusual. **Puntuación del usuario en comparación con la de la organización** representa en qué percentil se encuentra el usuario según la clasificación de la organización: en qué puesto está en la lista de usuarios que debe investigar respecto a otros usuarios de la organización. El número aparecerá en color rojo si un usuario está en el percentil 90 de los usuarios de riesgo de toda la organización o por encima de dicho percentil.<br>La página **Usuario** le ayuda a responder a las siguientes preguntas:
    1. ¿Quién es el usuario?<br>Fíjese en el panel izquierdo para obtener información sobre quién es el usuario y qué información se tiene de él. Este panel proporciona información sobre el rol del usuario en la empresa y el departamento. ¿Es el usuario un ingeniero de DevOps que a menudo realiza actividades inusuales como parte de su trabajo? ¿Es el usuario un empleado descontento que ha sido descartado para un ascenso?
    2. ¿Es un usuario de riesgo?<br>Consulte la parte superior del panel derecho para saber si merece la pena investigar al usuario. ¿Qué es la [puntuación de riesgo](#risk-score) del empleado?
    3. ¿Qué riesgo representa el usuario para la organización?<br>Examine la lista que se encuentra en el panel inferior, que proporciona cada actividad y cada alerta relacionadas con el usuario. Esta lista le ayuda a empezar a entender qué tipo de riesgo representa el usuario para que pueda empezar una investigación más a fondo.

  >[!NOTE]
  >Es importante recordar que mientras la página **Usuario** proporciona información para los dispositivos, recursos y cuentas de todas las actividades, la puntuación de prioridad de investigación es la suma de todas las actividades de riesgo y las alertas de los últimos siete días.
 
 
## <a name="investigate-a-user"></a>Investigación de un usuario
Cuando algo parezca anómalo o haya un usuario al que desea investigar, explore en profundidad las alertas correspondientes de dicho usuario. Es posible que las actividades pequeñas por sí solas no parezcan ser causa de alarma, pero cuando Cloud App Security las agrupa junto con otras actividades algo preocupantes, le permite ver que es necesario realizar una investigación.
 
Al investigar a un usuario, se formulará estas preguntas sobre las actividades y alertas que observa:
- ¿Sus actividades tienen sentido para el trabajo que realiza?
- Examine la escala de tiempo: ¿se realizaron las actividades en momentos en que tiene sentido?
- Para cada actividad para la que la respuesta fue "no", explórela en profundidad y, en **Registro de actividad**, coteje esta actividad con otras actividades realizadas por el mismo usuario. Allí puede ver si hubo otras actividades de riesgo, desde dónde se conectó el usuario y puede pasar fácilmente a otras exploraciones en profundidad, como actividades locales y en la nube no anómalas recientes, para continuar con la investigación.


## Comprensión del riesgo de los usuarios <a name ="risk-score"></a>
    
Use **Puntuación de prioridad de la investigación** para determinar los usuarios que desea investigar en primer lugar. Cloud App Security crea perfiles de usuario para cada usuario en función de los análisis, que tienen en cuenta el tiempo, los grupos de personas del mismo nivel y la actividad esperada del usuario. La actividad que resulta anómala para la línea de base de un usuario se evalúa y puntúa. Una vez que se completa la puntuación, se ejecutan el aprendizaje automático y los cálculos dinámicos del mismo nivel, que son propiedad de Microsoft, en las actividades de usuario para calcular la prioridad de investigación para cada usuario. 

La opción **Puntuación de prioridad de la investigación** le proporciona la capacidad de detectar tanto personal interno malintencionado como atacantes externos que se mueven lateralmente en las organizaciones, sin tener que depender de detecciones deterministas estándar.

Evaluando la urgencia de la investigación de cada usuario específico, Puntuación de prioridad de la investigación se basa en alertas de seguridad, actividades anómalas y el posible impacto en los negocios y los recursos relacionados con cada usuario. 

Si hace clic en el valor de la puntuación para una alerta o una actividad, puede ver las evidencias que explican cómo Cloud App Security puntuó la actividad.

Cada usuario de Azure AD tiene una puntuación de prioridad de la investigación dinámica, que se actualiza constantemente en función del comportamiento reciente y el impacto, creada a partir de datos que se evalúan desde Azure ATP, Microsoft Cloud App Security, así como Azure AD Identity Protection. Ahora puede entender de inmediato las principales amenazas de usuarios reales mediante **Puntuación de prioridad de la investigación** y luego comprobar directamente su impacto en el negocio e investigar todas las actividades relacionadas, sin importar si están comprometidas, extrayendo datos o actuando como amenazas internas.

Cloud App Security usa lo siguiente para medir el riesgo: 

- **Puntuación de las alertas**<br>La puntuación de alertas representa el posible impacto de una alerta específica en cada usuario. La puntuación de alertas se basa en la gravedad, el impacto en el usuario y la popularidad de las alertas en todos los usuarios y en todas las entidades de la organización.

- **Puntuación de las actividades**<br> La puntuación de las actividades determina la probabilidad de que un usuario específico realice una actividad específica, en función del aprendizaje de comportamiento del usuario y las personas del mismo nivel. Las actividades identificadas como las más anómalas reciben las puntuaciones más altas. 


## <a name="protect-your-organization"></a>Protección de la organización

Si ve que un usuario está comprometido o sospecha que hay un problema, es el momento de actuar.
- Directamente desde el portal de Cloud App Security, puede hacer clic en el control **Acciones del usuario** y establecer el usuario como de alto riesgo o suspenderlo.
- Como alternativa, puede restablecer la contraseña del usuario para bloquear su acceso.
- Si explora en profundidad una alerta y determina que la actividad no debe haber desencadenado dicha alerta, en el [cajón de actividades](activity-filters.md), haga clic en el vínculo **Envíenos comentarios** para que podamos estar seguros de ajustar nuestro sistema de alertas teniendo en cuenta la organización.
- Después de corregir el problema, cierre la alerta.


## <a name="see-also"></a>Consulte también  
[Actividades diarias para proteger el entorno de nube](daily-activities-to-protect-your-cloud-environment.md)   

[Los clientes Premier también pueden elegir Cloud App Security directamente desde el Portal Premier.](https://premier.microsoft.com/)  
  
  
