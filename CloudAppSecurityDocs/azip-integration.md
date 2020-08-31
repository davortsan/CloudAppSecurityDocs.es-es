---
title: Integración de Azure Information Protection con Cloud App Security
description: Este artículo proporciona información sobre cómo sacar provecho de las etiquetas de Azure Information Protection en Cloud App Security para tener un mayor control del uso de aplicaciones de nube de la organización.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 12/09/2019
ms.topic: how-to
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 0759c218b1125fa6c383e861228f6c6606841072
ms.sourcegitcommit: c174a7ada5c6a14f0fea9870672898c54e5e3b52
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/30/2020
ms.locfileid: "89149625"
---
# <a name="azure-information-protection-integration"></a>Integración de Azure Information Protection

*Se aplica a: Microsoft Cloud App Security*

Microsoft Cloud App Security le permite aplicar etiquetas de clasificación de Azure Information Protection automáticamente, con o sin protección, a los archivos como acción de gobernanza de directiva de archivo. También puede investigar archivos al filtrar la etiqueta de clasificación aplicada en el portal de Cloud App Security. El uso de clasificaciones permite mayor visibilidad y control de la información confidencial en la nube. La integración de Azure Information Protection con Cloud App Security es tan fácil como seleccionar una sola casilla.

> [!NOTE]
> Este artículo también es pertinente para Microsoft 365 etiquetas de confidencialidad unificada si ya ha [migrado las etiquetas de clasificación para el centro de seguridad y cumplimiento de Office 365](/azure/information-protection/configure-policy-migrate-labels). Si no migró las etiquetas de clasificación existentes y comienza a crear nuevas etiquetas en el centro de seguridad y cumplimiento de Office 365, Cloud App Security solo usará las etiquetas preexistentes configuradas en el portal de Azure Information Protection.

Al integrar Azure Information Protection en Cloud App Security, puede aprovechar todas las funciones de ambos servicios y proteger los archivos en la nube, entre lo que se incluye lo siguiente:

- La capacidad de aplicar etiquetas de clasificación como una acción de gobernanza a archivos que coincidan con las directivas.
- La capacidad de ver todos los archivos clasificados en una ubicación central.
- La capacidad de investigar en función del nivel de clasificación y cuantificar la exposición de la información confidencial en las aplicaciones en la nube.
- La capacidad de crear directivas para asegurarse de que los archivos clasificados se controlan correctamente.

> [!NOTE]
> Para habilitar esta característica, necesita una licencia de Cloud App Security y una licencia para Azure Information Protection Premium P1. Tan pronto como se activen las licencias, Cloud App Security sincroniza las etiquetas de las organizaciones del servicio Azure Information Protection.

## <a name="prerequisites"></a>Requisitos previos

- Para trabajar con la integración de Azure Information Protection, debe habilitar el [conector de aplicaciones para Microsoft 365](connect-office-365-to-microsoft-cloud-app-security.md).

Para usar etiquetas en Cloud App Security, las etiquetas se deben publicar como parte de la Directiva. Si está utilizando Azure Information Protection, las etiquetas deben publicarse a través del portal de Azure Information Protection. Si migró a etiquetas unificadas, las etiquetas deben publicarse a través del centro de seguridad y cumplimiento de Office 365.

Actualmente, Cloud App Security permite aplicar etiquetas de clasificación de Azure Information Protection a los siguientes tipos de archivo:

- Word: docm, docx, dotm, dotx
- Excel: xlam, xlsm, xlsx, xltx
- PowerPoint: potm, potx, ppsx, ppsm, pptm, pptx
- PDF
  > [!NOTE]
  > En el caso de PDF, debe usar etiquetas unificadas.

Esta característica está disponible actualmente para los archivos que se almacenan en Box, G Suite, SharePoint Online y OneDrive para la Empresa. Se admitirán más aplicaciones en la nube en futuras versiones.

