---
title: API de archivos Cloud App Security
description: En este artículo se proporciona información sobre el uso de la API de archivos.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 03/27/2020
ms.topic: reference
ms.collection: M365-security-compliance
ms.service: cloud-app-security
ms.suite: ems
ms.openlocfilehash: 6ad05db0010fd9a050a13cfddf19071204ef1977
ms.sourcegitcommit: 288f3011c0ce0e5f2d8cbaa9057a63be044465f7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/09/2020
ms.locfileid: "94375078"
---
# <a name="files-api"></a>API de archivos

[!INCLUDE [Banner for top of topics](includes/banner.md)]

> [!NOTE]
>
> - Esta API estará en desuso pronto. Microsoft Cloud App Security está desarrollando una nueva solución para identificar y actuar sobre los archivos que infringen las directivas.
> - Esta API no está disponible para Office 365 Cloud App Security.

La API de archivos proporciona metadatos sobre los archivos y las carpetas almacenados en las aplicaciones en la nube, como la fecha de la última modificación, la propiedad, etc.

A continuación se enumeran las solicitudes admitidas:

- [Enumerar archivos](api-files-list.md)
- [Archivo de captura](api-files-fetch.md)

## <a name="filters"></a>Filtros

Para obtener información sobre cómo funcionan los filtros, vea [filtros](api-introduction.md#filters).

En la tabla siguiente se describen los filtros admitidos:

| Filtrar | Tipo | Operadores | Descripción |
| --- | --- | --- | --- |
| service | integer | EQ, Neq | Filtre los archivos del appID de la aplicación especificada, por ejemplo: 11770 |
| instance | integer | EQ, Neq | Filtrar archivos de instancias especificadas |
| fileType | integer | EQ, Neq | Filtre los archivos con el tipo de archivo especificado. Los valores posibles son:<br /><br />**0** : otros<br />**1** : documento<br />**2** : hoja de cálculo<br />**3** : presentación<br />**4** : texto<br />**5** : imagen<br />**6** : carpeta |
| allowDeleted | boolean | eq | Los valores posibles son:<br /><br />**true** : devuelve los archivos eliminados<br />**false** o Not Set: devuelve archivos no eliminados (incluidos los de la papelera). Se reemplazará por el operador de basura |
| policy | string | cabinetmatchedrulesequals, Neq, isset, isnotset | Filtrar actividades relacionadas con las directivas especificadas |
| filename | string | eq | Filtrar archivos por nombre de archivo |
| modifiedDate | timestamp | LTE, GTE, intervalo, lte_ndays, gte_ndays | Filtrar archivos por la fecha en que se modificaron por última vez |
| createdDate | timestamp | LTE, GTE, intervalo | Filtrar archivos por la fecha en que se crearon |
| colaboradores. entidad | PK de entidad | EQ, Neq | Filtre los archivos compartidos con las entidades especificadas. Ejemplo: `[{ "id": "entity-id", "saas": 11161, "inst": 0 }]` |
| colaboradores. dominios | string | EQ, Neq | Filtrar archivos compartidos con dominios especificados |
| colaboradores. grupos | string | EQ, Neq | Filtrar archivos compartidos con grupos especificados |
| colaboradores. withDomain | string | EQ, Neq, DEQ | Filtrar archivos compartidos con dominios especificados |
| propietario. entidad | PK de entidad | EQ, Neq | Filtre los archivos que pertenecen a las entidades especificadas. Ejemplo: `[{ "id": "entity-id", "saas": 11161, "inst": 0 }]` |
| Owner. unidad organizativa | string | EQ, Neq | Filtrar archivos con propietarios de unidades organizativas especificadas |
| compartir | integer | EQ, Neq | Filtre los archivos con los niveles de uso compartido especificados. Los valores posibles son:<br /><br />**4** : público (Internet)<br />**3** : público<br />**2** : externo<br />**1** : interno<br />**0** : privado |
| fileId | string | EQ, Neq | Filtrar archivos por ID. de archivo |
| fileLabels | string | EQ, Neq, isset, isnotset | Archivos de filtro que contienen los identificadores de etiquetas de archivo (etiquetas) especificados |
| fileScanLabels | string | EQ, Neq, isset, isnotset | Archivos de filtro que contienen los identificadores de advertencia (etiquetas) de inspección de contenido especificados |
| extensión | string | EQ, Neq | Filtrar archivos por una extensión de archivo determinada |
| mimeType | string | EQ, Neq | Filtrar archivos por un tipo MIME determinado, debe ser una cadena única |
| con la papelera | boolean | eq | Los valores posibles son:<br /><br />**true** : devuelve solo los archivos de la papelera<br />**false** : devuelve archivos no repuestos |
| parentFolder | folder | EQ, Neq | Filtrar archivos contenidos en las carpetas especificadas |
| folder | boolean | eq | Los valores posibles son:<br /><br />**true** : solo devuelve carpetas<br >**false** : solo devuelve archivos |
| en cuarentena | boolean | eq | Los valores posibles son:<br /><br />**true** : devuelve solo archivos en cuarentena<br />**false** : solo devuelve archivos que no están en cuarentena |
| snapshotLastModifiedDate | timestamp | LTE, GTE, intervalo | Filtrar archivos por la fecha en que se modificó por última vez su instantánea |

[!INCLUDE [Open support ticket](includes/support.md)]
