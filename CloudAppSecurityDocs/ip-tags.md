---
title: Establecer etiquetas e intervalos IP | Microsoft Docs
description: "En este tema se proporcionan instrucciones para trabajar con etiquetas IP y categorías IP."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 8/27/2017
ms.topic: get-started-article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: bbf54f66-4ce2-428c-afc8-b5a64277014f
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: edf852bf90a0d4b9345f1beb675ef5ee3c4f941d
ms.sourcegitcommit: c3fda43ef6fe0d15f0eb9ea23a6f245bad8c371b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/27/2017
---
#  <a name="IPtagsandRanges"></a> Trabajar con etiquetas e intervalos IP

Para identificar fácilmente las direcciones IP conocidas, como las direcciones IP de la oficina física, es necesario establecer los intervalos de direcciones IP que permiten etiquetar y clasificar adecuadamente, así como personalizar la forma en que los registros y alertas se muestran e investigan.   
Cada grupo de intervalos IP se puede clasificar en función de una lista predeterminada de categorías IP o etiquetarse con etiquetas IP de creación propia. Además, esta configuración permite invalidar la información de geolocalización pública según su conocimiento de la red interna.  
  
Se admite tanto IPv4 como IPv6.  
  
Cloud App Security está configurado previamente con etiquetas integradas para las siguientes direcciones IP: 
- Cliente nativo
- Sistema operativo obsoleto
- Dispositivos administrados
- Proxy anónimo
- Botnet (cuando una red de robots (botnet) realice una actividad, recibirá un vínculo para obtener más información sobre el botnet específico)
- Tor
- Dispositivo compatible
- Dispositivo comprobado
- Suplantación

Para usar estas etiquetas integradas como parte de una búsqueda, consulte su identificador en la documentación de API de Cloud App Security. 

> [!NOTE]
> Para agregar intervalos de direcciones IP de forma masiva, puede crear un script mediante la [API de intervalos de direcciones IP](https://portal.cloudappsecurity.com/api-docs/).


Las etiquetas de dirección IP integradas y las etiquetas IP personalizadas se consideran de forma jerárquica, y las etiquetas IP personalizadas tienen prioridad sobre las etiquetas IP integradas. Por ejemplo, si una dirección IP se etiqueta como **De riesgo** en función de la información disponible sobre las amenazas pero hay una etiqueta IP personalizada que la identifica como **Corporativa**, la categoría y las etiquetas personalizadas tendrán prioridad.

En la barra de menús, haga clic en el icono de configuración ![icono de configuración](./media/settings-icon.png "icono de configuración") y seleccione **Intervalos de direcciones IP**. Haga clic en **+Agregar intervalo de direcciones IP** y configure lo siguiente:  
  
> [!NOTE]  
>  La ubicación y el ISP registrado invalidarán los valores predeterminados.   
> Las etiquetas IP, por contra, se agregan a la actividad sin invalidar datos.  
  
1.  Dé un **nombre** al intervalo IP. El nombre no aparecerá en el registro de actividades, sino que solo se usará para administrar el intervalo IP.  
  
     Para incluir el intervalo IP en una categoría IP, seleccione una categoría del menú desplegable.  
  
2.  Escriba el **intervalo de direcciones IP** que quiera configurar y, después, haga clic en el botón "+". Puede agregar cuantas direcciones IP y subredes quiera mediante la notación de prefijos de red (también conocida como notación CIDR), por ejemplo, 192.168.1.0/32.  
  
3.  Escriba un nuevo valor para **invalidar los campos de ubicación** u organización (ISP) de estas direcciones. Por ejemplo, si tiene una dirección IP que se considera públicamente como perteneciente a Irlanda, pero sabe que está en Estados Unidos, puede invalidar esta configuración.  
  
4.  Escriba un **ISP registrado**. Esto invalidará los datos de sus actividades.  
  
5.  Especifique una etiqueta para **etiquetar** las actividades de estas direcciones IP. La etiqueta se creará si escribe una palabra en el cuadro. Con la etiqueta ya configurada, puede agregarla a más intervalos IP seleccionándola de la lista. Puede agregar tantas etiquetas IP como quiera para cada intervalo. Las etiquetas IP se pueden usar al crear directivas.  Además de configurar las etiquetas IP, Cloud App Security tiene etiquetas integradas que no son configurables. Puede ver la lista de etiquetas en el [Filtro de etiquetas IP](activity-filters.md).  
  
6.  Las **categorías IP** sirven para reconocer fácilmente las actividades de las direcciones IP interesantes. Las categorías están disponibles en el portal, pero requieren una configuración de usuario para saber qué direcciones IP están incluidas en cada categoría, excepto la categoría de "De riesgo", que incluye dos etiquetas IP: proxy anónimo y Tor.  
  
     Las siguientes categorías IP están disponibles:  
  
    -   **Administrativo**: deben ser todas las direcciones IP de los administradores.  
  
    -   **Interno**: deben ser todas las direcciones IP de la red interna, las sucursales y las direcciones de itinerancia de Wi-Fi.  
  
    -   **De riesgo**: deben ser todas las direcciones IP que se consideran que entrañan riesgos. Puede englobar direcciones IP sospechosas detectadas en el pasado, direcciones IP en las redes de la competencia, etc.  
  
    -   **VPN**: deben ser las direcciones IP que se usan en los trabajos remotos.  
  
    -   **Proxy en la nube**: debe ser la dirección IP del proxy en la nube.  
  
7.  Haga clic en **Crear** cuando acabe.  
  
     ![nuevo intervalo de direcciones IP](./media/newipaddress-range.png "nuevo intervalo de direcciones IP")  
  
  
    
## <a name="see-also"></a>Consulte también  
[Configurar Cloud Discovery](set-up-cloud-discovery.md)   
[Para obtener soporte técnico, visite la página de soporte técnico asistido de Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Los clientes Premier también pueden elegir Cloud App Security directamente desde el Portal Premier.](https://premier.microsoft.com/)  
  
  