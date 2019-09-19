---
title: Creación de directivas para controlar las aplicaciones de OAuth en Cloud App Security
description: En este artículo se proporcionan instrucciones para crear directivas de permisos de la aplicación y trabajar con ellas en Microsoft Cloud App Security.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 7/25/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 9f68302c-bb3d-450c-bbf5-f8130cb163e3
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 2046536e45f6ecd7f1ede6249c69b0c7f09b6f57
ms.sourcegitcommit: 8a49c166424fea83853b0a6895212367526abe78
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2019
ms.locfileid: "71083852"
---
# <a name="oauth-app-policies"></a>Directivas de aplicación de OAuth

*Se aplica a: Microsoft Cloud App Security*

Además de la [investigación existente de aplicaciones OAuth](manage-app-permissions.md) conectada a su entorno, puede establecer directivas de permisos para recibir notificaciones automatizadas cuando una aplicación OAuth cumpla determinados criterios. Por ejemplo, puede recibir alertas automáticamente cuando haya aplicaciones que requieran un alto nivel de permisos y las hayan autorizado más de 50 usuarios. 

Las directivas de aplicación de OAuth de la aplicación permiten investigar qué permisos ha solicitado cada aplicación y qué usuarios los han autorizado para Office 365, G Suite y Salesforce. También es posible marcar estos permisos como aprobados o prohibidos. Si se marcan como prohibidos, se revocarán los permisos de cada aplicación para cada usuario que la haya autorizado. 

## <a name="create-a-new-oauth-app-policy"></a>Crear una directiva de aplicación de OAuth

Hay dos maneras de crear una directiva de aplicación de OAuth. La primera se encuentra en **Investigar** y la segunda en **Control**. 

Para crear una directiva de aplicación de OAuth:

1. En **Investigar**, seleccione **Aplicación de OAuth**.
2. Filtre las aplicaciones según sus necesidades. Por ejemplo, puede ver todas las aplicaciones que solicitan **permiso** para **modificar calendarios en el buzón**.
3. Haga clic en el botón **New policy from search** (Nueva directiva a partir de búsqueda). 
    ![nueva directiva a partir de búsqueda](./media/app-permissions-filter.png)
4. Puede usar el filtro **Community use** (Uso de la Comunidad) para obtener información sobre si permitir el permiso para esta aplicación es habitual, poco habitual o raro. Este filtro puede ser útil si tiene una aplicación que es poco frecuente y solicita un permiso que tiene un nivel de gravedad alto o solicita permiso de muchos usuarios. 
5. Puede establecer la directiva según la pertenencia a grupos de los usuarios que autorizaron las aplicaciones. Por ejemplo, un administrador puede decidir establecer una directiva que revoca aplicaciones poco habituales si solicitan permisos de nivel alto, solo si el usuario que autorizó los permisos es un miembro del grupo Administradores.

Como alternativa, también puede crear la directiva, para lo que debe hacer clic en **Control** y en **Directivas**. Después, haga clic en **Crear directiva** y en **OAuth app policy** (Directiva de aplicación de OAuth).

   ![Nueva directiva de aplicación de OAuth](./media/app-permissions-policy.png)

## <a name="oauth-app-anomaly-detection-policies"></a>Directivas de detección de anomalías de aplicación de OAuth

Además de las directivas de aplicación de OAuth que puede crear, hay las siguientes directivas de detección de anomalías integradas que perfilan los metadatos de las aplicaciones de OAuth para identificar las que son potencialmente malintencionadas:

| Nombre de la directiva | Descripción de la directiva |
| --- | --- |
| Nombre de aplicación OAuth engañoso | Examina las aplicaciones de OAuth conectadas a su entorno y desencadena una alerta cuando se detecta una aplicación con un nombre engañoso. Los nombres engañosos, como letras extranjeras que se parecen a las letras latinas, podrían indicar un intento de disfrazar una aplicación malintencionada como una aplicación conocida y de confianza. |
| Nombre de aplicación de OAuth sospechoso | Examina las aplicaciones de OAuth conectadas a su entorno y desencadena una alerta cuando se detecta una aplicación con un nombre sospechoso. Los nombres sospechosos, como los nombres de las aplicaciones conocidas publicadas por publicadores desconocidos, podrían indicar un intento de disfrazar una aplicación malintencionada como una aplicación conocida y de confianza. |
| Una aplicación OAuth usa una dirección URL de redireccionamiento no segura | Examina las aplicaciones de OAuth conectadas a su entorno y desencadena una alerta cuando una aplicación usa una dirección URL de redireccionamiento no segura (por ejemplo, no usa el protocolo HTTPS), que expone datos confidenciales a la interceptación. |
| Nombre de publicador engañoso para una aplicación de OAuth | Examina las aplicaciones de OAuth conectadas a su entorno y desencadena una alerta cuando se detecta una aplicación con un nombre de publicador engañoso. Los nombres de publicador engañosos, como letras extranjeras que se parecen a las letras latinas, podrían indicar un intento de disfrazar una aplicación malintencionada como una aplicación procedente de un editor conocido y de confianza. |

> [!NOTE]
> Las directivas de detección de anomalías solo están disponibles para las aplicaciones de OAuth autorizadas en el Azure Active Directory.

  ## <a name="next-steps"></a>Pasos siguientes 
  [Directivas de protección de datos](data-protection-policies.md)

[Los clientes Premier también pueden crear una solicitud de soporte técnico directamente en el portal Premier.](https://premier.microsoft.com/)