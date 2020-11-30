---
title: Cloud App Security API de REST
description: En este artículo se describe cómo interactuar con Cloud App Security a través de HTTPS.
ms.date: 03/27/2020
ms.topic: reference
ms.openlocfilehash: 468d039f6bc620616e86b98b4967a055c7d0e380
ms.sourcegitcommit: d87372b47ca98e942c2bf94032a6a61902627d69
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/30/2020
ms.locfileid: "96313991"
---
# <a name="cloud-app-security-rest-api"></a>Cloud App Security API de REST

[!INCLUDE [Banner for top of topics](includes/banner.md)]

En este artículo se describe cómo interactuar con Cloud App Security a través de HTTPS.

La API de Microsoft Cloud App Security proporciona acceso mediante programación a Cloud App Security a través de puntos de conexión de API de REST. Las aplicaciones pueden usar la API para realizar operaciones de lectura y actualización en objetos y datos de Cloud App Security. Por ejemplo, la API de Cloud App Security admite las siguientes operaciones comunes para un objeto de usuario:

- Cargar archivos de registro para Cloud Discovery
- Generar scripts de bloqueo
- Enumerar actividades y alertas
- Descartar o resolver alertas

## <a name="api-url-structure"></a>Estructura de la dirección URL de la API

Para usar la API de Cloud App Security, primero debe obtener la dirección URL de la API del inquilino. La dirección URL de la API usa el siguiente formato: `https://<portal_url>/api/<endpoint>` .

Para obtener la dirección URL del portal de Cloud App Security para su inquilino, siga estos pasos:

1. En el portal de Cloud App Security, haga clic en el **icono de signo de interrogación** en la barra de menús. Después, seleccione **Acerca de**.

    ![clic en Acerca de](media/about-menu.png)

1. En la pantalla Cloud App Security acerca de, puede ver la dirección URL del portal.

    ![Consultar el centro de datos](media/api-url.png)

Una vez que tenga la dirección URL del portal, agregue el `/api` sufijo para obtener la dirección URL de la API. Por ejemplo, si la dirección URL del portal es `https://mytenant.us2.contoso.com` , la dirección URL de la API es `https://mytenant.us2.contoso.com/api` .

## <a name="api-tokens"></a>Tokens de API

Cloud App Security requiere un token de API en el encabezado de todas las solicitudes de API para el servidor, como la siguiente:

```http
Authorization: Token <your_token_key>
```

Donde `<your_token_key>` es el token de la API personal.

Para obtener más información sobre los tokens de API, consulte [Administración de tokens de API](api-authentication.md).

### <a name="example"></a>Ejemplo

```rest
curl -XGET -H "Authorization:Token <your_token_key>" "https://<tenant_id>.<tenant_region>.contoso.com/api/example-endpoint"
```

## <a name="what-actions-are-supported"></a>¿Qué acciones se admiten?

En la tabla siguiente se describen las acciones admitidas:

|Recurso|Verbos HTTP|Rutas de URI|
|---|---|---|
|Detección|GET, POST o PUT|/api/v1/discovery/|
|Enriquecimiento de datos|POST|/api/subnet/|
|Actividades|GET o POST|/api/v1/activities/|
|Alertas|GET o POST|/api/v1/alerts/|
|Entidades|GET o POST|/api/v1/entities/|
|Archivos|GET o POST|/api/v1/files/|

Donde **Resource** representa un grupo de entidades relacionadas.

## <a name="what-field-types-are-supported"></a>¿Qué tipos de campo se admiten?

En la tabla siguiente se describen los tipos de campo admitidos:

|Campo|Description|
|---|---|
|string|Una cadena de texto|
|boolean|Un valor booleano que representa true/false|
|integer|Entero de 32 bits con signo|
|timestamp|Milisegundos desde la época|

## <a name="limits"></a>Límites

Puede elegir limitar las solicitudes proporcionando un parámetro de límite en la solicitud.

Se admiten los métodos siguientes para proporcionar el parámetro de límite:

- Codificada como dirección URL (con `Content-Type: application/x-www-form-urlencoded` encabezado)
- Datos de formulario
- Cuerpo JSON (con `Content-Type: multipart/form-data` y un encabezado de límite adecuado)

