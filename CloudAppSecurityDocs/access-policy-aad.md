---
title: Creación de directivas de acceso de Cloud App Security para permitir y bloquear el acceso
description: En este artículo se describe el procedimiento para configurar una directiva de acceso al control de aplicaciones de acceso condicional de Cloud App Security para permitir y bloquear el acceso a las aplicaciones conectadas a través de Azure AD mediante las funcionalidades de proxy inverso.
ms.date: 01/05/2021
ms.topic: how-to
ms.openlocfilehash: 951cde88df62054cf005d26e602d27acfb5aba23
ms.sourcegitcommit: ee66e70f711aa11501e308e53b1a4b46f2175e4e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/05/2021
ms.locfileid: "97894610"
---
# <a name="access-policies"></a>Directivas de acceso

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Las directivas de acceso de Microsoft Cloud App Security permiten la supervisión en tiempo real y el control del acceso a aplicaciones en la nube en función del usuario, la ubicación, el dispositivo y la aplicación. Puede crear directivas de acceso para cualquier dispositivo, incluidos los dispositivos que no están Unión a Azure AD híbrido y que no están administrados por Microsoft Intune mediante la implementación de certificados de cliente en dispositivos administrados o mediante el uso de certificados existentes, como certificados MDM de terceros. Por ejemplo, puede implementar certificados de cliente en dispositivos administrados y después bloquear el acceso desde dispositivos que no tengan ningún certificado.

> [!NOTE]
> En lugar de permitir o bloquear el acceso por completo, con las [directivas de sesión](session-policy-aad.md) puede permitir el acceso mientras supervisa la sesión o limitar determinadas actividades de la sesión.

## <a name="prerequisites-to-using-access-policies"></a>Requisitos previos para usar las directivas de acceso

- Azure AD Premium licencia P1 o la licencia requerida por su solución de proveedor de identidades (IdP)
- Las aplicaciones en cuestión deben estar [implementadas con control de aplicaciones de acceso condicional](proxy-deployment-aad.md).
- Asegúrese de que ha configurado la solución IdP para que funcione con Cloud App Security, como se indica a continuación:
  - En el caso del [acceso condicional de Azure AD](/azure/active-directory/active-directory-conditional-access-azure-portal), consulte [Configuración de la integración con Azure AD](proxy-deployment-aad.md#configure-integration-with-azure-ad).
  - Para información sobre otras soluciones IdP, consulte [Configuración de la integración con otras soluciones IdP](proxy-deployment-aad.md#configure-integration-with-other-idp-solutions).

## <a name="create-a-cloud-app-security-access-policy"></a>Crear una directiva de acceso de Cloud App Security

Para crear una directiva de acceso, siga este procedimiento:

1. Vaya a **control**  >  **directivas**  >  **acceso condicional**.

1. Haga clic en **Crear directiva** y seleccione **Directiva de acceso**.

    ![Crear una directiva de acceso condicional](media/create-policy-from-conditional-access-tab.png)

1. En la ventana **Directiva de acceso**, asigne un nombre a la directiva, por ejemplo, *Bloquear el acceso desde dispositivos no administrados*.

1. En la sección **Actividades que coinciden con todo lo siguiente** de **Origen de la actividad**, seleccione más filtros de actividad para aplicarlos a la directiva. Los filtros incluyen las siguientes opciones:

    - **Etiqueta de dispositivo**: use este filtro para identificar los dispositivos no administrados.

    - **Ubicación**: use este filtro para identificar las ubicaciones desconocidas (por tanto, que entrañan riesgo).

    - **Dirección IP**: use este filtro para filtrar por direcciones IP o usar las etiquetas de dirección IP previamente asignadas.

    - **Etiqueta de agente de usuario**: use este filtro para habilitar la heurística que permite identificar las aplicaciones de escritorio y móviles. Este filtro se puede establecer en "igual a" o "no es igual a". Los valores se deben probar con las aplicaciones de escritorio y móviles para cada aplicación en la nube.

1. En **Acciones**, seleccione una de las siguientes opciones:

    - **Prueba**: establezca esta acción para permitir explícitamente el acceso según los filtros de directiva que establezca.

    - **Bloquear**: establezca esta acción para bloquear expresamente el acceso según los filtros de directiva que haya establecido.

1. Puede **crear una alerta para cada evento que coincida con la gravedad de directiva**, establecer un límite de alerta y seleccionar si quiere que la alerta llegue como un correo electrónico, como un mensaje de texto o ambas.

## <a name="related-videos"></a>Vídeos relacionados

> [!div class="nextstepaction"]
> [Seminario Web de Control de aplicaciones de acceso condicional](webinars.md#on-demand-webinars)

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [« ANTERIOR: Cómo crear una directiva de sesión](session-policy-aad.md)

> [!div class="nextstepaction"]
> [SIGUIENTE: Explorar casos de uso populares »](use-case-proxy-block-session-aad.md)

## <a name="see-also"></a>Consulte también

> [!div class="nextstepaction"]
> [Bloqueo de descargas en dispositivos no administrados mediante controles de sesión](use-case-proxy-block-session-aad.md)

> [!div class="nextstepaction"]
> [Solución de problemas de controles de sesión y acceso](troubleshooting-proxy.md)

[!INCLUDE [Open support ticket](includes/support.md)]