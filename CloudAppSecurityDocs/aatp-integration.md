---
title: Integración de la protección contra amenazas avanzada de Azure con Cloud App Security
description: En este artículo se proporciona información sobre cómo aprovechar la información de protección contra amenazas avanzada de Azure en Cloud App Security para la detección de riesgos híbrido.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: rkarlin
ms.date: 6/27/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 63e82b47-bb08-4614-af55-f85d04edfc5a
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 99c866a8b2571c9572e042572d0f5160d0ae56e5
ms.sourcegitcommit: 3938edadc5f89f87cdeba607476cf3983b2413e8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/27/2019
ms.locfileid: "67411921"
---
# <a name="azure-advanced-threat-protection-integration"></a>Integración de protección contra amenazas avanzada de Azure

*Se aplica a: Microsoft Cloud App Security*

Microsoft Cloud App Security se integra con la protección de amenazas avanzada (ATP de Azure) Azure para proporcionar análisis de comportamiento de entidades (UEBA) de usuario en un entorno híbrido: aplicación de nube y locales, para obtener más información, consulte [Tutorial: Investigar los usuarios peligrosos inicien]() para obtener más información sobre el aprendizaje automático y análisis de comportamiento proporcionado por ATP de Azure, consulte [What ' s ATP de Azure?](https://docs.microsoft.com/azure-advanced-threat-protection/what-is-atp).

## <a name="prerequisites"></a>Requisitos previos

Para realizar una investigación completa de los usuarios en un entorno híbrido, debe tener:

- Una licencia válida de Azure ATP conectada a la instancia de Active Directory
- Debe ser un administrador global para habilitar la integración entre ATP de Azure y Microsoft Cloud App Security 
- Si no tiene ATP de Azure, Pruébelo ahora


>[!NOTE]
>Si no tiene una suscripción de Microsoft Cloud App Security, podrá usar el portal de Cloud App Security para obtener información de ATP de Azure.


## <a name="enable-azure-advanced-threat-protection"></a>Habilitar la protección contra amenazas avanzada de Azure

Para habilitar Cloud App Security para integrarse con ATP de Azure:

1. En Cloud App Security, en el engranaje de configuración, seleccione **configuración**.
    
   ![Menú de configuración](./media/azip-system-settings.png)

1. En **protección contra amenazas**, seleccione **ATP de Azure**.
   
    ![habilitar la protección contra amenazas avanzada de azure](./media/aatp-integration.png)

3. Seleccione la casilla de verificación **datos conectar ATP de Azure como las alertas y actividades de Cloud App Security**.


> [!NOTE]
> Puede tardar hasta 12 horas hasta que la integración surte efecto.
 
Después de habilitar la integración de protección contra amenazas avanzada de Azure, podrá ver las actividades en el entorno local para todos los usuarios de su organización. También se obtendrá avanzadas insights en los usuarios que combinen alertas y actividades sospechosas en los entornos de nube y locales.



## <a name="next-steps"></a>Pasos siguientes 
[Controlar las aplicaciones en la nube con directivas](control-cloud-apps-with-policies.md)   

[Los clientes Premier también pueden crear una solicitud de soporte técnico directamente en el portal Premier.](https://premier.microsoft.com/)  
  
