---
title: Integre la protección contra amenazas avanzada de Azure con Cloud App Security
description: En este artículo se proporciona información sobre cómo aprovechar la información sobre protección contra amenazas avanzada de Azure en Cloud App Security para la detección de riesgos híbridas.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 03/24/2020
ms.topic: how-to
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 33ccea97fd5b41802d7f8b12fe7413c5bd76d8a6
ms.sourcegitcommit: 870ca47381a36b4bc04e1ccb9b2a522944431fed
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/27/2020
ms.locfileid: "88963597"
---
# <a name="azure-advanced-threat-protection-integration"></a>Integración de protección contra amenazas avanzada de Azure

*Se aplica a: Microsoft Cloud App Security*

Microsoft Cloud App Security se integra con protección contra amenazas avanzada de Azure (ATP de Azure) para proporcionar análisis del comportamiento de la entidad de usuario (UEBA) en un entorno híbrido, tanto en la aplicación en la nube como en el entorno local, para obtener más información, consulte [Tutorial: investigar usuarios de riesgo](tutorial-ueba.md). Para obtener más información sobre el aprendizaje automático y el análisis de comportamiento proporcionado por ATP de Azure, consulte [¿Qué es ATP de Azure?](/azure-advanced-threat-protection/what-is-atp)

## <a name="prerequisites"></a>Requisitos previos

Para realizar una investigación completa de los usuarios en un entorno híbrido, debe tener:

- Una licencia válida de Azure ATP conectada a la instancia de Active Directory
- Debe ser un administrador global de Azure Active Directory para habilitar la integración entre ATP de Azure y Cloud App Security

> [!NOTE]
>
> - Si no tiene una suscripción para Microsoft Cloud App Security, podrá seguir usando Cloud App Security para obtener información sobre ATP de Azure.
> - Los administradores de Azure ATP pueden requerir nuevos permisos para obtener acceso a Cloud App Security. Para información sobre cómo asignar permisos a Cloud App Security, consulte [Administrar acceso de administrador](manage-admins.md).

## <a name="enable-azure-atp"></a>Habilitación de ATP de Azure

Para habilitar la integración de Cloud App Security con ATP de Azure:

1. En Cloud App Security, en el engranaje de configuración, seleccione **configuración**.

    ![Menú Configuración](media/azip-system-settings.png)

1. En **protección contra amenazas**, seleccione **ATP de Azure**.

    ![habilitación de la protección contra amenazas avanzada de Azure](media/aatp-integration.png)

1. Seleccione **Habilitar la integración de datos de ATP de Azure** y haga clic en **Guardar**.

> [!NOTE]
> Puede tardar hasta 12 horas hasta que la integración surta efecto.

Después de habilitar la integración de ATP de Azure, podrá ver las actividades locales para todos los usuarios de su organización. También obtendrá información avanzada sobre los usuarios que combinan alertas y actividades sospechosas en los entornos locales y en la nube. Además, las directivas de ATP de Azure aparecerán en la página directivas de Cloud App Security. Para obtener una lista de las directivas de ATP de Azure, consulte [alertas de seguridad](/azure-advanced-threat-protection/suspicious-activity-guide).

También debe usar los vínculos de **configuración de ATP de Azure** para configurar las opciones de ATP de Azure que son relevantes para Cloud App Security. Use la siguiente información para obtener más información acerca de estas opciones:

- [Configuración de sensores de ATP de Azure](/azure-advanced-threat-protection/install-atp-step5)
- [Configurar cuentas de servicio de directorio](/azure-advanced-threat-protection/install-atp-step2)
- [Configurar cuentas RADIUS para VPN](/azure-advanced-threat-protection/install-atp-step6-vpn)
- [Acceder al centro de mantenimiento de ATP de Azure](/azure-advanced-threat-protection/atp-health-center)

## <a name="disable-azure-atp"></a>Deshabilitación de ATP de Azure

Para deshabilitar la integración de Cloud App Security con ATP de Azure:

1. En Cloud App Security, en el engranaje de configuración, seleccione **configuración**.

1. En **protección contra amenazas**, seleccione **ATP de Azure**.

1. Desactive **Habilitar la integración de datos de ATP de Azure** y haga clic en **Guardar**.

> [!NOTE]
> Cuando la integración está deshabilitada, los datos existentes de ATP de Azure se conservan de acuerdo con las directivas de retención de Cloud App Security, pero se quita la sección evaluaciones de postura de seguridad de identidad.

## <a name="known-issues"></a>Problemas conocidos

### <a name="missing-siem-alert-updates"></a>Actualizaciones de alertas de SIEM que faltan

Este problema afecta a las alertas que se desencadenan más de una vez. La primera instancia de la alerta se envía al SIEM, pero no se envían los desencadenadores posteriores de la misma alerta.

#### <a name="resolution"></a>Solución

En este caso, no hay ninguna solución conocida.

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Controlar las aplicaciones en la nube con directivas](control-cloud-apps-with-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]