---
title: Administración de la seguridad de plataformas en la nube que usa la organización
description: En este tutorial se describe cómo usar Microsoft Cloud App Security para proteger las plataformas en la nube de Azure, AWS y GCP.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 09/17/2020
ms.topic: tutorial
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.suite: ems
ms.openlocfilehash: 069ed5a6182c88bef89c792793c9bab2e0700f56
ms.sourcegitcommit: 575f2b2efa9ca4477d7e60271d21e225ef2c38ea
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/22/2020
ms.locfileid: "90881014"
---
# <a name="tutorial-manage-cloud-platform-security"></a>Tutorial: Administración de la seguridad de plataformas en la nube

[!INCLUDE [Banner for top of topics](includes/banner.md)]

El trabajo remoto suele conllevar un uso intensivo de aplicaciones en la nube y plataformas en la nube para las tareas empresariales comunes, y expone la necesidad de proteger los entornos de nube y de la adopción de productos de seguridad en la nube. Según el [modelo de responsabilidad compartida](/azure/security/fundamentals/shared-responsibility), una organización es responsable de administrar y proteger su plataforma en la nube: Administración de identidad y acceso (IAM), Virtual Machines (VM) y sus recursos de proceso, datos y almacenamiento, recursos de red y mucho más.

![Protección del entorno de varias nubes](media/tutorial-cloud-platform-security.png)

## <a name="how-does-security-posture-management-help"></a>¿Cómo ayuda la administración de la posición de seguridad?

Es fundamental tener las herramientas de seguridad adecuadas para proteger los recursos que podrían no estar correctamente protegidos. Las organizaciones deben obtener visibilidad de la posición de sus recursos en la nube, tener capacidades de detección para obtener información sobre la utilización real de cada plataforma, ser capaces de supervisar las actividades sospechosas, evaluar y revisar las configuraciones y los estados de cumplimiento, así como estar habilitadas a fin de implementar mecanismos de protección en tiempo real.

La administración de la posición de seguridad en la nube (CSPM) se extiende más allá de la posición de seguridad de IaaS y PaaS, ya que también cubre las configuraciones de SaaS. Por ejemplo, el repositorio de GitHub con un nivel de acceso público o aplicaciones de OAuth que tienen acceso a mis aplicaciones SaaS, como Office 365, G Suite o Sales Force. La CSPM de SaaS es un dominio nuevo y creciente de CSPM, que es una expansión nativa del producto Cloud App Security.

## <a name="protecting-multiple-clouds-from-a-single-management-portal"></a>Protección de varias nubes desde un único portal de administración

La complejidad moderna de las organizaciones, muchas de las cuales usan varias plataformas en la nube para distintos propósitos, y diferentes escalas y estados de implementación, requiere la capacidad de realizar un seguimiento periódico del entorno de varias nubes.  El estado de implementación de algunos servicios puede cambiar con el tiempo y no necesariamente con una notificación completa de los cambios en los equipos de seguridad. Mediante la agrupación de estas señales en un portal, la experiencia de administración se optimiza para ofrecer una administración del tiempo y los recursos aún más eficiente, tanto a las personas que realizan la supervisión como a las que usan los recursos en la nube.

La posición de seguridad de la organización engloba todas las plataformas en la nube de una organización y esta nueva función está diseñada para que la usen los arquitectos de seguridad, los administradores de seguridad central o los analistas de cumplimiento. A partir de esta característica, los administradores pueden revisar las suscripciones con recursos no compatibles y controlar la corrección de cada una por parte del propietario del recurso.

En este tutorial se proporcionan instrucciones sobre el uso de Cloud App Security para proteger las plataformas en la nube de Azure, AWS y GCP.

> [!div class="checklist"]
>
> * Detección de recursos, utilización y Shadow IT de varias nubes
> * Supervisión de las actividades y alertas para detectar comportamientos sospechosos en las cargas de trabajo
> * Evaluación y corrección de los errores de configuración y del estado de cumplimiento de la plataforma en la nube
> * Automatización de la protección y la aplicación de directivas para los recursos en la nube en tiempo real

## <a name="how-to-secure-your-multi-cloud-environment"></a>Procedimientos para proteger el entorno de varias nubes

Para evitar errores de configuración críticos de la plataforma en la nube, es importante que las organizaciones obtengan visibilidad en el nivel de inquilino de varias nubes en el estado de configuración de la nube y que puedan mejorar su posición de seguridad en función de las pruebas comparativas de seguridad y las recomendaciones de cumplimiento. Utilice el proceso siguiente para proteger el entorno de varias nubes de la organización.

### <a name="phase-1-discover-multi-cloud-resources-usage-and-shadow-it"></a>Fase 1: Detección de recursos, utilización y Shadow IT de varias nubes

