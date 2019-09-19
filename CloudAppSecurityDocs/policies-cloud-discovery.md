---
title: Directivas de Cloud Discovery Cloud App Security | Microsoft Docs
description: En este artículo se describen los pasos para configurar muchas directivas de Cloud Discovery en Cloud App Security.
author: shsagir
ms.author: shsagir
ms.date: 06/13/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: cloud-app-security
ms.assetid: 570da960-771d-484f-932d-b086f2ec2978
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: ffcb2b67c03cf93843faf8255af86f4cb1c80a53
ms.sourcegitcommit: 8a49c166424fea83853b0a6895212367526abe78
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2019
ms.locfileid: "71085086"
---
# <a name="cloud-discovery-policies"></a>Directivas de Cloud Discovery

*Se aplica a: Microsoft Cloud App Security*

En este artículo se proporciona información general sobre cómo empezar a usar Cloud App Security para obtener visibilidad en la organización en la sombra con Cloud Discovery.

Cloud App Security permite detectar y analizar las aplicaciones en la nube que se usan en el entorno de la organización. En el panel de Cloud Discovery se muestran todas las aplicaciones en la nube que se ejecutan en el entorno y se clasifican por función y preparación para la empresa. Para cada aplicación, detecte los usuarios asociados, las direcciones IP, las máquinas, las transacciones y realiza la evaluación de riesgos sin necesidad de instalar un agente en los dispositivos de punto de conexión.

## Detección de un nuevo uso de aplicaciones grandes o de gran volumen<a name= "detect-volume"></a>

Detecte las nuevas aplicaciones que se usan con mucha capacidad, en cuanto al número de usuarios o la cantidad de tráfico de su organización.

### <a name="prerequisites"></a>Requisitos previos

Configure la carga de registros automática para informes de Cloud Discovery continuos, como se describe en [configurar la carga de registros automática para informes continuos](configure-automatic-log-upload-for-continuous-reports.md).

### <a name="steps"></a>Pasos

1.  En la página **directivas** , cree una nueva **Directiva de detección de aplicaciones** .

2.  En el campo **plantilla de directiva** , seleccione **nueva aplicación de gran volumen** o **nueva aplicación popular** y aplique la plantilla.

3.  Personalice los filtros de directiva para satisfacer los requisitos de su organización.

4.  Configure las acciones que deben llevarse a cabo cuando se desencadene una alerta.

> [!NOTE]
>  Una alerta se genera una vez para cada nueva aplicación que no se detectó en los últimos 90 días.

## <a name="detect-new-risky-or-non-compliant-app-use"></a>Detección de un nuevo uso de aplicaciones arriesgadas o no conformes

Detecte una posible exposición de su organización en aplicaciones en la nube que no cumplan los estándares de seguridad.

### <a name="prerequisites"></a>Requisitos previos

Configure la carga de registros automática para informes de Cloud Discovery continuos, como se describe en [configurar la carga de registros automática para informes continuos](configure-automatic-log-upload-for-continuous-reports.md).

### <a name="steps"></a>Pasos

1.  En la página **directivas** , cree una nueva **Directiva de detección de aplicaciones.**

2.  En el campo **plantilla de directiva** , seleccione la nueva plantilla aplicación de **riesgo** y aplique la plantilla.

3.  En **aplicación que coincide con todos los elementos siguientes** , establezca el control deslizante de [puntuación de riesgo](risk-score.md) y el factor de riesgo de cumplimiento para personalizar es el nivel de riesgo que desea que desencadene una alerta y establezca los otros filtros de directiva para satisfacer los requisitos de seguridad de su organización.

    1.  Opcional: Para obtener detecciones más significativas, personalice la cantidad de tráfico que desencadenará una alerta.

        1.  Active la casilla **desencadenar una coincidencia de Directiva si se producen todas las acciones siguientes en el mismo día** .

        2.  Seleccione el **tráfico diario** superior a 2000 GB (u otros).

4.  Configure las acciones de gobierno que se llevarán a cabo cuando se desencadene una alerta. En **gobierno**, seleccione la **aplicación de etiqueta como no autorizada.**<br>El acceso a la aplicación se bloqueará automáticamente cuando se cumpla la Directiva.

5.  Opcional: Aproveche las [integraciones nativas de Cloud App Security](set-up-cloud-discovery.md) con puertas de enlace web seguras para bloquear el acceso a las aplicaciones.

## <a name="detect-use-of-unsanctioned-business-apps"></a>Detección del uso de aplicaciones empresariales no autorizadas

Puede detectar cuándo los empleados siguen usando aplicaciones no autorizadas como reemplazo de aplicaciones aprobadas para el negocio.

### <a name="prerequisites"></a>Requisitos previos

-   Configure la carga de registros automática para informes de Cloud Discovery continuos, como se describe en [configurar la carga de registros automática para informes continuos](configure-automatic-log-upload-for-continuous-reports.md).

### <a name="steps"></a>Pasos

