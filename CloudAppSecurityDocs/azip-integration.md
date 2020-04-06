---
title: Integrar Azure Information Protection con Cloud App Security
description: En este artículo se proporciona información sobre cómo aprovechar las etiquetas de Azure Information Protection en Cloud App Security para el control adicional del uso de aplicaciones en la nube de su organización.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 12/09/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: b32007479ece2828cc13376f88188bfdc08ade7c
ms.sourcegitcommit: 288c279a0d2dd62a8ad8d7425c3e9e98857bf5f4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/05/2020
ms.locfileid: "80666464"
---
# <a name="azure-information-protection-integration"></a>Integración de Azure Information Protection

*Se aplica a: Microsoft Cloud App Security*

Microsoft Cloud App Security le permite aplicar etiquetas de clasificación de Azure Information Protection de forma automática, con o sin protección, a los archivos como una acción de gobierno de directiva de archivo. También puede investigar archivos filtrando la etiqueta de clasificación aplicada en el portal de Cloud App Security. El uso de las clasificaciones permite mayor visibilidad y control de los datos confidenciales en la nube. Integrar Azure Information Protection con Cloud App Security es tan sencillo como seleccionar una sola casilla.

> [!NOTE]
> Este artículo también es pertinente para las etiquetas de confidencialidad unificadas de Office 365 si ya ha [migrado las etiquetas de clasificación para el centro de seguridad y cumplimiento de office 365](https://docs.microsoft.com/azure/information-protection/configure-policy-migrate-labels). Si no migró las etiquetas de clasificación existentes y comienza a crear nuevas etiquetas en el centro de seguridad y cumplimiento de Office 365, Cloud App Security solo usará las etiquetas preexistentes configuradas en el portal de Azure Information Protection.

Al integrar Azure Information Protection en Cloud App Security, puede usar toda la capacidad de los servicios y proteger los archivos en la nube, entre los que se incluyen:

- La capacidad de aplicar etiquetas de clasificación como una acción de gobierno a los archivos que coinciden con directivas específicas
- La capacidad de ver todos los archivos clasificados en una ubicación central
- La capacidad de investigar según el nivel de clasificación y cuantificar la exposición de datos confidenciales a través de las aplicaciones en la nube.
- La capacidad de crear directivas para asegurarse de que los archivos clasificados se controlan correctamente.

> [!NOTE]
> Para habilitar esta característica, necesita una licencia de Cloud App Security y una licencia para Azure Information Protection Premium P1. En cuanto se hayan implementado ambas licencias, Cloud App Security sincronizará las etiquetas de las organizaciones del servicio Azure Information Protection.

## <a name="prerequisites"></a>Requisitos previos

- Para trabajar con la integración de Azure Information Protection, debe habilitar el [conector de aplicaciones para Office 365](connect-office-365-to-microsoft-cloud-app-security.md).

Para usar etiquetas en Cloud App Security, las etiquetas se deben publicar como parte de la Directiva. Si está utilizando Azure Information Protection, las etiquetas deben publicarse a través del portal de Azure Information Protection. Si migró a etiquetas unificadas, las etiquetas deben publicarse a través del centro de seguridad y cumplimiento de Office 365.

Actualmente, Cloud App Security admite aplicar etiquetas de clasificación de Azure Information Protection para los siguientes tipos de archivo:

- Word: docm, docx, dotm, dotx
- Excel: XLAM, xlsm, xlsx, xltx
- PowerPoint: potm, potx, ppsx, ppsm, pptm, pptx
- PDF
  > [!NOTE]
  > En el caso de PDF, debe usar etiquetas unificadas.

Esta característica está disponible actualmente para los archivos almacenados en Box, G Suite, SharePoint Online y OneDrive para la empresa. En futuras versiones se admitirán más aplicaciones en la nube.

Cloud App Security no pueden cambiar los archivos etiquetados con protección fuera de Cloud App Security. Sin embargo, puede examinar estos archivos concediendo permisos para [inspeccionar el contenido de los archivos protegidos](content-inspection.md#content-inspection-for-protected-files).

## <a name="how-it-works"></a>Cómo funciona

Probablemente esté familiarizado con las etiquetas de clasificación de archivos en [Azure Information Protection](https://docs.microsoft.com/azure/information-protection/what-is-information-protection). Puede ver las etiquetas de clasificación de Azure Information Protection en Cloud App Security. Tan pronto como integre Cloud App Security con Azure Information Protection, Cloud App Security examina los archivos como se indica a continuación:

1. Cloud App Security recupera la lista de todas las etiquetas de clasificación usadas en el inquilino. Esta acción se realiza cada hora para mantener actualizada la lista.

2. A continuación, Cloud App Security examina los archivos en busca de etiquetas de clasificación, como se indica a continuación:

    - Si ha habilitado el examen automático, todos los archivos nuevos o modificados se agregan a la cola de examen y se examinan todos los archivos y repositorios existentes.
    - Si establece una directiva de archivo para buscar etiquetas de clasificación, estos archivos se agregan a la cola de examen para las etiquetas de clasificación.

3. Como se indicó anteriormente, estos análisis son para las etiquetas de clasificación detectadas en el examen inicial Cloud App Security permite ver qué etiquetas de clasificación se usan en el inquilino. Las etiquetas externas, las etiquetas de clasificación establecidas por una persona externa a su inquilino, se agregan a la lista de etiquetas de clasificación. Si no desea que se busquen, active la casilla **examinar solo archivos para las etiquetas de clasificación de Azure Information Protection de este inquilino** .

4. Después de habilitar Azure Information Protection en Cloud App Security, todos los archivos nuevos que se agreguen a las aplicaciones conectadas en la nube se examinarán en busca de etiquetas de clasificación.

5. Puede crear nuevas directivas en Cloud App Security que apliquen automáticamente las etiquetas de clasificación.

## <a name="how-to-integrate-azure-information-protection-with-cloud-app-security"></a>Cómo integrar Azure Information Protection con Cloud App Security
  
### <a name="enable-azure-information-protection"></a>Habilitar Azure Information Protection

Todo lo que tiene que hacer para integrar Azure Information Protection con Cloud App Security es hacer clic en una sola casilla. Al habilitar el examen automático, se habilita la búsqueda de Azure Information Protection etiquetas de clasificación en los archivos de Office 365 sin necesidad de crear una directiva. Después de habilitarlo, si tiene archivos en el entorno de nube etiquetados con Azure Information Protection etiquetas de clasificación, los verá en Cloud App Security.

Para habilitar Cloud App Security para examinar archivos con la inspección de contenido habilitada para etiquetas de clasificación:

1. En Cloud App Security, en el engranaje de configuración, seleccione la página **configuración** en el encabezado **del sistema** .

    ![Menú de configuración](media/azip-system-settings.png)
1. En **Azure Information Protection**, seleccione **analizar automáticamente los archivos para las etiquetas de clasificación de Azure Information Protection**.

    ![habilitación de Azure Information Protection](media/enable-azip.png)

Después de habilitar Azure Information Protection, podrá ver los archivos que tienen etiquetas de clasificación y filtrarlos por etiqueta en Cloud App Security. Una vez que Cloud App Security esté conectado a la aplicación en la nube, podrá usar las características de integración de Azure Information Protection para aplicar etiquetas de clasificación de Azure Information Protection (con o sin protección) en el portal de Cloud App Security, agregándolas directamente a los archivos o configurando una directiva de archivo para aplicar etiquetas de clasificación automáticamente como una acción de gobierno.

> [!NOTE]
> El examen automático no examina los archivos existentes hasta que se vuelvan a modificar. Para examinar los archivos existentes para las etiquetas de clasificación de Azure Information Protection, debe tener al menos una **Directiva de archivo** que incluya la inspección de contenido. Si no tiene ninguna, cree una nueva **Directiva de archivo**, elimine todos los filtros preestablecidos, en **método de inspección** seleccione **DLP integrado**. En el campo **inspección de contenido** , seleccione **incluir archivos que coincidan con una expresión preestablecida** y seleccione cualquier valor predefinido y guarde la Directiva. Esto habilita la inspección de contenido, que detecta automáticamente Azure Information Protection etiquetas de clasificación.

#### <a name="set-internal-and-external-tags"></a>Establecer etiquetas internas y externas

De forma predeterminada, Cloud App Security examina las etiquetas de clasificación que se definieron en la organización, así como las externas definidas por otras organizaciones. 

Para omitir las etiquetas de clasificación establecidas externamente en la organización, en el portal de Cloud App Security, vaya a **configuración** y **Azure Information Protection**. Seleccione **solo archivos de análisis para las etiquetas de clasificación de Azure Information Protection y las advertencias de inspección de contenido de este inquilino**.

![omitir etiquetas](media/azip-ignore.png)

### <a name="apply-labels-directly-to-files"></a>Aplicar etiquetas directamente a los archivos

1. En la página **archivos** , en **investigar**, seleccione el archivo que desea proteger. Haga clic en los tres puntos al final de la fila del archivo y, a continuación, elija **Aplicar etiqueta de clasificación**.  

    ![proteger aplicación](media/protect-app.png)
  
    >[!NOTE]
    > Cloud App Security puede aplicar Azure Information Protection en archivos de hasta 50 MB.

2. Se le pedirá que elija una de las etiquetas de clasificación de su organización para aplicarla al archivo y haga clic en **aplicar**.

    ![etiqueta de clasificación de protección](media/protect-template.png)

3. Después de elegir una etiqueta de clasificación y hacer clic en aplicar, Cloud App Security aplicará la etiqueta de clasificación al archivo original.

4. También puede quitar las etiquetas de clasificación si elige la opción **quitar etiqueta de clasificación** .

> [!NOTE]
> Solo puede quitar etiquetas si no incluyen protección y se aplicaron desde dentro de Cloud App Security, no etiquetas aplicadas directamente en Information Protection.

Para obtener más información sobre cómo funcionan conjuntamente Cloud App Security y Azure Information Protection, consulte protección de los [datos frente a errores](https://docs.microsoft.com/enterprise-mobility-security/solutions/protect-data-user-mistake)de los usuarios.

### <a name="automatically-label-files"></a>Etiquetar archivos automáticamente

Puede aplicar automáticamente etiquetas de clasificación a los archivos mediante la creación de una directiva de archivo y la configuración de **Aplicar etiqueta de clasificación** como acción de gobierno.

Siga estas instrucciones para crear la Directiva de archivo:

1. Cree una directiva de archivo.
2. Establezca la Directiva para incluir el tipo de archivo que desea detectar. Por ejemplo, seleccione todos los archivos en los que el **nivel de acceso** no sea igual a **interno** y donde la **unidad organizativa propietario** sea igual a su equipo financiero.
3. En acciones de gobierno para la aplicación correspondiente, haga clic en **aplicar una etiqueta de clasificación** y seleccione el tipo de etiqueta.

    ![Aplicar etiqueta](media/aip-gov-action.png)

> [!NOTE]
> La función de aplicar automáticamente una etiqueta de Azure Information Protection mediante la directiva de archivo resulta eficaz. Para impedir que los clientes apliquen por error una etiqueta a un gran número de archivos, existe como medida de seguridad un límite diario de 100 acciones **Aplicar etiqueta** por aplicación e inquilino. Cuando se alcanza el límite diario, la acción Aplicar etiqueta se detiene temporalmente y continúa automáticamente al día siguiente (después de las 12:00 UTC). Para aumentar el límite del inquilino, abra una incidencia de soporte técnico.

### <a name="control-file-exposure"></a>Controlar la exposición de archivos

- Por ejemplo, si a continuación se muestra un documento etiquetado con una etiqueta de clasificación de Azure Information Protection:

    ![pantalla Azure Information Protection de ejemplo](media/azip-screen.png)

- Puede ver este documento en Cloud App Security mediante el filtrado de la etiqueta de clasificación de Azure Information Protection en la página **archivos** .

    ![Cloud App Security comparado con Azure Information Protection](media/cas-compared-azip.png)

- Puede obtener más información sobre estos archivos y sus etiquetas de clasificación en el cajón de archivos. Simplemente haga clic en el archivo correspondiente en la página **archivos** y compruebe si tiene una etiqueta de clasificación.

    ![cajón de archivos](media/azip-file-drawer.png)

- Después, puede crear directivas de archivo en Cloud App Security para controlar los archivos que se comparten de forma inapropiada y buscar los archivos etiquetados y que se han modificado recientemente.

- Puede crear una directiva que aplique automáticamente una etiqueta de clasificación a archivos específicos.
- También puede desencadenar alertas en las actividades relacionadas con la clasificación de archivos.

> [!Note]
> Cuando Azure Information Protection etiquetas están deshabilitadas en un archivo, las etiquetas deshabilitadas aparecen como deshabilitadas en Cloud App Security. No se muestran las etiquetas eliminadas.

**Directiva de ejemplo: datos confidenciales que se comparten externamente en Box:**

1. Cree una directiva de archivo.
2. Establezca el nombre, la gravedad y la categoría de la Directiva.
3. Agregue los siguientes filtros para buscar todos los datos confidenciales que se comparten externamente en Box:

    ![Directiva de confidencialidad](media/azip-confidentiality-policy.png)

**Ejemplo de datos con restricción de directiva que se modificaron recientemente fuera de la carpeta Finance en SharePoint:**

1. Cree una directiva de archivo.
2. Establezca el nombre, la gravedad y la categoría de la Directiva.
3. Agregue los siguientes filtros para buscar todos los archivos restringidos modificados recientemente sin incluir la carpeta Finance en la opción de selección de carpeta:

    ![Directiva de datos restringidos](media/azip-restricted-data-policy.png)

También puede elegir establecer alertas, notificaciones de usuario o realizar una acción inmediata para estas directivas.
Más información sobre [las acciones de gobierno](governance-actions.md).

Obtenga más información acerca de [Azure Information Protection](https://docs.microsoft.com/information-protection/understand-explore/what-is-information-protection) y consulte el [tutorial de inicio rápido](https://docs.microsoft.com/information-protection/get-started/infoprotect-quick-start-tutorial)de Azure Information Protection.

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Controlar las aplicaciones en la nube con directivas](control-cloud-apps-with-policies.md)

## <a name="related-videos"></a>Vídeos relacionados

> [!div class="nextstepaction"]
> [Integraciones de Cloud App Security + Azure Information Protection](https://channel9.msdn.com/Shows/Microsoft-Security/MCAS--AIP-Integrations)  

[!INCLUDE [Open support ticket](includes/support.md)]
