---
title: Inspección de contenido de Cloud App Security mediante el servicio de clasificación de datos de Microsoft
description: En este artículo se describe el proceso que Cloud App Security sigue al realizar la inspección de contenido de DLP mediante el servicio de clasificación de datos de Microsoft.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 7/30/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: bf25d1e6-e5dc-449f-b50e-1cd4a21b6d3d
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: c4e00f152fcb09f2133805157b85b2a930ad3aca
ms.sourcegitcommit: 094bb42a198fe733cfd3aec79d74487672846dfa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/24/2019
ms.locfileid: "74461344"
---
# <a name="microsoft-data-classification-services-integration"></a>Integración de los servicios de clasificación de datos de Microsoft

*Se aplica a: Microsoft Cloud App Security*

Microsoft Cloud App Security le permite usar el servicio de clasificación de datos de Microsoft de forma nativa para clasificar los archivos de las aplicaciones en la nube. El servicio de clasificación de datos de Microsoft proporciona una experiencia de protección de información unificada en Office 365, Azure Information Protection y Microsoft Cloud App Security. Este servicio de clasificación permite ampliar el trabajo de clasificación de datos a las aplicaciones en la nube de terceros que están protegidas por Microsoft Cloud App Security, aprovechando las decisiones ya adoptadas en un número aún mayor de aplicaciones.

>[!NOTE]
> This feature is currently available in the US, Europe (except France), Australia, India, Canada, Japan, and APAC.

## <a name="enable-content-inspection-with-data-classification-services"></a>Habilitar la inspección de contenido con los servicios de clasificación de datos

Tiene la opción para establecer el **método de inspección** para que use el **servicio de clasificación de datos de Microsoft** sin ninguna configuración adicional necesaria. Esta opción es útil al crear una directiva de prevención de pérdida de datos para los archivos en Microsoft Cloud App Security.

1. En la página [Directiva de archivo](data-protection-policies.md), en **Método de inspección** seleccione **Servicio de clasificación de datos**. You can also set the **Inspection method** in the [session policy](session-policy-aad.md) page with **Control file download (with DLP)** selected.
     ![configuración del servicio de clasificación de datos](./media/dcs-enable.png)
2. Seleccione si debe aplicarse la directiva cuando se cumpla **cualquier** criterio o **todos** ellos.
3. En **Elija el tipo de inspección**, seleccione **Tipos de información confidencial**.
 ![configuración del servicio de clasificación de datos](./media/dcs-sensitive-information-type.png)

4. Puede usar los [tipos de información confidencial predeterminados](https://support.office.com/article/what-the-sensitive-information-types-look-for-fd505979-76be-4d9f-b459-abef3fc9e86b) para definir lo que ocurre con los archivos protegidos por Microsoft Cloud App Security. También puede reutilizar cualquiera de los [tipos personalizados de información confidencial de Office 365](https://support.office.com/article/create-a-custom-sensitive-information-type-82c382a5-b6db-44fd-995d-b333b3c7fc30).
    > [!NOTE]
    > You can configure your policy to use advanced classification types such as Fingerprints and Exact Data Match.

5. Si lo desea, puede mostrar los cuatro últimos caracteres de una coincidencia. De manera predeterminada, las coincidencias se enmascaran y se muestran en su contexto, e incluyen los 40 caracteres antes y después de la coincidencia. Si activa esta casilla, se mostrarán los cuatro últimos caracteres de la propia coincidencia.

6. Leveraging file policies, you can also set alerts and governance actions for the policy. Para obtener más información, consulte [Directivas de archivo](data-protection-policies.md) y [Acciones de gobernanza](governance-actions.md). Leveraging session policies, you can also monitor and control actions in real-time when a file matches a DCS type. For more information, see [session policy](session-policy-aad.md).

Configurar estas directivas es una manera sencilla de llevar la eficacia de las capacidades de DLP de Office 365 al resto de las aplicaciones en la nube autorizadas, y de proteger los datos almacenados en ellas con el conjunto de herramientas completo suministrado por Microsoft Cloud App Security: por ejemplo, la capacidad de [aplicar automáticamente las etiquetas de clasificación de Azure Information Protection](azip-integration.md) y la capacidad para controlar permisos de uso compartido.

## <a name="next-steps"></a>Pasos siguientes

[Controlar las aplicaciones en la nube con directivas](control-cloud-apps-with-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]