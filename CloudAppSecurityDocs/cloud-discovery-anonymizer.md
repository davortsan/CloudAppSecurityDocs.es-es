---
title: Anonimización de datos de usuario en Cloud App Security
description: En este artículo se proporciona información sobre cómo proteger la privacidad de los usuarios al anonimizar los nombres de usuario en los datos de Cloud Discovery.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 04/20/2020
ms.topic: how-to
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: ec8e89711fbaea90237bf279633fef134a41eabc
ms.sourcegitcommit: 575f2b2efa9ca4477d7e60271d21e225ef2c38ea
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/22/2020
ms.locfileid: "90881545"
---
# <a name="cloud-discovery-data-anonymization"></a>Anonimización de datos de Cloud Discovery

[!INCLUDE [Banner for top of topics](includes/banner.md)]

La anonimización de datos de Cloud Discovery le permite proteger la privacidad del usuario. Cuando se haya cargado el registro de datos en el portal de Microsoft Cloud App Security, se depura el registro y se reemplaza toda la información de nombres de usuario con nombres de usuario cifrados. De este modo, todas las actividades de la nube se mantienen anónimas. Cuando sea necesario, para una investigación de seguridad específica (por ejemplo, una infracción de seguridad o una actividad sospechosa del usuario), los administradores pueden resolver el nombre de usuario real. Si un administrador tiene un motivo para sospechar de un usuario específico, puede buscar el nombre de usuario cifrado de un nombre de usuario conocido y, después, comenzar la investigación usando el nombre de usuario cifrado. Cada conversión de nombre de usuario se audita en el **registro de gobierno**del portal.

Puntos clave:

- No se almacena ni se muestra ninguna información privada. Solo información cifrada.
- Los datos privados se cifran mediante AES-128 con una clave dedicada por inquilino.
- La resolución de nombres de usuario se realiza ad hoc, por nombre de usuario descifrando un nombre de usuario cifrado determinado.

## <a name="how-data-anonymization-works"></a>Cómo funciona la anonimización de datos

1. Hay tres formas de aplicar la anonimización de datos:

    - Puede configurar los datos para anonimizar desde un archivo de registro específico, mediante la [creación de un nuevo informe de instantáneas](create-snapshot-cloud-discovery-reports.md) y seleccionando **Anonimización de la información privada**.  
    ![Anonimización de datos de instantáneas](media/anonymize-log.png)

    - Puede establecer los datos para anonimizar desde una [carga automatizada para un nuevo origen de datos](configure-automatic-log-upload-for-continuous-reports.md) seleccionando **Anonymize private information** (Anonimizar información privada) al agregar el nuevo origen de datos.  
    ![Anonimización de datos de registro](media/anonymize-autolog.png)

    - Puede establecer el valor predeterminado en Cloud App Security para anonimizar todos los datos de los informes de instantáneas de los archivos de registro cargados y de los informes continuados de recopiladores de registros como se muestra a continuación:

    1. En el engranaje de configuración, seleccione **configuración de Cloud Discovery**.

    2. En la pestaña Anonimización, para anonimizar nombres de usuario de forma predeterminada, seleccione **Anonimizar la información privada de forma predeterminada en los nuevos informes y orígenes de datos**. También puede seleccionar **información de la máquina anonimización de forma predeterminada en el informe "usuarios del punto de conexión de Win10"**.
    3. Haga clic en **Save**(Guardar).

    ![Página de configuración de anonimización](media/anonymizer1.png)

2. Cuando se selecciona la anonimización, Cloud App Security analiza el registro del tráfico y extrae los atributos de datos específicos.
3. Cloud App Security reemplaza el nombre de usuario por un nombre de usuario cifrado.
4. Después, analiza los datos de uso de la nube y genera informes de Cloud Discovery basados en los datos anónimos.

    ![Anonimizar el panel de Cloud Discovery](media/anonymize-dashboard.png)

5. En el caso de una investigación específica, como una investigación de una alerta de uso anómalo, puede resolver el nombre de usuario específico en el portal y proporcionar una justificación empresarial.

    > [!NOTE]
    > Los siguientes pasos también funcionan con los nombres de equipo en la pestaña **máquinas** .

    **Para resolver un nombre de usuario único**

    1. Haga clic en los tres puntos al final de la fila del usuario que desea resolver y seleccione **Deanonymize usuario**.

        ![Tabla de usuario de anonimización](media/anonymize-user-table.png)

    1. En el elemento emergente, escriba la justificación para resolver el nombre de usuario y, a continuación, haga clic en **resolver**. En la fila correspondiente, se muestra el nombre de usuario resuelto.

        > [!NOTE]
        > Esta acción se audita.

        ![Anonimización resolver emergente](media/anonymize-resolve-dialog.png)

    La siguiente manera alternativa de resolver nombres de usuario únicos también puede usarse para buscar el nombre de usuario cifrado de un nombre de usuario conocido.

    1. En el engranaje de configuración, seleccione **configuración de Cloud Discovery**.

    1. En la pestaña **Anonymization** (Anonimización), en **Anonymize and resolve usernames** (Anonimizar y resolver nombres de usuario), escriba una justificación de por qué se realiza la resolución.
    1. En **Enter username to resolve** (Escriba el nombre de usuario para resolver), seleccione **From anonymized** (De anónimo) y escriba el nombre de usuario anónimo, o seleccione **To anonymized** (Para anónimo) y escriba el nombre de usuario original para resolver. Haga clic en **Resolver**.

        ![Resolver elemento emergente de anonimización](media/anonymizer.png)

    **Para resolver varios nombres de usuario**

    1. Active las casillas que aparecen al mantener el mouse sobre los iconos de usuario por los usuarios que desea resolver o, en la esquina superior izquierda, seleccione la casilla **selección masiva** .

        ![Anonimización resolver en masa](media/anonymize-bulk-resolve.png)

    1. Haga clic en **Deanonymize usuario**.
    1. En el elemento emergente, escriba la justificación para resolver el nombre de usuario y, a continuación, haga clic en **resolver**. En las filas correspondientes, se muestran los nombres de usuario resueltos.

        > [!NOTE]
        > Esta acción se audita.

        ![Anonimización resolver emergente](media/anonymize-resolve-dialog.png)

6. La acción se audita en el **registro de gobierno**del portal.

    ![Acción anonimización en el registro de gobierno](media/anonymize-gov-log.png)

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Controlar las aplicaciones en la nube con directivas](control-cloud-apps-with-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]
