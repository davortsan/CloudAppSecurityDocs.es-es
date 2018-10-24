---
title: Creación de directivas para controlar los permisos de la aplicación en Cloud App Security | Microsoft Docs
description: En este tema se proporcionan instrucciones para crear directivas de permisos de la aplicación y trabajar con ellas en Microsoft Cloud App Security.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 10/08/2018
ms.topic: conceptual
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 9f68302c-bb3d-450c-bbf5-f8130cb163e3
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: e9fc80f128cf463654b6a4dce1f08717df271ee1
ms.sourcegitcommit: c80c584c444b12dc8c788208cf973b46192b0cf0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/10/2018
ms.locfileid: "49072759"
---
*Se aplica a: Microsoft Cloud App Security*


# <a name="app-permission-policies"></a>Directivas de permisos de la aplicación

Además de la [investigación existente de aplicaciones OAuth](manage-app-permissions.md) conectada a su entorno, puede establecer directivas de permisos para recibir notificaciones automatizadas cuando una aplicación OAuth cumpla determinados criterios. Por ejemplo, puede recibir alertas automáticamente cuando haya aplicaciones que requieran un alto nivel de permisos y las hayan autorizado más de 50 usuarios. 

Las directivas de permisos de la aplicación permiten investigar qué permisos ha solicitado cada aplicación y qué usuarios los han autorizado para Office 365, G Suite y Salesforce. También es posible marcar estos permisos como aprobados o prohibidos. Si se marcan como prohibidos, se revocarán los permisos de cada aplicación para cada usuario que la haya autorizado. 

## <a name="create-a-new-app-permission-policy"></a>Creación de una directiva de permisos de la aplicación
Hay dos maneras de crear una directiva de permisos de la aplicación. La primera se encuentra en **Investigar** y la segunda en **Control**. 

Para crear una directiva de permisos de la aplicación

1. En **Investigar**, seleccione **Permisos de la aplicación**.
2. Filtre las aplicaciones según sus necesidades. Por ejemplo, puede ver todas las aplicaciones que solicitan **permiso** para **modificar calendarios en el buzón**.
3. Haga clic en el botón **New policy from search** (Nueva directiva a partir de búsqueda). 
    ![nueva directiva a partir de búsqueda](./media/app-permissions-filter.png)
4. Puede usar el filtro **Community use** (Uso de la Comunidad) para obtener información sobre si permitir el permiso para esta aplicación es habitual, poco habitual o raro. Este filtro puede ser útil si tiene una aplicación que es poco frecuente y solicita un permiso que tiene un nivel de gravedad alto o solicita permiso de muchos usuarios. 

Como alternativa, también puede crear la directiva, para lo que debe hacer clic en **Control** y en **Directivas**. Después, haga clic en **Crear directiva** y en **App permission policy** (Directiva de permisos de la aplicación).

  
   ![nueva directiva de permisos de la aplicación](./media/app-permissions-policy.png)



  ## <a name="next-steps"></a>Pasos siguientes 
  [Directivas de protección de datos](data-protection-policies.md)   

[Los clientes Premier también pueden elegir Cloud App Security directamente desde el Portal Premier.](https://premier.microsoft.com/)  
  
  