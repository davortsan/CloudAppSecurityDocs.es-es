---
title: Conexión de WorkDay a Cloud App Security
description: En este artículo se proporciona información sobre cómo conectar la aplicación WorkDay a Cloud App Security mediante el conector de API para la visibilidad y el control del uso.
keywords: ''
author: ShlomoSagir-MS
ms.author: shsagir
manager: ShlomoSagir-MS
ms.date: 9/8/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: d22d5e20ca3ad8f8484fb22f16b595c91d27aa22
ms.sourcegitcommit: 5929f232232f2c3cba460680d959b121dff1aa3a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/08/2019
ms.locfileid: "70803045"
---
# <a name="connect-workday-to-microsoft-cloud-app-security"></a>Conexión de WorkDay a Microsoft Cloud App Security

*Se aplica a: Microsoft Cloud App Security*

En este artículo se proporcionan instrucciones para conectar Microsoft Cloud App Security a su cuenta de WorkDay existente mediante la API del conector de aplicaciones. Esta conexión le proporciona visibilidad y control sobre el uso de WorkDay.

## <a name="prerequisites"></a>Requisitos previos

La cuenta de WorkDay usada para conectarse a Cloud App Security debe ser miembro de un grupo de seguridad (nuevo o existente). El grupo de seguridad debe tener los siguientes permisos seleccionados para los siguientes dominios:

| Área funcional | Dominio | Subdominio | Permisos de informe/tarea | Permisos de integración |
| --- | --- | --- | --- | --- |
| System (Sistema) | Configurar: Configuración de inquilinos: General | Configurar: Configuración de inquilinos: seguridad | Ver, modificar | Get, Put |
| System (Sistema) | Administración de seguridad | | Ver, modificar | Get, Put |
| System (Sistema) | Auditoría del sistema | | Vista | Get |
| Personal | Datos de trabajo: Personal | Datos de trabajo: Informes de trabajo público | Vista | Get |

Para obtener más información sobre la configuración de usuarios, grupos de seguridad y permisos de la integración de WorkDay, consulte los pasos del 1 al 4 de la guía de [concesión de acceso a la integración o el extremo externo a WorkDay](https://go.microsoft.com/fwlink/?linkid=2103212) (accesible con las credenciales de la comunidad o la documentación de WorkDay).

Se recomienda usar un usuario del sistema de integración de WorkDay.

## <a name="how-to-connect-workday-to-cloud-app-security-using-oauth"></a>Cómo conectar WorkDay a Cloud App Security mediante OAuth

1. Inicie sesión en su cuenta de WorkDay con un usuario administrador que sea miembro del grupo de seguridad mencionado en los requisitos previos.

1. Busque "Editar configuración de inquilino – sistema" y, en **registro de actividad de usuario**, seleccione **Habilitar registro de actividad de usuario**.

    ![Captura de pantalla para permitir el registro de actividad de usuario](media/connect-workday-enable-logging.png)

1. Busque "Editar configuración de inquilino – seguridad" y, en **configuración de oauth 2,0**, seleccione **clientes de OAuth 2,0 habilitados**.

1. Busque "registrar el cliente de API" y seleccione **registrar API Client – tarea**.

1. En la página **registrar el cliente de API** , rellene la información siguiente y, a continuación, haga clic en **Aceptar**.

    | Nombre del campo | Valor |
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
