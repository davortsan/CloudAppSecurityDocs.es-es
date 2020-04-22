---
title: Detección y administración de shadow IT | Microsoft Docs
description: En este tutorial se describe el proceso para aplicar automáticamente etiquetas de clasificación de Azure Information Protection en Microsoft Cloud App Security.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 11/11/2019
ms.topic: tutorial
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: dannyk
ms.suite: ems
ms.openlocfilehash: 4c85117dfd4080946fa5e1a205ec9fc890dea199
ms.sourcegitcommit: 0b929f7c8feed7dfb40d5294179fd5c6fc079614
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/21/2020
ms.locfileid: "79241824"
---
# <a name="tutorial-discover-and-manage-shadow-it-in-your-network"></a>Tutorial: detección y administración de shadow IT en la red

*Se aplica a: Microsoft Cloud App Security*

Cuando se pregunta a los administradores de TI cuántas aplicaciones en la nube creen que usan sus empleados, la media es de 30 o 40. En realidad, la media de aplicaciones que usan los empleados de su organización es de más de 1000 aplicaciones distintas. Shadow IT le permite conocer e identificar qué aplicaciones se usan y cuál es el nivel de riesgo que suponen. El 80 % de los empleados usan aplicaciones no autorizadas que no ha revisado nadie y que es posible que no cumplan con las directivas de seguridad y cumplimiento. Además, debido a que los clientes pueden acceder a sus recursos y aplicaciones desde fuera de la red corporativa, ya no es suficiente disponer de reglas y directivas en los firewalls.

En este tutorial se proporcionan las instrucciones para usar Cloud Discovery, una herramienta con la que podrá detectar qué aplicaciones se usan, explorar el riesgo que estas suponen, configurar directivas para identificar el uso de nuevas aplicaciones peligrosas y desautorizar dichas aplicaciones para bloquearlas de forma nativa con su dispositivo de proxy o firewall.

> [!div class="checklist"]
>
> * Detección e identificación de shadow IT
> * Evaluación y análisis
> * Administración de las aplicaciones
> * Creación avanzada de informes sobre detección de Shadow IT
> * Control de aplicaciones autorizadas

## <a name="how-to-discover-and-manage-shadow-it-in-your-network"></a>Detección y administración de shadow IT en su red

Use este proceso para implementar Cloud Discovery de shadow IT en su organización.

![ciclo de vida de shadow IT](media/shadow-it-lifecycle.png)

### <a name="phase-1-discover-and-identify-shadow-it"></a>Fase 1: Detección e identificación de shadow IT

1. **Detección de shadow IT**: ejecute Cloud Discovery para identificar la postura de seguridad de su organización y así ver qué sucede realmente en su red. Para obtener más información, consulte [Configuración de Cloud Discovery](set-up-cloud-discovery.md). Esto puede realizarse mediante cualquiera de los métodos siguientes:

    * Para tenerlo todo a punto rápidamente, use Cloud Discovery e intégrelo con [Microsoft Defender ATP](wdatp-integration.md). Esta integración nativa le permite empezar inmediatamente a recopilar datos del tráfico de red en dispositivos Windows 10, tanto en la red como fuera de esta.

    * Para obtener cobertura en todos los dispositivos conectados a la red, es importante implementar el [Recopilador de registros de Cloud App Security](discovery-docker.md) en los firewalls y otros servidores proxy para recopilar datos de los puntos de conexión y enviarlos a Cloud App Security para su análisis.

    * Integre Cloud App Security con el proxy. Cloud App Security se integra de forma nativa con algunos servidores proxy de terceros, incluido [Zscaler](zscaler-integration.md).

