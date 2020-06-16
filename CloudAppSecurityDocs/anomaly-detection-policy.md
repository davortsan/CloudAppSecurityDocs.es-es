---
title: Creación de directivas de detección de anomalías en Cloud App Security
description: En este artículo se proporciona una descripción de las directivas de detección de anomalías, así como información de referencia sobre los bloques de creación de una directiva de detección de anomalías.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 03/24/2020
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 85cf523e8cc733156c2365da114cc893b022e1e3
ms.sourcegitcommit: 223c9e4cefe6986537dcfbd697a236a3cee1768c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/16/2020
ms.locfileid: "84801157"
---
# <a name="get-instantaneous-behavioral-analytics-and-anomaly-detection"></a>Obtención de análisis de comportamiento y detección de anomalías instantáneos

*Se aplica a: Microsoft Cloud App Security*

Las directivas de detección de anomalías de Microsoft Cloud App Security ofrecen análisis de comportamiento de usuarios y entidades (UEBA) y aprendizaje automático (ML) de serie para que pueda ejecutar inmediatamente la detección de amenazas avanzada en el entorno en la nube. Dado que se habilitan automáticamente, las nuevas directivas de detección de anomalías ofrecen resultados al instante proporcionando detecciones inmediatas, dirigidas a numerosas anomalías de comportamientos entre los usuarios, las máquinas y los dispositivos conectados a la red.  Además, las nuevas directivas exponen más datos del motor de detección de Cloud App Security para ayudarle a acelerar el proceso de investigación e incluir amenazas en curso.

Las directivas de detección de anomalías se habilitan automáticamente, pero Cloud App Security tiene un período de aprendizaje inicial de siete días durante el cual no todas las alertas de detección de anomalías se generan. Después de ese período, cada sesión se compara con la actividad, cuándo los usuarios estaban activos, las direcciones IP, los dispositivos, etc. que se detectaron durante el mes pasado y la puntuación de riesgo de estas actividades.  Estas detecciones forman parte del motor de detección de anomalías heurísticos que genera perfiles de su entorno y desencadena alertas con respecto a una línea base que se aprendió en la actividad de su organización. Estas detecciones también usan algoritmos de aprendizaje automático diseñados para generar perfiles de los usuarios y el patrón de inicio de sesión para reducir los falsos positivos.

Las anomalías se detectan mediante el examen de la actividad del usuario. El riesgo se evalúa mediante el análisis de más de 30 indicadores de riesgo distintos, agrupados por factores de riesgo, que son los siguientes:

* Dirección IP de riesgo
* Errores de inicio de sesión
* Actividad administrativa
* Cuentas inactivas
* Location
* Viaje imposible
* Agente de usuario y dispositivo
* Tasa de actividad

Basándose en los resultados de la directiva, se activan alertas de seguridad. Cloud App Security examina todas las sesiones de los usuarios en la nube y le alerta cuando ocurre algo que es diferente a la línea base de la organización o de la actividad normal del usuario.

Además de las alertas nativas de Cloud App Security, también obtendrá las siguientes alertas de detección basadas en la información recibida de Azure Active Directory (AD) Identity Protection:

