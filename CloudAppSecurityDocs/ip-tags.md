---
title: 'Establecer intervalos IP y etiquetas: Cloud App Security | Microsoft Docs'
description: En este artículo se proporcionan instrucciones para trabajar con etiquetas IP y categorías IP.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 12/16/2018
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: c26c5cea5a366220c5f8fdff030db1240a7e1a73
ms.sourcegitcommit: 9fe879ce7f07933866191724de5f108f43e3f923
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/24/2020
ms.locfileid: "77566932"
---
#  <a name="IPtagsandRanges"></a>Trabajar con etiquetas y intervalos IP

*Se aplica a: Microsoft Cloud App Security*

Para identificar fácilmente las direcciones IP conocidas, como las direcciones IP de la oficina física, debe establecer intervalos de direcciones IP. Los intervalos de direcciones IP permiten etiquetar, clasificar y personalizar la forma en que se muestran e investigan los registros y las alertas. Cada grupo de intervalos IP se puede clasificar en función de una lista preestablecida de categorías IP. También puede crear etiquetas IP personalizadas para los intervalos IP. Además, puede invalidar la información de ubicación geográfica pública según el conocimiento de la red interna. Se admiten tanto IPv4 como IPv6.

Cloud App Security viene preconfigurada con intervalos IP integrados para proveedores de nube populares, como Azure y Office 365. Además, hemos incorporado el etiquetado basado en la inteligencia de amenazas de Microsoft, incluidos el proxy anónimo, Zombi y Tor. Puede ver la lista completa en el menú desplegable de la página intervalos de direcciones IP.

> [!NOTE]
>
> - Para usar estas etiquetas integradas como parte de una búsqueda, consulte su identificador en la documentación de la API de Cloud App Security.
> - Puede Agregar intervalos IP de forma masiva mediante la creación de un script mediante la **API de intervalos de direcciones IP**.
> - No se pueden agregar intervalos IP con direcciones IP superpuestas.
> - Para ver la documentación de la API, en la barra de menús del portal de Cloud App Security, haga clic en el signo de interrogación y en la documentación de la **API**.

Las etiquetas de dirección IP integradas y las etiquetas IP personalizadas se consideran jerárquicamente. Las etiquetas IP personalizadas tienen prioridad sobre las etiquetas IP integradas. Por ejemplo, si una dirección IP se etiqueta como de **riesgo** en función de la información sobre amenazas, pero hay una etiqueta IP personalizada que la identifica como **corporativa**, la categoría y las etiquetas personalizadas tienen prioridad.

>[!NOTE]
> Cuando una dirección IP se etiqueta como corporativo, se refleja en el portal y las direcciones IP se excluyen de la activación de detecciones específicas (por ejemplo, un [viaje imposible](anomaly-detection-policy.md#impossible-travel)) porque estas direcciones IP se consideran de confianza.

## <a name="create-an-ip-address-range"></a>Crear un intervalo de direcciones IP

En la barra de menús, haga clic en el icono de configuración. Seleccione **intervalos de direcciones IP**. Haga clic en el signo más para agregar intervalos de direcciones IP y establezca los campos siguientes:

1. **Asigne un nombre** al intervalo de direcciones IP. El nombre no aparece en el registro de actividades, sino que solo se usa para administrar el intervalo de direcciones IP.

    Para incluir el intervalo IP en una categoría IP, seleccione una categoría en el menú desplegable.

2. Escriba el **intervalo de direcciones IP** que desea configurar y, a continuación, haga clic en el botón "+". Puede agregar todas las direcciones IP y subredes que desee mediante la notación de prefijo de red (también conocida como notación CIDR), por ejemplo 192.168.1.0/32.

3. Las **categorías** se usan para reconocer fácilmente las actividades de las direcciones IP interesantes. Las categorías están disponibles en el portal. Sin embargo, normalmente requieren la configuración de usuario para determinar qué direcciones IP se incluyen en cada categoría. La excepción a esta configuración es la categoría "arriesgada", que incluye dos etiquetas IP: proxy anónimo y Tor.

    Las siguientes categorías IP están disponibles:

    - **Administrativo**: estas direcciones IP deben ser todas las direcciones IP de los administradores.

    - **Proveedor**de la nube: estas direcciones IP deben ser las direcciones IP que usa el proveedor de servicios en la nube.

    - **Corporativo**: estas direcciones IP deben ser todas las direcciones IP de la red interna, las sucursales y las direcciones de itinerancia de Wi-Fi.

    - **Arriesgado**: estas direcciones IP deben ser cualquier dirección IP que considere arriesgado. Pueden incluir direcciones IP sospechosas que haya visto en el pasado, direcciones IP en las redes de los competidores, etc.

    - **VPN**: estas direcciones IP deben ser cualquier dirección IP que se use para los trabajadores remotos.

4. Para **etiquetar** las actividades de estas direcciones IP, escriba una etiqueta. Al escribir una palabra en el cuadro, se crea la etiqueta. Una vez que ya tenga una etiqueta configurada, puede agregarla fácilmente a intervalos IP adicionales seleccionándola en la lista. Puede Agregar tantas etiquetas IP como desee para cada intervalo. Las etiquetas IP se pueden usar al crear directivas.  Junto con las etiquetas IP que configure, Cloud App Security tiene etiquetas integradas que no son configurables. Puede ver la lista de etiquetas en el [filtro de etiquetas IP](activity-filters.md).
    > [!NOTE]
    > - La ubicación y los valores predeterminados de invalidación de ISP registrados.
    > - Las etiquetas IP se agregan a la actividad sin invalidar los datos.

5. Para **invalidar los** campos de ubicación u organización (ISP) para estas direcciones, escriba nuevo valor. Por ejemplo, supongamos que tiene una dirección IP que se considera públicamente en Irlanda. Sin embargo, sabe que la dirección IP se encuentra en Estados Unidos. Invalidará la ubicación de ese intervalo de direcciones IP.

6. Escriba un **ISP registrado**. Esta configuración invalida los datos de las actividades.

7. Cuando haya terminado, haga clic en **crear**.

    ![intervalo nuevo](media/newipaddress-range.png "intervalo nuevo")

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Configurar Cloud Discovery](set-up-cloud-discovery.md)

[!INCLUDE [Open support ticket](includes/support.md)]
