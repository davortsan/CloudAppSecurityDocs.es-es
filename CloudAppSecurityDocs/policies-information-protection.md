---
title: Directivas de protección de información - Cloud App Security | Microsoft Docs
description: En este tema se describe los pasos para configurar muchas de las directivas de protección de información en Cloud App Security.
author: rkarlin
ms.author: rkarlin
ms.date: 06/13/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: cloud-app-security
ms.assetid: 9a616767-4558-46f1-9da8-aa337920ae45
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: e4b07d47ece8da911e7d8a4a1bd210641f590b36
ms.sourcegitcommit: 9f671d5dd5e5da023d598425442d8736546ca183
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/11/2019
ms.locfileid: "66837783"
---
# <a name="information-protection-policies"></a>Directivas de protección de información

*Se aplica a: Microsoft Cloud App Security*

Las directivas de archivo de cloud App Security le permiten aplicar una amplia gama de procesos automatizados. Las directivas se pueden establecer para proporcionar protección de información, incluido el análisis de conformidad, tareas de eDiscovery legales y DLP para contenido confidencial compartido públicamente.

Cloud App Security puede supervisar cualquier tipo de archivo basado en más de 20 filtros de metadatos, por ejemplo, escriba el nivel de acceso y el archivo. Para obtener más información, consulte [directivas de archivos](data-protection-policies.md).

## <a name="detect-and-prevent-external-sharing-of-sensitive-data"></a>Detecte y evite el uso compartido externo de datos confidenciales

Detectar cuándo los archivos con la información de identificación personal u otros datos confidenciales se almacenan en un servicio en la nube y compartirlos con usuarios que son externos a su organización que infringe la directiva de seguridad de su compañía y crea una posible infracción de cumplimiento.

### <a name="prerequisites"></a>Requisitos previos

Debe tener al menos una aplicación conectada mediante [conectores de aplicaciones](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md).
 
### <a name="steps"></a>Pasos

1. En el **directivas** página, cree un nuevo **directiva de archivo**.

2. Establezca el filtro **nivel de acceso** es igual a **público (Internet) / Public / externo**.

3. En **método de inspección**, seleccione **servicio de clasificación de datos (DC)** y en **Seleccione tipo** seleccione el tipo de información confidencial que desee inspeccionar los controladores de dominio.

6. Configurar la **gobierno** acciones que se deben realizar cuando se desencadene una alerta. Por ejemplo, puede crear una acción de gobierno que se ejecuta en las infracciones de archivo detectado en G Suite en el que selecciona la opción de **quitar usuarios externos** y **quitar el acceso público**.

7. Cree la directiva de archivo.

## <a name="detect-externally-shared-confidential-data"></a>Detectar información confidencial compartido externamente

Detectar cuándo los archivos que se etiquetan **confidencial** y se almacenan en una nube de servicio se comparten con usuarios externos, infringiendo las directivas de empresa.

### <a name="prerequisites"></a>Requisitos previos

- Debe tener al menos una aplicación conectada mediante [conectores de aplicaciones](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md).

- Habilitar [integración de Azure Information Protection](azip-integration.md).

### <a name="steps"></a>Pasos

1.  En el **directivas** página, cree un nuevo **directiva de archivo**.

2.  Establezca el filtro **etiqueta de clasificación** a **Azure Information Protection** es igual a la **confidencial** equivalente del etiqueta o su compañía.

3.  Establezca el filtro **nivel de acceso** es igual a **público (Internet) / Public / externo**.

1.  Opcional: Establecer el **gobierno** las acciones realizadas en los archivos cuando se detecta una infracción. Las acciones de gobierno disponibles varían entre los servicios.

5.  Cree la directiva de archivo.

## <a name="detect-and-encrypt-sensitive-data-at-rest"></a>Detectar y cifrar los datos confidenciales en reposo

Detectar archivos que contienen información de identificación personal y otros datos confidenciales que se comparten en una aplicación de nube y aplican etiquetas de clasificación para limitar el acceso únicamente a los empleados de su empresa.

