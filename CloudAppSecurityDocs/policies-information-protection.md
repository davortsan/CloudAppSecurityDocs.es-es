---
title: Directivas de protección de la información-Cloud App Security | Microsoft Docs
description: En este tema se describen los pasos para configurar muchas directivas de protección de la información en Cloud App Security.
author: shsagir
ms.author: shsagir
ms.date: 06/13/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: cloud-app-security
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 681a2389b0a1a47013bdec2d4925cf47326330a9
ms.sourcegitcommit: 826d2ec022647bce6c3135c115a41ee894ff8ecd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/16/2020
ms.locfileid: "84800847"
---
# <a name="information-protection-policies"></a>Directivas de protección de la información

*Se aplica a: Microsoft Cloud App Security*

Cloud App Security las directivas de archivo permiten aplicar una amplia gama de procesos automatizados. Las directivas se pueden establecer para proporcionar protección de la información, incluidos los exámenes de cumplimiento continuos, las tareas legales de eDiscovery y DLP para el contenido confidencial compartido públicamente.

Cloud App Security puede supervisar cualquier tipo de archivo en función de más de 20 filtros de metadatos, por ejemplo, el nivel de acceso y el tipo de archivo. Para obtener más información, vea [directivas de archivo](data-protection-policies.md).

## <a name="detect-and-prevent-external-sharing-of-sensitive-data"></a>Detectar e impedir el uso compartido externo de datos confidenciales

Detecte Cuándo los archivos con información de identificación personal u otros datos confidenciales se almacenan en un servicio en la nube y se comparten con usuarios externos a su organización que infringen la Directiva de seguridad de la empresa y crea una posible infracción de cumplimiento.

### <a name="prerequisites"></a>Requisitos previos

Debe tener al menos una aplicación conectada mediante los [conectores de aplicaciones](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md).

### <a name="steps"></a>Pasos

1. En la página **directivas** , cree una nueva **Directiva de archivo**.

2. Establezca el **nivel de acceso** del filtro es es **público (Internet)/público/externo**.

3. En **método de inspección**, seleccione **servicio de clasificación de datos (DC)** y, en **Seleccionar tipo** , seleccione el tipo de información confidencial que quiere que los DC inspeccionen.

4. Configure las acciones de **gobierno** que se realizarán cuando se desencadene una alerta. Por ejemplo, puede crear una acción de gobierno que se ejecute en las infracciones de archivos detectadas en G Suite, en la que puede seleccionar la opción para **quitar usuarios externos** y **quitar el acceso público**.

5. Cree la Directiva de archivo.

## <a name="detect-externally-shared-confidential-data"></a>Detección de datos confidenciales compartidos externamente

Detectar cuándo los archivos con la etiqueta **confidencial** y que se almacenan en un servicio en la nube se comparten con usuarios externos, infringiendo las directivas de la empresa.

### <a name="prerequisites"></a>Requisitos previos

- Debe tener al menos una aplicación conectada mediante los [conectores de aplicaciones](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md).

- Habilitar la [integración de Azure Information Protection](azip-integration.md).

### <a name="steps"></a>Pasos

1. En la página **directivas** , cree una nueva **Directiva de archivo**.

2. Establezca la **etiqueta de clasificación** de filtro en **Azure Information Protection** es igual a la etiqueta **confidencial** o al equivalente de su empresa.

3. Establezca el **nivel de acceso** del filtro es es **público (Internet)/público/externo**.

4. Opcional: establecer las acciones de **gobierno** que se realizarán en los archivos cuando se detecte una infracción. Las acciones de gobierno disponibles varían entre los servicios.

5. Cree la Directiva de archivo.

## <a name="detect-and-encrypt-sensitive-data-at-rest"></a>Detección y cifrado de datos confidenciales en reposo

Detectar archivos que contienen información de identificación personal y otros datos confidenciales que se comparten en una aplicación en la nube y aplicar etiquetas de clasificación para limitar el acceso únicamente a los empleados de la empresa.

