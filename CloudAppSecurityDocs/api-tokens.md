---
title: "Administración de tokens de API en Cloud App Security | Microsoft Docs"
description: "En este tema se proporciona información sobre cómo generar tokens de API para Cloud App Security."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 7/1/2017
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: 4f5e6b1e-6b2c-4358-98f0-945e2993d5fe
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 291a9bf9a0c45a7ef2667b5a4266ebb582d3a23b
ms.sourcegitcommit: a0290ac2a662994f7771975ef6c20d0b47e9edd8
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/03/2017
---
# <a name="api-tokens"></a>Tokens de API
    
La API de Cloud App Security proporciona acceso mediante programación a Cloud App Security a través de puntos de conexión de API de REST. Las aplicaciones pueden usar la API para realizar operaciones de lectura y actualización en objetos y datos de Cloud App Security. Por ejemplo, la API de Cloud App Security admite las siguientes operaciones comunes para un objeto de usuario:

- Cargar archivos de registro para Cloud Discovery
- Generar scripts de bloqueo
- Enumerar actividades, alertas e informes de directiva
- Descartar o resolver alertas

Para ver la documentación completa de la API, en el portal de Cloud App Security, vaya a Ayuda > **Documentación de la API**.

Para tener acceso a la API, tendrá que crear un token de API y usarlo en el software para conectar con la API de Cloud App Security.

La pestaña de tokens de API ayuda a administrar todos los tokens de API del inquilino. 


## <a name="generate-a-token"></a>Generar un token

1. En el menú **Configuración**, seleccione **Extensiones de seguridad** y **API tokens** (Tokens de API).

2. Haga clic en el icono de signo más. En **Generar nuevo token**, proporcione un nombre para identificar el token en el futuro y haga clic en **Siguiente**.
![Generar token de API de Cloud App Security](./media/api-token-gen.png)

3. Copie el valor del token y guárdelo para poder recuperarlo en caso necesario. Si lo pierde, deberá volver a generar el token. El token tendrá los privilegios del usuario que lo haya emitido. Por ejemplo, un lector de seguridad no puede emitir un token que modifique datos.

4. Puede filtrar los tokens por estado Activo, Inactivo o Generado. 

  - Los tokens generados son los que no se han usado nunca. 
  - Los tokens activos son los que se han generado y usado durante los últimos 7 días. 
  - Los tokens inactivos se han usado, pero no ha habido ninguna actividad durante los últimos 7 días.


## <a name="api-token-management"></a>Administración de tokens de API

En la página de tokens de API se incluye una tabla de todos los tokens de API que se han generado.

Los administradores totales podrán ver todos los tokens generados para el inquilino en cuestión. Los demás usuarios solo verán los tokens que han generado por sí mismos.

La tabla contiene detalles sobre cuándo se ha generado el token y cuando se ha usado por última vez. Además, permite revocar el token. 

Después de que se haya revocado un token, se quitará de la tabla y el software que lo usaba no podrá realizar llamadas de API hasta que se proporcione un nuevo token. 

> [!NOTE]
> Los conectores SIEM y los recopiladores de registros también usan tokens de API. Estos tokens deben administrarse desde los recopiladores de registros y las secciones de los agentes SIEM y no aparecerán en esta tabla. 

## <a name="see-also"></a>Consulte también  
[Solución de problemas de integración de SIEM](troubleshooting-siem.md)   
[Para obtener soporte técnico, visite la página de soporte técnico asistido de Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Los clientes Premier también pueden elegir Cloud App Security directamente desde el Portal Premier.](https://premier.microsoft.com/)  
  
  