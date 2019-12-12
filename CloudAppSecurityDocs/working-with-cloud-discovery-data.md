---
title: 'Uso de datos de Cloud Discovery para detectar comportamientos de riesgo: Cloud App Security | Microsoft Docs'
description: En este tema se proporcionan instrucciones sobre cómo trabajar con datos de Cloud Discovery, lo que incluye trabajar con la puntuación de riesgo de la aplicación.
keywords: ''
author: shsagir
ms.author: shsagir
manager: angrobe
ms.date: 05/06/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 6e58d3a621f6384fcc011aeb293e01472ee082cc
ms.sourcegitcommit: 6eff466c7a6817b14a60d8c3b2c201c7ae4c2e2c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "74721166"
---
# <a name="working-with-discovery-data"></a>Trabajo con datos de detección

*Se aplica a: Microsoft Cloud App Security*

El panel de Cloud Discovery está diseñado para proporcionar más información sobre cómo se usan las aplicaciones en la nube en la organización. Proporciona una visión general de un vistazo sobre los tipos de aplicaciones que se usan, las alertas abiertas y los niveles de riesgo de las aplicaciones de la organización. También muestra quiénes son los usuarios que más usan las aplicaciones y proporciona un mapa de ubicación de la sede central de la aplicación. El panel de Cloud Discovery tiene muchas opciones para filtrar los datos. Con el filtrado se pueden generar vistas específicas en función de lo que más le interese y gráficos fáciles de entender para que se haga una idea general de un vistazo.

![panel de Cloud Discovery](media/cloud-discovery-dashboard.png)

## <a name="review-the-cloud-discovery-dashboard"></a>Revisar el panel de Cloud Discovery

Lo primero que debe hacer para obtener una visión general de sus aplicaciones de Cloud Discovery es ir al panel de Cloud Discovery y revisar esta información:

1. Primero, vea el uso general de aplicaciones en la nube de la organización en la **información general sobre el uso de alto nivel**.

2. Después, profundice un nivel para ver cuáles son las **categorías que más se usan** en la organización para cada uno de los diferentes parámetros de uso. Puede ver qué porcentaje de este uso lo realizan las aplicaciones autorizadas.

3. Profundice todavía más y vea todas las aplicaciones de una categoría específica en la pestaña **Aplicaciones detectadas**.

4. Puede ver los **principales usuarios y las direcciones IP de origen** para identificar los usuarios predominantes de aplicaciones en la nube de la organización.
5. Compruebe cómo se extienden las aplicaciones detectadas según la ubicación geográfica (de acuerdo con su sede central) en el **mapa de la sede central de la aplicación**.

6. Por último, no olvide revisar la puntuación de riesgo de la aplicación detectada en el **App risk overview** (Información general sobre el riesgo de la aplicación). Compruebe el **estado de alertas de detección** para ver cuántas alertas abiertas se deben investigar.

## <a name="exclude-entities"></a>Excluir entidades

Si tiene usuarios del sistema, direcciones IP o máquinas que son ruidosos y no interesantes, o aplicaciones que no son relevantes, es posible que quiera excluir sus datos de los datos de Cloud Discovery que se analizan. Por ejemplo, puede excluir toda la información que se origina en 127.0.0.1 o el host local.

Para crear una exclusión:

1. En el portal, en el icono de configuración, seleccione **Configuración de Cloud Discovery**.
2. Haga clic en la pestaña **Excluir entidades**.
3. Seleccione la pestaña **Usuarios excluidos**, **Direcciones IP excluidas** o **Máquinas excluidas** y haga clic en el botón + para agregar la exclusión.
4. Agregue un alias de usuario, una dirección IP o un nombre de máquina. Se recomienda agregar información sobre por qué se ha realizado la exclusión.

    ![excluir usuario](media/exclude-user.png "excluir usuario")

## <a name="manage-continuous-reports"></a>Administrar informes continuos

Los informes continuos personalizados proporcionan más granularidad al supervisar los datos de registro de Cloud Discovery de la organización. Al crear informes personalizados, es posible filtrar por ubicaciones geográficas concretas, redes y sitios o unidades organizativas. De forma predeterminada, solo aparecen los informes siguientes en el selector de informes de Cloud Discovery:

- El **informe global** consolida toda la información del portal de todos los orígenes de datos incluidos en los registros.  El informe global no incluye datos de Microsoft Defender ATP.

- El **informe específico de origen de datos** muestra únicamente la información de un origen de datos concreto.

Para crear un informe continuo:

1. En el portal, en el icono de configuración, seleccione **Configuración de Cloud Discovery**.

2. Haga clic en la pestaña **Informe continuo**.

3. Haga clic en el botón **Crear informe**.

4. Escriba un nombre de informe.

5. Seleccione los orígenes de datos que quiere incluir (todos u orígenes específicos).

6. Establezca los filtros que quiera sobre los datos. Estos filtros pueden ser **Grupos de usuarios**, **Etiquetas de dirección IP** o **Intervalos de direcciones IP**. Para obtener más información sobre el trabajo con etiquetas de dirección IP e intervalos de direcciones IP, consulte [Organize the data according to your needs](ip-tags.md) (Organizar los datos de acuerdo a las necesidades).

    ![crear informe continuo personalizado](media/create-custom-continuous-report.png)

> [!NOTE]
> Todos los informes personalizados se limitan a un máximo de 1 GB de datos sin comprimir. Si hay más de 1 GB de datos, se exportará el primer GB de datos en el informe.

## <a name="deleting-cloud-discovery-data"></a>Eliminar datos de Cloud Discovery

Hay una serie de razones por las que puede que quiera eliminar los datos de Cloud Discovery. Se recomienda eliminarlos en los casos siguientes:

- Si cargó manualmente archivos de registro y ha pasado mucho tiempo desde que actualizó el sistema con nuevos archivos de registro y no quiere que los datos antiguos afecten a los resultados.

- Cuando se establece una nueva vista de datos personalizada, solo se aplica a los nuevos datos a partir de ese momento. Por eso, es posible que quiera borrar los datos antiguos y luego volver a cargar los archivos de registro para permitir que la vista de datos personalizada tome los eventos de los datos del archivo de registro.

- Si hay muchos usuarios o direcciones IP que hayan vuelto a trabajar recientemente después de estar sin conexión durante algún tiempo, su actividad se identificará como anómala y es posible que obtenga muchas infracciones positivas falsas.

Para eliminar datos de Cloud Discovery:

1. En el portal, en el icono de configuración, seleccione **Configuración de Cloud Discovery**.

2. Haga clic en la pestaña **Eliminar datos**.

    Es importante estar seguro de querer eliminar los datos antes de continuar: esta acción no se puede deshacer y elimina **todos** los datos de Cloud Discovery del sistema.

3. Haga clic en el botón **Eliminar**.

    ![eliminar datos](media/delete-data.png "eliminar datos")

    > [!NOTE]
    >  El proceso de eliminación tarda unos minutos y no es inmediato.

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Actividades diarias para proteger el entorno de nube](daily-activities-to-protect-your-cloud-environment.md)

[!INCLUDE [Open support ticket](includes/support.md)]
