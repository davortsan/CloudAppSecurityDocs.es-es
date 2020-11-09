---
title: 'Establecer intervalos IP y etiquetas: Cloud App Security'
description: En este artículo se proporcionan instrucciones para trabajar con etiquetas IP y categorías IP.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 11/09/2020
ms.topic: how-to
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 09eff7b997b8c2745d58d4de6db37a549816bae3
ms.sourcegitcommit: 70c31de91753184a2f8d16b4a9f050231a71f3ad
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/09/2020
ms.locfileid: "94383860"
---
# <a name="working-with-ip-ranges-and-tags"></a><a name="IPtagsandRanges"></a> Trabajar con etiquetas y intervalos IP

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Para identificar fácilmente las direcciones IP conocidas, como las direcciones IP de oficina física, deberá establecer los intervalos de direcciones IP. Los intervalos de direcciones IP permiten etiquetar, clasificar y personalizar la forma en que los registros y alertas se muestran e investigan. Cada grupo de intervalos IP se puede clasificar en función de una lista predeterminada de categorías IP. También podrá crear etiquetas IP personalizadas para los intervalos IP. Además, puede invalidar la información de geolocalización pública según su conocimiento de la red interna. Se admiten tanto IPv4 como IPv6.

Cloud App Security está preconfigurado con intervalos IP integrados de proveedores populares de servicios en la nube como Azure y Office 365. También hay etiquetas integradas basadas en la inteligencia sobre amenazas de Microsoft, incluidos proxy anónimos, redes de robots (botnet) y Tor. Puede ver la lista completa en la lista desplegable de la página de intervalos de direcciones IP.

> [!NOTE]
>
> - Para usar estas etiquetas integradas como parte de una búsqueda, consulte su identificador en la documentación de API de Cloud App Security.
> - Puede Agregar intervalos IP de forma masiva mediante la creación de un script mediante la **API de intervalos de direcciones IP**.
> - No se pueden agregar intervalos IP con direcciones IP superpuestas.
> - Para ver la documentación de API, en la barra de menús del portal de Cloud App Security haga clic en el signo de interrogación y después en **Documentación de API**.

Las etiquetas de dirección IP integradas y las etiquetas IP personalizadas se consideran de forma jerárquica. Las etiquetas IP personalizadas tienen prioridad sobre las etiquetas IP integradas. Por ejemplo, si una dirección IP se etiqueta como **De riesgo** en función de la información disponible sobre las amenazas pero hay una etiqueta IP personalizada que la identifica como **Corporativa** , la categoría y las etiquetas personalizadas tendrán prioridad.

>[!NOTE]
> Cuando una dirección IP se etiqueta como corporativo, se refleja en el portal y las direcciones IP se excluyen de la activación de detecciones específicas (por ejemplo, un [viaje imposible](anomaly-detection-policy.md#impossible-travel)) porque estas direcciones IP se consideran de confianza.

## <a name="create-an-ip-address-range"></a>Crear un intervalo de direcciones IP

En la barra de menús, haga clic en el icono de configuración. Seleccione **Intervalo de direcciones IP**. Haga clic en el signo más para agregar intervalos de direcciones IP y configurar los campos siguientes:

1. Dé un **nombre** al intervalo IP. El nombre no se mostrará en el registro de actividades, solo se usará para administrar el intervalo IP.

    Para incluir el intervalo IP en una categoría IP, seleccione una categoría del menú desplegable.

2. Escriba el **intervalo de direcciones IP** que quiera configurar y, después, haga clic en el botón "+". Puede agregar cuantas direcciones IP y subredes quiera mediante la notación de prefijos de red (también conocida como notación CIDR), por ejemplo, 192.168.1.0/32.

3. Las **categorías** sirven para reconocer fácilmente las actividades de las direcciones IP interesantes. Las categorías están disponibles en el portal. Pero normalmente requieren la configuración de usuario para determinar qué direcciones IP están incluidas en cada categoría. La excepción a esta configuración es la categoría "De riesgo", que incluye dos etiquetas IP: proxy anónimo y Tor.

    Las siguientes categorías IP están disponibles:

    - **Administrativo** : estas direcciones IP deben ser todas las direcciones IP de los administradores.

    - **Proveedor de nube** : estas direcciones IP deben ser las direcciones IP usadas por el proveedor de nube.

    - **Corporativo** : estas direcciones IP deben ser todas las direcciones IP públicas de la red interna, las sucursales y las direcciones de itinerancia de Wi-Fi.

    - **De riesgo** : estas direcciones IP deben ser todas las direcciones IP que se consideran que entrañan riesgos. Puede englobar direcciones IP sospechosas detectadas en el pasado, direcciones IP en las redes de la competencia y así sucesivamente.

    - **VPN** : estas direcciones IP deben ser las direcciones IP que se usan en los trabajos remotos.

4. Especifique una etiqueta para **etiquetar** las actividades de estas direcciones IP. La etiqueta se creará si escribe una palabra en el cuadro. Con la etiqueta ya configurada, puede agregarla a más intervalos IP seleccionándola en la lista. Puede agregar tantas etiquetas IP como quiera para cada intervalo. Las etiquetas IP se pueden usar al crear directivas.  Junto con las etiquetas IP que configure, Cloud App Security tiene etiquetas integradas que no son configurables. Puede ver la lista de etiquetas en el [Filtro de etiquetas IP](activity-filters.md).
    > [!NOTE]
    > - La ubicación y el ISP registrado invalidarán los valores predeterminados.
    > - Las etiquetas IP se agregan a la actividad sin invalidar datos.

5. Escriba un nuevo valor para **invalidar los campos de ubicación** u organización (ISP) de estas direcciones. Por ejemplo, supongamos que tiene una dirección IP que se considera públicamente como perteneciente a Irlanda. Pero sabe que la dirección IP se encuentra en Estados Unidos. Invalidará la ubicación de ese intervalo de direcciones IP.

6. Escriba un **ISP registrado**. Esta configuración invalidará los datos de las actividades.

7. Cuando haya terminado, haga clic en **Crear**.

    ![nuevo intervalo de direcciones IP](media/newipaddress-range.png "nuevo intervalo de direcciones IP")

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Configuración de Cloud Discovery](set-up-cloud-discovery.md)

[!INCLUDE [Open support ticket](includes/support.md)]
