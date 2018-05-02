---
title: Crear informes de instantánea del uso de aplicaciones en la nube de Cloud Discovery | Microsoft Docs
description: En este artículo se proporciona información sobre cómo cargar registros manualmente para crear un informe de instantáneas de las aplicaciones de Cloud Discovery.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 4/22/2018
ms.topic: article
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: ecc1949d-c861-4636-952a-c3a260719bb5
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: c2c9395841277f14d59b83cd0883f8e98cc38a6e
ms.sourcegitcommit: 45311f2cafef79483e40d971a4c61c7673834d96
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2018
---
*Se aplica a: Microsoft Cloud App Security*


# <a name="create-snapshot-cloud-discovery-reports"></a>Crear informes de instantáneas de Cloud Discovery
Es importante cargar un registro manualmente y dejar que Microsoft Cloud App Security lo analice antes de intentar usar el recopilador de registros automáticos.
Si aún no tiene un registro y quiere ver un ejemplo del aspecto que debería tener, siga el procedimiento siguiente para descargar un archivo de registro de ejemplo.


Para crear un informe de instantáneas:
  
1. Recopile archivos de registro del firewall y el servidor proxy a través de los cuales los usuarios de la organización acceden a Internet. Asegúrese de recopilar registros durante períodos de tráfico pico que sean representativos de toda la actividad de usuario de la organización.  
  
2. En el portal de Cloud App Security, haga clic en **Detectar** y, después, en **Crear nuevo informe de instantáneas**.  
  
   ![Crear nuevo informe de instantáneas](./media/create-new-snapshot-report.png)
     
3. Escriba un **nombre de informe** y una **descripción**
  
    ![Nuevo informe de instantáneas](./media/new-snapshot-report.png) 

4. Seleccione el **Origen de datos** desde el que quiere cargar los archivos de registro.  
  
5. Compruebe el formato del registro para asegurarse de que es correcto según el ejemplo que puede descargar. Haga clic en **View and verify** (Ver y comprobar) y luego haga clic en **Download sample log** (Descargar registro de ejemplo). Después, compare su registro con el ejemplo proporcionado para asegurarse de que es compatible. 

   ![Comprobar el formato del registro](./media/cloud-discovery-snapshot-verify.png)  

   > [!NOTE]
   > El formato FTP de ejemplo se admite en las instantáneas y la carga automatizada, mientras que Syslog solo se admite en la carga automatizada.<br></br>
   Si se descarga un registro de ejemplo, se descargará un registro de FTP de ejemplo.


6. **Elija los registros de tráfico** que quiera cargar. Puede cargar hasta 20 archivos a la vez. También se admiten los archivos comprimidos.  
  
7. Haga clic en **Crear**.  

8. Una vez finalizada la carga, aparecerá el mensaje de estado en la esquina superior derecha de la pantalla, que informa de que el registro se ha cargado correctamente.  
  
9. Después de cargar los archivos de registro, pasará algún tiempo hasta que se redistribuyan y se analicen.  
   Una vez completado el procesamiento de los archivos de registro, recibirá un correo electrónico que le notificará que ya está listo. 
  
10. En la barra de estado de la parte superior del portal aparecerá un banner de notificación para mantenerlo informado del estado de procesamiento de los archivos de registro.  
    ![barra de menú del procesamiento del archivo de registro](./media/processing-log-file-menu-bar.png) 
   
11. Una vez cargados correctamente los registros, verá una notificación informándole de que el procesamiento de los archivos de registro se ha completado correctamente. En este punto, puede ver el informe. Para ello, haga clic en el vínculo de la barra de estado o vaya al icono de engranaje de configuración y seleccione **Cloud Discovery settings** (Configuración de Cloud Discovery).   
  
     ![Pestaña de configuración de Cloud Discovery](./media/discovery-settings-tab.png)
12. Después, seleccione **Informes de instantáneas** y elija el informe de instantáneas.
 
![administración de informes de instantáneas](./media/snapshot-report-managment.png)

  
      
## <a name="see-also"></a>Consulte también  
[Controlar las aplicaciones en la nube con directivas](control-cloud-apps-with-policies.md)   

[Los clientes Premier también pueden elegir Cloud App Security directamente desde el Portal Premier.](https://premier.microsoft.com/)  
    
      
  