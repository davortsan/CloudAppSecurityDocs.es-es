---
title: ¿Qué es Cloud App Security?
description: En este artículo se describe Microsoft Cloud App Security y cómo funciona.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 8/15/2019
ms.topic: overview
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: d46756b1-7dd8-4190-9799-3a97688f1266
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 49ecd0d844dd30c4816095686a353c301df4fa49
ms.sourcegitcommit: 0b929f7c8feed7dfb40d5294179fd5c6fc079614
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/21/2020
ms.locfileid: "74720457"
---
# <a name="microsoft-cloud-app-security-overview"></a>Introducción a Microsoft Cloud App Security

*Se aplica a: Microsoft Cloud App Security*

> [!NOTE]
> Para información sobre Office 365 Cloud App Security, consulte [Introducción a Office 365 Cloud App Security](https://support.office.com/article/Get-started-with-Advanced-Management-Security-d9ee4d67-f2b3-42b4-9c9e-c4529904990a).

Pasar a la nube aumenta la flexibilidad de los empleados y la TI por igual. Sin embargo, también presenta nuevos desafíos y complejidades para proteger la organización. Para aprovechar todas las ventajas de las aplicaciones y los servicios en la nube, los equipos de TI deben encontrar el equilibrio adecuado entre admitir el acceso y no perder el control para proteger datos esenciales.

Microsoft Cloud App Security es un agente de seguridad de acceso a la nube que admite distintos modos de implementación, incluyendo la recopilación de registros, los conectores de API y el proxy inverso. Proporciona visibilidad enriquecida, control sobre el viaje de los datos y análisis sofisticados para identificar y combatir las ciberamenazas en todos los servicios en la nube de terceros y Microsoft.

Microsoft Cloud App Security integra de forma nativa las principales soluciones de Microsoft y se ha diseñado pensando en los profesionales de la seguridad. Ofrece una implementación simple, una administración centralizada y funcionalidades de automatización innovadoras.

Para información sobre las licencias, consulte la [hoja de datos de licencias de Microsoft Cloud App Security](https://aka.ms/mcaslicensing).

## <a name="the-cloud-app-security-framework"></a>Marco de Cloud App Security

- **Detectar y controlar el uso de Shadow IT**: identifique las aplicaciones en la nube y los servicios IaaS y PaaS que usa la organización. Investigue patrones de uso, evalúe los niveles de riesgo y la preparación para el negocio de más de 16 000 aplicaciones SaaS contra más de 80 riesgos. Empiece a administrarlas con el fin de garantizar la seguridad y el cumplimiento.

- **Proteger información confidencial en cualquier lugar en la nube**: comprenda, clasifique y proteja la exposición de información confidencial en reposo. Aproveche las directivas y los procesos automatizados listos para usar a fin de aplicar los controles en tiempo real en todas las aplicaciones en la nube.

- **Protegerse frente a ciberamenazas y anomalías**: detecte un comportamiento poco habitual en las aplicaciones en la nube para identificar el ransomware, usuarios en peligro o aplicaciones no autorizadas, analice el uso de alto riesgo y corríjalo automáticamente para limitar el riesgo para su organización.

- **Evaluar el cumplimiento de las aplicaciones en la nube**: valore si las aplicaciones en la nube cumplen los requisitos de desempeño pertinentes, incluidos el cumplimiento de normas y los estándares del sector. Impida las pérdidas de datos hacia las aplicaciones que no cumplen con las normas y limite el acceso a los datos regulados.

## <a name="architecture"></a>Arquitectura

Cloud App Security integra la visibilidad con la nube de varias maneras:

- El uso de Cloud Discovery para asignar e identificar el entorno de nube y las aplicaciones en la nube que usa la organización.
- La autorización y desautorización de aplicaciones en la nube.
- El uso de conectores de aplicaciones fáciles de implementar que aprovechan las ventajas de las API de proveedor para la visibilidad y la gobernanza de las aplicaciones a las que se conecta.
- El uso de la protección de Control de aplicaciones de acceso condicional para obtener visibilidad y control en tiempo real sobre el acceso y las actividades dentro de las aplicaciones en la nube.
- Le ayuda a tener un control continuo mediante la configuración y el ajuste continuo de las directivas.

![Diagrama de la arquitectura de Cloud App Security](media/proxy-architecture.png)

### <a name="data-retention--compliance"></a>Cumplimiento y retención de datos

Para más información sobre el cumplimiento y la retención de los datos de Microsoft Cloud App Security, consulte [Seguridad y privacidad de los datos de Microsoft Cloud App Security](cas-compliance-trust.md).

### <a name="cloud-discovery"></a>Cloud Discovery

Cloud Discovery usa los registros de tráfico para detectar y analizar de forma dinámica las aplicaciones en la nube que usa la organización. Para crear un informe de instantáneas del uso de la nube por parte de su organización, puede cargar manualmente los archivos de registro desde los firewalls o servidores proxy con el fin de analizarlos. Para configurar informes continuos, use los recopiladores de registros de Cloud App Security para reenviar periódicamente los registros.

Para más información sobre Cloud Discovery, consulte [Configuración de Cloud Discovery](set-up-cloud-discovery.md).

### <a name="sanctioning-and-unsanctioning-an-app"></a>Autorización y desautorización de aplicaciones

Puede usar Cloud App Security para autorizar o desautorizar aplicaciones de la organización mediante el *catálogo de aplicaciones en la nube*. El equipo de analistas de Microsoft dispone de un catálogo amplio y en continuo crecimiento de más de 16 000 aplicaciones en la nube que se clasifican y puntúan en función de estándares del sector. Puede usar el catálogo de aplicaciones en la nube para clasificar el riesgo de estas según certificaciones normativas, estándares del sector y procedimientos recomendados. Luego, puede personalizar las puntuaciones y las ponderaciones de distintos parámetros según las necesidades de su organización. En función de estas puntuaciones, Cloud App Security le permite conocer el riesgo de una aplicación. La puntuación se basa en más de 80 factores de riesgo que podrían afectar al entorno.

### <a name="app-connectors"></a>Conectores de aplicaciones

Los conectores de aplicaciones usan las API de los proveedores de aplicaciones en la nube para integrar la nube de Cloud App Security con otras aplicaciones en la nube. Los conectores de aplicaciones amplían el control y la protección. También proporcionan acceso a información directamente desde aplicaciones en la nube, para el análisis de Cloud App Security.

Para conectar una aplicación y ampliar la protección, el administrador de la aplicación autoriza a Cloud App Security el acceso a esta. Luego, Cloud App Security consulta los registros de actividad de la aplicación y examina los datos, las cuentas y el contenido de la nube. Cloud App Security puede aplicar directivas, detectar amenazas y proporcionar acciones de gobernanza para resolver los problemas.

Cloud App Security usa las API proporcionadas por el proveedor de nube. Cada aplicación tiene sus propias limitaciones de marco de trabajo y API. Cloud App Security funciona con proveedores de aplicaciones para optimizar el uso de las API y garantizar el máximo rendimiento. Los motores de Cloud App Security tienen en cuenta las diferentes limitaciones que imponen las aplicaciones sobre las API (como el límite de ancho de banda de red, los límites de API y las ventanas de API dinámicas de cambio de tiempo) para usar la capacidad permitida. Algunas operaciones, como el examen de todos los archivos del inquilino, requieren un gran número de API, por lo que se reparten durante un período más largo. Tenga en cuenta que algunas directivas pueden ejecutarse durante varias horas o varios días.

### <a name="conditional-access-app-control-protection"></a>Protección del Control de aplicaciones de acceso condicional

El Control de aplicaciones de acceso condicional de Microsoft Cloud App Security usa la arquitectura de proxy inverso para proporcionarle las herramientas que necesita para tener visibilidad y control en tiempo real sobre el acceso y las actividades realizadas dentro de su entorno de nube. Con el Control de aplicaciones de acceso condicional, puede proteger su organización de las siguientes formas:

- Evitar pérdidas de datos al bloquear las descargas antes de que se produzcan
- Establecer reglas que fuercen la protección con cifrado de los datos almacenados en la nube y descargados de esta
- Obtener visibilidad sobre los puntos de conexión no protegidos para que pueda supervisar lo que se hace en los dispositivos no administrados
- Controlar el acceso desde redes no corporativas o direcciones IP de riesgo

### <a name="policy-control"></a>Control de directivas

Puede usar directivas para definir el comportamiento de los usuarios en la nube. Use directivas para detectar comportamientos de riesgo, infracciones o puntos de datos y actividades sospechosos en el entorno de nube. Si es necesario, puede usar directivas para integrar los procesos de corrección a fin de lograr una mitigación de riesgos completa. Los tipos de directivas se correlacionan con los diferentes tipos de información que podría recopilar sobre el entorno de nube y los tipos de acciones correctoras que podría llevar a cabo.

## <a name="related-videos"></a>Vídeos relacionados

- [Unirse a la comunidad de seguridad](https://channel9.msdn.com/Shows/Microsoft-Security/Join-the-Security-Community)

## <a name="next-steps"></a>Pasos siguientes

Consulte los aspectos básicos en [Introducción a Cloud App Security](getting-started-with-cloud-app-security.md).

[!INCLUDE [Open support ticket](includes/support.md)].
