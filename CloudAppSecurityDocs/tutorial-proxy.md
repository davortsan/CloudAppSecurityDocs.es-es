---
title: Protección de cualquier aplicación en uso de la organización en tiempo real
description: En este tutorial se proporcionan instrucciones para usar controles de acceso y de sesión para supervisar y controlar el acceso a las aplicaciones y sus datos.
author: shsagir
ms.author: shsagir
ms.service: cloud-app-security
ms.topic: tutorial
ms.date: 01/01/2020
ms.collection: M365-security-compliance
ms.openlocfilehash: fec6182d004b934f564291e4ca9f4fe06aa8d723
ms.sourcegitcommit: 0b929f7c8feed7dfb40d5294179fd5c6fc079614
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/21/2020
ms.locfileid: "75667565"
---
# <a name="tutorial-protect-any-apps-in-use-in-your-organization-in-real-time"></a>Tutorial: Protección de cualquier aplicación en uso de la organización en tiempo real

*Se aplica a: Microsoft Cloud App Security*

Las aplicaciones que autoriza a los empleados a usar, a menudo almacenan algunos de los datos corporativos y secretos más confidenciales. En el área de trabajo moderna, los usuarios acceden a estas aplicaciones en muchas situaciones de riesgo. Estos usuarios podrían ser asociados de la organización sobre los que tiene poca visibilidad, o bien empleados que usan dispositivos no administrados o que proceden de direcciones IP públicas. Debido a la amplia gama de riesgos de este panorama, se debe emplear una estrategia de confianza cero. A menudo, no es suficiente conocer las infracciones y la pérdida de datos en estas aplicaciones después de que se produzcan; por tanto, muchos escenarios de protección de la información y ciberamenazas se deben solucionar o evitar en tiempo real.

En este tutorial se proporcionan instrucciones para usar controles de acceso y de sesión para supervisar y controlar el acceso a las aplicaciones y sus datos. Administrar el acceso a los datos de forma adaptativa y mitigar las amenazas permite que Cloud App Security proteja los recursos más confidenciales. En concreto, se tratarán los escenarios siguientes:

> [!div class="checklist"]
>
> * Supervisión de las actividades de los usuarios en busca de anomalías
> * Protección de los datos cuando se filtren
> * Impedir que se carguen datos no protegidos en las aplicaciones

## <a name="how-to-protect-your-organization-from-any-app-in-real-time"></a>Procedimiento para proteger la organización de cualquier aplicación en tiempo real

Use este proceso para implementar controles en tiempo real en la organización.

### <a name="phase-1-monitor-user-activities-for-anomalies"></a>Fase 1: Supervisión de las actividades de los usuarios en busca de anomalías

1. **Implementación de las aplicaciones**: comience por implementar las aplicaciones importantes que se usan en la organización. Nuestra integración nativa con el acceso condicional de Azure Active Directory (Azure AD) simplifica la implementación. Puede implementar aplicaciones mediante los pasos siguientes:

    * Comience por [implementar aplicaciones destacadas](proxy-intro-aad.md) por Cloud App Security por estar listas para usarse. Para obtener una lista de las aplicaciones destacadas, vea [Aplicaciones y clientes compatibles](proxy-intro-aad.md#supported-apps-and-clients).

    * Después, en el caso de las aplicaciones que Cloud App Security no destaca, use el proceso siguiente para [incorporar e implementar cualquier aplicación](proxy-deployment-any-app.md).

    Una vez que se han implementado las aplicaciones, se supervisan en tiempo real, lo que le brinda información inmediata sobre sus actividades e información relacionada. Puede usar esta información para identificar comportamientos anómalos.

1. **Supervisión e investigación**: en Cloud App Security, use el [Registro de actividad](activity-filters.md) para supervisar y caracterizar el uso de la aplicación en el entorno y comprender sus riesgos. Puede restringir el ámbito de las actividades que se muestran mediante [búsqueda, filtros y consultas](activity-filters-queries.md) para identificar rápidamente las actividades de riesgo.

### <a name="phase-2-protect-your-data-when-its-exfiltrated"></a>Fase 2: Protección de los datos cuando se filtren

Una preocupación principal para muchas organizaciones es cómo evitar la filtración de datos antes de que se produzca. Dos de los mayores riesgos son los dispositivos no administrados (que pueden no estar protegidos con un PIN o pueden contener aplicaciones malintencionadas) y los usuarios invitados sobre los que el departamento de TI tiene poca visibilidad y control.

Ahora que las aplicaciones están implementadas, puede configurar fácilmente directivas para mitigar estos riesgos si aprovecha nuestras integraciones nativas con Microsoft Intune para la administración de dispositivos, con Azure AD para grupos de usuarios y Azure Information Protection para la protección de datos.

* **Mitigación de dispositivos no administrados**: cree una [directiva de sesión para etiquetar](session-policy-aad.md#create-a-cloud-app-security-session-policy) y proteger los archivos extremadamente confidenciales destinados únicamente a los usuarios de la organización.
* **Mitigación de los usuarios invitados**: cree una [directiva de sesión para aplicar permisos personalizados](session-policy-aad.md#protect-download) a cualquier archivo que descarguen los usuarios invitados. Por ejemplo, puede establecer permisos para que los usuarios invitados solo puedan acceder a un archivo protegido.

### <a name="phase-3-prevent-unprotected-data-from-being-uploaded-to-your-apps"></a>Fase 3: Impedir que se carguen datos no protegidos en las aplicaciones

Además de evitar la filtración de datos, las organizaciones suelen querer asegurarse de que los datos infiltrados en las aplicaciones en la nube también son seguros. Un caso de uso común es cuando un usuario intenta cargar archivos que no están etiquetados de forma correcta.

Para cualquiera de las aplicaciones que ha configurado antes, puede configurar una directiva de sesión para evitar la carga de archivos que no estén etiquetados de forma correcta, como se indica a continuación:

1. Cree una directiva de sesión para [bloquear las cargas de archivos etiquetados de forma incorrecta](session-policy-aad.md#protect-upload).

1. Configure una directiva para mostrar un [mensaje de bloqueo con instrucciones sobre cómo corregir la etiqueta e intentarlo de nuevo](session-policy-aad.md#educate-protect).

Este tipo de protección de las cargas de archivos garantiza que los datos guardados en la nube tengan aplicados los permisos de acceso correctos. En caso de que un archivo se comparta o se pierda, solo los usuarios autorizados podrán acceder a él.
