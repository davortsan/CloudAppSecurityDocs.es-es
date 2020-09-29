---
title: Detección y protección de la información confidencial de una organización
description: En este tutorial se describe el proceso para detectar y proteger la información confidencial en Microsoft Cloud App Security.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 05/26/2020
ms.topic: tutorial
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.suite: ems
ms.openlocfilehash: 4a75a256f8d4fa2e9483a153fce7ba1e1ab28376
ms.sourcegitcommit: 575f2b2efa9ca4477d7e60271d21e225ef2c38ea
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/22/2020
ms.locfileid: "90880936"
---
# <a name="tutorial-discover-and-protect-sensitive-information-in-your-organization"></a>Tutorial: Detección y protección de la información confidencial de una organización

[!INCLUDE [Banner for top of topics](includes/banner.md)]

En un mundo ideal, todos los empleados entienden la importancia de la protección de la información y trabajan dentro de las directivas. En el mundo real, es probable que un asociado ocupado que trabaja con frecuencia con información de cuentas cargue accidentalmente un documento confidencial en el repositorio de Box con permisos incorrectos. Al cabo de una semana, se da cuenta de que información confidencial de su empresa se ha filtrado a la competencia.

Para evitar que esto suceda, Microsoft Cloud App Security proporciona una amplia gama de funcionalidades de DLP que cubren los diversos puntos de fuga de datos que existen en las organizaciones.

En este tutorial, se proporciona información general e instrucciones para usar Cloud App Security para detectar datos confidenciales potencialmente expuestos y aplicar controles para evitar su exposición.

> [!div class="checklist"]
>
> * Detección de los datos
> * Clasificación de información confidencial
> * Proteger los datos
> * Supervisión e informes de los datos

## <a name="how-to-discover-and-protect-sensitive-information-in-your-organization"></a>Detección y protección de la información confidencial de la organización

El enfoque adoptado para la protección de la información se puede dividir en las siguientes fases, que le permiten proteger los datos durante su ciclo de vida completo, en varias ubicaciones y dispositivos.

![ciclo de vida de shadow IT](media/tutorial-dlp-solution.png)

### <a name="phase-1-discover-your-data"></a>Fase 1: Detección de los datos

1. **Conectar aplicaciones**: el primer paso para detectar qué datos se usan en la organización es conectar las aplicaciones en la nube que se usan en la organización a Cloud App Security. Una vez conectadas, Cloud App Security puede examinar datos, agregar clasificaciones y aplicar directivas y controles. La forma en que se conectan las aplicaciones afectará a cómo y cuándo se aplican las detecciones y los controles. Puede conectar las aplicaciones de alguna de las siguientes maneras:

    * **Usar un conector de aplicaciones**: los conectores de aplicaciones usan las API proporcionadas por los proveedores de aplicaciones. Proporcionan mayor visibilidad y control sobre las aplicaciones que se usan en la organización. Las detecciones se realizan periódicamente (cada 12 horas) y en tiempo real (se desencadena cada vez que se detecta un cambio). Para más información e instrucciones sobre cómo agregar aplicaciones, vea [Conectar aplicaciones](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md).
    * **Utilizar el Control de aplicaciones de acceso condicional**: la solución Control de aplicaciones de acceso condicional usa una arquitectura de proxy inverso que se integra de forma única con el acceso condicional de Azure Active Directory (AD). Una vez configurados en Azure AD, los usuarios se enrutarán a Cloud App Security donde se aplican las directivas de acceso y sesión para proteger los datos que las aplicaciones intentan usar. Este método de conexión permite aplicar controles a [cualquier aplicación](proxy-deployment-any-app.md). Para más información, vea [Proteger aplicaciones con el Control de aplicaciones de acceso condicional de Microsoft Cloud App Security](proxy-intro-aad.md).

1. **Investigar**: después de conectar una aplicación a Cloud App Security mediante su conector de API, Cloud App Security examina todos los archivos utilizados. A continuación, puede ir a la página de investigación de archivos (**Investigar** > **Archivos**) para obtener información general de los archivos compartidos por las aplicaciones en la nube, su accesibilidad y su estado. Para más información, vea [Investigar archivos](file-filters.md).

### <a name="phase-2-classify-sensitive-information"></a>Fase 2: Clasificación de información confidencial

