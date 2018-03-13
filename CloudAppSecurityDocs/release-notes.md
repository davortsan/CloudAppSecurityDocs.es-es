---
title: Novedades de Cloud App Security | Microsoft Docs
description: "Este tema se actualiza con frecuencia para informarle de las novedades de la versión más reciente de Cloud App Security."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 3/7/2018
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: d418ef3d-76ee-45d5-b5ae-21346e5239a3
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 08a798bb20830afcbdb498c2ac72787873f72fab
ms.sourcegitcommit: 9de7ed2224aeed049fc2a87e52307988f8837eeb
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/08/2018
---
# <a name="whats-new-with-microsoft-cloud-app-security"></a>Novedades de Microsoft Cloud App Security


## <a name="cloud-app-security-release-118"></a>Cloud App Security versión 118
Fecha de publicación: 4 de marzo de 2018

- Ahora puede aprovechar las funcionalidades de detección y supervisión de Shadow IT de Microsoft Cloud App Security en sus propias aplicaciones personalizadas exclusivas. La nueva posibilidad de agregar aplicaciones personalizadas a Cloud Discovery permite supervisar el uso de la aplicación y recibir alertas sobre cambios en el patrón de uso. Para obtener más información, vea [Protecting your custom apps](cloud-discovery-custom-apps.md) (Protección de las aplicaciones personalizadas). Esta característica se está implantando gradualmente.

- Las páginas de **configuración** del portal de Cloud App Security se han rediseñado. El nuevo diseño consolida todas las páginas de configuración, proporciona la funcionalidad de búsqueda y un mejor diseño. 

- Cloud Discovery admite ahora Barracuda F-Series Firewalls y Barracuda F-Series Firewall Web Log Streaming.

- La funcionalidad de búsqueda en las páginas de dirección IP y de usuario habilita ahora Autocompletar para que le resulte más fácil encontrar lo que busca.

- Ahora puede realizar acciones en masa en las páginas de configuración de exclusión de entidades y de exclusión de direcciones IP. Esto hace que le resulte más fácil seleccionar varios usuarios y grupos o direcciones IP y excluirlos de la supervisión como parte de Cloud Discovery en su organización. 

## <a name="cloud-app-security-release-117"></a>Cloud App Security versión 117
Fecha de publicación: 20 de febrero de 2018

-   La mayor integración de Cloud App Security con Azure Information Protection permite ahora proteger archivos de G Suite. Esta característica de versión preliminar pública permite examinar y clasificar archivos de G Suite y aplicar automáticamente etiquetas de protección de Azure Information Protection para protegerlos. Para obtener más información, consulte [Integración de Azure Information Protection](azip-integration.md).

-   Cloud Discovery admite ahora [Digital Arts i-FILTER](http://www.daj.jp/en/products/if/).

-   La tabla Agentes SIEM incluye ahora más detalles que facilitan la administración.

## <a name="cloud-app-security-release-116"></a>Cloud App Security versión 116
Publicado el 4 de febrero de 2018
- La directiva de detección de anomalías de Cloud App Security se ha mejorado con nuevas **detecciones basadas en escenarios** entre las que se incluyen viaje imposible, actividad desde una dirección IP sospechosa y varios intentos incorrectos de inicio de sesión. Las nuevas directivas se habilitan automáticamente, lo que proporciona la detección de amenazas desde el primer momento en todo el entorno de nube. Además, las nuevas directivas exponen más datos a partir del motor de detección de Cloud App Security, lo que le ayuda a agilizar el proceso de investigación y contener las amenazas en curso. Para obtener más información, vea [Obtención de análisis de comportamiento y detección de anomalías instantáneos](https://docs.microsoft.com/en-us/cloud-app-security/anomaly-detection-policy).

- Despliegue gradual: Cloud App Security ahora se pone en correlación entre los usuarios y sus cuentas en aplicaciones de SaaS. Esto le permite investigar fácilmente todas las actividades de los usuarios, en todas sus diferentes aplicaciones de SaaS correlacionadas, con independencia de qué aplicación o cuenta utilizan.  

-   Despliegue gradual: Cloud App Security ahora admite varias instancias de la misma aplicación conectada. Si tiene varias instancias de, por ejemplo, Salesforce (una para venta y otra para marketing) podrá conectarlas a Cloud App Security y administrarlas desde la misma consola para crear directivas granulares y una investigación más a fondo. 

- Los analizadores de Cloud Discovery ahora admiten dos formatos adicionales de punto de control: XML y KPC.



## <a name="cloud-app-security-release-115"></a>Notas de la versión 115 de Cloud App Security
Fecha de publicación: 21 de enero de 2018

-   En esta versión se proporciona una experiencia mejorada al seleccionar carpetas específicas en las directivas de archivo. Ahora puede ver y seleccionar fácilmente varias carpetas para incluirlas en una directiva. 
-   En la página **Aplicaciones detectadas**: 
   - La característica de etiquetado masivo le permite aplicar etiquetas personalizadas (además de etiquetas autorizadas y no autorizadas). 
   - Cuando se **genera un informe de direcciones IP** o se **genera un informe de usuarios**, los informes exportados ahora incluyen la información sobre si el tráfico provenía de aplicaciones autorizadas o no autorizadas. 
-   Ahora puede solicitar un nuevo conector de aplicación de API del equipo de Microsoft Cloud App Security directamente en el portal, desde la página **Conectar una aplicación**. 


## <a name="cloud-app-security-release-114"></a>Notas de la versión 114 de Cloud App Security
Fecha de publicación: 7 de enero de 2018

- A partir de la versión 114, estamos implementando de forma gradual la capacidad de crear y guardar las consultas personalizadas en las páginas Registro de actividad y Aplicaciones detectadas. Las consultas personalizadas le permiten crear plantillas de filtro que se pueden volver a usar para investigar en profundidad. Además, se han agregado **consultas sugeridas** para proporcionar plantillas de investigación predeterminadas para filtrar las actividades y aplicaciones detectadas. Las **consultas sugeridas** incluyen filtros personalizados para identificar los riesgos, como las actividades de suplantación, las actividades de administrador, las aplicaciones de almacenamiento en la nube no conformes que implican un riesgo, las aplicaciones empresariales con cifrado débil y los riesgos de seguridad. Puede usar las **consultas sugeridas** como punto de partida, modificarlas según considere y después guardarlas como una nueva consulta. Para obtener más información, consulte [Filtros y consultas de actividad](activity-filters-queries.md) y [Filtros y consultas de aplicaciones detectadas](discovered-app-queries.md).
 
- Ahora puede comprobar el estado actual del servicio de Cloud App Security si va a [status.cloudappsecurity.com](https://status.cloudappsecurity.com) o directamente desde el portal al hacer clic en **Ayuda**>**Estado del sistema**. 
 


## <a name="see-also"></a>Consulte también  

Para obtener una descripción de las versiones anteriores a las mencionadas aquí, consulte [Past releases of Microsoft Cloud App Security](release-note-archive.md) (Versiones anteriores de Microsoft Cloud App Security).

[Los clientes Premier también pueden elegir Cloud App Security directamente desde el Portal Premier.](https://premier.microsoft.com/)  
  
  