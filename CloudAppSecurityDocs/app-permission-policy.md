---
title: Creación de directivas para controlar los permisos de la aplicación en Cloud App Security | Microsoft Docs
description: En este tema se proporcionan instrucciones para crear directivas de permisos de la aplicación y trabajar con ellas en Microsoft Cloud App Security.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 6/24/2018
ms.topic: article
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 9f68302c-bb3d-450c-bbf5-f8130cb163e3
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: dba05f619d68278bc31f13a0bfa46ec013e3f637
ms.sourcegitcommit: 49a06f2169af74304eef0288e31783c06ccd3b74
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/24/2018
ms.locfileid: "36747131"
---
*Se aplica a: Microsoft Cloud App Security*


# <a name="app-permission-policies"></a>Directivas de permisos de la aplicación

Además de la [investigación existente de aplicaciones OAuth](manage-app-permissions.md) conectada a su entorno, puede establecer directivas de permisos para recibir notificaciones automatizadas cuando una aplicación OAuth cumpla determinados criterios. Por ejemplo, puede recibir alertas automáticamente cuando haya aplicaciones que requieran un alto nivel de permisos y las hayan autorizado más de 50 usuarios. 

Las directivas de permisos de la aplicación le permiten investigar para Office 365, G Suite y Salesforce qué permisos ha solicitado cada aplicación y qué usuarios los han autorizado. También es posible marcar estos permisos como aprobados o prohibidos. Si se marcan como prohibidos, se revocarán los permisos de cada aplicación para cada usuario que la haya autorizado. 

Para crear una directiva de permisos de la aplicación
1. En **Investigar**, seleccione **Permisos de la aplicación**.
2. Filtre las aplicaciones según sus necesidades. Por ejemplo, puede ver todas las aplicaciones que solicitan **permiso** para **modificar calendarios en el buzón**.
3. Haga clic en el botón **New policy from search** (Nueva directiva a partir de búsqueda). 
    ![nueva directiva a partir de búsqueda](./media/app-permissions-filter.png)
4. Puede usar el filtro **Community use** (Uso de la comunidad) para saber si conceder permiso a esta aplicación es común, poco frecuente o raro. Esto puede resultar útil si tiene una aplicación que es poco frecuente y esta solicita un permiso con un nivel de gravedad alto o solicita permiso a muchos usuarios. 

Como alternativa, también puede crear la directiva, para lo que debe hacer clic en **Control** y en **Directivas**. Después, haga clic en **Crear directiva** y en **App permission policy** (Directiva de permisos de la aplicación).

  
   ![nueva directiva de permisos de la aplicación](./media/app-permissions-policy.png)



  ## <a name="see-also"></a>Consulte también  
  [Directivas de protección de datos](data-protection-policies.md)   

[Los clientes Premier también pueden elegir Cloud App Security directamente desde el Portal Premier.](https://premier.microsoft.com/)  
  
  