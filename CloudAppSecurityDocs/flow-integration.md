---
title: Integración de Flow con Cloud App Security para obtener la automatización de alertas personalizadas
description: En este artículo se proporciona información sobre cómo obtener la automatización de alertas personalizadas mediante la integración de Flow con Cloud App Security.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: barbkess
ms.date: 12/10/2018
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 344f92e2-6b3b-46db-bfd0-3b1016e0bc34
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 497272a2072cf61349c1b0c9ccf49644b7f91665
ms.sourcegitcommit: eba8c158d34198363a8da02b3cb6258df10f7673
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/28/2019
ms.locfileid: "58543131"
---
# <a name="integrate-with-flow-for-custom-alert-automation---preview"></a>Integración de Flow para la automatización de alertas personalizadas: versión preliminar

*Se aplica a: Microsoft Cloud App Security*

Cloud App Security se integra con [Microsoft Flow](https://docs.microsoft.com/flow/getting-started) para proporcionar cuadernos de estrategias de automatización y orquestación de alertas personalizadas. Mediante el uso del [ecosistema de conectores](https://docs.microsoft.com/connectors/) disponible en Microsoft Flow, puede automatizar la activación de cuadernos de estrategias cuando Cloud App Security genera alertas. Por ejemplo, crear automáticamente un problema en sistemas de vales mediante el [conector de ServiceNow](https://docs.microsoft.com/connectors/service-now/) o enviar un correo electrónico de aprobación para ejecutar una acción de control personalizado cuando se active una alerta en Cloud App Security.  

## <a name="prerequisites"></a>Requisitos previos 

 - Debe tener un [plan de Microsoft Flow](https://flow.microsoft.com/en-us/pricing) válido

## <a name="how-it-works"></a>Cómo funciona

Por sí mismo, Cloud App Security proporciona opciones de control predefinidas como la suspensión de usuarios o hacer que los archivos sean privados al definir las directivas. Al crear un cuaderno de estrategias en Microsoft Flow mediante el conector de Cloud App Security, puede crear flujos de trabajo para habilitar las opciones de control personalizado para sus directivas. Después de crear el cuaderno de estrategias en Flow, solo tiene que asociarlo a una directiva de Cloud App Security para enviar alertas a Flow. Microsoft Flow ofrece varios conectores y condiciones para crear un flujo de trabajo personalizado para su organización. 

El [conector de Cloud App Security](https://docs.microsoft.com/connectors/cloudappsecurity/) en flujo automatizado admite desencadenadores y acciones. Flow se activa automáticamente cuando Cloud App Security genera una alerta. Una de las posibles acciones es cambiar el estado de alerta en Cloud App Security. 

## <a name="how-to-create-playbooks-with-microsoft-flow"></a>Cómo crear cuadernos de estrategias con Microsoft Flow

1. [Crear un token de API](api-tokens.md) en Cloud App Security. 

2. Vaya al [portal de Microsoft Flow](https://flow.microsoft.com) y elija [ **Crear un nuevo flujo desde cero**](https://docs.microsoft.com/flow/get-started-logic-flow). 

3. En Activadores y conectores de búsqueda, escriba **Cloud App Security** y seleccione **Cuando se genera una alerta**.

   ![Flujo al generarse una alerta](./media/flow-when-alert.png)

4. En **Configuración de autenticación**, pegue el token de API del paso 1. 

5. Defina el flujo de trabajo que debe activarse cuando una directiva de Cloud App Security genera una alerta. Puede agregar una acción o una condición lógica, cambiar las condiciones o los bucles y guardar el cuaderno de estrategias. 

   ![Flujo de trabajo de Flow](./media/flow-workflow.png)

6. En el portal de Cloud App Security, vaya a **Directivas** y, en la fila de la directiva cuyas alertas quiera reenviar a Flow, haga clic en los puntos suspensivos y seleccione **Configuración**. 
7. En **Alertas**, seleccione **Enviar alertas a Flow** y elija el nombre del cuaderno de estrategias en el menú desplegable.  

   ![Habilitar Flow en el portal de Cloud App Security](./media/flow-mcas-config.png)

8. Los cuadernos de estrategias que ha creado o que se les ha concedido acceso pueden verse en la pantalla **Extensiones de seguridad**. 

  
   ![ver cuadernos de estrategias en Cloud App Security](./media/flow-extensions.png)
 
 

## <a name="next-steps"></a>Pasos siguientes 
[Controlar las aplicaciones en la nube con directivas](control-cloud-apps-with-policies.md)   

[Los clientes Premier también pueden crear una solicitud de soporte técnico directamente en el portal Premier.](https://premier.microsoft.com/)  
