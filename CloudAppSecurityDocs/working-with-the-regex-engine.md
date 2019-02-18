---
title: Uso del motor de RegEx en Cloud App Security para directivas de inspección de contenido
description: En este artículo se proporcionan instrucciones para usar RegEx para la coincidencia de patrones en directivas de Cloud App Security.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: barbkess
ms.date: 12/14/2018
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: dc8b87e5-e6c1-4a65-ab8c-067fb527fce4
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 07085a2c2e8a27e6e6ad35d9e088a95f8d543522
ms.sourcegitcommit: 8ef0438fa35916c48625ff750cb85e9628d202f2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/15/2019
ms.locfileid: "56281124"
---
# <a name="working-with-the-regex-engine"></a>Trabajar con el motor de RegEx

*Se aplica a: Microsoft Cloud App Security*
 
En este artículo se proporcionan instrucciones para usar RegEx para la coincidencia de patrones en directivas de Cloud App Security.

## <a name="regular-expressions-in-cloud-app-security"></a>Expresiones regulares en Cloud App Security

Las directivas de inspección de contenido de Microsoft Cloud App Security usan RegEx para la coincidencia de patrones. La inspección de contenido puede aplicarse como parte de las directivas de archivo.

### <a name="testing-regular-expressions"></a>Prueba de expresiones regulares

Para probar expresiones regulares, puede usar los siguientes sitios web:  
  
- [https://regexpal.com/](https://regexpal.com/): asegúrese de que selecciona **Case insensitive** (No distingue mayúsculas de minúsculas).  
  
- [https://regex101.com/](https://regex101.com/): proporciona un análisis detallado de la expresión regular.  

### <a name="limitations-of-regular-expressions-in-cloud-app-security"></a>Limitaciones de las expresiones regulares en Cloud App Security

Se imponen las siguientes limitaciones a las expresiones regulares personalizadas:  
  
- La búsqueda nunca distingue mayúsculas de minúsculas  

- Los cuantificadores permitidos son {n, m}, donde n, m < 10  
  
- Todos los grupos deben ser grupos sin captura, por ejemplo, (?:xxx)  
  
     En lugar de (group), use (?:group)  
  
- No se permiten los cuantificadores *, +, {n,}  
  
     Use {0,9} en lugar de *  
  
     Use {1,9} en lugar de +  
  
- No se permiten las referencias inversas \\<número\> o \k\<nombre>  
  
### <a name="example-expressions"></a>Expresiones de ejemplo  

En la tabla siguiente se proporcionan expresiones de ejemplo y si coincidirían o no.

|                                                               |                                                               |                                    |
|---------------------------------------------------------------|---------------------------------------------------------------|------------------------------------|
|              <strong>Expresión regular</strong>              |                     <strong>Datos</strong>                     |      <strong>Coincide</strong>      |
|            Colou?r (?:black&#124;blue&#124;white)             |   Color negro<br /><br /> Color blanco<br /><br /> Color rojo   | Sí<br /><br /> Sí<br /><br /> No |
|           [a-z0-9]{1,9}@[a-z0-9]{1,9}\\.[a-z]{2,3}            | Some1@abc.com<br /><br /> user@host.org<br /><br /> @bad.com  | Sí<br /><br /> Sí<br /><br /> No |
| 20\d{2}-(?:0[1-9]&#124;1[0-2])-(?:[0-2][0-9]&#124;30&#124;31) |   31-12-2015<br /><br /> 09-01-2015<br /><br /> 31-12-1999    | Sí<br /><br /> Sí<br /><br /> No |
|                       d.n't\s{0,10}c.r.                       | Don't care<br /><br /> D!n'tcor0<br /><br /> Doesn't care | Sí<br /><br /> Sí<br /><br /> No |

## <a name="check-out-this-video"></a>Eche un vistazo a este vídeo.

[Trabajar con el motor de RegEx](https://channel9.msdn.com/Shows/Microsoft-Security/Microsoft-Cloud-App-Security-Working-with-the-Regex-Engine)

## <a name="next-steps"></a>Pasos siguientes

[Actividades diarias para proteger el entorno de nube](daily-activities-to-protect-your-cloud-environment.md)   

[Los clientes Premier también pueden crear una solicitud de soporte técnico directamente en el portal Premier.](https://premier.microsoft.com/)  
  