### <a name="prerequisites"></a>Requisitos previos

- Debe tener al menos una aplicación conectada mediante los [conectores de aplicaciones](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md).

- Habilitar la [integración de Azure Information Protection](azip-integration.md).

### <a name="steps"></a>Pasos

1. En la página **directivas** , cree una nueva **Directiva de archivo**.

2. En **método de inspección**, seleccione **servicio de clasificación de datos (DC)** y, en **Seleccionar tipo** , seleccione el tipo de información confidencial que quiere que los DC inspeccionen.

3. En **alerta**, Active **aplicar control de etiqueta de clasificación** y seleccione la etiqueta de clasificación que utiliza su empresa para restringir el acceso a los empleados de la empresa.

4. Cree la Directiva de archivo.

> [!NOTE]
> La capacidad de aplicar una etiqueta de clasificación directamente en Cloud App Security solo se admite actualmente para Box, G Suite, SharePoint Online y OneDrive para la empresa.

## <a name="detect-stale-externally-shared-data"></a>Detectar datos compartidos externamente obsoletos

Detectar archivos no usados y obsoletos, archivos que no se actualizaron recientemente, a los que se puede tener acceso públicamente a través de un vínculo público directo, una búsqueda web o a usuarios externos específicos.

### <a name="prerequisites"></a>Requisitos previos

Debe tener al menos una aplicación conectada mediante los [conectores de aplicaciones](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md).

### <a name="steps"></a>Pasos

1. En la página **directivas** , cree una nueva **Directiva de archivo**.

2. Seleccione y aplique la plantilla de directiva **archivos compartidos externamente obsoletos**.

3. Personalice el filtro que se **modificó por última vez** para que coincida con la Directiva de su organización.

4. Opcional: establecer acciones de **gobierno** que se realizarán en los archivos cuando se detecte una infracción. Las acciones de gobierno disponibles varían entre los servicios. Por ejemplo:

    - G Suite: convertir el archivo en privado y notificar al último editor de archivos

    - Box: notificar al último editor de archivos

    - SharePoint Online: convertir el archivo en privado y enviar un resumen de coincidencia de directiva al propietario del archivo

5. Cree la Directiva de archivo.

## <a name="detect-data-access-from-an-unauthorized-location"></a>Detección del acceso a datos desde una ubicación no autorizada

Detectar cuándo se tiene acceso a los archivos desde una ubicación no autorizada, en función de las ubicaciones comunes de la organización, para identificar una posible fuga de datos o acceso malintencionado.

### <a name="prerequisites"></a>Requisitos previos

Debe tener al menos una aplicación conectada mediante los [conectores de aplicaciones](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md).

### <a name="steps"></a>Pasos

1. En la página **directivas** , cree una nueva **Directiva de actividad**.

2. Establezca el **tipo de actividad** de filtro en las actividades de archivos y carpetas que le interesen, como **Ver**, **Descargar**, **obtener acceso**y **modificar**.

3. Establezca la **Ubicación** del filtro no es igual a y, a continuación, especifique los países desde los que la organización espera la actividad.

    1. Opcional: puede usar el enfoque opuesto y establecer el filtro en **Ubicación** es igual a si su organización bloquea el acceso desde determinados países.

4. Opcional: cree acciones de **gobierno** que se aplicarán a la infracción detectada (la disponibilidad varía entre los servicios), como **suspender usuario**.

5. Cree la Directiva de actividad.

## <a name="detect-and-protect-confidential-data-store-in-a-non-compliant-sp-site"></a>Detección y protección del almacén de datos confidencial en un sitio de SP no compatible

Detectar archivos etiquetados como confidenciales y almacenados en un sitio de SharePoint no compatible.

### <a name="prerequisites"></a>Requisitos previos

Azure Information Protection las etiquetas se configuran y se usan dentro de la organización.

### <a name="steps"></a>Pasos

1. En la página **directivas** , cree una nueva **Directiva de archivo**.

