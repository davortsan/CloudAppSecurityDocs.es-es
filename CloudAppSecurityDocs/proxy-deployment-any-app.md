---
title: Implementar el Control de aplicación de Cloud App Security acceso condicional para las aplicaciones
description: En este artículo se proporciona información sobre cómo implementar las características de proxy inverso de Control de aplicaciones de Microsoft Cloud App Security condicional acceso para las aplicaciones.
keywords: ''
author: ShlomoSagir-MS
ms.author: shsagir
manager: ShlomoSagir-MS
ms.date: 7/2/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.suite: ems
ms.openlocfilehash: 6d96e788c741de31242a075bf65f80344d0c54ed
ms.sourcegitcommit: ee00e0033bf45a5f795bfd3e1d71fa1f70f97acb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/02/2019
ms.locfileid: "67515076"
---
# <a name="onboard-and-deploy-conditional-access-app-control-for-any-app"></a>Incorporar e implementar el Control de aplicaciones de acceso condicional para cualquier aplicación

*Se aplica a: Microsoft Cloud App Security*

>[!div class="step-by-step"]
[« Anterior: Introducción al control de aplicaciones de acceso condicional](proxy-intro-aad.md)<br>
[Siguiente: Cómo crear una directiva de sesión »](session-policy-aad.md)

Los controles de sesión en Microsoft Cloud App Security pueden configurarse para trabajar con las aplicaciones web. Este artículo se describe cómo incorporar e implementar aplicaciones de línea de negocio personalizadas, con características que no sean aplicaciones SaaS y aplicaciones locales que hospedan a través de Azure AD Application Proxy con los controles de sesión.

Para obtener una lista de aplicaciones que se destaquen por Cloud App Security para que funcione de fábrica, consulte [proteger aplicaciones con el Control de aplicaciones de Microsoft Cloud App Security condicional acceso](proxy-intro-aad.md).

## <a name="prerequisites"></a>Requisitos previos

- Su organización debe tener las licencias para usar Conditional Access App Control siguientes:

  - Edición de Azure Active Directory Premium
  - Seguridad de aplicaciones en la nube

- Las aplicaciones deben configurarse con el inicio de sesión único de Azure AD
- Las aplicaciones deben usar los protocolos SAML u Openid Connect 2.0

## <a name="to-deploy-a-any-app"></a>Para implementar una aplicación de cualquier

Siga estos pasos para configurar cualquier aplicación que estén controladas por Cloud App Security Conditional Access App Control.

