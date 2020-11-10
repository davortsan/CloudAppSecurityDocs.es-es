---
title: Integre Microsoft defender para identidad con Cloud App Security
description: En este artículo se proporciona información sobre cómo aprovechar Microsoft defender para obtener información sobre identidades en Cloud App Security para la detección de riesgos híbridos.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 11/08/2020
ms.topic: how-to
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 0c5bb0d20a4e82280841d95352181739be8ea4fa
ms.sourcegitcommit: 66d818441eaae1e07c4bb2ce35bbcb833febf622
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/10/2020
ms.locfileid: "94428115"
---
# <a name="microsoft-defender-for-identity-integration"></a>Microsoft defender para la integración de identidades

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Microsoft Cloud App Security se integra con Microsoft defender para que la identidad proporcione análisis del comportamiento de la entidad de usuario (UEBA) en un entorno híbrido, tanto en la aplicación en la nube como en el entorno local, para obtener más información, consulte [Tutorial: investigar usuarios de riesgo](tutorial-ueba.md). Para obtener más información sobre el aprendizaje automático y el análisis de comportamiento proporcionado por defender for Identity, vea [¿Qué es defender para Identity?](/defender-for-identity/what-is)

## <a name="prerequisites"></a>Requisitos previos

Para realizar una investigación completa de los usuarios en un entorno híbrido, debe tener:

- Una licencia válida de Microsoft defender para la identidad conectada a la instancia de Active Directory
- Debe ser un administrador global de Azure Active Directory para habilitar la integración entre defender para identidad y Cloud App Security

> [!NOTE]
>
> - Si no tiene una suscripción para Microsoft Cloud App Security, todavía podrá usar Cloud App Security para obtener defender para obtener información de identidades.
> - Defender para administradores de identidad puede requerir nuevos permisos para obtener acceso a Cloud App Security. Para información sobre cómo asignar permisos a Cloud App Security, consulte [Administrar acceso de administrador](manage-admins.md).

## <a name="enable-defender-for-identity"></a>Habilitar defender para identidad

Para habilitar la integración de Cloud App Security con defender para la identidad:

1. En Cloud App Security, en el engranaje de configuración, seleccione **configuración**.

    ![Menú Configuración](media/azip-system-settings.png)

1. En **protección contra amenazas** , seleccione **Microsoft defender para identidad**.

    ![habilitación de la protección contra amenazas avanzada de Azure](media/mdi-integration.png)

1. Seleccione **Habilitar Microsoft defender para la integración de datos de identidad** y, a continuación, haga clic en **Guardar**.

> [!NOTE]
> Puede tardar hasta 12 horas hasta que la integración surta efecto.

Después de habilitar defender para la integración de identidades, podrá ver las actividades locales para todos los usuarios de su organización. También obtendrá información avanzada sobre los usuarios que combinan alertas y actividades sospechosas en los entornos locales y en la nube. Además, las directivas de defender para identidad aparecerán en la página directivas de Cloud App Security. Para obtener una lista de las directivas de identidad de defender, consulte [alertas de seguridad](/defender-for-identity/suspicious-activity-guide). Para editar estas directivas, consulte [exclusión de entidades de detecciones](/defender-for-identity/excluding-entities-from-detections).

También debe usar los vínculos **defender for Identity Configuration** para configurar defender para la configuración de identidades que sean relevantes para Cloud App Security. Use la siguiente información para obtener más información acerca de estas opciones:

- [Configuración de Microsoft defender para los sensores de identidad](/defender-for-identity/install-step5)
- [Configurar cuentas de servicio de directorio](/defender-for-identity/install-step2)
- [Configurar cuentas RADIUS para VPN](/defender-for-identity/install-step6-vpn)
- [Acceder a Microsoft defender para Identity Health Center](/defender-for-identity/health-center)

## <a name="disable-defender-for-identity"></a>Deshabilitar defender para identidad

Para deshabilitar la integración de Cloud App Security con defender para la identidad:

1. En Cloud App Security, en el engranaje de configuración, seleccione **configuración**.

1. En **protección contra amenazas** , seleccione **Microsoft defender para identidad**.

1. Desactive **Habilitar Microsoft defender para la integración de datos de identidad** y haga clic en **Guardar**.

> [!NOTE]
> Cuando se deshabilita la integración, el defender existente para los datos de identidad se mantiene de acuerdo con las directivas de retención de Cloud App Security, pero se quita la sección de evaluaciones de postura de seguridad de identidad.

## <a name="known-issues"></a>Problemas conocidos

### <a name="missing-siem-alert-updates"></a>Actualizaciones de alertas de SIEM que faltan

Este problema afecta a las alertas que se desencadenan más de una vez. La primera instancia de la alerta se envía al SIEM, pero no se envían los desencadenadores posteriores de la misma alerta.

#### <a name="resolution"></a>Solución

En este caso, no hay ninguna solución conocida.

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Controlar las aplicaciones en la nube con directivas](control-cloud-apps-with-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]