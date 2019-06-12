---
title: Directivas de cloud Discovery - Cloud App Security | Microsoft Docs
description: En este tema se describe los pasos para configurar muchas de las directivas de Cloud Discovery en Cloud App Security.
author: rkarlin
ms.author: rkarlin
ms.date: 06/13/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: cloud-app-security
ms.assetid: 570da960-771d-484f-932d-b086f2ec2978
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 4c9d90852f1dbdf18da285f63abbb46e91595655
ms.sourcegitcommit: 9f671d5dd5e5da023d598425442d8736546ca183
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/11/2019
ms.locfileid: "66837763"
---
# <a name="cloud-discovery-policies"></a>Directivas de Cloud Discovery

*Se aplica a: Microsoft Cloud App Security*

Este artículo proporciona información general sobre cómo empezar a usar Cloud App Security para proporcionar visibilidad de su organización en Shadow IT con Cloud Discovery.

Cloud App Security permite detectar y analizar las aplicaciones en la nube que están en uso en el entorno de su organización. El panel de Cloud Discovery muestra todas las aplicaciones en la nube que se ejecutan en el entorno y los clasifica por preparación de la función y enterprise. Para cada aplicación, detectar los usuarios asociados, direcciones IP, máquinas, transacciones y evaluación de riesgos dirige sin necesidad de instalar a un agente en los dispositivos de punto de conexión.

## Detectar el uso de gran volumen o de amplia aplicación nueva <a name= "detect-volume"></a>

Detectar nuevas aplicaciones muy usadas, en términos de número de usuarios o la cantidad de tráfico de su organización.

### <a name="prerequisites"></a>Requisitos previos

Informa de configurar la carga de registros automática para la detección continua de la nube, como se describe en [configurar la carga de registros automática para informes continuos](configure-automatic-log-upload-for-continuous-reports.md).

### <a name="steps"></a>Pasos

1.  En el **directivas** página, cree un nuevo **directiva de detección de aplicaciones**

2.  En el **plantilla de directiva** campos, seleccione **nueva aplicación de gran volumen** o **nueva aplicación popular** y aplicar la plantilla.

3.  Personalizar los filtros de directiva para satisfacer los requisitos de su organización.

4.  Configurar las acciones que se deben realizar cuando se desencadene una alerta.

> [!NOTE]
>  Una vez, se genera una alerta para cada nueva aplicación que no se detectó en los últimos 90 días.

## <a name="detect-new-risky-or-non-compliant-app-use"></a>Detectar el uso nuevas aplicaciones de riesgo o no compatible

Detectar la posible exposición de su organización en las aplicaciones de nube que no cumplen los estándares de seguridad.

### <a name="prerequisites"></a>Requisitos previos

Informa de configurar la carga de registros automática para la detección continua de la nube, como se describe en [configurar la carga de registros automática para informes continuos](configure-automatic-log-upload-for-continuous-reports.md).

### <a name="steps"></a>Pasos

1.  En el **directivas** página, cree un nuevo **directiva de detección de aplicaciones.**

2.  En el **plantilla de directiva** campos, seleccione el **nueva aplicación de riesgo** plantilla y aplicar la plantilla.

3.  En **App que coinciden con todo lo siguiente** establecer el [puntuación de riesgo](risk-score.md) control deslizante y y el factor de riesgo de cumplimiento para personalizar el nivel de riesgo que desee desencadenar una alerta y establezca los otros filtros de directiva para satisfacer requisitos de seguridad de su organización.

    1.  Opcional: Para obtener las detecciones más significativas, personalizar la cantidad de tráfico que desencadenará una alerta.

        1.  Compruebe el **desencadenar una coincidencia de directiva si todo lo siguiente que se produce en el mismo día** casilla de verificación.

        2.  Seleccione **tráfico diario** mayor que 2000 GB (u otros).

4.  Configurar acciones de gobierno que se realizará cuando se desencadena una alerta. En **gobierno**, seleccione **etiquetar aplicación como no autorizada.**<br>Acceso a la aplicación se bloqueará automáticamente cuando coincida la directiva.

5.  Opcional: Aproveche [integraciones nativas de Cloud App Security](set-up-cloud-discovery.md) con Secure Web las puertas de enlace para bloquear el acceso a la aplicación.

## <a name="detect-use-of-unsanctioned-business-apps"></a>Detectar el uso de aplicaciones de negocio no autorizadas

Puede detectar cuando los empleados seguirán usando las aplicaciones no autorizadas como un reemplazo para las aplicaciones aprobadas de listo para el negocio.

### <a name="prerequisites"></a>Requisitos previos

-   Informa de configurar la carga de registros automática para la detección continua de la nube, como se describe en [configurar la carga de registros automática para informes continuos](configure-automatic-log-upload-for-continuous-reports.md).

### <a name="steps"></a>Pasos

