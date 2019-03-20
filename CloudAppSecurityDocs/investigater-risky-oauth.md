---
title: 'Investigación de aplicaciones de OAuth de riesgo: Cloud App Security | Microsoft Docs'
description: En este artículo se proporciona información sobre cómo investigar las aplicaciones de riesgo de OAuth en Cloud App Security.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: barbkess
ms.date: 3/17/2019
ms.topic: tutorial
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 4118681e-362f-4b10-aa08-39691aa7800a
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 77b33d524e3a88d49c4dd2bcd71bc31c0fa26250
ms.sourcegitcommit: 57bad4dc9b28326c93ee480d308d52ea23c42089
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/18/2019
ms.locfileid: "58163662"
---
# <a name="investigate-risky-oauth-apps"></a>Investigación de aplicaciones de riesgo de OAuth

*Se aplica a: Microsoft Cloud App Security*

OAuth es un estándar abierto para autenticación y autorización basadas en tokens. OAuth permite que la información de la cuenta de un usuario sea utilizada por servicios de terceros, sin exponer la contraseña del usuario. OAuth actúa como un intermediario en nombre del usuario, proporcionando al servicio un token de acceso que autoriza el uso compartido de información específica de la cuenta.

Muchas aplicaciones de terceros que puedan instalar los usuarios profesionales de su organización solicitan permiso para acceder a datos e información de usuario e iniciar sesión en nombre del usuario en otras aplicaciones de nube. Cuando los usuarios instalan estas aplicaciones, a menudo hacen clic en **Aceptar** sin revisar detenidamente los detalles en el mensaje, incluyendo la concesión de permisos a la aplicación.

Aceptar los permisos de aplicaciones de terceros es un riesgo de seguridad potencial para su organización, por lo tanto, Microsoft Cloud App Security le ofrece la capacidad de investigar y supervisar los permisos de aplicaciones que sus usuarios otorgaron. Este artículo pretende ayudarle a investigar las aplicaciones de OAuth de su organización y se centra en las aplicaciones que tienen más probabilidades de ser sospechosas. 

Nuestro enfoque recomendado es investigar las aplicaciones utilizando las habilidades y la información proporcionadas en el portal de Cloud App Security para filtrar las aplicaciones con pocas posibilidades de ser de riesgo y centrarnos en las aplicaciones sospechosas. 

## <a name="how-to-investigate"></a>Procedimiento de investigación 

1.  De todas las aplicaciones de OAuth conectadas, consulte el uso de los filtros en el portal. Las consultas y los filtros recomendados son: 
    1. Nivel de permiso alto y uso comunitario no común. El uso de este filtro le ayudaría a centrarse en una aplicación con un potencial de riesgo alto, en la cual el usuario probablemente no haya entendido el riesgo. 
    2. Permisos de riesgo específicos relacionados con un tipo determinado de aplicaciones (por ejemplo, las aplicaciones con acceso completo a todos los buzones). El uso de este filtro le ayudaría a investigar en un contexto específico y encontrar las aplicaciones que parecen legítimas pero contienen permisos irrelevantes. Esas aplicaciones tienen más probabilidades de ser malintencionadas. 
    3. Aplicaciones que los usuarios externos han autorizado. El uso de este filtro le ayudará a encontrar aplicaciones que podrían no estar en sintonía con los estándares de seguridad de su empresa. 
2.  Céntrese en las aplicaciones siguientes, que pueden ser sospechosas: 
    1. Aplicaciones con un número reducido de “Autorizado por”. Centrarse en esas aplicaciones podría ayudarlo a encontrar aplicaciones malintencionadas autorizadas por un usuario comprometido. 
    2. Las aplicaciones con permisos que no se ajustan a la finalidad de la aplicación (por ejemplo, una aplicación de reloj con acceso total a todos los buzones de correo). Centrarse en esas aplicaciones puede ayudarle a encontrar aplicaciones que parecen legítimas, pero que realmente son malintencionadas. 
    3. Aplicaciones con nombre, publicador o sitio web sospechoso. Centrarse en esas aplicaciones puede ayudarle a encontrar rápidamente aplicaciones sospechosas. 
    4. Aplicaciones con una notificación “Última autorización” antigua. Centrarse en esas aplicaciones podría ayudarle a encontrar aplicaciones que ya no son necesarias. 
3. Utilice el vínculo de actividades relacionadas y, en la página del registro de actividad, vea las actividades realizadas por la aplicación. Tenga en cuenta que esto genera automáticamente un filtro para las actividades que el usuario iguala al nombre de la aplicación. Sin embargo, algunas aplicaciones pueden realizar actividades como uno de los usuarios. Esos eventos estarían disponibles en el registro de actividad, pero podrían filtrarse. 
4. Si una aplicación parece sospechosa, se recomienda comprobar el nombre y el publicador de la misma en las diferentes tiendas de aplicaciones. Céntrese en las aplicaciones siguientes, que pueden ser sospechosas: 
    1. Aplicación con un número reducido de descargas.
    2. Aplicación con una puntuación baja o comentarios malos.
    3. Aplicación con un publicador o sitio web sospechoso.
    4. Aplicación con una fecha anterior de la última actualización; puede indicar una aplicación que ya no se admite. 
    5. Las aplicaciones que no se ajustan a sus permisos, pueden indicar que esta aplicación es malintencionada. 
5. Si la aplicación sigue siendo sospechosa, puede buscar la dirección URL y el publicador del nombre de la aplicación en línea. 

## <a name="example"></a>Ejemplo 

Elija la opción “Aplicaciones de OAuth” en el icono de investigación
 
Use las opciones de filtro para filtrar las aplicaciones (equivalente al paso 1)
 

Investigue una aplicación sospechosa mediante la información disponible en el portal (equivalente al paso 2)
 

Use el registro de actividad (equivalente al paso 3)
 

Referencias https://searchmicroservices.techtarget.com/definition/OAuth https://docs.microsoft.com/cloud-app-security/manage-app-permissions


 
## <a name="next-steps"></a>Pasos siguientes
[Actividades diarias para proteger el entorno de nube](daily-activities-to-protect-your-cloud-environment.md) 

[Los clientes Premier también pueden crear una solicitud de soporte técnico directamente en el portal Premier.](https://premier.microsoft.com/) 
 
