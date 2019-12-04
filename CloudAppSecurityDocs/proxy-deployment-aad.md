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
ms.openlocfilehash: 290429e345e6b814a34a3e9214b5f69fdcbf7ddf
ms.sourcegitcommit: 7c93b6f93d2699d466b172590710ed01697bbdad
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74720926"
---
# <a name="deploy-conditional-access-app-control-for-featured-apps"></a>Implementación del Control de aplicaciones de acceso condicional para aplicaciones destacadas

*Se aplica a: Microsoft Cloud App Security*

Los controles de sesión de Microsoft Cloud App Security funcionan con las aplicaciones destacadas. Para obtener una lista de las aplicaciones que se incluyen en Cloud App Security trabajar de forma integrada, consulte [proteger aplicaciones con Microsoft Cloud App Security control de aplicaciones de acceso condicional](proxy-intro-aad.md#featured-apps).

## <a name="prerequisites"></a>Requisitos previos

Para implementar el Control de aplicaciones de acceso condicional para aplicaciones de Azure AD, necesita una [licencia válida de Azure AD Premium P1](https://docs.microsoft.com/azure/active-directory/license-users-groups) y otra de Cloud App Security.

## <a name="to-deploy-featured-apps"></a>Para implementar aplicaciones destacadas

Siga estos pasos para configurar las aplicaciones destacadas que se van a controlar mediante Microsoft Cloud App Security Control de aplicaciones de acceso condicional.

**Paso 1: [ir al portal de Azure ad y crear una directiva de acceso condicional para las aplicaciones y enrutar la sesión a Cloud App Security](#add-azure-ad)**

**Paso 2: [iniciar sesión en cada aplicación con un usuario con ámbito en la Directiva](#sign-in-scoped)**

**Paso 3: [comprobar que las aplicaciones están configuradas para usar controles de acceso y de sesión](#portal)**

**Paso 4: [probar la implementación](#test)**

## Paso 1: crear una directiva de prueba de acceso condicional Azure AD<a name="add-azure-ad"></a>

1. En Azure Active Directory, en **seguridad**, haga clic en **acceso condicional**.

1. Haga clic en **Nueva directiva** y cree una directiva.

1. En la sección **Usuarios** de la directiva de prueba, asigne un usuario de prueba o uno que se pueda usar para un primer inicio de sesión y su comprobación.

1. En la sección **Aplicaciones en la nube** de la directiva de PRUEBA, asigne las aplicaciones que quiera controlar con el control de aplicaciones de acceso condicional.

1. En **Sesión**, configure la directiva para que use cualquiera de las directivas integradas, **Solo supervisar** o **Bloquear descargas**. También puede seleccionar **Usar directiva personalizada** para establecer una directiva avanzada en el portal de Cloud App Security.

1. Opcionalmente, agregue cualquier **asignación de condiciones** o **control de acceso** que corresponda.

    ![Acceso condicional de Azure AD](media/azure-ad-caac-policy.png)

1. Haga clic en **Habilitar** y **Guardar**.

## Paso 2: iniciar sesión en cada aplicación con un usuario con ámbito en la Directiva<a name="sign-in-scoped"></a>

> [!NOTE]
> Antes de continuar, asegúrese de cerrar primero las sesiones existentes.

Después de crear la directiva, inicie sesión en cada aplicación configurada en esa directiva. Asegúrese de que inicia sesión con un usuario configurado en la directiva.

Cloud App Security sincronizará los detalles de la Directiva con sus servidores para cada nueva aplicación en la que inicie sesión. Este proceso puede tardar hasta un minuto.

## Paso 3: comprobar que las aplicaciones están configuradas para usar controles de acceso y de sesión<a name="portal"></a>

Las instrucciones anteriores le han ayudado a crear una directiva integrada de Cloud App Security para aplicaciones destacadas directamente en Azure AD. En este paso, compruebe que los controles de sesión y acceso estén configurados para estas aplicaciones.

1. En el portal de Cloud App Security, haga clic en el icono configuración engranaje ![configuración](media/settings-icon.png "icono de configuración")y seleccione **control de aplicaciones de acceso condicional**.

1. En la tabla Control de aplicaciones de acceso condicional Apps, examine la columna **controles disponibles** y compruebe que el **control de acceso** y el **control de sesión** aparecen para las aplicaciones.

    > [!NOTE]
    > Si el control de sesión no aparece para una aplicación, aún no está disponible para esa aplicación específica. Puede agregarla inmediatamente como una [aplicación personalizada](proxy-deployment-any-app.md)o puede abrir una solicitud para agregarla como una aplicación destacada haciendo clic en **solicitar control**de la sesión.
    >
    >![Solicitud del Control de aplicaciones de acceso condicional](media/caac-request.png)

## Paso 4: probar la implementación<a name="test"></a>

1. Primero, cierre cualquier sesión existente. Después, intente iniciar sesión en cada aplicación que se ha implementado correctamente. Inicie sesión con un usuario que coincida con la directiva configurada en Azure AD.

1. En el portal de Cloud App Security en **Investigar**, seleccione **Registro de actividad** y asegúrese de que se capturan las actividades de inicio de sesión de cada aplicación.

1. Puede filtrar haciendo clic en **Avanzadas** y, luego, mediante la opción **Origen es igual a Acceso condicional**.

    ![Filtrar por Acceso condicional de Azure AD](media/sso-logon.png)

1. Se recomienda que inicie sesión en aplicaciones de escritorio y móviles desde dispositivos administrados y no administrados. Esto es para asegurarse de que las actividades se capturan correctamente en el registro de actividad.<br />
Para confirmar que la actividad se captura correctamente, haga clic en un registro de inicio de sesión único en la actividad para abrir el cajón de actividad. Asegúrese de que la propiedad **Etiqueta de agente de usuario** refleja correctamente si el dispositivo es un cliente nativo (es decir, un aplicación de escritorio o móvil) o si es un dispositivo administrado (Compatible, Unido a dominio o Certificado de cliente válido).

> [!NOTE]
> Después de implementarse, no se puede quitar una aplicación de la página Control de aplicaciones de acceso condicional. Mientras no establezca una sesión o una directiva de acceso en la aplicación, el Control de aplicaciones de acceso condicional no cambiará el comportamiento de la aplicación.

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Cómo crear una directiva de acceso](access-policy-aad.md)

## <a name="see-also"></a>Consulta también

> [!div class="nextstepaction"]
> [Introducción a Control de aplicaciones de acceso condicional](proxy-intro-aad.md)

> [!div class="nextstepaction"]
> [Trabajo con el control de aplicaciones de acceso condicional de Cloud App Security](proxy-intro-aad.md)

> [!div class="nextstepaction"]
> [Implementar Control de aplicaciones de acceso condicional para cualquier aplicación»](proxy-deployment-any-app.md)

[!INCLUDE [Open support ticket](includes/support.md)]
