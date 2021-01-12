---
title: API de enriquecimiento de datos de Cloud App Security
description: En este artículo se proporciona información sobre el uso de la API de enriquecimiento de datos.
ms.date: 12/13/2020
ms.topic: reference
ms.openlocfilehash: d2050afec68bc29b0f401188b60c3dbb631a4a1b
ms.sourcegitcommit: 0768aa1992819e2651a14a731f79e178fdececc5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/12/2021
ms.locfileid: "98114758"
---
# <a name="data-enrichment-api"></a>API de enriquecimiento de datos

[!INCLUDE [Banner for top of topics](includes/banner.md)]

La API de enriquecimiento de datos permite administrar intervalos de direcciones IP identificables, como las direcciones IP de la oficina física. Los intervalos de direcciones IP permiten etiquetar, clasificar y personalizar la forma en que los registros y alertas se muestran e investigan. Para obtener más información, vea [trabajar con etiquetas y intervalos IP](ip-tags.md).

A continuación se enumeran las solicitudes admitidas:

- [Enumerar intervalos de direcciones IP](api-data-enrichment-list.md)
- [Actualización del intervalo de direcciones IP](api-data-enrichment-create.md)
- [Actualización del intervalo de direcciones IP](api-data-enrichment-update.md)
- [Eliminación del intervalo de direcciones IP](api-data-enrichment-delete.md)

## <a name="properties"></a>Propiedades

El objeto de respuesta define las siguientes propiedades.

| Propiedad. | Tipo | Descripción |
| --- | --- | --- |
| total | int | Número total de registros |
| hasNext | bool | Indica si hay registros adicionales |
| datos | list | Lista de los registros existentes |
| _id | string | Identificador único del intervalo de direcciones IP |
| name | string | Nombre único del intervalo. |
| subredes | list | Una matriz de máscaras, direcciones IP (IPv4/IPv6) y cadenas originales |
| ubicación | string | Objeto que incluye el nombre de la ubicación, la latitud, la longitud, el código de país y el nombre del país. |
| organization | string | El ISP registrado |
| etiquetas| list | Una matriz de objetos nuevos o existentes, incluidos el nombre de etiqueta, el identificador, la descripción, la plantilla de nombre y el identificador de inquilino. |
| category | int | La categoría del intervalo IP. Proporcionar una categoría le ayuda a reconocer fácilmente las actividades de las direcciones IP interesantes. Los valores posibles son:<br /><br />**1**: empresa<br />**2**: administración<br />**3**: arriesgado<br />**4**: VPN<br />**5**: proveedor de la nube<br />**6**: otros |
| lastModified | long | Marca de tiempo de la última regla modificada |

## <a name="filters"></a>Filtros

Para obtener información sobre cómo funcionan los filtros, vea [filtros](api-introduction.md#filters).

En la tabla siguiente se describen los filtros admitidos:

| Filter | Tipo | Operadores | Descripción |
| --- | --- | --- | --- |
| category | integer | EQ, Neq | Filtrar intervalos IP por categoría. Los valores posibles son:<br /><br />**1**: empresa<br />**2**: administración<br />**3**: arriesgado<br />**4**: VPN<br />**5**: proveedor de la nube<br />**6**: otros |
| etiquetas | string | EQ, Neq | Filtrar intervalos IP por ID. de etiqueta |
| builtIn | bool | eq | Filtrar intervalos IP por tipo. Los valores posibles son: **true** (integrado) o **false** (personalizado). |

[!INCLUDE [Open support ticket](includes/support.md)]
