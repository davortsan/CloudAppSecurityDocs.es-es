---
title: Conectar Office 365 a Cloud App Security
description: En este artículo se proporciona información sobre cómo conectar Office 365 a Cloud App Security mediante el conector de API para la visibilidad y el control del uso.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 7/30/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 74b03bd9db046a7637ea84d69914d1e87b47c2ae
ms.sourcegitcommit: 4f3883a9e85d0aaf2802b10433b221c3f1838d88
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/13/2020
ms.locfileid: "79285499"
---
# <a name="connect-office-365-to-microsoft-cloud-app-security"></a>Conectar Office 365 a Microsoft Cloud App Security

*Se aplica a: Microsoft Cloud App Security*

En este artículo se proporcionan instrucciones para conectar Microsoft Cloud App Security a su cuenta de Microsoft Office 365 existente mediante la API del conector de aplicaciones. Esta conexión le proporciona visibilidad y control sobre el uso de Office 365. Para obtener información sobre cómo Cloud App Security protege Office 365, consulte [protección de office 365](protect-office-365.md).
  
Cloud App Security es compatible con la plataforma dedicada de Office 365 y las últimas ofertas de servicios de Office 365 (lo que se conoce comúnmente como la familia de versiones de vNext de Office 365).  Cloud App Security no es compatible con Microsoft Business Productivity online Standard Suite (BPOS) heredado.

> [!NOTE]
> En algunos casos, una versión de servicio de vNext difiere ligeramente en los niveles administrativos y de administración de la oferta estándar de Office 365.

Cloud App Security admite las siguientes aplicaciones de Office 365:

- Dynamics 365 CRM
- Exchange (solo aparece después de que se detectan actividades de Exchange en el portal y requiere que active la auditoría)
- Office 365
- OneDrive
- Automatización de la energía
- Power BI (solo aparece después de que se detecten las actividades de Power BI en el portal y es necesario activar la auditoría)
- SharePoint
- Skype Empresarial
- Equipos (solo aparece después de que se detectan actividades de los equipos en el portal)
- Yammer

> [!NOTE]
> Cloud App Security se integra directamente con los [registros de auditoría de Office 365](https://docs.microsoft.com/microsoft-365/compliance/detailed-properties-in-the-office-365-audit-log?view=o365-worldwide) y recibe todos los eventos auditados de **todos los servicios admitidos**, como PowerApps, Forms, Sway y Stream.

## <a name="how-to-connect-office-365-to-cloud-app-security"></a>Cómo conectar Office 365 a Cloud App Security  

> [!NOTE]
>
>- Debe tener al menos una licencia de Office 365 asignada para conectar Office 365 a Cloud App Security.
>- Para habilitar la supervisión de las actividades de Office 365 en Cloud App Security, es necesario habilitar la auditoría en el [centro de seguridad y cumplimiento de Office](https://support.microsoft.com/help/4026501/office-auditing-in-office-365-for-admins).
>- El registro de auditoría de administrador de Exchange, que está habilitado de forma predeterminada en Office 365, registra un evento en el registro de auditoría de Office 365 cuando un administrador (o un usuario que tiene asignados privilegios administrativos) realiza un cambio en la organización de Exchange Online. Los cambios realizados mediante el centro de administración de Exchange o mediante la ejecución de un cmdlet en Windows PowerShell se registran en el registro de auditoría de administración de Exchange. Para obtener información más detallada sobre el registro de auditoría de administrador en Exchange, consulte [registro de auditoría de administrador](https://docs.microsoft.com/exchange/security-and-compliance/exchange-auditing-reports/view-administrator-audit-log).
>- El registro de auditoría de buzones de correo de Exchange debe estar activado para cada buzón de usuario antes de que se registre la actividad de usuario en Exchange Online, vea [actividades de buzón de Exchange](https://support.office.com/article/Search-the-audit-log-in-the-Office-365-Security-Compliance-Center-0d4d0f35-390b-4518-800e-0c7ec95e946c).
>- Si las aplicaciones de Office están habilitadas, los grupos que forman parte de Office 365 también se importan a Cloud App Security desde las aplicaciones de Office específicas. por ejemplo, si SharePoint está habilitado, los grupos de Office 365 se importan también como grupos de SharePoint.
>- Debe [Habilitar la auditoría en PowerBI](https://powerbi.microsoft.com/documentation/powerbi-admin-auditing/) para obtener los registros desde allí. Una vez habilitada la auditoría, Cloud App Security comienza a obtener los registros (con un retraso de 24-72 horas).
>- Debe [Habilitar la auditoría en Dynamics 365](https://docs.microsoft.com/dynamics365/customer-engagement/admin/enable-use-comprehensive-auditing#enable-auditing) para obtener los registros desde allí. Una vez habilitada la auditoría, Cloud App Security comienza a obtener los registros (con un retraso de 24-72 horas).
>- Si el Azure Active Directory está establecido para que se sincronice automáticamente con los usuarios de su Active Directory entorno local, la configuración del entorno local invalida la configuración de Azure AD y el uso de la acción **suspender** el gobierno del usuario se revierte.
>- En el caso de las actividades de inicio de sesión Azure AD, Cloud App Security solo muestra las actividades de inicio de sesión interactivas y las actividades de inicio de sesión de los protocolos heredados, como ActiveSync. Las actividades de inicio de sesión no interactivas se pueden ver en el registro de auditoría Azure AD.

1. En la página **aplicaciones conectadas** , haga clic en el botón más y seleccione **Office 365**.

    ![conectar 0365](media/connect-0365.png)

2. En el menú emergente Office 365, haga clic en **conectar office 365**.

    ![conectar 0365](media/office-connect.png)

3. Después de que Office 365 se muestre como conectado correctamente, haga clic en **cerrar**.

> [!NOTE]
> Después de conectar Office 365, verá los datos de una semana, incluidas las aplicaciones de terceros conectadas a Office 365 que están extrayendo API. En el caso de las aplicaciones de terceros que no extraían API antes de la conexión, verá eventos desde el momento en que se conecta Office 365, ya que Cloud App Security activa las API que estaban desactivadas de forma predeterminada.

Si tiene problemas para conectar la aplicación, consulte [solución de problemas de conectores de aplicaciones](troubleshooting-api-connectors-using-error-messages.md).

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Controlar las aplicaciones en la nube con directivas](control-cloud-apps-with-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]
