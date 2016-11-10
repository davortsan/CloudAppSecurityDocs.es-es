---
title: "Crear informes de instantáneas de Cloud Discovery | Microsoft Docs"
description: "En este artículo se proporciona información sobre cómo cargar registros manualmente para crear un informe de instantáneas de las aplicaciones de Cloud Discovery."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 10/15/2016
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: ecc1949d-c861-4636-952a-c3a260719bb5
ms.reviewer: reutam
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: ed4ea71b24767d3602d40894d1cbac7447bcd8a2
ms.openlocfilehash: 669d1c1942e8c7e930cd2421e9b56821eff04d12


---

# <a name="create-snapshot-cloud-discovery-reports"></a>Crear informes de instantáneas de Cloud Discovery
Es importante cargar un registro manualmente y dejar que Cloud App Security lo analice antes de intentar usar el recopilador de registros automáticos.

Para crear un informe de instantáneas:
  
1.  Recopile archivos de registro del firewall y el servidor proxy a través de los cuales los usuarios de la organización acceden a Internet. Asegúrese de recopilar registros durante períodos de tráfico pico que sean representativos de toda la actividad de usuario de la organización.  
  
2.  En el portal de Cloud App Security, haga clic en **Detectar** y, después, en **Crear nuevo informe de instantáneas**.  
  
     ![Crear nuevo informe de instantáneas](./media/create-new-snapshot-report.png)
     
      
3.  Escriba un **nombre de informe** y una **descripción**
  
4.  Seleccione el **Origen de datos** desde el que quiere cargar los archivos de registro.  
  
5.  **Elija los registros de tráfico** que quiera cargar. Puede cargar hasta 20 archivos a la vez.  
  
6.  Haga clic en **Crear**.  
  
     ![Nuevo informe de instantáneas](./media/new-snapshot-report.png) 
  
7.  Una vez finalizada la carga, aparecerá el mensaje de estado en la esquina superior derecha de la pantalla, que informa de que el registro se ha cargado correctamente.  
  
8.  Después de cargar los archivos de registro, pasará algún tiempo hasta que se redistribuyan y se analicen.  
Una vez completado el procesamiento de los archivos de registro, recibirá un correo electrónico que le notificará que ya está listo. 
  
9. En la barra de estado de la parte superior del portal aparecerá un banner de notificación para mantenerlo informado del estado de procesamiento de los archivos de registro.  
  
![barra de menú del procesamiento del archivo de registro](./media/processing-log-file-menu-bar.png) 
  
     After the logs are uploaded successfully, you should see a notification letting you know that the log file processing completed successfully.  
   
10. En este punto, puede ver el informe. Para ello, haga clic en el vínculo de la barra de estado o vaya al icono de engranaje de configuración y seleccione **Cloud Discovery settings** (Configuración de Cloud Discovery).   
  
     ![Pestaña de configuración de Cloud Discovery](./media/discovery-settings-tab.png)
11. Después, seleccione **Administrar los informes de instantáneas** y seleccione su informe de instantáneas.
 
![administración de informes de instantáneas](./media/snapshot-report-managment.png)
      
## <a name="see-also"></a>Consulte también  
[Controlar las aplicaciones en la nube con directivas](control-cloud-apps-with-policies.md)   
[Para obtener soporte técnico, visite la página de soporte técnico asistido de Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Los clientes Premier también pueden elegir Cloud App Security directamente desde el Portal Premier.](https://premier.microsoft.com/)  
    
      
  


<!--HONumber=Oct16_HO4-->