**Paso 1: [Configurar la característica de directiva de acceso condicional de Azure Active Directory para distribuir aplicaciones en cuestión a Cloud App Security](#conf-azure-ad).**

**Paso 2: [Configurar los usuarios que se implementación la aplicación](#conf-users).**

**Paso 3: [Configuración de la aplicación que se va a implementar](#conf-app)**

**Paso 4: [Compruebe que la aplicación funciona correctamente](#verify-app)**

**Paso 5: [Permitir que la aplicación para su uso en su organización](#enable-app)**

**Paso 6: [Actualizar la directiva de Azure AD](#update-azure-ad)**

> [!NOTE]
> Para implementar el Control de aplicaciones de acceso condicional para aplicaciones de Azure AD, necesita una [licencia válida de Azure AD Premium P1](https://docs.microsoft.com/azure/active-directory/license-users-groups) y otra de Cloud App Security.

## Paso 1: Configurar la característica de directiva de acceso condicional de Azure Active Directory para distribuir aplicaciones en cuestión a Cloud App Security<a name="conf-azure-ad"></a>  

1. En Azure Active Directory, en **seguridad**, haga clic en **acceso condicional**.

1. En el **acceso condicional** , en la barra de herramientas en la parte superior, haga clic en **nueva directiva**.

1. En el **New** página, en el **nombre** cuadro de texto, escriba **prueba**.

1. En el **usuarios y grupos** página, asigne los usuarios de prueba relevantes que serán la incorporación de las aplicaciones.

1. En el **aplicaciones en la nube** página, asigne las aplicaciones que quiera controlar con Control de aplicaciones de acceso condicional.

1. En **sesión**, seleccione **Use Conditional Access App Control** y, a continuación, seleccione **supervisar sólo**.

   ![Acceso condicional de Azure AD](./media/azure-ad-caac-policy.png)

1. Haga clic en **habilitar** y **guardar**.

## Paso 2: Configurar los usuarios que va a implementar la aplicación<a name="conf-users"></a>

1. En Cloud App Security, en la barra de menús, haga clic en el engranaje de configuración ![icono configuración](./media/settings-icon.png "icono configuración") y seleccione **configuración**.

1. En **Conditional Access App Control**, seleccione **incorporación y mantenimiento de la aplicación**.

1. Escriba el nombre principal de usuario o correo electrónico para los usuarios que serán la incorporación de la aplicación y, a continuación, haga clic en **guardar**.

    ![Captura de pantalla de configuración de incorporación de la aplicación y mantenimiento.](media/app-onboarding-settings.png)

## Paso 3: Configuración de la aplicación que se va a implementar<a name="conf-app"></a>

1. Vaya a la aplicación que se va a implementar. Si se reconoce su dominio de aplicación, se le pedirá para continuar el proceso de configuración de la aplicación. Si no se reconoce su dominio de aplicación, se le pedirá configurar dominios de la aplicación. Haga clic en **Configurar aplicación** para continuar el proceso de configuración.

    > [!NOTE]
    > Para los dominios de aplicación reconocida, asegúrese de que la aplicación está configurada con todos los dominios necesarios para que la aplicación funcione correctamente.

1. Repita los pasos siguientes para instalar el **CA actual** y **CA siguiente** certificados raíz autofirmados.
    1. Seleccione el certificado.
    1. Haga clic en **abierto**y cuando se le solicite haga clic en **abierto** nuevo.
    1. Haga clic en **instalar certificado**.
    1. Elija **usuario actual** o **máquina Local**.
    1. Seleccione **colocar todos los certificados en el siguiente almacén** y, a continuación, haga clic en **examinar**.
    1. Seleccione **entidades emisoras de certificados raíz de confianza** y, a continuación, haga clic en **Aceptar**.
    1. Haga clic en **Finalizar**.

    > [!NOTE]
    > Para los certificados que lo haya reconocido, una vez haya instalado el certificado, debe reiniciar el explorador y vaya a la misma página. Verá una marca de verificación por la confirmación de vínculos de los certificados que están instalados.

1. Haga clic en **Continue**.

## Paso 4: Compruebe que la aplicación funciona correctamente<a name="verify-app"></a>

1. Compruebe que el flujo de inicio de sesión funciona correctamente.
    > [!NOTE]
    > Algunas aplicaciones emiten un nonce hash durante la autenticación que se puede interrumpir el proceso de inicio de sesión. Si esto ocurre, consulte la Guía de solución de problemas para resolver el problema.
1. Una vez que esté en la aplicación, realice las siguientes comprobaciones:
    1. Visite todas las páginas dentro de la aplicación que forman parte del proceso de trabajo de usuarios y comprobación que las páginas se representan correctamente.
    1. Comprobar que el comportamiento y la funcionalidad de la aplicación no está afectado negativamente por realizar acciones comunes como la descarga y carga de archivos.

## Paso 5: Permitir que la aplicación para su uso en su organización<a name="enable-app"></a>

Cuando esté listo para habilitar la aplicación para su uso en el entorno de producción de su organización, realice los pasos siguientes.

1. En Cloud App Security, en la barra de menús, haga clic en el engranaje de configuración ![icono configuración](./media/settings-icon.png "icono configuración") y seleccione **Conditional Access App Control**.
1. En la lista de aplicaciones, en la fila en la que aparece la aplicación que se va a implementar, elija los tres puntos al final de la fila y, a continuación, elija **Editar aplicación**.
1. Seleccione **uso con Conditional Access App Control** y, a continuación, haga clic en **guardar**.

## Paso 6: Actualizar la directiva de Azure AD<a name="update-azure-ad"></a>

1. En Azure Active Directory, en **seguridad**, haga clic en **acceso condicional**.
1. Actualizar la directiva creada en [Paso1](#conf-azure-ad) para incluir la correspondiente a los usuarios, grupos y controles que requiere.
1. En **sesión** > **Use Conditional Access App Control**, si seleccionó **directiva personalizada de uso**, vaya a Cloud App Security y cree correspondiente Directiva de sesión. Para obtener más información, consulte [Directivas de sesión](session-policy-aad.md).

>[!div class="step-by-step"]
[« Anterior: Implementar el Control de aplicaciones de acceso condicional para aplicaciones de Azure AD](proxy-deployment-aad.md)<br>
[Siguiente: Cómo crear una directiva de sesión »](session-policy-aad.md)

## <a name="next-steps"></a>Pasos siguientes 
[Trabajo con el control de aplicaciones de acceso condicional de Cloud App Security](proxy-intro-aad.md)

[Los clientes Premier también pueden crear una solicitud de soporte técnico directamente en el portal Premier.](https://premier.microsoft.com/)