1. **Definir qué información es confidencial**: antes de buscar información confidencial en los archivos, primero debe definir qué cuentas son confidenciales para su organización. Como parte del [servicio de clasificación de datos](dcs-inspection.md), se ofrecen más de 100 tipos de información confidencial predefinidos, o bien puede [crear el suyo propio](/microsoft-365/compliance/create-a-custom-sensitive-information-type) para adaptarse a la directiva de su empresa. **Cloud App Security se integra de forma nativa con Microsoft Information Protection** y los mismos tipos y etiquetas confidenciales están disponibles en ambos servicios. Por lo tanto, si desea definir información confidencial, diríjase al portal de Microsoft Information Protection para crearlos y, una vez definidos, estarán disponibles en Cloud App Security. También puede usar tipos de clasificaciones avanzadas como la huella digital o la coincidencia exacta de datos (EDM).

    Para aquellos que ya han realizado el trabajo duro de identificar información confidencial y de aplicar las etiquetas de confidencialidad adecuadas, puede usar esas etiquetas en las directivas sin tener que volver a examinar el contenido.
1. **Habilitar la integración de Azure Information Protection**
    1. En Cloud App Security, en el engranaje de configuración, seleccione la página **Configuración** en el encabezado **Sistema**.
    1. En **Azure Information Protection**, seleccione **Buscar automáticamente las etiquetas de clasificación de Azure Information Protection en los archivos nuevos**.

    Para más información, consulte [Integración de Azure Information Protection](azip-integration.md).
1. **Crear directivas para identificar información confidencial en archivos**: una vez que conozca los tipos de información que desea proteger, es el momento de crear directivas para detectarlos. Empiece por crear las siguientes directivas:

    **Directiva de archivo**  
    Use este tipo de directiva para examinar el contenido de los archivos almacenados en las aplicaciones en la nube conectadas a la API casi en tiempo real y los datos en reposo. Los archivos se examinan con uno de los métodos de inspección admitidos, como el **contenido cifrado con Azure Information Protection** gracias a su **integración nativa** con Cloud App Security.

    1. Vaya a **Control** > **Directivas**, haga clic en **Crear directiva** y, después, seleccione **Directiva de archivo**.
    1. En **Método de inspección**, elija y configure uno de los siguientes servicios de clasificación:

        * **[Servicios de clasificación de datos](dcs-inspection.md)** : se usan las decisiones de clasificación tomadas en Office 365, Azure Information Protection y Cloud App Security para proporcionar una experiencia de etiquetado unificada. Se trata del método de inspección de contenido preferido, ya que proporciona una experiencia coherente y unificada en todos los productos de Microsoft.
        * **[DLP integrado](content-inspection-built-in.md)** : se inspeccionan archivos en busca de información confidencial con el motor de inspección de contenido de DLP integrado.
        * **[Integración de DLP externa](icap-stunnel.md)** : en el caso de las empresas que desean usar sus propias soluciones DLP de terceros, las directivas de archivos de Cloud App Security pueden dirigir archivos de forma segura para su inspección a su solución DLP externa a través de un servidor ICAP.

    1. Si se trata de archivos muy confidenciales, seleccione **Crear una alerta** y elija las alertas que necesite, para que se le informe cuando haya archivos con información confidencial desprotegida en la organización.
    1. Haga clic en **Crear**.

    **Directiva de sesión**  
    Use este tipo de directiva para examinar y proteger el acceso a archivos en tiempo real para:

    * **Prevenir la filtración de datos**: se bloquean las opciones de descarga, corte, copia e impresión de documentos confidenciales en dispositivos no administrados, por ejemplo.
    * **Proteger archivos en la descarga**: se requiere que los documentos estén etiquetados y protegidos con Azure Information Protection. Esta acción garantiza que el documento está protegido y el acceso del usuario se restringe en una sesión potencialmente arriesgada.
    * **Evitar la carga de archivos sin etiqueta**: se requiere que un archivo tenga la etiqueta y la protección correctas antes de que otros carguen, distribuyan y usen un archivo confidencial. Con esta acción, puede asegurarse de que los archivos sin etiqueta con contenido confidencial estén bloqueados para que no se carguen hasta que el usuario clasifique el contenido.

    1. Vaya a **Control** > **Directivas**, haga clic en **Crear directiva** y, después, seleccione **Directiva de sesión**.
    1. En **Tipo de control de sesión**, elija una de las opciones con DLP.
    1. En **Método de inspección**, elija y configure uno de los siguientes servicios de clasificación:

        * **[Servicios de clasificación de datos](dcs-inspection.md)** : se usan las decisiones de clasificación tomadas en Office 365, Azure Information Protection y Cloud App Security para proporcionar una experiencia de etiquetado unificada. Se trata del método de inspección de contenido preferido, ya que proporciona una experiencia coherente y unificada en todos los productos de Microsoft.
        * **[DLP integrado](content-inspection-built-in.md)** : se inspeccionan archivos en busca de información confidencial con el motor de inspección de contenido de DLP integrado.

    1. Si se trata de archivos muy confidenciales, seleccione **Crear una alerta** y elija las alertas que necesite, para que se le informe cuando haya archivos con información confidencial desprotegida en la organización.
    1. Haga clic en **Crear**.

