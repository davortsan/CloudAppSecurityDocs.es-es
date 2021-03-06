---
title: Referencia de plantillas de directiva de Cloud App Security
description: En este artículo se proporciona información sobre las plantillas de directiva incluidas en Microsoft Cloud App Security.
ms.date: 12/1/2019
ms.topic: how-to
ms.openlocfilehash: 6ae6eec80234a858e1d854db004cc5a2615d1c79
ms.sourcegitcommit: d87372b47ca98e942c2bf94032a6a61902627d69
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/30/2020
ms.locfileid: "96310931"
---
# <a name="policy-template-reference"></a>Referencia de plantillas de directiva

[!INCLUDE [Banner for top of topics](includes/banner.md)]

En este artículo se proporciona información sobre las plantillas de directiva incluidas en Microsoft Cloud App Security.

## <a name="policy-templates"></a>Plantillas de directiva

Se recomienda empezar la creación de directivas basándose en una plantilla existente, siempre que sea posible, para mejorar la facilidad de uso. En esta tabla se enumeran las plantillas de directiva que existen en Microsoft Cloud App Security.

|Categoría de riesgo|Nombre de plantilla|Descripción|
|-----|----|----|
|Cloud Discovery|Comportamiento anómalo en los usuarios detectados|Alerta cuando se detecta un comportamiento anómalo en los usuarios y aplicaciones detectados, como grandes cantidades de datos cargados en comparación con otros usuarios o grandes transacciones del usuario en comparación con su historial.|
|Cloud Discovery|Comportamiento anómalo de direcciones IP detectadas|Alerta cuando se detecta un comportamiento anómalo en las direcciones IP y las aplicaciones detectadas, como grandes cantidades de datos cargados en comparación con otras direcciones IP o grandes transacciones de aplicaciones en comparación con el historial de la dirección IP.|
|Cloud Discovery|Comprobación de cumplimiento de aplicaciones de colaboración|Alerta cuando se detectan nuevas aplicaciones de colaboración que no son compatibles con SOC2 y SSAE 16, y que tienen más de 50 usuarios, con un uso diario total superior a 50 MB.|
|Cloud Discovery|Comprobación de cumplimiento de aplicación de almacenamiento en la nube|Alerta cuando se detectan nuevas aplicaciones de almacenamiento en la nube que no son compatibles con SOC2, SSAE 16, ISAE 3402 y PCI DSS, y que tienen más de 50 usuarios, con un uso diario total superior a 50 MB.|
|Cloud Discovery|Comprobación de cumplimiento de aplicaciones CRM|Alerta cuando se detectan nuevas aplicaciones CRM que no son compatibles con SOC2, SSAE 16, ISAE 3402, ISO 27001 e HIPAA, y que tienen más de 50 usuarios, con un uso diario total superior a 50 MB.|
|Cloud Discovery|Nueva aplicación de almacenamiento en nube|Alerta cuando se detectan nuevas aplicaciones de almacenamiento en nube que tienen más de 50 usuarios, con un uso diario total superior a 50 MB.|
|Cloud Discovery|Nueva aplicación de hospedaje de código|Alerta cuando se detectan nuevas aplicaciones de hospedaje de código que tienen más de 50 usuarios, con un uso diario total superior a 50 MB.|
|Cloud Discovery|Nueva aplicación de colaboración|Alerta cuando se detectan nuevas aplicaciones de colaboración que tienen más de 50 usuarios, con un uso diario total superior a 50 MB.|
|Cloud Discovery|Nueva aplicación CRM|Envía una alerta cuando se detectan aplicaciones de CRM nuevas con más de 50 usuarios activos y un uso diario total superior a 50 MB.|
|Cloud Discovery|Nueva aplicación de gran volumen|Alerta cuando se detectan aplicaciones nuevas con un tráfico diario total superior a 500 MB.|
|Cloud Discovery|Nueva aplicación con volumen de carga alto|Alerta cuando se detectan nuevas aplicaciones cuyo total de tráfico de carga diario es superior a 500 MB.|
|Cloud Discovery|Nueva aplicación de administración de recursos humanos|Alerta cuando las aplicaciones de administración de recursos humanos recientemente detectadas tienen más de 50 usuarios, con un uso diario total superior a 50 MB.|
|Cloud Discovery|Nueva aplicación de reuniones en línea|Alerta cuando se detectan nuevas aplicaciones de reuniones en línea que tienen más de 50 usuarios, con un uso diario total superior a 50 MB.|
|Cloud Discovery|Nueva aplicación popular|Alerta cuando se descubren nuevas aplicaciones que tienen más de 500 usuarios.|
|Cloud Discovery|Nueva aplicación de riesgo|Alerta cuando se detectan nuevas aplicaciones con una puntuación de riesgo inferior a 6 y que tienen más de 50 usuarios, con un uso diario total superior a 50 MB.|
|Cloud Discovery|Nueva aplicación de ventas|Alerta cuando se detectan nuevas aplicaciones de ventas que tienen más de 50 usuarios, con un uso diario total superior a 50 MB.|
|Cloud Discovery|Nuevas aplicaciones de sistema de administración de proveedores|Alerta cuando se detectan nuevas aplicaciones de sistema de administración de proveedores que tienen más de 50 usuarios, con un uso diario total superior a 50 MB.|
|DLP|Código fuente compartido externamente|Alerta cuando se comparte un archivo con código fuente fuera de la organización.|
|DLP|Archivo con información de tarjeta de pago detectado en la nube (motor DLP integrado)|Alerta cuando nuestro motor de prevención de pérdida de datos (DLP) integrado de Microsoft Cloud App Security detecta un archivo que contiene información de tarjeta de pago (PCI) en una aplicación de nube autorizada.|
|DLP|Archivo con información sanitaria protegida detectado en la nube (motor DLP integrado)|Alerta cuando nuestro motor de prevención de pérdida de datos (DLP) integrado de Microsoft Cloud App Security detecta un archivo que contiene información de estado protegida (PHI) en una aplicación de nube autorizada.|
|DLP|Archivo con información privada detectado en la nube (motor DLP integrado)|Alerta cuando nuestro motor de prevención de pérdida de datos (DLP) integrado de Microsoft Cloud App Security detecta un archivo que contiene datos personales en una aplicación de nube autorizada.|
|Detección de amenazas|Actividad administrativa desde una dirección IP no corporativa|Cuando un usuario administrador realiza una actividad administrativa desde una dirección IP que no está incluida en la categoría de intervalo de direcciones IP corporativas, se puede optar por enviar o recibir una alerta. Primero configure las direcciones IP corporativas en la página Configuración y establezca los **intervalos de direcciones IP**.|
|Detección de amenazas|Inicio de sesión desde una dirección IP de riesgo|Alerta cuando un usuario inicia sesión en las aplicaciones autorizadas desde una dirección IP de riesgo. De forma predeterminada, la categoría de direcciones IP de riesgo contiene direcciones que tienen etiquetas de dirección IP de proxy anónimo, Tor o red de robots (botnet). Puede agregar más direcciones IP a esta categoría en la página de configuración de intervalos de direcciones IP.|
|Detección de amenazas|Descarga masiva de un solo usuario|Alerta cuando un solo usuario realiza más de 50 descargas en 1 minutos.|
|Detección de amenazas|Varios intentos de inicio de sesión de usuario erróneos en una aplicación|Alerta cuando un usuario intenta iniciar sesión en una única aplicación y se produce un error más de 10 veces en 5 minutos.|
|Detección de amenazas|Actividad potencial de ransomware|Alerta cuando un usuario carga en la nube archivos que podrían estar infectados con ransomware.|
|Control de uso compartido|Archivo compartido con direcciones de correo electrónico personales|Alerta cuando se comparte un archivo con la dirección de correo electrónico personal de un usuario.|
|Control de uso compartido|Archivo compartido con un dominio no autorizado|Alerta cuando se comparte un archivo con un dominio no autorizado (por ejemplo, la competencia).|
|Control de uso compartido|Certificados digitales compartidos (extensiones de archivo)|Alerta cuando se comparte públicamente un archivo que contiene certificados digitales. Use esta plantilla para ayudar a regular su almacenamiento de AWS.|
|Control de uso compartido|Cubos de S3 accesibles públicamente (AWS)|Alerta cuando un cubo de AWS S3 se comparte públicamente.|
|Control de uso compartido|Archivos compartidos externamente obsoletos|Alerta cuando los archivos compartidos externamente no se han modificado durante al menos 6 meses.|

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Actividades diarias para proteger el entorno de nube](daily-activities-to-protect-your-cloud-environment.md)

[!INCLUDE [Open support ticket](includes/support.md)]
