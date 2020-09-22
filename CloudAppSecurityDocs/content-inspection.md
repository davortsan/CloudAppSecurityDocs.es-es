---
title: Cómo Cloud App Security realiza la inspección de contenido de DLP
description: En este artículo se describe el proceso que Cloud App Security sigue al realizar la inspección de contenido de DLP en los datos en la nube.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 1/6/2019
ms.topic: how-to
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 0845fdb1e9258dfa84162c01daa52ec78f3c7e1f
ms.sourcegitcommit: 575f2b2efa9ca4477d7e60271d21e225ef2c38ea
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/22/2020
ms.locfileid: "90881231"
---
# <a name="content-inspection"></a>Inspección de contenido

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Si habilita la inspección de contenido, puede optar entre usar expresiones preestablecidas o buscar otras expresiones personalizadas.

Puede especificar una expresión regular para excluir un archivo de los resultados. Esta opción es muy útil si tiene un estándar de palabra clave de clasificación interna que quiera excluir de la directiva.

También puede decidir cuál es el número mínimo de infracciones de contenido que debe producirse antes de que el archivo se considere una infracción. Por ejemplo, puede elegir 10 si quiere recibir alertas sobre archivos con al menos 10 números de tarjeta de crédito en su contenido.

Cuando el contenido se compare con la expresión seleccionada, el texto de la infracción se reemplazará por caracteres "X". De manera predeterminada, las infracciones se enmascaran y se muestran en su contexto mostrando 100 caracteres antes y después de la infracción. Los números en el contexto de la expresión se reemplazan por caracteres "#" y nunca se almacenan dentro de Cloud App Security. Puede seleccionar la opción de **quitar la máscara de los últimos cuatro caracteres de una infracción** para mostrarlos. Es necesario establecer qué tipos de datos buscará la expresión regular: contenido, metadatos o nombre de archivo. De forma predeterminada, buscará el contenido y los metadatos.

## <a name="content-inspection-for-protected-files"></a>Inspección de contenido para archivos protegidos

Cloud App Security permite a los administradores conceder permiso a Cloud App Security para descifrar archivos cifrados y examinar su contenido en busca de infracciones.

Para dar Cloud App Security los permisos necesarios:

1. Vaya a **Configuración** y, a continuación, a **Azure Information Protection**.
2. Habilite **Inspeccionar archivos protegidos**.
3. Siga las indicaciones para permitir los permisos requeridos en Azure Active Directory.
4. Puede ajustar la configuración según la directiva de archivo para determinar qué directivas examinarán los archivos protegidos.

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Controlar las aplicaciones en la nube con directivas](control-cloud-apps-with-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]
