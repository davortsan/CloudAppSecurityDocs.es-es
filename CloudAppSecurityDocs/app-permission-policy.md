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
ms.openlocfilehash: 1822ce576b71a196917a3f8d2b94122b88eac163
ms.sourcegitcommit: 094bb42a198fe733cfd3aec79d74487672846dfa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/24/2019
ms.locfileid: "74461138"
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

## <a name="oauth-app-anomaly-detection-policies"></a>OAuth app anomaly detection policies

In addition to OAuth app policies you can create, there are the following out-of-the-box anomaly detection policies that profile metadata of OAuth apps to identify ones that are potentially malicious:

| Nombre de directiva | Descripción de la directiva |
| --- | --- |
| Misleading OAuth app name | Scans OAuth apps connected to your environment and triggers an alert when an app with a misleading name is detected. Misleading names, such as foreign letters that resemble Latin letters, could indicate an attempt to disguise a malicious app as a known and trusted app. |
| Suspicious OAuth app name | Scans OAuth apps connected to your environment and triggers an alert when an app with a suspicious name is detected. Suspicious names, such as names of known apps published by unknown publishers, could indicate an attempt to disguise a malicious app as a known and trusted app. |
| Non-secure redirect URL is used by an OAuth app | Scans OAuth apps connected to your environment and triggers an alert when an app uses a non-secure redirect URL (for example, does not use the HTTPS protocol), which exposes sensitive data to interception. |
| Misleading publisher name for an OAuth app | Scans OAuth apps connected to your environment and triggers an alert when an app with a misleading publisher name is detected. Misleading publisher names, such as foreign letters that resemble Latin letters, could indicate an attempt to disguise a malicious app as an app coming from a known and trusted publisher. |

> [!NOTE]
> Anomaly detection policies are only available for OAuth apps that are authorized in your Azure Active Directory.

  ## <a name="next-steps"></a>Pasos siguientes 
  [Directivas de protección de datos](data-protection-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]