**Identificación de la posición de seguridad**: para empezar, identifique la posición de seguridad en la nube de su organización mediante la ejecución de Cloud Discovery a fin de ver lo que sucede en la red y evaluar la utilización real de los recursos en las plataformas en la nube. Se puede lograr mediante la [configuración de Cloud Discovery](set-up-cloud-discovery.md) para supervisar y analizar el tráfico en Cloud App Security. El análisis de los registros de tráfico web con la detección de Shadow IT de Cloud App Security proporciona una visibilidad mejorada sobre la utilización de Shadow TI de los recursos en la nube, lo que identifica las actividades anómalas mediante el motor de detección de anomalías Machine Learning o con el uso de directivas personalizadas que defina lo siguiente:

* **Detección**: descubra la utilización de las plataformas en la nube que hospedan recursos de su organización. Por ejemplo, evalúe el volumen real de los datos que se han descargado de los recursos de almacenamiento e identifique el uso de recursos sospechosos que puede indicar intentos de filtración de datos. Del mismo modo, identifique las actividades de carga sospechosas que pueden indicar un intento de poner en peligro su entorno mediante la inserción de código malintencionado en un destino.
* **Investigar**: use la página **Recursos detectados** para ver el acceso a los datos entre recursos, incluidas las cuentas de almacenamiento, la infraestructura y las aplicaciones personalizadas hospedadas en Azure, AWS y GCP. Formule preguntas como las siguientes: ¿Ha habido un número sospechoso de transacciones en el acceso a un recurso específico?

    ![Visualización de recursos detectados](media/tutorial-cloud-platform-security-view-discovered-resources.png)

    Para investigar más a fondo, puede explorar en profundidad cada recurso a fin de ver los tipos de interacciones que se han producido, los usuarios que han accedido a ellos y, posteriormente, explorar en profundidad con el fin de investigar incluso más a los usuarios.

    ![Investigación de los recursos detectados](media/tutorial-cloud-platform-security-investigate-discovered-resources.png)

### <a name="phase-2-monitor-activities-and-alerts-to-detect-suspicious-behavior-across-workloads"></a>Fase 2: Supervisión de las actividades y alertas para detectar comportamientos sospechosos en las cargas de trabajo

Realice un seguimiento de las actividades sospechosas que pueden indicar una vulneración, como un cambio en el rol de IAM (Administración de identidad y acceso) o el cambio de configuración de CloudTrail. Por ejemplo, use nuestra [plantilla de directiva](policy-template-reference.md) predefinida de **cubos de AWS S3 de acceso público** para realizar el seguimiento de los cambios de configuración del cubo S3.

La supervisión de los registros de auditoría de cambios sospechosos es un buen lugar para aplicar herramientas de detección de anomalías, generar alertas sobre posibles vulneraciones mediante la identificación de varios intentos de inicio de sesión erróneos o varias actividades de máquina virtual eliminadas en combinación con un escenario de viaje imposible.

![Visualización de alertas](media/tutorial-cloud-platform-security-view-alerts.png)

Aplique la información que ha obtenido de las alertas para ajustar las detecciones de actividad del usuario a fin de identificar el auténtico peligro y reducir la fatiga de alertas resultante del tratamiento de elevados volúmenes de detecciones de falsos positivos. Considere la posibilidad de optimizar los parámetros de directiva siguientes:

