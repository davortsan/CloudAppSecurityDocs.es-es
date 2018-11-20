---
title: Crear directivas en aplicaciones de Cloud Discovery en Cloud App Security | Microsoft Docs
description: En este tema se proporciona información sobre cómo trabajar con directivas de Cloud Discovery.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 11/13/2018
ms.topic: conceptual
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 45446111-ed1a-4699-9df5-840cc6664a6b
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 01b08ae0246dbae89a71794bca170d757725c3c8
ms.sourcegitcommit: 77850c6777504c2478611cb71a387e7fcc5f2551
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/13/2018
ms.locfileid: "51597211"
---
# <a name="cloud-discovery-policies"></a>Directivas de Cloud Discovery

*Se aplica a: Microsoft Cloud App Security*

Puede crear directivas de detección de aplicaciones para que se le envíen alertas cuando se detecten nuevas aplicaciones. Cloud App Security también busca en todos los registros de Cloud Discovery para comprobar si hay anomalías. 

## <a name="creating-an-app-discovery-policy"></a>Crear una directiva de detección de aplicaciones  
Las directivas de detección permiten establecer alertas que avisan cuando se detectan nuevas aplicaciones en la organización.  
  
1. En la consola, haga clic en **Control**, seguido de **Directivas**.  
  
2. Haga clic en **Crear directiva** y seleccione **Directiva de detección de aplicaciones**.  
  
     ![Menú de directiva de detección de aplicaciones](./media/app-discovery-policy-menu.png "Menú de directiva de detección de aplicaciones")  
  
3. Proporcione un nombre y una descripción para la directiva. Si quiere, puede basarse en una plantilla. Para obtener más información sobre las plantillas de directiva, vea [Controlar las aplicaciones en la nube con directivas](control-cloud-apps-with-policies.md).  
  
4. Establezca la **gravedad** de la directiva.

5. Agregue filtros para definir qué aplicaciones detectadas van a activar esta directiva.  
  
6. Puede establecer el umbral de sensibilidad de la directiva. Habilite la opción **Desencadenar una coincidencia de directiva si todo lo siguiente sucede en el mismo día**. Puede establecer los criterios que la aplicación debe superar diariamente para que coincida con la directiva. Seleccione uno de estos criterios: 
     - Tráfico diario
     - Datos descargados
     - Número de direcciones IP
     - Número de transacciones
     - Número de usuarios
     - Datos cargados

  
7. Establezca un **límite de alertas diarias** en **Alertas**. Seleccione si quiere que la alerta se envíe como mensaje de correo electrónico, de texto o ambos. A continuación, proporcione números de teléfono y direcciones de correo electrónico según sea necesario.
     - Al hacer clic en **Guardar configuración de alertas como valor predeterminado para la organización**, permitirá que se use la configuración para futuras directivas.
     - Si tiene una configuración predeterminada, puede seleccionar **Usar la configuración predeterminada de la organización**.
  
8. Seleccione las acciones de **Gobierno** que se aplicarán cuando una aplicación coincida con esta directiva. Es posible etiquetar las directivas como **autorizadas** o **no autorizadas**, o bien una etiqueta personalizada. 

9. Haga clic en **Crear**.  
  
Si, por ejemplo, le interesa detectar las aplicaciones de hospedaje de riesgo que hay en su entorno en la nube, establezca la directiva de la siguiente forma:  
  
Establezca los filtros de directiva para detectar los servicios que se encuentren en la categoría **Servicios de hospedaje** y que tengan una puntuación de riesgo de 1, lo que indica un riesgo elevado.

 Establezca los umbrales que deben desencadenar una alerta para una determinada aplicación detectada en la parte inferior. Por ejemplo, defina que se envíe una alerta solo si más de 100 usuarios del entorno han usado la aplicación y si han descargado una cantidad determinada de datos del servicio.
También puede establecer el límite de alertas diarias que quiere recibir.  
  
![Ejemplo de directiva de detección de aplicaciones](./media/app-discovery-policy-example.png "Ejemplo de directiva de detección de aplicaciones")  
  
## <a name="cloud-discovery-anomaly-detection"></a>Detección de anomalías de Cloud Discovery

Cloud App Security busca en todos los registros de Cloud Discovery para encontrar anomalías. Por ejemplo, cuando un usuario que nunca ha usado Dropbox de repente carga 600 GB o cuando hay muchas más transacciones de lo habitual en una aplicación determinada. La directiva de detección de anomalías está habilitada de forma predeterminada. No es necesario configurar ninguna directiva nueva para que funcione. Pero puede ajustar los tipos de anomalías sobre los que quiere que se le envíen alertas en la directiva predeterminada.  
  
1. En la consola, haga clic en **Control**, seguido de **Directivas**.  
  
2. Haga clic en **Crear directiva** y seleccione la directiva **Detección de anomalías de Cloud Discovery**.  
  
     ![Menú de directiva de detección de anomalías de Cloud Discovery](./media/cloud-discovery-anomaly-detection-policy-menu.png "Menú de directiva de detección de anomalías de Cloud Discovery")  
  
3. Proporcione un nombre y una descripción para la directiva. Si quiere, puede basarse en una plantilla. Para obtener más información sobre las plantillas de directiva, vea [Controlar aplicaciones en la nube con directivas](control-cloud-apps-with-policies.md).  
  
4. Haga clic en **Agregar filtros** para definir qué aplicaciones detectadas van a activar esta directiva.  
  
     Los filtros se eligen en las listas desplegables. Para agregar filtros, haga clic en el botón del signo más. Para quitar un filtro, haga clic en la "X". 
  
5. En **Aplicar a**, elija si esta directiva se aplica a **Todos los informes continuos** o a **Informes continuos específicos**. Seleccione si la directiva se aplica a **Usuarios**, **Direcciones IP** o a ambos.  
  
6. Seleccione las fechas en las que se ha producido la actividad anómala para activar la alerta en **Generar alertas solo para las actividades sospechosas que se produzcan después de la fecha**.  
  
7. Establezca un **límite de alertas diarias** en **Alertas**. Seleccione si quiere que la alerta se envíe como mensaje de correo electrónico, de texto o ambos. A continuación, proporcione números de teléfono y direcciones de correo electrónico según sea necesario.
     - Al hacer clic en **Guardar configuración de alertas como valor predeterminado para la organización**, permitirá que se use la configuración para futuras directivas.
     - Si tiene una configuración predeterminada, puede seleccionar **Usar la configuración predeterminada de la organización**.
  
8. Haga clic en **Crear**.  
  
![Nueva directiva de detección de anomalías](./media/new-discovery-anomaly-policy.png "Nueva directiva de detección de anomalías")  
  
## <a name="next-steps"></a>Pasos siguientes 
[Directivas de actividad de usuario](user-activity-policies.md)   

[Los clientes Premier también pueden elegir Cloud App Security directamente desde el Portal Premier.](https://premier.microsoft.com/)  
  
  