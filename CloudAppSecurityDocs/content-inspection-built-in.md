---
title: Cómo realiza Cloud App Security la inspección de contenido
description: En este artículo se describe el proceso Cloud App Security sigue al realizar la inspección de contenido de DLP en los datos de la nube.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 12/10/2018
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 543631f5ffaa6716d8686e86e1386b55c081158b
ms.sourcegitcommit: 288c279a0d2dd62a8ad8d7425c3e9e98857bf5f4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/05/2020
ms.locfileid: "80666476"
---
# <a name="built-in-content-inspection"></a>Inspección de contenido integrado

*Se aplica a: Microsoft Cloud App Security*

En este artículo se describe el proceso Microsoft Cloud App Security siguiente al ejecutar la inspección de contenido DLP integrada en los datos de la nube.

Cloud App Security la inspección de contenido funciona de la siguiente manera:

1. En primer lugar, Cloud App Security realiza un análisis casi en tiempo real (NRT) de las unidades y los eventos que se detectan como nuevos o modificados.
2. Una vez completado el análisis, Cloud App Security realiza un examen continuo de todos los archivos relevantes en todas las unidades.

Los archivos del examen NRT y el examen continuo se agregan a la cola para su inspección. El orden de los archivos en la cola de examen se establece por actividad en los archivos y en el análisis de las unidades. Los archivos solo se analizan si los metadatos de archivo muestran que se trata de un tipo MIME admitido. Este análisis es para los archivos que son pertinentes para el examen de datos (documentos, imágenes, presentaciones, hojas de cálculo, texto y archivos zip/Archive).

Una vez que se ha analizado un archivo, se producen las siguientes acciones:

1. Cloud App Security aplica todas las directivas personalizadas relacionadas con los metadatos y no con el contenido en sí. Por ejemplo, una directiva que le avisa cuando los archivos tienen más de 20 MB o una directiva que le avisa cuando se guardan archivos docx en OneDrive.

2. Si hay una directiva que requiera la inspección de contenido y el archivo es apto para la inspección de contenido, el contenido se pone en cola para su inspección. La longitud de la cola depende del tamaño del inquilino y del número de archivos que requieren examen.

3. En este punto, puede ver el estado de la inspección de contenido; para ello, vaya a **investigar** > **archivos** y haga clic en un archivo. En el cajón de archivos que se abre con los detalles del archivo, el estado de la **inspección de contenido** mostrará **completado**, **pendiente**, **no aplicable** (si no se admite el tipo de archivo) o un mensaje de error. Para obtener información sobre los mensajes de error de examen de contenido, consulte [solución de problemas de inspección de contenido](troubleshooting-content-inspection.md).

> [!NOTE]
> Si ve un guión en el estado del examen, significa que el archivo no está en cola para su examen. Consulte [directivas de archivo](data-protection-policies.md) para obtener información sobre cómo establecer directivas de inspección de contenido.

Las directivas de análisis de inspección de contenido integradas pueden buscar los siguientes elementos:

- Direcciones de correo electrónico
- Números de tarjeta de crédito
  - Todas las empresas de tarjetas de crédito (Visa, MasterCard, American Express, Diners Club, Discover, JCB, Dankort, UnionPay)
  - Delimitadores: espacio, punto o guión
  - Este análisis también incluye la validación Luhn
- Códigos SWIFT
- Números de pasaporte internacionales
- Números de licencia de los controladores
- Fechas
- Números de tránsito del enrutamiento de ABA bancario
- Códigos de identificador bancario
- Números de la demanda de seguros de salud HICN Health
- Números de identificador de proveedor nacional de HIPAA NPI
- Nombre completo de PHI y fechas de nacimiento
- Números de licencia de ID. de California o de controladores
- Números de licencia de los controladores
- Direcciones particulares
- Tarjetas de Passport
- Números de la seguridad social

## <a name="supported-languages"></a>Idiomas compatibles

El motor de inspección de contenido de Cloud App Security:

- Admite todos los caracteres Unicode
- Trata sobre los tipos de archivo 100
- Se admiten varios idiomas, especialmente los archivos que utilizan juegos de caracteres Unicode. Asegúrese de definir las directivas para tener en cuenta esos idiomas. Por ejemplo, si busca palabras clave, debe incluir las palabras clave en los idiomas que desee usar.
- En los tipos de archivo basados en texto que usan codificación no Unicode, por ejemplo, Chino GB2312, la comparación con palabras clave de chino Unicode no funcionará según lo previsto.
- En el caso de los tipos de archivo que se basan en bibliotecas de terceros, es posible que las cadenas y palabras coincidentes no siempre funcionen según lo esperado. Esto es más común en los archivos (como los tipos de archivos binarios) en los que la inspección de contenido se basa en bibliotecas de terceros que devuelven cadenas de Java para conjuntos de caracteres y de idioma.

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Controlar las aplicaciones en la nube con directivas](control-cloud-apps-with-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]
