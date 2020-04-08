---
title: Protección de archivos con la cuarentena de administrador de Cloud App Security
description: En este tutorial se describe el escenario para usar la cuarentena de administrador para controlar las vulneraciones de datos.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 7/30/2019
ms.topic: tutorial
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 83bb7ac4d1b75a98f426f97f09d6019befc221ad
ms.sourcegitcommit: 288c279a0d2dd62a8ad8d7425c3e9e98857bf5f4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/05/2020
ms.locfileid: "80666420"
---
# <a name="tutorial-protect-files-with-admin-quarantine"></a>Tutorial: Protección de archivos con la cuarentena de administrador

*Se aplica a: Microsoft Cloud App Security*

Las [directivas de archivo](data-protection-policies.md) son una excelente herramienta para buscar amenazas a las directivas de protección de la información. Por ejemplo, cree directivas de archivo que encuentren lugares en los que los usuarios almacenaron información confidencial, números de tarjetas de crédito y archivos ICAP de terceros en la nube.

Este tutorial lo ayudará a usar Microsoft Cloud App Security para que pueda detectar archivos no deseados almacenados en la nube que lo dejen en estado vulnerable y llevar a cabo acciones inmediatas para detener sus seguimientos, además de bloquear los archivos que suponen una amenaza mediante la **cuarentena de administrador** a fin de proteger los archivos en la nube, solucionar problemas e impedir que se produzcan otras vulneraciones a futuro.

> [!div class="checklist"]
>
> * Descripción del funcionamiento de la cuarentena
> * Configuración de la cuarentena de administrador

## <a name="understand-how-quarantine-works"></a>Descripción del funcionamiento de la cuarentena

>[!NOTE]
>
> * Para obtener una lista de las aplicaciones que admiten la cuarentena del administrador, vea la lista de [acciones de gobernanza](governance-actions.md).
> * Si se detecta que un archivo en SharePoint o OneDrive es malware, no se pone en cuarentena en el portal de Cloud App Security.
> * Los archivos con etiquetas no se pueden poner en cuarentena.

1. Cuando un archivo coincide con una directiva, la opción **Cuarentena de administrador** estará disponible para el archivo.

2. Lleve a cabo una de estas acciones para poner en cuarentena el archivo:

    * Aplique manualmente la acción **Cuarentena de administrador**:

    ![acción de cuarentena](media/quarantine-action.png)

    * Establézcalo como acción de cuarentena automatizada en la directiva:

    ![poner en cuarentena automáticamente](media/quarantine-automated.png)

3. Cuando se aplica la **cuarentena de administrador**, se producen las acciones siguientes en segundo plano:

    1. El archivo original se mueve a la carpeta de la cuarentena de administrador que estableció.
    2. Se elimina el archivo original.
    3. Un archivo de marcador de exclusión se carga a la ubicación del archivo original.

    ![marcador de exclusión en cuarentena](media/quarantine-tombstone.png)

    4. El usuario solo puede acceder al archivo de marcador de exclusión. En el archivo, puede leer las instrucciones personalizadas que proporciona el departamento de TI y el id. de correlación para dárselo a TI para que libere el archivo.

4. Cuando reciba la alerta de que un archivo se puso en cuarentena, investigue el archivo en la página **Alertas** de Cloud App Security:

    ![alertas de cuarentena](media/quarantine-alerts.png)

5. Y también en el **Informe de directiva** en la pestaña **En cuarentena**:

    ![informe de cuarentena](media/quarantine-report.png)

6. Una vez que un archivo se pone en cuarentena, use este proceso para solucionar la situación de amenaza:

    1. Inspeccione el archivo en la carpeta de elementos en cuarentena de SharePoint Online.
    2. También puede consultar los registros de auditoría para examinar en profundidad las propiedades del archivo.
    3. Si encuentra que el archivo va en contra de la directiva corporativa, ejecute el proceso de respuesta a incidentes (IR) de la organización.
    4. Si observa que el archivo es inocuo, puede restaurar el archivo que está en cuarentena. En ese momento se libera el archivo original, lo que significa que se vuelve a copiar en la ubicación original, se elimina el marcador de exclusión y el usuario puede acceder al archivo.

      ![restauración de cuarentena](media/quarantine-restore.png)

7. Compruebe que la directiva se ejecuta sin problemas. Luego, puede usar las acciones de gobernanza automática en la directiva para impedir futuras filtraciones y aplicar automáticamente una cuarentena de administración cuando se cumpla la directiva.

> [!NOTE]
> Cuando restaure un archivo:
>
> * Los recursos compartidos originales no se restauran, se aplica la herencia de carpetas predeterminada.
> * El archivo restaurado contiene solo la versión más reciente.
> * La administración del acceso al sitio de la carpeta de cuarentena es responsabilidad del cliente.

## <a name="set-up-admin-quarantine"></a>Configuración de la cuarentena de administrador

1. Establezca directivas de archivo que detecten infracciones. Entre los ejemplos de estos tipos de directivas se incluyen los siguientes:

    - Una directiva de solo metadatos, como una etiqueta de clasificación en SharePoint Online.
    - Una directiva DLP nativa, como una directiva que busca números de tarjeta de crédito.
    - Una directiva ICAP de terceros, como una directiva que busca Vontu.

2. Establezca una ubicación para la cuarentena:
   1. En Office 365 SharePoint o OneDrive para la Empresa, no puede colocar archivos en la cuarentena de administrador como parte de una directiva hasta que la configure: ![configuración de la cuarentena](media/quarantine-warning.png).

      Para establecer la configuración de la cuarentena de administración, en el engranaje de configuración, vaya a **Configuración**. Proporcione una ubicación para los archivos en cuarentena y una notificación de usuario que el usuario recibirá cuando su archivo se ponga en cuarentena.
      ![configuración de cuarentena](media/quarantine-settings.png)

   2. En Box, no se puede personalizar la ubicación de la carpeta de cuarentena ni el mensaje del usuario. La ubicación de la carpeta es la unidad del administrador que conectó Box con Cloud App Security y el mensaje del usuario es: Este archivo se puso en cuarentena en la unidad del administrador porque es posible que infrinja las directivas de cumplimiento y de seguridad de la empresa. Póngase en contacto con el administrador de TI para obtener ayuda.

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Actividades diarias para proteger el entorno de nube](daily-activities-to-protect-your-cloud-environment.md)

[!INCLUDE [Open support ticket](includes/support.md)]
