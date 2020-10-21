---
title: API de Cloud App Security alertas
description: En este artículo se proporciona información sobre el uso de la API de alertas.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 10/20/2020
ms.topic: reference
ms.collection: M365-security-compliance
ms.service: cloud-app-security
ms.suite: ems
ms.openlocfilehash: c5b927cf1cfaa1038b4b2ab1aa096978ec9c964c
ms.sourcegitcommit: ee40375712d2cc4090bd4e9cb58df486ec02aa62
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/21/2020
ms.locfileid: "92326949"
---
# <a name="alerts-api"></a>API de alertas

[!INCLUDE [Banner for top of topics](includes/banner.md)]

La API de alertas proporciona información acerca de los riesgos inmediatos identificados por Cloud App Security y que requieren atención. Las alertas pueden ser consecuencia de patrones de uso sospechosos o de archivos que contienen contenido que infringe la Directiva de la empresa.

A continuación se enumeran las solicitudes admitidas:

- [Mostrar alertas](api-alerts-list.md)
- [Cerrar benigno](api-alerts-close-benign.md)
- [Cerrar falso positivo](api-alerts-close-false-positive.md)
- [Cerrar verdadero positivo](api-alerts-close-true-positive.md)
- [Captura de alertas](api-alerts-fetch.md)
- [Marcación de alerta como leída](api-alerts-mark-read.md)
- [Marcación de alerta como no leída](api-alerts-mark-unread.md)

## <a name="deprecated-requests"></a>Solicitudes en desuso

En la tabla siguiente se enumeran las solicitudes desusadas como obsoletas y las que las sustituyen.

| Solicitud obsoleta | Alternativa |
| --- | --- |
| Descarte masivo | [Cerrar falso positivo](api-alerts-close-false-positive.md) |
| Resolución masiva | [Cerrar verdadero positivo](api-alerts-close-true-positive.md) |
| Descartar alerta | [Cerrar falso positivo](api-alerts-close-false-positive.md) |

> [!NOTE]
> Las solicitudes en desuso se han asignado a sus alternativas para evitar interrupciones. Sin embargo, si usa solicitudes obsoletas en su entorno, se recomienda actualizarlas a sus alternativas.

## <a name="filters"></a>Filtros

Para obtener información sobre cómo funcionan los filtros, vea [filtros](api-introduction.md#filters).

En la tabla siguiente se describen los filtros admitidos:

| Filter | Tipo | Operadores | Descripción |
| --- | --- | --- | --- |
| Entity. Entity | PK de entidad | EQ, Neq | Filtre las alertas relacionadas con las entidades especificadas. Ejemplo: `[{ "id": "entity-id", "saas": 11161, "inst": 0 }]` |
| entidad. IP | string | EQ, Neq | Filtrar las alertas relacionadas con las direcciones IP especificadas |
| Entity. Service | Entero | EQ, Neq | Filtrar las alertas relacionadas con el appId de servicio especificado, por ejemplo: 11770 |
| entidad. instancia | Entero | EQ, Neq | Filtrar las alertas relacionadas con las instancias especificadas; por ejemplo: 11770, 1059065 |
| entidad. Directiva | string | EQ, Neq | Filtrar las alertas relacionadas con las directivas especificadas |
| Entity. File | string | EQ, Neq | Filtrar las alertas relacionadas con el archivo especificado |
| severity | Entero | EQ, Neq | Filtre por gravedad. Entre los posibles valores se incluyen:<br /><br />**0**: bajo<br />**1**: medio<br/>**2**: alto |
| resolutionStatus | Entero | EQ, Neq | Filtrar por estado de resolución de alerta, los valores posibles incluyen:<br /><br />**0**: abrir<br />**1**: descartado<br />**2**: resuelto |
| leer | boolean | eq | Si se establece en "true", solo devuelve alertas de lectura, si se establece en "false", devuelve alertas no leídas. |
| date | timestamp | LTE, GTE, intervalo, lte_ndays, gte_ndays | Filtrar por la hora a la que se desencadenó una alerta |
| resolutionDate | timestamp | LTE, GTE, intervalo | Filtrar por la hora en que se resolvió una alerta |
| riesgo | Entero | EQ, Neq | Filtrar por riesgo |
| alertType | Entero | EQ, Neq | Filtrar por tipo de alerta |
| id | string | EQ, Neq | Filtrar por ID. de alerta |
| source | string | eq | El origen de la alerta, ya sea integrada o Directiva |

[!INCLUDE [Open support ticket](includes/support.md)]
