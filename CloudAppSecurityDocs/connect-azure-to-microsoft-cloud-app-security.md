---
title: Conectar Azure con Cloud App Security para la visibilidad y el control del uso | Microsoft Docs
description: "En este tema se proporciona información sobre cómo conectar Azure con Cloud App Security mediante el conector de API."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 9/3/2017
ms.topic: get-started-article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: 3a677bc7-c8b7-4c6a-aada-82c8b3778352
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 7e2b6d0f02d49eaa4354f5344d0555fc3f503fb8
ms.sourcegitcommit: 5688d3916a54deada225f7a83c34a7c501953960
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/04/2017
---
# <a name="connect-azure-to-microsoft-cloud-app-security"></a>Conectar Azure con Microsoft Cloud App Security

En esta sección se proporcionan instrucciones para conectar Cloud App Security con una cuenta de Azure existente mediante la API del conector de aplicaciones.  
  
## <a name="setting-up-azure-for-connection-to-cloud-app-security"></a>Configurar Azure para la conexión con Cloud App Security

Cloud App Security se conecta a Azure mediante centros de eventos. En esta sección se proporcionan instrucciones para transmitir mediante streaming todos los registros de actividad a un único centro de eventos de la suscripción. 

### <a name="step-1-stream-your-azure-activity-logs-to-event-hubs"></a>Paso 1: Transmitir mediante streaming los registros de actividad de Azure a centros de eventos

1.  Transmita mediante streaming el registro de actividad de Azure de la suscripción de Azure a un centro de eventos. Siga la guía oficial de la documentación de Azure: https://docs.microsoft.com/es-es/azure/monitoring-and-diagnostics/monitoring-stream-activity-logs-event-hubs

 > [!NOTE]
 > Si tiene más de una suscripción a Azure, repita este paso para cada suscripción, pero use un único centro de eventos que compartan las suscripciones.

 Después de completar las instrucciones, se creará un centro de eventos en el espacio de nombres seleccionado.
 
 > [!NOTE]
 > Si se produce un error después de intentar exportar los registros de actividad, vaya a la hoja **Proveedores de recursos** de Azure y asegúrese de que “microsoft.insights” está registrado.

### <a name="step-2-get-a-connection-string-to-your-event-hub"></a>Paso 2: obtener una cadena de conexión para el centro de eventos

1.  Vaya la hoja **Event Hubs - Versión preliminar**.
  
   ![Hoja Centros de eventos](media/azure-event-hubs.png "Centros de eventos de Azure")

2.  Seleccione el espacio de nombres de su centro de eventos.
  
    ![Espacio de nombres del centro de eventos](media/azure-namespace.png "Espacio de nombres de Azure")

3.  En el menú, en **Entidades**, haga clic en **Centros de eventos**. 
  
    ![Entidades de Centros de eventos](media/azure-event-hubs-entities.png "Entidades del centro de eventos de Azure")

4.  Seleccione el nuevo centro de eventos creado por Azure Monitor. Se denomina **insights-operational-logs**.
  > [!NOTE]
  > Pueden pasar unos minutos hasta que se cree el centro de eventos.

   ![Registros operativos de información](media/azure-insight-operational-logs.png "Registros operativos de información de Azure")
  
  
5. Cree una directiva de acceso que conceda permiso a Cloud App Security para leer en el centro de eventos. Para ello, haga clic en **Directivas de acceso compartido** y en **Agregar**.
  
    ![Directivas de acceso compartido](media/azure-shared-access-policies.png "Directiva de acceso compartido de Azure")

6.  Escriba un nombre para la nueva directiva y asegúrese de incluir por lo menos la **notificación Escuchar**. Cuando termine, haga clic en **Crear**.
  
    ![Nueva directiva de Azure](media/azure-new-policy.png "Crear directiva de Azure")

7.  En **Configuración** y en **Directivas de acceso compartido**, haga clic en la directiva de acceso que acaba de crear.   
  
    ![Seleccionar directiva de Azure](media/azure-select-policy.png "Seleccionar directiva de Azure")

8. En la ventana de la directiva, copie una de las cadenas de conexión. Para ello, haga clic en el botón situado junto a **Cadena de conexión: clave principal** o **Cadena de conexión: clave secundaria**.

### <a name="step-3-add-azure-to-cloud-app-security"></a>Paso 3: agregar Azure a Cloud App Security
 
1.  En el portal de Cloud App Security, haga clic en **Investigar** y, después, en **Aplicaciones conectadas**.  
  
3.  En la página **Conectores de aplicaciones**, haga clic en el botón del signo más y seleccione **Microsoft Azure**.  
  
     ![conectar Azure con Cloud App Security](media/azure-connect-app.png "conectar Azure")  
  
4.  En el campo **Cadena de conexión**, pegue la cadena de conexión que ha copiado en el paso anterior.  
  
5.  En el campo **Grupo de consumidores**, escriba: `$Default`
    
   >[!NOTE] 
   > Si ha creado un grupo de consumidores diferente, use el nombre de ese **grupo de consumidores**.
  
6.  Haga clic en **Conectar**.
     Esta acción probará la conexión y puede tardar unos minutos en completarse. Cuando reciba la notificación de que se ha realizado correctamente, haga clic en **Cerrar**.  


> [!NOTE]
> Esta característica está en versión preliminar pública.


## <a name="see-also"></a>Consulte también  
[Controlar las aplicaciones en la nube con directivas](control-cloud-apps-with-policies.md)   
[Para obtener soporte técnico, visite la página de soporte técnico asistido de Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Los clientes Premier también pueden elegir Cloud App Security directamente desde el Portal Premier.](https://premier.microsoft.com/)  
  
  