---
title: "Implementación del proxy de Cloud App Security para Azure AD | Microsoft Docs"
description: "En este tema, se proporciona información sobre cómo implementar el proxy de Cloud App Security para aplicaciones de Azure AD."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 8/10/2017
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: 2490c5e5-e723-4fc2-a5e0-d0a3a7d01fc2
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 58b309ddcc893d47a8adc89e9b286eff97ec99ed
ms.sourcegitcommit: 4cf65f627f2d370ee4a4decae1acbb9658874056
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/13/2017
---
# <a name="deploying-the-cloud-app-security-proxy-for-azure-ad"></a>Implementación del proxy de Cloud App Security para Azure AD

> [!NOTE]
> Se recomienda intentar la instalación en un espacio aislado o en un entorno de prueba antes de instalarlo en un entorno de producción.

Los pasos que se describen a continuación se deben realizar para implementar el proxy de Cloud App Security y permitir tanto el control de acceso como el control de sesión.


## <a name="step-1-create-an-azure-ad-conditional-access-policy"></a>Paso 1: Crear una directiva de acceso condicional de Azure AD

1. En Azure Active Directory, en **Seguridad**, haga clic en **Acceso condicional**.

 ![Acceso condicional de Azure AD](./media/conditional-access.png)

2. Haga clic en **Nueva directiva** y cree una directiva asegurándose de que en **Sesión** selecciona **Usar las restricciones que exige el proxy**.

## <a name="step-2-log-on-to-each-app"></a>Paso 2: Iniciar sesión en cada aplicación

Use sus credenciales para iniciar sesión en cada aplicación que quiera controlar con el proxy.

## <a name="step-3-add-the-apps-in-cloud-app-security"></a>Paso 3: Agregar las aplicaciones en Cloud App Security

1.  En el portal de Cloud App Security, vaya al engranaje Configuración y elija **Proxy**.

2. Las aplicaciones en las que ha iniciado sesión deberían aparecer en la tabla. 

3. Para cada aplicación, haga clic en los tres puntos en la esquina derecha de la fila de la tabla y haga clic en **Continuar configuración**.

4. En el asistente del proxy, haga clic en **Finalizar**.


En cuestión de minutos, todas las solicitudes de inicio de sesión a la aplicación se enrutarán a través del proxy de Cloud App Security. 

## <a name="test-the-configuration"></a>Probar la configuración

1.  Intente iniciar sesión en la aplicación. Si se produce un error en el inicio de sesión, asegúrese de haber completado correctamente todos los pasos del asistente del proxy. 

2.  En el portal de Cloud App Security, en **Investigar**, seleccione **Registro de actividad** y asegúrese de que haya eventos de **registro de inicio de sesión único** capturados por el proxy.



## <a name="see-also"></a>Consulte también  
[Trabajo con el proxy de Cloud App Security](proxy-intro.md)   
[Para obtener soporte técnico, visite la página de soporte técnico asistido de Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Los clientes Premier también pueden elegir Cloud App Security directamente desde el Portal Premier.](https://premier.microsoft.com/)  
  