---
title: "Descripción de Cloud App Security | Microsoft Docs"
description: "En este tema se proporciona una descripción de Cloud App Security e información sobre su funcionamiento."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 10/15/2016
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: d46756b1-7dd8-4190-9799-3a97688f1266
ms.reviewer: reutam
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: ed4ea71b24767d3602d40894d1cbac7447bcd8a2
ms.openlocfilehash: d2ece0e3a47dc0febbb1314c496045abdc5c8d61


---
# <a name="what-is-cloud-app-security"></a>Descripción de Cloud App Security
 
> [!NOTE] 
> Para obtener información sobre las funciones de administración de seguridad avanzada de Cloud App Security en Office 365, consulte la introducción a la [administración de seguridad avanzada](https://support.office.com/article/Get-started-with-Advanced-Management-Security-d9ee4d67-f2b3-42b4-9c9e-c4529904990a). 
 
Aunque la migración a la nube ha aumentado la flexibilidad de cara a los empleados y ha reducido los costos de TI, también ha planteado nuevos retos y dificultades a la hora de mantener la seguridad de las organizaciones. Para aprovechar todas las ventajas de las aplicaciones en la nube, los equipos de TI deben encontrar el equilibrio adecuado entre permitir el acceso y no perder el control para proteger datos críticos.  
  
Cloud App Security es un componente crítico de la pila de Microsoft Cloud Security. Es una completa solución que ayuda a las organizaciones a sacar el máximo partido de la promesa de aplicaciones en la nube sin perder el control con una mejor visibilidad de la actividad. También aumenta la protección de datos críticos en las aplicaciones en la nube. Con herramientas para ayudar a detectar TI en la sombra, evaluar riesgos, aplicar directivas, investigar actividades y detener amenazas, las organizaciones pueden migrar a la nube de forma segura sin perder el control de los datos críticos.  
  
## <a name="the-cloud-app-security-framework"></a>Marco de Cloud App Security  

|       |   |   |
|-------|---|:---|
|![Detectar](./media/discovery-icon.png)|Detectar|Descubra Shadow IT con Cloud App Security. Gane visibilidad al detectar aplicaciones, actividades, usuarios, datos y archivos en el entorno de nube, además de aplicaciones de terceros que están conectadas a la nube.|
|![Investigar](./media/investigate-icon.png)|Investigar|Investigue las aplicaciones en la nube con herramientas forenses de nube para profundizar en aplicaciones de riesgo, usuarios y archivos concretos de la red y para detectar patrones en los datos recopilados de la nube y generar informes para supervisarla.|
|![Control](./media/protect-icon.png)|Control|Mitigue el riesgo al establecer directivas y alertas para lograr el máximo control sobre el tráfico de red de nube. Use Cloud App Security para migrar a los usuarios a alternativas de aplicaciones seguras y autorizadas en la nube.|
|![Proteger](./media/protect-icon.png)|Proteger|Use Cloud App Security para autorizar o no aplicaciones, aplicar la prevención de pérdida de datos (DLP), controlar los permisos y el uso compartido y generar alertas e informes personalizados.|


## <a name="architecture"></a>Arquitectura  

Cloud App Security habilita la integración de visibilidad con la nube de las maneras siguientes:  
  
-   Visibilidad con Cloud Discovery para asignar e identificar el entorno de nube y las aplicaciones en la nube en uso.  
-   Posibilidad de autorizar o no aplicaciones en la nube.  
-   Visibilidad y gobierno de aplicaciones a las que se conecte mediante los conectores de aplicaciones fáciles de implementar que aprovechan las API del proveedor.  
-   Control continuo al permitir establecer y luego ajustar las directivas de forma continua.  
  
![](./media/architecture.png)  
  
> [!NOTE]  
>  Cuando Cloud App Security realiza la inspección de contenido, se aplica la privacidad de los datos. Los datos no se almacenan en la base de datos de Cloud App Security, únicamente los metadatos de los registros de archivos y las infracciones identificadas. Consulte nuestra [directiva de privacidad](http://go.microsoft.com/fwlink/?LinkId=512132) y [Microsoft Trust Center](https://www.microsoft.com/TrustCenter/Privacy/You-are-in-control-of-your-data) para obtener más información sobre la retención de datos.
Cloud App Security conserva los datos como se indica a continuación:
>- Registro de actividad: 180 días
>- Datos de detección: 90 días
>- Alertas: ilimitado 

Después de recopilar datos de estos orígenes, Cloud App Security ejecuta un sofisticado análisis de ellos, alerta de inmediato de actividades anómalas y proporciona una gran visibilidad. Luego puede configurar una directiva en Cloud App Security y usarla para proteger todo el contenido del entorno de nube.  
  
###  <a name="how-cloud-discovery-works"></a>Funcionamiento de Cloud Discovery  

Cloud Discovery usa los registros de tráfico para detectar y analizar de forma dinámica qué aplicaciones en la nube están en uso en la organización.  
  
Puede crear un informe de instantáneas del uso de la nube de la organización mediante la carga manual de los archivos de registro desde los firewalls o los servidores proxy para su análisis, o bien puede configurar informes continuos mediante el uso de los recopiladores de registros de Cloud App Security para reenviar los registros periódicamente.  

Para obtener más información sobre Cloud Discovery, consulte [Set up Cloud Discovery](set-up-cloud-discovery.md) (Configurar Cloud Discovery).
  
### <a name="how-sanctioning-and-unsanctioning-an-app-works"></a>Funcionamiento de la autorización o no autorización de una aplicación  

Cloud App Security permite autorizar o no aplicaciones de la organización mediante el **catálogo de aplicaciones en la nube**.  
  
El equipo de analistas de Microsoft tiene un amplio catálogo en permanente aumento de más de 13.000 aplicaciones en la nube clasificadas y puntuadas según estándares del sector. El **catálogo de aplicaciones en la nube** evalúa el riesgo de las aplicaciones en la nube en función de certificaciones normativas, estándares del sector y procedimientos recomendados. A continuación puede personalizar las puntuaciones y la importancia de los distintos parámetros según las necesidades de la organización. En función de estas puntuaciones, Cloud App Security permite saber el nivel de riesgo de una aplicación según más de 50 factores de riesgo que podrían afectar al entorno.  
  
### <a name="how-app-connectors-work"></a>Funcionamiento de los conectores de aplicaciones  
Los conectores de aplicaciones aprovechan las API proporcionadas por los distintos proveedores de aplicaciones en la nube para permitir que la nube de Cloud App Security se integre con otras aplicaciones en la nube y ampliar el control y la protección. Esto permite a Cloud App Security extraer información directamente de las aplicaciones en la nube para su análisis.  
Para conectar una aplicación y ampliar la protección, el administrador de la aplicación autoriza a Cloud App Security el acceso a ella. Luego, Cloud App Security consulta los registros de actividad y examina los datos, las cuentas y el contenido en la nube de la aplicación. Después, Cloud App Security puede aplicar directivas, detectar amenazas y proporcionar acciones de gobierno para solucionar problemas.  
  
Cloud App Security aprovecha las API que proporciona el proveedor de nube. Cada aplicación tiene su propio marco de trabajo y limitaciones de API. Cloud App Security funciona con los proveedores de aplicaciones para optimizar el uso de las API y garantizar el máximo rendimiento. Teniendo en cuenta las diferentes limitaciones que las aplicaciones imponen a las API (como la limitación de peticiones, los límites de API, las ventanas de API dinámicas de tiempo cambiante, etc.), los motores de Cloud App Security aprovechan la capacidad permitida. Algunas operaciones, como el análisis de todos los archivos del inquilino, requieren numerosas API y, por lo tanto, se reparten a lo largo de un período de tiempo mayor. Tenga en cuenta que algunas directivas pueden ejecutarse durante varias horas o varios días.  
  
### <a name="how-policy-control-works"></a>Funcionamiento del control de directivas  

Las directivas permiten definir la forma en que quiere que los usuarios se comporten en la nube. Permiten detectar comportamientos de riesgo, infracciones o puntos de datos y actividades sospechosos en el entorno de nube y, si fuera necesario, integrar procesos de corrección para lograr una mitigación de riesgos completa. Hay varios tipos de directivas que se correlacionan con los diferentes tipos de información que quiere recopilar sobre el entorno de nube y los tipos de acciones correctoras que quizás quiera realizar.  
  
## <a name="see-also"></a>Consulte también  

[Introducción a Cloud App Security](getting-started-with-cloud-app-security.md)   
[Para obtener soporte técnico, visite la página de soporte técnico asistido de Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Los clientes Premier también pueden elegir Cloud App Security directamente desde el Portal Premier.](https://premier.microsoft.com/)  
  
  


<!--HONumber=Oct16_HO4-->


