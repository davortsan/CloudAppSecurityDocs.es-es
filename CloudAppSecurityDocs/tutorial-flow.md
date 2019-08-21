---
title: Automatización de alertas para proteger puntos de conexión | Microsoft Docs
description: En este tutorial se explica el proceso de configuración de alertas de Microsoft Cloud App Security a fin de usar Microsoft Flow para ejecutar acciones de Microsoft Defender.
author: ShlomoSagir-MS
ms.author: shsagir
ms.service: cloud-app-security
ms.topic: tutorial
ms.date: 8/15/2019
ms.openlocfilehash: bfec590f92172773bf263dbb5b84832329c63488
ms.sourcegitcommit: 12dfc4c0b8d72aad8cfae9c70f0014ca312b9e4e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69037429"
---
# <a name="tutorial-automate-alerts-to-protect-endpoints"></a>Tutorial: Automatización de alertas para proteger puntos de conexión

Por sí mismo, Cloud App Security proporciona opciones de control predefinidas como la suspensión de usuarios o hacer que los archivos sean privados al definir las directivas. Al crear un cuaderno de estrategias de Microsoft Flow mediante el conector Cloud App Security, puede crear flujos de trabajo para habilitar acciones de punto de conexión personalizadas para las directivas con Advanced Threat Protection (ATP) de Microsoft Defender. Después de crear el cuaderno de estrategias en Flow, solo tiene que asociarlo a una directiva de Cloud App Security para enviar alertas a Flow. Microsoft Flow ofrece varios conectores y condiciones para crear un flujo de trabajo personalizado para su organización.

