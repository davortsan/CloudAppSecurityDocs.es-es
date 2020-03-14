---
title: Control del uso de aplicaciones en la nube mediante la creación de directivas-Cloud App Security | Microsoft Docs
description: En este artículo se proporciona información sobre cómo se usan las directivas y cómo se configuran para controlar el uso de aplicaciones en la nube.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 09/26/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: e4675430b45e92579cd4c692247c5a481bad233e
ms.sourcegitcommit: 4f3883a9e85d0aaf2802b10433b221c3f1838d88
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/13/2020
ms.locfileid: "79285619"
---
# <a name="control-cloud-apps-with-policies"></a>Control de aplicaciones en la nube con directivas

*Se aplica a: Microsoft Cloud App Security*

Las directivas le permiten definir la forma en que desea que los usuarios se comporten en la nube. Permiten detectar comportamientos de riesgo, infracciones o puntos de datos y actividades sospechosos en el entorno de nube. Si es necesario, puede integrar los flujos de trabajo de corrección para lograr una mitigación de riesgos completa. Hay varios tipos de directivas que se correlacionan con los diferentes tipos de información que quiere recopilar sobre el entorno de nube y los tipos de acciones correctivas que puede querer realizar.

Por ejemplo, si hay una amenaza de infracción de datos que quiere poner en cuarentena, necesitará un tipo de directiva diferente que si desea bloquear la utilización de una aplicación en la nube arriesgada por su organización.

## <a name="policy-types"></a>Tipos de directivas

Al mirar la página **Directiva** , se pueden distinguir las distintas directivas y plantillas por tipo e icono para ver qué directivas están disponibles. Las directivas disponibles dependen del origen de datos y de lo que se haya habilitado en Cloud App Security para su organización. Por ejemplo, si cargó Cloud Discovery registros, se mostrarán las directivas relacionadas con Cloud Discovery.

Se pueden crear los siguientes tipos de directivas:

|Icono de tipo de Directiva|Tipo de directiva|Uso|
|-----|-----------------|---------|
|![icono de directiva de acceso](media/proxy-policy.png)|Directiva de acceso|Las directivas de acceso proporcionan supervisión y control en tiempo real de los inicios de sesión de los usuarios a las aplicaciones en la nube.|
|![icono de directiva de actividad](media/activity_policy.png)|Directiva de actividad|Las directivas de actividad permiten aplicar una amplia gama de procesos automatizados mediante las API del proveedor de la aplicación. Estas directivas permiten supervisar actividades específicas realizadas por varios usuarios o seguir tasas inesperadamente altas de un determinado tipo de actividad.|
|![icono de directiva de detección de anomalías](media/anomaly_detection_policy.png)|Directiva de detección de anomalías|Las directivas de detección de anomalías permiten buscar actividades inusuales en la nube. La detección se basa en los factores de riesgo que se establecen para avisarle cuando ocurre algo diferente de la línea de base de la organización o de la actividad normal del usuario.|
|![icono de directiva de Cloud Discovery](media/discovery_policy.png)|Directiva de detección de aplicaciones|Las directivas de detección de aplicaciones permiten establecer alertas que le notifican cuando se detectan nuevas aplicaciones en la organización.|
|![icono de directiva de detección de anomalías](media/anomaly_detection_policy.png)|Directiva de detección de anomalías de Cloud Discovery|Cloud Discovery las directivas de detección de anomalías examinan los registros que se usan para detectar aplicaciones en la nube y buscan apariciones inusuales. Por ejemplo, cuando un usuario que nunca ha usado Dropbox antes carga de repente 600 GB en Dropbox, o cuando hay muchas más transacciones de lo habitual en una aplicación determinada.|
|![icono de directiva de archivo](media/file_policy.png)|Directiva de archivo|Las directivas de archivo permiten analizar las aplicaciones en la nube para buscar archivos o tipos de archivo especificados (compartidos, compartidos con dominios externos), datos (información de propiedad, datos personales, información de la tarjeta de crédito y otros tipos de datos) y aplicar acciones de gobierno a los archivos ( las acciones de gobierno son específicas de la aplicación de nube).|
|![icono de directiva de sesión](media/proxy-policy.png)|Directiva de sesión|Las directivas de sesión proporcionan supervisión y control en tiempo real sobre la actividad de los usuarios en las aplicaciones en la nube.|

## <a name="identifying-risk"></a>Identificación de riesgos

Cloud App Security ayuda a mitigar los distintos riesgos en la nube. Puede configurar cualquier directiva y alerta para que se asocie a uno de los siguientes riesgos:

- **Control de acceso:** ¿Quién accede a qué desde dónde?

    Supervise continuamente el comportamiento y detecte actividades anómalas, incluidos los ataques externos y de Insider de alto riesgo, y aplique una directiva para alertar, bloquear o requerir verificación de identidad para cualquier aplicación o acción específica dentro de una aplicación. Habilita directivas de control de acceso local y móvil basadas en el usuario, el dispositivo y la geografía con bloqueo general y vista, edición y bloqueo pormenorizados. Detectar eventos de inicio de sesión sospechosos, incluidos errores de autenticación multifactor, errores de inicio de sesión de cuenta deshabilitados y eventos de suplantación.

