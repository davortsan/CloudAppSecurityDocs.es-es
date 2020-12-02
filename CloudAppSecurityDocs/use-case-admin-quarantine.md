---
title: Protección de archivos con la cuarentena de administrador de Cloud App Security
description: En este tutorial se describe el escenario para usar la cuarentena de administrador para controlar las vulneraciones de datos.
ms.date: 7/30/2019
ms.topic: tutorial
ms.openlocfilehash: 5d0a9e666b415806a0cb6a3a047f0b81e2b2a4fc
ms.sourcegitcommit: d87372b47ca98e942c2bf94032a6a61902627d69
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/30/2020
ms.locfileid: "96315776"
---
# <a name="tutorial-protect-files-with-admin-quarantine"></a>Tutorial: Protección de archivos con la cuarentena de administrador

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Las [directivas de archivo](data-protection-policies.md) son una excelente herramienta para buscar amenazas en las directivas de protección de la información. Por ejemplo, cree directivas de archivo que busquen los lugares en los que los usuarios almacenan información confidencial, números de tarjetas de crédito y archivos ICAP de terceros en la nube.

En este tutorial obtendrá información sobre cómo usar Microsoft Cloud App Security para detectar archivos no deseados almacenados en la nube que le hagan vulnerable. También aprenderá a emprender acciones inmediatas para detenerlos y bloquear aquellos que supongan una amenaza mediante la **cuarentena de administrador**. De este modo, podrá proteger los archivos en la nube, solucionar los problemas y evitar que se produzcan vulneraciones en el futuro.

> [!div class="checklist"]
>
> * Funcionamiento de la cuarentena
> * Configuración de la cuarentena de administrador

## <a name="understand-how-quarantine-works"></a>Funcionamiento de la cuarentena

>[!NOTE]
>
> * Para obtener una lista de las aplicaciones que admiten la cuarentena del administrador, vea la lista de [acciones de gobernanza](governance-actions.md).
> * Si se detecta que un archivo en SharePoint o OneDrive es malware, no se pone en cuarentena en el portal de Cloud App Security.
> * Los archivos con etiquetas no se pueden poner en cuarentena.

1. Cuando un archivo coincida con una directiva, la opción de **cuarentena de administrador** estará disponible para el archivo.

2. Realice una de las acciones siguientes para poner en cuarentena el archivo:

    * Aplique manualmente la acción de **cuarentena de administrador**:

    ![acción de cuarentena](media/quarantine-action.png)

    * Establézcala como una acción de cuarentena automatizada en la directiva:

    ![poner en cuarentena automáticamente](media/quarantine-automated.png)

3. Cuando se aplica la **cuarentena de administrador**, ocurre lo siguiente en segundo plano:

    1. El archivo original se mueve a la carpeta de cuarentena de administrador que haya establecido.
    2. Se elimina el archivo original.
    3. Se carga un archivo de marcador de exclusión en la ubicación original del archivo.

    ![marcador de exclusión de cuarentena](media/quarantine-tombstone.png)

    4. El usuario solo puede acceder al archivo de marcador de exclusión. En él, puede leer las instrucciones personalizadas que ha proporcionado el departamento de TI y el identificador de correlación que tiene que darle al profesional de TI para liberar el archivo.

4. Cuando aparezca la alerta que indica que un archivo se ha puesto en cuarentena, investigue el archivo en la página **Alertas** de Cloud App Security:

    ![alertas de cuarentena](media/quarantine-alerts.png)

5. También en el **Informe de la directiva** en la pestaña **En cuarentena**:

    ![informe de cuarentena](media/quarantine-report.png)

6. Una vez que un archivo se ha puesto en cuarentena, siga el proceso siguiente para corregir la situación de amenaza:

    1. Inspeccione el archivo en la carpeta en cuarentena en SharePoint Online.
    2. También puede consultar los registros de auditoría para profundizar en las propiedades del archivo.
    3. Si encuentra que el archivo va en contra de la directiva corporativa, ejecute el proceso de respuesta a incidentes (IR) de la organización.
    4. Si descubre que el archivo es inofensivo, puede restaurarlo de la cuarentena. En ese momento se libera el archivo original, lo que significa que se vuelve a copiar en la ubicación original, se elimina el marcador de exclusión y el usuario puede acceder a él.

      ![restauración de la cuarentena](media/quarantine-restore.png)

7. Compruebe que la directiva se ejecuta sin problemas. Después, puede usar las acciones de gobernanza automáticas de la directiva para evitar más fugas y aplicar automáticamente una cuarentena de administrador cuando se produzca una coincidencia con la directiva.

> [!NOTE]
> Al restaurar un archivo:
>
> * No se restauran los recursos compartidos originales y se aplica la herencia de carpetas predeterminada.
> * El archivo restaurado solo contiene la versión más reciente.
> * La administración del acceso al sitio de la carpeta de cuarentena es responsabilidad del cliente.

## <a name="set-up-admin-quarantine"></a>Configuración de la cuarentena de administrador

1. Establezca directivas de archivo que detecten las vulneraciones. Entre los ejemplos de estos tipos de directivas se incluyen los siguientes:

    - Una directiva de solo metadatos, como una etiqueta de clasificación en SharePoint Online.
    - Una directiva DLP nativa, como una directiva que busca números de tarjetas de crédito.
    - Una directiva ICAP de terceros, como una directiva que busca Vontu.

2. Establezca una ubicación de cuarentena:
   1. En Office 365 SharePoint o OneDrive para la Empresa, no puede colocar archivos en la cuarentena de administrador como parte de una directiva hasta que la configure: ![advertencia de cuarentena](media/quarantine-warning.png).

      Para establecer la configuración de la cuarentena de administrador, en el engranaje de configuración, vaya a **Configuración**. Proporcione la ubicación de los archivos en cuarentena y la notificación que recibirá el usuario cuando su archivo se ponga en cuarentena.
      ![configuración de cuarentena](media/quarantine-settings.png)

   2. En el caso de Box, no se pueden personalizar la ubicación de la carpeta de cuarentena ni el mensaje de usuario. La ubicación de la carpeta es la unidad del administrador que ha conectado Box con Cloud App Security y el mensaje de usuario es el siguiente: "Este archivo se puso en cuarentena en la unidad del administrador porque es posible que infrinja las directivas de cumplimiento y de seguridad de la empresa. Póngase en contacto con el administrador de TI para obtener ayuda.

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Actividades diarias para proteger el entorno de nube](daily-activities-to-protect-your-cloud-environment.md)

[!INCLUDE [Open support ticket](includes/support.md)]
