---
title: Conectar Office 365 con Cloud App Security para la visibilidad y el control del uso | Microsoft Docs
description: "En este tema se proporciona información sobre cómo conectar la aplicación Office 365 con Cloud App Security mediante el conector de API."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 11/22/2017
ms.topic: get-started-article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: a79bf393-0d2c-44b6-8dab-86c740fd7333
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: e568172068f5ec63a519c495f7e824bd49b03883
ms.sourcegitcommit: 6e4eac42e553fd288da7de9c67eb79f11a420245
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/22/2017
---
# <a name="connect-office-365-to-microsoft-cloud-app-security"></a>Conectar Office 365 con Microsoft Cloud App Security
En esta sección se proporcionan instrucciones para conectar Cloud App Security con una cuenta de Microsoft Office 365 existente mediante la API del conector de aplicaciones.  
  
Cloud App Security es compatible con la plataforma dedicada de Office 365 heredada, así como con las últimas ofertas de los servicios de Office 365 (conocidos comúnmente como la familia de versiones de vNext de Office 365).  Cloud App Security no es compatible con Microsoft Business Productivity Online Standard Suite heredado. 

> [!NOTE]
> En algunos casos, la versión de un servicio de vNext difiere ligeramente en los niveles de administración de la oferta de Office 365 estándar.

Cloud App Security admite las siguientes aplicaciones de Office 365:

- Office 365
- SharePoint
- OneDrive
- Equipos (solo aparece después de que se hayan detectado actividades de equipos en el portal)
- Power BI (solo aparece después de que se hayan detectado actividades de Power BI en el portal, y es necesario activar la auditoría)
- Exchange (solo aparece después de que se hayan detectado actividades de Exchange en el portal, y es necesario activar la auditoría)

 
## <a name="how-to-connect-office-365-to-cloud-app-security"></a>Cómo conectar Office 365 con Cloud App Security  
  
> [!NOTE]
>- Debe tener al menos una licencia de Office 365 asignada para conectar Office 365 a Cloud App Security.
>-  El registro de auditoría de administrador de Exchange, que está habilitado de forma predeterminada en Office 365, registra un evento en el registro de auditoría de Office 365 cuando un administrador (o un usuario al que se han asignado privilegios administrativos) realiza un cambio en la organización de Exchange Online. Los cambios realizados mediante el Centro de administración de Exchange o mediante la ejecución de un cmdlet en Windows PowerShell se registran en el registro de auditoría de administrador de Exchange. Para obtener más información sobre el registro de auditoría de administrador de Exchange, consulte [Registro de auditoría de administrador](http://go.microsoft.com/fwlink/p/?LinkID=619225).
>- El registro de auditoría de buzones de Exchange debe estar activado para cada buzón de usuario antes de que se registre la actividad del usuario en Exchange Online. Consulte las [actividades de buzones de Exchange](https://support.office.com/article/Search-the-audit-log-in-the-Office-365-Security-Compliance-Center-0d4d0f35-390b-4518-800e-0c7ec95e946c).
>- Si las aplicaciones de Office están habilitadas, también se importan los grupos que forman parte de Office 365 a Cloud App Security desde las aplicaciones de Office específicas. Por ejemplo, si SharePoint está habilitado, se importan también grupos de Office 365 como grupos de SharePoint.
>- Debe [habilitar la auditoría en Power BI](https://powerbi.microsoft.com/documentation/powerbi-admin-auditing/) para obtener los registros desde ahí. Una vez habilitada, Cloud App Security empieza a obtener los registros (con un retraso de 24-72 horas).
> Si Azure Active Directory está establecido de modo que se sincronice automáticamente con los usuarios del entorno local de Active Directory, la configuración del entorno local reemplaza la configuración de Azure AD y se revierte el uso de la acción de gobierno **Suspender usuario**. 
 
1.  En la página **Conectores de aplicaciones**, haga clic en el botón del signo más y seleccione **Office 365**.  

2.  En el menú emergente de Office 365, haga clic en Conectar Office 365.

      ![conectar O365](./media/connect-0365.png) 
 
3.  Para probar la conexión a Office 365, haga clic en Probar ahora. La prueba puede tardar unos minutos.
  
    ![probar la conexión a O365](./media/o365-test-connection.png) 
 
4.   Cuando se indique que Office 365 está conectado correctamente, haga clic en **Cerrar**.
  
     ![O365 conectado](./media/o365-connected.png) 

> [!NOTE] 
> Después de conectar Office 365, podrá ver los datos de la semana anterior, incluidas las aplicaciones de terceros conectadas a Office 365 que extraen API. En el caso de las aplicaciones de terceros que no extraían API antes de la conexión, verá eventos a partir del momento en que conectó Office 365, ya que Cloud App Security activa las API que estaban desactivadas de forma predeterminada.

## <a name="see-also"></a>Consulte también  
[Controlar las aplicaciones en la nube con directivas](control-cloud-apps-with-policies.md)   
[Para obtener soporte técnico, visite la página de soporte técnico asistido de Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Los clientes Premier también pueden elegir Cloud App Security directamente desde el Portal Premier.](https://premier.microsoft.com/)  
  
  