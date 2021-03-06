---
title: Integre Microsoft Power Automate con Microsoft Cloud App Security para obtener una automatización de alertas personalizada
description: En este artículo se proporciona información sobre cómo obtener una automatización de alertas personalizada mediante la integración de Microsoft Power Automate con Cloud App Security.
ms.date: 01/05/2021
ms.topic: how-to
ms.openlocfilehash: 8b2575764470bb444c2bb7a36e37cf80dc6251ce
ms.sourcegitcommit: 0768aa1992819e2651a14a731f79e178fdececc5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/12/2021
ms.locfileid: "98114741"
---
# <a name="integrate-with-microsoft-power-automate-for-custom-alert-automation"></a>Integración con Microsoft Power Automate para la automatización de alertas personalizada

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Cloud App Security se integra con [Microsoft Power Automate](/flow/getting-started) para proporcionar una automatización de alertas personalizada y guías de orquestación. Con el [ecosistema de conectores](/connectors/) disponible en Power Automatic, puede automatizar la activación de los cuadernos de estrategias cuando Cloud App Security genera alertas. Por ejemplo, crear automáticamente un problema en sistemas de vales mediante el [conector de ServiceNow](/connectors/service-now/) o enviar un correo electrónico de aprobación para ejecutar una acción de control personalizado cuando se active una alerta en Cloud App Security.

## <a name="prerequisites"></a>Requisitos previos

- Debe tener un [plan de Microsoft Power Automate](https://flow.microsoft.com/pricing) válido.

## <a name="how-it-works"></a>Funcionamiento

Por su cuenta, Cloud App Security proporciona opciones de gobierno predefinidas, como suspender a un usuario o hacer que un archivo sea privado al definir directivas. Mediante la creación de una guía en Power Automate mediante Cloud App Security Connector, puede crear flujos de trabajo para habilitar opciones de gobierno personalizadas para sus directivas. Una vez que se haya creado la guía en Power Automate, basta con asociarla a una directiva en Cloud App Security para enviar alertas a Power Automate. Microsoft Power Automate ofrece varios conectores y condiciones para crear un flujo de trabajo personalizado para su organización.

El [conector de Cloud App Security](/connectors/cloudappsecurity/) de Power Automatic es compatible con los desencadenadores y las acciones automatizadas. Power Automatic se desencadena automáticamente cuando Cloud App Security genera una alerta. Una de las posibles acciones es cambiar el estado de alerta en Cloud App Security.

## <a name="how-to-create-playbooks-with-power-automate"></a>Creación de guías con Power Automatic

1. [Crear un token de API](api-authentication.md) en Cloud App Security.

2. Vaya al [portal de Power Automate](https://flow.microsoft.com), seleccione **Mis flujos**, seleccione **nuevo** y, en la lista desplegable, seleccione **automatizado-desde** cero.

    ![Power Automate crear nuevo flujo](media/flow-create-new.png)

3. Proporcione un nombre para el flujo y, en **elegir el desencadenador de su flujo**, escriba **Cloud App Security** y seleccione **cuando se genere una alerta**.

    ![Energía automatizada cuando se genera una alerta](media/flow-when-alert.png)

4. En **Configuración de autenticación**, pegue el token de API del paso 1.

5. Defina el flujo de trabajo que debe activarse cuando una directiva de Cloud App Security genera una alerta. Puede agregar una acción o una condición lógica, cambiar las condiciones o los bucles y guardar el cuaderno de estrategias.

    ![Flujo de trabajo de automatización de energía](media/flow-workflow.png)

6. En el portal de Cloud App Security, vaya a **directivas** y, en la fila de la Directiva cuyas alertas desea reenviar a Power Automatic, haga clic en los tres puntos y seleccione **configuración**.
7. En **alertas**, seleccione **enviar alertas a Power Automatic** y elija el nombre de la guía en el menú desplegable.

    ![Habilitación de Power Automatic en Cloud App Security portal](media/flow-mcas-config.png)

8. En la pantalla **extensiones de seguridad** se pueden consultar Cloud App Security guías a las que ha creado o a las que se le concede acceso.

    ![ver cuadernos de estrategias en Cloud App Security](media/flow-extensions.png)

## <a name="related-videos"></a>Vídeos relacionados

> [!div class="nextstepaction"]
> [Seminario Web de Automation and Integration with Power Automatic](webinars.md#on-demand-webinars)

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Controlar las aplicaciones en la nube con directivas](control-cloud-apps-with-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]