El [conector Cloud App Security](https://docs.microsoft.com/connectors/cloudappsecurity/) de Flow admite activaciones y acciones automatizadas. Flow se activa automáticamente cuando Cloud App Security genera una alerta. Una de las posibles acciones es cambiar el estado de alerta en Cloud App Security.

En este tutorial se aprende a automatizar alertas para:

> [!div class="checklist"]
> * Ejecutar un examen antivirus mediante ATP de Microsoft Defender
> * Aislar un equipo mediante ATP de Microsoft Defender

En el marco de este tutorial, el procedimiento explica cómo automatizar alertas para ejecutar un examen antivirus mediante ATP de Microsoft Defender. Para automatizar alertas con el fin de aislar un equipo, siga los mismos pasos, pero cambie el flujo antivirus por el flujo de aislamiento.

> [!NOTE]
> Estos flujos solo son relevantes para las directivas que contienen actividad del usuario. Por ejemplo, no puede usar estos flujos con directivas de OAuth o de detección.

Si no tiene un plan de Flow, [regístrese para obtener una cuenta de evaluación gratuita](https://flow.microsoft.com/pricing).

## <a name="prerequisites"></a>Requisitos previos

* Debe tener un [plan de Microsoft Flow](https://flow.microsoft.com/pricing) válido
* El entorno de Flow debe estar sincronizado con Azure AD, supervisado por ATP de Defender y unido a un dominio

## <a name="run-an-antivirus-scan-using-microsoft-defender-atp"></a>Ejecutar un examen antivirus mediante ATP de Microsoft Defender

Los siguientes pasos le guían a lo largo del proceso de creación de un flujo que ejecuta un examen antivirus y de su incorporación a una directiva que detecta comportamientos sospechosos. Cuando se genera una alerta para un usuario por un comportamiento sospechoso, desencadena el flujo que ejecuta un examen antivirus en el equipo que emplea el usuario susceptible de estar en peligro.

### <a name="step-1-create-a-flow-to-run-an-antivirus-scan"></a>Paso 1: Crear un flujo para ejecutar un examen antivirus

> [!NOTE]
> Si ya ha creado un flujo con un conector de ATP de Defender, Flow vuelve a usar el conector automáticamente y se puede omitir el paso de **inicio de sesión**.

1. Vaya al [portal de Microsoft Flow](https://flow.microsoft.com/) y seleccione Plantillas.
    ![Captura de pantalla de la página principal de Flow, en la que se muestra la selección de plantillas.](media/tutorial-flow-templates.png)
1. Busque "Cloud App Security" y seleccione **Run antivirus scan using Windows Defender upon a Cloud App Security alert** (Ejecutar examen antivirus con Windows Defender tras alerta de Cloud App Security).
    ![Captura de pantalla de la página principal de Flow, en la que se muestran los resultados de búsqueda.](media/tutorial-flow-templates-search.png)
1. Haga clic en **Iniciar sesión** y escriba las credenciales de administrador que quiere usar con el conector de ATP de Microsoft Defender.
    ![Captura de pantalla de la página principal de Flow, en la que se muestra el proceso de inicio de sesión.](media/tutorial-flow-templates-signin.png)

> [!TIP]
> Mantenga abierta la página, ya que va a necesitarla más adelante.

### <a name="step-2-create-a-cloud-app-security-connector"></a>Paso 2: Crear un conector Cloud App Security

> [!NOTE]
> Si ya ha creado un flujo con un conector Cloud App Security, Flow vuelve a usar el token automáticamente y se puede omitir este paso.

1. En la barra de menús de Cloud App Security, haga clic en el engranaje de configuración ![icono de configuración](./media/settings-icon.png "icono de configuración") y seleccione **Extensiones de seguridad**.
1. En la página **Extensiones de seguridad**, haga clic en el botón más para generar un nuevo token de API.
1. En la ventana emergente **Generar nuevo token**, escriba el nombre del token (por ejemplo, "Flow-token") y haga clic en **Generar**.
    ![Captura de pantalla de la ventana del token, en la que se muestran la entrada de nombre y el botón Generar.](media/tutorial-flow-token-generate.png)
1. Una vez generado el token, haga clic en el icono de copia situado a la derecha del token generado y luego en **Cerrar**. Va a necesitar el token más adelante.
    ![Captura de pantalla de la ventana del token, en la que se muestran el token y el proceso de copia.](media/tutorial-flow-token-copy.png)

### <a name="step-3-configure-the-flow"></a>Paso 3: Configurar el flujo

> [!NOTE]
> Si ya ha creado un flujo con un conector de Azure AD, Flow vuelve a usar el token automáticamente y se puede omitir este paso.

1. De nuevo en el portal de Microsoft Flow, haga clic en **Crear**.
    ![Captura de pantalla de la página principal de Flow, en la que se muestra el proceso de creación.](media/tutorial-flow-templates-create.png)
1. En la ventana emergente **Cloud App Security**, escriba el nombre de la conexión (por ejemplo, "Cloud App Security Token"), pegue el token de API que ha copiado y haga clic en **Crear**.
    ![Captura de pantalla de la ventana Cloud App Security, en la que se muestran la entrada de nombre y clave y el botón Crear.](media/tutorial-flow-token-generate.png)
1. En la lista de aplicaciones, en la fila en la que aparece **HTTP con Azure AD**, seleccione los tres puntos del final y haga clic en **Agregar nueva conexión**.
1. En la ventana emergente **HTTP con Azure AD**, en los campos **Dirección URL del recurso base** y **URI de recurso de Azure AD**, escriba `https://graph.microsoft.com`, haga clic en **Iniciar sesión** y escriba las credenciales de administrador que quiere usar con el conector HTTP con Azure AD.
    ![Captura de pantalla de la ventana HTTP con Azure AD, en la que se muestran los campos de recursos y el botón de inicio de sesión.](media/tutorial-flow-templates-azure.png)
1. Haga clic en **Continue**.
    ![Captura de pantalla de la ventana Plantillas de Flow, en la que se muestran las acciones completadas y el botón Continuar.](media/tutorial-flow-templates-continue.png)
1. Una vez que todos los conectores estén conectados correctamente, en la página del flujo, en **Apply to each machine** (Aplicar a cada equipo), puede modificar el comentario y el tipo de examen y hacer clic en **Guardar**.
    ![Captura de pantalla de la página del flujo, en la que se muestra la sección de configuración del examen.](media/tutorial-flow-templates-scan.png)

### <a name="step-4-apply-the-flow-to-a-policy"></a>Paso 4: Aplicar el flujo a una directiva

1. En Cloud App Security, edite la directiva en la que quiere agregar el flujo antivirus y, en **Alertas**, seleccione **Enviar alertas a Flow** y luego **Ejecutar examen antivirus con Windows Defender tras alerta de Cloud App Security**.
    ![Captura de pantalla de la página de directivas, en la que se muestra la sección de configuración de alertas.](media/tutorial-flow-templates-alerts.png)

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
[Integración con Flow para la automatización de alertas personalizadas](flow-integration.md)
