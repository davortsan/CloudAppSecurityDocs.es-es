---
title: API de Cloud App Security actividades
description: En este artículo se proporciona información sobre el uso de la API de actividades.
ms.date: 03/27/2020
ms.topic: reference
ms.openlocfilehash: 501d8a5ccaad1673c34aa0367f06531de94035b5
ms.sourcegitcommit: d87372b47ca98e942c2bf94032a6a61902627d69
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/30/2020
ms.locfileid: "96314688"
---
# <a name="activities-api"></a>API de actividades

[!INCLUDE [Banner for top of topics](includes/banner.md)]

La API de actividad le permite ver todas las acciones realizadas en las aplicaciones en la nube. Los datos de esta API pueden proporcionar información sobre quién inicia sesión en qué aplicación y cuándo, qué archivos se descargan desde ubicaciones sospechosas, etc.

A continuación se enumeran las solicitudes admitidas:

- [Enumeración de actividades](api-activities-list.md)
- [Captura de actividades](api-activities-fetch.md)
- [Comentarios sobre actividades](api-activities-feedback.md)

## <a name="filters"></a>Filtros

Para obtener información sobre cómo funcionan los filtros, vea [filtros](api-introduction.md#filters).

En la tabla siguiente se describen los filtros admitidos:

| Filtrar | Tipo | Operadores | Descripción |
| --- | --- | --- | --- |
| service | integer | EQ, Neq | Filtre las actividades relacionadas con el appID de servicio especificado, por ejemplo: 11770 |
| instance | integer | EQ, Neq | Filtrar actividades de instancias especificadas |
| usuario. unidad organizativa | string | EQ, Neq, isset, isnotset | Filtrar actividades por la unidad organizativa del usuario que realiza la operación |
| Activity. eventType | string | EQ, Neq | Filtrar actividades por tipo de evento |
| activity.id | string | eq | Buscar una actividad por identificador |
| Activity. suplantado | boolean | eq | Si se establece en "true", solo devuelve eventos suplantados, si se establece en "false", devuelve eventos no suplantados |
| Activity. Type | boolean | eq | Si se establece en "true", solo devuelve eventos de administrador, si se establece en "false", devuelve eventos regulares |
| Activity. takenAction | string | EQ, Neq | Filtre las actividades por las acciones realizadas en ellas. Los valores posibles son:<br /><br />**bloquear**: bloqueado<br />**proxy**: redirigido al control de sesión<br />**BypassProxy**: omitir el control de sesión<br />**cifrado**: cifrado<br />**descifrado**: descifrado<br />**verificado**: comprobado<br />**encryptionFailed**: error de cifrado<br />**proteger**: protegido<br />**comprobar**: requerir autenticación paso a paso<br />**null**: ninguna acción |
| Device. Type | string | EQ, Neq | Filtre las actividades por tipo de dispositivo. Los valores posibles son:<br /><br />**escritorio**: PC<br />**Móvil**: móvil<br />**Tableta**: tableta<br />**Otros**: otros<br />**null**: ningún valor |
| Device. Tags | string | EQ, Neq | Filtrar actividades por ID. de etiquetas de dispositivo |
| userAgent. userAgent | string | Contains, ncontains | Filtrar las actividades que realizan o no contienen las cadenas especificadas en el agente de usuario |
| userAgent. Tags | string | EQ, Neq | Filtrar actividades que contienen los identificadores de etiquetas de agente de usuario especificados |
| Ubicación. país | string | EQ, Neq, isset, isnotset | Filtrar actividades que se originan en el código de país o región especificado |
| Ubicación. organizaciones | string | EQ, Neq, isset, isnotset, Contains | Filtrar actividades procedentes de la organización especificada |
| Dirección IP. | string | EQ, StartsWith, doesnotstartwith, isset, isnotset, Neq | Filtrar actividades que se originan en la dirección IP determinada |
| fileSelector | archivo | EQ, Neq | Filtrar las actividades que contienen el archivo o carpeta especificados |
| office365url | string | StartsWith, EQ, EndsWith | Filtrar actividades por direcciones URL de Office 365 |
| fileId | string | eq | Buscar un archivo por identificador |
| IP. categoría | integer | EQ, Neq | Filtre las actividades con las categorías de subred especificadas. Los valores posibles son:<br /><br />**1**: empresa<br />**2**: administración<br />**3**: arriesgado<br />**4**: VPN<br />**5**: proveedor de la nube<br />**6**: otros |
| IP. Tags | string | EQ, Neq | Filtrar actividades por ID. de etiquetas IP |
| text | string | EQ, startswithsingle, texto | Filtrar actividades realizando una búsqueda de texto libre |
| date | timestamp | LTE, GTE, intervalo, lte_ndays, gte_ndays | Filtrar las actividades que se produjeron en el intervalo de tiempo especificado |
| policy | string | EQ, Neq, isset, isnotset | Filtrar actividades relacionadas con las directivas especificadas |
| source | string | EQ, Neq | Filtrar todas las actividades por tipo de origen o ID. de secuencia. Ejemplo: `[{ "s:stream-id", "t:source-type" }]` los valores de tipo de origen posibles incluyen:<br /><br />**0**: control de acceso<br />**1**: control de sesión<br />**2**: conector de aplicaciones<br />**3**: análisis del conector de aplicaciones<br />**5**: detección<br />**6**: MDATP |
| Activity. alertId | string | eq | Filtrar todas las actividades relevantes para un ID. de alerta |
| activityObject | string | EQ, Neq | Filtrar las actividades que contienen el identificador especificado |
| fileLabels | string | EQ, Neq | Archivos de filtro que contienen los identificadores de etiquetas de archivo (etiquetas) especificados |
| created || LTE, GTE, intervalo, gt, lt, EQ | Filtrar actividades creadas en el intervalo de tiempo especificado |
| Entidad | PK de entidad | EQ, Neq, isset, isnotset, StartsWith | Filtre las actividades por la entidad que llevó a cabo la actividad. Ejemplo: `[{ "id": "entity-id", "saas": 11161, "inst": 0 }]` |
| User. username | string | EQ, Neq, isset, isnotset, StartsWith | Filtrar actividades por el usuario que realizó la actividad |
| User. Tags | string | EQ, Neq, isset, isnotset, StartsWith | Filtre las actividades por etiquetas que pertenezcan al usuario que realiza la ejecución. Requiere ID. de grupo |
| usuario. dominio | string | EQ, Neq, isset, isnotset | Filtrar actividades por el dominio de usuario que realiza la operación |

[!INCLUDE [Open support ticket](includes/support.md)]
