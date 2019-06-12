---
title: Directivas de protección - Cloud App Security de amenazas | Microsoft Docs
description: En este tema se describe los pasos para configurar muchas directivas de protección contra amenazas en Cloud App Security.
author: rkarlin
ms.author: rkarlin
ms.date: 06/13/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: cloud-app-security
ms.assetid: 7c8d5bfd-194e-40ba-b0b0-dfae80f45ecb
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 4cb65835bf2f03eb6bef2fc5973be3420cdedb3d
ms.sourcegitcommit: 9f671d5dd5e5da023d598425442d8736546ca183
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/11/2019
ms.locfileid: "66837773"
---
# <a name="threat-protection-policies"></a>Directivas de protección contra amenazas

*Se aplica a: Microsoft Cloud App Security*


Cloud App Security le permite identificar problemas de seguridad de uso y la nube de alto riesgo, detecte comportamientos inusuales de los usuarios y evite amenazas en las aplicaciones de nube autorizada. Obtenga visibilidad sobre las actividades de usuario y administrador y definir directivas para recibir automáticamente alertas cuando se detectan comportamientos sospechosos o actividades específicas que consideran que entrañan riesgos. Extraer de la gran cantidad de datos de investigación de seguridad para ayudar a garantizar que las aplicaciones autorizadas tengan todos los controles de seguridad que necesita en el lugar y ayudan a mantener el control sobre ellas e inteligencia de amenazas de Microsoft.

## <a name="detect-and-control-user-activity-from-unfamiliar-locations"></a>Detectar y controlar la actividad del usuario desde ubicaciones desconocidas

Detección automática de acceso de usuario o actividad desde ubicaciones desconocidas que no visitó nunca nadie en su organización.

### <a name="prerequisites"></a>Requisitos previos

Debe tener al menos una aplicación conectada mediante [conectores de aplicaciones](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md) o integrado con [control de aplicaciones de acceso condicional con controles de sesión](proxy-deployment-aad.md).

### <a name="steps"></a>Pasos

Esta detección está configurada automáticamente-de-fábrica que le avise cuando no hay acceso desde ubicaciones nuevas. No es necesario realizar ninguna acción para configurar esta directiva. Para obtener más información, vea [Directivas de detección de anomalías](anomaly-detection-policy.md).

## <a name="detect-compromised-account-by-impossible-location-impossible-travel"></a>Detectar la cuenta en peligro por ubicación imposible (viaje imposible)

Detección automática de acceso de usuario o actividad desde 2 ubicaciones diferentes dentro de un período de tiempo más corto que el tiempo que tarda en viajar entre los dos.

### <a name="prerequisites"></a>Requisitos previos

Debe tener al menos una aplicación conectada mediante [conectores de aplicaciones](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md) o integrado con [control de aplicaciones de acceso condicional con controles de sesión](proxy-deployment-aad.md).
### <a name="steps"></a>Pasos

