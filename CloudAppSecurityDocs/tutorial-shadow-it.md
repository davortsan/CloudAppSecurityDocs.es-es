---
title: Detección y administración de shadow IT | Microsoft Docs
description: En este tutorial se describe el proceso para aplicar etiquetas de clasificación de Azure Information Protection en Microsoft Cloud App Security de forma automática.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 04/21/2019
ms.topic: tutorial
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: eac0b192-98d7-4939-9a07-1d4a7f8c39c3
ms.reviewer: dannyk
ms.suite: ems
ms.openlocfilehash: 31cc0a6eed8887d184b8a3912decb586dd9a46b4
ms.sourcegitcommit: c342abeec95359ddabdabcc3a081a0f91d52407c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72335991"
---
# <a name="tutorial-discover-and-manage-shadow-it-in-your-network"></a>Tutorial: detección y administración de shadow IT en la red 

*Se aplica a: Microsoft Cloud App Security*

Al preguntar a los administradores de TI por el número de aplicaciones en la nube que creen que usan sus empleados, la respuesta es que la media ronda las 30 o 40, cuando en realidad es de más de 1000 aplicaciones distintas. Shadow IT le ayuda a conocer e identificar las aplicaciones que se usan y el nivel de riesgo al que se enfrenta. El 80 % de los empleados usa aplicaciones no autorizadas que no se han revisado y que puede que no sean conformes con las directivas de seguridad y cumplimiento. Además, dado que los empleados pueden acceder a los recursos y aplicaciones desde fuera de la red empresarial, ya no es suficiente disponer de reglas y directivas en los firewalls. 

En este tutorial se proporcionan instrucciones sobre el uso de Cloud Discovery para detectar las aplicaciones que se usan, explorar su riesgo, y configurar directivas para identificar nuevas aplicaciones de riesgo en uso y no autorizarlas con el fin de bloquearlas de forma nativa mediante el dispositivo proxy o firewall.

> [!div class="checklist"]
> * Detección de identificación de shadow IT
> * Evaluación y análisis
> * Administración de las aplicaciones
> * Control de las aplicaciones autorizadas
 
## <a name="how-to-discover-and-manage-shadow-it-in-your-network"></a>Cómo detectar y administrar shadow IT en la red

Siga este proceso para implementar Cloud Discovery de shadow IT en su organización.

![Ciclo de vida de shadow IT](./media/shadow-it-lifecycle.png)

### <a name="phase-1-discover-and-identify-shadow-it"></a>Fase 1: detección de identificación de shadow IT
    
1. **Detección de shadow IT**: Identifique el estado de su organización en lo que respecta a la seguridad mediante la ejecución de Cloud Discovery y descubra lo que sucede realmente en la red. Para obtener más información, consulte [Configurar Cloud Discovery](set-up-cloud-discovery.md). Esto puede hacerse mediante cualquiera de los métodos siguientes:
   
    - Para tenerlo todo a punto rápidamente, use Cloud Discovery e intégrelo con [Microsoft Defender ATP](wdatp-integration.md). Esta integración nativa permite empezar a recopilar datos sobre el tráfico en la nube en sus dispositivos Windows 10, así como activar y desactivar la red.
   
    - Para abarcar todos los dispositivos conectados a la red, es importante implementar el [recopilador de registros de Cloud App Security](discovery-docker.md) en los firewalls y otros servidores proxy. De este modo, podrá recopilar datos de los puntos de conexión y enviarlos a Cloud App Security para su análisis.

   - Integre Cloud App Security con su proxy. Cloud App Security se integra de forma nativa con algunos servidores proxy de terceros, incluido [Zscaler](zscaler-integration.md).
   
 
