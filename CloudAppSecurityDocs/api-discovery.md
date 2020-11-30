---
title: API de Cloud Discovery de Cloud App Security
description: En este artículo se proporciona información sobre el uso de la API de Cloud Discovery.
ms.date: 03/27/2020
ms.topic: reference
ms.openlocfilehash: bf02c6a77cfaf165c4ae064c77012228846c44cf
ms.sourcegitcommit: d87372b47ca98e942c2bf94032a6a61902627d69
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/30/2020
ms.locfileid: "96314314"
---
# <a name="cloud-discovery-api"></a>API de Cloud Discovery

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Cloud Discovery analiza los registros del sistema proporcionados por el usuario para detectar aplicaciones nuevas y desconocidas en el entorno de nube. Use la API de Cloud Discovery para automatizar la carga de los archivos de registro de detección de su empresa. El proceso de carga de archivos consta de tres llamadas API a las que se debe llamar consecutivamente.

Además, Cloud App Security permite bloquear el acceso a aplicaciones no autorizadas mediante el uso de los dispositivos de seguridad locales existentes. Use la llamada generar script de bloque para obtener un script de bloque dedicado e importarlo en el dispositivo.

A continuación se enumeran las solicitudes admitidas:

- [Iniciación de la carga de archivos](api-discovery-initiate.md)
- [Realización de la carga de archivos](api-discovery-perform.md)
- [Finalización de la carga de archivos](api-discovery-finalize.md)
- [Generación de scripts de bloques](api-discovery-script.md)

[!INCLUDE [Open support ticket](includes/support.md)]
