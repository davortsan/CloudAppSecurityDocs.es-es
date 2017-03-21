---
title: "Anonimización de datos de Cloud Discovery | Microsoft Docs"
description: "En este artículo se proporciona información sobre cómo anonimizar los nombres de usuario en los datos de Cloud Discovery."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 12/27/2016
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: eb250ede-fede-4699-a08b-b8ea4b232f07
ms.reviewer: reutam
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 99ad61811b68b47ac62b4bac83b611e535d4a6be
ms.openlocfilehash: 049494e45caf670f753f6b5fbfbbf117462b7156


---


## <a name="cloud-discovery-data-anonymization"></a>Anonimización de datos de Cloud Discovery

La anonimización de datos de Cloud Discovery le permite proteger la privacidad del usuario. Una vez que el registro de datos se ha cargado en el portal de Cloud App Security, se depura el registro y se reemplaza toda la información de nombres de usuario con nombres de usuario cifrados. De este modo, todas las actividades de la nube se mantienen anónimas. Cuando sea necesario, para una investigación de seguridad específica (por ejemplo, debido a una infracción de seguridad o una actividad sospechosa del usuario), los administradores pueden resolver el nombre de usuario real. Si un administrador tiene un motivo para sospechar de un usuario específico, puede buscar el nombre de usuario cifrado de un nombre de usuario conocido y, después, comenzar la investigación usando el nombre de usuario cifrado. En el **Registro de gobierno** del portal se audita cada conversión de nombre de usuario.

Puntos clave:
-   No se almacena ni se muestra ninguna información privada. Solo información cifrada.
-   Los datos privados se cifran mediante AES-128 con una clave dedicada por inquilino.
-   La resolución de nombres de usuario se realiza ad hoc, por nombre de usuario descifrando un nombre de usuario cifrado determinado.


Cómo funciona la anonimización de datos:

1.  Hay tres formas de aplicar la anonimización de datos: 
    
    - Puede configurar los datos para anonimizar desde un archivo de registro específico, mediante la [creación de un nuevo informe de instantáneas](create-snapshot-cloud-discovery-reports.md) y seleccionando **Anonymize private information** (Anonimizar información privada).
 ![Anonimización de datos de instantáneas](./media/anonymize-log.png)

    - Puede establecer los datos para anonimizar desde una [carga automatizada para un nuevo origen de datos](configure-automatic-log-upload-for-continuous-reports.md) seleccionando **Anonymize private information** (Anonimizar información privada) al agregar el nuevo origen de datos.  
 ![Anonimización de datos de registro](./media/anonymize-autolog.png)

    - Puede establecer el valor predeterminado en Cloud App Security para anonimizar todos los datos de los informes de instantáneas de los archivos de registro cargados y de los informes continuados de recopiladores de registros como se muestra a continuación:
     
        1. En el engranaje de configuración, seleccione **Configuración de Cloud Discovery**.
     
        2. En la pestaña Anonymization (Anonimización), para ocultar los nombres de usuario de forma predeterminada, seleccione **Anonymize private information by default in new reports and data sources** (Anonimizar información privada de forma predeterminada en los nuevos informes y orígenes de datos).
  ![Anonimización](./media/anonymizer.png)
  

2.  Cuando se selecciona la anonimización, Cloud App Security analiza el registro del tráfico y extrae los atributos de datos específicos.
3.  Cloud App Security reemplaza el nombre de usuario con un nombre de usuario cifrado.
4.  Después, analiza los datos de uso de la nube y genera informes de Cloud Discovery basados en los datos anónimos.
 ![Anonimización del panel de Cloud Discovery](./media/anonymize-dashboard.png)
 

5.  Para una investigación específica, como la investigación de una alerta de uso erróneo, puede resolver el nombre de usuario específico en el portal y proporcionar una justificación comercial. Esta página también se puede usar para buscar el nombre de usuario cifrado de un nombre de usuario conocido. 

    1. En el engranaje Configuración, seleccione **Configuración de Cloud Discovery**.
    2. En la pestaña **Anonymization** (Anonimización), en **Anonymize and resolve usernames** (Anonimizar y resolver nombres de usuario), escriba una justificación de por qué se realiza la resolución.
    3. En **Enter username to resolve** (Escriba el nombre de usuario para resolver), seleccione **From anonymized** (De anónimo) y escriba el nombre de usuario anónimo, o seleccione **To anonymized** (Para anónimo) y escriba el nombre de usuario original para resolver. Haga clic en **Resolver**. 
![Anonimización](./media/anonymizer.png)

6.  La acción se audita en el **Registro de gobierno** del portal. 
![Anonimización](./media/anonymize-gov-log.png)




  
      
## <a name="see-also"></a>Consulte también  
[Controlar las aplicaciones en la nube con directivas](control-cloud-apps-with-policies.md)   
[Para obtener soporte técnico, visite la página de soporte técnico asistido de Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Los clientes Premier también pueden elegir Cloud App Security directamente desde el Portal Premier.](https://premier.microsoft.com/)  
    
      
  


<!--HONumber=Dec16_HO4-->

