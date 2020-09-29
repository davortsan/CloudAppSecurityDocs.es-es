---
title: Detección de actividad sospechosa del usuario con análisis de comportamiento (UEBA)
description: En este tutorial se describe el proceso para ajustar las detecciones de actividad del usuario en Microsoft Cloud App Security.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 05/10/2020
ms.topic: tutorial
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: galz
ms.suite: ems
ms.openlocfilehash: bdf58b83e01dc6ab088d3956f2a71ef52f368438
ms.sourcegitcommit: 575f2b2efa9ca4477d7e60271d21e225ef2c38ea
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/22/2020
ms.locfileid: "90881188"
---
# <a name="tutorial-detect-suspicious-user-activity-with-ueba"></a>Tutorial: Detección de actividad sospechosa del usuario con UEBA

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Microsoft Cloud App Security proporciona las mejores detecciones en la cadena de interrupción de ataque para usuarios en peligro, amenazas internas, filtración, ransomware, etc. Nuestra completa solución se logra combinando varios métodos de detección, incluidos anomalías, análisis de comportamiento (UEBA) y detecciones de actividad basadas en reglas, para proporcionar una visión general de cómo los usuarios usan las aplicaciones en su entorno.

Así pues, ¿por qué es importante detectar un comportamiento sospechoso? El impacto de un usuario capaz de modificar su entorno en la nube puede ser significativo e influir directamente en su capacidad para ejecutar su negocio. Por ejemplo, se pueden poner en peligro recursos corporativos clave tales como los servidores que ejecutan el servicio o sitio web público que ofrece a los clientes.

Cuando se usan datos capturados de varios orígenes, Cloud App Security los analiza para extraer las actividades del usuario y la aplicación de la organización que proporcionan a sus analistas de seguridad visibilidad del uso de la nube. Los datos recopilados se correlacionan, estandarizan y enriquecen con la inteligencia sobre amenazas, la ubicación y muchos otros detalles para proporcionar una vista precisa y coherente de las actividades sospechosas.

Por tanto, para comprender totalmente los beneficios de estas detecciones, asegúrese primero de configurar los orígenes siguientes:

