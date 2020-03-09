---
title: Implementación de Control de aplicaciones de acceso condicional de Cloud App Security para aplicaciones Azure AD
description: En este artículo se proporciona información sobre cómo implementar las características de Microsoft Cloud App Security Control de aplicaciones de acceso condicional proxy inverso para aplicaciones Azure AD.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 9/23/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: cloud-app-security
ms.suite: ems
ms.openlocfilehash: 0fc3f43aa76f64d1228a6e45d2fdc743a494a8e3
ms.sourcegitcommit: 3f6ef6b97a0953470135d115323a00cf11441ab7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/08/2020
ms.locfileid: "78927776"
---
# <a name="deploy-conditional-access-app-control-for-featured-apps"></a>Implementación del Control de aplicaciones de acceso condicional para aplicaciones destacadas

*Se aplica a: Microsoft Cloud App Security*

Los controles de sesión de Microsoft Cloud App Security funcionan con las aplicaciones destacadas. Para obtener una lista de las aplicaciones que se incluyen en Cloud App Security trabajar de forma integrada, consulte [proteger aplicaciones con Microsoft Cloud App Security control de aplicaciones de acceso condicional](proxy-intro-aad.md#featured-apps).

## <a name="prerequisites"></a>Requisitos previos

Para implementar Control de aplicaciones de acceso condicional para aplicaciones de Azure AD, necesita una [licencia válida para Azure ad Premium P1](https://docs.microsoft.com/azure/active-directory/license-users-groups) , así como una licencia de Cloud App Security.

## <a name="to-deploy-featured-apps"></a>Para implementar aplicaciones destacadas

Siga estos pasos para configurar las aplicaciones destacadas que se van a controlar mediante Microsoft Cloud App Security Control de aplicaciones de acceso condicional.

**Paso 1: [ir al portal de Azure ad y crear una directiva de acceso condicional para las aplicaciones y enrutar la sesión a Cloud App Security](#add-azure-ad)**

**Paso 2: [iniciar sesión en cada aplicación con un usuario con ámbito en la Directiva](#sign-in-scoped)**

**Paso 3: [comprobar que las aplicaciones están configuradas para usar controles de acceso y de sesión](#portal)**

**Paso 4: [probar la implementación](#test)**

## Paso 1: crear una directiva de prueba de acceso condicional Azure AD<a name="add-azure-ad"></a>

1. En Azure Active Directory, en **seguridad**, haga clic en **acceso condicional**.

1. Haga clic en **nueva Directiva** y cree una nueva Directiva.

1. En la Directiva de prueba, en **usuarios**, asigne un usuario o usuario de prueba que se pueda usar para el inicio de sesión y la comprobación iniciales.

1. En la Directiva de prueba, en **aplicación en la nube**, asigne las aplicaciones que quiera controlar con control de aplicaciones de acceso condicional.

1. En **sesión**, establezca la Directiva para usar cualquiera de las directivas integradas, **supervisar solo** o **bloquear descargas**. O seleccione **usar directiva personalizada** para establecer una directiva avanzada en el portal de Cloud App Security.

1. Agregue las **asignaciones de condiciones** aplicables o **los controles de concesión** (opcional).

    ![Acceso condicional de Azure AD](media/azure-ad-caac-policy.png)

1. Haga clic en **Habilitar** y **Guardar**.

## Paso 2: iniciar sesión en cada aplicación con un usuario con ámbito en la Directiva<a name="sign-in-scoped"></a>

> [!NOTE]
> Antes de continuar, asegúrese de cerrar primero las sesiones existentes.

Una vez creada la Directiva, inicie sesión en cada una de las aplicaciones configuradas en esa Directiva. Asegúrese de iniciar sesión con un usuario configurado en la Directiva.

Cloud App Security sincronizará los detalles de la Directiva con sus servidores para cada nueva aplicación en la que inicie sesión. Esto puede tardar hasta un minuto.

## Paso 3: comprobar que las aplicaciones están configuradas para usar controles de acceso y de sesión<a name="portal"></a>

Las instrucciones anteriores le ayudaron a crear una directiva de Cloud App Security integrada para aplicaciones destacadas directamente en Azure AD. En este paso, compruebe que los controles de sesión y acceso estén configurados para estas aplicaciones.

1. En el portal de Cloud App Security, haga clic en el icono configuración engranaje ![configuración](media/settings-icon.png "icono de configuración")y seleccione **control de aplicaciones de acceso condicional**.

1. En la tabla Control de aplicaciones de acceso condicional Apps, examine la columna **controles disponibles** y compruebe que el **control de acceso** y el **control de sesión** aparecen para las aplicaciones.

    > [!NOTE]
    > Si el control de sesión no aparece para una aplicación, aún no está disponible para esa aplicación específica. Puede agregarla inmediatamente como una [aplicación personalizada](proxy-deployment-any-app.md)o puede abrir una solicitud para agregarla como una aplicación destacada haciendo clic en **solicitar control**de la sesión.
    >
    >![Solicitud de control de aplicaciones de acceso condicional](media/caac-request.png)

## Paso 4: probar la implementación<a name="test"></a>

1. Primero cierre la sesión de las sesiones existentes. A continuación, intente iniciar sesión en cada aplicación que se implementó correctamente. Inicie sesión con un usuario que coincida con la Directiva configurada en Azure AD.

1. En el portal de Cloud App Security, en **investigar**, seleccione **registro de actividad**y asegúrese de que se capturan las actividades de inicio de sesión de cada aplicación.

1. Puede filtrar haciendo clic en **Opciones avanzadas**y, a continuación, filtrar con el **origen es el control de acceso**.

    ![Filtrar mediante Azure AD acceso condicional](media/sso-logon.png)

1. Se recomienda iniciar sesión en aplicaciones de escritorio y móviles desde dispositivos administrados y no administrados. Esto es para asegurarse de que las actividades se capturan correctamente en el registro de actividad.<br />
Para comprobar que la actividad se ha capturado correctamente, haga clic en una actividad iniciar sesión de inicio de sesión único para abrir el cajón de actividades. Asegúrese de que la **etiqueta de agente de usuario** refleja correctamente si el dispositivo es un cliente nativo (es decir, una aplicación de escritorio o móvil) o si es un dispositivo administrado (compatible, unido a un dominio o certificado de cliente válido).

> [!NOTE]
> Una vez implementada, no se puede quitar una aplicación de la página Control de aplicaciones de acceso condicional. Siempre que no se establezca una sesión o una directiva de acceso en la aplicación, el Control de aplicaciones de acceso condicional no cambiará ningún comportamiento de la aplicación.

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [«ANTERIOR: Introducción a la Control de aplicaciones de acceso condicional](proxy-intro-aad.md)

> [!div class="nextstepaction"]
> [SIGUIENTE: incorporación e implementación de Control de aplicaciones de acceso condicional para cualquier aplicación»](proxy-deployment-any-app.md)

[!INCLUDE [Open support ticket](includes/support.md)]