2. Establezca la **etiqueta de clasificación** de filtro en **Azure Information Protection** es igual a la etiqueta **confidencial** o al equivalente de su empresa.

3. Establezca la **carpeta principal** del filtro no es igual a y, a continuación, en **seleccionar una carpeta** , elija todas las carpetas compatibles de la organización.

4. En **alertas** , seleccione **crear una alerta para cada archivo coincidente**.

5. Opcional: establecer las acciones de **gobierno** que se realizarán en los archivos cuando se detecte una infracción. Las acciones de gobierno disponibles varían entre los servicios. Por ejemplo, establezca **Box** para **Enviar el Resumen de coincidencia de directiva al propietario del archivo** y **poner en cuarentena de administrador**.

6. Cree la Directiva de archivo.

## <a name="detect-externally-shared-source-code"></a>Detectar código fuente compartido externamente

Detectar si los archivos que contienen contenido que podría ser código fuente se comparten públicamente o se comparten con usuarios ajenos a la organización.

### <a name="prerequisites"></a>Requisitos previos

Debe tener al menos una aplicación conectada mediante los [conectores de aplicaciones](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md).

### <a name="steps"></a>Pasos

1. En la página **directivas** , cree una nueva **Directiva de archivo**.

2. Seleccionar y aplicar la plantilla de directiva **código fuente compartido externamente**

3. Opcional: Personalice la lista de **extensiones** de archivo para que coincidan con las extensiones de archivo de código fuente de su organización.

4. Opcional: establecer las acciones de **gobierno** que se realizarán en los archivos cuando se detecte una infracción. Las acciones de gobierno disponibles varían entre los servicios. Por ejemplo, en Box, **envíe el Resumen de coincidencia de directiva al propietario del archivo** y **colóquelo en cuarentena de administrador**.

5. Seleccionar y aplicar la plantilla de Directiva

## <a name="detect-unauthorized-access-to-group-data"></a>Detectar el acceso no autorizado a los datos de grupo

Detectar si un usuario que no forma parte del grupo tiene un acceso excesivo a determinados archivos que pertenecen a un grupo de usuarios específico, lo que podría ser una posible amenaza de Insider.

### <a name="prerequisites"></a>Requisitos previos

Debe tener al menos una aplicación conectada mediante los [conectores de aplicaciones](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md).

### <a name="steps"></a>Pasos

1. En la página **directivas** , cree una nueva **Directiva de actividad**.

2. En **acción** , seleccione **actividad repetida** y Personalice las **actividades mínimas repetidas** y establezca un **período de tiempo** para cumplir con la Directiva de su organización.

3. Establezca el **tipo de actividad** de filtro en las actividades de archivos y carpetas que le interesen, como **Ver**, **Descargar**, **obtener acceso**y **modificar**.

4. Establezca el valor de filtrar **usuario** en **de grupo** es igual a y, a continuación, seleccione los grupos de usuarios correspondientes.

    > [!NOTE]
    > Los [grupos de usuarios se pueden importar manualmente](user-groups.md) desde las aplicaciones compatibles.

5. Establezca los **archivos y** carpetas de filtro en **archivos o carpetas específicos** y, a continuación, elija los archivos y las carpetas que pertenecen al grupo de usuarios auditados.

6. Establecer las acciones de **gobierno** que se realizarán en los archivos cuando se detecte una infracción. Las acciones de gobierno disponibles varían entre los servicios. Por ejemplo, puede elegir **suspender usuario**.

7. Cree la Directiva de archivo.

## <a name="detect-publicly-accessible-s3-buckets"></a>Detección de cubos S3 de acceso público

Detección y protección frente a posibles fugas de datos desde los cubos de AWS S3.

### <a name="prerequisites"></a>Requisitos previos

Debe tener una instancia de AWS conectada mediante los [conectores de aplicaciones](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md).

### <a name="steps"></a>Pasos

1. En la página **directivas** , cree una nueva **Directiva de archivo**.

2. Seleccione y aplique la plantilla de directiva **cubos S3 de acceso público (AWS)**.

