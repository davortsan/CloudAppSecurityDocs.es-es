---
title: Integre la protección contra amenazas avanzada de Azure con Cloud App Security
description: En este artículo se proporciona información sobre cómo aprovechar la información sobre protección contra amenazas avanzada de Azure en Cloud App Security para la detección de riesgos híbridas.
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
ms.openlocfilehash: 63da07db9a3fa29c49f08f8082b969adcbda6bca
ms.sourcegitcommit: 4861a99debc71f266de738d5db78b711590b5e88
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/24/2019
ms.locfileid: "68431150"
---
# <a name="azure-advanced-threat-protection-integration"></a>Integración de protección contra amenazas avanzada de Azure

*Se aplica a: Microsoft Cloud App Security*

Microsoft Cloud App Security se integra con protección contra amenazas avanzada de Azure (ATP de Azure) para proporcionar análisis del comportamiento de la entidad de usuario (UEBA) en un entorno híbrido, tanto en la aplicación en la nube [como en el entorno local, para obtener más información, consulte Tutorial: Investigue a los](tutorial-ueba.md) usuarios de riesgo para obtener más información sobre el aprendizaje automático y el análisis del comportamiento proporcionado por ATP de Azure, consulte [¿Qué es ATP de Azure?](https://docs.microsoft.com/azure-advanced-threat-protection/what-is-atp)

## <a name="prerequisites"></a>Requisitos previos

Para realizar una investigación completa de los usuarios en un entorno híbrido, debe tener:

- Una licencia válida de Azure ATP conectada a la instancia de Active Directory
- Debe ser un administrador global para habilitar la integración entre ATP de Azure y Microsoft Cloud App Security 
- Si no dispone de ATP de Azure, pruébelo ahora.


>[!NOTE]
>Si no tiene una suscripción para Microsoft Cloud App Security, todavía podrá usar el portal de Cloud App Security para obtener información sobre ATP de Azure.


## <a name="enable-azure-advanced-threat-protection"></a>Habilitación de la protección contra amenazas avanzada de Azure

Para habilitar Cloud App Security para la integración con ATP de Azure:

1. En Cloud App Security, en el engranaje de configuración, seleccione **configuración**.
    
   ![Menú de configuración](./media/azip-system-settings.png)

1. En **protección contra amenazas**, seleccione **ATP de Azure**.
   
    ![habilitación de la protección contra amenazas avanzada de Azure](./media/aatp-integration.png)

3. Active la casilla para **conectar los datos de ATP de Azure, incluidas las alertas y las actividades con Cloud App Security**.


> [!NOTE]
> Puede tardar hasta 12 horas hasta que la integración surta efecto.
 
Después de habilitar la integración de protección contra amenazas avanzada de Azure, podrá ver las actividades locales para todos los usuarios de su organización. También obtendrá información avanzada sobre los usuarios que combinan alertas y actividades sospechosas en los entornos locales y en la nube.



## <a name="next-steps"></a>Pasos siguientes 
[Controlar las aplicaciones en la nube con directivas](control-cloud-apps-with-policies.md)   

[Los clientes Premier también pueden crear una solicitud de soporte técnico directamente en el portal Premier.](https://premier.microsoft.com/)  
  
