---
title: Conexión de WorkDay a Cloud App Security
description: En este artículo se proporciona información sobre cómo conectar la aplicación WorkDay a Cloud App Security mediante el conector de API para la visibilidad y el control del uso.
keywords: ''
author: ShlomoSagir-MS
ms.author: shsagir
manager: ShlomoSagir-MS
ms.date: 9/5/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: fefff041971b65d27e4a3409034af0569894dc04
ms.sourcegitcommit: 24c0dd16c7e8212f614fb6fd66c9f18ce75c0b45
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/05/2019
ms.locfileid: "70373126"
---
# <a name="connect-workday-to-microsoft-cloud-app-security"></a>Conexión de WorkDay a Microsoft Cloud App Security

*Se aplica a: Microsoft Cloud App Security*

En este artículo se proporcionan instrucciones para conectar Microsoft Cloud App Security a su cuenta de WorkDay existente mediante la API del conector de aplicaciones. Esta conexión le proporciona visibilidad y control sobre el uso de WorkDay.

## <a name="prerequisites"></a>Requisitos previos

- La cuenta de WorkDay usada para conectarse a Cloud App Security debe ser miembro de un grupo de seguridad que tenga habilitados los siguientes dominios:

  - Administración de seguridad del sistema
  - Sistema-auditoría del sistema
  - Personalización de datos de trabajo: Informes de trabajo público

  Se recomienda usar un usuario del sistema de integración de WorkDay.

- Si la implementación de WorkDay administra los intervalos de direcciones IP, debe incluir en la lista blanca todas Cloud App Security direcciones IP. Para ver la lista de direcciones IP, consulte [requisitos de red: conector de aplicaciones](network-requirements.md#app-connector).

## <a name="how-to-connect-workday-to-cloud-app-security-using-oauth"></a>Cómo conectar WorkDay a Cloud App Security mediante OAuth

1. Inicie sesión con una cuenta de administrador en su cuenta de WorkDay.

1. Busque "Editar configuración de inquilino – sistema" y, en **registro de actividad de usuario**, seleccione **Habilitar registro de actividad de usuario**.

    ![Captura de pantalla para permitir el registro de actividad de usuario](media/connect-workday-enable-logging.png)

1. Busque "Editar configuración de inquilino – seguridad" y, en **configuración de oauth 2,0**, seleccione **clientes de OAuth 2,0 habilitados**.

1. Busque "registrar el cliente de API" y seleccione **registrar API Client – tarea**.

1. En la página **registrar el cliente de API** , rellene la información siguiente y, a continuación, haga clic en **Aceptar**.

    | Nombre del campo | Value |
    | ---- | ---- |
    | Nombre de cliente | Microsoft Cloud App Security |
    | Tipo de concesión de cliente | Concesión de código de autorización |
    | Tipo de token de acceso | Portador |
    | URI de redireccionamiento | `https://portal.cloudappsecurity.com/api/oauth/connect` |
    | Ámbitos de OAuth2 | **Personal** y **sistema** |
    | Ámbito (áreas funcionales) | **Personal** y **sistema** |

    ![Captura de pantalla del registro del cliente de API](media/connect-workday-register-api-client.png)

1. Una vez registrado, tome nota de los siguientes parámetros y, a continuación, haga clic en **listo**.

    - Identificador de cliente
    - Secreto de cliente
    - Punto de conexión de API de REST de WorkDay
    - Extremo de token
    - Extremo de autorización

    ![Captura de pantalla de la confirmación del registro del cliente de API](media/connect-workday-register-api-client-confirm.png)

1. En el portal de Cloud App Security, haga clic en **investigar** y, a continuación, en **aplicaciones conectadas**.

1. En la página **conectores de aplicaciones** , haga clic en el botón más y, a continuación, en **WorkDay**.

    ![Captura de pantalla de la adición del conector de aplicaciones](media/connect-workday-add-app.png)

1. En el menú emergente, agregue el nombre de instancia y, a continuación, haga clic en **conectar WorkDay**.

    ![Captura de pantalla de la adición de nombre de instancia](media/connect-workday-add-app-connect.png)

1. En la página siguiente, rellene los detalles con la información anotada anteriormente y, a continuación, haga clic en **conectar en WorkDay**.

    ![Captura de pantalla del rellenado de detalles de la aplicación](media/connect-workday-add-app-connect-details.png)

1. En WorkDay, una ventana emergente le preguntará si desea permitir el acceso Cloud App Security a su cuenta de WorkDay. Para continuar, haga clic en **Permitir**.

    ![Captura de pantalla sobre cómo autorizar el acceso a la aplicación](media/connect-workday-add-app-allow.png)

1. De vuelta en el portal de Cloud App Security, debería ver un mensaje que le indica que WorkDay se conectó correctamente. Haga clic en **Probar API** para confirmar que la conexión se ha realizado correctamente.

    La prueba puede tardar unos minutos. Cuando reciba la notificación de que se ha realizado correctamente, haga clic en **Cerrar**.

> [!NOTE]
> Después de conectar WorkDay, recibirá eventos durante siete días antes de la conexión.

## <a name="next-steps"></a>Pasos siguientes

[Controlar las aplicaciones en la nube con directivas](control-cloud-apps-with-policies.md)

[Los clientes Premier también pueden crear una solicitud de soporte técnico directamente en el portal Premier.](https://premier.microsoft.com/)
