---
title: Ampliación de la gobernanza a la corrección de puntos de conexión | Microsoft Docs
description: En este tutorial se describe el proceso para configurar las alertas de las directivas de Microsoft Cloud App Security para desencadenar flujos de trabajo de Microsoft Flow y ejecutar acciones de corrección de Advanced Threat Protection de Microsoft Defender.
author: shsagir
ms.author: shsagir
ms.service: cloud-app-security
ms.topic: tutorial
ms.date: 9/8/2019
ms.openlocfilehash: 06fe00d3a289aa32846be71509707aa384b2177f
ms.sourcegitcommit: 0b929f7c8feed7dfb40d5294179fd5c6fc079614
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/21/2020
ms.locfileid: "74720537"
---
# <a name="tutorial-extend-governance-to-endpoint-remediation"></a>Tutorial: Ampliación de la gobernanza a la corrección de puntos de conexión

Cloud App Security ofrece opciones de gobernanza predefinidas para directivas (por ejemplo, para suspender un usuario o convertir un archivo en privado). Mediante la integración nativa con Microsoft Flow, puede usar un amplio ecosistema de conectores de software como servicio (SaaS) para crear flujos de trabajo con el fin de automatizar procesos, incluidos procesos de corrección.

Por ejemplo, al detectar una posible amenaza de malware, puede usar flujos de trabajo para iniciar acciones de corrección de Advanced Threat Protection (ATP) de Microsoft Defender, como la ejecución de un examen antivirus o aislar un punto de conexión.

En este tutorial obtendrá información sobre cómo configurar una acción de gobernanza de directivas para usar un flujo de trabajo que ejecute un examen antivirus en un punto de conexión donde un usuario muestre signos de comportamiento sospechoso.