Cloud App Security no pueden cambiar los archivos etiquetados con protección fuera de Cloud App Security. Sin embargo, puede examinar estos archivos concediendo permisos para [inspeccionar el contenido de los archivos protegidos](content-inspection.md#content-inspection-for-protected-files).

## <a name="how-it-works"></a>Funcionamiento

Probablemente esté familiarizado con las etiquetas de clasificación de archivos de [Azure Information Protection](/azure/information-protection/what-is-information-protection). Puede ver las etiquetas de clasificación de Azure Information Protection en Cloud App Security. Al integrar Cloud App Security con Azure Information Protection, Cloud App Security examina los archivos del modo siguiente:

1. Cloud App Security recupera la lista de todas las etiquetas de clasificación que se hayan usado en su inquilino. Esta acción se realiza cada hora para mantener la lista actualizada.

2. Después, Cloud App Security examina los archivos en busca de etiquetas de clasificación de la manera siguiente:

    - Si ha habilitado el examen automático, todos los archivos nuevos o modificados se agregan a la cola de examen y se examinan todos los archivos y repositorios existentes.
    - Si ha establecido una directiva de archivo para buscar etiquetas de clasificación, estos archivos se agregan a la cola de examen de etiquetas de clasificación.

3. Como se mencionó anteriormente, estos exámenes son para las etiquetas de clasificación detectadas en el examen inicial que Cloud App Security lleva a cabo para ver qué etiquetas de clasificación se usan en el inquilino. Las etiquetas externas, es decir, las etiquetas de clasificación establecidas por una persona externa al inquilino, se agregan a la lista de etiquetas de clasificación. Si no quiere que se examinen, active la casilla **Only scan files for Azure Information Protection classification labels from this tenant** (Examinar solo archivos en busca de etiquetas de clasificación de Azure Information Protection en este inquilino) (consulte la información a continuación).

4. Después de habilitar Azure Information Protection en Cloud App Security, todos los archivos nuevos que se agreguen a las aplicaciones conectadas en la nube se examinarán en busca de etiquetas de clasificación.

5. Puede crear directivas de seguridad de Cloud App Security que apliquen sus etiquetas de clasificación de forma automática.

## <a name="how-to-integrate-azure-information-protection-with-cloud-app-security"></a>Cómo integrar Azure Information Protection con Cloud App Security

### <a name="enable-azure-information-protection"></a>Habilitar Azure Information Protection

Lo único que tiene que hacer para integrar Azure Information Protection con Cloud App Security es activar una casilla. Al habilitar el examen automático, se habilita la búsqueda de Azure Information Protection etiquetas de clasificación en los archivos de Microsoft 365 sin necesidad de crear una directiva. Después de habilitarlo, si tiene archivos en su entorno de nube con etiquetas de clasificación de Azure Information Protection, los verá en Cloud App Security.

Para permitir que Cloud App Security examine archivos que tengan la inspección de contenido habilitada en busca de etiquetas de clasificación:

1. En Cloud App Security, en el engranaje de configuración, seleccione la página **Configuración** en el encabezado **Sistema**.

    ![Menú Configuración](media/azip-system-settings.png)
1. En **Azure Information Protection**, seleccione **Buscar automáticamente las etiquetas de clasificación de Azure Information Protection en los archivos nuevos**.

    ![habilitar azure information protection](media/enable-azip.png)

Después de habilitar Azure Information Protection, podrá ver los archivos que tienen etiquetas de clasificación y filtrarlos por etiqueta en Cloud App Security. Una vez que Cloud App Security esté conectado a la aplicación en la nube, podrá usar las características de integración de Azure Information Protection para aplicar etiquetas de clasificación de Azure Information Protection (con o sin protección) en el portal de Cloud App Security. Para ello, puede agregarlas directamente a los archivos o configurar una directiva de archivo para aplicar de forma automática las etiquetas de clasificación como una acción de gobernanza.

> [!NOTE]
> El examen automático no examina los archivos existentes hasta que se vuelvan a modificar. Para examinar los archivos existentes para las etiquetas de clasificación de Azure Information Protection, debe tener al menos una **Directiva de archivo** que incluya la inspección de contenido. Si no tiene ninguna, cree una nueva **Directiva de archivo**, elimine todos los filtros preestablecidos, en **método de inspección** seleccione **DLP integrado**. En el campo **inspección de contenido** , seleccione **incluir archivos que coincidan con una expresión preestablecida** y seleccione cualquier valor predefinido y guarde la Directiva. Esto habilita la inspección de contenido, que detecta automáticamente etiquetas de clasificación de Azure Information Protection.

#### <a name="set-internal-and-external-tags"></a>Establecer etiquetas internas y externas

De forma predeterminada, Cloud App Security examina las etiquetas de clasificación que se han definido en su organización, así como las externas que han definido otras organizaciones.

Para omitir las etiquetas de clasificación establecidas externas a la organización, en el portal de Cloud App Security, vaya a **Settings** (Configuración) y **Azure Information Protection**. Seleccione **Only scan files for Azure Information Protection classification labels and content inspection warnings from this tenant** (Examinar los archivos solo para detectar las etiquetas de clasificación de Azure Information Protection y las advertencias de inspección de contenido de este inquilino).

![ignorar las etiquetas](media/azip-ignore.png)

### <a name="apply-labels-directly-to-files"></a>Aplicar etiquetas directamente a archivos

1. En la página **Files** (Archivos) en **Investigate** (Investigar), seleccione el archivo que quiere proteger. Haga clic en los tres puntos al final de la fila del archivo y, luego, elija **Apply classification label** (Aplicar etiqueta de clasificación).

    ![protección de la aplicación](media/protect-app.png)

    >[!NOTE]
    > Cloud App Security puede aplicar Azure Information Protection en archivos que tengan un tamaño de hasta 50 MB.

2. Se le pide que elija una de las etiquetas de clasificación de su organización para aplicarla al archivo; haga clic en **Aplicar**.

    ![etiqueta de clasificación de protección](media/protect-template.png)

3. Después de elegir una etiqueta de clasificación y hacer clic en Aplicar, Cloud App Security aplicará la etiqueta de clasificación al archivo original.

4. También puede elegir la opción **Quitar etiqueta de clasificación** para quitar las etiquetas de clasificación.

> [!NOTE]
> Solo puede quitar las etiquetas si no incluyen protección y se aplicaron desde Cloud App Security, no directamente desde Information Protection.

Para obtener más información sobre cómo funcionan conjuntamente Cloud App Security y Azure Information Protection, consulte [aplicar automáticamente etiquetas de clasificación de Azure Information Protection](use-case-information-protection.md).

### <a name="automatically-label-files"></a>Etiquetar archivos automáticamente

Para aplicar de forma automática etiquetas de clasificación a los archivos, cree una directiva de archivo y configure la opción **Aplicar etiqueta de clasificación** como la acción de gobernanza.

Siga estas instrucciones para crear la directiva de archivo:

1. Cree una directiva de archivo.
2. Establezca la directiva para incluir el tipo de archivo que quiere detectar. Por ejemplo, establezca todos los archivos donde **Access level** (Nivel de acceso) no sea igual a **Internal** (Interna) y donde **Owner OU** (UO de propietario) sea igual al equipo financiero.
3. En las acciones de gobernanza de la aplicación correspondiente, vaya a **Apply a classification label** (Aplicar una etiqueta de clasificación) y, luego, seleccione el tipo de etiqueta.

    ![Aplicar etiqueta](media/aip-gov-action.png)

> [!NOTE]
> La posibilidad de aplicar automáticamente una etiqueta de Azure Information Protection mediante la directiva de archivo resulta una funcionalidad eficaz. Para impedir que los clientes apliquen por error una etiqueta a gran cantidad de archivos, como medida de seguridad existe un límite diario de 100 acciones **Aplicar etiqueta** por aplicación y por inquilino. Cuando se alcanza el límite diario, la acción de aplicar etiqueta se detiene temporalmente y continúa automáticamente al día siguiente (después de 12:00 UTC). Para aumentar el límite del inquilino, abra una incidencia de soporte técnico.

### <a name="control-file-exposure"></a>Controlar la exposición del archivo

- Por ejemplo, si el documento siguiente está etiquetado con una etiqueta de clasificación de Azure Information Protection:

    ![Pantalla de ejemplo de Azure Information Protection](media/azip-screen.png)

- Puede ver este documento en Cloud App Security mediante el filtrado por la etiqueta de clasificación de Azure Information Protection en la página **Files** (Archivos).

    ![Comparación de Cloud App Security con Azure Information Protection](media/cas-compared-azip.png)

- Puede obtener más información sobre estos archivos y sus etiquetas de clasificación en el cajón de archivos. Simplemente haga clic en el archivo en cuestión en la página **Files** (Archivos) y compruebe si tiene una etiqueta de clasificación.

    ![cajón de archivo](media/azip-file-drawer.png)

- Después, puede crear directivas de archivos en Cloud App Security para controlar los archivos que se comparten de forma inapropiada y los archivos que están etiquetados y se han modificado recientemente.

- Puede crear una directiva que aplique automáticamente una etiqueta de clasificación a determinados archivos.
- También puede desencadenar alertas en las actividades relacionadas con la clasificación de archivos.

> [!Note]
> Cuando las etiquetas de Azure Information Protection están deshabilitadas en un archivo, las etiquetas deshabilitadas aparecen como deshabilitadas en Cloud App Security. No se muestran las etiquetas eliminadas.

**Directiva de ejemplo: datos confidenciales que se comparten externamente en Box:**

1. Cree una directiva de archivo.
2. Establezca el nombre, la gravedad y la categoría de la Directiva.
3. Agregue los siguientes filtros para buscar todos los datos confidenciales que se comparten externamente en Box:

    ![directiva de confidencialidad](media/azip-confidentiality-policy.png)

**Directiva de ejemplo: datos restringidos que se han modificado recientemente fuera de la carpeta Finanzas en SharePoint:**

1. Cree una directiva de archivo.
2. Establezca el nombre, la gravedad y la categoría de la Directiva.
3. Agregue los siguientes filtros para buscar todos los archivos restringidos que se han modificado recientemente, al tiempo que excluye la carpeta Finanzas en la opción de selección de carpeta:

    ![directiva de datos restringidos](media/azip-restricted-data-policy.png)

También puede establecer alertas, notificaciones al usuario o emprender acciones inmediatas para estas directivas.
Obtenga más información sobre [acciones de gobernanza](governance-actions.md).

Obtenga más información sobre [Azure Information Protection](/information-protection/understand-explore/what-is-information-protection) y consulte su [Tutorial de inicio rápido](/information-protection/get-started/infoprotect-quick-start-tutorial).

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Controlar las aplicaciones en la nube con directivas](control-cloud-apps-with-policies.md)

## <a name="related-videos"></a>Vídeos relacionados

> [!div class="nextstepaction"]
> [Cloud App Security + Azure Information Protection Integrations](https://channel9.msdn.com/Shows/Microsoft-Security/MCAS--AIP-Integrations) (Integraciones de Cloud App Security y Azure Information Protection)

[!INCLUDE [Open support ticket](includes/support.md)]