- **Cumplimiento:** ¿Se infringen los requisitos de cumplimiento?

    Catalogar e identificar datos confidenciales o regulados, incluidos los permisos de uso compartido de cada archivo, almacenados en servicios de sincronización de archivos para garantizar el cumplimiento de normas como PCI, SOX e HIPAA

- **Control de configuración:** ¿Se están realizando cambios no autorizados en la configuración?

    Supervise los cambios de configuración, incluida la manipulación de la configuración remota.

- **Cloud Discovery:** ¿Se están usando nuevas aplicaciones en la organización? ¿Tiene un problema de uso de aplicaciones de TI en las que no conoce?

    Valore el riesgo general de cada aplicación en la nube en función de las certificaciones normativas y del sector, y los procedimientos recomendados. Permite supervisar el número de usuarios, actividades, volumen de tráfico y horas de uso típicas de cada aplicación en la nube.

- **DLP:** ¿Se están compartiendo públicamente archivos de propiedad? ¿Necesita poner archivos en cuarentena?

    La integración DLP local proporciona integración y corrección de bucle cerrado con soluciones DLP locales existentes.

- **Cuentas con privilegios:** ¿Necesita supervisar las cuentas de administrador?

    Supervisión de la actividad en tiempo real e informes de usuarios con privilegios y administradores.

- **Control de uso compartido:** ¿Cómo se comparten los datos en el entorno de nube?

    Inspeccione el contenido de los archivos y el contenido en la nube y aplique directivas de uso compartido internas y externas. Supervise la colaboración y aplique directivas de uso compartido, como el bloqueo de archivos para que no se compartan fuera de la organización.

- **Detección de amenazas:** ¿Existen actividades sospechosas que pongan en peligro su entorno de nube?

    Reciba notificaciones en tiempo real de cualquier infracción de la Directiva o de umbral de actividad a través de mensajes de texto o correo electrónico. Mediante la aplicación de algoritmos de aprendizaje automático, Cloud App Security le permite detectar comportamientos que podrían indicar que un usuario está utilizando datos inutilizables.

## <a name="how-to-control-risk"></a>Control del riesgo

Siga este proceso para controlar el riesgo con directivas:

1. Cree una directiva a partir de una plantilla o una consulta.

1. Ajuste la Directiva para lograr los resultados esperados.

1. Agregue acciones automatizadas para responder a los riesgos y corregirlos automáticamente.

### <a name="create-a-policy"></a>Creación de una directiva

Puede usar las plantillas de directiva de Cloud App Security como base para todas las directivas o crear directivas a partir de una consulta.

Las plantillas de directiva ayudan a establecer los filtros correctos y las configuraciones necesarias para detectar eventos específicos de interés en el entorno. Las plantillas incluyen directivas de todos los tipos y se pueden aplicar a varios servicios.

Para crear una directiva a partir de **plantillas de directiva**, realice los pasos siguientes:

1. En la consola de, haga clic en **control** y luego en **plantillas**.

    ![Crear la Directiva a partir de una plantilla](media/create-policy-from-template.png)

1. Haga clic en el **+** en el extremo derecho de la fila de la plantilla que desea usar. Se abre una página crear Directiva, con la configuración predefinida de la plantilla.

1. Modifique la plantilla según sea necesario para la directiva personalizada. Cada propiedad y campo de esta nueva directiva basada en plantilla se puede modificar según sus necesidades.
   > [!NOTE]
   > Al usar los filtros de Directiva, **contiene** solo búsquedas de palabras completas separadas por comass, puntos, espacios o guiones bajos. Por ejemplo, si busca **malware** o **virus**, busca virus_malware_file. exe, pero no encuentra malwarevirusfile. exe. Si busca *malware. exe*, encontrará todos los archivos con malware o exe en el nombre de archivo, mientras que si busca **"malware. exe"** (con comillas) solo encontrará los archivos que contengan exactamente "malware. exe".  
**Equals** busca solo la cadena completa, por ejemplo, si busca malware. *exe* , encontrará malware. exe pero no malware. exe. txt.

1. Después de crear la nueva directiva basada en plantilla, aparece un vínculo a la nueva Directiva en la columna **directivas vinculadas** de la tabla plantilla de directivas junto a la plantilla desde la que se creó la Directiva.
    Puede crear tantas directivas como desee de cada plantilla y se vinculen a la plantilla original. La vinculación permite realizar el seguimiento de todas las directivas compiladas con la misma plantilla.

Como alternativa, puede **crear una directiva durante la investigación**. Si está investigando el **registro de actividad**, **los archivos** o **las cuentas**y profundiza en la búsqueda de algo específico, en cualquier momento puede crear una nueva directiva basada en los resultados de la investigación.

