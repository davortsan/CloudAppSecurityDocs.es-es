---
title: Conectar WebEx a Cloud App Security
description: En este artículo se proporciona información sobre cómo conectar la aplicación WebEx a Cloud App Security mediante el conector de API para la visibilidad y el control del uso.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 04/16/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: e3a3f99dd64526439c9c5f4967a2918c33dfdde9
ms.sourcegitcommit: 6eff466c7a6817b14a60d8c3b2c201c7ae4c2e2c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "74719757"
---
# <a name="connect-cisco-webex-to-microsoft-cloud-app-security"></a>Conexión de Cisco WebEx a Microsoft Cloud App Security

*Se aplica a: Microsoft Cloud App Security*

En este artículo se proporcionan instrucciones para conectar Microsoft Cloud App Security a su cuenta de Cisco WebEx existente mediante las API del conector. Esta conexión le proporciona visibilidad y control sobre los usuarios, las actividades y los archivos de WebEx.

## <a name="prerequisites"></a>Requisitos previos

- Se recomienda crear una cuenta de servicio dedicada para la conexión. Esto le permite ver las acciones de gobierno realizadas en WebEx como realizadas desde esta cuenta, como eliminar mensajes enviados en WebEx. De lo contrario, el nombre del administrador que se conectó Cloud App Security a Webex aparecerá como el usuario que realizó las acciones.
- Debe tener permisos de administrador total **y** de administrador de cumplimiento en WebEx.

## <a name="how-to-connect-webex-to-cloud-app-security"></a>Cómo conectar WebEx a Cloud App Security

1. En la consola de Cloud App Security, haga clic en **Investigar** y, después, en **Aplicaciones conectadas**.

1. En la página **conectores de aplicaciones** , haga clic en el botón de signo más seguido de **Cisco WebEx**.

    ![conectar WebEx](media/cisco-webex.png "conectar WebEx")

1. En el elemento emergente, escriba el nombre de instancia de este conector.

1. Haga clic en **conectar Cisco WebEx**. Se abre la página de inicio de sesión de WebEx. Escriba sus credenciales para permitir el acceso Cloud App Security a la instancia WebEx del equipo.

1. WebEx le pregunta si desea permitir el acceso Cloud App Security a la información del equipo, el registro de actividad y realizar actividades como un miembro del equipo. Para continuar, haga clic en **Permitir**.

1. De nuevo en la consola de Cloud App Security, debería recibir un mensaje que indica que WebEx se conectó correctamente.

1. Haga clic en **Probar API** para asegurarse de que la conexión se ha realizado correctamente.

    La prueba puede tardar unos minutos. Cuando reciba la notificación de que se ha realizado correctamente, haga clic en **Cerrar**.

Después de conectar WebEx, recibirá eventos durante 7 días antes de la conexión. Cloud App Security examina eventos durante los últimos tres meses. Para aumentar esto, debe tener una licencia de Cisco WebEx Pro y abrir una incidencia con Cloud App Security soporte técnico.

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Controlar las aplicaciones en la nube con directivas](control-cloud-apps-with-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]
