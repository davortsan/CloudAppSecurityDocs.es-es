---
title: Obtener recomendaciones de configuración de seguridad para AWS-Cloud App Security | Microsoft Docs
description: En este artículo se proporciona información sobre cómo obtener recomendaciones de configuración de seguridad en Cloud App Security mediante la integración de con Amazon Web Services.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 8/1/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: c6d8f8af-867b-43ab-adee-f06520577fe7
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 40d8d1f578f826f1782cfbf643f8b2db136f24d2
ms.sourcegitcommit: 8a49c166424fea83853b0a6895212367526abe78
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2019
ms.locfileid: "71085001"
---
# <a name="security-configuration-for-aws"></a>Configuración de seguridad para AWS

*Se aplica a: Microsoft Cloud App Security*

Microsoft Cloud App Security proporciona una evaluación de la configuración de seguridad de su entorno de Amazon Web Services. Esta evaluación proporciona recomendaciones de seguridad fundamentales basadas en la prueba comparativa de Center for Internet Security (CIS) para AWS.

## <a name="prerequisites"></a>Requisitos previos

- La central de seguridad de AWS debe estar configurada para todas las regiones de la cuenta de AWS. Para obtener más información, consulte [configuración del centro de seguridad de AWS](https://go.microsoft.com/fwlink/?linkid=2100208).
    > [!NOTE]
    > Si es la primera vez que habilita el centro de seguridad, puede tardar varias horas para que los datos iniciales estén disponibles.
- El Amazon Web Services debe estar conectado a Cloud App Security. Para obtener más información, consulte [Connect AWS to Microsoft Cloud App Security](connect-aws-to-microsoft-cloud-app-security.md).

## <a name="how-to-view-aws-security-recommendation"></a>Cómo ver la recomendación de seguridad de AWS

1. En Cloud App Security, vaya a **investigar** > **configuración de seguridad**y, a continuación, seleccione la pestaña **Amazon Web Services** .
    - Microsoft Cloud App Security proporciona recomendaciones únicamente para las 50 suscripciones principales.
    - Es posible que los cambios tarden hasta 15 minutos en surtir efecto.

     ![menú de configuración de seguridad](media/security-configuration-menu.png)

1. Puede filtrar las recomendaciones por tipo, por recurso y por cuentas. Además, puede hacer clic en el icono de configuración de seguridad ![Icono de ASC](./media/asc-icon.png) para abrir la recomendación en Amazon Security hub para obtener más información y profundizar en la recomendación.

   ![configuración de seguridad](media/security-configuration-aws.png)

## <a name="next-steps"></a>Pasos siguientes 
[Controlar las aplicaciones en la nube con directivas](control-cloud-apps-with-policies.md)

[Los clientes Premier también pueden crear una solicitud de soporte técnico directamente en el portal Premier.](https://premier.microsoft.com/)  
  
