---
title: "Descripción de Cloud App Security | Microsoft Docs"
description: En este tema se describe Cloud App Security y su funcionamiento.
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 5/16/2017
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: d46756b1-7dd8-4190-9799-3a97688f1266
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: b76354c792ba75ab30b977112d3d0897ca4229a6
ms.sourcegitcommit: a0290ac2a662994f7771975ef6c20d0b47e9edd8
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/03/2017
---
# <a name="what-is-cloud-app-security"></a>Descripción de Cloud App Security

> [!NOTE]
> Para obtener información sobre la administración de seguridad avanzada de Cloud App Security en Office 365, consulte [Introducción a la administración de seguridad avanzada](https://support.office.com/article/Get-started-with-Advanced-Management-Security-d9ee4d67-f2b3-42b4-9c9e-c4529904990a).

Migrar a la nube aumenta la flexibilidad de cara a los empleados y reduce los costes de TI, pero también plantea nuevos retos y dificultades a la hora de mantener la seguridad de las organizaciones. Para aprovechar todas las ventajas de las aplicaciones en la nube, los equipos de TI deben encontrar el equilibrio adecuado entre admitir el acceso y no perder el control para proteger datos esenciales.  

Cloud App Security es un componente crítico de la pila de Microsoft Cloud Security. Es una completa solución que puede ayudar a su organización a sacar el máximo partido de la promesa de aplicaciones en la nube sin perder el control con una mejor visibilidad de la actividad. También ayuda a aumentar la protección de los datos críticos de las aplicaciones en la nube. Con herramientas que ayudan a detectar TI en la sombra, evaluar riesgos, aplicar directivas, investigar actividades y detener amenazas, su organización puede migrar a la nube de forma más segura sin perder el control de los datos críticos. 

## <a name="the-cloud-app-security-framework"></a>Marco de Cloud App Security  

- **Cloud Discovery**: detecte todo el uso en la nube de su organización, incluida la creación de informes y el control de Shadow IT y la evaluación de riesgos.
    
- **Protección de datos**: supervise y controle sus datos en la nube mediante la obtención de visibilidad, la aplicación de directivas DLP, alertas e investigación. 
    
- **Protección contra amenazas**: detecte incidentes de seguridad y uso erróneo. Use las herramientas de análisis de comportamiento e investigación avanzada para mitigar los riesgos y establecer directivas y alertas para lograr el máximo control sobre el tráfico de red en la nube.

## <a name="architecture"></a>Arquitectura  

Cloud App Security integra visibilidad con la nube de las siguientes formas:  

-   Utilizando Cloud Discovery para asignar e identificar el entorno de nube y las aplicaciones en la nube que utiliza su organización.
-   Autorizando o no aplicaciones en la nube.  
-   Utilizando conectores de aplicaciones fáciles de implementar que aprovechan las API del proveedor, para lograr visibilidad y administración de las aplicaciones a las que se conecte.  
-   Ayudándole a tener un control continuo al establecer y luego ajustar las directivas de forma continua.  

![Diagrama de la arquitectura de Cloud App Security](./media/architecture.png)  

### <a name="data-retention--compliance"></a>Cumplimiento y retención de datos

Cloud App Security está certificada oficialmente con Microsoft Compliance por ISO, HIPAA, CSA STAR, cláusulas de modelo EU, entre otros. Para ver la lista completa de certificaciones, vaya a [Ofertas de Microsoft Compliance] (https://go.microsoft.com/fwlink/?linkid=842039) y seleccione Cloud App Security.  

Cuando Cloud App Security realiza la inspección de contenido, se aplica la privacidad de los datos. El contenido del archivo no se almacena en la base de datos de Cloud App Security; solo los metadatos de los registros de archivo y las infracciones que se han identificado se almacenan en la base de datos de Cloud App Security. Para obtener más información sobre la retención de datos, consulte nuestra [directiva de privacidad](http://go.microsoft.com/fwlink/?LinkId=512132) y [Microsoft Trust Center](https://www.microsoft.com/TrustCenter/Privacy/You-are-in-control-of-your-data).
Cloud App Security conserva los datos como se indica a continuación: 
 
- Registro de actividad: 180 días 
- Datos de detección: 90 días 
- Alertas: 180 días 

Después de recopilar datos de estos orígenes, Cloud App Security ejecuta análisis sofisticados sobre los datos. Le avisa de inmediato de actividades anómalas y le proporciona visibilidad en su entorno de la nube. Puede configurar una directiva en Cloud App Security y usarla para proteger todo el contenido del entorno de la nube.  

### <a name="cloud-discovery"></a>Cloud Discovery  

Cloud Discovery usa los registros de tráfico para detectar y analizar de forma dinámica las aplicaciones en la nube que están en uso en la organización. Para crear un informe de instantáneas del uso de la nube de su organización, puede cargar manualmente los archivos de registro de los firewalls o servidores proxy para su análisis. Para configurar informes continuos, utilice recopiladores de registro de Cloud App Security para reenviar periódicamente los registros.  

Para obtener más información sobre Cloud Discovery, consulte [Set up Cloud Discovery](set-up-cloud-discovery.md) (Configurar Cloud Discovery).

### <a name="sanctioning-and-unsanctioning-an-app"></a>Autorización o no autorización de una aplicación  

Puede utilizar Cloud App Security para autorizar o no aplicaciones de la organización mediante el *catálogo de aplicaciones en la nube*. El equipo de analistas de Microsoft tiene un amplio catálogo en permanente aumento de más de 15 000 aplicaciones en la nube clasificadas y puntuadas según estándares del sector. Puede utilizar el catálogo de aplicaciones en la nube para evaluar el riesgo de las aplicaciones en la nube en función de certificaciones normativas, estándares del sector y procedimientos recomendados. A continuación puede personalizar las puntuaciones y la importancia de los distintos parámetros según las necesidades de la organización. En función de estas puntuaciones, Cloud App Security permite conocer el nivel de riesgo de una aplicación atendiendo a más de 50 factores de riesgo que podrían afectar al entorno.  

### <a name="app-connectors"></a>Conectores de aplicaciones  
Los conectores de aplicaciones utilizan las API de los proveedores de aplicaciones de la nube para integrar la nube de Cloud App Security con otras aplicaciones de la nube. Los conectores de aplicaciones amplían la protección y el control. También proporcionan acceso a la información directamente desde las aplicaciones de la nube, para el análisis de Cloud App Security.  

Para conectar una aplicación y ampliar la protección, el administrador de aplicaciones autoriza a Cloud App Security a acceder a la aplicación. Después, Cloud App Security consulta los registros de actividad de la aplicación y analiza los datos, las cuentas y el contenido de la nube. Cloud App Security puede aplicar directivas, detectar amenazas y proporcionar acciones de gobierno para solucionar problemas.  

Cloud App Security utiliza las API proporcionadas por el proveedor de la nube. Cada aplicación tiene su propio marco de trabajo y limitaciones de API. Cloud App Security funciona con los proveedores de aplicaciones para optimizar el uso de las API y garantizar el máximo rendimiento. Teniendo en cuenta las diferentes limitaciones que las aplicaciones imponen a las API (como la limitación de peticiones, los límites de API y las ventanas de API dinámicas de tiempo cambiante), los motores de Cloud App Security utilizan la capacidad permitida. Algunas operaciones, como el análisis de todos los archivos del inquilino, requieren numerosas API y, por lo tanto, se reparten a lo largo de un período de tiempo mayor. Tenga en cuenta que algunas directivas pueden ejecutarse durante varias horas o varios días.  

### <a name="policy-control"></a>Control de directivas  

Puede utilizar directivas para definir el comportamiento de los usuarios en la nube. Utilice directivas para detectar comportamiento arriesgado, infracciones o actividades y puntos de datos sospechosos en su entorno de la nube. Si es necesario, puede utilizar directivas para integrar los procesos de corrección con el fin de lograr la mitigación total de los riesgos. Varios tipos de directivas se correlacionan con los diferentes tipos de información que puede querer recopilar sobre el entorno de la nube y los tipos de acciones correctoras que quizás quiera realizar.  

## <a name="see-also"></a>Consulte también  

Consulte los aspectos básicos en [Introducción a Cloud App Security](getting-started-with-cloud-app-security.md).    
Para obtener soporte técnico, visite la página de [soporte técnico asistido de Cloud App Security](http://support.microsoft.com/oas/default.aspx?prid=16031).   
Los clientes Premier también pueden elegir Cloud App Security directamente desde el [Portal Premier](https://premier.microsoft.com/).   