### <a name="prerequisites"></a>Requisitos previos

- Debe tener al menos una aplicación conectada mediante [conectores de aplicaciones](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md).

- Habilitar [integración de Azure Information Protection](azip-integration.md).
 
### <a name="steps"></a>Pasos

1.  En el **directivas** página, cree un nuevo **directiva de archivo**.

2.  En **método de inspección**, seleccione **servicio de clasificación de datos (DC)** y en **Seleccione tipo** seleccione el tipo de información confidencial que desee inspeccionar los controladores de dominio.

5.  En **alerta**, comprobar **aplicar la regulación de la etiqueta de clasificación** y seleccione la etiqueta de clasificación que usa la empresa para restringir el acceso a los empleados de la empresa. 

6.  Cree la directiva de archivo.

> [!NOTE]
> La capacidad de aplicar una etiqueta de clasificación directamente en Cloud App Security está actualmente solo se admite en Box, G Suite, SharePoint online y OneDrive para la empresa.

## <a name="detect-stale-externally-shared-data"></a>Detectar externamente obsoletos de datos compartidos

Detectar archivos obsoletos y no utilizados, los archivos que no se han actualizado recientemente, que son accesibles públicamente a través del vínculo público directo, búsqueda web, o a usuarios externos específicos.

### <a name="prerequisites"></a>Requisitos previos

Debe tener al menos una aplicación conectada mediante [conectores de aplicaciones](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md).

### <a name="steps"></a>Pasos

1.  En el **directivas** página, cree un nuevo **directiva de archivo**.

2.  Seleccionar y aplicar la plantilla de directiva **archivos compartidos externamente obsoletos**.

3.  Personalizar el filtro **modificó por última vez** para que coincida con la directiva de su organización.

4.  Opcional: Establecer **gobierno** las acciones realizadas en los archivos cuando se detecta una infracción. Las acciones de gobierno disponibles varían entre los servicios. Por ejemplo:

    - G Suite: Hacer que el archivo privado y notificar el último editor del archivo

    - Cuadro: Notificar al último editor del archivo

    - SharePoint online: Hacer privado el archivo y enviar un resumen de la coincidencia de directiva al propietario del archivo

6.  Cree la directiva de archivo.

## <a name="detect-data-access-from-an-unauthorized-location"></a>Detectar el acceso a datos desde una ubicación no autorizada

Detectar cuándo se tiene acceso a los archivos desde una ubicación no autorizada, basándose en las ubicaciones comunes de su organización, para identificar una posible pérdida de datos o el acceso malintencionado.

### <a name="prerequisites"></a>Requisitos previos

Debe tener al menos una aplicación conectada mediante [conectores de aplicaciones](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md).
### <a name="steps"></a>Pasos

1. En el **directivas** página, cree un nuevo **directiva de actividad**.

2. Establezca el filtro **tipo de actividad** a las actividades de archivos y carpetas que le interesen, como **vista**, **descargar**, **acceso**y  **Modificar**.

3. Establezca el filtro **ubicación** no igual y, a continuación, escriba los países desde los que su organización espera que la actividad. 

    1.  Opcional: Puede usar el enfoque opuesto y establezca el filtro en **ubicación** es igual que si su organización boquea desde países específicos.

4.  Opcional: Crear **gobierno** acciones que se aplicará a detectan infracción (disponibilidad varía entre servicios), como **suspender usuario**.

6.  Crear la directiva de actividad.

## <a name="detect-and-protect-confidential-data-store-in-a-non-compliant-sp-site"></a>Detecte y proteja el almacén de datos confidenciales en un sitio de SP no compatibles

Detectar archivos que están etiquetados como confidenciales y se almacenan en un sitio de SharePoint que no son compatibles.

### <a name="prerequisites"></a>Requisitos previos

Etiquetas de Azure Information Protection se configuran y se usa dentro de la organización.

### <a name="steps"></a>Pasos

1.  En el **directivas** página, cree un nuevo **directiva de archivo**.

2.  Establezca el filtro **etiqueta de clasificación** a **Azure Information Protection** es igual a la **confidencial** equivalente del etiqueta o su compañía.