1.  En el catálogo de aplicaciones en la nube, busque las aplicaciones listo para el negocio y marcarlos con un [etiqueta de aplicación personalizada](discovered-app-queries.md#creating-and-managing-custom-app-tags).

2.  Siga los pasos de [detectar nuevo volumen alto o el uso de amplia aplicación](#detect-volume).

3.  Agregar un **etiqueta de la aplicación** filtrar y elija las etiquetas de aplicación que creó para sus aplicaciones listo para el negocio.

4.  Configurar acciones de gobierno que se realizará cuando se desencadena una alerta. En el gobierno, seleccione **etiquetar aplicación como no autorizada**.<br>Acceso a la aplicación se bloqueará automáticamente cuando coincida la directiva.

5.  Opcional: Aproveche [integraciones nativas de Cloud App Security](set-up-cloud-discovery.md) con Secure Web las puertas de enlace para bloquear el acceso a la aplicación.

## <a name="detect-unusual-usage-patterns-on-your-network"></a>Detectar patrones de uso inusuales en la red

Detectar patrones de uso de tráfico anómalo (carga o descarga) en sus aplicaciones en la nube, que se originan en los usuarios o direcciones IP dentro de la red de su organización.

### <a name="prerequisites"></a>Requisitos previos

Informa de configurar la carga de registros automática para la detección continua de la nube, como se describe en [configurar la carga de registros automática para informes continuos](configure-automatic-log-upload-for-continuous-reports.md).

### <a name="steps"></a>Pasos

1.  En el **directivas** página, cree un nuevo **directiva de detección de anomalías de Cloud Discovery**.

2.  En el **plantilla de directiva** campos, seleccione **comportamiento anómalo en usuarios detectados** o **comportamiento anómalo en direcciones IP detectadas**.

3.  Personalizar los filtros para cumplir los requisitos de su organización.

4. Si desea recibir alertas cuando no haya anomalías que implican las aplicaciones de riesgo, use el **puntuación de riesgo** filtra y establezca el intervalo en el que las aplicaciones se consideran peligrosas.

4.  Use el control deslizante a **seleccionar la sensibilidad de la detección de anomalías**.

> [!NOTE]
>  Una vez establecida la carga de registros continua, el motor de detección de anomalías tarda unos días hasta una línea base (período de aprendizaje), se establece para el comportamiento esperado de la organización. Una vez establecida una línea base, comenzar a recibir alertas basadas en las discrepancias desde el comportamiento de tráfico esperado entre aplicaciones en la nube realizadas por usuarios o direcciones IP.

## <a name="detect-data-exfiltration-to-unsanctioned-storage-apps"></a>Detectar la exfiltración de datos para aplicaciones de almacenamiento no autorizadas

Detectar posibles exfiltración de datos de un usuario a una aplicación de almacenamiento de nube no sancionadas.

### <a name="prerequisites"></a>Requisitos previos

Informa de configurar la carga de registros automática para la detección continua de la nube, como se describe en [configurar la carga de registros automática para informes continuos](configure-automatic-log-upload-for-continuous-reports.md).

### <a name="steps"></a>Pasos

1.  En el **directivas** página, edite la directiva integrada **exfiltración de datos para las aplicaciones no autorizadas**.

2.  Seleccione el filtro **la categoría de aplicación** es igual a **almacenamiento en nube**.

3.  Seleccione la casilla de verificación **crear una alerta para cada evento que coincida con la gravedad de directiva**.

4.  Configurar las acciones que se deben realizar cuando se desencadene una alerta.

## <a name="detect-risky-oauth-apps"></a>Detectar las aplicaciones de riesgo de OAuth

Obtenga visibilidad y control sobre [aplicaciones OAuth](investigate-risky-oauth.md) que se instalan dentro de aplicaciones como Salesforce, Office 365 y G Suite. Las aplicaciones de OAuth que solicitan permisos alta y tienen poco frecuente Comunidad use podrían considerarse arriesgadas.

### <a name="prerequisites"></a>Requisitos previos

Informa de configurar la carga de registros automática para la detección continua de la nube, como se describe en [configurar la carga de registros automática para informes continuos](configure-automatic-log-upload-for-continuous-reports.md).

### <a name="steps"></a>Pasos

1.  En el **directivas** página, cree un nuevo **directiva de aplicación de OAuth**.

2.  Seleccione el filtro **aplicación** y establezca la aplicación debería cubrir la directiva, G Suite, Office 365 o Salesforce.

3.  Seleccione **nivel de permiso** filtrar equals **alta** (disponible para G Suite y Office 365).

4.  Agregue el filtro **uso de la Comunidad** es igual a **raras**.

4.  Configurar las acciones que se deben realizar cuando se desencadene una alerta. Por ejemplo, para Office 365, consulte **revocar aplicación** para aplicaciones de OAuth detectadas por la directiva.

> [!NOTE]
>  Se admite para las tiendas de aplicaciones de Office 365, Salesforce y G Suite.

## <a name="next-steps"></a>Pasos siguientes 

[Actividades diarias para proteger el entorno de nube](daily-activities-to-protect-your-cloud-environment.md)   

[Los clientes Premier también pueden crear una solicitud de soporte técnico directamente en el portal Premier.](https://premier.microsoft.com/)  
  
  
