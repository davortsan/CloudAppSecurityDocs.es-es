---
title: API de Cloud App Security alertas
description: En este artículo se proporciona información sobre el uso de la API de alertas.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 03/27/2020
ms.topic: reference
ms.collection: M365-security-compliance
ms.service: cloud-app-security
ms.suite: ems
ms.openlocfilehash: 54aa8efa3ad214ff55f3800ffb95126766e549e4
ms.sourcegitcommit: 575f2b2efa9ca4477d7e60271d21e225ef2c38ea
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/22/2020
ms.locfileid: "90880658"
---
# <a name="alerts-api"></a>API de alertas

[!INCLUDE [Banner for top of topics](includes/banner.md)]

La API de alertas proporciona información acerca de los riesgos inmediatos identificados por Cloud App Security y que requieren atención. Las alertas pueden ser consecuencia de patrones de uso sospechosos o de archivos que contienen contenido que infringe la Directiva de la empresa.

A continuación se enumeran las solicitudes admitidas:

- [Enumeración de alertas](api-alerts-list.md)
- [Descarte masivo](api-alerts-bulk-dismiss.md)
- [Resolución masiva](api-alerts-bulk-resolve.md)
- [Captura de alertas](api-alerts-fetch.md)
- [Descartar alerta](api-alerts-dismiss.md)
- [Marcación de alerta como leída](api-alerts-mark-read.md)
- [Marcación de alerta como no leída](api-alerts-mark-unread.md)

## <a name="filters"></a>Filtros

Para obtener información sobre cómo funcionan los filtros, vea [filtros](api-introduction.md#filters).

En la tabla siguiente se describen los filtros admitidos:

| Filtrar | Tipo | Operadores | Descripción |
| --- | --- | --- | --- |
| Entity. Entity | PK de entidad | EQ, Neq | Filtre las alertas relacionadas con las entidades especificadas. Ejemplo: `[{ "id": "entity-id", "saas": 11161, "inst": 0 }]` |
| entidad. IP | string | EQ, Neq | Filtrar las alertas relacionadas con las direcciones IP especificadas |
| Entity. Service | Entero | EQ, Neq | Filtrar las alertas relacionadas con el appId de servicio especificado, por ejemplo: 11770 |
| entidad. instancia | Entero | EQ, Neq | Filtrar las alertas relacionadas con las instancias especificadas; por ejemplo: 11770, 1059065 |
| entidad. Directiva | string | EQ, Neq | Filtrar las alertas relacionadas con las directivas especificadas |
| Entity. File | string | EQ, Neq | Filtrar las alertas relacionadas con el archivo especificado |
| severity | Entero | EQ, Neq | Filtre por gravedad. Los valores posibles son:<br /><br />**0**: bajo<br />**1**: medio<br/>**2**: alto |
| resolutionStatus | Entero | EQ, Neq | Filtrar por estado de resolución de alerta, los valores posibles incluyen:<br /><br />**0**: abrir<br />**1**: descartado<br />**2**: resuelto |
| leer | boolean | eq | Si se establece en "true", solo devuelve alertas de lectura, si se establece en "false", devuelve alertas no leídas. |
| date | timestamp | LTE, GTE, intervalo, lte_ndays, gte_ndays | Filtrar por la hora a la que se desencadenó una alerta |
| resolutionDate | timestamp | LTE, GTE, intervalo | Filtrar por la hora en que se resolvió una alerta |
| riesgo | Entero | EQ, Neq | Filtrar por riesgo |
| alertType | Entero | EQ, Neq | Filtrar por tipo de alerta |
| id | string | EQ, Neq | Filtrar por ID. de alerta |
| source | string | eq | El origen de la alerta, ya sea integrada o Directiva |

[!INCLUDE [Open support ticket](includes/support.md)]