3. Establecer las acciones de **gobierno** que se realizarán en los archivos cuando se detecte una infracción. Las acciones de gobierno disponibles varían entre los servicios. Por ejemplo, establezca AWS para que **sea privado** , lo que haría que los cubos S3 fuera privados.

4. Cree la Directiva de archivo.

## <a name="detect-and-protect-gdpr-related-data-across-file-storage-apps"></a>Detección y protección de datos relacionados con RGPD en aplicaciones de file Storage

Detectar archivos que se comparten en aplicaciones de almacenamiento en la nube y que contienen información de identificación personal y otros datos confidenciales que están enlazados mediante una directiva de cumplimiento de RGPD. A continuación, aplique automáticamente etiquetas de clasificación para limitar el acceso únicamente al personal autorizado.

### <a name="prerequisites"></a>Requisitos previos

- Debe tener al menos una aplicación conectada mediante los [conectores de aplicaciones](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md).

- La [integración de Azure Information Protection](azip-integration.md) está habilitada y la etiqueta RGPD está configurada en AIP.

### <a name="steps"></a>Pasos

1. En la página **directivas** , cree una nueva **Directiva de archivo**.

2. En **método de inspección**, seleccione **servicio de clasificación de datos (DC)** y, en **Seleccionar tipo** , seleccione uno o más tipos de información que cumplan con la compatibilidad con RGPD, por ejemplo: el número de la tarjeta de débito de la UE, el número de licencia de los controladores de la UE, el número de identificación nacional de la UE, el número de pasaporte de la UE

3. Establezca las acciones de **gobierno** que se realizarán en los archivos cuando se detecte una infracción, seleccionando **aplicar regulación de etiqueta de clasificación** para cada aplicación compatible.

4. Crear la Directiva de archivo

> [!NOTE]
> Actualmente, **Aplicar etiqueta de clasificación** solo se admite para Box, G Suite, SharePoint Online y OneDrive para la empresa.

## <a name="block-downloads-for-external-users-in-real-time"></a>Bloquear descargas para usuarios externos en tiempo real

Impedir que los usuarios externos expongan los datos de la empresa, bloqueando las descargas de archivos en tiempo real, utilizando [los controles de sesión](proxy-intro-aad.md)de Cloud App Security.

### <a name="prerequisites"></a>Requisitos previos

- [Implemente el control de aplicaciones de acceso condicional para aplicaciones Azure ad](proxy-deployment-aad.md).

