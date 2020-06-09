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
ms.openlocfilehash: 0363d275c764d1e92d8d3f295de82e0c5bd2143a
ms.sourcegitcommit: 286f8d5d940d1bb9a09daa3070ac4fc3768208f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/08/2020
ms.locfileid: "84505444"
---
# <a name="alerts-api"></a>API de alertas

*Se aplica a: Microsoft Cloud App Security*

La API de alertas proporciona información acerca de los riesgos inmediatos identificados por Cloud App Security y que requieren atención. Las alertas pueden ser consecuencia de patrones de uso sospechosos o de archivos que contienen contenido que infringe la Directiva de la empresa.

A continuación se enumeran las solicitudes admitidas:

- [Mostrar alertas](api-alerts-list.md)
- [Descartar de forma masiva](api-alerts-bulk-dismiss.md)
- [Resolución masiva](api-alerts-bulk-resolve.md)
- [Capturar alerta](api-alerts-fetch.md)
- [Descartar alerta](api-alerts-dismiss.md)
- [Marcar alerta como leída](api-alerts-mark-read.md)
- [Marcar alerta como no leída](api-alerts-mark-unread.md)

## <a name="filters"></a>Filtros

Para obtener información sobre cómo funcionan los filtros, vea [filtros](api-introduction.md#filters).

En la tabla siguiente se describen los filtros admitidos:

| Filter | Tipo | Operadores | Descripción |
| --- | --- | --- | --- |
| Entity. Entity | PK de entidad | EQ, Neq | Filtre las alertas relacionadas con las entidades especificadas. Ejemplo: `[{ "id": "entity-id", "saas": 11161, "inst": 0 }]` |
| entidad. IP | string | EQ, Neq | Filtrar las alertas relacionadas con las direcciones IP especificadas |
| Entity. Service | integer | EQ, Neq | Filtrar las alertas relacionadas con el appId de servicio especificado, por ejemplo: 11770 |
| entidad. instancia | integer | EQ, Neq | Filtrar las alertas relacionadas con las instancias especificadas; por ejemplo: 11770, 1059065 |
| entidad. Directiva | string | EQ, Neq | Filtrar las alertas relacionadas con las directivas especificadas |
| Entity. File | string | EQ, Neq | Filtrar las alertas relacionadas con el archivo especificado |
| severity | integer | EQ, Neq | Filtre por gravedad. Los valores posibles son:<br /><br />**0**: bajo<br />**1**: medio<br/>**2**: alto |
| resolutionStatus | integer | EQ, Neq | Filtrar por estado de resolución de alerta, los valores posibles incluyen:<br /><br />**0**: abrir<br />**1**: descartado<br />**2**: resuelto |
| leer | boolean | eq | Si se establece en "true", solo devuelve alertas de lectura, si se establece en "false", devuelve alertas no leídas. |
| date | timestamp | LTE, GTE, intervalo, lte_ndays, gte_ndays | Filtrar por la hora a la que se desencadenó una alerta |
| resolutionDate | timestamp | LTE, GTE, intervalo | Filtrar por la hora en que se resolvió una alerta |
| riesgo | integer | EQ, Neq | Filtrar por riesgo |
| alertType | integer | EQ, Neq | Filtrar por tipo de alerta |
| id | string | EQ, Neq | Filtrar por ID. de alerta |
| source | string | eq | El origen de la alerta, ya sea integrada o Directiva |

[!INCLUDE [Open support ticket](includes/support.md)]