Debe crear tantas directivas como sea necesario para detectar datos confidenciales a fin de cumplir con la directiva de la empresa.

### <a name="phase-3-protect-your-data"></a>Fase 3: Proteger los datos

Por lo tanto, ahora puede detectar archivos con información confidencial, pero lo que realmente desea hacer es proteger esa información frente a posibles amenazas. Una vez que tenga constancia de algún incidente, puede corregir manualmente la situación o puede usar una de las acciones de gobernanza automática proporcionadas por Cloud App Security para proteger los archivos. Entre las acciones se incluyen los controles nativos de Azure Information Protection, las acciones proporcionadas por la API y la supervisión en tiempo real. El tipo de gobernanza que se puede aplicar depende del tipo de directiva que configure, como se indica a continuación:

1. **Acciones de [gobernanza de directivas de archivos](governance-actions.md#file-governance-actions)** : se usan la API del proveedor de aplicaciones en la nube y las integraciones nativas para proteger archivos. Entre tales acciones, se incluyen:
    * Desencadenar alertas y enviar notificaciones por correo electrónico sobre el incidente.
    * Administrar etiquetas aplicadas a un archivo para aplicar controles de Azure Information Protection nativos.
    * Cambiar el acceso compartido a un archivo.
    * Poner un archivo en cuarentena.
    * Quitar permisos específicos de archivos o carpetas en Office 365.
    * Enviar un archivo a la carpeta de la papelera.

1. **Controles de directivas de sesión**: se usan las funcionalidades del proxy inverso para proteger archivos. Entre ellas, se incluyen:
    * Desencadenar alertas y enviar notificaciones por correo electrónico sobre el incidente.
    * [Supervisar todas las actividades](session-policy-aad.md#monitor-session): permite explícitamente la descarga o carga de archivos y supervisa todas las actividades relacionadas.
    * [Bloquear](session-policy-aad.md#block-download): bloquea explícitamente la descarga o carga de archivos. Use esta opción para proteger los archivos confidenciales de su organización contra la filtración o la infiltración desde cualquier dispositivo, incluidos los dispositivos no administrados.
    * [Proteger](session-policy-aad.md#protect-download): aplica automáticamente una etiqueta de clasificación a los archivos que coinciden con los filtros de archivos de la directiva. Use esta opción para proteger la descarga de archivos confidenciales.

### <a name="phase-4-monitor-and-report-on-your-data"></a>Fase 4: Supervisión e informes de los datos

Las directivas están diseñadas para inspeccionar y proteger los datos. Ahora, deberá [comprobar el panel](daily-activities-to-protect-your-cloud-environment.md#check-the-dashboard) diariamente para ver qué nuevas alertas se han activado. Es un buen lugar para vigilar el estado del entorno en la nube. El panel le ayudará a tener una idea de lo que está ocurriendo y, si es necesario, iniciar una [investigación](investigate.md).

Una de las formas más efectivas de supervisar los incidentes con los archivos confidenciales es consultar la página **Directivas** y revisar las coincidencias con las directivas configuradas. Además, si ha configurado las alertas, también debe considerar la opción de supervisar periódicamente las alertas de archivos en la página **Alertas**, especificando la categoría como **DLP** y revisando qué directivas relacionadas con los archivos se van a activar. Revisar estos incidentes puede ayudarle a ajustar las directivas para que se centren en las amenazas que son de interés para la organización.

En conclusión, administrar de esta forma la información confidencial garantiza que los datos que se guardan en la nube tienen la máxima protección contra la filtración e infiltración malintencionadas. Además, en caso de que un archivo se comparta o se pierda, solo los usuarios autorizados podrán acceder a él.

## <a name="see-also"></a>Consulte también

> [!div class="nextstepaction"]
> [Descripción de los filtros y datos de archivos](file-filters.md)

> [!div class="nextstepaction"]
> [Directivas de archivos](data-protection-policies.md)

> [!div class="nextstepaction"]
> [Inspección de contenido](content-inspection.md)

> [!div class="nextstepaction"]
> [Actividades diarias para proteger el entorno de nube](daily-activities-to-protect-your-cloud-environment.md)

[!INCLUDE [Open support ticket](includes/support.md)]  
