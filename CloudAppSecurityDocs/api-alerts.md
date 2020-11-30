---
title: API de Cloud App Security alertas
description: En este artículo se proporciona información sobre el uso de la API de alertas.
ms.date: 10/20/2020
ms.topic: reference
ms.openlocfilehash: 8ff6871cac8aa11678fc058bfdc328642ad70ba0
ms.sourcegitcommit: d87372b47ca98e942c2bf94032a6a61902627d69
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/30/2020
ms.locfileid: "96314552"
---
# <a name="alerts-api"></a>API de alertas

[!INCLUDE [Banner for top of topics](includes/banner.md)]

La API de alertas proporciona información acerca de los riesgos inmediatos identificados por Cloud App Security y que requieren atención. Las alertas pueden ser consecuencia de patrones de uso sospechosos o de archivos que contienen contenido que infringe la Directiva de la empresa.

A continuación se enumeran las solicitudes admitidas:

- [Enumeración de alertas](api-alerts-list.md)
- [Cerrar inofensivo](api-alerts-close-benign.md)
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

| Filtrar | Tipo | Operadores | Descripción |
| --- | --- | --- | --- |
| Entity. Entity | PK de entidad | EQ, Neq | Filtre las alertas relacionadas con las entidades especificadas. Ejemplo: `[{ "id": "entity-id", "saas": 11161, "inst": 0 }]` |
| entidad. IP | string | EQ, Neq | Filtrar las alertas relacionadas con las direcciones IP especificadas |
| Entity. Service | integer | EQ, Neq | Filtrar las alertas relacionadas con el appId de servicio especificado, por ejemplo: 11770 |
| entidad. instancia | integer | EQ, Neq | Filtrar las alertas relacionadas con las instancias especificadas; por ejemplo: 11770, 1059065 |
| entidad. Directiva | string | EQ, Neq | Filtrar las alertas relacionadas con las directivas especificadas |
| Entity. File | string | EQ, Neq | Filtrar las alertas relacionadas con el archivo especificado |
| alertOpen | boolean | eq | Si se establece en "true", solo devuelve alertas abiertas, si se establece en "false", solo devuelve alertas cerradas |
| severity | integer | EQ, Neq | Filtre por gravedad. Los valores posibles son:<br /><br />**0**: bajo<br />**1**: medio<br/>**2**: alto |
| resolutionStatus | integer | EQ, Neq | Filtrar por estado de resolución de alerta, los valores posibles incluyen:<br /><br />**0**: abrir <br />**1**: descartado (estado heredado)<br />**2**: resuelto (estado heredado)<br />**3**: cerrado como falso positivo<br />**4**: cerrado como benigno<br />**5**: cerrado como verdadero positivo |
| leer | boolean | eq | Si se establece en "true", solo devuelve alertas de lectura, si se establece en "false", devuelve alertas no leídas. |
| date | timestamp | LTE, GTE, intervalo, lte_ndays, gte_ndays | Filtrar por la hora a la que se desencadenó una alerta |
| resolutionDate | timestamp | LTE, GTE, intervalo | Filtrar por la hora en que se resolvió una alerta |
| riesgo | integer | EQ, Neq | Filtrar por riesgo |
| alertType | integer | EQ, Neq | Filtrar por tipo de alerta |
| id | string | EQ, Neq | Filtrar por ID. de alerta |
| source | string | eq | El origen de la alerta, ya sea integrada o Directiva |

[!INCLUDE [Open support ticket](includes/support.md)]
