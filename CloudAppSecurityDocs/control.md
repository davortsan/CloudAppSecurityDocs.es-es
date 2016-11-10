---
title: Control | Microsoft Docs
description: "En este artículo se proporciona información sobre las acciones de gobierno que se pueden realizar en Cloud App Security para controlar el uso de aplicaciones en la nube de la organización."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 10/15/2016
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: bc11bbfe-ec6c-458c-8302-8112c383199d
ms.reviewer: reutam
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: ed4ea71b24767d3602d40894d1cbac7447bcd8a2
ms.openlocfilehash: 9dc74c35f32c9a3dff251d6e0ac6b35a3591f4b9


---

# <a name="control"></a>Control
Las acciones de gobierno se pueden aplicar a los archivos de los usuarios en el entorno de nube. Después de haber investigado exhaustivamente y aprendido sobre la nube, puede usar las acciones de gobierno para proteger la organización.  
  
## <a name="applying-governance-actions"></a>Aplicar acciones de gobierno  
Las acciones de gobierno se pueden aplicar desde las directivas, desde las alertas y desde el registro **Archivo**.  
  
Puede revisar y ver en cualquier momento el estado de todas las acciones de gobierno aplicadas anteriormente si va al icono de engranaje **Configuración** ![icono de configuración](./media/settings-icon.png "settings icon") y hace clic en **Registro de gobierno**.  
  
En el caso de las acciones de gobierno erróneas, haga clic en el icono de reintento ![icono de reintento](./media/retry-icon.png "retry icon") para volver a aplicarlas.  
  
Hay acciones de gobierno distintas según el tipo de directiva, de infracción y de aplicación.  
  
## <a name="moving-from-detection-to-automatic-remediation"></a>Pasar de la detección a la corrección automática  
Después de definir y personalizar los filtros de una directiva, puede seleccionar acciones de gobierno automatizadas que se apliquen tras cada infracción de esa directiva.  
Puesto que las acciones correctoras aprovechan las API del proveedor de nube, pueden variar de una aplicación a otra.  
  
> [!NOTE]  
>  Tenga especial cuidado al definir acciones de gobierno, ya que podrían provocar la pérdida irreversible de permisos de acceso a los archivos.  
> Se recomienda restringir los filtros para representar exactamente los archivos en los que quiere actuar por medio de varios campos de búsqueda. Cuanto más restringidos sean los filtros, mejor.  
>   
>  Para obtener orientación, puede usar el botón **Editar y obtener vista previa de resultados** de la sección Filtros.  
  
![editar la directiva de archivo y obtener una vista previa de resultados](./media/file-policy-edit-and-preview-results.png "file policy edit and preview results")  
  
## <a name="migration"></a>Migración  
Cloud App Security le ayuda a implementar las migraciones, ya que le informa de qué usuarios de la organización usan una determinada aplicación y le ofrece herramientas para supervisar la adopción de aplicaciones nuevas. También puede ayudarle a decidir qué tipos de aplicaciones debe ofrecer en la organización al proporcionarle las herramientas para saber lo que todos los usuarios ya están usando.  
  
### <a name="how-to-migrate-your-users-to-a-new-app"></a>Cómo migrar a los usuarios a una nueva aplicación  
Imagínese esta situación: hace poco adquirió Office 365 y quiere que todos los usuarios de la organización dejen de usar todas las demás aplicaciones de almacenamiento en la nube y empiecen a usar OneDrive. Esto es lo que puede hacer:  
  
-   Vaya al **panel de Cloud Discovery** y, en **Categorías**, filtre las aplicaciones por **Almacenamiento en la nube**. Luego ordene los resultados por **Usuarios** o **Direcciones IP** y compruebe qué aplicación es la más popular.  
  
-   Puede ver qué usuarios están usando otras aplicaciones.  
  
     También puede explorar en profundidad esas aplicaciones y notificar a los usuarios que las usan que quiere que migren a OneDrive, de la siguiente forma:  
  
    1.  En el **panel de Cloud Discovery**, haga clic en Dropbox y luego en la pestaña **Dirección IP** o **Usuarios**.  
  
    2.  Haga clic en la flecha ![icono de flecha](./media/arrow-icon.png "arrow icon") y seleccione **Exportar**.  
  
### <a name="find-more-secure-alternatives"></a>Buscar alternativas más seguras  
El catálogo de servicios de Cloud App Security puede ayudarle a encontrar alternativas adecuadas para la organización en sustitución de las aplicaciones de riesgo que los usuarios puedan estar usando.  
  
Imagínese esta situación: está pensando en comprar una herramienta de productividad y no está seguro de si los usuarios la usarían o no.  
  
-   Vaya al **panel de Cloud Discovery**.  
  
-   En **Categorías**, filtre las aplicaciones por **Productividad**.  
  
-   Consulte la **Puntuación** de cada aplicación en uso para ver si es segura y, si no es así, por qué no lo es.  
  
-   Si decide que quiere comprar una licencia Enterprise para toda la organización, es posible que también quiera mirar la columna **Usuarios** para ver lo que ya es más popular entre los usuarios, si es de confianza y qué características de seguridad tiene antes de tomar la decisión.  
  
## <a name="see-also"></a>Consulte también  
[Controlar las aplicaciones en la nube con directivas](control-cloud-apps-with-policies.md)   
[Para obtener soporte técnico, visite la página de soporte técnico asistido de Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Los clientes Premier también pueden elegir Cloud App Security directamente desde el Portal Premier.](https://premier.microsoft.com/)  
  
  


<!--HONumber=Oct16_HO4-->