3.  Establezca el filtro **carpeta primaria** no es igual y, a continuación, en **seleccionar una carpeta** elija todas las carpetas compatibles de su organización.

6.  En **alertas** seleccione **crear una alerta para cada archivo coincidente**.

7.  Opcional: Establecer el **gobierno** las acciones realizadas en los archivos cuando se detecta una infracción. Las acciones de gobierno disponibles varían entre los servicios. Por ejemplo, establecer **cuadro** a **implícita de coincidencia de directiva de envío para el propietario del archivo** y **poner en cuarentena de administrador**.

8.  Cree la directiva de archivo.

## <a name="detect-externally-shared-source-code"></a>Detectar el código fuente compartido externamente

Detectar cuándo los archivos que contienen el contenido que podría ser el código fuente se comparten públicamente o se comparten con usuarios fuera de su organización.

### <a name="prerequisites"></a>Requisitos previos

Debe tener al menos una aplicación conectada mediante [conectores de aplicaciones](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md).

### <a name="steps"></a>Pasos

1.  En el **directivas** página, cree un nuevo **directiva de archivo**.

2.  Seleccionar y aplicar la plantilla de directiva **comparten externamente de código fuente**

3.  Opcional: Personalizar la lista de archivos **extensiones** para que coincida con las extensiones de archivo de código fuente de su organización.

4. Opcional: Establecer el **gobierno** las acciones realizadas en los archivos cuando se detecta una infracción. Las acciones de gobierno disponibles varían entre los servicios. Por ejemplo, en el cuadro, **implícita de coincidencia de directiva de envío para el propietario del archivo** y **poner en cuarentena de administrador**.

5. Seleccionar y aplicar la plantilla de directiva

## <a name="detect-unauthorized-access-to-group-data"></a>Detectar accesos no autorizados para agrupar los datos

Detectar cuándo un usuario que no forma parte del grupo, lo que sería una posible amenaza interna tiene acceso excesivamente determinados archivos que pertenecen a un grupo de usuarios específico.

### <a name="prerequisites"></a>Requisitos previos

Debe tener al menos una aplicación conectada mediante [conectores de aplicaciones](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md).

### <a name="steps"></a>Pasos

1. En el **directivas** página, cree un nuevo **directiva de actividad**.

2.  En **actuar en** seleccione **actividad repetida** y personalizar la **mínimo actividades repetidas** y establezca un **período de tiempo** para cumplir con su Directiva de la organización.

3.  Establezca el filtro **tipo de actividad** a las actividades de archivos y carpetas que le interesen, como **vista**, **descargar**, **acceso**y  **Modificar**.

4.  Establezca el filtro **usuario** a **del grupo** es igual a y, a continuación, seleccione los grupos de usuarios pertinentes. 

> [!NOTE]
> [Grupos de usuarios se pueden importar manualmente](user-groups.md) desde aplicaciones compatibles.

6.  Establezca el filtro **archivos y carpetas** a **determinados archivos o carpetas** es igual a y, a continuación, elija los archivos y carpetas que pertenecen al grupo de usuarios auditados.

9.  Establecer el **gobierno** las acciones realizadas en los archivos cuando se detecta una infracción. Las acciones de gobierno disponibles varían entre los servicios. Por ejemplo, puede elegir a **suspender usuario**.

11. Cree la directiva de archivo.

## <a name="detect-publicly-accessible-s3-buckets"></a>Detectar públicamente depósitos S3

Detectar y protegerse frente a posibles pérdidas de datos de los depósitos de AWS S3.

### <a name="prerequisites"></a>Requisitos previos

Debe tener una instancia AWS conectada mediante [conectores de aplicaciones](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md).

### <a name="steps"></a>Pasos

1.  En el **directivas** página, cree un nuevo **directiva de archivo**.

2.  Seleccionar y aplicar la plantilla de directiva **depósitos de S3 accesibles públicamente (AWS)** .

