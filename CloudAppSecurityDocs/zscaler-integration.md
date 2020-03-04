---
title: Integración de Cloud App Security con Zscaler
description: En este artículo se describe cómo integrar Microsoft Cloud App Security con Zscaler para un Cloud Discovery sin problemas y un bloque automatizado de aplicaciones no autorizadas.
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
ms.openlocfilehash: bc418943f4825c7433401f271d710333066039cc
ms.sourcegitcommit: 5a0ea6fe5b90aafadb90da25854dabc4cf05d5fc
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/03/2020
ms.locfileid: "78238381"
---
# <a name="integrate-cloud-app-security-with-zscaler"></a>Integración de Cloud App Security con Zscaler

*Se aplica a: Microsoft Cloud App Security*

Si trabaja con Cloud App Security y Zscaler, puede integrar los dos productos para mejorar su experiencia de Cloud Discovery de seguridad. Zscaler, como un proxy en la nube independiente, supervisa el tráfico de su organización, lo que le permite establecer directivas para el bloqueo de transacciones. Juntos, Cloud App Security y Zscaler proporcionan las siguientes capacidades:

- Implementación sin problemas de Cloud Discovery: el uso de Zscaler para crear un proxy del tráfico y enviarlo a Cloud App Security elimina la necesidad de instalar recopiladores de registros en los puntos de conexión de la red para habilitar Cloud Discovery.
- Las funcionalidades de bloqueo de Zscaler se aplican automáticamente en las aplicaciones que establezca como no autorizadas en Cloud App Security.
- Mejore el portal de Zscaler con la evaluación de riesgos de Cloud App Security para las aplicaciones de nube líderes de 200, que se pueden ver directamente en el portal de Zscaler.

## <a name="prerequisites"></a>Requisitos previos

- Una licencia válida para Microsoft Cloud App Security
- Una licencia válida para Zscaler Cloud 5,6
- Una suscripción a Zscaler NSS activa

## <a name="deployment"></a>Implementación

1. En el portal de Zscaler, siga los pasos para completar la [integración de asociados de Zscaler con Microsoft Cloud App Security](https://help.zscaler.com/zia/configuring-mcas-integration).
2. En el portal de Cloud App Security, lleve a cabo los siguientes pasos de integración:
    1. Haga clic en el engranaje de configuración y seleccione **configuración de Cloud Discovery**.
    2. Haga clic en la pestaña **carga de registro automática** y, a continuación, haga clic en **Agregar origen de datos**.
    3. En la página **Agregar origen de datos** , escriba la siguiente configuración:

        - Nombre = NSS
        - Source = Zscaler QRadar LEEF
        - Tipo de receptor = syslog-UDP

        ![origen de datos Zscaler](media/data-source-zscaler.png)

        > [!NOTE]
        > Asegúrese de que el nombre del origen de datos es idéntico al nombre de fuente utilizado al crear la Cloud App Security fuente NSS. Para obtener más información, consulte [agregar Cloud App Security fuentes NSS](https://help.zscaler.com/zia/adding-mcas-nss-feeds).

    4. Haga clic en **ver ejemplo de archivo de registro esperado**. A continuación, haga clic en **Descargar registro de ejemplo** para ver un registro de detección de ejemplo y asegúrese de que coincide con los registros.<br />

3. Investigue las aplicaciones en la nube detectadas en la red. Para obtener más información y los pasos de investigación, consulte [trabajar con Cloud Discovery](working-with-cloud-discovery-data.md).

4. Cualquier aplicación que establezca como no autorizada en Cloud App Security se hará ping en Zscaler cada dos horas y, a continuación, Zscaler la bloqueará automáticamente. Para obtener más información sobre cómo no autorizar aplicaciones, consulte autorización o no autorización de [una aplicación](governance-discovery.md#BKMK_SanctionApp).

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Controlar las aplicaciones en la nube con directivas](control-cloud-apps-with-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]
