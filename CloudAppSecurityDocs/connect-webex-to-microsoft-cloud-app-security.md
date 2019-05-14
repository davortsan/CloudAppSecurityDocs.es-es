---
title: Conectar WebEx cloud App Security
description: En este artículo proporciona información sobre cómo conectar su aplicación de WebEx a Cloud App Security mediante el conector de API para la visibilidad y control sobre el uso.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: rkarlin
ms.date: 04/16/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: c43271fd-9a61-4727-9945-de1c6ea5422c
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: be23b571e25ba283bd661f647cf38d462b37882b
ms.sourcegitcommit: 9f0c562322394a3dfac7f1d84286e673276a28b1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/14/2019
ms.locfileid: "65568174"
---
# <a name="connect-cisco-webex-to-microsoft-cloud-app-security"></a>Conectar Cisco WebEx con Microsoft Cloud App Security

*Se aplica a: Microsoft Cloud App Security*

Este artículo proporciona instrucciones para conectar Microsoft Cloud App Security con una cuenta de Cisco WebEx existente mediante las API del conector. Esta conexión proporciona visibilidad sobre y control sobre los usuarios, actividades y los archivos de WebEx. 
 
## <a name="prerequisites"></a>Requisitos previos

- Se recomienda que cree una cuenta de servicio dedicada para la conexión. Esto le permite ver que las acciones de gobierno realizadas en WebEx como se realiza desde esta cuenta, como eliminan los mensajes enviados de WebEx. En caso contrario, el nombre del administrador que ha había conectado a Cloud App Security a WebEx aparecerá como el usuario que realiza las acciones.  
- Debe tener Administrador total **y** permisos de administrador de cumplimiento de WebEx.


## <a name="how-to-connect-webex-to-cloud-app-security"></a>Cómo conectar WebEx a Cloud App Security  
  
1.  En la consola de Cloud App Security, haga clic en **Investigar** y, después, en **Aplicaciones conectadas**.  
  
2.  En el **conectores de aplicaciones** página, haga clic en el botón del signo más seguido **Cisco WebEx**.  
  
     ![conectar WebEx](./media/cisco-webex.png "conectar WebEx")  
  
3.  En el menú emergente, escriba el nombre de instancia de este conector.  
  
4.  Haga clic en **conectar Cisco Webex**. Se abre la página de inicio de sesión de WebEx. Escriba sus credenciales para permitir que Cloud App Security acceda a la instancia de WebEx de su equipo.  
  
6.  WebEx le pregunta si desea permitir que Cloud App Security acceda a la información de su equipo, el registro de actividad y que realice actividades como un miembro del equipo. Para continuar, haga clic en **Permitir**.  
  
7.  En la consola de Cloud App Security, debería recibir un mensaje que se ha conectado correctamente WebEx.  
  
8.  Haga clic en **Probar API** para confirmar que la conexión se ha realizado correctamente.  
  
     La prueba puede tardar unos minutos. Cuando reciba la notificación de que se ha realizado correctamente, haga clic en **Cerrar**.  
  
Después de conectar WebEx, recibirá eventos durante 7 días anteriores a la conexión. Cloud App Security examina los eventos en los últimos tres meses. Para aumentar esta opción, debe tener una licencia de pro de Cisco WebEx y abra una incidencia con soporte técnico de Cloud App Security.

 
## <a name="next-steps"></a>Pasos siguientes 
[Controlar las aplicaciones en la nube con directivas](control-cloud-apps-with-policies.md)   

[Los clientes Premier también pueden crear una solicitud de soporte técnico directamente en el portal Premier.](https://premier.microsoft.com/)  
  
  
