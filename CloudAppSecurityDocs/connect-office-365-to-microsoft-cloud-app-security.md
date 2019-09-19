---
title: Conectar Office 365 con Cloud App Security
description: En este artículo se proporciona información sobre cómo conectar Office 365 con Cloud App Security mediante el conector de API para la visibilidad y el control del uso.
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
ms.assetid: a79bf393-0d2c-44b6-8dab-86c740fd7333
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: fc9c45a20e59c7dd4591cbeda53df6951c3cac44
ms.sourcegitcommit: 8a49c166424fea83853b0a6895212367526abe78
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2019
ms.locfileid: "71084065"
---
# <a name="connect-office-365-to-microsoft-cloud-app-security"></a>Conectar Office 365 con Microsoft Cloud App Security

*Se aplica a: Microsoft Cloud App Security*

En este artículo se proporcionan instrucciones para conectar Microsoft Cloud App Security con una cuenta de Microsoft Office 365 existente mediante la API del conector de aplicaciones.  Esta conexión le ofrece visibilidad y control del uso de Office 365.
  
Cloud App Security es compatible con la plataforma dedicada de Office 365 heredada, así como con las últimas ofertas de los servicios de Office 365 (conocidos comúnmente como la familia de versiones de vNext de Office 365).  Cloud App Security no es compatible con Microsoft Business Productivity Online Standard Suite heredado (BPOS). 

> [!NOTE]
> En algunos casos, la versión de un servicio de vNext difiere ligeramente en los niveles de administración de la oferta de Office 365 estándar.

Cloud App Security admite las siguientes aplicaciones de Office 365:

- Office 365
- SharePoint
- OneDrive
- Equipos (solo aparece después de que se hayan detectado actividades de equipos en el portal)
- Power BI (solo aparece después de que se hayan detectado actividades de Power BI en el portal, y es necesario activar la auditoría)
- Exchange (solo aparece después de que se hayan detectado actividades de Exchange en el portal, y es necesario activar la auditoría)
- Dynamics 365

## <a name="how-to-connect-office-365-to-cloud-app-security"></a>Cómo conectar Office 365 con Cloud App Security  

> [!NOTE]
>- Debe tener al menos una licencia de Office 365 asignada para conectar Office 365 a Cloud App Security.
>- Para habilitar la supervisión de las actividades de Office 365 en Cloud App Security, es necesario habilitar la auditoría en el [centro de seguridad y cumplimiento de Office](https://support.microsoft.com/help/4026501/office-auditing-in-office-365-for-admins).
>- El registro de auditoría de administrador de Exchange, que está habilitado de forma predeterminada en Office 365, registra un evento en el registro de auditoría de Office 365 cuando un administrador (o un usuario al que se han asignado privilegios administrativos) realiza un cambio en la organización de Exchange Online. Los cambios realizados mediante el Centro de administración de Exchange o mediante la ejecución de un cmdlet en Windows PowerShell se registran en el registro de auditoría de administrador de Exchange. Para obtener más información sobre el registro de auditoría de administrador de Exchange, consulte [Registro de auditoría de administrador](https://docs.microsoft.com/exchange/security-and-compliance/exchange-auditing-reports/view-administrator-audit-log).
>- El registro de auditoría de buzones de Exchange debe estar activado para cada buzón de usuario antes de que se registre la actividad del usuario en Exchange Online. Consulte las [actividades de buzones de Exchange](https://support.office.com/article/Search-the-audit-log-in-the-Office-365-Security-Compliance-Center-0d4d0f35-390b-4518-800e-0c7ec95e946c).
>- Si las aplicaciones de Office están habilitadas, también se importan los grupos que forman parte de Office 365 a Cloud App Security desde las aplicaciones de Office específicas. Por ejemplo, si SharePoint está habilitado, se importan también grupos de Office 365 como grupos de SharePoint.
>- Debe [habilitar la auditoría en Power BI](https://powerbi.microsoft.com/documentation/powerbi-admin-auditing/) para obtener los registros desde ahí. Una vez habilitada, Cloud App Security empieza a obtener los registros (con un retraso de 24-72 horas).
>- Debe [Habilitar la auditoría en Dynamincs 365](https://docs.microsoft.com/dynamics365/customer-engagement/admin/enable-use-comprehensive-auditing#enable-auditing-in-dynamics-365-for-customer-engagement/) para obtener los registros desde allí. Una vez habilitada, Cloud App Security empieza a obtener los registros (con un retraso de 24-72 horas).
>- Si Azure Active Directory está establecido de modo que se sincronice automáticamente con los usuarios del entorno local de Active Directory, la configuración del entorno local reemplaza la configuración de Azure AD y se revierte el uso de la acción de gobernanza **Suspender usuario**.

1. En la página **Conectores de aplicaciones**, haga clic en el botón del signo más y seleccione **Office 365**.  

      ![conectar O365](./media/connect-0365.png) 

2. En el menú emergente de Office 365, haga clic en **Conectar Office 365**.

      ![conectar O365](./media/office-connect.png) 

3. Cuando se indique que Office 365 está conectado correctamente, haga clic en **Cerrar**.

> [!NOTE]
> Después de conectar Office 365, podrá ver los datos de la semana anterior, incluidas las aplicaciones de terceros conectadas a Office 365 que extraen API. En el caso de las aplicaciones de terceros que no extraían API antes de la conexión, verá eventos a partir del momento en que conectó Office 365, ya que Cloud App Security activa las API que estaban desactivadas de forma predeterminada.

## <a name="next-steps"></a>Pasos siguientes

[Controlar las aplicaciones en la nube con directivas](control-cloud-apps-with-policies.md)

[Los clientes Premier también pueden crear una solicitud de soporte técnico directamente en el portal Premier.](https://premier.microsoft.com/)