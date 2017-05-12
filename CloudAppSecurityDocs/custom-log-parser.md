---
title: Uso del analizador de registros personalizado para registros no admitidos | Microsoft Docs
description: "En este artículo se proporciona información sobre el empleo del analizador de registros personalizado para cargar registros de dispositivos que no son compatibles con Cloud App Security."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 5/7/2017
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: a612d87e-5471-4add-b4b1-dbbb530f2b61
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 73da4104de24a7b2e6814f04b227140b0b57235f
ms.sourcegitcommit: 945cb3c047ae1bfc05be20cc7798c43005b27c9b
ms.translationtype: HT
ms.contentlocale: es-ES
---
# <a name="use-a-custom-log-parser"></a>Uso del analizador de registros personalizado
Cloud App Security le permite configurar un analizador personalizado para satisfacer y procesar el formato de los registros de modo que se puedan usar para Cloud Discovery, incluso si proceden de un firewall o un dispositivo que no se admite explícitamente por Cloud App Security. 

El analizador personalizado le permite utilizar registros de firewalls no admitidos siguiendo este proceso. 


 
Para configurar un analizador CSV personalizado:
1.    En el portal de Cloud App Security, haga clic en **Detectar** y, después, en **Crear nuevo informe de instantáneas**.  
  
    ![Crear nuevo informe de instantáneas](./media/create-new-snapshot-report.png)
     
3.  Escriba un **nombre de informe** y una **descripción**
  
4.  En **Origen de datos**, seleccione **Custom log format...**  (Formato de registro personalizado...).  

     ![Nuevo informe de instantáneas](./media/custom-log-upload.png)   

5. Recopile archivos del firewall y el servidor proxy a través de los cuales los usuarios de la organización obtienen acceso a Internet. Asegúrese de recopilar registros durante períodos de tráfico pico que sean representativos de toda la actividad de usuario de la organización. 

6. Abra los registros que desea procesar en un editor de texto y revise su formato, asegurándose de que los nombres de columna del registro se correspondan con los campos de la pantalla **Custom log format** (Formato de registro personalizado).

  ![analizador de registro personalizado](./media/log-data.png) 

7. A continuación, rellene los campos de acuerdo con sus datos para delinear las columnas de datos que se relacionan con campos específicos de Cloud App Security. Tendrá que modificar los nombres de columna del archivo de registro para establecer correctamente la relación.
  
   > [!NOTE]
    > Estos campos distinguen mayúsculas de minúsculas. Asegúrese de escribir los nombres de las columnas de forma idéntica en Cloud App Security y en el archivo de registro. Además, asegúrese de que el formato de fecha seleccionado es idéntico.

   ![analizador de registro personalizado](./media/custom-log-parser.png) 


7. Haga clic en **Guardar**. El formato de registro personalizado que ha configurado se guardará como analizador personalizado de forma predeterminada. Puede editarlo en cualquier momento haciendo clic en Editar.

5. En **Elija los registros de tráfico**, seleccione el archivo de registro que se ha modificado y cárguelo. Puede cargar hasta 20 archivos a la vez. También se admiten los archivos comprimidos.  
  

6.  Haga clic en **Crear**.  

7.  Una vez finalizada la carga, aparecerá el mensaje de estado en la esquina superior derecha de la pantalla, que informa de que el registro se ha cargado correctamente.  
  
8.  Después de cargar los archivos de registro, pasará algún tiempo hasta que se redistribuyan y se analicen.  
Una vez completado el procesamiento de los archivos de registro, recibirá un correo electrónico que le notificará que ya está listo. 
  
9. En la barra de estado de la parte superior del portal aparecerá un banner de notificación para mantenerlo informado del estado de procesamiento de los archivos de registro.  
![barra de menú del procesamiento del archivo de registro](./media/processing-log-file-menu-bar.png) 
   
10. Una vez cargados correctamente los registros, verá una notificación informándole de que el procesamiento de los archivos de registro se ha completado correctamente. En este punto, puede ver el informe. Para ello, haga clic en el vínculo de la barra de estado o vaya al icono de engranaje de configuración y seleccione **Cloud Discovery settings** (Configuración de Cloud Discovery).   
  
     ![Pestaña de configuración de Cloud Discovery](./media/discovery-settings-tab.png)
11. Después, seleccione **Administrar los informes de instantáneas** y seleccione su informe de instantáneas.
 
    ![administración de informes de instantáneas](./media/snapshot-report-managment.png)

  
      




## <a name="see-also"></a>Vea también
 
[Crear informes de instantáneas de Cloud Discovery](create-snapshot-cloud-discovery-reports.md)

[Configurar la carga de registros automática para informes continuos](configure-automatic-log-upload-for-continuous-reports.md)

[Trabajar con datos de Cloud Discovery](working-with-cloud-discovery-data.md)

