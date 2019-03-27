---
title: Descripción de Cloud App Security
description: En este artículo se describe Microsoft Cloud App Security y su funcionamiento.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: barbkess
ms.date: 1/27/2019
ms.topic: overview
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: d46756b1-7dd8-4190-9799-3a97688f1266
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 12e1ea59e4d8f99b57f6ba494430aef6082d4204
ms.sourcegitcommit: fe4cd2174f6dc83811a2d484f079e8dfbac5d082
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/26/2019
ms.locfileid: "58476712"
---
# <a name="microsoft-cloud-app-security-overview"></a>Introducción a Microsoft Cloud App Security

*Se aplica a: Microsoft Cloud App Security*

> [!NOTE]
> Para obtener información sobre Office 365 Cloud App Security, consulte [Introducción a Office 365 Cloud App Security](https://support.office.com/article/Get-started-with-Advanced-Management-Security-d9ee4d67-f2b3-42b4-9c9e-c4529904990a).

Pasar a la nube aumenta la flexibilidad de los empleados y reduce los costos de TI. En cambio, también plantea nuevos retos y dificultades a la hora de mantener su organización segura. Para aprovechar todas las ventajas de las aplicaciones en la nube, los equipos de TI deben encontrar el equilibrio adecuado entre admitir el acceso y no perder el control para proteger datos esenciales.  

Cloud App Security es un componente crítico de la pila de Microsoft Cloud Security. Es una completa solución que puede ayudar a su organización a sacar el máximo partido de la promesa de aplicaciones en la nube sin perder el control con una mejor visibilidad de la actividad. También ayuda a aumentar la protección de los datos críticos de las aplicaciones en la nube. Con herramientas que ayudan a detectar TI en la sombra, evaluar riesgos, aplicar directivas, investigar actividades y detener amenazas, su organización puede migrar a la nube de forma más segura sin perder el control de los datos críticos. 

Para información sobre las licencias, consulte la [hoja de datos de licencias de Microsoft Cloud App Security](https://aka.ms/mcaslicensing).

## <a name="the-cloud-app-security-framework"></a>Marco de Cloud App Security  

- **Cloud Discovery**: detecte todo el uso en la nube de su organización, incluida la creación de informes y el control de Shadow IT, así como la evaluación de riesgos.

- **Protección de datos**: supervise y controle sus datos en la nube mediante la obtención de visibilidad, la aplicación de directivas DLP, las alertas y la investigación. 

- **Protección contra amenazas**: detecte incidentes de seguridad y uso anómalo. Use las herramientas de análisis de comportamiento e investigación avanzada para mitigar los riesgos y establecer directivas y alertas para lograr el máximo control sobre el tráfico de red en la nube.

## <a name="architecture"></a>Arquitectura  

Cloud App Security integra visibilidad con la nube de las siguientes formas:  

- Al usar Cloud Discovery para asignar e identificar el entorno de nube y las aplicaciones en la nube que usa su organización.
- Al autorizar o no aplicaciones en la nube.  
- Al usar conectores de aplicaciones fáciles de implementar que aprovechan las API del proveedor, para lograr visibilidad y administración de las aplicaciones a las que se conecte.  
- Al usar la protección del control de aplicaciones de acceso condicional para obtener visibilidad en tiempo real y control del acceso y las actividades de las aplicaciones en la nube.
- Al establecer y luego ajustar las directivas de forma continua para ayudarle a tener un control continuo.  

![Diagrama de la arquitectura de Cloud App Security](./media/proxy-architecture.png)  

### <a name="data-retention--compliance"></a>Cumplimiento y retención de datos

Para más información sobre el cumplimiento y retención de datos de Microsoft Cloud App Security, consulte [Seguridad y privacidad de datos de Microsoft Cloud App Security](cas-compliance-trust.md).

### <a name="cloud-discovery"></a>Cloud Discovery  

Cloud Discovery usa los registros de tráfico para detectar y analizar de forma dinámica las aplicaciones en la nube que están en uso en la organización. Para crear un informe de instantáneas del uso de la nube de su organización, puede cargar manualmente los archivos de registro de los firewalls o servidores proxy para su análisis. Para configurar informes continuos, utilice recopiladores de registro de Cloud App Security para reenviar periódicamente los registros.  

Para obtener más información sobre Cloud Discovery, consulte [Set up Cloud Discovery](set-up-cloud-discovery.md) (Configurar Cloud Discovery).

### <a name="sanctioning-and-unsanctioning-an-app"></a>Autorización o no autorización de una aplicación  

Puede utilizar Cloud App Security para autorizar o no aplicaciones de la organización mediante el *catálogo de aplicaciones en la nube*. El equipo de analistas de Microsoft tiene un amplio catálogo en permanente aumento de más de 16 000 aplicaciones en la nube clasificadas y puntuadas según estándares del sector. Puede utilizar el catálogo de aplicaciones en la nube para evaluar el riesgo de las aplicaciones en la nube en función de certificaciones normativas, estándares del sector y procedimientos recomendados. A continuación puede personalizar las puntuaciones y la importancia de los distintos parámetros según las necesidades de la organización. Según estas puntuaciones, Cloud App Security le permite saber el nivel de riesgo de una aplicación. La puntuación se basa en más de 70 factores de riesgo que podrían afectar a su entorno.  

### <a name="app-connectors"></a>Conectores de aplicaciones

Los conectores de aplicaciones utilizan las API de los proveedores de aplicaciones de la nube para integrar la nube de Cloud App Security con otras aplicaciones de la nube. Los conectores de aplicaciones amplían la protección y el control. También proporcionan acceso a la información directamente desde las aplicaciones de la nube, para el análisis de Cloud App Security.  

Para conectar una aplicación y ampliar la protección, el administrador de aplicaciones autoriza a Cloud App Security a acceder a la aplicación. Después, Cloud App Security consulta los registros de actividad de la aplicación y analiza los datos, las cuentas y el contenido de la nube. Cloud App Security puede aplicar directivas, detectar amenazas y proporcionar acciones de gobernanza para solucionar problemas.  

Cloud App Security utiliza las API proporcionadas por el proveedor de la nube. Cada aplicación tiene su propio marco de trabajo y limitaciones de API. Cloud App Security funciona con los proveedores de aplicaciones para optimizar el uso de las API y garantizar el máximo rendimiento. Teniendo en cuenta las diferentes limitaciones que las aplicaciones imponen a las API (como la limitación de peticiones, los límites de API y las ventanas de API dinámicas de tiempo cambiante), los motores de Cloud App Security utilizan la capacidad permitida. Algunas operaciones, como el análisis de todos los archivos del inquilino, requieren numerosas API y, por lo tanto, se reparten a lo largo de un período de tiempo mayor. Tenga en cuenta que algunas directivas pueden ejecutarse durante varias horas o varios días.  

### <a name="conditional-access-app-control-protection"></a>Protección de control de aplicaciones de acceso condicional

El control de aplicaciones de acceso condicional de Microsoft Cloud App Security usa la arquitectura de proxy inverso para ofrecerle las herramientas que necesita a fin de tener visibilidad en tiempo real y control del acceso al entorno en la nube y a las actividades realizadas en él. Con el control de aplicaciones de acceso condicional puede proteger su organización:

- Bloquee las descargas antes de que se realicen para evitar las fugas de datos
- Establezca reglas que obliguen a proteger cifrados los datos almacenados y descargados de la nube
- Obtenga visibilidad de los puntos de conexión no protegidos para que pueda supervisar lo que se hace en los dispositivos no administrados
- Controle el acceso desde redes no corporativas o direcciones IP de riesgo

### <a name="policy-control"></a>Control de directivas  

Puede utilizar directivas para definir el comportamiento de los usuarios en la nube. Utilice directivas para detectar comportamiento arriesgado, infracciones o actividades y puntos de datos sospechosos en su entorno de la nube. Si es necesario, puede utilizar directivas para integrar los procesos de corrección con el fin de lograr la mitigación total de los riesgos. Los tipos de directivas se correlacionan con los diferentes tipos de información que puede querer recopilar sobre el entorno de la nube y los tipos de acciones correctoras que quizás quiera realizar.  

## <a name="related-videos"></a>Vídeos relacionados

- [Joining the security community](https://channel9.msdn.com/Shows/Microsoft-Security/Join-the-Security-Community) (Unirse a la comunidad de seguridad)

## <a name="next-steps"></a>Pasos siguientes  

Consulte los aspectos básicos en [Introducción a Cloud App Security](getting-started-with-cloud-app-security.md).    

[Los clientes Premier también pueden crear una nueva solicitud de soporte técnico directamente en el portal Premier.](https://premier.microsoft.com/)   