* **[Registro de actividad](activity-filters.md)**  
Actividades de sus [aplicaciones conectadas a la API](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md).
* **[Registro de detección](tutorial-shadow-it.md)**  
Actividades extraídas de los registros de tráfico del proxy y el firewall que se reenvían a Cloud App Security. Los registros se analizan en contraposición con el [catálogo de aplicaciones en la nube](risk-score.md), se clasifican y se puntúan en función de más de 80 factores de riesgo.
* **[Registro del proxy](proxy-intro-aad.md)**  
Actividades de las [aplicaciones de control de aplicaciones de acceso condicional](tutorial-proxy.md#phase-1-monitor-user-activities-for-anomalies).

A continuación, querrá ajustar las directivas. Las siguientes directivas se pueden ajustar estableciendo filtros, umbrales dinámicos (UEBA) para ayudar a entrenar sus modelos de detección y supresiones para reducir las detecciones de falsos positivos habituales:

* Detección de anomalías
* Detección de anomalías de Cloud Discovery
* Detección de actividad basada en reglas

En este tutorial se proporcionan instrucciones para ajustar las detecciones de actividad del usuario a fin de identificar el auténtico peligro y reducir la fatiga de alertas resultante del tratamiento de elevados volúmenes de detecciones de falsos positivos.

> [!div class="checklist"]
>
> * Configuración de intervalos de direcciones IP
> * Ajuste de directivas de detección de anomalías
> * Ajuste de directivas de detección de anomalías de Cloud Discovery
> * Ajuste de directivas de detección basada en reglas
> * Configuración de alertas
> * Investigación y corrección

## <a name="phase-1-configure-ip-address-ranges"></a>Fase 1: Configuración de intervalos de direcciones IP

Antes de configurar directivas individuales, es aconsejable configurar intervalos IP a fin de que estén disponibles para su uso en el ajuste de cualquier tipo de directiva de detección de actividad del usuario sospechosa.

Dado que la información de direcciones IP es fundamental en casi todas las investigaciones, [configurar direcciones IP conocidas](ip-tags.md) ayuda a nuestros algoritmos de aprendizaje automático a identificar ubicaciones conocidas y considerarlas como parte de los modelos de Machine Learning. Por ejemplo, agregar el intervalo de direcciones IP de la VPN ayudará al modelo a clasificar correctamente este intervalo IP y lo excluirá automáticamente de las detecciones de viaje imposible, ya que la ubicación de la VPN no representa la verdadera ubicación de ese usuario.

Nota:  Los intervalos IP configurados no se limitan a las detecciones y se usan en Cloud App Security en áreas como las actividades del registro de actividad, el acceso condicional, etc. Tenga esto en cuenta al configurar los intervalos. Así pues, por ejemplo, la identificación de las direcciones IP de la oficina física permite personalizar el modo en que se muestran e investigan los registros y las alertas.

### <a name="review-out-of-the-box-anomaly-detection-alerts"></a>Revisión de alertas de detección de anomalías predefinidas

Cloud App Security incluye un conjunto de alertas de detección de anomalías para identificar distintos escenarios de seguridad. Estas detecciones se habilitan automáticamente de forma inmediata y comenzarán a generar perfiles de la actividad del usuario y a generar alertas en cuanto estén conectados los [conectores de aplicaciones](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md) pertinentes.

Para empezar, familiarícese con las [diferentes directivas de detección](control-cloud-apps-with-policies.md), dé prioridad a los principales escenarios que cree que son más pertinentes para la organización y ajuste las directivas en consecuencia.

## <a name="phase-2-tune-anomaly-detection-policies"></a>Fase 2: Ajuste de directivas de detección de anomalías

Varias directivas de detección de anomalías integradas están disponibles en Cloud App Security y preconfiguradas para casos de uso de seguridad comunes. Debe dedicar algo de tiempo a familiarizarse con las detecciones más populares, como, por ejemplo:

* **Viaje imposible**  
Actividades del mismo usuario en ubicaciones diferentes dentro de un período que es más breve que el tiempo de viaje esperado entre las dos ubicaciones.
* **Actividad desde un país poco frecuente**  
Actividad de una ubicación que ni el usuario ni ningún usuario de la organización han visitado nunca o recientemente.
* **Detección de malware**  
Analiza los archivos en las aplicaciones en la nube y ejecuta los archivos sospechosos a través del motor de inteligencia sobre amenazas de Microsoft para determinar si están asociados a malware conocido.
* **Actividad de ransomware**  
Cargas en la nube de archivos que pueden estar infectados con ransomware.
* **Actividad desde direcciones IP sospechosas**  
Actividad de una dirección IP que Inteligencia sobre amenazas de Microsoft ha identificado como de riesgo.
* **Reenvío sospechoso desde la bandeja de entrada**  
Detecta reglas de reenvío sospechoso desde la bandeja de entrada establecidas en la bandeja de entrada de un usuario.
* **Varias actividades de descarga de archivos poco habituales**  
Detecta varias actividades de descarga de archivos en una única sesión en relación con la línea base descubierta. Esto podría indicar un intento de brecha.
* **Actividades administrativas poco habituales**  
Detecta varias actividades administrativas en una única sesión en relación con la línea base descubierta. Esto podría indicar un intento de brecha.

Para obtener una lista completa de las detecciones y lo que hacen, consulte las [directivas de detección de anomalías](anomaly-detection-policy.md#anomaly-detection-policies).

Una vez que esté familiarizado con las directivas, debe tener en cuenta cómo desea ajustarlas a los requisitos específicos de la organización para dirigir mejor las actividades que quizás desee investigar más.

1. **Definición del ámbito de las directivas para usuarios o grupos específicos**

    Definir el ámbito de las directivas para usuarios específicos puede ayudar a reducir el ruido de las alertas que no son pertinentes para la organización. Cada directiva puede [configurarse para incluir o excluir usuarios y grupos específicos](anomaly-detection-policy.md#scope-anomaly-detection-policies), como en los ejemplos siguientes:

    * **Simulaciones de ataques**  
    Muchas organizaciones emplean un usuario o grupo para simular ataques constantemente. Obviamente, no tiene sentido recibir alertas constantemente de las actividades de estos usuarios. Por tanto, puede configurar las directivas para excluir a estos usuarios o grupos. Esto también ayuda a los modelos de Machine Learning a identificar estos usuarios y ajustar sus umbrales dinámicos en consecuencia.
    * **Detecciones de destino**  
    Su organización puede estar interesada en investigar un grupo específico de usuarios VIP como, por ejemplo, los miembros de un administrador o grupo CXO. En este escenario, puede crear una directiva para las actividades que quiera detectar y elegir incluir solo el conjunto de usuarios o grupos que le interesen.

2. **Ajuste de detecciones de inicios de sesión anómalos**

    Algunas organizaciones quieren ver las alertas resultantes de las [actividades de inicio de sesión con errores](anomaly-detection-policy.md#multiple-failed-login-attempts) porque pueden indicar que alguien intenta dirigir una o varias cuentas de usuario. Por otro lado, los ataques por fuerza bruta en las cuentas de usuario se producen todo el tiempo en la nube y las organizaciones no pueden evitarlos de ninguna forma. Por tanto, las organizaciones más grandes normalmente deciden recibir alertas de las actividades de inicio de sesión sospechosas que dan lugar a actividades de inicio de sesión correcto, ya que pueden representar un auténtico peligro.

    El robo de identidad es una fuente de peligro clave y supone un vector de amenaza importante para la organización. Nuestras alertas de detecciones de [viaje imposible](anomaly-detection-policy.md#impossible-travel), [direcciones IP anónimas](anomaly-detection-policy.md#activity-from-anonymous-ip-addresses) y [país poco frecuente](anomaly-detection-policy.md#activity-from-infrequent-country) le ayudan a detectar aquellas actividades que sugieren que una cuenta podría estar en peligro. Es posible que desee personalizar estas directivas para centrarse solo en los inicios de sesión correctos que indican una amenaza inminente que requiere una acción y proceder en consecuencia. Por ejemplo, puede personalizar la directiva de país poco frecuente para alertar solo de los inicios de sesión correctos desde ubicaciones que no visitó recientemente ningún usuario de la organización. Puede conseguirlo [editando la directiva](anomaly-detection-policy.md#tune-anomaly-detection-policies). En Configuración avanzada, establezca Analizar actividades de inicio de sesión en una de las opciones de inicio de sesión correcto.

3. **Ajuste de la sensibilidad del [viaje imposible](anomaly-detection-policy.md#impossible-travel)** [Configure el control de sensibilidad](anomaly-detection-policy.md#tune-anomaly-detection-policies) que determina el nivel de supresiones que se aplica al comportamiento anómalo antes de desencadenar una alerta de viaje imposible. Por ejemplo, las organizaciones interesadas en alta fidelidad deben considerar la posibilidad de aumentar el nivel de sensibilidad. Por otro lado, si la organización tiene muchos usuarios que viajan, considere la posibilidad de reducir el nivel de sensibilidad para suprimir las actividades de las ubicaciones comunes de un usuario aprendidas en actividades anteriores. Puede elegir entre los niveles de sensibilidad siguientes:

    * **Bajo**: supresiones del usuario, el inquilino y el sistema
    * **Media**: supresiones del usuario y el sistema
    * **Alta**: solo supresiones del sistema

    Donde:

    | Tipo de supresión | Descripción |
    | --- | --- |
    | **Sistema** | Detecciones integradas que siempre se suprimen. |
    | **Inquilino** | Actividades comunes basadas en la actividad anterior del inquilino. Por ejemplo, la supresión de actividades de un ISP sobre el que se alertó anteriormente en la organización. |
    | **Usuario** | Actividades comunes basadas en la actividad anterior del usuario específico. Por ejemplo, la supresión de actividades de una ubicación que suele utilizar el usuario. |

## <a name="phase-3-tune-cloud-discovery-anomaly-detection-policies"></a>Fase 3: Ajuste de directivas de detección de anomalías de Cloud Discovery

Al igual que ocurre con las directivas de detección de anomalías, hay varias [directivas de detección de anomalías de Cloud Discovery](cloud-discovery-anomaly-detection-policy.md) que puede ajustar. Por ejemplo, la directiva de filtración de datos a aplicaciones no autorizadas le avisa cuando los datos se filtran a una aplicación no autorizada y viene preconfigurada con la configuración basada en la experiencia de Microsoft del campo de seguridad.

Sin embargo, puede ajustar las directivas integradas o crear sus propias directivas que le ayuden a identificar otros escenarios que tal vez le interese investigar. Dado que estas directivas se basan en los registros de Cloud Discovery, cuentan con diferentes [funcionalidades de ajuste](cloud-discovery-anomaly-detection-policy.md#cloud-discovery-anomaly-detection-policy-reference) más centradas en el comportamiento anómalo de la aplicación y la filtración de datos.

1. **Ajuste de la supervisión de uso**  
Establezca los filtros de uso para controlar la línea base, el ámbito y el período de actividad para detectar un comportamiento anómalo. Por ejemplo, puede que desee recibir alertas de actividades anómalas relacionadas con los empleados de nivel ejecutivo.

2. **Ajuste de la sensibilidad de la alerta**  
Para evitar la fatiga de alertas, configure la sensibilidad de las alertas. Puede usar el control de sensibilidad para controlar el número de alertas de alto riesgo enviadas por 1000 usuarios cada semana. Las sensibilidades más elevadas no requieren que tanta varianza se considere una anomalía y genere más alertas. En general, establezca una sensibilidad baja para los usuarios que no tienen acceso a los datos confidenciales.

## <a name="phase-4-tune-rule-based-detection-activity-policies"></a>Fase 4: Ajuste de directivas de detección basadas en reglas (actividad)

Las [directivas de detección basadas en reglas](user-activity-policies.md) proporcionan la capacidad de complementar las directivas de detección de anomalías con requisitos específicos de la organización. Recomendamos crear las directivas basadas en reglas utilizando una de nuestras plantillas de directiva de actividad (vaya a **Control** > **Plantillas** y establezca el filtro de **tipo** en **Directiva de actividad**) y [configurándolas](activity-filters-queries.md) a continuación para detectar aquellos comportamientos que no sean normales en su entorno. Por ejemplo, en el caso de algunas organizaciones sin presencia en un país/región en particular, puede que tenga sentido crear una directiva que detecte las actividades anómalas de ese país y alertar sobre ellas. En el caso de otras organizaciones con sucursales grandes en ese país, las actividades del mismo serían normales y no tendría sentido detectar dichas actividades.

1. **Ajuste del volumen de actividad**  
Elija el volumen de actividad requerido antes de que la detección genere una alerta. Con nuestro ejemplo de país, si no tiene presencia alguna en un país/región, incluso una sola actividad es importante y garantiza una alerta. Sin embargo, un error de inicio de sesión único podría ser un error humano y solo de interés si hay muchos errores en un breve período.
2. **Ajuste de los [filtros de actividad](activity-filters-queries.md)**  
Establezca los filtros que necesita para detectar el tipo de actividad sobre el que desea generar alertas. Por ejemplo, para detectar la actividad de un país, use el parámetro **Ubicación**.
3. **Ajuste de alertas**  
Para evitar la fatiga de alertas, establezca el **límite de alertas diarias**.

## <a name="phase-5-configure-alerts"></a>Fase 5: Configuración de alertas

Puede optar por recibir alertas en el formato y medio que mejor se adapten a sus necesidades. Para recibir alertas inmediatas en cualquier momento del día, es posible que prefiera recibirlas por correo electrónico o mensaje de texto.

También es posible que desee poder analizar alertas en el contexto de otras alertas desencadenadas por otros productos de la organización para obtener una visión holística de una posible amenaza. Por ejemplo, puede que desee correlacionar entre eventos basados en la nube y locales para ver si hay cualquier otra evidencia de mitigación que pueda confirmar un ataque.

Además, también puede desencadenar una automatización de alertas personalizada mediante nuestra integración con [Microsoft Power Automate](flow-integration.md). Por ejemplo, puede configurar un cuaderno de estrategias para crear automáticamente una incidencia en [ServiceNow](/connectors/service-now/) o enviar un correo electrónico de aprobación para ejecutar una acción de gobierno personalizada cuando se desencadene una alerta.

Use las siguientes directrices para configurar sus alertas:

1. **Correo electrónico/SMS**  
Elija su preferencia de entrega para recibir alertas. Puede recibir alertas por correo electrónico, mensaje de texto o ambas opciones.
2. **SIEM**  
Hay varias opciones de integración de SIEM, entre las que se incluyen [Azure Sentinel](siem-sentinel.md), [API Microsoft Graph Security](/graph/security-integration#list-of-connectors-from-microsoft) y otras [SIEM genéricas](siem.md). Elija la integración que mejor se adapte a sus necesidades.
3. **Automatización de Power Automate**  
Cree los cuadernos de estrategias de automatización que necesita y establézcala como la alerta de la directiva en la acción de Power Automate.

## <a name="phase-6-investigate-and-remediate"></a>Fase 6: Investigación y corrección

Fantástico, ha configurado las directivas y empieza a recibir alertas de actividad sospechosa. ¿Qué debe hacer al respecto? En primer lugar, debe realizar los pasos para investigar la actividad. Por ejemplo, es posible que desee ver las actividades que indican que un [usuario se ha puesto en peligro](tutorial-ueba.md#identify).

Para optimizar la protección, debe considerar la posibilidad de configurar acciones de corrección automáticas para minimizar el riesgo en su organización. Nuestras directivas permiten aplicar [acciones de gobierno](control.md) junto con las alertas para que el riesgo en su organización se reduzca incluso antes de empezar a investigar. Las acciones disponibles vienen determinadas por el tipo de directiva, incluidas acciones como suspender a un usuario o bloquear el acceso al recurso solicitado.

[!INCLUDE [Open support ticket](includes/support.md)]