Dado que las directivas no son las mismas en todos los grupos de usuarios, regiones y grupos de negocios, es posible que quiera crear un informe de shadow IT dedicado para cada una de estas unidades. Para obtener más información, vea [Docker en Windows local](discovery-docker-windows.md#continuous-reports).

Ahora que Cloud Discovery se está ejecutando en la red, examine los informes continuos que se generan y consulte el [panel de Cloud Discovery](working-with-cloud-discovery-data.md) para obtener una visión completa de las aplicaciones que se usan en su organización. Le recomendamos que las examine por categoría, porque muchas veces verá que se usan aplicaciones no autorizadas para propósitos relacionados con el trabajo legítimos que no podía realizar una aplicación autorizada.

1. **Identifique los niveles de riesgo de las aplicaciones**: Use el catálogo de aplicaciones en la nube de Cloud App Security para profundizar más en los riesgos relacionados con las aplicaciones detectadas. El catálogo de riesgo de Cloud App Security incluye más de 16 000 aplicaciones que se evalúan con más de 80 factores de riesgo. Los factores de riesgo abarcan desde información general sobre la aplicación (dónde está la sede de la aplicación o quién es el editor) hasta los controles y las medidas de seguridad (compatibilidad para el cifrado en reposo o proporción de un registro de auditoría de la actividad del usuario). Para obtener más información, vea [Trabajo con la puntuación de riesgo](risk-score.md).

    * En el portal de Cloud App Security, en **Detección**, haga clic en **Aplicaciones detectadas**. Filtre la lista de aplicaciones detectadas en su organización según los factores de riesgo que quiera analizar. Por ejemplo, puede usar los filtros avanzados para encontrar todas las aplicaciones con una puntuación de riesgo inferior a 8.

    * Para explorar la aplicación en profundidad y obtener más información sobre los factores de riesgo de seguridad de la aplicación, haga clic en el nombre y, a continuación, en la pestaña **Información**.

### <a name="phase-2-evaluate-and-analyze"></a>Fase 2: Evaluación y análisis

1. **Evalúe el cumplimiento**: compruebe si las aplicaciones están certificadas como compatibles según los estándares de su organización, como HIPAA, SOC2 o RGPD.

    * En el portal de Cloud App Security, en **Detección**, haga clic en **Aplicaciones detectadas**. Filtre la lista de aplicaciones detectadas en su organización según los factores de riesgo de cumplimiento que quiera analizar. Por ejemplo, use la consulta sugerida para filtrar las aplicaciones que no cumplen con la normativa.

    * Para explorar la aplicación en profundidad y obtener más información sobre de los factores de riesgo del cumplimiento de la aplicación, haga clic en el nombre y, a continuación, en la pestaña **Información**.

1. **Analice el uso**: ahora que sabe si quiere o no que se use la aplicación en la organización, querrá investigar cómo y quién la usa. Si solo se usa de forma limitada en la organización, es posible que no suponga un problema, pero si el uso aumenta puede que quiera recibir una notificación para decidir si quiere bloquear la aplicación.

    * En el portal de Cloud App Security, en **Detección**, haga clic en **Aplicaciones detectadas** y, a continuación, explore en profundidad haciendo clic en la aplicación específica que quiera investigar. La pestaña **Uso** le permite saber cuántos usuarios activos están usando la aplicación y cuánto tráfico genera. Esto ya puede proporcionarle una buena idea de lo que ocurre con la aplicación. Después, si quiere ver quién está usando la aplicación en concreto, puede profundizar más haciendo clic en **Total de usuarios activos**. Este paso importante puede proporcionarle información pertinente. Por ejemplo, si detecta que todos los usuarios de una aplicación específica pertenecen al departamento de marketing, es posible que haya una necesidad empresarial de esta aplicación y, si es peligrosa, debería comunicarse con ese departamento para encontrar una alternativa antes de bloquearla.

    * Profundice aún más al investigar el uso de aplicaciones detectadas. Vea subdominios y recursos para obtener información sobre actividades específicas, acceso a datos y uso de recursos en los servicios en la nube. Para obtener más información, consulte [Análisis detallado de las aplicaciones detectadas](discovered-apps.md#deep-dive-into-discovered-apps) y [Detección de recursos y aplicaciones personalizadas](discovered-apps.md#discover-resources-and-custom-apps).

1. Use el catálogo de aplicaciones en la nube y filtre por las aplicaciones que pertenezcan a la misma categoría de aplicación en cuestión. Luego, con el uso de los filtros avanzados, identifique soluciones que cumplan con los distintos controles de seguridad que se necesiten para cumplir con la directiva de su organización.

### <a name="phase-3-manage-your-apps"></a>Fase 3: Administración de las aplicaciones

* **Administre las aplicaciones en la nube**: Cloud App Security le ayuda con el proceso de administración del uso de aplicaciones en su organización. Después de identificar los distintos patrones y comportamientos usados en su organización, puede crear nuevas etiquetas de aplicaciones personalizadas para clasificar las aplicaciones según su estado de negocio o su justificación. Estas etiquetas se pueden usar para fines de supervisión específicos, por ejemplo, para identificar si hay un tráfico elevado dirigido a aplicaciones etiquetadas como aplicaciones de almacenamiento en la nube peligrosas. Las etiquetas de las aplicaciones se pueden administrar en la **configuración de Cloud Discovery** > **Etiquetas de aplicación**. Estas etiquetas se pueden usar posteriormente para el filtrado en las páginas de Cloud Discovery y crear directivas con ellas.

* **Supervisión continua**: ahora que ha investigado en profundidad las aplicaciones, es posible que quiera establecer directivas que supervisen las aplicaciones y proporcionen control cuando sea necesario.

Ahora es el momento de crear directivas para que se le avise automáticamente cuando se produzca algo sospechoso. Por ejemplo, puede que quiera crear una **directiva de detección de aplicaciones** que le permita saber cuándo hay un pico en las descargas o en el tráfico de una aplicación sospechosa. Para conseguirlo, debe habilitar las directivas **Comportamiento anómalo en usuarios detectados**, **Comprobación de cumplimiento de la aplicación de almacenamiento en la nube** y **Nueva aplicación de riesgo**. Puede además establecer la directiva para recibir notificaciones por correo electrónico o mensaje de texto. Para obtener más información, vea [referencia de la plantilla de directiva](policy-template-reference.md), más sobre [directivas de Cloud Discovery](cloud-discovery-policies.md) y configuración de [directivas de detección de aplicaciones](cloud-discovery-policies.md).

Examine la página de alertas y use el filtro **Tipo de directiva** para ver las alertas de detección de aplicaciones. En el caso de las aplicaciones que coincidan con las directivas de detección de aplicaciones, se recomienda realizar una investigación en profundidad para obtener más información sobre la justificación empresarial del uso de la aplicación, por ejemplo, poniéndose en contacto con los usuarios de la aplicación. Después, repita los pasos de la fase 2 para evaluar el riesgo de la aplicación. A continuación, determine los siguientes pasos para la aplicación, tanto si aprueba su uso en el futuro como si quiere bloquearla la próxima vez que un usuario accede a ella, en cuyo caso debe etiquetarla como no autorizada para que se pueda bloquear mediante el firewall, el proxy o la puerta de enlace web segura. Para obtener más información, consulte [Integración con ATP de Microsoft Defender](wdatp-integration.md#block-access-to-unsanctioned-cloud-apps), [Integración con Zscaler](zscaler-integration.md), [Integración con iboss](iboss-integration.md) y [Exportar un script de bloque para controlar aplicaciones detectadas](governance-discovery.md#export-a-block-script-to-govern-discovered-apps).

### <a name="phase-4-advanced-shadow-it-discovery-reporting"></a>Fase 4: Creación avanzada de informes sobre detección de Shadow IT

Además de las opciones de informes disponibles en Cloud App Security, puede integrar los registros de Cloud Discovery en Azure Sentinel para profundizar en su investigación y análisis. Una vez que los datos están en Azure Sentinel, puede verlos en paneles, ejecutar consultas mediante el lenguaje de consultas de Kusto, exportar consultas a Microsoft Power BI, integrarlos con otros orígenes y crear alertas personalizadas. Para más información, consulte [Integración con Azure Sentinel](siem-sentinel.md).

### <a name="phase-5-control-sanctioned-apps"></a>Fase 5: Control de aplicaciones autorizadas

1. Para habilitar el control de aplicaciones a través de las API, [conecte aplicaciones a través de API](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md) para la supervisión continua.

2. Proteja aplicaciones con el [Control de aplicaciones de acceso condicional](proxy-intro-aad.md).

La naturaleza de las aplicaciones en la nube conlleva una actualización diaria de estas, así como la aparición de nuevas a diario. Por este motivo, los empleados usan continuamente nuevas aplicaciones y es importante mantener, revisar y actualizar las directivas, comprobar qué aplicaciones utilizan los usuarios y ver cuáles son los patrones de uso y comportamiento. Siempre puede ir al panel de Cloud Discovery, ver las nuevas aplicaciones que se están usando y seguir las instrucciones de este artículo para asegurarse de que la organización y los datos están protegidos.

## <a name="see-also"></a>Consulte también

> [!div class="nextstepaction"]
> [Actividades diarias para proteger el entorno de nube](daily-activities-to-protect-your-cloud-environment.md)

[!INCLUDE [Open support ticket](includes/support.md)]  
