---
title: API de Cloud App Security entidades
description: En este artículo se proporciona información sobre el uso de la API de entidades.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 03/27/2020
ms.topic: reference
ms.collection: M365-security-compliance
ms.service: cloud-app-security
ms.suite: ems
ms.openlocfilehash: d55eb6d29586ba68cb46bd97b6718529da87ea51
ms.sourcegitcommit: 286f8d5d940d1bb9a09daa3070ac4fc3768208f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/08/2020
ms.locfileid: "84505224"
---
# <a name="entities-api"></a>API Entities

*Se aplica a: Microsoft Cloud App Security*

> [!NOTE]
> Esta API no está disponible para Office 365 Cloud App Security.

La API de entidades proporciona información básica sobre los usuarios y las cuentas que usan las aplicaciones en la nube de su organización, lo que le permite comprender los patrones de uso del servicio.

A continuación se enumeran las solicitudes admitidas:

- [Listar entidades](api-entities-list.md)
- [Capturar entidad](api-entities-fetch.md)
- [Capturar árbol de entidades](api-entities-fetch-tree.md)

## <a name="filters"></a>Filtros

Para obtener información sobre cómo funcionan los filtros, vea [filtros](api-introduction.md#filters).

En la tabla siguiente se describen los filtros admitidos:

| Filter | Tipo | Operadores | Descripción |
| --- | --- | --- | --- |
| type| cadena | EQ, Neq | Filtrar entidades por su tipo |
| isAdmin | string | eq | Filtrar entidades que son administradores |
| Entidad | PK de entidad | EQ, Neq | Filtre las entidades con entidades específicas PKS. Si se selecciona un usuario, también devolverá todas sus cuentas. Ejemplo: `[{ "id": "entity-id", "saas": 11161, "inst": 0 }]` |
| userGroups |string | EQ, Neq | Filtrar entidades por sus identificadores de grupo asociados |
| app | integer | EQ, Neq | Filtrar entidades mediante servicios con el identificador de SaaS especificado, por ejemplo: 11770 |
| instance | integer | EQ, Neq | Filtre las entidades mediante servicios con el Appstances especificado (identificador de SaaS e identificador de instancia), por ejemplo: 11770, 1059065 |
| isExternal | boolean | eq | Afiliación de la entidad. Los valores posibles son:<br /><br />**true**: External<br />**false**: interno<br />**null**: ningún valor |
| dominio | string | EQ, Neq, isset, isnotset | Dominio relacionado de la entidad |
| organization | string | EQ, Neq, isset, isnotset | Filtrar entidades con la unidad organizativa especificada |
| lastSeen | timestamp | LTE, GTE, | entidades de filtro de intervalo que se han detectado por última vez entre las fechas dadas |
| status | string | EQ, Neq | Filtre las entidades por estado. Los valores posibles son:<br /><br />**0**: N/A<br />**1**: almacenado provisionalmente<br />**2**: activo<br />**3**: suspendido<br />**4**: eliminado |
| score | integer | lt, gt, isset, isnotset | Filtrar entidades por su puntuación de prioridad de investigación |

[!INCLUDE [Open support ticket](includes/support.md)]
