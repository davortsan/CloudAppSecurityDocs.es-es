---
title: Referencia de plantillas de directiva en Cloud App Security | Microsoft Docs
description: "En este tema se proporciona información sobre cómo se usan las directivas y cómo se configuran para controlar el uso de aplicaciones en la nube."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 11/6/2017
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: a6658937-57a2-484a-85cb-5a4cdbeeb002
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: d9ffe832652885548ddeb49fd782d2a104c7523f
ms.sourcegitcommit: b729e881851cdd8dc3f105ddbf6b4b907b8588dd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/06/2017
---
# <a name="policy-templates"></a>Plantillas de directiva

La lista siguiente contiene todas las plantillas de directiva que existen en Cloud App Security. Se recomienda empezar la creación de directivas basándose en una plantilla existente, siempre que sea posible, para mejorar la facilidad de uso.

|Categoría de riesgo|Nombre de plantilla|Descripción|
|-----|----|----|
|Cloud Discovery|Comportamiento anómalo en los usuarios detectados|Alerta cuando se detecta un comportamiento anómalo en los usuarios y aplicaciones detectados, como grandes cantidades de datos cargados en comparación con otros usuarios o grandes transacciones del usuario en comparación con su historial.|
|Cloud Discovery|Comportamiento anómalo de direcciones IP detectadas|Alerta cuando se detecta un comportamiento anómalo en las direcciones IP y las aplicaciones detectadas, como grandes cantidades de datos cargados en comparación con otras direcciones IP o grandes transacciones de aplicaciones en comparación con el historial de la dirección IP.|
|Cloud Discovery|Comprobación de cumplimiento de aplicaciones de colaboración|Alerta cuando se detectan nuevas aplicaciones de colaboración que no son compatibles con SOC2 y SSAE 16 y que tienen más de 50 usuarios, con un uso diario total superior a 50 MB.|
|Cloud Discovery|Comprobación de cumplimiento de aplicación de almacenamiento en la nube|Alerta cuando se detectan nuevas aplicaciones de almacenamiento en la nube que no son compatibles con SOC2, SSAE 16, ISAE 3402 y PCI DSS y que tienen más de 50 usuarios, con un uso diario total superior a 50 MB.|
|Cloud Discovery|Comprobación de cumplimiento de aplicaciones CRM|Alerta cuando se detectan nuevas aplicaciones CRM que no son compatibles con SOC2, SSAE 16, ISAE 3402, ISO 27001 e HIPAA y que tienen más de 50 usuarios, con un uso diario total superior a 50 MB.|
|Cloud Discovery|Nueva aplicación de almacenamiento en nube|Alerta cuando se detectan nuevas aplicaciones de almacenamiento en nube que tienen más de 50 usuarios, con un uso diario total superior a 50 MB.|
|Cloud Discovery|Nueva aplicación de hospedaje de código|Alerta cuando se detectan nuevas aplicaciones de hospedaje de código que tienen más de 50 usuarios, con un uso diario total superior a 50 MB.|
|Cloud Discovery|Nueva aplicación de colaboración|Alerta cuando se detectan nuevas aplicaciones de colaboración que tienen más de 50 usuarios, con un uso diario total superior a 50 MB.|
|Cloud Discovery|Nueva aplicación CRM|Alerta cuando se detectan nuevas aplicaciones CRM que tienen más de 50 usuarios, con un uso diario total superior a 50 MB.|
|Cloud Discovery|Nueva aplicación de gran volumen|Alerta cuando se detectan aplicaciones nuevas con un tráfico diario total superior a 500 MB.|
|Cloud Discovery|Nueva aplicación con volumen de carga alto|Alerta cuando se detectan nuevas aplicaciones cuyo total de tráfico de carga diario es superior a 500 MB.|
|Cloud Discovery|Nueva aplicación de administración de recursos humanos|Alerta cuando las aplicaciones de administración de recursos humanos recientemente detectadas tienen más de 50 usuarios, con un uso diario total superior a 50 MB.|
|Cloud Discovery|Nueva aplicación de reuniones en línea|Alerta cuando se detectan nuevas aplicaciones de reuniones en línea que tienen más de 50 usuarios, con un uso diario total superior a 50 MB.|
|Cloud Discovery|Nueva aplicación popular|Alerta cuando se descubren nuevas aplicaciones que tienen más de 500 usuarios.|
|Cloud Discovery|Nueva aplicación de riesgo|Alerta cuando se detectan nuevas aplicaciones con una puntuación de riesgo inferior a 6 y que tienen más de 50 usuarios, con un uso diario total superior a 50 MB.|
|Cloud Discovery|Nueva aplicación de ventas|Alerta cuando se detectan nuevas aplicaciones de ventas que tienen más de 50 usuarios, con un uso diario total superior a 50 MB.|
|Cloud Discovery|Nuevas aplicaciones de sistema de administración de proveedores|Alerta cuando se detectan nuevas aplicaciones de sistema de administración de proveedores que tienen más de 50 usuarios, con un uso diario total superior a 50 MB.|
|DLP|Código fuente compartido externamente|Alerta cuando se comparte un archivo con código fuente fuera de la organización.|
|DLP|Archivo con información de tarjeta de pago detectado en la nube (motor DLP integrado)|Alerta cuando nuestro motor de prevención de pérdida de datos (DLP) integrado detecta un archivo que contiene información de tarjeta de pago en una aplicación de nube autorizada.|
|DLP|Archivo con información sanitaria protegida detectado en la nube (motor DLP integrado)|Alerta cuando nuestro motor de prevención de pérdida de datos (DLP) integrado detecta un archivo que contiene información sanitaria protegida en una aplicación de nube autorizada.|
|DLP|Archivo con información de identificación personal detectado en la nube (motor DLP integrado)|Alerta cuando nuestro motor de prevención de pérdida de datos (DLP) integrado detecta un archivo que contiene información de identificación personal en una aplicación de nube autorizada.|
|Detección de amenazas|Actividad administrativa desde una dirección IP no corporativa|Cuando un usuario administrador realiza una actividad administrativa desde una dirección IP que no está incluida en la categoría de intervalo de direcciones IP corporativas, se puede optar por enviar o recibir una alerta. Primero debe configurar las direcciones IP corporativas en la página Configuración y establecer los **intervalos de direcciones IP**.|
|Detección de amenazas|Detección de anomalías generales|Alerta cuando se detecta una sesión anómala en una de las aplicaciones autorizadas, como viaje imposible, patrón de inicio de sesión o cuenta inactiva.|
|Detección de amenazas|Inicio de sesión desde una dirección IP de riesgo|Alerta cuando un usuario inicia sesión en las aplicaciones autorizadas desde una dirección IP de riesgo. De forma predeterminada, la categoría de direcciones IP de riesgo contiene direcciones que tienen etiquetas de dirección IP de proxy anónimo, Tor o red de robots (botnet). Puede agregar más direcciones IP a esta categoría en la página de configuración de intervalos de direcciones IP.|
|Detección de amenazas|Descarga masiva de un solo usuario|Alerta cuando un solo usuario realiza más de 50 descargas en 1 minutos.|
|Detección de amenazas|Varios intentos de inicio de sesión de usuario erróneos en una aplicación|Alerta cuando un usuario intenta iniciar sesión en una única aplicación y se produce un error más de 10 veces en 5 minutos.|
|Detección de amenazas|Actividad potencial de ransomware|Alerta cuando un usuario carga en la nube archivos que podrían estar infectados con ransomware.|
|Detección de amenazas|Inicio de sesión de usuario desde una dirección IP no categorizada|Alerta cuando un usuario inicia sesión desde una dirección IP que no está incluida en una categoría específica de intervalos IP. Puede categorizar direcciones IP. Para ello, vaya a la página de configuración y seleccione los intervalos de direcciones IP.|
|Control de uso compartido|Archivo compartido con direcciones de correo electrónico personales|Alerta cuando se comparte un archivo que contiene la dirección de correo electrónico personal de un usuario.|
|Control de uso compartido|Archivo compartido con un dominio no autorizado|Alerta cuando se comparte un archivo con un dominio no autorizado (por ejemplo, la competencia).|
|Control de uso compartido|Certificados digitales compartidos (extensiones de archivo)|Alerta cuando se comparte públicamente un archivo que contiene certificados digitales.|
|Control de uso compartido|Archivos compartidos externamente obsoletos|Busca archivos compartidos externamente que no se han abierto o modificado durante 6 meses y los quita de la unidad.|



## <a name="see-also"></a>Consulte también  
[Actividades diarias para proteger el entorno de nube](daily-activities-to-protect-your-cloud-environment.md)   
[Para obtener soporte técnico, visite la página de soporte técnico asistido de Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Los clientes Premier también pueden elegir Cloud App Security directamente desde el Portal Premier.](https://premier.microsoft.com/)  
  