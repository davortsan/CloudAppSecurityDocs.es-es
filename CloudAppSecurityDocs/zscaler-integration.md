---
title: Integración de Cloud App Security con Zscaler
description: En este artículo se describe cómo integrar Microsoft Cloud App Security con Zscaler para conseguir un Cloud Discovery sin problemas y el bloqueo automatizado de aplicaciones no autorizadas.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 03/03/2020
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: f4f7b05caa3c516294f08864b0a711b71be047f3
ms.sourcegitcommit: 3f0693bf32fef5b4819c51ca7eeaee751eb03df6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84611178"
---
# <a name="integrate-cloud-app-security-with-zscaler"></a>Integración de Cloud App Security con Zscaler

*Se aplica a: Microsoft Cloud App Security*

Si trabaja con Cloud App Security y Zscaler, puede integrar los dos productos para mejorar la seguridad de la experiencia de Cloud Discovery. Zscaler, como proxy en la nube independiente, supervisa el tráfico de la organización, lo que le permite establecer directivas para bloquear transacciones. Juntos, Cloud App Security y Zscaler proporcionan las siguientes funcionalidades:

- Implementación sin problemas de Cloud Discovery: Use Zscaler para crear un proxy del tráfico y enviarlo a Cloud App Security. Gracias a esto, se elimina la necesidad de instalar los recopiladores de registros en los puntos de conexión de la red para habilitar Cloud Discovery.
- Las funcionalidades de bloque de Zscaler se aplican automáticamente a las aplicaciones que haya establecido como no autorizadas en Cloud App Security.
- Mejore el portal de Zscaler con la evaluación de riesgos de Cloud App Security para 200 aplicaciones líderes en la nube que pueden verse directamente en el portal de Zscaler.

## <a name="prerequisites"></a>Requisitos previos

- Una licencia válida para Microsoft Cloud App Security o una licencia válida para Azure Active Directory Premium P1
- Una licencia válida para Zscaler Cloud 5.6
- Una suscripción activa de Zscaler NSS

## <a name="deployment"></a>Implementación

1. En el portal de Zscaler, realice los pasos para completar la [integración de asociados de Zscaler con Microsoft Cloud App Security](https://help.zscaler.com/zia/configuring-mcas-integration).
2. En el portal de Cloud App Security, realice los pasos de integración siguientes:
    1. Haga clic en el engranaje de configuración y seleccione **Configuración de Cloud Discovery**.
    2. Haga clic en la pestaña **Carga automática del registro** y luego en **Agregar origen de datos**.
    3. En la página **Agregar origen de datos**, escriba la siguiente configuración:

        - Nombre = NSS
        - Origen = Zscaler QRadar LEEF
        - Tipo de receptor = Syslog - UDP

        ![Zscaler de origen de datos](media/data-source-zscaler.png)

        > [!NOTE]
        > Asegúrese de que el nombre del origen de datos es idéntico al nombre de fuente utilizado al crear la Cloud App Security fuente NSS. Para obtener más información, consulte [agregar Cloud App Security fuentes NSS](https://help.zscaler.com/zia/adding-mcas-nss-feeds).

    4. Haga clic en **Ver ejemplo de archivo de registro previsto**. A continuación, haga clic en **Descargar registro de ejemplo** para ver un registro de detección de ejemplo y asegúrese de que coincida con los registros.<br />

3. Investigue las aplicaciones en la nube que se han detectado en la red. Para obtener más información y pasos de investigación, consulte [Trabajo con Cloud Discovery](working-with-cloud-discovery-data.md).

4. Las aplicaciones que se establecen como no autorizadas en Cloud App Security recibirán un ping por parte de Zscaler cada dos horas y luego Zscaler las bloqueará automáticamente. Para más información sobre las aplicaciones no autorizadas, consulte [Autorizar o no autorizar una aplicación](governance-discovery.md#BKMK_SanctionApp).

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Control de aplicaciones en la nube con directivas](control-cloud-apps-with-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]
