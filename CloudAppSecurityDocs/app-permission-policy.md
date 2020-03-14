---
title: Crear directivas para controlar las aplicaciones de OAuth en Cloud App Security
description: En este artículo se proporcionan instrucciones para crear y trabajar con directivas de permisos de la aplicación en Microsoft Cloud App Security.
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
ms.openlocfilehash: 9d007c4760ace7a4337e4738406016576fa04171
ms.sourcegitcommit: 4f3883a9e85d0aaf2802b10433b221c3f1838d88
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/13/2020
ms.locfileid: "79285309"
---
# <a name="oauth-app-policies"></a>Directivas de aplicación de OAuth

*Se aplica a: Microsoft Cloud App Security*

Además de la [investigación existente de las aplicaciones de OAuth](manage-app-permissions.md) conectadas a su entorno, puede establecer directivas de permisos en para obtener notificaciones automatizadas cuando una aplicación de OAuth cumple determinados criterios. Por ejemplo, puede recibir automáticamente una alerta cuando haya aplicaciones que requieran un nivel de permisos elevado y que hayan sido autorizadas por más de 50 usuarios.

Las directivas de aplicación de OAuth permiten investigar qué permisos solicitó cada aplicación y qué usuarios los autorizaron para Office 365, G Suite y Salesforce. También puede marcar estos permisos como aprobados o prohibidos. Si los marca como prohibidos, se revocarán los permisos de cada aplicación para cada usuario que lo haya autorizado.

## <a name="create-a-new-oauth-app-policy"></a>Crear una nueva Directiva de aplicación de OAuth

Hay dos maneras de crear una nueva Directiva de aplicación de OAuth. La primera forma es **investigar** y la segunda está bajo **control**.

Para crear una nueva Directiva de aplicación de OAuth:

1. En **investigar** , seleccione **aplicación de OAuth**.

1. Filtrar las aplicaciones según sus necesidades; por ejemplo, puede ver todas las aplicaciones que solicitan **permiso** para **modificar los calendarios en el buzón**.
1. Haga clic en el botón **Nueva directiva a partir de búsqueda**.
    ![nueva Directiva de Search](media/app-permissions-filter.png)
1. Puede usar el filtro de uso de la **comunidad** para obtener información sobre si el permiso para esta aplicación es común, infrecuente o poco frecuente. Este filtro puede ser útil si tiene una aplicación que no es habitual y solicita permiso con un nivel de gravedad alto o solicita permiso de muchos usuarios.
1. Puede establecer la Directiva en función de la pertenencia a grupos de los usuarios que han autorizado las aplicaciones. Por ejemplo, un administrador puede decidir establecer una directiva que revoca aplicaciones no comunes si requieren permisos elevados, solo si el usuario que autoriza los permisos es miembro del grupo de administradores.

También puede crear la Directiva haciendo clic en **control** seguido de **directivas**. A continuación, haga clic en **crear Directiva** seguido de **Directiva de aplicación de OAuth**.

   ![nueva Directiva de aplicación de OAuth](media/app-permissions-policy.png)

## <a name="oauth-app-anomaly-detection-policies"></a>Directivas de detección de anomalías de aplicación de OAuth

Además de las directivas de aplicación de OAuth que puede crear, hay las siguientes directivas de detección de anomalías integradas que perfilan los metadatos de las aplicaciones de OAuth para identificar las que son potencialmente malintencionadas:

| Nombre de la directiva | Descripción de la directiva |
| --- | --- |
| Nombre de aplicación OAuth engañoso | Examina las aplicaciones de OAuth conectadas a su entorno y desencadena una alerta cuando se detecta una aplicación con un nombre engañoso. Los nombres engañosos, como letras extranjeras que se parecen a las letras latinas, podrían indicar un intento de disfrazar una aplicación malintencionada como una aplicación conocida y de confianza. |
| Nombre de publicador engañoso para una aplicación de OAuth | Examina las aplicaciones de OAuth conectadas a su entorno y desencadena una alerta cuando se detecta una aplicación con un nombre de publicador engañoso. Los nombres de publicador engañosos, como letras extranjeras que se parecen a las letras latinas, podrían indicar un intento de disfrazar una aplicación malintencionada como una aplicación procedente de un editor conocido y de confianza. |
| Consentimiento de aplicación de OAuth malintencionado | Examina las aplicaciones de OAuth conectadas a su entorno y desencadena una alerta cuando se autoriza una aplicación potencialmente malintencionada. Las aplicaciones de OAuth malintencionadas se pueden usar como parte de una campaña de suplantación de identidad en un intento de poner en peligro a los usuarios. Esta detección aprovecha la investigación de seguridad de Microsoft y la experiencia con la inteligencia sobre amenazas para identificar aplicaciones malintencionadas. |

<!--| Suspicious OAuth app name | Scans OAuth apps connected to your environment and triggers an alert when an app with a suspicious name is detected. Suspicious names, such as names of known apps published by unknown publishers, could indicate an attempt to disguise a malicious app as a known and trusted app. |
| Non-secure redirect URL is used by an OAuth app | Scans OAuth apps connected to your environment and triggers an alert when an app uses a non-secure redirect URL (for example, does not use the HTTPS protocol), which exposes sensitive data to interception. |-->

> [!NOTE]
> Las directivas de detección de anomalías solo están disponibles para las aplicaciones de OAuth autorizadas en el Azure Active Directory.

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Directivas de protección de datos](data-protection-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]
