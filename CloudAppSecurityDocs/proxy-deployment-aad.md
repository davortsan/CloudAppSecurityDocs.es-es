---
title: Implementación del control de aplicaciones de acceso condicional para aplicaciones de Azure AD
description: En este artículo se ofrece información sobre cómo implementar las características del proxy inverso de control de aplicaciones de acceso condicional de Microsoft Cloud App Security para aplicaciones de Azure AD.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 9/23/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: cloud-app-security
ms.suite: ems
ms.openlocfilehash: 14209e0b394571ee0d71784cb4c50683226a7a2e
ms.sourcegitcommit: 094bb42a198fe733cfd3aec79d74487672846dfa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/24/2019
ms.locfileid: "74460622"
---
# <a name="deploy-conditional-access-app-control-for-featured-apps"></a>Implementación del Control de aplicaciones de acceso condicional para aplicaciones destacadas

*Se aplica a: Microsoft Cloud App Security*

>[!div class="step-by-step"]
[« Anterior: Introducción a Control de aplicación de acceso condicional](proxy-intro-aad.md)<br>
[Next: Onboard and deploy Conditional Access App Control for any app »](proxy-deployment-any-app.md)

Session controls in Microsoft Cloud App Security work with the featured apps. For a list of apps that are featured by Cloud App Security to work out-of-the-box, see [Protect apps with Microsoft Cloud App Security Conditional Access App Control](proxy-intro-aad.md#featured-apps).

## <a name="prerequisites"></a>Requisitos previos

Para implementar el Control de aplicaciones de acceso condicional para aplicaciones de Azure AD, necesita una [licencia válida de Azure AD Premium P1](https://docs.microsoft.com/azure/active-directory/license-users-groups) y otra de Cloud App Security.

## <a name="to-deploy-featured-apps"></a>To deploy featured apps

Follow these steps to configure featured apps to be controlled by Microsoft Cloud App Security Conditional Access App Control.

**Step 1: [Go to the Azure AD portal and create a conditional access policy for the apps and route the session to Cloud App Security](#add-azure-ad)**

**Step 2: [Sign in to each app using a user scoped to the policy](#sign-in-scoped)**

**Step 3: [Verify the apps are configured to use access and session controls](#portal)**

**Step 4: [Test the deployment](#test)**

## Step 1: Create an Azure AD conditional access test policy <a name="add-azure-ad"></a>

1. In Azure Active Directory, under **Security**, click **Conditional Access**.

1. Haga clic en **Nueva directiva** y cree una directiva.

1. En la sección **Usuarios** de la directiva de prueba, asigne un usuario de prueba o uno que se pueda usar para un primer inicio de sesión y su comprobación.

1. En la sección **Aplicaciones en la nube** de la directiva de PRUEBA, asigne las aplicaciones que quiera controlar con el control de aplicaciones de acceso condicional.

1. En **Sesión**, configure la directiva para que use cualquiera de las directivas integradas, **Solo supervisar** o **Bloquear descargas**. También puede seleccionar **Usar directiva personalizada** para establecer una directiva avanzada en el portal de Cloud App Security.

1. Opcionalmente, agregue cualquier **asignación de condiciones** o **control de acceso** que corresponda.

   ![Acceso condicional de Azure AD](./media/azure-ad-caac-policy.png)

1. Click **Enable** and **Save**.

## Step 2: Sign in to each app using a user scoped to the policy<a name="sign-in-scoped"></a>

> [!NOTE]
> Before proceeding, make sure to first sign out of existing sessions.

Después de crear la directiva, inicie sesión en cada aplicación configurada en esa directiva. Asegúrese de que inicia sesión con un usuario configurado en la directiva.

Cloud App Security will sync your policy details to its servers for each new app you sign in to. Este proceso puede tardar hasta un minuto.

## Step 3: Verify the apps are configured to use access and session controls<a name="portal"></a>

Las instrucciones anteriores le han ayudado a crear una directiva integrada de Cloud App Security para aplicaciones destacadas directamente en Azure AD. In this step, verify that the access and session controls are configured for these apps.

1. In the Cloud App Security portal, click the settings cog ![settings icon](./media/settings-icon.png "icono de configuración"), and then select **Conditional Access App Control**.

1. In the Conditional Access App Control apps table, look at the **Available controls** column and verify that both **Access control** and **Session control** appear for your apps.

   > [!NOTE]
   > If session control doesn't appear for an app, it's not yet available for that specific app. You can either add it immediately as a [custom app](proxy-deployment-any-app.md), or you can open a request to add it as a featured app by clicking **Request session control**.
    >
    >![Solicitud del Control de aplicaciones de acceso condicional](media/caac-request.png)

## Step 4: Test the deployment<a name="test"></a>

1. Primero, cierre cualquier sesión existente. Después, intente iniciar sesión en cada aplicación que se ha implementado correctamente. Inicie sesión con un usuario que coincida con la directiva configurada en Azure AD.

1. En el portal de Cloud App Security en **Investigar**, seleccione **Registro de actividad** y asegúrese de que se capturan las actividades de inicio de sesión de cada aplicación.

1. Puede filtrar haciendo clic en **Avanzadas** y, luego, mediante la opción **Origen es igual a Acceso condicional**.

    ![Filtrar por Acceso condicional de Azure AD](./media/sso-logon.png)

1. Se recomienda que inicie sesión en aplicaciones de escritorio y móviles desde dispositivos administrados y no administrados. Esto es para asegurarse de que las actividades se capturan correctamente en el registro de actividad.<br>
Para confirmar que la actividad se captura correctamente, haga clic en un registro de inicio de sesión único en la actividad para abrir el cajón de actividad. Asegúrese de que la propiedad **Etiqueta de agente de usuario** refleja correctamente si el dispositivo es un cliente nativo (es decir, un aplicación de escritorio o móvil) o si es un dispositivo administrado (Compatible, Unido a dominio o Certificado de cliente válido).

> [!NOTE]
> Después de implementarse, no se puede quitar una aplicación de la página Control de aplicaciones de acceso condicional. Mientras no establezca una sesión o una directiva de acceso en la aplicación, el Control de aplicaciones de acceso condicional no cambiará el comportamiento de la aplicación.

>[!div class="step-by-step"]
[« Anterior: Introducción a Control de aplicación de acceso condicional](proxy-intro-aad.md)<br>[Next: Onboard and deploy Conditional Access App Control for any app »](proxy-deployment-any-app.md)

## <a name="next-steps"></a>Pasos siguientes

[Working with Cloud App Security Conditional Access App Control](proxy-intro-aad.md)

[!INCLUDE [Open support ticket](includes/support.md)]
