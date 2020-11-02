---
title: 'Directivas de protección contra amenazas: Cloud App Security'
description: En este tema se describen los pasos para configurar muchas directivas de protección contra amenazas en Cloud App Security.
author: shsagir
ms.author: shsagir
ms.date: 06/13/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: cloud-app-security
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 92a02c1810c427de10719193bd0b75249c9e6c21
ms.sourcegitcommit: e711727f2f00ee3b54e08337a5040449e352ca46
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/02/2020
ms.locfileid: "93186083"
---
# <a name="threat-protection-policies"></a>Directivas de protección contra amenazas

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Cloud App Security le permite identificar problemas de seguridad en la nube y de uso de alto riesgo, detectar comportamientos anómalos de los usuarios y evitar amenazas en las aplicaciones en la nube autorizadas. Obtenga visibilidad de las actividades de usuario y administración, y defina directivas para alertar automáticamente cuando se detecten comportamientos sospechosos o actividades específicas que considere arriesgado. Extraiga la inmensa cantidad de datos de investigación de seguridad e inteligencia de amenazas de Microsoft para asegurarse de que sus aplicaciones autorizadas tienen todos los controles de seguridad que necesita y le ayudan a mantener el control sobre ellas.

> [!NOTE]
> Al integrar Cloud App Security con protección contra amenazas avanzada de Azure (ATP de Azure), las directivas de ATP de Azure también aparecen en la página directivas. Para obtener una lista de las directivas de ATP de Azure, consulte [alertas de seguridad](/azure-advanced-threat-protection/suspicious-activity-guide).

## <a name="detect-and-control-user-activity-from-unfamiliar-locations"></a>Detección y control de la actividad de los usuarios desde ubicaciones desconocidas

Detección automática del acceso o actividad de los usuarios desde ubicaciones desconocidas que nunca han visitado otros usuarios de su organización.

### <a name="prerequisites"></a>Requisitos previos

Debe tener al menos una aplicación conectada mediante los [conectores de aplicaciones](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md) o incorporada mediante el [control de aplicaciones de acceso condicional con controles de sesión](proxy-deployment-aad.md).

### <a name="steps"></a>Pasos

Esta detección se configura automáticamente de forma automática para avisarle cuando haya acceso desde nuevas ubicaciones. No es necesario realizar ninguna acción para configurar esta Directiva. Para más información, consulte [Directivas de detección de anomalías](anomaly-detection-policy.md).

## <a name="detect-compromised-account-by-impossible-location-impossible-travel"></a>Detección de una cuenta en peligro por ubicación imposible (viaje imposible)

Detección automática del acceso o actividad de los usuarios desde dos ubicaciones diferentes dentro de un período de tiempo menor que el tiempo que se tarda en viajar entre los dos.

### <a name="prerequisites"></a>Requisitos previos

Debe tener al menos una aplicación conectada mediante los [conectores de aplicaciones](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md) o incorporada mediante el [control de aplicaciones de acceso condicional con controles de sesión](proxy-deployment-aad.md).
### <a name="steps"></a>Pasos