* Configuración de los [intervalos de direcciones IP](tutorial-suspicious-activity.md#phase-1-configure-ip-address-ranges)
* Ajuste de las [directivas de detección de anomalías](tutorial-suspicious-activity.md#phase-2-tune-anomaly-detection-policies), como actividades administrativas inusuales, actividades inusuales de descarga de varios archivos, actividad de ransomware y actividades de inicio de sesión con errores en las plataformas en la nube
* Ajuste de las [directivas de detección de anomalías de Cloud Discovery](tutorial-suspicious-activity.md#phase-3-tune-cloud-discovery-anomaly-detection-policies) mediante el ajuste de la utilización de sensibilidad de alertas y supervisión
* Ajuste de las [directivas de detección basadas en reglas y directivas de actividad](tutorial-suspicious-activity.md#phase-4-tune-rule-based-detection-activity-policies), incluidos los cubos de AWS S3 de acceso público
* Configuración de las [alertas](tutorial-suspicious-activity.md#phase-5-configure-alerts)
* [Investigación y corrección](tutorial-suspicious-activity.md#phase-6-investigate-and-remediate)

### <a name="phase-3-assess-and-remediate-cloud-platform-misconfigurations-and-compliance-status"></a>Fase 3: Evaluación y corrección de los errores de configuración y del estado de cumplimiento de la plataforma en la nube

Evalúe el estado del cumplimiento de seguridad por inquilino, en todas las plataformas de nube pública, incluidas las suscripciones de Azure, las cuentas de AWS y los proyectos de GCP. Las evaluaciones permiten comunicar brechas de configuración y detalles de recomendación a los propietarios de recursos y la corrección de la unidad.

Cada plataforma en la nube proporciona una lista de recursos mal configurados según los procedimientos recomendados de cumplimiento normativo.

Los arquitectos de la nube o los analistas de cumplimiento pueden evaluar las brechas de configuración de cada entorno de nube y la corrección por parte de los propietarios de los recursos. Por ejemplo, las recomendaciones se pueden evaluar mediante lo siguiente:

* Suscripción para diferenciar entre entornos de producción y entornos que no son de suscripción.
* Gravedad para identificar recomendaciones de alta gravedad que suelen tener distintos Acuerdos de Nivel de Servicio y procesos relativos a las recomendaciones de baja gravedad.

En el caso de las recomendaciones de configuración de seguridad de Azure, se muestran las recomendaciones de todo el inquilino de Azure y de todas sus suscripciones basadas en los procedimientos recomendados de Azure Security Center. Al seleccionar una recomendación, se le redirigirá a la página de recomendaciones de Azure Security Center, donde podrá ver detalles adicionales acerca de la recomendación y usarla para impulsar la corrección por parte del propietario de la suscripción. Algunas recomendaciones tienen opciones de **Corrección rápida** para corregir la incidencia. A fin de obtener más información sobre las recomendaciones de seguridad de Azure, vea [Configuración de seguridad para Azure](security-config-azure.md).

![Visualización de recomendaciones de Azure](media/tutorial-cloud-platform-security-view-azure-recommendations.png)

En el caso de las recomendaciones de configuración de seguridad de AWS, se puede seleccionar una recomendación para explorar en profundidad en los detalles de los recursos afectados. Por ejemplo, la recomendación 2.9 de AWS CIS "Asegúrese de que el registro de flujos de VPC está habilitado en todas las VPC" muestra los recursos que no tienen el registro de VPC habilitado. Los detalles incluyen los nombres de la VPC, la cuenta en la que se hospeda el recurso y la región. Puede seleccionar el vínculo de AWS para ver la búsqueda pertinente y cambiar la configuración relacionada en AWS a fin de cumplir con la recomendación. A fin de obtener más información sobre la Configuración de seguridad para AWS, vea [Configuración de seguridad para AWS](security-config-aws.md).

![Visualización de las recomendaciones de AWS](media/tutorial-cloud-platform-security-view-aws-recommendations.png)

En el caso de las recomendaciones de configuración de seguridad de GCP, la selección de una recomendación revela información de recomendaciones detallada y pasos de corrección para ayudarle a comprender y evaluar mejor el impacto y el esfuerzo que supone corregir la incidencia. Después, puede seleccionar el vínculo de Centro de comandos de seguridad de GCP para corregir la búsqueda en la plataforma. A fin de obtener más información sobre las recomendaciones de GCP, vea [Configuración de seguridad para GCP](security-config-gcp.md).

![Visualización de las recomendaciones de GCP](media/tutorial-cloud-platform-security-view-gcp-recommendations.png)

### <a name="phase-4-automate-protection-and-policy-enforcement-for-cloud-resources-in-real-time"></a>Fase 4: Automatización de la protección y la aplicación de directivas para los recursos en la nube en tiempo real

Proteja los recursos de su organización frente a pérdidas de datos y robos en tiempo real mediante la aplicación de directivas de control de acceso y de sesión. Para obtener más información, vea [Protección de aplicaciones en tiempo real](tutorial-proxy.md).

* Evite la filtración de datos mediante el [bloqueo de descargas](session-policy-aad.md#block-download) a dispositivos no administrados o peligrosos y protéjase en una sesión de riesgo.
* Evite la [carga de archivos malintencionados](session-policy-aad.md#block-malware-on-upload) a las plataformas en la nube y bloquee el acceso de usuarios específicos basado en distintos factores de riesgo.

![Especificación de la acción de corrección de la directiva](media/tutorial-cloud-platform-security-remediation.png)

## <a name="see-also"></a>Consulte también

> [!div class="nextstepaction"]
> [Protección del entorno de Azure](protect-azure.md)

> [!div class="nextstepaction"]
> [Protección del entorno de AWS](protect-aws.md)

> [!div class="nextstepaction"]
> [Protección del entorno de GCP](protect-gcp.md)

[!INCLUDE [Open support ticket](includes/support.md)]
