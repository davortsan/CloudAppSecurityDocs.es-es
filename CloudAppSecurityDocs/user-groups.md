---
title: Importar grupos de usuarios de aplicaciones conectadas | Microsoft Docs
description: En este tema se proporcionan instrucciones para importar grupos de usuarios en Cloud App Security.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 12/9/2018
ms.topic: conceptual
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 87b831ef-5977-4df8-bed3-3ee54a8adbb5
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: d952746375c18730b92f7629ac4978c61ebfbfa9
ms.sourcegitcommit: c497253a7ab63973bb806607e5f15dece91640be
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/10/2018
ms.locfileid: "53123795"
---
*Se aplica a: Microsoft Cloud App Security*
   
# <a name="import-user-groups"></a>Importar grupos de usuarios

Al conectar aplicaciones mediante conectores de API, Microsoft Cloud App Security permite importar grupos de usuarios de, por ejemplo, Office 365 y Azure Active Directory.
Hay dos tipos de grupos de usuarios: 
- Grupos automáticos </br>Microsoft Cloud App Security crea de manera predeterminada grupos automáticos. Por ejemplo, hay un grupo automático de usuarios denominado **Externos** que combina todos los usuarios de todas las aplicaciones que son externos a la organización y que tienen acceso a archivos o que se encontraban en las actividades de usuario en el inquilino.
 En Cloud App Security existen los siguientes grupos automáticos:
  - External
  - Administrador de Dropbox
  - Administrador de Office 365
  - Administrador de G Suite
  - Administrador de Box
  - Todos los perfiles estándar y personalizados de Salesforce, como Administrador del sistema de Salesforce. Vea [aquí](https://help.salesforce.com/articleView?id=standard_profiles.htm&language=en&type=0) la lista completa.

- Grupos importados</br>Puede importar cualquier grupo de las aplicaciones conectadas. Por ejemplo, puede importar grupos de usuarios de Office 365 (Active Directory) y otras aplicaciones conectadas. Esto le permite buscar amenazas en la organización, no solo examinando toda la organización o un usuario específico, sino un grupo específico. 

Puede aprovechar la existencia de grupos de usuarios importados para investigar qué documentos consulta el departamento de Recursos Humanos, para comprobar si sucede algo inusual en el grupo ejecutivo o para verificar si un miembro del grupo de administración ha llevado a cabo alguna actividad fuera del país. Para importar grupos de usuarios:

1. En la barra de menús, haga clic en el icono de configuración ![icono de configuración](./media/settings-icon.png "icono de configuración") y seleccione **Grupos de usuarios**.
2. Haga clic en **Importar grupo de usuarios**.

   ![Importar grupos de usuarios](./media/user-groups-add.png)

3. Seleccione la aplicación de la que va a importar el grupo de usuarios. La lista de aplicaciones dependerá de los conectores de aplicaciones implementados.
4. Seleccione el grupo que quiere importar. La lista de grupos disponibles incluirá todos los grupos de usuarios existentes en la aplicación. Si quiere agregar un grupo nuevo, deberá hacerlo directamente en la propia aplicación, y cuando aparezca aquí, deberá seleccionarlo.
5. En función del tamaño del grupo, la importación puede tardar hasta una hora. Puede seleccionar la opción de recibir una notificación por correo electrónico cuando finalice el proceso de importación.
6. Haga clic en **Importar**. Después de importar un grupo, Cloud App Security sincroniza automáticamente los miembros del grupo, igual que Active Directory Connect.
7. Una vez finalizada la importación, en la página **Grupos de usuarios** puede hacer clic en un grupo específico para ver una lista de todos los miembros del grupo. También puede hacer clic en cualquier miembro del grupo para consultar los detalles de una cuenta específica y para ver qué aplicaciones usan y un resumen de la cuenta con gráficos del usuario y su actividad, entre otras cosas.

La importación de grupos le permite seleccionar esos grupos como filtros cuando examine el **registro de actividad** y cuando cree directivas. 

> [!NOTE]
> - Para que las actividades se etiqueten como realizadas por un miembro del grupo de usuarios, deberán llevarse a cabo después de la importación de un grupo.
> - Después de la sincronización inicial, los grupos se actualizan cada hora.

Para obtener más información sobre el uso de los filtros de grupo de usuario, vea [Actividades](activity-filters.md).


    
## <a name="see-also"></a>Consulte también  
[Configurar Cloud Discovery](set-up-cloud-discovery.md)   

[Los clientes Premier también pueden crear una solicitud de soporte técnico directamente en el portal Premier.](https://premier.microsoft.com/)  
  
  