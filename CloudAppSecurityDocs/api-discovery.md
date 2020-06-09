---
title: API de Cloud Discovery de Cloud App Security
description: En este artículo se proporciona información sobre el uso de la API de Cloud Discovery.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 03/27/2020
ms.topic: reference
ms.collection: M365-security-compliance
ms.service: cloud-app-security
ms.suite: ems
ms.openlocfilehash: 647570edd98fd1fd4977a9096fcf475f3ee09a8e
ms.sourcegitcommit: 286f8d5d940d1bb9a09daa3070ac4fc3768208f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/08/2020
ms.locfileid: "84505254"
---
# <a name="cloud-discovery-api"></a>API de Cloud Discovery

*Se aplica a: Microsoft Cloud App Security*

Cloud Discovery analiza los registros del sistema proporcionados por el usuario para detectar aplicaciones nuevas y desconocidas en el entorno de nube. Use la API de Cloud Discovery para automatizar la carga de los archivos de registro de detección de su empresa. El proceso de carga de archivos consta de tres llamadas API a las que se debe llamar consecutivamente.

Además, Cloud App Security permite bloquear el acceso a aplicaciones no autorizadas mediante el uso de los dispositivos de seguridad locales existentes. Use la llamada generar script de bloque para obtener un script de bloque dedicado e importarlo en el dispositivo.

A continuación se enumeran las solicitudes admitidas:

- [Iniciar carga de archivos](api-discovery-initiate.md)
- [Realizar la carga de archivos](api-discovery-perform.md)
- [Finalizar carga de archivos](api-discovery-finalize.md)
- [Generar script de bloque](api-discovery-script.md)

[!INCLUDE [Open support ticket](includes/support.md)]