3.  Establecer el **gobierno** las acciones realizadas en los archivos cuando se detecta una infracción. Las acciones de gobierno disponibles varían entre los servicios. Por ejemplo, establézcalo AWS **hacer privado** que haría que el S3 depósitos privada.

5.  Cree la directiva de archivo.

## <a name="detect-and-protect-gdpr-related-data-across-file-storage-apps"></a>Detecte y proteja el RGPD relacionados con datos en las aplicaciones de almacenamiento de archivos 

Detectar archivos que se comparten en aplicaciones de almacenamiento en la nube y contienen información de identificación personal y otros datos confidenciales que está enlazados por una directiva de cumplimiento del RGPD. A continuación, aplicar automáticamente etiquetas de clasificación para limitar el acceso únicamente al personal autorizado.

### <a name="prerequisites"></a>Requisitos previos

- Debe tener al menos una aplicación conectada mediante [conectores de aplicaciones](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md).

- [Integración de Azure Information Protection](azip-integration.md) está habilitada y se configura la etiqueta de RGPD en AIP.

### <a name="steps"></a>Pasos

1.  En el **directivas** página, cree un nuevo **directiva de archivo**.

2.  En **método de inspección**, seleccione **servicio de clasificación de datos (DC)** y en **Seleccione tipo** seleccione uno o varios tipos de información que cumplen con el RGPD cumplimiento, por ejemplo: Número de tarjeta de débito de la UE, controladores de la UE licencia número, número de identificación nacional de la UE, número de pasaporte de Europa, EU SSN, SU número de identificación fiscal.

5.  Establecer el **gobierno** las acciones realizadas en los archivos cuando se detecta una infracción, seleccionando **gobierno de la etiqueta de clasificación se aplican** para cada aplicación compatible.

7.  Crear la directiva de archivo

> [!NOTE]
>  Actualmente, **Aplicar etiqueta de clasificación** solo se admite en Box, G Suite, SharePoint online y OneDrive para la empresa.

## <a name="block-downloads-for-external-users-in-real-time"></a>Bloquear las descargas para los usuarios externos en tiempo real

Impedir que los datos de empresa desde la que se va a exfiltrated por los usuarios externos, por bloquear las descargas de archivos en tiempo real, el uso de Cloud App Security [controles de sesión](proxy-intro-aad.md).

### <a name="prerequisites"></a>Requisitos previos

- [Implementar el control de aplicaciones de acceso condicional para aplicaciones de Azure AD](proxy-deployment-aad.md).

