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
ms.openlocfilehash: 9b6d7c4428b8383a4107a824a6113fcd3362dfa1
ms.sourcegitcommit: 575f2b2efa9ca4477d7e60271d21e225ef2c38ea
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/22/2020
ms.locfileid: "90881092"
---
# <a name="entities-api"></a>Entities API

[!INCLUDE [Banner for top of topics](includes/banner.md)]

> [!NOTE]
> Esta API no está disponible para Office 365 Cloud App Security.

La API de entidades proporciona información básica sobre los usuarios y las cuentas que usan las aplicaciones en la nube de su organización, lo que le permite comprender los patrones de uso del servicio.

A continuación se enumeran las solicitudes admitidas:

- [Listar entidades](api-entities-list.md)
- [Captura de entidades](api-entities-fetch.md)
- [Captura de árboles de entidades](api-entities-fetch-tree.md)

## <a name="filters"></a>Filtros

Para obtener información sobre cómo funcionan los filtros, vea [filtros](api-introduction.md#filters).

En la tabla siguiente se describen los filtros admitidos:

| Filtrar | Tipo | Operadores | Descripción |
| --- | --- | --- | --- |
| type| string | EQ, Neq | Filtrar entidades por su tipo |
| isAdmin | string | eq | Filtrar entidades que son administradores |
| Entidad | PK de entidad | EQ, Neq | Filtre las entidades con entidades específicas PKS. Si se selecciona un usuario, también devolverá todas sus cuentas. Ejemplo: `[{ "id": "entity-id", "saas": 11161, "inst": 0 }]` |
| userGroups |string | EQ, Neq | Filtrar entidades por sus identificadores de grupo asociados |
| app | Entero | EQ, Neq | Filtrar entidades mediante servicios con el identificador de SaaS especificado, por ejemplo: 11770 |
| instance | Entero | EQ, Neq | Filtre las entidades mediante servicios con el Appstances especificado (identificador de SaaS e identificador de instancia), por ejemplo: 11770, 1059065 |
| isExternal | boolean | eq | Afiliación de la entidad. Los valores posibles son:<br /><br />**true**: External<br />**false**: interno<br />**null**: ningún valor |
| dominio | string | EQ, Neq, isset, isnotset | Dominio relacionado de la entidad |
| organization | string | EQ, Neq, isset, isnotset | Filtrar entidades con la unidad organizativa especificada |
| lastSeen | timestamp | LTE, GTE, | entidades de filtro de intervalo que se han detectado por última vez entre las fechas dadas |
| status | string | EQ, Neq | Filtre las entidades por estado. Los valores posibles son:<br /><br />**0**: N/A<br />**1**: almacenado provisionalmente<br />**2**: activo<br />**3**: suspendido<br />**4**: eliminado |
| score | Entero | lt, gt, isset, isnotset | Filtrar entidades por su puntuación de prioridad de investigación |

[!INCLUDE [Open support ticket](includes/support.md)]
