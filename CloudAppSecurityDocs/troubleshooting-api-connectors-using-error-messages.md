---
title: 'Solución de problemas relacionados con mensajes de error de los conectores de aplicaciones: Cloud App Security | Microsoft Docs'
description: En este artículo se proporciona una lista de los mensajes de error de los conectores de aplicaciones de la API, así como recomendaciones para solucionarlos.
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
ms.assetid: 4b6ac04a-4653-4c4a-bd6f-5926743475cc
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 2691be1e80bbeebf3c36f7cd25b2cb1df0dbc560
ms.sourcegitcommit: 094bb42a198fe733cfd3aec79d74487672846dfa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/24/2019
ms.locfileid: "74460021"
---
# <a name="troubleshooting-app-connectors-using-error-messages"></a>Solucionar problemas relacionados con conectores de aplicaciones a partir de los mensajes de error

*Se aplica a: Microsoft Cloud App Security*

En este artículo se proporciona una lista de los mensajes de error de los conectores de aplicaciones de la API y recomendaciones para solucionarlos.

## <a name="troubleshooting"></a>Solución de problemas

Los errores de conectores de aplicaciones se pueden consultar en el cuadro de diálogo del conector de aplicaciones después de intentar conectar una aplicación en la nube mediante el conector de aplicaciones de la API.


