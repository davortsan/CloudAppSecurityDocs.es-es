---
title: Inspección de contenido de Cloud App Security mediante el servicio de clasificación de datos de Microsoft | Microsoft Docs
description: En este artículo se describe el proceso que Cloud App Security sigue al realizar la inspección de contenido de DLP mediante el servicio de clasificación de datos de Microsoft.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 10/31/2018
ms.topic: conceptual
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: bf25d1e6-e5dc-449f-b50e-1cd4a21b6d3d
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 7bf867e9eff77e51e84a2af9d60abe31efb40e2f
ms.sourcegitcommit: d70e5bf78a1db6d9e277c486638a08a474942edb
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2018
ms.locfileid: "50745653"
---
*Se aplica a: Microsoft Cloud App Security*



# <a name="microsoft-data-classification-services-integration"></a>Integración de los servicios de clasificación de datos de Microsoft

Microsoft Cloud App Security permite usar el servicio de clasificación de datos de Microsoft de forma nativa, para clasificar los archivos de las aplicaciones en la nube. El servicio de clasificación de datos de Microsoft proporciona una experiencia de protección de información unificada en Office 365, Azure Information Protection y Microsoft Cloud App Security. Este servicio de clasificación permite ampliar el trabajo de clasificación de datos a las aplicaciones en la nube de terceros que están protegidas por Microsoft Cloud App Security, aprovechando las decisiones ya adoptadas en un número aún mayor de aplicaciones.

>[!NOTE]
> Esta característica solo está disponible en Estados Unidos y Europa (excepto en Francia) y APAC.


## <a name="enable-content-inspection-with-data-classification-services"></a>Habilitar la inspección de contenido con los servicios de clasificación de datos
Tiene la opción para establecer el **método de inspección** para que use el **servicio de clasificación de datos de Microsoft** sin ninguna configuración adicional necesaria. Esta opción es útil al crear una directiva de prevención de pérdida de datos para los archivos en Microsoft Cloud App Security.


1. En la página [Directiva de archivo](data-protection-policies.md), en **Método de inspección** seleccione **Servicio de clasificación de datos**.
     ![configuración del servicio de clasificación de datos](./media/dcs-enable.png)
2. Seleccione si debe aplicarse la directiva cuando se cumpla **cualquier** criterio o **todos** ellos.
3. En **Elija el tipo de inspección**, seleccione **Tipos de información confidencial**.
 ![configuración del servicio de clasificación de datos](./media/dcs-sensitive-information-type.png)

4. Puede usar los [tipos de información confidencial predeterminados](https://support.office.com/article/what-the-sensitive-information-types-look-for-fd505979-76be-4d9f-b459-abef3fc9e86b) para definir lo que ocurre con los archivos protegidos por Microsoft Cloud App Security. También puede reutilizar cualquiera de los [tipos personalizados de información confidencial de Office 365](https://support.office.com/article/create-a-custom-sensitive-information-type-82c382a5-b6db-44fd-995d-b333b3c7fc30).

5. Si lo desea, puede mostrar los cuatro últimos caracteres de una coincidencia. De manera predeterminada, las coincidencias se enmascaran y se muestran en su contexto, e incluyen los 40 caracteres antes y después de la coincidencia. Si activa esta casilla, se mostrarán los cuatro últimos caracteres de la propia coincidencia.

6. También puede establecer alertas y acciones de gobierno para la directiva. Para obtener más información, consulte [Directivas de archivo](data-protection-policies.md) y [Acciones de gobierno](governance-actions.md).

Configurar estas directivas es una manera sencilla de llevar la eficacia de las capacidades de DLP de Office 365 al resto de las aplicaciones en la nube autorizadas, y de proteger los datos almacenados en ellas con el conjunto de herramientas completo suministrado por Microsoft Cloud App Security: por ejemplo, la capacidad de [aplicar automáticamente las etiquetas de clasificación de Azure Information Protection](azip-integration.md) y la capacidad para controlar permisos de uso compartido.



## <a name="next-steps"></a>Pasos siguientes  
[Controlar las aplicaciones en la nube con directivas](control-cloud-apps-with-policies.md)   

[Los clientes Premier también pueden elegir Cloud App Security directamente desde el Portal Premier.](https://premier.microsoft.com/)  
  