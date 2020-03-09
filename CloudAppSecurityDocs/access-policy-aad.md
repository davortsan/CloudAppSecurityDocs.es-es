---
title: Crear directivas de acceso Cloud App Security para permitir y bloquear el acceso
description: En este artículo se describe el procedimiento para configurar una directiva de acceso Control de aplicaciones de acceso condicional de Cloud App Security para permitir y bloquear el acceso a las aplicaciones conectadas a través de Azure AD mediante capacidades de proxy inverso.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 12/10/2018
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 5ab52bf417a6a0a6fea583fac9f64f70ea78e4a3
ms.sourcegitcommit: 3f6ef6b97a0953470135d115323a00cf11441ab7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/08/2020
ms.locfileid: "78927747"
---
# <a name="access-policies"></a>Directivas de acceso

*Se aplica a: Microsoft Cloud App Security*

Las directivas de acceso Microsoft Cloud App Security permiten la supervisión en tiempo real y el control del acceso a las aplicaciones en la nube en función del usuario, la ubicación, el dispositivo y la aplicación. Puede crear directivas de acceso para cualquier dispositivo, incluidos los dispositivos que no están Unidos a un dominio y no administrados por Windows Intune, mediante la implementación de certificados de cliente en dispositivos administrados o mediante el uso de certificados existentes, como certificados MDM de terceros. Por ejemplo, puede implementar certificados de cliente en dispositivos administrados y, a continuación, bloquear el acceso desde dispositivos sin un certificado.

> [!NOTE]
> En lugar de permitir o bloquear el acceso por completo, con [las directivas de sesión](session-policy-aad.md) puede permitir el acceso mientras supervisa la sesión o limitar las actividades de sesión específicas.

## <a name="prerequisites-to-using-access-policies"></a>Requisitos previos para el uso de directivas de acceso

- Licencia de Azure AD Premium P1
- Las aplicaciones pertinentes deben [implementarse con control de aplicaciones de acceso condicional](proxy-deployment-aad.md)
- Debe haber una [Directiva de acceso condicional Azure ad](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal) que redirija a los usuarios a Microsoft Cloud App Security, como se describe a continuación.

> [!NOTE]
> - Las directivas de acceso también admiten aplicaciones que están configuradas con proveedores de identidades distintos de Azure AD. Para obtener más información, envíe un correo electrónico a mcaspreview@microsoft.com.

## <a name="create-an-azure-ad-conditional-access-policy"></a>Creación de una directiva de acceso condicional Azure AD

Azure Active Directory las directivas de acceso condicional y las directivas de sesión de Cloud App Security funcionan conjuntamente para examinar cada sesión de usuario y tomar decisiones de directiva para cada aplicación. Para configurar una directiva de acceso condicional en Azure AD, siga este procedimiento:

1. Configure una [Azure ad Directiva de acceso condicional](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal) con asignaciones para el usuario o grupo de usuarios y la aplicación que desea controlar con control de aplicaciones de acceso condicional.

    > [!NOTE]
    > Esta directiva afectará solo a las aplicaciones que se [implementaron con control de aplicaciones de acceso condicional](proxy-deployment-aad.md) .

2. Para enrutar a los usuarios a Microsoft Cloud App Security, seleccione el **uso de control de aplicaciones de acceso condicional restricciones aplicadas** en **sesión**.

## <a name="create-a-cloud-app-security-access-policy"></a>Creación de una directiva de acceso Cloud App Security

Para crear una nueva Directiva de acceso, siga este procedimiento:

1. En el portal, seleccione **control** y, después, **directivas**.
2. En la página **directivas** , haga clic en **crear Directiva** y seleccione **Directiva de acceso**.

3. En la ventana **Directiva de acceso** , asigne un nombre a la Directiva, como *bloquear el acceso desde dispositivos no administrados*.

4. En la sección **actividades que coinciden con todo de la siguiente** , en origen de la **actividad**, seleccione los filtros de actividad adicionales que se van a aplicar a la Directiva. Los filtros incluyen las siguientes opciones:

    - **Etiquetas de dispositivo**: Use este filtro para identificar los dispositivos no administrados.

    - **Ubicación**: Use este filtro para identificar ubicaciones desconocidas (y, por tanto, arriesgadas).

    - **Dirección IP**: Use este filtro para filtrar por direcciones IP o usar etiquetas de dirección IP asignadas previamente.

    - **Etiqueta de agente de usuario**: Use este filtro para habilitar la heurística a fin de identificar aplicaciones móviles y de escritorio. Este filtro se puede establecer en es igual a o no es igual a. Los valores se deben probar con las aplicaciones móviles y de escritorio de cada aplicación en la nube.

5. En **acciones**, seleccione una de las siguientes opciones:

    - **Prueba**: establezca esta acción para permitir explícitamente el acceso según los filtros de directiva que establezca.

    - **Bloquear**: establezca esta acción para bloquear explícitamente el acceso según los filtros de directiva que establezca.

6. Puede **crear una alerta para cada evento coincidente con la gravedad de la Directiva** y establecer un límite de alertas y seleccionar si desea que la alerta sea un correo electrónico, un mensaje de texto o ambos.

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [«ANTERIOR: Cómo crear una directiva de sesión](session-policy-aad.md)

> [!div class="nextstepaction"]
> [SIGUIENTE: explorar los casos de uso más populares»](use-case-proxy-block-session-aad.md)

## <a name="see-also"></a>Vea también

> [!div class="nextstepaction"]
> [Bloqueo de descargas en dispositivos no administrados mediante controles de sesión](use-case-proxy-block-session-aad.md)

[!INCLUDE [Open support ticket](includes/support.md)]