* Credenciales perdidas: se desencadena cuando se han perdido las credenciales válidas de un usuario. Para obtener más información, vea [detección de credenciales perdidas de Azure ad](/azure/active-directory/identity-protection/concept-identity-protection-risks#user-risk).
* Inicio de sesión peligroso: combina un número de detecciones de inicio de sesión Azure AD Identity Protection en una sola detección. Para obtener más información, consulte [el Azure ad de las detecciones de riesgo de inicio de sesión](/azure/active-directory/identity-protection/concept-identity-protection-risks#sign-in-risk).

Estas directivas aparecerán en la página directivas de Cloud App Security y se pueden habilitar o deshabilitar.

## <a name="anomaly-detection-policies"></a>Directivas de detección de anomalías

Puede ver las directivas de detección de anomalías en el portal haciendo clic en **Control** y luego en **Directivas**. Seleccione **Directiva de detección de anomalías** para el tipo de directiva.

 ![nuevas directivas de detección de anomalías](media/new-anomaly-detection-policies.png)

Están disponibles las directivas de detección de anomalías siguientes:

### <a name="impossible-travel"></a>Viaje imposible

* Esta detección identifica dos actividades de usuario (en una o varias sesiones) que se originan desde ubicaciones geográficamente distantes dentro de un período de tiempo menor que el tiempo que habría tardado el usuario para viajar de la primera ubicación a la segunda, lo que indica que otro usuario está usando las mismas credenciales. Esta detección usa un algoritmo de aprendizaje automático que omite falsos positivos obvios que contribuyan a la condición de viaje imposible, como las redes privadas virtuales y las ubicaciones que otros usuarios de la organización usen con frecuencia. La detección tiene un período de aprendizaje inicial de siete días durante el cual aprende el patrón de actividad de un usuario nuevo. La detección de viaje imposible identifica actividad inusual e imposible de usuario entre dos ubicaciones. La actividad debe ser lo suficientemente inusual como para ser considerada un indicador de peligro y digna de una alerta. Para solucionar este problema, la lógica de detección incluye diferentes niveles de supresión para abordar escenarios que pueden desencadenar falsos positivos, como las actividades de VPN. El control deslizante de sensibilidad permite cambiar el algoritmo y definir cuán estricta es la lógica de detección. Cuanto mayor sea el nivel de confidencialidad, menor será la supresión que se aplica como parte de la lógica de detección. De este modo, puede adaptar la detección según sus necesidades de cobertura y destinos SNR.

    > [!NOTE]
    > Cuando las direcciones IP de ambos lados del viaje se consideran seguras, el viaje es de confianza y se excluye de desencadenar la detección de viajes imposibles. Por ejemplo, ambos lados se consideran seguros si se [etiquetan como corporativos](ip-tags.md). Sin embargo, si la dirección IP de un solo lado del viaje se considera segura, la detección se desencadena como normal.

### <a name="activity-from-infrequent-country"></a>Actividad desde un país poco frecuente

* Esta detección tiene en cuenta las ubicaciones de actividad anteriores para determinar las ubicaciones nuevas e infrecuentes. El motor de detección de anomalías almacena información sobre las ubicaciones anteriores utilizadas por los usuarios de la organización. Se desencadena una alerta cuando se produce una actividad desde una ubicación que ningún usuario de la organización ha visitado recientemente o nunca.

### <a name="malware-detection"></a>Detección de malware

* Esta detección identifica los archivos maliciosos en el almacenamiento en nube, tanto si proceden de aplicaciones de Microsoft como de aplicaciones de terceros. Microsoft Cloud App Security usa la inteligencia sobre amenazas de Microsoft para reconocer si determinados archivos están asociados a ataques de malware conocidos y son potencialmente maliciosos. Esta directiva integrada está deshabilitada de forma predeterminada. No se analizan todos los archivos, pero se usa la heurística para buscar archivos potencialmente peligrosos. Una vez que se han detectado archivos, puede ver una lista de **archivos infectados**. Haga clic en el nombre del archivo de malware en el cajón de archivos para abrir un informe de malware que le proporcione información sobre el tipo de malware con el que está infectado el archivo.

    Puede usar esta detección en tiempo real mediante directivas de sesión para controlar las cargas y descargas de archivos.

    > [!NOTE]
    >
    > * Para la detección de malware de Office 365, necesita una licencia válida para la protección contra amenazas avanzada de Office 365 P1.
    > * Cloud App Security admite la detección de malware en las siguientes aplicaciones:
    >   * Box
    >   * Dropbox
    >   * G Suite
    >   * Office 365

### <a name="activity-from-anonymous-ip-addresses"></a>Actividad desde direcciones IP anónimas

* Esta detección identifica que los usuarios estaban activos desde una dirección IP que se ha identificado como una dirección IP de proxy anónima. Estos servidores proxy los usan las personas que desean ocultar la dirección IP de su dispositivo y se pueden usar para fines malintencionados. Esta detección usa un algoritmo de aprendizaje automático que reduce los falsos positivos, como las direcciones IP no etiquetadas que los usuarios de la organización usan habitualmente.

### <a name="ransomware-activity"></a>Actividad de ransomware

* Cloud App Security amplió sus funcionalidades de detección de ransomware con la detección de anomalías para garantizar una cobertura más completa frente a los ataques sofisticados de ransomware. Al usar nuestra experiencia en investigación de seguridad para identificar patrones de comportamiento que reflejan la actividad de ransomware, Cloud App Security garantiza una protección holística y sólida. Puede que represente un proceso de cifrado adverso si Cloud App Security identifica, por ejemplo, una alta tasa de cargas de archivos o de actividades de eliminación de archivos. Estos datos se recopilan en los registros procedentes de las API conectadas y luego se combinan con los patrones de comportamiento aprendidos y la inteligencia sobre amenazas, por ejemplo, extensiones de ransomware conocidas. Para obtener más información sobre cómo Cloud App Security detecta ransomware, vea [Proteger la organización frente a ransomware](use-case-ransomware.md).

### <a name="activity-performed-by-terminated-user"></a>Actividad realizada por el usuario cancelado

* Esta detección le permite identificar cuando un empleado que ya no trabaja en la compañía sigue realizando acciones en las aplicaciones SaaS. Dado que los datos muestran que el mayor riesgo de una amenaza interna procede de empleados que se fueron en malos términos, es importante estar atento a la actividad en las cuentas de empleados dados de baja. A veces, cuando los empleados dejan una compañía, sus cuentas se desaprovisionan de las aplicaciones corporativas, pero en muchos casos sigue conservando el acceso a determinados recursos corporativos. Esto es incluso más importante si se tienen en cuenta las cuentas con privilegios, ya que el daño potencial que un ex administrador puede infligir es intrínsecamente mayor.
Esta detección aprovecha las ventajas de capacidad de Cloud App Security para supervisar el comportamiento de usuario entre las aplicaciones, lo que permite la identificación de la actividad normal del usuario, el hecho de que la cuenta se ha cerrado y la actividad real en otras aplicaciones. Por ejemplo, un empleado que es Azure AD cuenta se ha terminado pero todavía tiene acceso a la infraestructura de AWS corporativa, tiene la posibilidad de producir daños a gran escala.

La detección busca los usuarios cuya cuenta de Azure AD ha quedado suspendida, pero siguen realizando actividades en otras plataformas, como AWS o Salesforce. Esto es especialmente pertinente para los usuarios que usen otra cuenta (distinta al inicio de sesión único principal) para administrar los recursos, ya que a menudo estas cuentas no se suspenden cuando el usuario deja la empresa.

### <a name="activity-from-suspicious-ip-addresses"></a>Actividad desde direcciones IP sospechosas

* Se identifica la actividad de los usuarios desde una dirección IP considerada como de riesgo en Microsoft Threat Intelligence. Estas direcciones IP están implicadas en actividades malintencionadas como Botnet C&C y pueden indicar que la cuenta está en peligro. Esta detección usa un algoritmo de aprendizaje automático que reduce los falsos positivos, como las direcciones IP no etiquetadas que los usuarios de la organización usan habitualmente.

### <a name="suspicious-inbox-forwarding"></a>Reenvío sospechoso desde la bandeja de entrada

* Esta detección busca reglas de reenvío de correo electrónico sospechosas, por ejemplo, si un usuario creó una regla de bandeja de entrada que reenvía una copia de todos los correos electrónicos a una dirección externa.

> [!NOTE]
> Cloud App Security le avisa solo para cada regla de reenvío que se identifica como sospechosa, en función del comportamiento típico para el usuario.

### <a name="suspicious-inbox-manipulation-rules"></a>Reglas de manipulación sospechosa de la bandeja de entrada

* Esta detección genera un perfil del entorno y activa alertas cuando se establecen reglas sospechosas que eliminan o mueven mensajes o carpetas en la bandeja de entrada de un usuario. Esto puede indicar que la cuenta del usuario está en peligro, que los mensajes se están ocultando de manera intencionada o que el buzón se está usando para enviar correo no deseado y malware en la organización.

### <a name="suspicious-email-deletion-activity-preview"></a>Actividad de eliminación de correos electrónicos sospechosos (versión preliminar)

* Esta directiva genera perfiles de su entorno y desencadena alertas cuando un usuario realiza actividades de eliminación de correo electrónico sospechosas en una sola sesión. Esta Directiva puede indicar que los buzones de usuario pueden estar en peligro por posibles vectores de ataque, como la comunicación de comando y control (C&C/C2) por correo electrónico.

### <a name="unusual-activities-by-user"></a>Actividades inusuales (realizadas por un usuario)

Estas detecciones identifican a los usuarios que realizan:

* Varias actividades inusuales de descarga de archivos
* Actividades inusuales de uso compartido de archivos
* Actividades inusuales de eliminación de archivos
* Actividades inusuales de suplantación
* Actividades inusuales administrativas
* Actividades inusuales de uso compartido de informes de Power BI (versión preliminar)
* Actividades de creación de varias máquinas virtuales inusuales (versión preliminar)
* Actividades inusuales de eliminación de almacenamiento múltiple (versión preliminar)
* Región inusual para el recurso de nube (versión preliminar)

Estas directivas buscan actividades dentro de una única sesión según la línea base establecida, lo que podría indicar un intento de vulneración. Estas detecciones aprovechan un algoritmo de aprendizaje automático que crea perfiles a partir del patrón de inicio de sesión de los usuarios y reduce los falsos positivos. Estas detecciones forman parte del motor de detección de anomalías heurísticos que genera perfiles de su entorno y desencadena alertas con respecto a una línea base que se aprendió en la actividad de su organización.

### <a name="multiple-failed-login-attempts"></a>Varios intentos incorrectos de inicio de sesión

* Se identifica a los usuarios que intentan iniciar sesión varias veces sin éxito en una única sesión según la línea base establecida, lo que podría indicar un intento de vulneración.

### <a name="data-exfiltration-to-unsanctioned-apps"></a>Filtración de datos a aplicaciones no autorizadas

* Esta directiva se habilita automáticamente para enviarle una alerta cada vez que un usuario o una dirección IP usan una aplicación que no tiene permitido realizar una actividad que parezca un intento de filtrar información de la organización.

### <a name="multiple-delete-vm-activities"></a>Varias actividades de eliminación de VM

* Esta directiva crea un perfil del entorno y activa alertas cuando los usuarios eliminan varias máquinas virtuales en una única sesión, en relación con la línea base de la organización. Esto podría indicar un intento de infracción de seguridad.

## <a name="enable-automated-governance"></a>Habilitación de la gobernanza automatizada<a name="adp-automated-gov"></a>

Puede habilitar acciones de corrección automatizadas en las alertas generadas por directivas de detección de anomalías.

1. Haga clic en el nombre de la directiva de detección en la página **Directiva**.
1. En la ventana **Editar directiva de detección de anomalías** que se abre, en **Gobernanza**, establezca las acciones de corrección que quiera para cada aplicación conectada o para todas las aplicaciones.
1. Haga clic en **Actualizar**.

## <a name="tune-anomaly-detection-policies"></a>Ajuste de directivas de detección de anomalías

Para influir en el motor de detección de anomalías con el fin de suprimir o exponer alertas de acuerdo con sus preferencias, haga lo siguiente:

* En la directiva de viaje imposible, puede establecer el control deslizante de sensibilidad para determinar el nivel de comportamiento anómalo necesario antes de que se desencadene una alerta. Por ejemplo, si se establece en Low, se suprimirán las alertas de viaje imposibles de las ubicaciones comunes de un usuario y, si se establece en alto, se mostrarán dichas alertas. Puede elegir entre los niveles de sensibilidad siguientes:

  * **Bajo**: suprimes del sistema, del inquilino y del usuario
  * **Media**: supresiones del usuario y el sistema
  * **Alta**: solo supresiones del sistema

    Donde:

    | Tipo de supresión | Descripción |
    | --- | --- |
    | **Sistema** | Detecciones integradas que siempre se suprimen. |
    | **Inquilino** | Actividades comunes basadas en la actividad anterior del inquilino. Por ejemplo, la supresión de actividades de un ISP sobre el que se alertó anteriormente en la organización. |
    | **Usuario** | Actividades comunes basadas en la actividad anterior del usuario específico. Por ejemplo, la supresión de actividades de una ubicación que suele utilizar el usuario. |

* También puede configurar si las alertas de actividad de un país o región poco frecuente, direcciones IP anónimas, direcciones IP sospechosas y viajes imposibles deben analizar tanto inicios de sesión con errores como correctos o simplemente inicios de sesión correctos.

> [!NOTE]
> De forma predeterminada, los protocolos de inicio de sesión heredados, como los que no usan la autenticación multifactor (por ejemplo, WS-Trust), no se supervisan con la Directiva de viajes imposibles. Si su organización usa protocolos heredados, para evitar que falten actividades relevantes, edite la Directiva y, en **Configuración avanzada**, establezca **analizar las actividades de inicio de sesión** en **todos los inicios de sesión**.

## <a name="scope-anomaly-detection-policies"></a>Ámbito de directivas de detección de anomalías

Se puede establecer un ámbito para cada directiva de detección de anomalías por separado para que se aplique solo a los usuarios y grupos que desea incluir y excluir en la directiva.
Por ejemplo, puede establecer la actividad a partir de la detección de condados poco frecuentes para omitir un usuario específico que viaja de forma habitual.

Para establecer el ámbito de una directiva de detección de anomalías:

1. Haga **Control**clic en  >  **directivas**de control y establezca el filtro de **tipo** en **Directiva de detección de anomalías**.
1. Haga clic en la directiva cuyo ámbito desea establecer.
1. En **Ámbito**, cambie la lista desplegable de la configuración predeterminada de **Todos los usuarios y grupos** a **Usuarios y grupos específicos**.
1. Seleccione **Incluir** para especificar los usuarios y grupos para los que se aplicará esta directiva. Cualquier usuario o grupo que no se seleccione aquí no se considerará una amenaza y no generará una alerta.
1. Seleccione **Excluir** para especificar los usuarios para los que no se aplicará esta directiva. Cualquier usuario que seleccione aquí no se considerará una amenaza y no generará una alerta, incluso si es miembro de los grupos seleccionados en **Incluir**.

    ![ámbito de detección de anomalías](media/anomaly-detection-scoping.png)

## <a name="triage-anomaly-detection-alerts"></a>Evaluación de las alertas de detección de anomalías

Puede evaluar la prioridad de las diversas alertas desencadenadas por las nuevas directivas de detección de anomalías rápidamente y decidir cuáles es necesario atender primero. Para ello, necesita el contexto de la alerta, de forma que pueda ver la imagen más grande y comprender si realmente está ocurriendo algo malintencionado.

1. En el **registro de actividades**, puede abrir una actividad para mostrar el cajón de actividades. Haga clic en **usuario** para ver la pestaña información de usuario. Esta pestaña incluye información como el número de alertas, las actividades y el lugar desde el que se han conectado, lo que es importante en una investigación.

    ![detección de anomalías alert1 ](media/anomaly-alert-user1.png) ![ detección de anomalías alert1](media/anomaly-alert-user2.png)

1. Esto le permite comprender qué actividades sospechosas realizó el usuario y aumentar la confianza en cuanto a si la cuenta se vio comprometida. Por ejemplo, una alerta sobre varios inicios de sesión erróneos realmente puede ser sospechosa y puede indicar posibles ataques por fuerza bruta, pero también puede ser un error de configuración de aplicación, haciendo que la alerta resulte ser verdadera. Sin embargo, si ve una alerta de varios inicios de sesión erróneos con actividades sospechosas adicionales, entonces hay una mayor probabilidad de que la cuenta se vea comprometida. En el ejemplo siguiente, puede ver que, después de la alerta de los **diversos intentos de inicio de sesión erróneos**, hubo **actividad desde una dirección IP TOR** y **actividad de viaje imposible**, ambas buenos indicadores de riesgo (IOC) por sí mismas. Si esto no era lo suficientemente sospechoso, puede ver que el mismo usuario realizó una **actividad de descarga masiva**, que suele ser un indicador del atacante que realiza la exfiltración de datos.

    ![alerta de detección de anomalías 1](media/anomaly-alert-user3.png)

1. En el caso de los archivos infectados con malware, una vez que se han detectado, puede ver una lista de **archivos infectados**. Haga clic en el nombre de archivo de malware en el cajón de archivos para abrir un informe de malware con información sobre el tipo de malware con el que está infectado el archivo.

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Actividades diarias para proteger el entorno de nube](daily-activities-to-protect-your-cloud-environment.md)

[!INCLUDE [Open support ticket](includes/support.md)]
