---
title: Integración de Cloud App Security con Zscaler para Cloud Discovery sin problemas y bloqueo automatizado de aplicaciones autorizadas | Microsoft Docs
description: Integre Cloud App Security con Zscaler para Cloud Discovery en la nube y bloqueo automatizado de aplicaciones autorizadas.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 12/9/2018
ms.topic: conceptual
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 8abeab8e-3b7a-46a7-bbec-9aaf26f778a8
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 2935fc6a68f73e6d69c237c6efbab3971a6b0e6a
ms.sourcegitcommit: c497253a7ab63973bb806607e5f15dece91640be
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/10/2018
ms.locfileid: "53123523"
---
*Se aplica a: Microsoft Cloud App Security*

# <a name="integrate-cloud-app-security-with-zscaler"></a>Integración de Cloud App Security con Zscaler

Si trabaja con Cloud App Security y Zscaler, puede integrar los dos productos para mejorar la seguridad de la experiencia de Cloud Discovery. Zscaler, como proxy en la nube independiente, supervisa el tráfico de la organización, lo que le permite establecer directivas para bloquear transacciones. Juntos, Cloud App Security y Zscaler proporcionan las siguientes funcionalidades:

- Implementación sin problemas de Cloud Discovery: el uso de Zscaler para establecer un proxy para el tráfico y enviarlo a Cloud App Security elimina la necesidad de instalar los recopiladores de registros en los puntos de conexión de red para habilitar Cloud Discovery.
- Las funcionalidades de bloque de Zscaler se aplican automáticamente a las aplicaciones que haya establecido como no autorizadas en Cloud App Security.
- Mejore el portal de Zscaler con la evaluación de riesgos de Cloud App Security para 200 aplicaciones líderes en la nube que pueden verse directamente en el portal de Zscaler.
    

## <a name="prerequisites"></a>Requisitos previos

- Una licencia válida para Microsoft Cloud App Security
- Una licencia válida para Zscaler Cloud 5.6
- Una suscripción activa de Zscaler NSS 

## <a name="deployment"></a>Implementación

1. En el portal de Zscaler, realice los pasos necesarios para completar la [integración de asociados de Zscaler con Microsoft Cloud App Security](https://help.zscaler.com/zia/configuring-mcas-integration).
2. En el portal de Cloud App Security, realice los pasos de integración siguientes:
    1. Haga clic en el engranaje de configuración y seleccione **Configuración de Cloud Discovery**. 
    2. Haga clic en la pestaña **Carga automática del registro** y luego en **Agregar origen de datos**.
    3. En la página **Agregar origen de datos**, escriba la siguiente configuración:
        - Nombre = NSS
        - Origen = Zscaler QRadar LEEF
        - Tipo de receptor = Syslog - UDP

          ![zscaler de origen de datos](./media/data-source-zscaler.png)

    4. Haga clic en **Ver ejemplo de archivo de registro previsto**. A continuación, haga clic en **Descargar registro de ejemplo** para ver un registro de detección de ejemplo y asegúrese de que coincida con los registros.<br>
    
3. Investigue las aplicaciones en la nube detectadas en la red; consulte [Trabajar con Cloud Discovery](working-with-cloud-discovery-data.md) para más información y pasos de investigación.
 
4. Las aplicaciones que se establecen como no autorizadas en Cloud App Security recibirán un ping por parte de Zscaler cada dos horas y luego Zscaler las bloqueará automáticamente. Para más información sobre las aplicaciones no autorizadas, consulte [Autorizar o no autorizar una aplicación](governance-discovery.md#BKMK_SanctionApp).
    
    
    
    
    

 
## <a name="see-also"></a>Consulte también  
[Controlar las aplicaciones en la nube con directivas](control-cloud-apps-with-policies.md)   

[Los clientes Premier también pueden crear una solicitud de soporte técnico directamente en el portal Premier.](https://premier.microsoft.com/)  
  
  