- Asegúrese de que la aplicación es un aplicaciones basado en SAML que utiliza Azure AD para inicio de sesión único. Para obtener más información sobre las aplicaciones compatibles, consulte [admite las aplicaciones y los clientes](proxy-intro-aad.md#supported-apps-and-clients).

### <a name="steps"></a>Pasos

1. En el **directivas** página, cree un nuevo **directiva de sesión**.

2. En **Tipo de control de sesión**, seleccione **Controlar la descarga de archivos (con DLP)** .

3. En **filtros de actividad**, seleccione **usuario** y establézcalo en **del grupo** es igual a **usuarios externos**.

   >[!NOTE]
   > No es necesario establecer los filtros de aplicación para habilitar esta directiva se aplique a todas las aplicaciones.

1. Puede usar el **filtro de archivos** para personalizar el tipo de archivo. Esto le ofrece control pormenorizado sobre qué tipo de archivos de los controles de directiva de sesión.

2. En **acciones**, seleccione **bloque**. Puede seleccionar **personalizar el mensaje de bloque** para establecer un mensaje personalizado para enviarse a los usuarios para que comprenden el motivo se bloquea el contenido y cómo puede habilitarlo mediante la aplicación de la etiqueta de clasificación correcta.

3. Haga clic en **Crear**.

  
## <a name="enforce-read-only-mode-for-external-users-in-real-time"></a>Aplicar el modo de solo lectura para los usuarios externos en tiempo real

Impedir que los datos de empresa exfiltrated por los usuarios externos, mediante el bloqueo de impresión y copiar y pegar actividades en tiempo real, el uso de Cloud App Security [controles de sesión](proxy-intro-aad.md).

### <a name="prerequisites"></a>Requisitos previos

-   [Implementar el control de aplicaciones de acceso condicional para aplicaciones de Azure AD](proxy-deployment-aad.md).
-   Asegúrese de que la aplicación es un aplicaciones basado en SAML que utiliza Azure AD para inicio de sesión único. Para obtener más información sobre las aplicaciones compatibles, consulte [admite las aplicaciones y los clientes](proxy-intro-aad.md#supported-apps-and-clients).
 
### <a name="steps"></a>Pasos

1. En el **directivas** página, cree un nuevo **directiva de sesión**.

2. En **tipo de control de sesión**, seleccione **bloquear actividades**.

3. En el **origen de la actividad** filtro:
   
    1. Seleccione **usuario** y establecer **del grupo** a **usuarios externos**.

    2. Seleccione **tipo de actividad** es igual a **impresión** y **cortar o copiar elemento**.

    > [!NOTE]
    > No es necesario establecer los filtros de aplicación para habilitar esta directiva se aplique a todas las aplicaciones.

4. Opcional: En **método de inspección**, seleccione el tipo de inspección para aplicar y establecer las condiciones necesarias para el examen de DLP.

5. En **acciones**, seleccione **bloque**. Puede seleccionar **personalizar el mensaje de bloque** para establecer un mensaje personalizado para enviarse a los usuarios para que comprenden el motivo se bloquea el contenido y cómo puede habilitarlo mediante la aplicación de la etiqueta de clasificación correcta.

6. Haga clic en **Crear**.

## <a name="block-upload-of-unclassified-documents-in-real-time"></a>Carga de bloque de sin clasificar documentos en tiempo real

Impedir que los usuarios cargar datos no protegidos en la nube, mediante el uso de Cloud App Security [controles de sesión](proxy-intro-aad.md).

### <a name="prerequisites"></a>Requisitos previos

- [Implementar el control de aplicaciones de acceso condicional para aplicaciones de Azure AD](proxy-deployment-aad.md).

- Asegúrese de que la aplicación es un aplicaciones basado en SAML que utiliza Azure AD para inicio de sesión único. Para obtener más información sobre las aplicaciones compatibles, consulte [admite las aplicaciones y los clientes](proxy-intro-aad.md#supported-apps-and-clients).

- Las etiquetas de clasificación de Azure Information Protection deben configurarse y usarse dentro de la organización.

### <a name="steps"></a>Pasos

1. En el **directivas** página, cree un nuevo **directiva de sesión**.

2. En **tipo de control de sesión**, seleccione **carga de archivos de Control (con DLP)** o **controlar la descarga de archivos (con DLP)** .

   >[!NOTE]
   > No es necesario establecer los filtros para habilitar esta directiva se aplique a todos los usuarios y aplicaciones.

3. Seleccione el filtro de archivos **etiqueta de clasificación** no igual y, a continuación, seleccione las etiquetas de su empresa usa para etiquetar los archivos clasificados.

2. Opcional: En **método de inspección**, seleccione el tipo de inspección para aplicar y establecer las condiciones necesarias para el examen de DLP.

3. En **acciones**, seleccione **bloque**. Puede seleccionar **personalizar el mensaje de bloque** para establecer un mensaje personalizado para enviarse a los usuarios para que comprenden el motivo se bloquea el contenido y cómo puede habilitarlo mediante la aplicación de la etiqueta de clasificación correcta.

4. Haga clic en **Crear**.

> [!NOTE]
> Para obtener la lista de tipos de archivo que Cloud App Security actualmente admite para las etiquetas de clasificación de Azure Information Protection, consulte [requisitos previos de integración de Azure Information Protection](azip-integration.md#prerequisites).


## <a name="next-steps"></a>Pasos siguientes 

[Actividades diarias para proteger el entorno de nube](daily-activities-to-protect-your-cloud-environment.md)   

[Los clientes Premier también pueden crear una solicitud de soporte técnico directamente en el portal Premier.](https://premier.microsoft.com/)  
  
  