1.  En el catálogo de aplicaciones en la nube, busque las aplicaciones preparadas para la empresa y márquelos con una [etiqueta de aplicación personalizada](discovered-app-queries.md#creating-and-managing-custom-app-tags).

2.  Siga los pasos que se describen en [detección de nuevas aplicaciones de gran volumen o uso ancho](#detect-volume).

3.  Agregue un filtro de etiqueta de la **aplicación** y elija las etiquetas de la aplicación que creó para las aplicaciones para la empresa.

4.  Configure las acciones de gobierno que se llevarán a cabo cuando se desencadene una alerta. En gobierno, seleccione la **aplicación de etiqueta como no autorizada**.<br>El acceso a la aplicación se bloqueará automáticamente cuando se cumpla la Directiva.

5.  Opcional: Aproveche las [integraciones nativas de Cloud App Security](set-up-cloud-discovery.md) con puertas de enlace web seguras para bloquear el acceso a las aplicaciones.

## <a name="detect-unusual-usage-patterns-on-your-network"></a>Detección de patrones de uso inusuales en la red

Detección de patrones de uso de tráfico anómalos (cargas y descargas) en las aplicaciones en la nube, que se originan a partir de usuarios o direcciones IP dentro de la red de su organización.

### <a name="prerequisites"></a>Requisitos previos

Configure la carga de registros automática para informes de Cloud Discovery continuos, como se describe en [configurar la carga de registros automática para informes continuos](configure-automatic-log-upload-for-continuous-reports.md).

### <a name="steps"></a>Pasos

1.  En la página **directivas** , cree una nueva **Directiva de detección de anomalías Cloud Discovery**.

2.  En el campo **plantilla de directiva** , seleccione **comportamiento anómalo en usuarios detectados** o **comportamiento anómalo en direcciones IP detectadas**.

3.  Personalice los filtros para satisfacer los requisitos de su organización.

4. Si quiere que se le avise solo cuando haya anomalías que impliquen aplicaciones de riesgo, use los filtros de **puntuación de riesgo** y establezca el intervalo en el que las aplicaciones se consideran arriesgadas.

4.  Use el control deslizante para **seleccionar la sensibilidad de la detección de anomalías**.

> [!NOTE]
>  Una vez establecida la carga continua de registros, el motor de detección de anomalías tarda unos días hasta que se establece una línea de base (período de aprendizaje) para el comportamiento esperado de la organización. Una vez establecida una línea base, comienza a recibir alertas basadas en discrepancias del comportamiento esperado del tráfico en aplicaciones en la nube realizadas por usuarios o desde direcciones IP.

## <a name="detect-data-exfiltration-to-unsanctioned-storage-apps"></a>Detección de la filtración de datos a aplicaciones de almacenamiento no autorizadas

Detección de posibles exfiltración de datos por parte de un usuario en una aplicación de almacenamiento en la nube no autorizada.

### <a name="prerequisites"></a>Requisitos previos

Configure la carga de registros automática para informes de Cloud Discovery continuos, como se describe en [configurar la carga de registros automática para informes continuos](configure-automatic-log-upload-for-continuous-reports.md).

### <a name="steps"></a>Pasos

1.  En la página **directivas** , edite la exfiltración de datos de directiva integrada **en aplicaciones no autorizadas**.

2.  Seleccione la **categoría aplicación** de filtro es igual a **almacenamiento en la nube**.

3.  Active la casilla para **crear una alerta para cada evento coincidente con la gravedad de la Directiva**.

4.  Configure las acciones que deben llevarse a cabo cuando se desencadene una alerta.

## <a name="detect-risky-oauth-apps"></a>Detección de aplicaciones de OAuth peligrosas

Obtenga visibilidad y control sobre las [aplicaciones de OAuth](investigate-risky-oauth.md) que se instalan dentro de aplicaciones como G Suite, Office 365 y Salesforce. Las aplicaciones de OAuth que solicitan permisos altos y tienen poco uso de la comunidad se pueden considerar arriesgadas.

### <a name="prerequisites"></a>Requisitos previos

Debe tener la aplicación G Suite, Office 365 o Salesforce conectada mediante los [conectores de aplicaciones](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md).

### <a name="steps"></a>Pasos

1.  En la página **directivas** , cree una nueva **Directiva de aplicación de OAuth**.

2.  Seleccione la **aplicación** de filtro y establezca la aplicación que debe cubrir la Directiva, G Suite, Office 365 o Salesforce.

3.  Seleccione el filtro de **nivel de permiso** es igual a **alto** (disponible para G Suite y O365).

4.  Agregar el uso de la **comunidad** de filtros es igual a **inusual**.

4.  Configure las acciones que deben llevarse a cabo cuando se desencadene una alerta. Por ejemplo, para Office 365, Active **revocar aplicación** para OAuth aplicaciones detectadas por la Directiva.

> [!NOTE]
>  Compatible con tiendas de aplicaciones de G Suite, Office 365 y Salesforce.

## <a name="next-steps"></a>Pasos siguientes 

[Actividades diarias para proteger el entorno de nube](daily-activities-to-protect-your-cloud-environment.md)   

[Los clientes Premier también pueden crear una solicitud de soporte técnico directamente en el portal Premier.](https://premier.microsoft.com/)  
  
  