1.  Esta detección está configurada automáticamente-de-fábrica que le avise cuando no hay acceso desde ubicaciones imposibles. No es necesario realizar ninguna acción para configurar esta directiva. Para obtener más información, vea [Directivas de detección de anomalías](anomaly-detection-policy.md).
2. Opcional: puede [personalizar directivas de detección de anomalías](anomaly-detection-policy.md#scope-anomaly-detection-policies): 
    - Personalizar el ámbito de detección en cuanto a los usuarios y grupos

    - Elegir los tipos de inicios de sesión a tener en cuenta

    - Establecer las preferencias de sensibilidad para alertas

3.  Crear la directiva de detección de anomalías.

## <a name="detect-suspicious-activity-from-an-on-leave-employee"></a>Detectar actividades sospechosas de un empleado "baja"

Detectar cuándo un usuario, que está en el sueldo y no debe estar activo en los recursos de la organización, se accede a cualquiera de los recursos de nube de su organización.

### <a name="prerequisites"></a>Requisitos previos

- Debe tener al menos una aplicación conectada mediante [conectores de aplicaciones](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md).

- Crear un grupo de seguridad en Azure Active Directory para los usuarios sin sueldo y agregar todos los usuarios que desea supervisar.

### <a name="steps"></a>Pasos

1.  En el [grupos de usuarios](user-groups.md) pantalla, haga clic en **crear grupo de usuarios** y grupo de importaciones pertinente de Azure AD.

2.  En el **directivas** página, cree un nuevo **directiva de actividad**.

3.  Establezca el filtro **grupo de usuarios** igual al nombre de los grupos de usuarios creado en Azure AD para el impago deje los usuarios.

4.  Opcional: Establecer el **gobierno** las acciones realizadas en los archivos cuando se detecta una infracción. Las acciones de gobierno disponibles varían entre los servicios. Puede elegir **suspender usuario**.

6.  Cree la directiva de archivo.

## <a name="detect-and-notify-when-outdated-browser-os-is-used"></a>Detectar y notificar cuando está obsoleta es usar el explorador del sistema operativo

Detectar cuándo un usuario está usando un explorador con una versión obsoleta del cliente que puede suponer riesgos de seguridad para su organización o de cumplimiento.

### <a name="prerequisites"></a>Requisitos previos

Debe tener al menos una aplicación conectada mediante [conectores de aplicaciones](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md) o integrado con [control de aplicaciones de acceso condicional con controles de sesión](proxy-deployment-aad.md).

### <a name="steps"></a>Pasos

1.  En el **directivas** página, cree un nuevo **directiva de actividad**.

2.  Establezca el filtro **etiqueta de agente de usuario** es igual a **explorador obsoleto** y **sistema operativo obsoleto**.

3. Establecer el **gobierno** las acciones realizadas en los archivos cuando se detecta una infracción. Las acciones de gobierno disponibles varían entre los servicios. En **todas las aplicaciones**, seleccione **enviar notificación al usuario**, de modo que los usuarios pueden actuar sobre la alerta y actualizar los componentes necesarios.

5.  Crear la directiva de actividad.

## <a name="detect-and-alert-when-admin-activity-is-detected-on-risky-ip-addresses"></a>Detecta y resuelve una alerta cuando se detecta actividad administrativa en direcciones IP de riesgo

Detectar las actividades de administración realizadas desde y dirección IP que se considera una dirección IP de riesgo, y notifique el administrador del sistema para una investigación más detallada o establecer una acción de gobierno en la cuenta del administrador.

### <a name="prerequisites"></a>Requisitos previos

- Debe tener al menos una aplicación conectada mediante [conectores de aplicaciones](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md).
 
- En el engranaje de configuración, seleccione **intervalos de direcciones IP** y haga clic en el + para agregar intervalos de direcciones IP para las subredes internas y sus direcciones IP públicas de salida. Establecer el **categoría** a **interno**.

### <a name="steps"></a>Pasos

1.  En el **directivas** página, cree un nuevo **directiva de actividad**.

2.  Establecer **actuar en** a **única actividad**.

3.  Establezca el filtro **dirección IP** a **categoría** es igual a **riesgo**

4.  Establezca el filtro **actividades administrativas** a **True**

5.  Establecer el **gobierno** las acciones realizadas en los archivos cuando se detecta una infracción. Las acciones de gobierno disponibles varían entre los servicios. En **todas las aplicaciones**, seleccione **enviar notificación al usuario**, de modo que los usuarios pueden actuar sobre la alerta y actualizar los componentes necesarios **CC el administrador del usuario**.

7.  Crear la directiva de actividad.

## <a name="detect-activities-by-service-account-from-external-ip-addresses"></a>Detección de actividades mediante la cuenta de servicio de direcciones IP externas

Detectar actividades de cuenta de servicio que se originan desde una dirección IP no interna direcciones. Esto podría indicar un comportamiento sospechoso o una cuenta en peligro.

### <a name="prerequisites"></a>Requisitos previos

- Debe tener al menos una aplicación conectada mediante [conectores de aplicaciones](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md).
- En el engranaje de configuración, seleccione **intervalos de direcciones IP** y haga clic en el + para agregar intervalos de direcciones IP para las subredes internas y sus direcciones IP públicas de salida. Establecer el **categoría** a **interno**.

- Estandarizar un convenciones de nomenclatura para las cuentas de servicio en su entorno, por ejemplo, establezca todos los nombres de cuenta para comenzar con "svc".

### <a name="steps"></a>Pasos

1.  En el **directivas** página, cree un nuevo **directiva de actividad**.

2.  Establezca el filtro **usuario** a **nombre** y, a continuación, **comienza con** y escriba su convención de nomenclatura, por ejemplo, svc.

3.  Establezca el filtro **dirección IP** a **categoría** no es igual a **otros** y **Corporate**.

4.  Establecer el **gobierno** las acciones realizadas en los archivos cuando se detecta una infracción. Las acciones de gobierno disponibles varían entre los servicios.

5.  Crear la directiva.

## <a name="detect-mass-download-data-exfiltration"></a>Detectar descarga masiva (exfiltración de datos)

Detectar cuándo un determinado usuario obtiene acceso o descarga un gran número de archivos en un breve período de tiempo.

### <a name="prerequisites"></a>Requisitos previos

Debe tener al menos una aplicación conectada mediante [conectores de aplicaciones](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md) o integrado con [control de aplicaciones de acceso condicional con controles de sesión](proxy-deployment-aad.md).

### <a name="steps"></a>Pasos

1.  En el **directivas** página, cree un nuevo **directiva de actividad**.

2.  Establezca el filtro **direcciones IP** a **etiqueta** no es igual a **Microsoft Azure**. Se excluirán actividades basadas en máquinas no interactivo.

3.  Establezca el filtro **tipos de actividad** es igual a y, a continuación, seleccione todas las actividades de descarga correspondiente.

4. Establecer el **gobierno** las acciones realizadas en los archivos cuando se detecta una infracción. Las acciones de gobierno disponibles varían entre los servicios.
5.  Crear la directiva.

## <a name="detect-potential-ransomware-activity"></a>Detectar actividad potencial de Ransomware

Detección automática de la actividad potencial de Ransomware.

### <a name="prerequisites"></a>Requisitos previos

Debe tener al menos una aplicación conectada mediante [conectores de aplicaciones](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md).

### <a name="steps"></a>Pasos

- Esta detección está configurada automáticamente-de-fábrica que le avise cuando hay un riesgo potencial de ransomware detectado. No es necesario realizar ninguna acción para configurar esta directiva. Para obtener más información, vea [Directivas de detección de anomalías](anomaly-detection-policy.md).  

- Es posible configurar el **ámbito** de la detección y personalizar las acciones de gobierno que se realizará cuando se desencadena una alerta. Para obtener más información acerca de cómo Cloud App Security identifica Ransomware, vea [proteger la organización frente a ransomware](use-case-ransomware.md).

> [!NOTE]
> Esto se aplica a Office 365, G Suite, cuadro y Dropbox.

## <a name="detect-malware-in-the-cloud"></a>Detectar software malintencionado en la nube

Detectar archivos que contienen código malintencionado en los entornos de nube mediante el uso de la integración de Cloud App Security con el motor de inteligencia de amenazas de Microsoft.

### <a name="prerequisites"></a>Requisitos previos

Debe tener al menos una aplicación conectada mediante [conectores de aplicaciones](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md).

### <a name="steps"></a>Pasos

- Esta detección está configurada automáticamente-de-fábrica que le avise cuando hay un archivo que puede contener malware. No es necesario realizar ninguna acción para configurar esta directiva. Para obtener más información, vea [Directivas de detección de anomalías](anomaly-detection-policy.md).  

## <a name="detect-rogue-admin-takeover"></a>Detectar la adquisición de administración rogue

Detectar actividad admin repetidas que podría indicar la presencia de intentos malintencionado.

### <a name="prerequisites"></a>Requisitos previos

Debe tener al menos una aplicación conectada mediante [conectores de aplicaciones](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md).

### <a name="steps"></a>Pasos

1.  En el **directivas** página, cree un nuevo **directiva de actividad**.

2.  Establecer **actuar en** a **actividad repetida** y personalizar la **mínimo actividades repetidas** y establezca un **período de tiempo** para cumplir con su Directiva de la organización...

3.  Establezca el filtro **usuario** a **del grupo** es igual a y seleccione el Administrador de relacionados se agrupan como **solo Actor**.

4.  Establezca el filtro **tipo de actividad** es igual a todas las actividades relacionadas con actualizaciones de contraseñas, los cambios y se restablece.

5. Establecer el **gobierno** las acciones realizadas en los archivos cuando se detecta una infracción. Las acciones de gobierno disponibles varían entre los servicios.
6.  Crear la directiva.

## <a name="detect-suspicious-inbox-manipulation-rules"></a>Detectar las reglas de manipulación de bandeja de entrada sospechosa

Si se estableció una regla de bandeja de entrada sospechosos en la Bandeja de entrada del usuario, puede indicar que está en peligro la cuenta de usuario, y que se está usando el buzón para distribuir el software malintencionado en su organización.

### <a name="prerequisites"></a>Requisitos previos

- Uso de Microsoft Exchange para el correo electrónico.

### <a name="steps"></a>Pasos

- Esta detección está configurada automáticamente-de-fábrica que le avise cuando hay un conjunto de reglas de la Bandeja de entrada sospechosa. No es necesario realizar ninguna acción para configurar esta directiva. Para obtener más información, vea [Directivas de detección de anomalías](anomaly-detection-policy.md).  


## <a name="detect-leaked-credentials"></a>Detectar las credenciales filtradas
  
Cuando los cibercriminales poner en peligro las contraseñas válidas de los usuarios legítimos, comparten a menudo esas credenciales. Esto se hace normalmente publicándolas en los sitios web o pegar oscuros o comerciales o venta de esas credenciales en el mercado negro.

Cloud App Security usa inteligencia de amenazas de Microsoft para que coincidan con estas credenciales a los que se utilizan dentro de la organización.

### <a name="prerequisites"></a>Requisitos previos

Debe tener al menos una aplicación conectada mediante [conectores de aplicaciones](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md).

### <a name="steps"></a>Pasos

Esta detección está configurada automáticamente-de-fábrica que le avise cuando se detecta una pérdida de credencial posibles. No es necesario realizar ninguna acción para configurar esta directiva. Para obtener más información, vea [Directivas de detección de anomalías](anomaly-detection-policy.md).  


## <a name="detect-anomalous-file-downloads"></a>Detectar las descargas de archivos anómalos

Detectar cuando los usuarios realizan varias actividades de descarga de archivos en una única sesión, en relación con la línea base aprendida. Esto podría indicar un intento de brecha.

### <a name="prerequisites"></a>Requisitos previos

Debe tener al menos una aplicación conectada mediante [conectores de aplicaciones](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md) o integrado con [control de aplicaciones de acceso condicional con controles de sesión](proxy-deployment-aad.md).

### <a name="steps"></a>Pasos

- Esta detección está configurada automáticamente-de-fábrica que le avise cuando se produzca una descarga anómalo. No es necesario realizar ninguna acción para configurar esta directiva. Para obtener más información, vea [Directivas de detección de anomalías](anomaly-detection-policy.md).  
- Es posible configurar el ámbito de la detección y personalizar la acción que se realizará cuando se desencadene una alerta.

## <a name="detect-anomalous-file-shares-by-a-user"></a>Detectar recursos compartidos de archivos anómalo por un usuario

Detectar cuando los usuarios realizan varias actividades de uso compartido de archivos en una única sesión con respecto a la línea base aprendida, lo que podría indicar un intento de brecha.

### <a name="prerequisites"></a>Requisitos previos
Debe tener al menos una aplicación conectada mediante [conectores de aplicaciones](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md) o integrado con [control de aplicaciones de acceso condicional con controles de sesión](proxy-deployment-aad.md).
### <a name="steps"></a>Pasos

- Esta detección está configurada automáticamente-de-fábrica para avisarle cuando los usuarios realizan el uso compartido de archivos varios. No es necesario realizar ninguna acción para configurar esta directiva. Para obtener más información, vea [Directivas de detección de anomalías](anomaly-detection-policy.md).  
- Es posible configurar el ámbito de la detección y personalizar la acción que se realizará cuando se desencadene una alerta.

## <a name="detect-anomalous-activities-from-infrequent-country"></a>Detectar actividad anómala de un país poco frecuente

Detección de actividades desde una ubicación que no ha estado recientemente o nunca se ha visitado por el usuario o por cualquier usuario en su organización.

### <a name="prerequisites"></a>Requisitos previos

Debe tener al menos una aplicación conectada mediante [conectores de aplicaciones](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md) o integrado con [control de aplicaciones de acceso condicional con controles de sesión](proxy-deployment-aad.md).

### <a name="steps"></a>Pasos

- Esta detección está configurada automáticamente-de-fábrica que le avise cuando se produce una actividad anómala desde un país poco frecuente. No es necesario realizar ninguna acción para configurar esta directiva. Para obtener más información, vea [Directivas de detección de anomalías](anomaly-detection-policy.md).  
- Es posible configurar el ámbito de la detección y personalizar la acción que se realizará cuando se desencadene una alerta.

> [!NOTE]
> Detección de ubicaciones anómalas requiere un período de aprendizaje inicial de siete días. Durante el período de aprendizaje, Cloud App Security no generan alertas para las nuevas ubicaciones.

## <a name="detect-activity-performed-by-a-terminated-user"></a>Detectar actividad realizada por un usuario cancelado

Detectar cuándo un usuario que ya no es un empleado de su organización realiza una actividad en una aplicación autorizada. Esto puede indicar actividad malintencionada por parte de un empleado despedido que todavía tiene acceso a recursos corporativos.

### <a name="prerequisites"></a>Requisitos previos

Debe tener al menos una aplicación conectada mediante [conectores de aplicaciones](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md).

### <a name="steps"></a>Pasos

- Esta detección está configurada automáticamente-de-fábrica que le avise cuando se realiza una actividad por un empleado despedido. No es necesario realizar ninguna acción para configurar esta directiva. Para obtener más información, vea [Directivas de detección de anomalías](anomaly-detection-policy.md).  
- Es posible configurar el ámbito de la detección y personalizar la acción que se realizará cuando se desencadene una alerta.


## <a name="next-steps"></a>Pasos siguientes 

[Actividades diarias para proteger el entorno de nube](daily-activities-to-protect-your-cloud-environment.md)   

[Los clientes Premier también pueden crear una solicitud de soporte técnico directamente en el portal Premier.](https://premier.microsoft.com/)  
  
  
