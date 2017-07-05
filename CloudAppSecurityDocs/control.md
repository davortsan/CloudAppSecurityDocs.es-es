---
title: "Cómo usar acciones de gobierno para controlar el uso de las aplicaciones en la nube | Microsoft Docs"
description: "En este artículo se proporciona información sobre las acciones de gobierno que se pueden realizar en Cloud App Security para controlar el uso de aplicaciones en la nube de la organización."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 3/26/2017
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: bc11bbfe-ec6c-458c-8302-8112c383199d
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: b22b51e5d41f525240c0430c31760177bf62ca1f
ms.sourcegitcommit: 2f4474084c7e07ac4853945ab5aa1ea78950675d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/28/2017
---
# <a name="control"></a>Control
Puede aplicar acciones de gobierno a los archivos de los usuarios en el entorno de la nube. Después de haber investigado exhaustivamente y aprendido sobre la nube, puede utilizar las acciones de gobierno para ayudar a proteger la organización.  

## <a name="use-policies-to-assess-risk"></a>Usar directivas para evaluar el riesgo  
Después de echar un vistazo a las alertas abiertas, vaya al centro de directivas para revisar las infracciones de directivas que no han activado alertas.  

-   En el panel de Cloud App Security, haga clic en **Control** y, luego, en **Directivas**.  

-   Seleccione una directiva específica para ver la lista **Infringiendo ahora** de coincidencias de directivas que no han activado alertas.  

-   Haga clic en las infracciones de una en una y decida qué hacer con cada una. Para obtener más información sobre las acciones de gobierno, consulte las imágenes que aparecen a continuación.  

     Si la directiva está establecida para detectar infracciones de cumplimiento normativo y alguien guarda números de tarjetas de crédito en archivos en OneDrive, tendrá una coincidencia en la directiva.  

     ![Coincidencias de PCI](./media/pci-matches.png "Coincidencias de PCI")  

-   Seleccione la coincidencia para ver los archivos reales que han infringido la directiva.  

     ![Coincidencias de contenido de PCI](./media/pci-content-matches.png "Coincidencias de contenido de PCI")  

     Puede seleccionar el propio archivo para obtener información sobre los archivos.  

     Puede hacer clic en **Colaboradores** para ver quién tiene acceso a este archivo.  

     Puede hacer clic en **Coincidencias** para ver los números de tarjeta de crédito reales.  

     ![Coincidencias de contenido de números de tarjetas de crédito](./media/content-matches-ccn.png "Coincidencias de contenido de números de tarjetas de crédito")  

## <a name="apply-governance-actions"></a>Aplicar acciones de gobierno  
Puede aplicar acciones de gobierno desde las directivas, desde las alertas y desde el registro **Archivo**.  

Puede revisar y ver en cualquier momento el estado de todas las acciones de gobierno aplicadas anteriormente si va al icono de engranaje **Configuración** ![icono de configuración](./media/settings-icon.png "icono de configuración") y elije **Registro de gobierno**.  

Para volver a aplicar cualquier acción de gobierno errónea, elija el icono **Reintentar** ![icono de reintento](./media/retry-icon.png "icono de reintento") para aplicarla de nuevo.  

Hay acciones de gobierno distintas según el tipo de directiva, de infracción y de aplicación.  

## <a name="move-from-detection-to-automatic-remediation"></a>Pasar de la detección a la corrección automática  
Después de definir y personalizar los filtros de una directiva, puede seleccionar acciones de gobierno automatizadas que se producirán tras cada infracción de esa directiva.  
Puesto que las acciones correctoras utilizan las API del proveedor de la nube, pueden variar de una aplicación a otra.  

> [!NOTE]  
>  Tenga especial cuidado al establecer las acciones de gobierno, ya que pueden dar lugar a la pérdida irreversible de permisos de acceso a los archivos.  
> Es recomendable restringir los filtros para representar exactamente los archivos en los que quiere actuar por medio de varios campos de búsqueda. Cuanto más restringidos sean los filtros, mejor.  
>   
>  Para obtener orientación, puede utilizar el botón **Editar y obtener vista previa de resultados** de la sección **Filtros**.  

![Editar la directiva de archivo y obtener una vista previa de resultados](./media/file-policy-edit-and-preview-results.png "Editar la directiva de archivo y obtener una vista previa de resultados")  

## <a name="migration"></a>Migración  
Cloud App Security le ayuda a implementar las migraciones, ya que le informa de qué usuarios de la organización usan una determinada aplicación y le ofrece herramientas para supervisar la adopción de aplicaciones nuevas. También puede ayudarle a decidir qué tipos de aplicaciones debe ofrecer en la organización al proporcionarle las herramientas para saber lo que todos los usuarios ya están usando.  

### <a name="migrate-your-users-to-a-new-app"></a>Migrar a los usuarios a una nueva aplicación  
Imagínese esta situación: hace poco adquirió Office 365 y quiere que todos los usuarios de la organización dejen de usar todas las demás aplicaciones de almacenamiento en la nube y empiecen a usar OneDrive. Esto es lo que puede hacer:  

1.   Vaya al **panel de Cloud Discovery** y, en **Categorías**, filtre las aplicaciones por **Almacenamiento en la nube**. Luego ordene los resultados por **Usuarios** o **Direcciones IP** y compruebe qué aplicación es la más popular.  

2.   Puede ver qué usuarios están usando otras aplicaciones. También puede explorar en profundidad esas aplicaciones y notificar a los usuarios que las utilizan que quiere que migren a OneDrive, de la siguiente forma:

    1.  En el **panel de Cloud Discovery**, elija **Dropbox** y luego la ficha **Dirección IP** o **Usuarios**.  

    2.  Elija la flecha ![Icono de flecha](./media/arrow-icon.png "icono de flecha") y seleccione **Exportar**.  

### <a name="find-more-secure-alternatives"></a>Buscar alternativas más seguras  
El catálogo de servicios de Cloud App Security puede ayudarle a encontrar alternativas adecuadas para la organización en sustitución de las aplicaciones de riesgo que los usuarios puedan estar utilizando.  

Imagínese esta situación: está pensando en comprar una herramienta de productividad y no está seguro de si los usuarios la utilizarían.  

1.   Vaya al **panel de Cloud Discovery**.  

2.   En **Categorías**, filtre las aplicaciones por **Productividad**.  

3.   Consulte la **Puntuación** de cada aplicación en uso para ver si es segura y, si no es así, por qué no lo es.  

4.   Si decide que desea comprar una licencia empresarial para toda la organización, quizás desee observar también la columna **Usuarios**. Allí puede ver las aplicaciones más populares entre los usuarios, comprobar si son de confianza y ver las características de seguridad que tienen antes de tomar una decisión.  

## <a name="see-also"></a>Vea también  
Para obtener información sobre cómo usar y configurar directivas para controlar el uso de la aplicación de la nube, consulte [Controlar las aplicaciones en la nube con directivas](control-cloud-apps-with-policies.md).   
Para obtener soporte técnico, visite la página de [soporte técnico asistido de Cloud App Security](http://support.microsoft.com/oas/default.aspx?prid=16031).   
Los clientes Premier también pueden elegir Cloud App Security directamente desde el [Portal Premier](https://premier.microsoft.com/).  
