---
title: Administración de tokens de API en Cloud App Security
description: En este artículo se proporciona información sobre cómo generar tokens de API para Cloud App Security.
ms.date: 07/14/2020
ms.topic: how-to
ms.openlocfilehash: 2066d62d80e0e85131852f23418147409ba147ff
ms.sourcegitcommit: d87372b47ca98e942c2bf94032a6a61902627d69
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/30/2020
ms.locfileid: "96313855"
---
# <a name="api-tokens"></a>Tokens de API

[!INCLUDE [Banner for top of topics](includes/banner.md)]

La API de Microsoft Cloud App Security proporciona acceso mediante programación a Cloud App Security a través de puntos de conexión de API de REST. Las aplicaciones pueden usar la API para realizar operaciones de lectura y actualización en objetos y datos de Cloud App Security. Por ejemplo, la API de Cloud App Security admite las siguientes operaciones comunes para un objeto de usuario:

- Cargar archivos de registro para Cloud Discovery
- Generar scripts de bloqueo
- Enumerar actividades, alertas e informes de directiva
- Descartar o resolver alertas

Para obtener más información sobre el uso de nuestra API, consulte [Cloud App Security API de REST](api-introduction.md).

Si quiere acceder a la API, deberá crear un token de API y usarlo en el software para conectar con la API de Cloud App Security.

La pestaña de tokens de API ayuda a administrar todos los tokens de API del inquilino.

## <a name="generate-a-token"></a>Generar un token

1. En el menú **Configuración**, seleccione **Extensiones de seguridad** y **API tokens** (Tokens de API).

2. Haga clic en el icono de signo más. En **Generar nuevo token**, proporcione un nombre para identificar el token en el futuro y haga clic en **Siguiente**.
  ![Cloud App Security genera el token de API](media/api-token-gen.png)

3. Copie el valor del token y guárdelo para poder recuperarlo en caso necesario. Si lo pierde, deberá regenerar el token. El token tiene los privilegios del usuario que lo emitió. Por ejemplo, un lector de seguridad no puede emitir un token que modifique datos.

4. Puede filtrar los tokens por estado Activo, Inactivo o Generado.

    - Los tokens generados son los que no se han usado nunca.
    - Los tokens activos son los que se han generado y usado durante los siete últimos días.
    - Los tokens inactivos se han usado, pero no ha habido ninguna actividad durante los siete últimos días.

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

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Cloud App Security API de REST](api-introduction.md)

> [!div class="nextstepaction"]
> [Solución de problemas de integración de SIEM](troubleshooting-siem.md)

[!INCLUDE [Open support ticket](includes/support.md)]

## <a name="check-out-this-video"></a>Eche un vistazo a este vídeo.

[Microsoft Cloud App Security: tokens y API de REST](https://channel9.msdn.com/Shows/Microsoft-Security/Microsoft-Cloud-App-Security--REST-APIs-and-Tokens)