> [!div class="mx-tableFixed"]
> 
> |Mensaje de error|Aplicación correspondiente|Descripción|Solución|
> |----|----|----|------------|
> |HttpRequestFailure: Server returned: 400 Bad Request: {"error":{"code":"AF20012","message":"Specified tenant ID (Tenant_ID goes here) is incorrectly configured in the system." (HttpRequestFailure: El servidor devolvió: 400 Solicitud incorrecta: {"error":{"code":"AF20012","message":"El id. de inquilino especificado (ID_de_inquilino) está configurado incorrectamente en el sistema".)|Office 365 |No se han encontrado licencias de Office 365 asignadas. |Asigne al menos una licencia de Office 365 a su inquilino.| 
> |AuthFatalFailureException: com.box.boxjavalibv2.exceptions.BoxServerException: {"error":"invalid_grant","error_description":"Invalid refresh token"} (AuthFatalFailureException: com.box.boxjavalibv2.exceptions.BoxServerException: {"error":"invalid_grant","error_description":"Token de actualización no válido"})|Cuadro|El token de actualización de Box no es válido.|Siga el proceso para volver a conectar Box con Cloud App Security.|
> |BoxRestException: Failed to parse response. (BoxRestException: No se pudo analizar la respuesta.)|Cuadro|Error interno.|Haga clic de nuevo en el vínculo Probar ahora para probar la conexión con Box.|
> |ContextManagerServiceException: com.adallom.adalib.httputils.exceptions.TokenRefreshException: {"error":"invalid_grant","error_description":"Invalid refresh token"}' (ContextManagerServiceException: com.adallom.adalib.httputils.exceptions.TokenRefreshException: {"error":"invalid_grant","error_description":"Token de actualización no válido"}')|Cuadro|El token de actualización de Box no es válido.|Siga el proceso para volver a conectar Box con Cloud App Security.|
> |BoxServerException: User cannot access this feature without having an enterprise (BoxServerException: El usuario no puede acceder a esta característica sin una empresa)|Cuadro|La cuenta de Box no es una cuenta Enterprise.|Actualice la licencia de Box a la versión Enterprise de Box y, después, siga el proceso para conectar de nuevo Box con Cloud App Security.|
> |BoxServerException: Unauthorized - Cannot authorize with this service (BoxServerException: No autorizado. No se puede autorizar con este servicio)|Cuadro|El administrador de Box ha eliminado la aplicación Cloud App Security en Box.|Siga el proceso para volver a conectar Box con Cloud App Security.|
> |HttpRequestFailure: Server returned: 401 Unauthorized (HttpRequestFailure: El servidor devolvió: 401 No autorizado)|Okta|El token de Okta no es válido.|Siga el proceso para volver a conectar Okta con Cloud App Security.|
> |IOException:|Okta|Error interno.|Póngase en contacto con el soporte técnico.|
> |HttpRequestFailure: Server returned: 404 Not Found (HttpRequestFailure: El servidor devolvió: 404 No encontrado)|Okta|Error interno.|Póngase en contacto con el soporte técnico.|
> |SocketTimeoutException: Read timed out (SocketTimeoutException: Agotado el tiempo de espera de lectura)|Salesforce|Error interno.|Haga clic de nuevo en el vínculo Probar ahora para probar la conexión con Salesforce.|
> |HttpRequestFailure: Server returned: 400 Bad Request (HttpRequestFailure: El servidor devolvió: 400 Solicitud incorrecta)|Salesforce|O bien la conexión con Salesforce no se ha completado, o bien ha expirado.|Siga el proceso para volver a conectar Salesforce con Cloud App Security.|
> |HttpRequestFailure: Server returned: 401 Unauthorized (HttpRequestFailure: El servidor devolvió: 401 No autorizado)|Office 365|Problema interno.|Haga clic de nuevo en el vínculo Probar ahora.|
> |TokenRefreshException: {"error":"invalid_grant","error_description":"AADSTS70002: Error validating credentials. AADSTS70008: The provided authorization code or refresh token is expired. (TokenRefreshException: {"error":"invalid_grant","error_description":"AADSTS70002: Error al validar las credenciales. AADSTS70008: El código de autorización proporcionado o token de actualización ha expirado.) Envíe una nueva solicitud de autorización interactiva para este usuario y recurso.|Office 365|El token ha expirado.|Siga el proceso para volver a conectar Office 365 con Cloud App Security.|
> |SocketTimeoutException: Read timed out (SocketTimeoutException: Agotado el tiempo de espera de lectura)|Office 365|Error interno.|Haga clic de nuevo en el vínculo Probar ahora.|
> |NullPointerException|Office 365|Error interno.|Póngase en contacto con el soporte técnico.|
> |IgniteException|Office 365|El dominio o el usuario no son válidos.|Restablezca la configuración y siga el proceso para volver a conectar Office 365 con Cloud App Security.|
> |ContextManagerServiceException: com.adallom.adalib.httputils.exceptions.TokenRefreshException: {"error":"invalid_grant","error_description":"AADSTS70002: Error validating credentials. AADSTS70008: The provided authorization code or refresh token is expired. (TokenRefreshException: {"error":"invalid_grant","error_description":"AADSTS70002: Error al validar las credenciales. AADSTS70008: El código de autorización proporcionado o token de actualización ha expirado.) Envíe una nueva solicitud de autorización interactiva para este usuario y recurso.|Office 365|El dominio o el usuario no son válidos.|Restablezca la configuración y siga el proceso para volver a conectar Office 365 con Cloud App Security.|
> |HttpRequestFailure: Server returned: 400 Bad Request (HttpRequestFailure: El servidor devolvió: 400 Solicitud incorrecta)|Office 365|Error interno.|Haga clic de nuevo en el vínculo Probar ahora dentro de unos minutos. Si no funciona, siga el proceso para volver a conectar Office 365 con Cloud App Security.|
> |GoogleJsonResponseException: 401 Unauthorized (GoogleJsonResponseException: 401 No autorizado)|G Suite|Acceso denegado: No está autorizado para leer registros de actividad. El usuario con que el inicie sesión en G Suite debe ser un usuario administrador.|Siga el proceso para volver a conectar G Suite con Cloud App Security mediante una cuenta de administrador.|
> |GoogleJsonResponseException: 403 Forbidden (GoogleJsonResponseException: 403 Prohibido)|G Suite|Problema al ejecutar la API de G Suite.|Si acaba de implementar el conector de aplicaciones de Cloud App Security para G Suite, compruebe lo siguiente: si hizo clic en Ilimitado, asegúrese de que su cuenta de G Suite es realmente ilimitada. Si no es así, vuelva a ejecutar el conector de aplicaciones y desactive la opción de cuenta ilimitada. Compruebe que los ámbitos definidos durante la configuración son correctos. Si no está realizando una implementación nueva y ve este error, es posible que se haya alcanzado el límite diario de API y al día siguiente se renovarán los eventos de G Suite.|
> |TokenResponseException: 400 Bad Request (TokenResponseException: 400 Solicitud incorrecta)|G Suite|O bien la conexión con G Suite no se ha completado, o bien ha expirado.|Siga el proceso para volver a conectar G Suite con Cloud App Security.|
> |RuntimeException: com.adallom.adalib.httputils.exceptions.HttpRequestFailure: Server returned: 403 Forbidden (RuntimeException: com.adallom.adalib.httputils.exceptions.HttpRequestFailure: El servidor devolvió: 403 Prohibido)|ServiceNow|Los permisos no son correctos.|Siga el proceso para volver a conectar ServiceNow con Cloud App Security mediante una cuenta de administrador.|
> |HttpRequestFailure: Server returned: 401 Unauthorized (HttpRequestFailure: El servidor devolvió: 401 No autorizado)|Exchange Online|Usuario o contraseña incorrectos.|Asegúrese de que el nombre de usuario y la contraseña son correctos y siga el proceso para volver a conectar Exchange Online con Cloud App Security.|
> |HttpRequestFailure: Server returned: 404 Not Found (HttpRequestFailure: El servidor devolvió: 404 No encontrado)|Exchange Online|El usuario que está usando para iniciar sesión en Exchange Online no tiene un buzón principal en Exchange Online (por ejemplo, un usuario que no existe en Azure AD o un usuario que existe en Azure AD pero no tiene una licencia de Exchange Online).|Siga el proceso para volver a conectar Exchange Online con Cloud App Security mediante una nueva cuenta de administrador.|
> |NullPointerException|AWS|Error interno.|Póngase en contacto con el soporte técnico.|
> |HttpRequestFailure: Server returned: 500 Internal server error (HttpRequestFailure: El servidor devolvió: 500 Error interno del servidor)|Todas las aplicaciones|Se ha producido un error en la aplicación.|Compruebe el estado de la aplicación.|
> |El tiempo de servicio expiró.|Todas las aplicaciones|Se ha detectado un tiempo de espera en la conexión entre Cloud App Security y la aplicación. Esto podría deberse a un problema con la aplicación.|Inténtelo más tarde.|

## <a name="next-steps"></a>Pasos siguientes

[Actividades diarias para proteger el entorno de nube](daily-activities-to-protect-your-cloud-environment.md)   

[!INCLUDE [Open support ticket](includes/support.md)]  

