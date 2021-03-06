---
title: Administración de tokens de API
description: En este artículo se proporciona información sobre cómo generar y administrar tokens de API para Cloud App Security.
ms.date: 03/27/2020
ms.topic: reference
ms.openlocfilehash: cd577565cb67b51dd93c649e69cd00a551736789
ms.sourcegitcommit: 421870fac566642809eff0a545ec1981be1c9165
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/20/2020
ms.locfileid: "97705889"
---
# <a name="managing-api-tokens"></a>Administración de tokens de API

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Para acceder a la API de Cloud App Security, tiene que crear un token de API y usarlo en el software para conectarse a la API. Este token se incluirá en el encabezado cuando Cloud App Security realice solicitudes de API.

La pestaña de tokens de API ayuda a administrar todos los tokens de API del inquilino.

## <a name="generate-a-token"></a>Generar un token

1. En el menú **Configuración**, seleccione **Extensiones de seguridad** y **API tokens** (Tokens de API).

2. Haga clic en el icono de signo más. En **Generar nuevo token**, proporcione un nombre para identificar el token en el futuro y haga clic en **Siguiente**.

    ![Cloud App Security genera el token de API](media/api-token-gen.png)

3. Copie el valor del token y guárdelo para poder recuperarlo en caso necesario. Si lo pierde, deberá regenerar el token. El token tiene los privilegios del usuario que lo emitió. Por ejemplo, un lector de seguridad no puede emitir un token que modifique datos.

4. Puede filtrar los tokens por estado Activo, Inactivo o Generado.

    - **Generado:** Tokens que no se han usado nunca.
    - **Active:** Los tokens que se generaron y se usaron en los últimos siete días.
    - **Inactivo:** Los tokens que se usaron pero no había ninguna actividad en los últimos siete días.

5. Después de generar un nuevo token, se le proporcionará una nueva dirección URL para que pueda acceder al portal de Cloud App Security.

    ![Token de la API de Cloud App Security](media/generate-api-token.png)

    La dirección URL del portal genérico continuará funcionando, pero será notablemente más lenta que la dirección URL personalizada que reciba junto al token. Si alguna vez olvida la dirección URL, puede consultarla en el icono de interrogante (**?**) del menú seleccionando **Acerca de**.

## <a name="api-token-management"></a>Administración de tokens de API

En la página de tokens de API se incluye una tabla de todos los tokens de API que se han generado.

Los administradores totales podrán ver todos los tokens generados para el inquilino en cuestión. Los demás usuarios solo verán los tokens que han generado por sí mismos.

La tabla contiene detalles sobre cuándo se ha generado el token y cuando se ha usado por última vez. Además, permite revocar el token.

Después de que se haya revocado un token, se quitará de la tabla y el software que lo usaba no podrá realizar llamadas API hasta que se proporcione un nuevo token.

> [!NOTE]
>
> - Los conectores SIEM y los recopiladores de registros también usan tokens de API. Estos tokens deben administrarse desde los recopiladores de registros y las secciones de los agentes SIEM y no aparecerán en esta tabla.
> - Los tokens de API de usuarios desaprovisionados se conservan en Cloud App Security pero no se pueden usar. Cualquier intento de utilizarlos producirá una respuesta de Permiso denegado. Sin embargo, se recomienda revocar dichos tokens en la página de **tokens de API** .

[!INCLUDE [Open support ticket](includes/support.md)]

## <a name="check-out-this-video"></a>Eche un vistazo a este vídeo.

[Microsoft Cloud App Security: tokens y API de REST](https://channel9.msdn.com/Shows/Microsoft-Security/Microsoft-Cloud-App-Security--REST-APIs-and-Tokens)
