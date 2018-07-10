---
title: Visibilidad de las actividades de aplicaciones en la nube | Microsoft Docs
description: En este tema se proporciona una lista de actividades, filtros y parámetros de coincidencia que se pueden aplicar a directivas de actividad.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 7/1/2018
ms.topic: article
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: f3af2d25-9286-4e9b-b2ad-35653bec72ff
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 75731e401111286d3760163e512b623d6e85fdf2
ms.sourcegitcommit: 9d2a34a2d4145b39d855dd6f596c0fc858b92f9b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/02/2018
ms.locfileid: "37340029"
---
*Se aplica a: Microsoft Cloud App Security*


# <a name="activities"></a>Actividades
Microsoft Cloud App Security le ofrece visibilidad de todas las actividades de las aplicaciones conectadas. Después de conectar Cloud App Security con una aplicación mediante el conector de aplicaciones, Cloud App Security examina todas las actividades que se han producido (el período de tiempo de examen retroactivo varía según la aplicación) y después se actualiza constantemente con nuevas actividades. 

> [!NOTE] 
> Para obtener una lista completa de las actividades de Office 365 supervisadas por Cloud App Security, consulte [Buscar en el registro de auditoría del Centro de seguridad y cumplimiento de Office 365](https://support.office.com/article/Search-the-audit-log-in-the-Office-365-Security-Compliance-Center-0d4d0f35-390b-4518-800e-0c7ec95e946c?ui=en-US&rs=en-US&ad=US#ID0EABAAA=Audited_activities).

Se puede filtrar el **registro de actividades** para que pueda buscar actividades específicas. Puede crear directivas basadas en las actividades y después definir sobre qué quiere recibir alertas y actuar en consecuencia. También puede buscar actividades realizadas en determinados archivos. El tipo de actividades y la información que obtenemos de cada actividad dependen de la aplicación y de qué tipo de datos puede proporcionar la aplicación. 

Por ejemplo, puede usar el **registro de actividades** para buscar usuarios de la organización que usan sistemas operativos o exploradores que no están actualizados de la siguiente forma: después de conectar una aplicación a Cloud App Security en la página del **registro de actividades**, use el filtro avanzado y seleccione **User agent tag** (Etiqueta de agente de usuario). Después, seleccione **Outdated browser** (Explorador obsoleto) u **Outdated operating system** (Sistema operativo obsoleto).

 ![Ejemplo de actividad de explorador obsoleto](media/activity-example-outdated.png)
 
El filtro básico proporciona excelentes herramientas para empezar a filtrar sus actividades.

 ![filtro de registro de actividad básica](media/activity-log-filter-basic.png)

Para profundizar en actividades más específicas, puede ampliar el filtro básico haciendo clic en Opciones avanzadas.

 ![filtro de registro de actividad avanzada](media/activity-log-filter-advanced.png)

> [!NOTE] 
> La etiqueta Heredado se agrega a cualquier directiva de actividad que use el filtro de "usuario" anterior. Este filtro seguirá funcionando como de costumbre. Si quiere quitar la etiqueta Heredado, puede quitar el filtro y volver a agregarlo con el nuevo filtro **Nombre de usuario**.
 
## <a name="the-activity-drawer"></a>El cajón de actividades

### <a name="working-with-the-activity-drawer"></a>Trabajo con el cajón de actividades

Para ver más información sobre cada actividad, haga clic en la misma actividad en el registro de actividades. Se abrirá el cajón de actividades, que proporciona las siguientes acciones e información adicionales para cada actividad:

   - Directivas coincidentes: haga clic en el vínculo Directivas coincidentes para ver una lista de las directivas con las que coincide esta actividad.

   - Ver datos sin procesar: haga clic en la opción para ver los datos sin procesar para ver los datos reales recibidos desde la aplicación.

   - Usuario: haga clic en el usuario para ver la página correspondiente al usuario que realizó la actividad. 

   - Tipo de dispositivo: haga clic en el tipo de dispositivo para ver los datos sin procesar del agente de usuario. 

   - Ubicación: haga clic en la ubicación para ver la ubicación en los mapas de Bing.

   - Categoría y etiquetas de la dirección IP: haga clic en la etiqueta IP para ver la lista de etiquetas IP que se encuentran en esta actividad. Después, puede filtrar por todas las actividades que coinciden con esta etiqueta.    

 Los campos del cajón de actividades proporcionan vínculos contextuales a actividades adicionales y exploran en profundidad lo que desea realizar desde el cajón directamente. Por ejemplo, si mueve el cursor junto a la categoría de dirección IP, puede utilizar el icono Filtrar ![Agregar a filtro](./media/add-to-filter-icon.png) para agregar la dirección IP inmediatamente al filtro de la página actual. También puede utilizar el icono de engranaje de configuración ![icono de configuración](./media/contextual-settings-icon.png) que aparece para llegar directamente a la página de configuración necesaria para modificar la configuración de uno de los campos, como **Grupos de usuarios**.

 También puede usar los iconos de la parte superior de la pestaña para:
 - Ver las actividades del mismo tipo
 - Ver todas las actividades del mismo usuario
 - Ver las actividades de la misma dirección IP
 - Ver las actividades de la misma ubicación geográfica
 - Ver las actividades del mismo período (48 horas)
 
![cajón de actividades](./media/activity-drawer.png "cajón de actividades")  
  
Para obtener una lista de las acciones de control disponibles, vea [Acciones de control de actividades](governance-actions.md#activity-governance-actions).

#### <a name="user-insights"></a>Información de usuario

La experiencia de investigación incluye información predeterminada sobre el usuario activo. Con un solo clic, puede obtener una descripción detallada del usuario, incluida la ubicación desde la que se ha conectado, con cuántas alertas abiertas está relacionado e información sobre sus metadatos.

Para ver la información de usuario:

1. Haga clic en la actividad en el **Registro de actividades**.

2. Después, haga clic en la pestaña **Usuario**. <br></br> Se abrirá la pestaña **Usuario** del cajón de actividades, que contiene la información siguiente sobre el usuario:
    - **Alertas abiertas**: número de alertas abiertas relacionadas con el usuario.
    - **Infracción de archivos**: número de infracciones de archivo relacionadas con archivos que posee el usuario.
    - **Actividades**: número de actividades realizadas por el usuario durante los últimos 30 días.
    - **Países**: número de países desde los que se ha conectado el usuario durante los últimos 30 días.
    - **ISP**: número de ISP desde los que se ha conectado el usuario durante los últimos 30 días.
    - **Direcciones IP**: número de direcciones IP desde las que se ha conectado el usuario durante los últimos 30 días.

![información de usuario en Cloud App Security](./media/user-insights.png)

#### <a name="ip-address-insights"></a>Información de dirección IP

Debido a que la información de dirección IP es fundamental para casi todas las investigaciones, puede ver información detallada sobre las direcciones IP en el cajón de actividades. Desde una actividad específica, puede hacer clic en la pestaña de dirección IP para ver los datos consolidados sobre la dirección IP, incluido el número de alertas abiertas para la dirección IP específica, un gráfico de tendencias de la actividad reciente y un mapa de ubicación. Esto permite explorar en profundidad; por ejemplo, cuando se investigan alertas de viajes imposibles, puede comprender fácilmente dónde se usó la dirección IP y si participó o no en actividades sospechosas. También puede realizar acciones directamente en el cajón de direcciones IP que le permiten etiquetar una dirección IP como de riesgo, VPN o corporativa para facilitar una investigación futura y la creación de directivas.

Para ver la información de dirección IP:

1. Haga clic en la actividad en el **Registro de actividades**.

2. Luego haga clic en la pestaña **Dirección IP**. <br></br> Se abrirá la pestaña **Dirección IP** del espacio de actividades, que ofrece la información siguiente sobre la dirección IP:
    - **Alertas abiertas**: número de alertas abiertas relacionadas con la dirección IP.
    - **Actividades**: número de actividades realizadas por la dirección IP durante los últimos 30 días.
    - **Ubicación de IP**: ubicaciones geográficas desde las cuales se conectó la dirección IP durante los últimos 30 días.
    - **Actividades**: número de actividades realizadas desde esta dirección IP durante los últimos 30 días.
    - **Actividades administrativas**: número de actividades administrativas realizadas desde esta dirección IP durante los últimos 30 días.
    - Puede realizar las siguientes acciones en la dirección IP:
        - Etiquetar como riesgosa 
        - Etiquetar como dirección IP de VPN
        - Etiquetar como dirección IP riesgosa y agregar al grupo bloqueado


![Información de dirección IP en Cloud App Security](./media/ip-address-insights.png)

## Exportar actividades <a name="export"></a>

Puede exportar todas las actividades de usuario a un archivo CSV. 

En el **registro de actividad**, en la esquina superior derecha, haga clic en el botón **exportar** ![botón exportar](./media/export-button.png).

[!INCLUDE [Handle personal data](../includes/gdpr-intro-sentence.md)]



## <a name="see-also"></a>Consulte también  
[Actividades diarias para proteger el entorno de nube](daily-activities-to-protect-your-cloud-environment.md)   

[Los clientes Premier también pueden elegir Cloud App Security directamente desde el Portal Premier.](https://premier.microsoft.com/)  
  
  