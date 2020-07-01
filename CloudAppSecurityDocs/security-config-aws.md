---
title: Obtención de recomendaciones de configuración de seguridad para AWS
description: En este artículo se proporciona información sobre cómo obtener recomendaciones de configuración de seguridad en Cloud App Security mediante la integración de con Amazon Web Services.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 06/28/2020
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 904dc2c6a86d135502c81fd3037b9b8ca4459d99
ms.sourcegitcommit: b15034dd50142afd8e95de22a9232f711b1eae6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2020
ms.locfileid: "85625061"
---
# <a name="security-configuration-for-aws"></a>Configuración de seguridad para AWS

*Se aplica a: Microsoft Cloud App Security*

Microsoft Cloud App Security proporciona una evaluación de la configuración de seguridad de su entorno de Amazon Web Services. Esta evaluación proporciona recomendaciones de seguridad fundamentales basadas en la prueba comparativa de Center for Internet Security (CIS) para AWS.

## <a name="prerequisites"></a>Requisitos previos

- La central de seguridad de AWS debe estar configurada para todas las regiones de la cuenta de AWS. Para obtener más información, consulte [configuración del centro de seguridad de AWS](https://go.microsoft.com/fwlink/?linkid=2100208).
    > [!NOTE]
    > Si es la primera vez que habilita el centro de seguridad, puede tardar varias horas para que los datos iniciales estén disponibles.
- El Amazon Web Services debe estar conectado a Cloud App Security. Para obtener más información, consulte [Connect AWS to Microsoft Cloud App Security](connect-aws-to-microsoft-cloud-app-security.md).

## <a name="how-to-view-aws-security-recommendations"></a>Cómo ver las recomendaciones de seguridad de AWS

1. En Cloud App Security, vaya a **investigar**  >  **configuración de seguridad**y, a continuación, seleccione la pestaña **Amazon Web Services** .

    > [!NOTE]
    > Es posible que los cambios tarden hasta 15 minutos en surtir efecto.

    ![menú de configuración de seguridad](media/security-configuration-menu.png)

1. Puede filtrar las recomendaciones por tipo, por recurso y por cuentas. Además, puede hacer clic en el icono de configuración de seguridad ![Icono de ASC](media/asc-icon.png) para abrir la recomendación en Amazon Security hub para obtener más información y profundizar en la recomendación.

    ![configuración de seguridad](media/security-configuration-aws.png)

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Controlar las aplicaciones en la nube con directivas](control-cloud-apps-with-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]
