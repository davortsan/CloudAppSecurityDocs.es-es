---
title: Integración de Cloud App Security con seguridad de Menlo
description: En este artículo se describe cómo integrar Microsoft Cloud App Security con seguridad Menlo para un Cloud Discovery sin problemas y un bloque automatizado de aplicaciones no autorizadas.
ms.date: 11/09/2020
ms.topic: how-to
ms.openlocfilehash: 675a45375ef1e4a09c9a1369698512d9eac1f92f
ms.sourcegitcommit: d87372b47ca98e942c2bf94032a6a61902627d69
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/30/2020
ms.locfileid: "96311152"
---
# <a name="integrate-cloud-app-security-with-menlo-security"></a>Integración de Cloud App Security con seguridad de Menlo

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Si trabaja con la seguridad de Cloud App Security y Menlo, puede integrar los dos productos para mejorar su experiencia de Cloud Discovery de seguridad. Menlo Security, como una puerta de enlace web segura independiente, supervisa el tráfico de su organización, lo que le permite establecer directivas para el bloqueo de transacciones. Juntos, Cloud App Security y la seguridad Menlo proporcionan las siguientes capacidades:

- Implementación sin problemas de Cloud Discovery: Use la seguridad Menlo para crear un proxy del tráfico y enviarlo a Cloud App Security. Gracias a esto, se elimina la necesidad de instalar los recopiladores de registros en los puntos de conexión de la red para habilitar Cloud Discovery.
- Las funcionalidades de bloqueo de seguridad de Menlo se aplican automáticamente a las aplicaciones que establezca como no autorizadas en Cloud App Security.

## <a name="prerequisites"></a>Requisitos previos

- Una licencia válida para Microsoft Cloud App Security o una licencia válida para Azure Active Directory Premium P1
- Una licencia válida para la seguridad de Menlo

## <a name="deployment"></a>Implementación

1. Inicie sesión en el portal de administración de Menlo y use la guía de configuración de la [integración de seguridad de Menlo con Microsoft Cloud Access Security](https://admin.menlosecurity.com/docs/guides/web_admin_settings_casb.html?highlight=microsoft) para integrar los productos.

1. Investigue las aplicaciones en la nube que se han detectado en la red. Para obtener más información y pasos de investigación, consulte [Trabajo con Cloud Discovery](working-with-cloud-discovery-data.md).
1. A cualquier aplicación que establezca como no autorizada en Cloud App Security se hará ping por la seguridad de Menlo cada dos horas y, a continuación, se bloqueará automáticamente por la seguridad de Menlo. Para más información sobre las aplicaciones no autorizadas, consulte [Autorizar o no autorizar una aplicación](governance-discovery.md#BKMK_SanctionApp).

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Controlar las aplicaciones en la nube con directivas](control-cloud-apps-with-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]
