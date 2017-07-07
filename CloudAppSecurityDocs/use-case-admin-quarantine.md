---
title: "Caso de uso sobre cómo investigar y corregir las infracciones de archivo mediante la cuarentena de administrador | Microsoft Docs"
description: "En este tema se describe cómo usar la cuarentena de administrador para controlar las infracciones de datos."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 5/23/2017
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: 3fc04cfb-ad4c-4ac2-980a-ee9f4c740d88
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: dc11707b422613d82789a736c97aaa4b7ecddd6d
ms.sourcegitcommit: 2f4474084c7e07ac4853945ab5aa1ea78950675d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/28/2017
---
# <a name="protecting-your-files-with-admin-quarantine"></a>Proteger los archivos con la cuarentena de administrador

> [!NOTE]
> Se trata de una característica en vista previa.

Las [directivas de archivo](data-protection-policies.md) son una herramienta excelente para buscar las amenazas para las directivas de protección de información, por ejemplo, para buscar los lugares donde los usuarios almacenan información confidencial, números de tarjetas de crédito y archivos ICAP de terceros en la nube. Con Cloud App Security, no solo puede detectar estos archivos no deseados almacenados en la nube que generan vulnerabilidad, sino que puede emprender acciones inmediatas para detenerlos de inmediato y bloquear los archivos que supongan una amenaza. Mediante la **cuarentena de administrador**, puede proteger los archivos en la nube y solucionar los problemas, así como evitar que se produzcan fugas en el futuro. 

>[!NOTE] 
> Para obtener una lista de las aplicaciones que admiten la cuarentena de administrador, vea la lista de [acciones de gobierno](governance-actions.md).
 
## <a name="how-quarantine-works"></a>Cómo funciona la cuarentena 

1. Cuando un archivo coincida con una directiva, la opción de **cuarentena de administrador** estará disponible para el archivo.

3. Realice una de las acciones siguientes para poner en cuarentena el archivo:
    - Aplique manualmente la acción de **cuarentena de administrador**:
     
      ![acción de cuarentena](./media/quarantine-action.png)

    - Establézcala como una acción de cuarentena automatizada en la directiva: 

     ![poner en cuarentena automáticamente](./media/quarantine-automated.png)

4. Cuando se aplica la **cuarentena de administrador**, ocurre lo siguiente en segundo plano:

    1. El archivo original se mueve a la carpeta de cuarentena de administrador que haya establecido.
    2. Se elimina el archivo original.
    3. Se carga un archivo de marcador de exclusión en la ubicación original del archivo.

      ![marcador de exclusión de cuarentena](./media/quarantine-tombstone.png)

    4. El usuario tiene acceso únicamente al marcador de exclusión, donde puede leer las instrucciones personalizadas proporcionadas por el departamento de TI y el identificador de correlación para ponerse en contacto con los profesionales de TI para liberar el archivo.

4. Cuando aparezca la alerta que indica que un archivo se ha puesto en cuarentena, investigue el archivo en la página **Alertas** de Cloud App Security:

   ![alertas de cuarentena](./media/quarantine-alerts.png)
 
5. También en el **Informe de la directiva** en la pestaña **En cuarentena**:

  ![informe de cuarentena](./media/quarantine-report.png)
    
5. Una vez que un archivo se ha puesto en cuarentena, siga el proceso siguiente para corregir la situación de amenaza:
       
    1. Inspeccione el archivo en la carpeta en cuarentena en SharePoint Online.
    3. También puede consultar los registros de auditoría para profundizar en las propiedades del archivo.
    4. Si se descubre que el archivo va contra la directiva corporativa, ejecute el proceso de Respuesta a incidentes (IR) de la organización.
    5. Si se descubre que el archivo es inofensivo, puede restaurarlo de la cuarentena, con lo que se libera el archivo original, es decir, se copia de nuevo en la ubicación original, se elimina el marcador de exclusión y el usuario puede tener acceso al archivo.
       ![restauración de la cuarentena](./media/quarantine-restore.png)
6. Una vez que haya comprobado que la directiva se ejecuta sin problemas, puede usar las acciones de gobierno automáticas de la directiva para evitar más fugas y aplicar automáticamente la cuarentena de administrador cuando se produzca una coincidencia con la directiva.

>[!NOTE]
>Al restaurar un archivo:
- No se restauran los recursos compartidos originales y se aplica la herencia de carpetas predeterminada.
- El archivo restaurado solo contiene la versión más reciente.


>[!NOTE]
>La administración del acceso al sitio de la carpeta de cuarentena es responsabilidad del cliente.

#### <a name="how-to-set-up-admin-quarantine"></a>Cómo configurar la cuarentena de administrador

1. Establezca directivas de archivo que detecten infracciones, como una directiva de solo metadatos (por ejemplo, una etiqueta de clasificación en SharePoint Online), una directiva DLP nativa (por ejemplo, una directiva que busque números de tarjetas de crédito) o una directiva de terceros ICAP (por ejemplo, una directiva que busque Vontu).

2. Establezca una ubicación de cuarentena:
    1. En el caso de Office 365 SharePoint y OneDrive para la Empresa, antes de establecer la cuarentena de administrador, no podrá colocar los archivos en cuarentena de administrador como parte de una directiva: ![configuración de cuarentena](./media/quarantine-warning.png)

    Para configurar los valores de la cuarentena de administrador, en el engranaje de configuración, vaya a **Configuración general** y proporcione la ubicación de los archivos en cuarentena y la notificación que el usuario recibirá cuando su archivo se ponga en cuarentena. 
    ![configuración de cuarentena](./media/quarantine-settings.png)

    2. En el caso de Box, no se puede personalizar la ubicación de la carpeta de cuarentena ni el mensaje de usuario. La ubicación de la carpeta es la unidad del administrador que ha conectado Box con Cloud App Security y el mensaje de usuario es el siguiente: "Este archivo se puso en cuarentena en la unidad del administrador porque es posible que infrinja las directivas de cumplimiento y de seguridad de la empresa. Póngase en contacto con el administrador de TI para obtener ayuda".



## <a name="see-also"></a>Consulte también  
[Actividades diarias para proteger el entorno de nube](daily-activities-to-protect-your-cloud-environment.md)   
[Para obtener soporte técnico, visite la página de soporte técnico asistido de Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Los clientes Premier también pueden elegir Cloud App Security directamente desde el Portal Premier.](https://premier.microsoft.com/)  
  
  