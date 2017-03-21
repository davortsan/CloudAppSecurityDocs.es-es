---
title: "Uso del motor de RegEx para directivas de inspección de contenido | Microsoft Docs"
description: En este tema se proporcionan instrucciones para usar RegEx para la coincidencia de patrones en directivas de Cloud App Security.
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 3/12/2017
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: dc8b87e5-e6c1-4a65-ab8c-067fb527fce4
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: c386cbbdadaf97297e6d876cdac9f7d3e2142b73
ms.sourcegitcommit: b840b945b270e616560f565bcc6590dd68ad5ebd
translationtype: HT
---
# <a name="working-with-the-regex-engine"></a>Trabajar con el motor de RegEx
 
Cloud App Security dispone de directivas de inspección de contenido que usan expresiones regulares para la coincidencia de patrones. La inspección de contenido puede aplicarse como parte de las directivas de archivo. Para probar expresiones regulares, puede usar los siguientes sitios web:  
  
-   [http://regexpal.com/](http://regexpal.com/)  
  
     (Asegúrese de que selecciona **No distingue mayúsculas de minúsculas**).  
  
-   [https://regex101.com/](https://regex101.com/)  
  
     Proporciona un análisis detallado de la expresión regular.  
  
Se imponen las siguientes limitaciones a las expresiones regulares personalizadas:  
  
-   La búsqueda nunca distingue mayúsculas de minúsculas  
   
-   Los cuantificadores permitidos son {n, m}, donde n, m < 10  
  
-   Todos los grupos deben ser grupos sin captura, por ejemplo, (?:xxx)  
  
     En lugar de (group), use (?:group)  
  
-   No se permiten los cuantificadores *, +, {n,}  
  
     En lugar de * use {0,9}  
  
     En lugar de + use {1,9}  
  
-   No se permiten las referencias inversas \\<número\> o \k\<nombre>  
  
Expresiones de ejemplo  
  
||||  
|-|-|-|  
|**Expresión regular**|**Datos**|**Coincide**|  
|Colou?r (?:black&#124;blue&#124;white)|Color negro<br /><br /> Color blanco<br /><br /> Color rojo|Sí<br /><br /> Sí<br /><br /> No|  
|[a-z0-9]{1,9}@[a-z0-9]{1,9}\\.[a-z]{2,3}|Some1@abc.com<br /><br /> user@host.org<br /><br /> @bad.com|Sí<br /><br /> Sí<br /><br /> No|  
|20\d{2}-(?:0[1-9]&#124;1[0-2])-(?:[0-2][0-9]&#124;30&#124;31)|31-12-2015<br /><br /> 09-01-2015<br /><br /> 31-12-1999|Sí<br /><br /> Sí<br /><br /> No|  
|d.n't\s{0,10}c.r.|Don't care<br /><br /> D!n'tcor0<br /><br /> Doesn't care|Sí<br /><br /> Sí<br /><br /> No|  
 

## <a name="see-also"></a>Consulte también  
[Actividades diarias para proteger el entorno de nube](daily-activities-to-protect-your-cloud-environment.md)   
[Para obtener soporte técnico, visite la página de soporte técnico asistido de Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Los clientes Premier también pueden elegir Cloud App Security directamente desde el Portal Premier.](https://premier.microsoft.com/)  
  
  