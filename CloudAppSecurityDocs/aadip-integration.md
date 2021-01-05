---
title: Integrar Azure Active Directory Identity Protection con Cloud App Security
description: En este artículo se proporciona información sobre cómo aprovechar las alertas de Identity Protection en Cloud App Security para la detección de riesgos híbridas.
ms.date: 12/27/2020
ms.topic: how-to
ms.openlocfilehash: f71e73dfd3ca8be7d6ed5e03847ac6e11e290818
ms.sourcegitcommit: 4900168878f42e9fa79873df4b7c2d81991b5b27
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/04/2021
ms.locfileid: "97857961"
---
# <a name="azure-active-directory-identity-protection-integration"></a>Integración de Azure Active Directory Identity Protection

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Microsoft Cloud App Security se integra con Azure Active Directory Identity Protection (Identity Protection) para proporcionar análisis de comportamiento de la entidad de usuario (UEBA) en un entorno híbrido. Para obtener más información sobre el aprendizaje automático y el análisis de comportamiento que proporciona Identity Protection, consulte [¿Qué es Identity Protection?](/azure/active-directory/identity-protection/overview-identity-protection).

## <a name="prerequisites"></a>Requisitos previos

- Una cuenta de administrador de Cloud App Security para habilitar la integración entre la protección de identidades y el Cloud App Security.

## <a name="enable-identity-protection"></a>Habilitación de Identity Protection

> [!NOTE]
> La característica Identity Protection está habilitada de forma predeterminada. Sin embargo, si la característica estaba deshabilitada, puede seguir estos pasos para habilitarla.

Para habilitar la integración de Cloud App Security con Identity Protection:

1. En Cloud App Security, en el engranaje de configuración, seleccione **configuración**.

    ![Menú Configuración](media/azip-system-settings.png)

1. En **protección contra amenazas**, seleccione **Azure ad Identity Protection**.

    ![habilitación de la protección contra amenazas avanzada de Azure](media/aadip-integration.png)

1. Seleccione **Habilitar la integración de alertas de Azure ad Identity Protection** y, a continuación, haga clic en **Guardar**.

Después de habilitar la integración de Identity Protection, podrá ver las alertas de todos los usuarios de su organización.

## <a name="disable-identity-protection"></a>Deshabilitar Identity Protection

Para deshabilitar la integración de Cloud App Security con Identity Protection:

1. En Cloud App Security, en el engranaje de configuración, seleccione **configuración**.

1. En **protección contra amenazas**, seleccione **Azure ad Identity Protection**.

1. Desactive **habilitar Azure ad Identity Protection integración de alertas** y, a continuación, haga clic en **Guardar**.

> [!NOTE]
>
> - Cuando la integración está deshabilitada, las alertas de Identity Protection existentes se mantienen de acuerdo con las directivas de retención de Cloud App Security.
> - Como Cloud App Security solo consume inicios de sesión interactivos de Azure AD, es posible que algunas alertas no muestren actividades relacionadas. Puede investigar estas actividades en el portal de Azure AD.

## <a name="configure-identity-protection-policies"></a>Configurar directivas de Identity Protection

Las directivas de Identity Protection pueden ajustarse a las necesidades de la organización con el control deslizante gravedad. El control deslizante de sensibilidad le permite controlar qué alertas se ingestan. De esta manera, puede adaptar la detección según sus necesidades de cobertura y sus destinos (SNR).

Están disponibles las siguientes directivas:

|Directiva|Description|Estado predeterminado|Gravedad predeterminada|
|---|---|---|---|
|Filtración de credenciales|Muestra las alertas de credenciales perdidas, las credenciales válidas del usuario se han perdido|habilitado|Bajo: recibir todas las alertas|
|Inicio de sesión peligroso|Agrega varias detecciones de inicio de sesión de riesgo, inicios de sesión no realizadas por el usuario|habilitado|Alta: recepción de alertas de gravedad alta|

> [!NOTE]
> Cloud App Security no envía notificaciones de correo electrónico para las alertas de Identity Protection. Sin embargo, puede configurar las notificaciones por correo electrónico en el portal de Identity Protection.

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Controlar las aplicaciones en la nube con directivas](control-cloud-apps-with-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]
