---
title: Solucionar problemas de mensajes de error del conector de aplicaciones
description: En este artículo se proporciona una lista de los mensajes de error de los conectores de aplicaciones de la API, así como recomendaciones para solucionarlos.
ms.date: 01/29/2020
ms.topic: conceptual
ms.openlocfilehash: 5848e0286d6d99ed3699652e3a44ef5fe1cf359b
ms.sourcegitcommit: 40d17309b8729eb914ea91ba5fa7017340231488
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/29/2020
ms.locfileid: "97809004"
---
# <a name="troubleshooting-app-connectors-using-error-messages"></a>Solucionar problemas relacionados con conectores de aplicaciones a partir de los mensajes de error

[!INCLUDE [Banner for top of topics](includes/banner.md)]

En este artículo se proporciona una lista de los mensajes de error de los conectores de aplicaciones de la API y recomendaciones para solucionarlos.

## <a name="troubleshooting"></a>Solución de problemas

Los errores de conectores de aplicaciones se pueden consultar en el cuadro de diálogo del conector de aplicaciones después de intentar conectar una aplicación en la nube mediante el conector de aplicaciones de la API.

> [!div class="mx-tableFixed"]
>
> |Mensaje de error|Aplicación correspondiente|Description|Solución|
> |----|----|----|------------|
> |HttpRequestFailure: Server returned: 500 Internal server error (HttpRequestFailure: El servidor devolvió: 500 Error interno del servidor)|Todas las aplicaciones|Se ha producido un error en la aplicación.|Compruebe el estado de la aplicación.|
> |El tiempo de servicio expiró.|Todas las aplicaciones|Se ha detectado un tiempo de espera en la conexión entre Cloud App Security y la aplicación. Esto podría deberse a un problema con la aplicación.|Vuelva a intentarlo más tarde.|
> |NullPointerException|AWS|Error interno.|Ponerse en contacto con soporte técnico|
> |AuthFatalFailureException: com.box.boxjavalibv2.exceptions.BoxServerException: {"error":"invalid_grant","error_description":"Invalid refresh token"} (AuthFatalFailureException: com.box.boxjavalibv2.exceptions.BoxServerException: {"error":"invalid_grant","error_description":"Token de actualización no válido"})|Box|El token de actualización de Box no es válido.|Siga el proceso para volver a conectar Box con Cloud App Security.|
> |BoxRestException: Failed to parse response. (BoxRestException: No se pudo analizar la respuesta.)|Box|Error interno.|Haga clic de nuevo en el vínculo Probar ahora para probar la conexión con Box.|
> |ContextManagerServiceException: com.adallom.adalib.httputils.exceptions.TokenRefreshException: {"error":"invalid_grant","error_description":"Invalid refresh token"}' (ContextManagerServiceException: com.adallom.adalib.httputils.exceptions.TokenRefreshException: {"error":"invalid_grant","error_description":"Token de actualización no válido"}')|Box|El token de actualización de Box no es válido.|Siga el proceso para volver a conectar Box con Cloud App Security.|
> |BoxServerException: User cannot access this feature without having an enterprise (BoxServerException: El usuario no puede acceder a esta característica sin una empresa)|Box|La cuenta de Box no es una cuenta Enterprise.|Actualice la licencia de Box a la versión Enterprise de Box y, después, siga el proceso para conectar de nuevo Box con Cloud App Security.|
> |BoxServerException: Unauthorized - Cannot authorize with this service (BoxServerException: No autorizado. No se puede autorizar con este servicio)|Box|El administrador de Box ha eliminado la aplicación Cloud App Security en Box.|Siga el proceso para volver a conectar Box con Cloud App Security.|
> |HttpRequestFailure: Server returned: 401 Unauthorized (HttpRequestFailure: El servidor devolvió: 401 No autorizado)|Exchange Online|Usuario o contraseña incorrectos.|Asegúrese de que el nombre de usuario y la contraseña son correctos y siga el proceso para volver a conectar Exchange Online con Cloud App Security.|
> |HttpRequestFailure: Server returned: 404 Not Found (HttpRequestFailure: El servidor devolvió: 404 No encontrado)|Exchange Online|El usuario que está usando para iniciar sesión en Exchange Online no tiene un buzón principal en Exchange Online (por ejemplo, un usuario que no existe en Azure AD o un usuario que existe en Azure AD pero no tiene una licencia de Exchange Online).|Siga el proceso para volver a conectar Exchange Online con Cloud App Security mediante una nueva cuenta de administrador.|
> |GoogleJsonResponseException: 401 Unauthorized (GoogleJsonResponseException: 401 No autorizado)|Área de trabajo de Google|Acceso denegado. No está autorizado para leer registros de actividad. El usuario con el que inicia sesión en el área de trabajo de Google debe ser un usuario administrador.|Siga el proceso para conectar el área de trabajo de Google para Cloud App Security de nuevo con una cuenta de administrador.|
> |GoogleJsonResponseException: 403 Forbidden (GoogleJsonResponseException: 403 Prohibido)|Área de trabajo de Google|Problema al ejecutar la API de área de trabajo de Google.|Si acaba de implementar el Cloud App Security conector de aplicaciones para el área de trabajo de Google, compruebe lo siguiente: si hizo clic en ilimitado, asegúrese de que la cuenta de Google Workspace es realmente ilimitada. Si no es así, vuelva a ejecutar el conector de aplicaciones y desactive la opción de cuenta ilimitada. Compruebe que los ámbitos definidos durante la configuración son correctos. Si no se trata de una implementación nueva y ve este error, es posible que se haya alcanzado el límite de API para hoy y que los eventos de área de trabajo de Google se renueven mañana.|
> |TokenResponseException: 400 Bad Request (TokenResponseException: 400 Solicitud incorrecta)|Área de trabajo de Google|O bien la conexión con el área de trabajo de Google no se completó o expiró.|Siga el proceso para conectar el área de trabajo de Google a Cloud App Security de nuevo.|
> |HttpRequestFailure: Server returned: 401 Unauthorized (HttpRequestFailure: El servidor devolvió: 401 No autorizado)|Okta|El token de Okta no es válido.|Siga el proceso para volver a conectar Okta con Cloud App Security.|
> |IOException:|Okta|Error interno.|Ponerse en contacto con soporte técnico|
> |HttpRequestFailure: Server returned: 404 Not Found (HttpRequestFailure: El servidor devolvió: 404 No encontrado)|Okta|Error interno.|Ponerse en contacto con soporte técnico|
> |HttpRequestFailure: Server returned: 400 Bad Request: {"error":{"code":"AF20012","message":"Specified tenant ID (Tenant_ID goes here) is incorrectly configured in the system." (HttpRequestFailure: El servidor devolvió: 400 Solicitud incorrecta: {"error":{"code":"AF20012","message":"El id. de inquilino especificado (ID_de_inquilino) está configurado incorrectamente en el sistema".)|Office 365 |No se han encontrado licencias de Office 365 asignadas. |Asigne al menos una licencia de Office 365 a su inquilino.|
> |Microsoft. Office. Compliance. Audit. DataServiceException: el inquilino 998cea7e-35cd-46A5-ab3c-8ec88a45d7d5 no existe o {"error": "Code": "AF20023", "message": "se deshabilitó la suscripción".|Office 365|El registro de auditoría no está habilitado en Office 365|Habilite el registro de auditoría en Office 365. [Más información](connect-office-365-to-microsoft-cloud-app-security.md#how-to-connect-office-365-to-cloud-app-security)|
> |HttpRequestFailure: Server returned: 401 Unauthorized (HttpRequestFailure: El servidor devolvió: 401 No autorizado)|Office 365|Problema interno.|Haga clic de nuevo en el vínculo Probar ahora.|
> |TokenRefreshException: {"error":"invalid_grant","error_description":"AADSTS70002: Error validating credentials. AADSTS70008: The provided authorization code or refresh token is expired. (TokenRefreshException: {"error":"invalid_grant","error_description":"AADSTS70002: Error al validar las credenciales. AADSTS70008: El código de autorización proporcionado o token de actualización ha expirado.) Envíe una nueva solicitud de autorización interactiva para este usuario y recurso.|Office 365|Token expirado|Siga el proceso para volver a conectar Office 365 con Cloud App Security.|
> |SocketTimeoutException: Read timed out (SocketTimeoutException: Agotado el tiempo de espera de lectura)|Office 365|Error interno.|Haga clic de nuevo en el vínculo Probar ahora.|
> |NullPointerException|Office 365|Error interno.|Ponerse en contacto con soporte técnico|
> |IgniteException|Office 365|El dominio o el usuario no son válidos.|Restablezca la configuración y siga el proceso para volver a conectar Office 365 con Cloud App Security.|
> |ContextManagerServiceException: com.adallom.adalib.httputils.exceptions.TokenRefreshException: {"error":"invalid_grant","error_description":"AADSTS70002: Error validating credentials. AADSTS70008: The provided authorization code or refresh token is expired. (TokenRefreshException: {"error":"invalid_grant","error_description":"AADSTS70002: Error al validar las credenciales. AADSTS70008: El código de autorización proporcionado o token de actualización ha expirado.) Envíe una nueva solicitud de autorización interactiva para este usuario y recurso.|Office 365|El dominio o el usuario no son válidos.|Restablezca la configuración y siga el proceso para volver a conectar Office 365 con Cloud App Security.|
> |HttpRequestFailure: Server returned: 400 Bad Request (HttpRequestFailure: El servidor devolvió: 400 Solicitud incorrecta)|Office 365|Error interno.|Haga clic de nuevo en el vínculo Probar ahora dentro de unos minutos. Si no funciona, siga el proceso para volver a conectar Office 365 con Cloud App Security.|
> |SocketTimeoutException: Read timed out (SocketTimeoutException: Agotado el tiempo de espera de lectura)|Salesforce|Error interno.|Haga clic de nuevo en el vínculo Probar ahora para probar la conexión con Salesforce.|
> |HttpRequestFailure: Server returned: 400 Bad Request (HttpRequestFailure: El servidor devolvió: 400 Solicitud incorrecta)|Salesforce|O bien la conexión con Salesforce no se ha completado, o bien ha expirado.|Siga el proceso para volver a conectar Salesforce con Cloud App Security.|
> |Obtener permisos: NoHttpResponseException: `*******.salesforce.com:443` no se pudo responder|Salesforce|Restricción de IP en el ENV del cliente.|En el portal de Salesforce, en configuración de la  >  **sesión** de configuración, desactive la casilla **bloquear sesiones en la dirección IP desde la que se originaron** .|
> |RuntimeException: com.adallom.adalib.httputils.exceptions.HttpRequestFailure: Server returned: 403 Forbidden (RuntimeException: com.adallom.adalib.httputils.exceptions.HttpRequestFailure: El servidor devolvió: 403 Prohibido)|ServiceNow|Los permisos no son correctos.|Siga el proceso para volver a conectar ServiceNow con Cloud App Security mediante una cuenta de administrador.|
> |Obtener eventos: {"Code": 403, "serverResponse"<br />Obtener usuarios: {"Code": 403, "serverResponse"<br />…<br />"cuerpo": "{" error ":" Permiso denegado "}"|Workday|Permisos insuficientes para tener acceso a los registros de auditoría y/o a los puntos de conexión de usuario|Compruebe que todos los permisos están en vigor. [Más información](connect-workday-to-microsoft-cloud-app-security.md#prerequisites)|
> |"Code": 400, "serverResponse"<br />…<br />cuerpo ":" {"error": "invalid_grant"}|Workday|Problema de autenticación|La cuenta usada para configurar la instancia puede estar bloqueada o deshabilitada. Para comprobarlo, vea la cuenta de WorkDay y seleccione **ver el historial de inicio de sesión**. Es posible que vea un mensaje de error de autenticación en el informe especificando que la cuenta del sistema está deshabilitada. [Más información](connect-workday-to-microsoft-cloud-app-security.md#how-to-connect-workday-to-cloud-app-security-using-oauth)|
> |"Code": 401, "serverResponse":<br />…<br />cuerpo ":" {"error": "invalid_client"} "|Workday|Problema de validez del token de cliente|El token de cliente de la API de REST de OAuth 2,0 no es válido. Puede que el token haya expirado o que sea incorrecto. Genere otro token y asígnelo a la instancia conectada. [Más información](connect-workday-to-microsoft-cloud-app-security.md#how-to-connect-workday-to-cloud-app-security-using-oauth)|

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Actividades diarias para proteger el entorno de nube](daily-activities-to-protect-your-cloud-environment.md)

[!INCLUDE [Open support ticket](includes/support.md)]
