---
title: "Inspección de contenido | Microsoft Docs"
description: "En este artículo se describe el proceso que Cloud App Security sigue al realizar la inspección de contenido de DLP en los datos en la nube."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 11/27/2016
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: 2401adbc-0011-4938-9e3a-a4c719a2f619
ms.reviewer: reutam
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 52f2245779568abbf41d47c4b45cdcced302529b
ms.openlocfilehash: 19d5b0624233da2af64cf35bd2e7ef8ca118c638


---

# <a name="content-inspection"></a>Inspección de contenido
En este artículo se describe el proceso que Cloud App Security sigue al realizar la inspección de contenido de DLP en los datos en la nube. 


La inspección de contenido de Cloud App Security funciona de la manera siguiente:
1. Primero, Cloud App Security realiza un examen prácticamente en tiempo real (NRT) de las unidades y los eventos que se identifican como nuevos o modificados.
2. Después, realiza un examen continuo de todos los archivos pertinentes de todas las unidades.  

Tanto los archivos del examen en tiempo real como los del examen continuo se agregan a la cola para su inspección. El orden de los archivos colocados en la cola para su examen se establece por actividad en los archivos y en el examen de las unidades. Los archivos se examinan únicamente si los metadatos de archivo muestran que es un tipo MIME admitido. Tenga en cuenta que este examen se aplica a archivos pertinentes para el examen de datos (documentos, imágenes, presentaciones, hojas de cálculo, archivos de texto y archivos de almacenamiento o ZIP).  

Después de examinar un archivo, ocurre lo siguiente:

1. Cloud App Security aplica todas las directivas personalizadas relacionadas con los metadatos y no con el propio contenido. Por ejemplo, una directiva que avisa cuando los archivos tienen un tamaño superior a 20 MB o una directiva que avisa cuando se guardan archivos docx en OneDrive. 

2. Si hay una directiva que requiere la inspección de contenido y el archivo cumple los requisitos para la inspección de contenido, el contenido se pone en cola para su inspección. La longitud de la cola depende del tamaño del inquilino y del número de archivos que deban examinarse. 

3. En este punto, puede ver el estado de la inspección de contenido. Para ello, vaya a **Investigar** > **Archivos** y haga clic en un archivo. En el cajón de archivos que se abre con los detalles del archivo en cuestión, la opción **Estado de inspección de contenido** mostrará los estados **Completado**, **Pendiente** o **No disponible**, en caso de que el tipo de archivo no se admita, o bien un mensaje de error. Para obtener más información sobre los mensajes de error relacionados con la inspección de contenido, consulte [Solucionar problemas relacionados con la inspección de contenido](troubleshooting-content-inspection.md).

> [!NOTE]
> Si observa un guión en el estado del examen, significará que el archivo no está en la cola de examen. Consulte las [directivas de archivos](data-protection-policies.md) para obtener más información sobre cómo establecer directivas de inspección de contenido.

Las directivas de inspección de contenido integradas pueden buscar la siguiente información:

- Direcciones de correo electrónico 
- Números de tarjeta de crédito 
  - Todas las compañías de tarjetas de crédito (Visa, MasterCard, American Express, Diners Club, Discover, JCB, Dankort, UnionPay, etc.) 
  - Delimitadores de espacio, punto o guión
  - Este examen también incluye la validación Luhn.
- Códigos SWIFT
- Números de pasaportes internacionales
- Números de permisos de conducir
- Fechas
- Números de tránsito de enrutamiento bancario de ABA
- Códigos de identificación bancarios
- Números de reclamación de seguros de salud de HICN de la HIPAA
- Números de identificación de proveedores nacionales de NPI de la HIPPA
- Nombres completos y fechas de nacimiento de PHI
- Documentos de identificación de California o números de permisos de conducir
- Números de permisos de conducir
- Direcciones particulares
- Tarjetas de pasaporte
- Números de la seguridad social



## <a name="see-also"></a>Consulte también  
[Controlar las aplicaciones en la nube con directivas](control-cloud-apps-with-policies.md)   
[Para obtener soporte técnico, visite la página de soporte técnico asistido de Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Los clientes Premier también pueden elegir Cloud App Security directamente desde el Portal Premier.](https://premier.microsoft.com/)  
  


<!--HONumber=Nov16_HO5-->


