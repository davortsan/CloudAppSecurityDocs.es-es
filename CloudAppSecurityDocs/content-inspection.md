---
title: "Inspección de contenido | Microsoft Docs"
description: "En este artículo se describe el proceso que Cloud App Security sigue al realizar la inspección de contenido de DLP en los datos en la nube."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 10/15/2016
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: 2401adbc-0011-4938-9e3a-a4c719a2f619
ms.reviewer: reutam
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: ed4ea71b24767d3602d40894d1cbac7447bcd8a2
ms.openlocfilehash: ea1854d6bf32e01afe6183409b68ded32ee37dd1


---

# <a name="content-inspection"></a>Inspección de contenido
En este artículo se describe el proceso que Cloud App Security sigue al realizar la inspección de contenido de DLP en los datos en la nube. 


La inspección de contenido de Cloud App Security funciona de la manera siguiente:
1. Cloud App Security realiza un examen continuo de todos los archivos pertinentes de todas las unidades. 
2. Cloud App Security realiza un examen prácticamente en tiempo real (NRT) de las unidades y los eventos que se identifican como nuevos o modificados. 

Tanto los archivos del examen continuo como los archivos del examen NRT se agregan a la cola para su inspección. El orden de los archivos colocados en la cola para su examen se establece por actividad en los archivos y en el examen de las unidades. Los archivos se examinan únicamente si los metadatos de archivo muestran que es un tipo MIME admitido. Tenga en cuenta que este examen se aplica a archivos pertinentes para el examen de datos (documentos, imágenes, presentaciones, hojas de cálculo, archivos de texto y archivos de almacenamiento o ZIP).  

Después de examinar un archivo, ocurre lo siguiente:

1. Cloud App Security aplica todas las directivas personalizadas relacionadas con los metadatos y no con el propio contenido. Por ejemplo, una directiva que avisa cuando los archivos tienen un tamaño superior a 20 MB o una directiva que avisa cuando se guardan archivos docx en OneDrive. 

2. Si hay una directiva que requiere la inspección de contenido y el archivo cumple los requisitos para la inspección de contenido, el contenido se pone en cola para su inspección. La longitud de la cola depende del tamaño del inquilino y del número de archivos que deban examinarse. 

3. En este punto, puede ver el estado de la inspección de contenido. Para ello, vaya a **Investigar** > **Archivos** y haga clic en un archivo. En el cajón de archivos que se abre con los detalles del archivo, en el estado de **Inspección de contenido** se mostrará uno de los siguientes elementos: 

|Estado de la inspección de contenido|Descripción|
|----|----|
|Completed|La inspección de contenido se completó correctamente.|
|No disponible|La inspección de contenido no es aplicable para este archivo. Esto puede deberse a que no hay ninguna directiva que requiera la inspección de contenido de este archivo o a que no se admite el tipo de archivo.|
|Pending|El archivo está actualmente en la cola de inspección de contenido.|
|Error: Error de descarga|Cloud App Security no pudo descargar el archivo para la inspección.|
|Error: Archivo cifrado|El archivo no se pudo descifrar.|
|Error: El archivo está dañado|El archivo está dañado de algún modo y no se pudo inspeccionar.|
|Error: Error interno.|Se produjo un problema indeterminado al intentar inspeccionar el archivo.|
|Error: Error de DLP externo|Se produjo un error en la DLP externa y Cloud App Security no pudo inspeccionar el contenido.|
|Error: Se ha excedido el tamaño de archivo|El límite de archivo varía según el tamaño del archivo y el número de caracteres.|
|Error: Acceso denegado al archivo|El archivo es externo a la nube y Cloud App Security no pudo acceder a él.|
|Error: Archivo eliminado|El archivo ya no existe en la nube y no se pudo inspeccionar.|
|Error: Tipo de archivo no admitido|Cloud App Security no puede inspeccionar el contenido de este tipo de archivo. Esto puede deberse a que no se admite el tipo de archivo o a que el archivo no se encuentra realmente en el formato del tipo de archivo esperado.|

## <a name="see-also"></a>Consulte también  
[Controlar las aplicaciones en la nube con directivas](control-cloud-apps-with-policies.md)   
[Para obtener soporte técnico, visite la página de soporte técnico asistido de Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Los clientes Premier también pueden elegir Cloud App Security directamente desde el Portal Premier.](https://premier.microsoft.com/)  
  


<!--HONumber=Oct16_HO4-->


