---
title: Inspección de contenido de Cloud App Security mediante el servicio de clasificación de datos de Microsoft
description: En este artículo se describe el proceso que Cloud App Security sigue al realizar la inspección de contenido de DLP mediante el servicio de clasificación de datos de Microsoft.
ms.date: 06/24/2020
ms.topic: how-to
ms.openlocfilehash: 49eecb4cd91a27ba221f859335ad52b62b77bea8
ms.sourcegitcommit: d87372b47ca98e942c2bf94032a6a61902627d69
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/30/2020
ms.locfileid: "96311798"
---
# <a name="microsoft-data-classification-services-integration"></a>Integración de los servicios de clasificación de datos de Microsoft

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Microsoft Cloud App Security le permite usar el servicio de clasificación de datos de Microsoft de forma nativa para clasificar los archivos de las aplicaciones en la nube. El servicio de clasificación de datos de Microsoft proporciona una experiencia de protección de información unificada en Office 365, Azure Information Protection y Microsoft Cloud App Security. Este servicio de clasificación permite ampliar el trabajo de clasificación de datos a las aplicaciones en la nube de terceros que están protegidas por Microsoft Cloud App Security, aprovechando las decisiones ya adoptadas en un número aún mayor de aplicaciones.

>[!NOTE]
> Esta característica está actualmente disponible en Estados Unidos, Europa, Australia, India, Canadá, Japón y APAC.

## <a name="enable-content-inspection-with-data-classification-services"></a>Habilitar la inspección de contenido con los servicios de clasificación de datos

Tiene la opción para establecer el **método de inspección** para que use el **servicio de clasificación de datos de Microsoft** sin ninguna configuración adicional necesaria. Esta opción es útil al crear una directiva de prevención de pérdida de datos para los archivos en Microsoft Cloud App Security.

1. En la página [Directiva de archivo](data-protection-policies.md) , en método de **inspección**, seleccione servicio de **clasificación de datos**. También puede establecer el **método de inspección** en la página [Directiva de sesión](session-policy-aad.md) con la opción **Descargar archivo de control (con inspección)** seleccionada.

    ![configuración del servicio de clasificación de datos](media/dcs-enable.png)
2. Seleccione si debe aplicarse la directiva cuando se cumpla **cualquier** criterio o **todos** ellos.
3. En **Elija el tipo de inspección**, seleccione **Tipos de información confidencial**.

    ![Elegir tipo de inspección de servicio de clasificación de datos](media/dcs-sensitive-information-type.png)

4. Puede usar los [tipos de información confidencial predeterminados](https://support.office.com/article/what-the-sensitive-information-types-look-for-fd505979-76be-4d9f-b459-abef3fc9e86b) para definir lo que ocurre con los archivos protegidos por Microsoft Cloud App Security. También puede reutilizar cualquiera de los [tipos personalizados de información confidencial de Office 365](https://support.office.com/article/create-a-custom-sensitive-information-type-82c382a5-b6db-44fd-995d-b333b3c7fc30).
    > [!NOTE]
    > Puede configurar la Directiva para usar tipos de clasificación avanzados como [huellas digitales](/microsoft-365/compliance/document-fingerprinting?view=o365-worldwide&preserve-view=true), [coincidencia de datos exacta](/microsoft-365/compliance/create-custom-sensitive-information-types-with-exact-data-match-based-classification)y [clasificadores](/microsoft-365/compliance/classifier-getting-started-with)que se pueden entrenar.

5. Si lo desea, puede mostrar los cuatro últimos caracteres de una coincidencia. De manera predeterminada, las coincidencias se enmascaran y se muestran en su contexto, e incluyen los 40 caracteres antes y después de la coincidencia. Si activa esta casilla, se mostrarán los cuatro últimos caracteres de la propia coincidencia.

6. Al aprovechar las directivas de archivo, también puede establecer alertas y acciones de gobierno para la Directiva. Para obtener más información, consulte [Directivas de archivo](data-protection-policies.md) y [Acciones de gobernanza](governance-actions.md). Al aprovechar las directivas de sesión, también puede supervisar y controlar las acciones en tiempo real cuando un archivo coincide con un tipo de DC. Para obtener más información, vea [Directiva de sesión](session-policy-aad.md).

Configurar estas directivas es una manera sencilla de llevar la eficacia de las capacidades de DLP de Office 365 al resto de las aplicaciones en la nube autorizadas, y de proteger los datos almacenados en ellas con el conjunto de herramientas completo suministrado por Microsoft Cloud App Security: por ejemplo, la capacidad de [aplicar automáticamente las etiquetas de clasificación de Azure Information Protection](azip-integration.md) y la capacidad para controlar permisos de uso compartido.

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Controlar las aplicaciones en la nube con directivas](control-cloud-apps-with-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]