- Asegúrese de que la aplicación es una aplicación basada en SAML que use Azure AD para el inicio de sesión único. Para obtener más información sobre las aplicaciones compatibles, consulte [aplicaciones y clientes compatibles](proxy-intro-aad.md#supported-apps-and-clients).

### <a name="steps"></a>Pasos

1. En la página **directivas** , cree una nueva **Directiva de sesión**.

2. En **tipo de control de sesión**, seleccione **controlar la descarga de archivos (con inspección)**.

3. En **filtros de actividad**, **Seleccione usuario** y establézcalo en **de grupo** es igual a **usuarios externos**.

    >[!NOTE]
    > No es necesario establecer ningún filtro de aplicación para habilitar esta directiva para que se aplique a todas las aplicaciones.

4. Puede usar el **filtro de archivos** para personalizar el tipo de archivo. Esto le ofrece un control más granular sobre el tipo de archivos que controla la Directiva de sesión.

5. En **acciones**, seleccione **bloquear**. Puede seleccionar **personalizar el mensaje de bloqueo** para establecer un mensaje personalizado que se enviará a los usuarios para que comprenda el motivo por el que se bloquea el contenido y cómo puede habilitarlo aplicando la etiqueta de clasificación adecuada.

6. Haga clic en **Crear**.

## <a name="enforce-read-only-mode-for-external-users-in-real-time"></a>Aplicar el modo de solo lectura para usuarios externos en tiempo real

Impedir que los usuarios externos expongan los datos de la empresa, bloqueando las actividades de impresión y copia y pegado en tiempo real, utilizando [los controles de sesión](proxy-intro-aad.md)de Cloud App Security.

### <a name="prerequisites"></a>Requisitos previos

- [Implemente el control de aplicaciones de acceso condicional para aplicaciones Azure ad](proxy-deployment-aad.md).
- Asegúrese de que la aplicación es una aplicación basada en SAML que use Azure AD para el inicio de sesión único. Para obtener más información sobre las aplicaciones compatibles, consulte [aplicaciones y clientes compatibles](proxy-intro-aad.md#supported-apps-and-clients).

### <a name="steps"></a>Pasos

1. En la página **directivas** , cree una nueva **Directiva de sesión**.

2. En **tipo de control de sesión**, seleccione **bloquear actividades**.

3. En el filtro de origen de la **actividad** :

    1. Seleccione **usuario** y establezca **de grupo** en **usuarios externos**.

    2. Seleccione el **tipo de actividad** es igual a **Imprimir** y **cortar/copiar elemento**.

    > [!NOTE]
    > No es necesario establecer ningún filtro de aplicación para habilitar esta directiva para que se aplique a todas las aplicaciones.

4. Opcional: en **método de inspección**, seleccione el tipo de inspección que se va a aplicar y establezca las condiciones necesarias para el análisis de DLP.

5. En **acciones**, seleccione **bloquear**. Puede seleccionar **personalizar el mensaje de bloqueo** para establecer un mensaje personalizado que se enviará a los usuarios para que comprenda el motivo por el que se bloquea el contenido y cómo puede habilitarlo aplicando la etiqueta de clasificación adecuada.

6. Haga clic en **Crear**.

## <a name="block-upload-of-unclassified-documents-in-real-time"></a>Bloquear la carga de documentos sin clasificar en tiempo real

Evite que los usuarios carguen datos no protegidos en la nube mediante el uso de [los controles de sesión](proxy-intro-aad.md)de Cloud App Security.

### <a name="prerequisites"></a>Requisitos previos

- [Implemente el control de aplicaciones de acceso condicional para aplicaciones Azure ad](proxy-deployment-aad.md).

- Asegúrese de que la aplicación es una aplicación basada en SAML que use Azure AD para el inicio de sesión único. Para obtener más información sobre las aplicaciones compatibles, consulte [aplicaciones y clientes compatibles](proxy-intro-aad.md#supported-apps-and-clients).

- Azure Information Protection las etiquetas de clasificación deben configurarse y usarse dentro de la organización.

### <a name="steps"></a>Pasos

1. En la página **directivas** , cree una nueva **Directiva de sesión**.

2. En **tipo de control de sesión**, seleccione **controlar la carga de archivos (con inspección)** o **controlar la descarga de archivos (con inspección)**.

   >[!NOTE]
   > No es necesario establecer ningún filtro para habilitar esta directiva para que se aplique a todos los usuarios y aplicaciones.

3. Seleccione la **etiqueta clasificación** del filtro de archivos no es igual a y, a continuación, seleccione las etiquetas que utiliza la empresa para etiquetar los archivos clasificados.

4. Opcional: en **método de inspección**, seleccione el tipo de inspección que se va a aplicar y establezca las condiciones necesarias para el análisis de DLP.

5. En **acciones**, seleccione **bloquear**. Puede seleccionar **personalizar el mensaje de bloqueo** para establecer un mensaje personalizado que se enviará a los usuarios para que comprenda el motivo por el que se bloquea el contenido y cómo puede habilitarlo aplicando la etiqueta de clasificación adecuada.

6. Haga clic en **Crear**.

> [!NOTE]
> Para obtener la lista de tipos de archivo que Cloud App Security admite actualmente para las etiquetas de clasificación de Azure Information Protection, consulte [Azure Information Protection los requisitos previos de integración](azip-integration.md#prerequisites).

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Actividades diarias para proteger el entorno de nube](daily-activities-to-protect-your-cloud-environment.md)

[!INCLUDE [Open support ticket](includes/support.md)]
