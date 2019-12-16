---
title: Integre la protección contra amenazas avanzada de Azure con Cloud App Security
description: En este artículo se proporciona información sobre cómo aprovechar la información sobre protección contra amenazas avanzada de Azure en Cloud App Security para la detección de riesgos híbridas.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 11/20/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 2278a7a156525450c2ad4d8e75ee7a1aeb98fb0b
ms.sourcegitcommit: 362ec5187cb13f152d240b75ed1ecebb5236b0ee
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/15/2019
ms.locfileid: "75033368"
---
# <a name="azure-advanced-threat-protection-integration"></a>Integración de protección contra amenazas avanzada de Azure

*Se aplica a: Microsoft Cloud App Security*

Microsoft Cloud App Security [se](https://docs.microsoft.com/azure-advanced-threat-protection/what-is-atp)integra con la protección contra amenazas avanzada de Azure (ATP de Azure) para proporcionar análisis del comportamiento de la entidad de usuario (UEBA) en un entorno híbrido, tanto en la aplicación en la nube como en el entorno local, para obtener más información, consulte [Tutorial: investigación de usuarios de riesgo](tutorial-ueba.md) para obtener más información sobre el aprendizaje automático y el análisis de comportamiento proporcionado por ATP de Azure.

## <a name="prerequisites"></a>Requisitos previos

Para realizar una investigación completa de los usuarios en un entorno híbrido, debe tener:

- Una licencia válida de Azure ATP conectada a la instancia de Active Directory
- Debe ser un administrador global para habilitar la integración entre ATP de Azure y Microsoft Cloud App Security
- Si no dispone de ATP de Azure, pruébelo ahora.

>[!NOTE]
>Si no tiene una suscripción para Microsoft Cloud App Security, todavía podrá usar el portal de Cloud App Security para obtener información sobre ATP de Azure.

## <a name="enable-azure-atp"></a>Habilitación de ATP de Azure

Para habilitar la integración de Cloud App Security con ATP de Azure:

1. En Cloud App Security, en el engranaje de configuración, seleccione **configuración**.

   ![Menú Configuración](media/azip-system-settings.png)

1. En **protección contra amenazas**, seleccione **ATP de Azure**.

    ![habilitación de la protección contra amenazas avanzada de Azure](media/aatp-integration.png)

1. Seleccione **conectar datos de ATP de Azure, incluidas las alertas y las actividades con Cloud App Security** y, a continuación, haga clic en **Guardar**.

> [!NOTE]
> Puede tardar hasta 12 horas hasta que la integración surta efecto.

Después de habilitar la integración de ATP de Azure, podrá ver las actividades locales para todos los usuarios de su organización. También obtendrá información avanzada sobre los usuarios que combinan alertas y actividades sospechosas en los entornos locales y en la nube. Además, las directivas de ATP de Azure aparecerán en la página directivas de Cloud App Security. Para obtener una lista de las directivas de ATP de Azure, consulte [alertas de seguridad](https://docs.microsoft.com/azure-advanced-threat-protection/suspicious-activity-guide).

## <a name="disable-azure-atp"></a>Deshabilitación de ATP de Azure

Para deshabilitar la integración de Cloud App Security con ATP de Azure:

1. En Cloud App Security, en el engranaje de configuración, seleccione **configuración**.

1. En **protección contra amenazas**, seleccione **ATP de Azure**.

1. Desactive **conectar datos de ATP de Azure, incluidas las alertas y las actividades con Cloud App Security** y, a continuación, haga clic en **Guardar**.

> [!NOTE]
> Los datos existentes de ATP de Azure se conservan de acuerdo con las directivas de retención de Cloud App Security, pero se quitan las evaluaciones de postura de seguridad de identidad.

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Controlar las aplicaciones en la nube con directivas](control-cloud-apps-with-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]
