---
title: Crear directivas de acceso de Cloud App Security para permitir y bloquear el acceso | Microsoft Docs
description: En este tema, se describe el procedimiento para configurar una directiva de acceso al control de aplicaciones de acceso condicional de Cloud App Security para permitir y bloquear el acceso a las aplicaciones conectadas a través de Azure AD mediante las funcionalidades de proxy inverso.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 5/14/2018
ms.topic: article
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 9095cff1-f8b0-44a7-b1df-a83e674abbc6
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 06a78107b33613fe8d947ed55e057990268c7026
ms.sourcegitcommit: 2ca1f7b11679d15faa1abdf0b8a805c9aff89d2a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/14/2018
---
*Se aplica a: Microsoft Cloud App Security*

# <a name="access-policies"></a>Directivas de acceso 

> [!NOTE]
> Se trata de una característica en vista previa.


>[!div class="step-by-step"]
[« ANTERIOR: Cómo crear una directiva de sesión](session-policy-aad.md)<br>
[SIGUIENTE: Explorar casos de uso populares »](use-case-proxy-block-session-aad.md)


Las directivas de acceso de Microsoft Cloud App Security permiten la supervisión en tiempo real y el control del acceso a aplicaciones en la nube en función del usuario, la ubicación, el dispositivo y la aplicación. Puede crear directivas de acceso para cualquier dispositivo, incluidos aquellos que no están unidos al dominio y que no administra Windows Intune. Para ello, implemente certificados de cliente en dispositivos administrados o aproveche los certificados existentes, por ejemplo, los certificados de MDM de terceros. Por ejemplo, puede implementar certificados de cliente en dispositivos administrados y después bloquear el acceso desde dispositivos que no tengan ningún certificado. 

> [!NOTE]
> En lugar de permitir o bloquear el acceso por completo, con las [directivas de sesión](session-policy-aad.md) puede permitir el acceso mientras supervisa la sesión o limitar determinadas actividades de la sesión. 

## <a name="prerequisites-to-using-access-policies"></a>Requisitos previos para usar las directivas de acceso

- Tener una licencia de Azure AD Premium P2.
- Las aplicaciones en cuestión deben estar [implementadas con control de aplicaciones de acceso condicional](proxy-deployment-aad.md).
- Debe haber aplicada una [directiva de acceso condicional de Azure AD](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal) que redirija a los usuarios a Microsoft Cloud App Security, tal y como se describe aquí.

> [!NOTE]
> - Las directivas de acceso también admiten aplicaciones que estén configuradas con proveedores de identidades que no sean Azure AD en Private Preview. Para obtener más información sobre Private Preview, envíe un correo electrónico a mcaspreview@microsoft.com.

## <a name="create-an-azure-ad-conditional-access-policy"></a>Crear una directiva de acceso condicional de Azure AD

Las directivas de acceso condicional de Azure Active Directory y las directivas de sesión de Cloud App Security funcionan conjuntamente para examinar cada sesión de usuario y tomar decisiones de directiva relativas a cada aplicación. Haga lo siguiente para configurar una directiva de acceso condicional en Azure AD:

1. Configure una [directiva de acceso condicional de Azure AD](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal) con asignaciones de usuario o de grupo de usuarios y la aplicación SAML que quiere controlar con el control de aplicaciones de acceso condicional. 

   > [!NOTE]
   > Esta directiva afectará únicamente a las aplicaciones que se hayan [implementado con control de aplicaciones de acceso condicional](proxy-deployment-aad.md).

2. Enrute usuarios a Microsoft Cloud App Security; para ello, active **Use Conditional Access App Control enforced restrictions** (Usar las restricciones que exige el control de aplicaciones de acceso condicional) en la hoja **Sesión**.

   ![Acceso condicional de Azure AD con restricciones de control de aplicaciones de acceso condicional](./media/proxy-deploy-restrictions-aad.png)

## <a name="create-a-cloud-app-security-access-policy"></a>Crear una directiva de acceso de Cloud App Security 

Para crear una directiva de acceso, siga este procedimiento:

1. En el portal, seleccione **Control** y, después, **Directivas**.
2. En la página **Directivas**, haga clic en **Crear directiva** y seleccione **Directiva de acceso**.  

   ![Crear directiva de acceso](./media/access-policy-menu.png)

3. En la ventana **Directiva de acceso**, asigne un nombre a la directiva, por ejemplo, *Bloquear el acceso desde dispositivos no administrados*.

   ![Nueva directiva de acceso](./media/access-policy-screen.png)

4. En la sección **Actividades que coinciden con todo lo siguiente** de **Origen de la actividad**, seleccione más filtros de actividad para aplicarlos a la directiva. Las opciones son las siguientes: 
     
   - **Etiqueta de dispositivo**: use este filtro para identificar los dispositivos no administrados.

   - **Ubicación**: use este filtro para identificar las ubicaciones desconocidas (por tanto, que entrañan riesgo). 

   - **Dirección IP**: use este filtro para filtrar por direcciones IP o usar las etiquetas de dirección IP previamente asignadas. 

   - **Etiqueta de agente de usuario**: use este filtro para habilitar la heurística que permite identificar las aplicaciones de escritorio y móviles. Este filtro se puede establecer como igual o no igual a **Cliente nativo**, y conviene comprobarlo con las aplicaciones de escritorio y móviles de cada aplicación en la nube.
  
       ![Compatibilidad de cliente nativo](./media/user-agent-tag.png)

5. En **Acciones**, seleccione una de las siguientes opciones: 

    - **Permitir**: establezca esta acción para permitir expresamente el acceso según los filtros de directiva que haya establecido.

    - **Bloquear**: establezca esta acción para bloquear expresamente el acceso según los filtros de directiva que haya establecido. 

6. Puede **crear una alerta para cada evento que coincida con la gravedad de directiva**, establecer un límite de alerta y seleccionar si quiere que la alerta llegue como un correo electrónico, como un mensaje de texto o ambas.



>[!div class="step-by-step"]
[« ANTERIOR: Cómo crear una directiva de sesión](session-policy-aad.md)<br>
[SIGUIENTE: Explorar casos de uso populares »](use-case-proxy-block-session-aad.md)

 
## <a name="see-also"></a>Consulte también  
[Bloqueo de descargas en dispositivos no administrados con las funciones de control de aplicaciones de acceso condicional de Azure AD](use-case-proxy-block-session-aad.md)   

[Los clientes Premier también pueden elegir Cloud App Security directamente desde el Portal Premier.](https://premier.microsoft.com/)  
  
  