> [!div class="checklist"]
>
> * 1: [Generación de un token de la API Cloud App Security](#generate-token)
> * 2: [Creación de un flujo para ejecutar un examen antivirus](#create-flow)
> * 3: [Configuración del flujo](#configure-flow)
> * 4: [Configuración de la directiva que ejecutará el flujo](#configure-policy)

> [!NOTE]
> Estos flujos de trabajo solo son pertinentes para directivas que contengan actividad de usuarios. Por ejemplo, no puede usar estos flujos de trabajo con directivas de detección o de OAuth.

Si no tiene un plan de Microsoft Flow, [regístrese para obtener una cuenta de prueba gratuita](https://flow.microsoft.com/pricing).

## <a name="prerequisites"></a>Requisitos previos

* Debe tener un [plan de Microsoft Flow](https://flow.microsoft.com/pricing) válido.
* Necesita un plan válido de ATP de Microsoft Defender.
* El entorno de Microsoft Flow necesita estar sincronizado con Azure AD, supervisado por ATP de Defender y unido a un dominio.

## <a name="phase-1-generate-a-cloud-app-security-api-token"></a>Fase 1: Generación de un token de la API Cloud App Security<a name="generate-token"></a>

> [!NOTE]
> Si ha creado anteriormente un flujo de trabajo mediante un conector de Cloud App Security, Microsoft Flow reutilizará automáticamente el token, por lo que puede omitir este paso.

1. En la barra de menús de Cloud App Security, haga clic en el engranaje de configuración ![icono de configuración](media/settings-icon.png "icono de configuración") y seleccione **Extensiones de seguridad**.

1. En la página **Extensiones de seguridad**, haga clic en el botón del signo más para generar un nuevo token de la API.
1. En la ventana emergente **Generar nuevo token**, escriba el nombre del token (por ejemplo, "Flow-token") y haga clic en **Generar**.

    ![Captura de pantalla de la ventana del token, donde se muestran la entrada de nombre y el botón Generar.](media/tutorial-flow-token-generate.png)
1. Una vez generado el token, haga clic en el icono de copia situado a la derecha del token generado y luego en **Cerrar**. Va a necesitar el token más adelante.

    ![Captura de pantalla de la ventana del token, donde se muestran el token y el proceso de copia.](media/tutorial-flow-token-copy.png)

## <a name="phase-2-create-a-flow-to-run-an-antivirus-scan"></a>Fase 2: Creación de un flujo para ejecutar un examen antivirus<a name="create-flow"></a>

> [!NOTE]
> Si ya ha creado un flujo con un conector de ATP de Defender, Flow vuelve a usar el conector automáticamente y se puede omitir el paso de **inicio de sesión**.

1. Vaya al [portal de Microsoft Flow](https://flow.microsoft.com/) y seleccione Plantillas.

    ![Captura de pantalla de la página principal de Microsoft Flow, en la que se muestra la selección de plantillas.](media/tutorial-flow-templates.png)

1. Busque "Cloud App Security" y seleccione **Run antivirus scan using Windows Defender upon a Cloud App Security alert** (Ejecutar examen antivirus con Windows Defender tras alerta de Cloud App Security).

    ![Captura de pantalla de la página de plantillas de Microsoft Flow, donde se muestran los resultados de la búsqueda.](media/tutorial-flow-templates-search.png)

1. Haga clic en **Iniciar sesión** y escriba las credenciales de administrador que quiere usar con el conector de ATP de Microsoft Defender.

    ![Captura de pantalla de la página de plantillas de Microsoft Flow, donde se muestra el proceso de inicio de sesión.](media/tutorial-flow-templates-signin.png)

## <a name="phase-3-configure-the-flow"></a>Fase 3: Configuración del flujo<a name="configure-flow"></a>

> [!NOTE]
> Si ya ha creado un flujo con un conector de Azure AD, Microsoft Flow volverá a usar el token automáticamente, por lo que puede omitir este paso.

1. Haga clic en **Crear**.

    ![Captura de pantalla de la página de plantillas de Microsoft Flow, donde se muestra el botón Crear de Cloud App Security.](media/tutorial-flow-templates-create.png)

1. En la ventana emergente **Cloud App Security**, escriba el nombre de la conexión (por ejemplo, "Cloud App Security Token"), pegue el token de API que ha copiado y haga clic en **Crear**.

    ![Captura de pantalla de la ventana Cloud App Security, donde se muestran la entrada de nombre y clave, y el botón Crear.](media/tutorial-flow-templates-create-window.png)

1. En la lista de aplicaciones, en la fila en la que aparece **HTTP con Azure AD**, seleccione los tres puntos del final y haga clic en **Agregar nueva conexión**.

1. En la ventana emergente **HTTP con Azure AD**, en los campos **Dirección URL del recurso base** y **URI de recurso de Azure AD**, escriba `https://graph.microsoft.com`, haga clic en **Iniciar sesión** y escriba las credenciales de administrador que quiere usar con el conector HTTP con Azure AD.

    ![Captura de pantalla de la ventana HTTP con Azure AD, donde se muestran los campos de recursos y el botón de inicio de sesión.](media/tutorial-flow-templates-azure.png)

1. Haga clic en **Continue**.

    ![Captura de pantalla de la ventana Plantillas de Microsoft Flow, donde se muestran las acciones completadas y el botón Continuar.](media/tutorial-flow-templates-continue.png)

1. Una vez que todos los conectores estén conectados correctamente, en la página del flujo, en **Apply to each machine** (Aplicar a cada equipo), puede modificar el comentario y el tipo de examen y hacer clic en **Guardar**.

    ![Captura de pantalla de la página del flujo, donde se muestra la sección de configuración del examen.](media/tutorial-flow-templates-scan.png)

## <a name="phase-4-configure-a-policy-to-run-the-flow"></a>Fase 4: Configuración de la directiva que ejecutará el flujo<a name="configure-policy"></a>

1. En Cloud App Security, haga clic en **Control** y, después, seleccione **Directivas**.

1. En la lista de directivas, en la fila donde se muestre una directiva pertinente, seleccione el signo de tres puntos al final de la fila y, después, haga clic en **Editar directiva**.

1. En **Alertas**, seleccione **Enviar alertas a Flow** y, después, haga clic en **Ejecutar examen antivirus con Windows Defender tras una alerta de Cloud App Security**.

    ![Captura de pantalla de la página de directivas, donde se muestra la sección de configuración de alertas.](media/tutorial-flow-templates-alerts.png)

Ahora todas las alertas generadas para esta directiva iniciarán el flujo para ejecutar el examen antivirus.

Siga los pasos que se indican en este tutorial para crear una amplia variedad de acciones basadas en flujos de trabajo con el fin de ampliar las funciones de corrección de Cloud App Security, incluidas otras acciones de ATP de Defender. Para ver una lista de flujos de trabajo predefinidos de Cloud App Security, [busque "Cloud App Security"](https://go.microsoft.com/fwlink/?linkid=2102574) en Microsoft Flow.

## <a name="see-also"></a>Consulte también

> [!div class="nextstepaction"]
> [Integración con Microsoft Flow para la automatización de alertas personalizadas](flow-integration.md)
