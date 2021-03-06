---
title: Conectar Office 365 con Cloud App Security
description: En este artículo se proporciona información sobre cómo conectar Office 365 con Cloud App Security mediante el conector de API para la visibilidad y el control del uso.
ms.date: 08/17/2020
ms.topic: how-to
ms.openlocfilehash: 4d0735251469641c3e268eda2e99a791c6d05d2e
ms.sourcegitcommit: 243baad1adeb32d157c7f6165c08df2136b28db0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/27/2020
ms.locfileid: "97792797"
---
# <a name="connect-office-365-to-microsoft-cloud-app-security"></a>Conectar Office 365 con Microsoft Cloud App Security

[!INCLUDE [Banner for top of topics](includes/banner.md)]

En este artículo se proporcionan instrucciones para conectar Microsoft Cloud App Security a su cuenta de Office 365 existente mediante la API del conector de aplicaciones. Esta conexión le ofrece visibilidad y control del uso de Office 365. Para obtener información sobre cómo Cloud App Security protege Office 365, consulte [protección de office 365](protect-office-365.md).
  
Cloud App Security es compatible con la plataforma dedicada de Office 365 heredada, así como con las últimas ofertas de los servicios de Office 365 (conocidos comúnmente como la familia de versiones de vNext de Office 365).  Cloud App Security no es compatible con Microsoft Business Productivity Online Standard Suite heredado (BPOS).

> [!NOTE]
> En algunos casos, la versión de un servicio de vNext difiere ligeramente en los niveles de administración de la oferta de Office 365 estándar.

Cloud App Security admite las siguientes aplicaciones de Office 365:

- Dynamics 365 CRM
- Exchange (solo aparece después de que se hayan detectado actividades de Exchange en el portal, y es necesario activar la auditoría)
- Office
- OneDrive
- Power Automate
- Power BI (solo aparece después de que se hayan detectado actividades de Power BI en el portal, y es necesario activar la auditoría)
- SharePoint
- Skype Empresarial
- Equipos (solo aparece después de que se hayan detectado actividades de equipos en el portal)
- Yammer

> [!NOTE]
> Cloud App Security se integra directamente con los [registros de auditoría de Office 365](/microsoft-365/compliance/detailed-properties-in-the-office-365-audit-log?view=o365-worldwide&preserve-view=true) y recibe todos los eventos auditados de **todos los servicios admitidos**, como PowerApps, Forms, Sway y Stream.

## <a name="how-to-connect-office-365-to-cloud-app-security"></a>Cómo conectar Office 365 con Cloud App Security  

> [!NOTE]
>
>- Debe tener al menos una licencia de Office 365 asignada para conectar Office 365 a Cloud App Security.
>- Para habilitar la supervisión de las actividades de Office 365 en Cloud App Security, es necesario habilitar la auditoría en el [centro de seguridad y cumplimiento de Office](https://support.microsoft.com/help/4026501/office-auditing-in-office-365-for-admins).
>- El registro de auditoría de administrador de Exchange, que está habilitado de forma predeterminada en Office 365, registra un evento en el registro de auditoría de Office 365 cuando un administrador (o un usuario al que se han asignado privilegios administrativos) realiza un cambio en la organización de Exchange Online. Los cambios realizados mediante el Centro de administración de Exchange o mediante la ejecución de un cmdlet en Windows PowerShell se registran en el registro de auditoría de administrador de Exchange. Para obtener más información sobre el registro de auditoría de administrador de Exchange, consulte [Registro de auditoría de administrador](/exchange/security-and-compliance/exchange-auditing-reports/view-administrator-audit-log).
>- El registro de auditoría de buzones de Exchange debe estar activado para cada buzón de usuario antes de que se registre la actividad del usuario en Exchange Online. Consulte las [actividades de buzones de Exchange](https://support.office.com/article/Search-the-audit-log-in-the-Office-365-Security-Compliance-Center-0d4d0f35-390b-4518-800e-0c7ec95e946c).
>- Si las aplicaciones de Office están habilitadas, los grupos que forman parte de Office 365 también se importan a Cloud App Security desde las aplicaciones de Office específicas; por ejemplo, si SharePoint está habilitado, los grupos de Office 365 se importan también como grupos de SharePoint.
>- Debe [habilitar la auditoría en Power BI](https://powerbi.microsoft.com/documentation/powerbi-admin-auditing/) para obtener los registros desde ahí. Una vez habilitada, Cloud App Security empieza a obtener los registros (con un retraso de 24-72 horas).
>- Debe [Habilitar la auditoría en Dynamics 365](/dynamics365/customer-engagement/admin/enable-use-comprehensive-auditing#enable-auditing) para obtener los registros desde allí. Una vez habilitada, Cloud App Security empieza a obtener los registros (con un retraso de 24-72 horas).
>- Si Azure Active Directory está establecido de modo que se sincronice automáticamente con los usuarios del entorno local de Active Directory, la configuración del entorno local reemplaza la configuración de Azure AD y se revierte el uso de la acción de gobernanza **Suspender usuario**.
>- En el caso de las actividades de inicio de sesión Azure AD, Cloud App Security solo muestra las actividades de inicio de sesión interactivas y las actividades de inicio de sesión de los protocolos heredados, como ActiveSync. Las actividades de inicio de sesión no interactivas se pueden ver en el registro de auditoría Azure AD.
> - Las [implementaciones multigeográfica](/office365/enterprise/office-365-multi-geo) solo se admiten en OneDrive

1. En la página **aplicaciones conectadas** , haga clic en el botón más y seleccione **Office 365**.

    ![opción de menú conectar O365](media/connect-o365.png)

1. En el menú emergente de Office 365, haga clic en **Conectar Office 365**.

    ![conectar elemento emergente de O365](media/office-connect.png)

1. En la página componentes de Office 365, seleccione las opciones que necesite y, a continuación, haga clic en **conectar**.

    > [!NOTE]
    >
    > - Para lograr una protección óptima, se recomienda seleccionar todos los componentes de Office 365.
    > - El componente **Office 365 files** requiere el componente de **actividades de Office 365** y Cloud App Security la supervisión de archivos (  >  **los archivos** de configuración  >  **habilitan la supervisión de archivos**).

    ![conectar componentes de O365](media/connect-o365-components.png)

1. Cuando se indique que Office 365 está conectado correctamente, haga clic en **Cerrar**.

> [!NOTE]
> Después de conectar Office 365, podrá ver los datos de la semana anterior, incluidas las aplicaciones de terceros conectadas a Office 365 que extraen API. En el caso de las aplicaciones de terceros que no extraían API antes de la conexión, verá eventos desde el momento en que se conecta Office 365 porque Cloud App Security activa las API que estaban desactivadas de forma predeterminada.

Si tiene problemas para conectar la aplicación, consulte [solución de problemas de conectores de aplicaciones](troubleshooting-api-connectors-using-error-messages.md).

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Controlar las aplicaciones en la nube con directivas](control-cloud-apps-with-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]
