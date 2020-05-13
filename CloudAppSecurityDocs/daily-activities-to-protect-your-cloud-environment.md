---
title: Trabajo con el panel de Cloud App Security
description: En este artículo se proporcionan los conceptos básicos para usar el panel de Cloud App Security.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 05/06/2020
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 367778c25f0a56dd0db8f6457b884b02d382da6c
ms.sourcegitcommit: e0c2a8fbdce9cc0fd0d6b85c92e112fd306ad950
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/12/2020
ms.locfileid: "83203012"
---
# <a name="working-with-the-dashboard"></a>Trabajo con el panel

*Se aplica a: Microsoft Cloud App Security*

En este tema se describen las tareas diarias que debe realizar con Cloud App Security.  Después de tener Microsoft Cloud App Security configurado y ejecutándose, tendrá que:

- Configurar flujos de datos
- Autorizar las aplicaciones que quiera permitir que usen los usuarios
- Configurar directivas para supervisar el entorno de nube.

A continuación, puede utilizar Cloud App Security para controlar y proteger la nube, y para administrar los riesgos.

## <a name="check-the-dashboard"></a>Comprobar el panel

![Panel de Cloud App Security](media/dashboard.png "dashboard")

En el panel de Cloud App Security se proporciona una visión general de las actividades y características, entre ellas:

- Alertas abiertas
- Infracciones de la actividad
- Infracciones del contenido
- Un mapa de actividad que traza el origen de la actividad del usuario
- Tendencias de uso de aplicaciones conectadas en su entorno de la nube
- Usuarios principales según la detección de amenazas

Es recomendable que eche un vistazo al panel a diario para ver qué nuevas alertas se han activado. Es un buen lugar para vigilar el estado de su entorno de nube. Con el panel puede hacerse una idea de lo que sucede.

## <a name="gradual-deployment-of-our-enhanced-dashboard"></a>Implementación gradual de nuestro panel mejorado

Como parte de las mejoras continuas en el diseño del portal, el panel de Cloud App Security se ha mejorado en función de sus comentarios. El panel ofrece una experiencia de usuario mejorada con contenido y datos actualizados.

La información que se presenta en el panel es una introducción a toda la información más importante sobre su organización. Cada tarjeta de información proporciona vínculos a una investigación más profunda de la información presentada. También puede elegir ver la información del panel para una aplicación específica mediante el filtro proporcionado.

![Panel de Cloud App Security](media/dashboard-enhanced.png)

### <a name="what-can-you-expect-to-see-in-the-dashboard"></a>¿Qué puede esperar ver en el panel?

- **Alertas abiertas**  
Muestra el número de alertas abiertas, un gráfico de la distribución del estado de la alerta y las alertas recientes

- **Aplicaciones detectadas**  
Muestra el número de aplicaciones detectadas, un gráfico de la distribución del riesgo de la aplicación y las categorías principales de aplicaciones por tráfico.
- **Principales usuarios para investigar**  
Muestra el número de usuarios que se van a investigar y los usuarios con la prioridad de investigación más alta.
- **Control de aplicaciones de acceso condicional**  
Muestra el número de aplicaciones protegidas por Control de aplicaciones de acceso condicional, así como el número de sesiones y acciones protegidas en los últimos 30 días.
- **Estado de los conectores de aplicaciones**  
Muestra el número de instancias de la aplicación conectada a la API y su estado.
- **Archivos infectados con malware**  
Muestra el número de archivos infectados con malware.
- **Aplicaciones con privilegios de OAuth de Office 365**  
Muestra el número de aplicaciones de OAuth que rara vez se han concedido permisos con privilegios elevados.
- **Configuración de seguridad de Azure**  
Muestra el número y la gravedad de las recomendaciones de configuración de seguridad de Azure.
- **Configuración de seguridad de AWS**  
Muestra el número y la gravedad de las recomendaciones de configuración de seguridad de AWS.
- **Alertas DLP**  
Muestra un gráfico de alertas DLP en los últimos 30 días.
<!-- - **Activity map**  
Shows the global spread of activities performed by users over the last 30 days. -->

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Investigar alertas](investigate.md)

[!INCLUDE [Open support ticket](includes/support.md)]
