---
title: Integración de Cloud App Security con Corrata
description: En este artículo se describe cómo integrar Microsoft Cloud App Security con Corrata para un Cloud Discovery sin problemas y un bloque automatizado de aplicaciones no autorizadas.
ms.date: 05/17/2020
ms.topic: how-to
ms.openlocfilehash: b9ec2e83bd99db8c4e884e371edfa5be689813a0
ms.sourcegitcommit: d87372b47ca98e942c2bf94032a6a61902627d69
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/30/2020
ms.locfileid: "96312376"
---
# <a name="integrate-cloud-app-security-with-corrata"></a>Integración de Cloud App Security con Corrata

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Si trabaja con Cloud App Security y Corrata, puede integrar los dos productos para mejorar su experiencia de Cloud Discovery de seguridad para el uso de aplicaciones móviles. Corrata, como puerta de enlace móvil local, supervisa el tráfico de su organización desde dispositivos móviles, lo que permite establecer directivas para el bloqueo de transacciones. Juntos, Cloud App Security y Corrata proporcionan las siguientes capacidades:

- Implementación sin problemas de Cloud Discovery: Use Corrata para recopilar el tráfico del dispositivo móvil y enviarlo a Cloud App Security. Gracias a esto, se elimina la necesidad de instalar los recopiladores de registros en los puntos de conexión de la red para habilitar Cloud Discovery.
- Las funcionalidades de bloqueo de Corrata se aplican automáticamente en las aplicaciones que establezca como no autorizadas en Cloud App Security.
- Mejore el portal de Corrata con la evaluación de riesgos de Cloud App Security para las principales aplicaciones en la nube, que se pueden ver directamente en el portal de Corrata.

## <a name="prerequisites"></a>Requisitos previos

- Una licencia válida para Microsoft Cloud App Security
- Una licencia válida para Corrata Cloud

## <a name="deployment"></a>Implementación

1. En el portal de Corrata, siga los pasos para completar la [integración de asociados de Corrata con Microsoft Cloud App Security](https://corrata.com/microsoft-mcas-onboarding).
2. En el portal de Cloud App Security, realice los pasos de integración siguientes:
    1. Haga clic en el engranaje de configuración y seleccione **Configuración de Cloud Discovery**.
    2. Haga clic en la pestaña **Carga automática del registro** y luego en **Agregar origen de datos**.
    3. En la página **Agregar origen de datos**, escriba la siguiente configuración:

        - Nombre = Corrata
        - Source = Corrata
        - Tipo de receptor = FTP

        ![origen de datos Corrata](media/data-source-corrata.png)

    4. Haga clic en **Ver ejemplo de archivo de registro previsto**. A continuación, haga clic en **Descargar registro de ejemplo** para ver un registro de detección de ejemplo y asegúrese de que coincida con los registros.

3. Investigue las aplicaciones en la nube que se han detectado en la red. Para obtener más información y pasos de investigación, consulte [Trabajo con Cloud Discovery](working-with-cloud-discovery-data.md).

4. A cualquier aplicación que establezca como no autorizada en Cloud App Security se hará ping por Corrata y, a continuación, Corrata la bloqueará automáticamente. Para más información sobre las aplicaciones no autorizadas, consulte [Autorizar o no autorizar una aplicación](governance-discovery.md#BKMK_SanctionApp).

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Controlar las aplicaciones en la nube con directivas](control-cloud-apps-with-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]