> [!NOTE]
>
> - Si no se proporciona ningún límite, se establecerá un valor predeterminado de 100.
> - Las respuestas para todas las solicitudes realizadas con el token de API están limitadas a un máximo de 100 elementos.
> - El límite de limitación para todas las solicitudes de API es de 30 solicitudes por minuto por inquilino.

## <a name="filters"></a>Filtros

Si tiene un gran número de resultados, le resultará útil ajustar las solicitudes mediante filtros. En esta sección se describe la estructura de los operadores y que se pueden usar con los filtros.

### <a name="structure"></a>Estructura

Algunos de nuestros puntos de conexión de API admiten filtros al realizar consultas. En las secciones correspondientes, encontrará una referencia que enumera todos los campos que se pueden filtrar y los operadores admitidos para ese recurso.

La mayoría de los filtros admiten varios valores para proporcionarle consultas eficaces. Al combinar filtros y operadores, usamos y como operador lógico entre los filtros.

### <a name="example"></a>Ejemplo

```rest
curl -XGET -H "Authorization:Token <your_token_key>" "https://<tenant_id>.<tenant_region>.contoso.com/api/example-endpoint" -d '{
  "filters": {
    "some.field": {
      "eq": ["value1", "value2"],
      "isset": true
    },
    "some.field2": {
      "gte": 5
    }
  },
  "skip": 5,
  "limit": 10
}'
```

### <a name="operators"></a>Operadores

> [!NOTE]
> No todos los operadores son compatibles con todos los filtros.

En la tabla siguiente se describen los operadores admitidos:

| Operador | Tipo de respuesta | Description |
| --- | --- | --- |
| contains | lista de cadenas | Devuelve todos los registros pertinentes que contienen una de las cadenas proporcionadas. |
| deq | lista de valores | Devuelve todos los registros que contienen un valor que no es igual a uno de los valores proporcionados. |
| descendiente | lista de valores | Devuelve todos los registros pertinentes que coinciden con valores o descendientes de ellos. |
| doesnotstartwith | lista de cadenas | Devuelve todos los registros relevantes que no empiecen por cada una de las cadenas proporcionadas. |
| endswith | lista de cadenas | Devuelve todos los registros pertinentes que terminan con una de las cadenas proporcionadas. |
| eq | lista de valores | Devuelve todos los registros pertinentes que contienen uno de los valores proporcionados. |
| gt | valor único | Devuelve todos los registros cuyo valor es mayor que el valor proporcionado. |
| GTE | valor único | Devuelve todos los registros cuyo valor es mayor o igual que el valor proporcionado. |
| gte_ndays | number | Devuelve todos los registros con fecha posterior a los N días. |
| isnotset | boolean | Cuando se establece en "true", devuelve todos los registros pertinentes que no tienen un valor en el campo especificado. |
| isset | boolean | Cuando se establece en "true", devuelve todos los registros pertinentes que tienen un valor en el campo especificado. |
| lt | valor único | Devuelve todos los registros cuyo valor es menor que el valor proporcionado. |
| lte | valor único | Devuelve todos los registros cuyo valor es menor o igual que el valor proporcionado. |
| lte_ndays | number | Devuelve todos los registros con una fecha anterior a N días. |
| ncontains | lista de cadenas | Devuelve todos los registros pertinentes que no contienen una de las cadenas proporcionadas |
| ndescendantof | lista de valores | Devuelve todos los registros pertinentes que no coinciden con valores o descendientes de ellos. |
| NEQ | lista de valores | Devuelve todos los registros pertinentes que no contienen todos los valores proporcionados. |
| range | lista de objetos que contienen los campos "Inicio" y "fin" | Devuelve todos los registros dentro de uno de los intervalos proporcionados |
| startswith | lista de cadenas | Devuelve todos los registros pertinentes a partir de una de las cadenas proporcionadas. |
| startswithsingle | string | Devuelve todos los registros pertinentes a partir de la cadena proporcionada. |
| text | string | Realiza una búsqueda de texto completo de todos los registros. |

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Autenticación de API](api-authentication.md)

[!INCLUDE [Open support ticket](includes/support.md)]
