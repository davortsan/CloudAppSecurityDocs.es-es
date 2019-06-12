---
title: Integración de la protección contra amenazas avanzada de Azure con Cloud App Security
description: En este artículo se proporciona información sobre cómo aprovechar la información de protección contra amenazas avanzada de Azure en Cloud App Security para la detección de riesgos híbrido.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: rkarlin
ms.date: 6/21/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 63e82b47-bb08-4614-af55-f85d04edfc5a
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 3d5563b73c8b813608c5fd5bc0ea9120ba930e61
ms.sourcegitcommit: 9f671d5dd5e5da023d598425442d8736546ca183
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/11/2019
ms.locfileid: "66837733"
---
# <a name="azure-information-protection-integration"></a>Integración de Azure Information Protection

*Se aplica a: Microsoft Cloud App Security*

Microsoft Cloud App Security se integra con la protección de amenazas avanzada (ATP de Azure) Azure para proporcionar análisis de comportamiento de entidades (UEBA) de usuario en un entorno híbrido - aplicación de nube y locales. Para obtener más información sobre el aprendizaje automático y análisis de comportamiento proporcionado por ATP de Azure, consulte [What ' s ATP de Azure?](https://docs.microsoft.com/azure-advanced-threat-protection/what-is-atp).

Mediante la integración con ATP de Azure, el portal de Cloud App Security proporcionará alertas y conocimiento a partir de:
- Microsoft Cloud App Security, que identifica ataques dentro de una sesión en la nube, que cubre no sólo los productos de Microsoft, sino también las aplicaciones de terceros
- Azure protección contra amenazas avanzada, que utiliza aprendizaje automático y análisis de comportamiento para identificar ataques a través de su red local
- Azure Active Directory Identity Protection, que detecta e impide proactivamente los riesgos de usuario e inicio de sesión a las identidades de la nube


## <a name="prerequisites"></a>Requisitos previos

Para la investigación de usuario completo en un entorno híbrido, debe tener:

- Una licencia válida para Microsoft Cloud App Security
- Una licencia válida de ATP de Azure conectada a su instancia de Active Directory

>[!NOTE]
>Si no tiene una suscripción para que ATP de Azure, todavía podrá usar el portal de Cloud App Security para investigar a los usuarios, pero no recibirá información de su entorno local.


## <a name="enable-azure-advanced-threat-protection"></a>Habilitar la protección contra amenazas avanzada de Azure

Lo único que debe hacer para integrar la protección contra amenazas avanzada de Azure con Cloud App Security es haga clic en una casilla. Al habilitar la integración, permitir que Cloud App Security para tener acceso y analizar las actividades sospechosas locales vistas por ATP de Azure, póngalos a Cloud App Security y proporcionarle una visión completa de su entorno híbrido y todas las actividades de riesgo realizadas por los usuarios.

Para habilitar Cloud App Security para integrarse con ATP de Azure:

1. En Cloud App Security, en el engranaje de configuración, seleccione **configuración**.
    
   ![Menú de configuración](./media/azip-system-settings.png)

1. En **protección contra amenazas**, seleccione **ATP de Azure**.
   
    ![habilitar la protección contra amenazas avanzada de azure](./media/aatp-integration.png)

3. Seleccione la casilla de verificación **datos conectar ATP de Azure como las alertas y actividades de Cloud App Security**.
 
Después de habilitar la integración de protección contra amenazas avanzada de Azure, podrá ver las actividades en el entorno local para todos los usuarios de su organización. También se obtendrá avanzadas insights en los usuarios que combinen alertas y actividades sospechosas en los entornos de nube y locales.



Obtenga más información sobre [investigando los usuarios peligrosos inicien](tutorial-ueba.md).


## <a name="next-steps"></a>Pasos siguientes 
[Controlar las aplicaciones en la nube con directivas](control-cloud-apps-with-policies.md)   

[Los clientes Premier también pueden crear una solicitud de soporte técnico directamente en el portal Premier.](https://premier.microsoft.com/)  
  
