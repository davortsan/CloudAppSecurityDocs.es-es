---
title: Integrar Azure Active Directory Identity Protection con Cloud App Security
description: En este artículo se proporciona información sobre cómo aprovechar las alertas de Identity Protection en Cloud App Security para la detección de riesgos híbridas.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 03/24/2020
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: f5603102aa393c676b82fc179094526933e93f68
ms.sourcegitcommit: 2cf3c78a1b45a5b6ca534fdd12fd97afc51726e3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/26/2020
ms.locfileid: "80295786"
---
# <a name="azure-active-directory-identity-protection-integration"></a>Integración de Azure Active Directory Identity Protection

*Se aplica a: Microsoft Cloud App Security*

Microsoft Cloud App Security se integra con Azure Active Directory Identity Protection (Identity Protection) para proporcionar análisis de comportamiento de la entidad de usuario (UEBA) en un entorno híbrido. Para obtener más información sobre el aprendizaje automático y el análisis de comportamiento que proporciona Identity Protection, consulte [¿Qué es Identity Protection?](/azure/active-directory/identity-protection/overview-identity-protection).

## <a name="prerequisites"></a>Requisitos previos

- Una cuenta de administrador de Cloud App Security para habilitar la integración entre la protección de identidades y el Cloud App Security.

## <a name="enable-identity-protection"></a>Habilitar Identity Protection

> [!NOTE]
> La característica Identity Protection está habilitada de forma predeterminada. Sin embargo, si la característica estaba deshabilitada, puede seguir estos pasos para habilitarla.

Para habilitar la integración de Cloud App Security con Identity Protection:

1. En Cloud App Security, en el engranaje de configuración, seleccione **configuración**.

    ![Menú de configuración](media/azip-system-settings.png)

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
> Cuando la integración está deshabilitada, las alertas de Identity Protection existentes se mantienen de acuerdo con las directivas de retención de Cloud App Security.

## <a name="configure-identity-protection-policies"></a>Configurar directivas de Identity Protection

Las directivas de Identity Protection pueden ajustarse a las necesidades de la organización con el control deslizante gravedad. El control deslizante de sensibilidad le permite controlar qué alertas se ingestan. De esta manera, puede adaptar la detección según sus necesidades de cobertura y sus destinos (SNR).

Están disponibles las siguientes directivas:

|Directiva|Descripción|Estado predeterminado|Gravedad predeterminada|
|---|---|---|---|
|Credenciales perdidas|Muestra las alertas de credenciales perdidas, las credenciales válidas del usuario se han perdido|Habilitado|Bajo: recibir todas las alertas|
|Inicio de sesión peligroso|Agrega varias detecciones de inicio de sesión de riesgo, inicios de sesión no realizadas por el usuario|Habilitado|Alta: recepción de alertas de gravedad alta|

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Controlar las aplicaciones en la nube con directivas](control-cloud-apps-with-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]