Dado que las directivas son diferentes entre los grupos de usuarios, regiones y grupos empresariales, es posible que quiera crear un informe de shadow IT específico de cada una de estas unidades. Para más información, consulte [Docker en Windows local](discovery-docker-windows.md#continuous-reports).


Ahora que Cloud Discovery se está ejecutando en la red, consulte los informes continuos que se generan y eche un vistazo al [panel de Cloud Discovery](working-with-cloud-discovery-data.md) para obtener una visión global de las aplicaciones que se usan en su organización. Es recomendable examinarlas por categoría, ya que a menudo se encontrará con que las aplicaciones no autorizadas se usan para fines legítimos relacionados con el trabajo que no pueden abordarse mediante una aplicación autorizada. 

2. **Identificación de los niveles de riesgo de las aplicaciones**: Use el catálogo de aplicaciones en la nube de Cloud App Security para profundizar más en los riesgos relacionados con las aplicaciones detectadas. El catálogo de riesgo de Cloud App Security incluye más de 16 000 aplicaciones que se evalúan con más de 80 factores de riesgo. Los factores de riesgo parten de información general sobre la aplicación (ubicación de la sede central, editor de la aplicación, etc.) y abarcan medidas de seguridad y controles (compatibilidad con el cifrado en reposo, registro de auditoría de la actividad del usuario, etc.). Para obtener más información, consulte [Trabajo con la puntuación de riesgo](risk-score.md).
    
   - En el portal de Cloud App Security, en la sección **Detectar**, haga clic en **Aplicaciones detectadas**. Filtre la lista de aplicaciones detectadas en uso en su organización según los factores de riesgo que quiera analizar. Por ejemplo, puede usar los filtros avanzados para buscar todas las aplicaciones con una puntuación de riesgo inferior a 8. 

   - Para explorar la aplicación en profundidad y obtener más información sobre de los factores de riesgo de seguridad de la aplicación y su cumplimiento, haga clic en el nombre y, a continuación, en la pestaña **Información**.
    
### <a name="phase-2-evaluate-and-analyze"></a>Fase 2: evaluación y análisis

1. **Evaluación del cumplimiento**: Compruebe si las aplicaciones están certificadas como conformes con los estándares de su organización, como HIPAA, SOC2 y el RGPD.
   - En el portal de Cloud App Security, en la sección **Detectar**, haga clic en **Aplicaciones detectadas**. Filtre la lista de aplicaciones detectadas en su organización según los factores de riesgo que quiera analizar. Por ejemplo, use la consulta sugerida para filtrar las aplicaciones no conformes.
   - Para explorar la aplicación en profundidad y obtener más información sobre de los factores de riesgo del cumplimiento de la aplicación, haga clic en el nombre y, a continuación, en la pestaña **Información**.

2. **Análisis del uso**: Ahora que ya sabe si quiere que la aplicación se use o no en su organización, querrá investigar quién la está utilizando y qué uso está haciendo de ella. Quizás no haya ningún problema si se usa solo de forma limitada; sin embargo, si su uso aumenta, es posible que quiera recibir una notificación para decidir si bloquea la aplicación.
    - En el portal de Cloud App Security, en la sección **Detectar**, haga clic en **Aplicaciones detectadas** y, a continuación, en la aplicación específica que quiera investigar para explorarla en profundidad. La pestaña **Uso** le permite saber cuántos usuarios activos usan la aplicación y la cantidad de tráfico que genera. Esto puede darle una idea bastante acertada de lo que sucede con la aplicación. A continuación, si quiere ver quién la está utilizando, puede obtener todavía más información haciendo clic en **Total de usuarios activos**. Este paso es importante, ya que puede proporcionarle información pertinente. Por ejemplo, si descubre que todos los usuarios de una aplicación específica pertenecen al departamento de Marketing, es posible que exista una necesidad empresarial para utilizar esta aplicación. Asimismo, en el caso de que sea de riesgo, póngase en contacto con estos usuarios para buscar una alternativa antes de bloquearla.

4. Use el catálogo de aplicaciones en la nube y filtre por las aplicaciones que pertenezcan a la misma categoría de aplicación en cuestión. Luego, con el uso de los filtros avanzados, identifique soluciones que cumplan con los distintos controles de seguridad que se necesiten para cumplir con la directiva de su organización.


### <a name="phase-3-manage-your-apps"></a>Fase 3: administración de las aplicaciones
    
- **Administración de las aplicaciones en la nube**: Cloud App Security le ayuda con el proceso de administración del uso de las aplicaciones en su organización. Tras identificar los distintos patrones y los comportamientos presentes en su organización, puede crear nuevas etiquetas de aplicación personalizadas con el fin de clasificar cada una de ellas según su estado o justificación en la empresa.
A continuación, las etiquetas pueden usarse para fines de supervisión específicos, por ejemplo, identificar un tráfico elevado en las aplicaciones etiquetadas como de almacenamiento en la nube de riesgo. Las etiquetas de aplicaciones pueden administrarse en **Configuración de Cloud Discovery** > **Etiquetas de aplicaciones**. Posteriormente, las etiquetas pueden usarse para filtrar contenido en las páginas de Cloud Discovery y crear directivas que las utilicen.

- **Supervisión continua**: Ahora que ya ha investigado exhaustivamente las aplicaciones, es posible que quiera establecer directivas que permitan supervisar las aplicaciones y proporcionen un control cuando sea necesario.

Ahora es el momento de crear directivas para que pueda recibir alertas automáticamente cuando ocurra algo que le preocupe. Por ejemplo, es posible que quiera crear una **Directiva de detección de aplicaciones** que le permita saber si hay un pico en las descargas o el tráfico de una aplicación que quiera supervisar. Puede establecer la directiva para recibir notificaciones por correo electrónico o mensaje de texto. Para obtener más información, consulte [Referencia de plantillas de directiva](policy-template-reference.md) y [Directivas de Cloud Discovery](cloud-discovery-policies.md).


Configure las [**Directivas de detección de aplicaciones**](cloud-discovery-policies.md). Por ejemplo, se recomienda habilitar las directivas **Comportamiento anómalo en usuarios detectados**, **Comprobación de cumplimiento de la aplicación de almacenamiento en la nube** y **Nueva aplicación de riesgo**.


Eche un vistazo a la página de alertas y use el filtro de **Tipo de directiva** para consultar las alertas de detección de aplicaciones. En el caso de las aplicaciones que coincidan con las directivas de detección de aplicaciones, se recomienda realizar una investigación en profundidad para obtener más información sobre la justificación empresarial del uso de la aplicación, por ejemplo, poniéndose en contacto con los usuarios de las aplicaciones. Seguidamente, repita los pasos de la fase 2 para evaluar el riesgo de la aplicación. A continuación, determine los siguientes pasos: si aprueba el uso de la aplicación en el futuro o quiere bloquearla la próxima vez que un usuario acceda a ella. En este último caso, deberá etiquetarla como no autorizada, de modo que se pueda bloquear mediante el firewall, el proxy o la puerta de enlace web segura. 


### <a name="phase-4-control-sanctioned-apps"></a>Fase 4: control de las aplicaciones autorizadas

1. Para habilitar el control de aplicaciones a través de una API, [conecte las aplicaciones a través de una API](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md).(enable-instant-visibility-protection-and-governance-actions-for-your-apps.md) para su supervisión continua.

2. Proteja las aplicaciones con el [Control de aplicaciones de acceso condicional](proxy-intro-aad.md).


La naturaleza de las aplicaciones en la nube implica que se actualizan diariamente y aparecen otras nuevas continuamente. Por este motivo, los empleados utilizan constantemente nuevas aplicaciones y es importante mantener un seguimiento, revisar y actualizar las directivas, comprobar qué aplicaciones usan los usuarios y analizar los patrones de uso y comportamiento. Siempre puede ir al panel de Cloud Discovery, consultar las nuevas aplicaciones que se usan y seguir las instrucciones de este artículo para asegurarse de que tanto su organización como los datos estén protegidos.


## <a name="see-also"></a>Consulte también  
[Actividades diarias para proteger el entorno de nube](daily-activities-to-protect-your-cloud-environment.md)   

[Los clientes Premier también pueden elegir Cloud App Security directamente desde el Portal Premier.](https://premier.microsoft.com/)  
  
  