1. Esta detección se configura automáticamente de forma automática para avisarle cuando haya acceso desde ubicaciones imposibles. No es necesario realizar ninguna acción para configurar esta Directiva. Para más información, consulte [Directivas de detección de anomalías](anomaly-detection-policy.md).
2. Opcional: puede [personalizar las directivas de detección de anomalías](anomaly-detection-policy.md#scope-anomaly-detection-policies):

    - Personalizar el ámbito de detección en términos de usuarios y grupos

    - Elegir los tipos de inicios de sesión que se deben tener en cuenta

    - Establecer la preferencia de sensibilidad para las alertas

3. Cree la Directiva de detección de anomalías.

## <a name="detect-suspicious-activity-from-an-on-leave-employee"></a>Detección de actividades sospechosas de un empleado "activado"

Detectar cuándo un usuario, que se encuentra en un abandono no pagado y no debe estar activo en ningún recurso de la organización, tiene acceso a los recursos de la nube de su organización.

### <a name="prerequisites"></a>Requisitos previos

- Debe tener al menos una aplicación conectada mediante los [conectores de aplicaciones](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md).

- Cree un grupo de seguridad en Azure Active Directory para los usuarios con permiso no pagado y agregue todos los usuarios que desee supervisar.

### <a name="steps"></a>Pasos

1. En la pantalla [grupos de usuarios](user-groups.md) , haga clic en **Crear grupo de usuarios** e importe el grupo de Azure ad correspondiente.

2. En la página **directivas** , cree una nueva **Directiva de actividad** .

3. Establezca el **grupo de usuarios** de filtro en el nombre de los grupos de usuarios que ha creado en Azure ad para los usuarios no pagados.

4. Opcional: establecer las acciones de **gobierno** que se realizarán en los archivos cuando se detecte una infracción. Las acciones de gobierno disponibles varían entre los servicios. Puede elegir **suspender usuario** .

5. Cree la Directiva de archivo.

## <a name="detect-and-notify-when-outdated-browser-os-is-used"></a>Detección y notificación cuando se utiliza el sistema operativo del explorador obsoleto

Detecte Cuándo un usuario usa un explorador con una versión de cliente obsoleta que podría suponer riesgos de cumplimiento o seguridad para su organización.

### <a name="prerequisites"></a>Requisitos previos

Debe tener al menos una aplicación conectada mediante los [conectores de aplicaciones](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md) o incorporada mediante el [control de aplicaciones de acceso condicional con controles de sesión](proxy-deployment-aad.md).

### <a name="steps"></a>Pasos

1. En la página **directivas** , cree una nueva **Directiva de actividad** .

2. Establezca la **etiqueta de agente de usuario** filtrada en es el **Explorador obsoleto** y el **sistema operativo obsoleto** .

3. Establecer las acciones de **gobierno** que se realizarán en los archivos cuando se detecte una infracción. Las acciones de gobierno disponibles varían entre los servicios. En **todas las aplicaciones** , seleccione **notificar al usuario** para que los usuarios puedan actuar sobre la alerta y actualizar los componentes necesarios.

4. Cree la Directiva de actividad.

## <a name="detect-and-alert-when-admin-activity-is-detected-on-risky-ip-addresses"></a>Detección y alerta cuando se detecta actividad de administración en direcciones IP de riesgo

Detecte las actividades de administración realizadas desde y la dirección IP que se considera una dirección IP de riesgo, y notifique al administrador del sistema para que realice más investigación o establezca una acción de gobierno en la cuenta del administrador.

### <a name="prerequisites"></a>Requisitos previos

- Debe tener al menos una aplicación conectada mediante los [conectores de aplicaciones](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md).

- En el engranaje de configuración, seleccione **intervalos de direcciones IP** y haga clic en + para agregar intervalos de direcciones IP para las subredes internas y sus direcciones IP públicas de salida. Establezca la **categoría** en **interno** .

### <a name="steps"></a>Pasos

1. En la página **directivas** , cree una nueva **Directiva de actividad** .

2. Establezca **actuar en** **una sola actividad** .

3. Establecer la **dirección IP** del filtro en **categoría** es igual a **arriesgado**

4. Establezca la **actividad administrativa** filtrar en **true** .

5. Establecer las acciones de **gobierno** que se realizarán en los archivos cuando se detecte una infracción. Las acciones de gobierno disponibles varían entre los servicios. En **todas las aplicaciones** , seleccione **notificar al usuario** para que los usuarios puedan actuar en la alerta y actualizar los componentes necesarios en **el administrador del usuario** .

6. Cree la Directiva de actividad.

## <a name="detect-activities-by-service-account-from-external-ip-addresses"></a>Detección de actividades por cuenta de servicio desde direcciones IP externas

Detectar las actividades de la cuenta de servicio que se originan en una dirección IP no interna. Esto podría indicar un comportamiento sospechoso o una cuenta en peligro.

### <a name="prerequisites"></a>Requisitos previos

- Debe tener al menos una aplicación conectada mediante los [conectores de aplicaciones](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md).
- En el engranaje de configuración, seleccione **intervalos de direcciones IP** y haga clic en + para agregar intervalos de direcciones IP para las subredes internas y sus direcciones IP públicas de salida. Establezca la **categoría** en **interno** .

- Estandarizar las convenciones de nomenclatura para las cuentas de servicio en el entorno, por ejemplo, establecer que todos los nombres de cuenta empiecen por "SVC".

### <a name="steps"></a>Pasos

1. En la página **directivas** , cree una nueva **Directiva de actividad** .

2. Establezca el filtro **usuario** en **nombre** y, a continuación, **empiece por** y escriba su Convención de nomenclatura, como SVC.

3. Establezca el filtro **dirección IP** en **categoría** no es igual a **otro** y **corporativo** .

4. Establecer las acciones de **gobierno** que se realizarán en los archivos cuando se detecte una infracción. Las acciones de gobierno disponibles varían entre los servicios.

5. Crear la directiva.

## <a name="detect-mass-download-data-exfiltration"></a>Detección de la descarga masiva (exfiltración de datos)

Detectar cuándo un usuario determinado tiene acceso o descarga un número masivo de archivos en un breve período de tiempo.

### <a name="prerequisites"></a>Requisitos previos

Debe tener al menos una aplicación conectada mediante los [conectores de aplicaciones](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md) o incorporada mediante el [control de aplicaciones de acceso condicional con controles de sesión](proxy-deployment-aad.md).

### <a name="steps"></a>Pasos

1. En la página **directivas** , cree una nueva **Directiva de actividad** .

2. Establezca el filtro de **direcciones IP** en **etiqueta** no es igual a **Microsoft Azure** . Esto excluirá las actividades no interactivas basadas en dispositivos.

3. Establezca los **tipos de actividad** de filtro es igual a y, a continuación, seleccione todas las actividades de descarga pertinentes.

4. Establecer las acciones de **gobierno** que se realizarán en los archivos cuando se detecte una infracción. Las acciones de gobierno disponibles varían entre los servicios.
5. Crear la directiva.

## <a name="detect-potential-ransomware-activity"></a>Detección de una posible actividad de ransomware

Detección automática de la posible actividad de ransomware.

### <a name="prerequisites"></a>Requisitos previos

Debe tener al menos una aplicación conectada mediante los [conectores de aplicaciones](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md).

### <a name="steps"></a>Pasos

1. Esta detección se configura automáticamente de forma automática para avisarle cuando se detecte un riesgo de ransomware potencial. No es necesario realizar ninguna acción para configurar esta Directiva. Para más información, consulte [Directivas de detección de anomalías](anomaly-detection-policy.md).

2. Es posible configurar el **ámbito** de la detección y personalizar las acciones de gobierno que se llevarán a cabo cuando se desencadene una alerta. Para obtener más información acerca de cómo Cloud App Security identifica ransomware, consulte [protección de la organización desde ransomware](use-case-ransomware.md).

> [!NOTE]
> Esto se aplica a Office 365, G Suite, Box y Dropbox.

## <a name="detect-malware-in-the-cloud"></a>Detección de malware en la nube

Detecte archivos que contengan malware en los entornos de nube mediante la integración de Cloud App Security con el motor de inteligencia de amenazas de Microsoft.

### <a name="prerequisites"></a>Requisitos previos

- Para la detección de malware de Office 365, debe tener una licencia válida para la protección contra amenazas avanzada de Office 365 P1.
- Debe tener al menos una aplicación conectada mediante los [conectores de aplicaciones](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md).

### <a name="steps"></a>Pasos

- Esta detección se configura automáticamente de forma automática para avisarle cuando hay un archivo que puede contener malware. No es necesario realizar ninguna acción para configurar esta Directiva. Para más información, consulte [Directivas de detección de anomalías](anomaly-detection-policy.md).

## <a name="detect-rogue-admin-takeover"></a>Detección de la adquisición de administrador no autorizado

Detecte una actividad de administración repetida que puede indicar intenciones malintencionadas.

### <a name="prerequisites"></a>Requisitos previos

Debe tener al menos una aplicación conectada mediante los [conectores de aplicaciones](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md).

### <a name="steps"></a>Pasos

1. En la página **directivas** , cree una nueva **Directiva de actividad** .

2. Establezca **actúa en** la **actividad repetida** y Personalice las **actividades mínimas repetidas** y establezca un **período de tiempo** para cumplir con la Directiva de su organización.

3. Establezca el filtro **usuario** en **de grupo** es igual a y seleccione solo el grupo de administración relacionado como **actor** .

4. Establezca el **tipo de actividad** de filtro es igual a todas las actividades relacionadas con las actualizaciones, los cambios y los restablecimientos de contraseña.

5. Establecer las acciones de **gobierno** que se realizarán en los archivos cuando se detecte una infracción. Las acciones de gobierno disponibles varían entre los servicios.
6. Crear la directiva.

## <a name="detect-suspicious-inbox-manipulation-rules"></a>Detectar reglas de manipulación de bandeja de entrada sospechosas

Si se ha establecido una regla de bandeja de entrada sospechosa en la bandeja de entrada de un usuario, puede indicar que la cuenta de usuario está en peligro y que el buzón se usa para distribuir el correo no deseado y el malware en la organización.

### <a name="prerequisites"></a>Requisitos previos

- Uso de Microsoft Exchange para el correo electrónico.

### <a name="steps"></a>Pasos

- Esta detección se configura automáticamente de forma automática para avisarle cuando haya un conjunto de reglas de bandeja de entrada sospechoso. No es necesario realizar ninguna acción para configurar esta Directiva. Para más información, consulte [Directivas de detección de anomalías](anomaly-detection-policy.md).

## <a name="detect-leaked-credentials"></a>Detección de credenciales perdidas

Cuando los delincuentes cibernéticos ponen en peligro contraseñas válidas de usuarios legítimos, suelen compartir esas credenciales. Suelen hacer esto publicándolas en la Web oscura o sitios de pegado, o bien mediante el intercambio o la venta de esas credenciales en el mercado negro.

Cloud App Security usa la inteligencia de amenazas de Microsoft para hacer coincidir las credenciales con las que se usan dentro de la organización.

### <a name="prerequisites"></a>Requisitos previos

Debe tener al menos una aplicación conectada mediante los [conectores de aplicaciones](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md).

### <a name="steps"></a>Pasos

Esta detección se configura automáticamente de forma automática para avisarle cuando se detecte una posible pérdida de credenciales. No es necesario realizar ninguna acción para configurar esta Directiva. Para más información, consulte [Directivas de detección de anomalías](anomaly-detection-policy.md).

## <a name="detect-anomalous-file-downloads"></a>Detección de descargas de archivos anómalas

Detecte Cuándo los usuarios realizan varias actividades de descarga de archivos en una sola sesión, en relación con la base de referencia aprendida. Esto podría indicar un intento de infracción.

### <a name="prerequisites"></a>Requisitos previos

Debe tener al menos una aplicación conectada mediante los [conectores de aplicaciones](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md) o incorporada mediante el [control de aplicaciones de acceso condicional con controles de sesión](proxy-deployment-aad.md).

### <a name="steps"></a>Pasos

1. Esta detección se configura automáticamente de forma automática para avisarle cuando se produce una descarga anómala. No es necesario realizar ninguna acción para configurar esta Directiva. Para más información, consulte [Directivas de detección de anomalías](anomaly-detection-policy.md).

2. Es posible configurar el ámbito de la detección y personalizar la acción que se realizará cuando se desencadene una alerta.

## <a name="detect-anomalous-file-shares-by-a-user"></a>Detección de recursos compartidos de archivos anómalos por un usuario

Detecte Cuándo los usuarios realizan varias actividades de uso compartido de archivos en una sola sesión con respecto a la base de referencia aprendida, lo que podría indicar una infracción de intento.

### <a name="prerequisites"></a>Requisitos previos

Debe tener al menos una aplicación conectada mediante los [conectores de aplicaciones](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md) o incorporada mediante el [control de aplicaciones de acceso condicional con controles de sesión](proxy-deployment-aad.md).

### <a name="steps"></a>Pasos

1. Esta detección se configura automáticamente de forma automática para avisarle cuando los usuarios realicen varios recursos compartidos de archivos. No es necesario realizar ninguna acción para configurar esta Directiva. Para más información, consulte [Directivas de detección de anomalías](anomaly-detection-policy.md).

2. Es posible configurar el ámbito de la detección y personalizar la acción que se realizará cuando se desencadene una alerta.

## <a name="detect-anomalous-activities-from-infrequent-country"></a>Detección de actividades anómalas de un país poco frecuente

Detecte actividades de una ubicación que no se haya visitado recientemente o que nunca haya visitado el usuario o cualquier usuario de la organización.

### <a name="prerequisites"></a>Requisitos previos

Debe tener al menos una aplicación conectada mediante los [conectores de aplicaciones](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md) o incorporada mediante el [control de aplicaciones de acceso condicional con controles de sesión](proxy-deployment-aad.md).

### <a name="steps"></a>Pasos

1. Esta detección se configura automáticamente de forma automática para avisarle cuando se produce una actividad anómala de un país o región poco frecuente. No es necesario realizar ninguna acción para configurar esta Directiva. Para más información, consulte [Directivas de detección de anomalías](anomaly-detection-policy.md).

2. Es posible configurar el ámbito de la detección y personalizar la acción que se realizará cuando se desencadene una alerta.

> [!NOTE]
> La detección de ubicaciones anómalas requiere un período de aprendizaje inicial de 7 días. Durante el período de aprendizaje, Cloud App Security no genera alertas para las nuevas ubicaciones.

## <a name="detect-activity-performed-by-a-terminated-user"></a>Detección de la actividad realizada por un usuario Terminado

Detectar cuándo un usuario que ya no es un empleado de la organización realiza una actividad en una aplicación autorizada. Esto puede indicar una actividad malintencionada por parte de un empleado terminado que todavía tiene acceso a los recursos corporativos.

### <a name="prerequisites"></a>Requisitos previos

Debe tener al menos una aplicación conectada mediante los [conectores de aplicaciones](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md).

### <a name="steps"></a>Pasos

1. Esta detección se configura automáticamente de forma automática para avisarle cuando un empleado terminado realiza una actividad. No es necesario realizar ninguna acción para configurar esta Directiva. Para más información, consulte [Directivas de detección de anomalías](anomaly-detection-policy.md).

2. Es posible configurar el ámbito de la detección y personalizar la acción que se realizará cuando se desencadene una alerta.

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Actividades diarias para proteger el entorno de nube](daily-activities-to-protect-your-cloud-environment.md)

[!INCLUDE [Open support ticket](includes/support.md)]