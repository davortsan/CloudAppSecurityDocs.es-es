---
title: "Integración de Azure Information Protection | Documentos de Microsoft"
description: "Este artículo proporciona información sobre cómo sacar provecho de las etiquetas de Azure Information Protection en Cloud App Security para tener un mayor control del uso de aplicaciones de nube de la organización."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 11/03/2016
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: bc11bbfe-ec6c-458c-8302-8112c383199d
ms.reviewer: reutam
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 4ddfce677376f370e332938059e741af613853db
ms.openlocfilehash: 1fda4411d17acf90338263df9df147ed0075881c


---

# <a name="azure-information-protection-integration-private-preview"></a>Integración de Azure Information Protection - **VERSIÓN PRELIMINAR PRIVADA**

Cloud App Security le permite investigar archivos y establecer directivas basadas en etiquetas de archivo de Azure Information Protection, lo que permite mayor visibilidad y control de sus datos confidenciales en la nube. Para habilitar esta opción, establezca una directiva en Cloud App Security para analizar archivos que tengan la inspección de contenido habilitada. Además, como parte de la versión preliminar privada de Cloud App Security, puede desencadenar alertas en las actividades relacionadas con archivos clasificados. La integración de Azure Information Protection le permite:
-   Cuantificar la exposición de información confidencial en sus aplicaciones de nube.
-   Crear directivas y alertas sobre las infracciones de carga de datos clasificados en las aplicaciones de nube conectadas, o bien poner datos en cuarentena o bloquear que se puedan compartir externamente.
-   Investigar trazas de auditoría y corregir archivos que infringen las directivas 

> [!NOTE] De forma predeterminada, los archivos se analizan en busca de etiquetas solo cuando hay una directiva de archivo que los analiza con la inspección de contenido habilitada. Para analizar todos los archivos en busca de etiquetas sin directivas de archivos, habilite el examen automático.

## <a name="terminology-overview"></a>Información general de la terminología:
-   Etiqueta de clasificación de Azure Information Protection: un atributo establecido por los usuarios finales que se agrega a los archivos de la organización, ya sea de forma automática, según una directiva, o de forma manual.
-   Externo: una etiqueta establecida por alguien externo a la organización.
-   Etiqueta de archivo: la presentación de la etiqueta de clasificación en Cloud App Security. Este campo se muestra para cada archivo en la tabla de archivos y puede usarse en filtros.
-   Directiva de archivo: un conjunto de reglas basadas en filtros de archivos que permiten aplicar una amplia gama de procesos automatizados, con lo que se aprovechan las API del proveedor en la nube.

## <a name="license-and-tenant-creation"></a>Creación de licencias y de inquilinos
Para habilitar esta característica necesitará una licencia de Cloud App Security y una licencia para Azure Information Protection Premium P1 o P2. Tan pronto como se activen las licencias, Cloud App Security sincronizará las etiquetas de las organizaciones del servicio Azure Information Protection:

![pantalla de ejemplo de azip](./media/azip-screen.png)

![cas comparado con azip](./media/cas-compared-azip.png)
     
Además, de manera predeterminada, también se buscarán etiquetas de clasificación en los archivos cuyo contenido estén inspeccionado una o varias directivas de archivo.

## <a name="gain-visibility"></a>Ganar visibilidad

Las etiquetas de archivo analizadas para cada archivo están visibles en el cajón de archivo.
En la página **Archivos**, haga clic en el archivo correspondiente para ver si tiene etiquetas de archivo:

![cajón de archivo](./media/azip-file-drawer.png)

Puede hacer clic en las etiquetas para ver más información o la lista completa de etiquetas:
 
![lista de etiquetas](./media/azip-tags-list.png)

Use el filtro **Etiquetas de archivo** para buscar archivos con una etiqueta específica:
 
![filtro etiquetas de archivo](./media/azip-file-tags-filter.png)

O bien, para archivos que se han etiquetado con cualquier etiqueta de archivo:

![todos los filtros de etiquetas de archivo](./media/azip-file-tags-all-filter.png)

## <a name="enable-automatic-scan-coming-soon"></a>Habilitar el examen automático (próximamente)
Para habilitar el examen automático de etiquetas de archivo para los nuevos archivos en Office 365:

1. En Office 365, vaya a la página **Configuración general**.
2. En la configuración de seguridad de Azure, seleccione **Analizar automáticamente los archivos en busca de etiquetas de clasificación de Azure Information Protection**. Una vez se habilite la opción, se examinarán en busca de etiquetas todos los archivos nuevos que se agreguen a Office 365, y no solo aquellos cuyo contenido se examina por una directiva de archivo.

![habilitar azure information protection](./media/enable-azip.png)
 

## <a name="internal-and-external-tags-coming-soon"></a>Etiquetas internas y externas (próximamente)
De forma predeterminada, Cloud App Security examinará las etiquetas de clasificación que se han definido en su organización, así como las externas que han definido otras organizaciones. 

Para ignorarlas, vaya a **Configuración de seguridad de Azure** y seleccione **Ignorar etiquetas de clasificación de Azure Information Protection de otros inquilinos**.
 
![ignorar las etiquetas](./media/azip-ignore.png)

> [!Note]
> Si está trabajando en un inquilino de prueba, probablemente no querrá omitir las etiquetas de clasificación externas para poder probar archivos que haya recibido de otros inquilinos.

![etiquetas de azure information protection en cloud app security](./media/azip-tags-in-cas.png)

## <a name="use-azure-information-protection-tags-to-apply-control"></a>Usar etiquetas de Azure Information Protection para aplicar control
Cree directivas de archivos en Cloud App Security para buscar archivos que se comparten de forma inapropiada y archivos que están etiquetados y se han modificado recientemente. 

**Directiva 1: datos confidenciales que se comparten externamente en Box:**

1.  Cree una directiva de archivo.
2.  Establezca el nombre, la gravedad y la categoría de la directiva.
3.  Agregue los siguientes filtros para buscar todos los datos confidenciales que se comparten externamente en Box:

![directiva de confidencialidad](./media/azip-confidentiality-policy.png) 

**Directiva 2: datos restringidos que se han modificado recientemente fuera de la carpeta Finanzas en SharePoint:**

1.  Cree una directiva de archivo.
2.  Establezca el nombre, la gravedad y la categoría de la directiva.
3.  Agregue los siguientes filtros para buscar todos los datos restringidos que se han modificado recientemente y agregue una exclusión para la carpeta Finanzas en la opción de selección de carpeta: 
 
![directiva de datos restringidos](./media/azip-restricted-data-policy.png) 

También puede establecer alertas, notificaciones al usuario o emprender acciones inmediatas para estas directivas.
Obtenga más información sobre [acciones de gobierno](governance-actions.md).

Obtenga más información sobre [Azure Information Protection](https://docs.microsoft.com/en-us/information-protection/understand-explore/what-is-information-protection) y consulte su [Tutorial de inicio rápido](https://docs.microsoft.com/en-us/information-protection/get-started/infoprotect-quick-start-tutorial).

  

## <a name="see-also"></a>Consulte también  
[Controlar las aplicaciones en la nube con directivas](control-cloud-apps-with-policies.md)   
[Para obtener soporte técnico, visite la página de soporte técnico asistido de Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Los clientes Premier también pueden elegir Cloud App Security directamente desde el Portal Premier.](https://premier.microsoft.com/)  
  
  



<!--HONumber=Nov16_HO2-->


