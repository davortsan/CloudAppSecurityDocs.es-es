---
title: Creación de directivas para controlar las aplicaciones de OAuth en Cloud App Security
description: En este artículo se proporcionan instrucciones para crear directivas de permisos de la aplicación y trabajar con ellas en Microsoft Cloud App Security.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 11/27/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 25809c1ace00b31df32c225f6b72a2b4e98a70d8
ms.sourcegitcommit: 826d2ec022647bce6c3135c115a41ee894ff8ecd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/16/2020
ms.locfileid: "84800731"
---
# <a name="oauth-app-policies"></a>Directivas de aplicación de OAuth

*Se aplica a: Microsoft Cloud App Security*

Además de la [investigación existente de aplicaciones OAuth](manage-app-permissions.md) conectada a su entorno, puede establecer directivas de permisos para recibir notificaciones automatizadas cuando una aplicación OAuth cumpla determinados criterios. Por ejemplo, puede recibir automáticamente una alerta cuando haya aplicaciones que requieran un nivel de permisos elevado y que hayan sido autorizadas por más de 50 usuarios.

Las directivas de aplicación de OAuth de la aplicación permiten investigar qué permisos ha solicitado cada aplicación y qué usuarios los han autorizado para Office 365, G Suite y Salesforce. También es posible marcar estos permisos como aprobados o prohibidos. Si se marcan como prohibidos, se revocarán los permisos de cada aplicación para cada usuario que la haya autorizado.

## <a name="create-a-new-oauth-app-policy"></a>Crear una directiva de aplicación de OAuth

Hay dos maneras de crear una directiva de aplicación de OAuth. La primera se encuentra en **Investigar** y la segunda en **Control**.

Para crear una directiva de aplicación de OAuth:

1. En **Investigar**, seleccione **Aplicación de OAuth**.

1. Filtre las aplicaciones según sus necesidades. Por ejemplo, puede ver todas las aplicaciones que solicitan **permiso** para **modificar calendarios en el buzón**.
1. Haga clic en el botón **New policy from search** (Nueva directiva a partir de búsqueda).
    ![nueva directiva a partir de búsqueda](media/app-permissions-filter.png)
1. Puede usar el filtro de uso de la **comunidad** para obtener información sobre si el permiso para esta aplicación es común, infrecuente o poco frecuente. Este filtro puede ser útil si tiene una aplicación que es poco frecuente y solicita un permiso que tiene un nivel de gravedad alto o solicita permiso de muchos usuarios.
1. Puede establecer la directiva según la pertenencia a grupos de los usuarios que autorizaron las aplicaciones. Por ejemplo, un administrador puede decidir establecer una directiva que revoca aplicaciones no comunes si requieren permisos elevados, solo si el usuario que autoriza los permisos es miembro del grupo de administradores.

Como alternativa, también puede crear la directiva, para lo que debe hacer clic en **Control** y en **Directivas**. Después, haga clic en **Crear directiva** y en **OAuth app policy** (Directiva de aplicación de OAuth).

   ![Nueva directiva de aplicación de OAuth](media/app-permissions-policy.png)

## <a name="oauth-app-anomaly-detection-policies"></a>Directivas de detección de anomalías de aplicación de OAuth

Además de las directivas de aplicación de OAuth que puede crear, hay las siguientes directivas de detección de anomalías integradas que perfilan los metadatos de las aplicaciones de OAuth para identificar las que son potencialmente malintencionadas:

| Nombre de la directiva | Descripción de directiva |
| --- | --- |
| Nombre de aplicación OAuth engañoso | Examina las aplicaciones de OAuth conectadas a su entorno y desencadena una alerta cuando se detecta una aplicación con un nombre engañoso. Los nombres engañosos, como letras extranjeras que se parecen a las letras latinas, podrían indicar un intento de disfrazar una aplicación malintencionada como una aplicación conocida y de confianza. |
| Nombre de publicador engañoso para una aplicación de OAuth | Examina las aplicaciones de OAuth conectadas a su entorno y desencadena una alerta cuando se detecta una aplicación con un nombre de publicador engañoso. Los nombres de publicador engañosos, como letras extranjeras que se parecen a las letras latinas, podrían indicar un intento de disfrazar una aplicación malintencionada como una aplicación procedente de un editor conocido y de confianza. |
| Consentimiento de aplicación de OAuth malintencionado | Examina las aplicaciones de OAuth conectadas a su entorno y desencadena una alerta cuando se autoriza una aplicación potencialmente malintencionada. Las aplicaciones de OAuth malintencionadas se pueden usar como parte de una campaña de suplantación de identidad en un intento de poner en peligro a los usuarios. Esta detección aprovecha la investigación de seguridad de Microsoft y la experiencia con la inteligencia sobre amenazas para identificar aplicaciones malintencionadas. |

<!--
| OAuth apps authorized by external users | Scans OAuth apps connected to your environment and triggers an alert when an app was authorized by an external user. |
| OAuth apps with high permissions and rare community use – Google | Scans OAuth apps connected to your environment and triggers an alert for apps with high permissions and rare community use in Google. |
| OAuth apps with high permissions and rare community use – Office | Scans OAuth apps connected to your environment and triggers an alert for apps with high permissions and rare community use in Office. |
| OAuth apps with rare community use - Salesforce | Scans OAuth apps connected to your environment and triggers an alert for apps with rare community use in Salesforce. |
-->

> [!NOTE]
> Las directivas de detección de anomalías solo están disponibles para las aplicaciones de OAuth autorizadas en el Azure Active Directory.

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Directivas de protección de datos](data-protection-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]
