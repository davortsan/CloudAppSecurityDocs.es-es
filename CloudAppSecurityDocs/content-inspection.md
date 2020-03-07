---
title: Cómo realiza Cloud App Security la inspección de contenido
description: En este artículo se describe el proceso Cloud App Security sigue al realizar la inspección de contenido de DLP en los datos de la nube.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 1/6/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 83969121e83bfa2efae352fc66de00766c23e5d9
ms.sourcegitcommit: 445a7c208455e6ce2c4e13b028c811f4c3486290
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2020
ms.locfileid: "78342089"
---
# <a name="content-inspection"></a>Inspección de contenido

*Se aplica a: Microsoft Cloud App Security*

Si habilita la inspección de contenido, puede optar por usar expresiones preestablecidas o buscar otras expresiones personalizadas.

Puede especificar una expresión regular para excluir un archivo de los resultados. Esta opción es muy útil si tiene un estándar de palabra clave de clasificación interna que desea excluir de la Directiva.

Puede decidir establecer el número mínimo de infracciones de contenido que desea que coincidan antes de que el archivo se considere una infracción. Por ejemplo, puede elegir 10 Si desea recibir alertas sobre archivos con al menos 10 números de tarjeta de crédito en su contenido.

Cuando el contenido se compara con la expresión seleccionada, el texto de la infracción se reemplaza por caracteres "X". De forma predeterminada, las infracciones se enmascaran y se muestran en su contexto mostrando 100 caracteres antes y después de la infracción. Los números en el contexto de la expresión se reemplazan por caracteres "#" y nunca se almacenan dentro de Cloud App Security. Puede seleccionar la opción de **desenmascarar los últimos cuatro caracteres de una infracción** para desenmascarar los últimos cuatro caracteres de la infracción. Es necesario establecer qué tipos de datos busca la expresión regular: contenido, metadatos o nombre de archivo. De forma predeterminada, busca en el contenido y los metadatos.

## <a name="content-inspection-for-protected-files"></a>Inspección de contenido para archivos protegidos

Cloud App Security permite a los administradores conceder Cloud App Security permiso para descifrar archivos cifrados y buscar infracciones en el contenido.

Con el fin de proporcionar a Cloud App Security los permisos necesarios:

1. Vaya a **configuración** y, a continuación, **Azure Information Protection**.
2. Habilitar **inspeccionar archivos protegidos.**
3. Siga las indicaciones para permitir los permisos necesarios en Azure Active Directory.
4. Puede configurar las opciones por directiva de archivo para determinar qué directivas analizarán los archivos protegidos.

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Controlar las aplicaciones en la nube con directivas](control-cloud-apps-with-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]
