---
title: Crear directivas en aplicaciones de Cloud Discovery en Cloud App Security | Microsoft Docs
description: En este tema se proporciona información sobre cómo trabajar con directivas de Cloud Discovery.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 4/22/2018
ms.topic: article
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 45446111-ed1a-4699-9df5-840cc6664a6b
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 983a4af689351fe9c71d1971f16b858a577a31ae
ms.sourcegitcommit: 45311f2cafef79483e40d971a4c61c7673834d96
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2018
---
*Se aplica a: Microsoft Cloud App Security*


# <a name="cloud-discovery-policies"></a>Directivas de Cloud Discovery
    
## <a name="creating-an-app-discovery-policy"></a>Crear una directiva de detección de aplicaciones  
Las directivas de detección permiten establecer alertas que avisan cuando se detectan nuevas aplicaciones en la organización.  
  
1.  En la consola, haga clic en **Control**, seguido de **Directivas**.  
  
2.  Haga clic en **Crear directiva** y seleccione **Directiva de detección de aplicaciones**.  
  
     ![Menú de directiva de detección de aplicaciones](./media/app-discovery-policy-menu.png "Menú de directiva de detección de aplicaciones")  
  
3.  Asigne un nombre y una descripción a la directiva. Si quiere, puede basarla en una plantilla. Para obtener más información sobre las plantillas de directiva, vea [Controlar aplicaciones en la nube con directivas](control-cloud-apps-with-policies.md).  
  
4.  Establezca la **gravedad** de la directiva.

5. Agregue filtros para definir qué aplicaciones detectadas van a activar esta directiva.  
  
6.  Puede establecer el umbral de sensibilidad de la directiva. Después de habilitar la opción **Desencadenar una coincidencia de directiva si todo lo siguiente sucede en el mismo día**, puede establecer un valor mínimo para **Número de usuarios**, **Número de direcciones IP**, **Tráfico diario**, **Datos descargados**, **Datos cargados** y **Número de transacciones** que la aplicación debe cumplir para que coincida con la directiva.  
  
7.  Establezca un **Límite de alertas diarias** y seleccione si la alerta se enviará como un correo, como un mensaje de texto o como ambos, y proporcione detalles según sea necesario. Puede hacer clic en Guardar la configuración de la alerta como predeterminada para permitir que las directivas futuras guarden esta configuración de alertas (número de teléfono y direcciones de correo incluidos) como valores predeterminados.  
  
8. Seleccione las posibles acciones de **Gobierno** que se aplicarán cuando una aplicación coincida con esta directiva. Es posible etiquetar automáticamente las directivas como **autorizadas** o **no autorizadas** 

8.  Haga clic en **Crear**.  
  
Si, por ejemplo, está interesado en detectar las aplicaciones de hospedaje de riesgo que hay en su entorno en la nube, establezca la directiva así:  
  
Establezca los filtros de directiva para detectar los servicios que se encuentren en la categoría **Servicios de hospedaje** y que tengan una puntuación baja, lo que indica que entrañan riesgos.   
   
En la parte inferior, establezca los umbrales que deben activar una alerta para una determinada aplicación detectada: solo si hay más de cien usuarios en el entorno que han usado la aplicación y solo si han descargado una determinada cantidad de datos desde el servicio.   
También puede establecer el límite de alertas diarias que quiere recibir.  
  
![Ejemplo de directiva de detección de aplicaciones](./media/app-discovery-policy-example.png "Ejemplo de directiva de detección de aplicaciones")  
  
## <a name="cloud-discovery-anomaly-detection"></a>Detección de anomalías de Cloud Discovery  
Cloud App Security busca en todos los registros de Cloud Discovery para encontrar anomalías. Por ejemplo, cuando un usuario que nunca ha usado Dropbox de repente carga 600 GB o cuando hay muchas más transacciones de lo habitual en una aplicación determinada. La directiva de detección de anomalías está habilitada de forma predeterminada, por lo que no es necesario configurar una nueva directiva para que funcione. Con todo, puede ajustar aún más los tipos de anomalías de los que quiere que se le alerte en la directiva predeterminada.  
  
1.  En la consola, haga clic en **Control**, seguido de **Directivas**.  
  
2.  Haga clic en **Crear directiva** y seleccione la directiva **Detección de anomalías de Cloud Discovery**.  
  
     ![Menú de directiva de detección de anomalías de Cloud Discovery](./media/cloud-discovery-anomaly-detection-policy-menu.png "Menú de directiva de detección de anomalías de Cloud Discovery")  
  
3.  Asigne un nombre y una descripción a la directiva. Si quiere, puede basarla en una plantilla. Para obtener más información sobre las plantillas de directiva, vea [Controlar aplicaciones en la nube con directivas](control-cloud-apps-with-policies.md).  
  
4.  Haga clic en **Agregar filtros** para definir qué aplicaciones detectadas van a activar esta directiva.  
  
     Los filtros se eligen en el lado izquierdo de la página de la ventana emergente de filtro. Se puede filtrar por nombre de servicio, dominio, factor de riesgo, puntuación de riesgo y categoría. En el lado derecho de la página se muestran los resultados de los filtros seleccionados del catálogo de servicios actual. Tras elegir los filtros, guarde y confirme que las etiquetas correspondientes aparecen en el cuadro de filtros.  
  
5.  En **Aplicar a**, decida si esto se aplica a **Todas las vistas de datos** o a **Vistas específicas de datos**, y si se aplica a **Usuarios**, a **Direcciones IP** o a ambos.  
  
6.  Seleccione las fechas en las que se ha producido la actividad anómala para activar la alerta en **Generar alertas solo para las actividades sospechosas que se produzcan después de la fecha**.  
  
7.  En **Alertas**, puede establecer la sensibilidad de la detección de anomalías de baja a alta para configurar la frecuencia de las alertas que quiere recibir.  
Establezca un **Límite de alertas diarias** y seleccione si la alerta se enviará como un correo, como un mensaje de texto o como ambos, y proporcione detalles según sea necesario. Puede hacer clic en Guardar la configuración de la alerta como predeterminada para permitir que las directivas futuras guarden esta configuración de alertas (número de teléfono y direcciones de correo incluidos) como valores predeterminados. También puede hacer clic en **Usar los valores predeterminados de la organización** para establecer estos valores según los valores predeterminados de su organización.  
  
9. Haga clic en **Crear**.  
  
![Nueva directiva de detección de anomalías](./media/new-discovery-anomaly-policy.png "Nueva directiva de detección de anomalías")  
  
## <a name="see-also"></a>Consulte también  
[Directivas de actividad de usuario](user-activity-policies.md)   

[Los clientes Premier también pueden elegir Cloud App Security directamente desde el Portal Premier.](https://premier.microsoft.com/)  
  
  