---
title: Administración de tokens de API en Cloud App Security
description: En este artículo se proporciona información sobre cómo generar tokens de API para Cloud App Security.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 12/10/2018
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: fcde5b08363a790cf18cf873c0dfde183ec6ddcd
ms.sourcegitcommit: 9165220189564860d74a255a5c0be1ed362ba152
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/01/2020
ms.locfileid: "80522555"
---
# <a name="api-tokens"></a>Tokens de API

*Se aplica a: Microsoft Cloud App Security*

La API de Microsoft Cloud App Security proporciona acceso mediante programación a Cloud App Security a través de los puntos de conexión de la API de REST. Las aplicaciones pueden usar la API para realizar operaciones de lectura y actualización en Cloud App Security datos y objetos. Por ejemplo, la API de Cloud App Security admite las siguientes operaciones comunes para un objeto de usuario:

- Cargar archivos de registro para Cloud Discovery
- Generar scripts de bloqueo
- Enumerar actividades, alertas e informes de directivas
- Descartar o resolver alertas

Para ver la documentación completa de la API, en el portal de Cloud App Security vaya a ayuda > documentación de la **API**.

Para acceder a la API, tiene que crear un token de API y usarlo en el software para conectarse a la API de Cloud App Security.

La pestaña tokens de API le permite administrar todos los tokens de API de su inquilino.

## <a name="generate-a-token"></a>Generar un token

1. En el menú **configuración** , seleccione **extensiones de seguridad** y, a continuación, **tokens de API**.

2. Haga clic en el icono de signo más, **genere un token nuevo** y proporcione un nombre para identificar el token en el futuro y haga clic en **siguiente**.
  ![Cloud App Security genera el token de API](media/api-token-gen.png)

3. Copie el valor del token y guárdelo en algún lugar para la recuperación. Si lo pierde, tendrá que volver a generar el token. El token tiene los privilegios del usuario que lo emitió. Por ejemplo, un lector de seguridad no puede emitir un token que pueda modificar los datos.

4. Puede filtrar los tokens por estado: activo, inactivo o generado.

    - Generados son tokens que nunca se han utilizado.
    - Active son los tokens que se generaron y se usaron en los últimos siete días.
    - Se utilizó inactivo, pero no había ninguna actividad en los últimos siete días.

5. Después de generar un nuevo token, se le proporcionará una dirección URL nueva para acceder al portal de Cloud App Security.

    ![Cloud App Security Token de API](media/generate-api-token.png)

    La dirección URL del portal genérico sigue funcionando, pero es considerablemente más lenta que la dirección URL personalizada proporcionada con el token. Si olvida la dirección URL en cualquier momento, puede verla yendo al **?** en el menú y seleccione **acerca de**.

> [!NOTE]
> Si usa la activación de rol de Azure Active Directory Privileged Identity Management, el token de API solo será efectivo una vez que se active el rol. Para obtener más información, consulte [activación de los roles de Azure ad en PIM](https://docs.microsoft.com/azure/active-directory/privileged-identity-management/pim-how-to-activate-role).

## <a name="api-token-management"></a>Administración de tokens de API

La página de token de API incluye una tabla de todos los tokens de API que se generaron.

Los administradores completos ven todos los tokens generados para este inquilino. Otros usuarios solo verán los tokens que se generaron.

La tabla proporciona detalles sobre cuándo se generó el token y cuándo se usó por última vez y le permite revocar el token.

Una vez revocado un token, se quita de la tabla y el software que lo estaba usando no realiza llamadas a la API hasta que se proporcione un nuevo token.

> [!NOTE]
>
> - Los conectores SIEM y los recopiladores de registros también usan tokens de API. Estos tokens deben administrarse desde los recopiladores de registros y las secciones del agente SIEM y no aparecen en esta tabla.
> - Los tokens de API de usuarios desaprovisionados se conservan en Cloud App Security pero no se pueden usar. Cualquier intento de utilizarlos producirá una respuesta de Permiso denegado. Sin embargo, se recomienda revocar dichos tokens en la página de **tokens de API** .

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Solución de problemas de integración de SIEM](troubleshooting-siem.md)

[!INCLUDE [Open support ticket](includes/support.md)]

## <a name="check-out-this-video"></a>Consulte este vídeo.

[Microsoft Cloud App Security: tokens y API de REST](https://channel9.msdn.com/Shows/Microsoft-Security/Microsoft-Cloud-App-Security--REST-APIs-and-Tokens)
