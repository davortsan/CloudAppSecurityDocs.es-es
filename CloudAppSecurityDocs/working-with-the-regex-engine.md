---
title: Uso del motor de RegEx en Cloud App Security para directivas de inspección de contenido
description: En este artículo se proporcionan instrucciones para usar RegEx para la coincidencia de patrones en directivas de Cloud App Security.
ms.date: 12/14/2018
ms.topic: how-to
ms.openlocfilehash: 0f9d2aafded05ac8f06f1408080ab8bd0da550b5
ms.sourcegitcommit: d87372b47ca98e942c2bf94032a6a61902627d69
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/30/2020
ms.locfileid: "96316949"
---
# <a name="working-with-the-regex-engine"></a>Trabajo con el motor de RegEx

[!INCLUDE [Banner for top of topics](includes/banner.md)]

En este artículo se proporcionan instrucciones para usar RegEx para la coincidencia de patrones en directivas de Cloud App Security.

## <a name="regular-expressions-in-cloud-app-security"></a>Expresiones regulares en Cloud App Security

Las directivas de inspección de contenido de Microsoft Cloud App Security usan RegEx para la coincidencia de patrones. La inspección de contenido puede aplicarse como parte de las directivas de archivo.

### <a name="testing-regular-expressions"></a>Prueba de expresiones regulares

Para probar expresiones regulares, puede usar los siguientes sitios web:

- [https://regexpal.com/](https://regexpal.com/) Asegúrese de seleccionar no **distinguir mayúsculas de minúsculas**.

- [https://regex101.com/](https://regex101.com/) : Proporciona un análisis detallado de la expresión regular.

### <a name="limitations-of-regular-expressions-in-cloud-app-security"></a>Limitaciones de las expresiones regulares en Cloud App Security

Se imponen las siguientes limitaciones a las expresiones regulares personalizadas:

- La búsqueda nunca distingue mayúsculas de minúsculas

- Los cuantificadores permitidos son {n, m}, donde n, m < 10

- Todos los grupos deben ser grupos sin captura, por ejemplo, (?:xxx)

    En lugar de (group), use (?:group)

- No se permiten los cuantificadores *, +, {n,}

    Use {0,9} en lugar de *

    Use {1,9} en lugar de +

- Referencias inversas no permitidas: \\ número \> de<o \k\<name>

### <a name="example-expressions"></a>Expresiones de ejemplo

En la tabla siguiente se proporcionan expresiones de ejemplo y si coincidirían o no.

|              Expresión regular              |                     data                     |      Coincide      |
|---------------------------------------------------------------|---------------------------------------------------------------|------------------------------------|
|            Colou?r (?:black&#124;blue&#124;white)             |   Color negro<br /><br /> Color blanco<br /><br /> Color rojo   | Sí<br /><br /> Sí<br /><br /> No |
|           [a-z0-9]{1,9}@[a-z0-9]{1,9}\\.[a-z]{2,3}            | Some1@abc.com<br /><br /> user@host.org<br /><br /> @bad.com  | Sí<br /><br /> Sí<br /><br /> No |
| 20\d{2}-(?:0[1-9]&#124;1[0-2])-(?:[0-2][0-9]&#124;30&#124;31) |   31-12-2015<br /><br /> 09-01-2015<br /><br /> 31-12-1999    | Sí<br /><br /> Sí<br /><br /> No |
|                       d.n't\s{0,10}c.r.                       | Don't care<br /><br /> D!n'tcor0<br /><br /> Doesn't care | Sí<br /><br /> Sí<br /><br /> No |

## <a name="check-out-this-video"></a>Eche un vistazo a este vídeo.

> [!div class="nextstepaction"]
> [Trabajar con el motor de Regex](https://channel9.msdn.com/Shows/Microsoft-Security/Microsoft-Cloud-App-Security-Working-with-the-Regex-Engine)

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Actividades diarias para proteger el entorno de nube](daily-activities-to-protect-your-cloud-environment.md)

[!INCLUDE [Open support ticket](includes/support.md)]
