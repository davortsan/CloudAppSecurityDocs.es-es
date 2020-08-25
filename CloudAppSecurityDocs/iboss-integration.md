---
title: Integración de Cloud App Security con iboss
description: En este artículo se describe cómo integrar Microsoft Cloud App Security con iboss Secure Cloud Gateway para que Cloud Discovery funcione sin problemas y automatizar el bloqueo de aplicaciones no autorizadas.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 2/2/2019
ms.topic: how-to
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 8d849ed2b95577a805355eaae744ff81d2eb8176
ms.sourcegitcommit: 29a8e66c665f51d831516924ae4d9d8047b39276
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2020
ms.locfileid: "88781725"
---
# <a name="integrate-cloud-app-security-with-iboss"></a>Integración de Cloud App Security con iboss

*Se aplica a: Microsoft Cloud App Security*

Si trabaja con Cloud App Security y iboss, puede integrar los dos productos para mejorar la experiencia de seguridad de Cloud Discovery. iboss es una puerta de enlace en la nube segura e independiente que supervisa el tráfico de su organización y permite establecer directivas que bloqueen las transacciones. Juntos, Cloud App Security y iboss proporcionan las siguientes funcionalidades:

- Implementación fluida de Cloud Discovery: use iboss para redirigir el tráfico mediante proxy y enviarlo a Cloud App Security. Gracias a esto, se elimina la necesidad de instalar los recopiladores de registros en los puntos de conexión de la red para habilitar Cloud Discovery.
- Las funcionalidades de bloqueo de iboss se aplican automáticamente a las aplicaciones que haya establecido como no autorizadas en Cloud App Security.
- Mejore su portal de administración de iboss gracias a la valoración de riesgos de Cloud App Security de las 100 aplicaciones en la nube más importantes de su organización, que se pueden ver directamente en el portal de administración de iboss.

## <a name="prerequisites"></a>Requisitos previos

- Una licencia válida para Microsoft Cloud App Security
- Una licencia válida para iboss Secure Cloud Gateway (versión 9.1.100.0 o posterior)

## <a name="deployment"></a>Implementación

1. En el portal de Cloud App Security, realice los pasos de integración siguientes:
    1. Haga clic en el engranaje de configuración y seleccione **configuración de Cloud Discovery**.
    2. Haga clic en la pestaña **Carga automática del registro** y, luego, en **Agregar origen de datos**.
    3. En la página **Agregar origen de datos**, escriba la siguiente configuración:

        - Nombre: iboss
        - Origen: iboss Secure Cloud Gateway
        - Tipo de receptor = Syslog - UDP

        ![Origen de datos iboss](media/iboss-integration.png)

    4. Haga clic en **Ver ejemplo de archivo de registro previsto**. A continuación, haga clic en **Descargar registro de ejemplo** para ver un registro de detección de ejemplo y asegúrese de que coincida con los registros.<br />

1. Investigue las aplicaciones en la nube que se han detectado en la red. Para obtener más información y pasos de investigación, consulte [Trabajo con Cloud Discovery](working-with-cloud-discovery-data.md).

1. Las aplicaciones que se establecen como no autorizadas en Cloud App Security recibirán un ping por parte de iboss cada 10 minutos y, luego, iboss las bloqueará automáticamente. Para más información sobre las aplicaciones no autorizadas, consulte [Autorizar o no autorizar una aplicación](governance-discovery.md#BKMK_SanctionApp).

1. Si quiere configurar iboss para enviar registros de tráfico a Microsoft Cloud App Security, póngase en contacto con el equipo de soporte técnico de iboss.

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Controlar las aplicaciones en la nube con directivas](control-cloud-apps-with-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]