Por ejemplo, si está examinando el **registro de actividades**y ve una actividad de administrador desde fuera de las direcciones IP de su oficina.

Para crear una directiva basada en los resultados de la investigación, realice los pasos siguientes:

1. En la consola de, haga clic en **investigar** y, a continuación, en **registro de actividades**, **archivos**o **cuentas**.

1. Utilice los filtros en la parte superior de la página para limitar los resultados de la búsqueda al área sospechosa. Por ejemplo, en la página Registro de actividad, haga clic en **tipo de actividad** y seleccione **escribir administradores** en operación de Azure. A continuación, en **dirección IP**, seleccione **categoría** y establezca el valor para que no incluya categorías de dirección IP que haya creado para los dominios reconocidos, como las direcciones IP de administrador, corporativas y VPN.

    ![Crear archivo a partir de una investigación](media/create-file-from-investigation.png)

1. En la esquina superior derecha de la consola, haga clic en **nueva Directiva en la búsqueda**.

    ![Botón nueva Directiva de búsqueda](media/new-policy-from-search-button.png)

1. Se abre una página Crear directiva que contiene los filtros usados en la investigación.

1. Modifique la plantilla según sea necesario para la directiva personalizada. Cada propiedad y campo de esta nueva directiva basada en investigación se puede modificar según sus necesidades.

    > [!NOTE]
    > Al usar los filtros de Directiva, **contiene** solo búsquedas de palabras completas separadas por comass, puntos, espacios o guiones bajos. Por ejemplo, si busca **malware** o **virus**, busca virus_malware_file. exe, pero no encuentra malwarevirusfile. exe.  
**Equals** busca solo la cadena completa, por ejemplo, si busca malware. **exe** , encontrará malware. exe pero no malware. exe. txt.

    ![crear Directiva de actividad a partir de una investigación](media/create-activity-policy-from-investigation.png)

    > [!NOTE]
    > Para obtener más información sobre cómo establecer los campos de la Directiva, consulte la documentación de la directiva correspondiente:
    >
    > [Directivas de actividad de usuario](user-activity-policies.md)
    >
    > [Directivas de protección de datos](data-protection-policies.md)
    >
    > [Directivas de Cloud Discovery](cloud-discovery-policies.md)

### <a name="add-automated-actions-to-respond-and-remediate-risks-automatically"></a>Agregar acciones automatizadas para responder a los riesgos y corregirlos automáticamente

Para obtener una lista de las acciones de gobierno disponibles por aplicación, consulte [control de aplicaciones conectadas](governance-actions.md).

También puede establecer la Directiva para que le envíe una alerta por correo electrónico o mensaje de texto cuando se detecten coincidencias.

Para establecer las preferencias de notificación, tenga que [personalizar el portal](general-setup.md)

> [!NOTE]
> El número máximo de alertas enviadas a través de mensajes de texto es de 10 por número de teléfono al día. El día se calcula según la zona horaria UTC.

## <a name="enable-and-disable-policies"></a>Habilitar y deshabilitar directivas

Después de crear una directiva, puede habilitarla o deshabilitarla. La deshabilitación evita la necesidad de eliminar una directiva después de crearla para detenerla. En su lugar, si por algún motivo desea detener la Directiva, deshabilítela hasta que decida volver a habilitarla.

- Para habilitar una directiva, en la página **Directiva** , haga clic en los tres puntos al final de la fila de la Directiva que desea habilitar. Seleccione **Habilitar**.

    ![Habilitar Directiva](media/enable-policy.png)

- Para deshabilitar una directiva, en la página **Directiva** , haga clic en los tres puntos al final de la fila de la Directiva que desea deshabilitar. Seleccione **deshabilitar**.

    ![Deshabilitar Directiva](media/disable-policy.png)

De forma predeterminada, después de crear una nueva Directiva, está habilitada.

## <a name="policies-overview-report"></a>Informe información general sobre directivas

Cloud App Security le permite exportar un informe de información general de directivas que muestra métricas de alertas agregadas por directiva para ayudarle a supervisar, comprender y personalizar las directivas para proteger mejor su organización.

Para exportar un registro, realice los pasos siguientes:

1. En la página **directivas** , haga clic en el botón **exportar** .

1. Especifique el intervalo de tiempo necesario.

1. Haga clic en **Exportar**. Este proceso puede tardar algún tiempo.

Para descargar el informe exportado:

1. Cuando el informe esté listo, vaya a **configuración** y después a **informes exportados**.

1. En la tabla, seleccione el informe correspondiente en el **Informe información general** de la lista de directivas y haga clic en descargar.

    ![botón Descargar](media/download-button.png)

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Actividades diarias para proteger el entorno de nube](daily-activities-to-protect-your-cloud-environment.md)

[!INCLUDE [Open support ticket](includes/support.md)]
