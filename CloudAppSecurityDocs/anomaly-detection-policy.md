---
title: Crear directivas de detección de anomalías en Cloud App Security
description: En este artículo se proporciona una descripción de las directivas de detección de anomalías y se proporciona información de referencia sobre los bloques de creación de una directiva de detección de anomalías.
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
ms.openlocfilehash: dd637bc49d65452cedc13841686ea267134ef15e
ms.sourcegitcommit: 2cf3c78a1b45a5b6ca534fdd12fd97afc51726e3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/26/2020
ms.locfileid: "80291236"
---
# <a name="get-instantaneous-behavioral-analytics-and-anomaly-detection"></a>Obtención de análisis de comportamiento y detección de anomalías instantáneos

*Se aplica a: Microsoft Cloud App Security*

Las directivas de detección de anomalías de Microsoft Cloud App Security proporcionan análisis de comportamiento de usuarios y entidades (UEBA) y aprendizaje automático (ML) para que pueda ejecutar inmediatamente la detección de amenazas avanzada en su entorno en la nube. Dado que se habilitan automáticamente, las nuevas directivas de detección de anomalías proporcionan resultados inmediatos al proporcionar detecciones inmediatas, dirigidas a numerosas anomalías de comportamiento entre los usuarios y los equipos y dispositivos conectados a la red.  Además, las nuevas directivas exponen más datos del motor de detección de Cloud App Security para ayudarle a acelerar el proceso de investigación e incluir amenazas en curso.

Las directivas de detección de anomalías se habilitan automáticamente, pero Cloud App Security tiene un período de aprendizaje inicial de siete días durante el cual no se generan todas las alertas de detección de anomalías. Después, cada sesión se compara con la actividad, cuando los usuarios estaban activos, las direcciones IP, los dispositivos, etc. detectados durante el último mes y la puntuación de riesgo de estas actividades.  Estas detecciones forman parte del motor de detección de anomalías heurísticos que genera perfiles de su entorno y desencadena alertas con respecto a una línea base que se aprendió en la actividad de su organización. Estas detecciones también usan algoritmos de aprendizaje automático diseñados para generar perfiles de los usuarios y el patrón de inicio de sesión para reducir los falsos positivos.

Las anomalías se detectan examinando la actividad del usuario. El riesgo se evalúa examinando más de 30 indicadores de riesgo diferentes, agrupados en factores de riesgo, como se indica a continuación:

* Dirección IP de riesgo
* Errores de inicio de sesión
* Actividad de administración
* Cuentas inactivas
* Location
* Viaje imposible
* Agente de usuario y dispositivo
* Tasa de actividad

En función de los resultados de la Directiva, se desencadenan alertas de seguridad. Cloud App Security examina cada sesión de usuario en la nube y le alerta cuando ocurre algo diferente de la línea de base de la organización o de la actividad normal del usuario.

Además de las alertas nativas de Cloud App Security, también obtendrá las siguientes alertas de detección basadas en la información recibida de Azure Active Directory (AD) Identity Protection:

* Credenciales perdidas: se desencadena cuando se han perdido las credenciales válidas de un usuario. Para obtener más información, vea [detección de credenciales perdidas de Azure ad](/azure/active-directory/identity-protection/concept-identity-protection-risks#user-risk).
* Inicio de sesión peligroso: combina un número de detecciones de inicio de sesión Azure AD Identity Protection en una sola detección (deshabilitada de forma predeterminada). Para obtener más información, consulte [el Azure ad de las detecciones de riesgo de inicio de sesión](/azure/active-directory/identity-protection/concept-identity-protection-risks#sign-in-risk).

Estas directivas aparecerán en la página Cloud App Security directivas y se pueden habilitar, deshabilitar, pero no editar.

## <a name="anomaly-detection-policies"></a>Directivas de detección de anomalías

Para ver las directivas de detección de anomalías en el portal, haga clic en **control** y luego en **directivas**. Seleccione **Directiva de detección de anomalías** para el tipo de directiva.

 ![nuevas directivas de detección de anomalías](media/new-anomaly-detection-policies.png)

Están disponibles las siguientes directivas de detección de anomalías:

### <a name="impossible-travel"></a>Viaje imposible

* Esta detección identifica dos actividades de usuario (es decir, una o varias sesiones) que se originan en ubicaciones geográficamente distantes dentro de un período de tiempo más corto que el tiempo que habría llevado a que el usuario viajar de la primera ubicación a la segunda, lo que indicaría que otro usuario utiliza las mismas credenciales. Esta detección usa un algoritmo de aprendizaje automático que omite los falsos positivos obvios que contribuyen a la condición de viaje imposible, como las VPN y las ubicaciones que usan con regularidad otros usuarios de la organización. La detección tiene un período de aprendizaje inicial de siete días durante el cual aprende el patrón de actividad de un usuario nuevo. La detección de viajes imposibles identifica la actividad de usuario inusual e Impossible entre dos ubicaciones. La actividad debe ser lo suficientemente inusual como para considerarse un indicador de riesgo y merecente de una alerta. Para realizar este trabajo, la lógica de detección incluye distintos niveles de supresión para los escenarios de direcciones que pueden desencadenar falsos positivos, como las actividades de VPN. El control deslizante de sensibilidad le permite influir en el algoritmo y definir el grado de limitación de la lógica de detección. Cuanto mayor sea el nivel de confidencialidad, menor será la supresión que se aplica como parte de la lógica de detección. De esta manera, puede adaptar la detección según sus necesidades de cobertura y sus destinos de SNR.

    > [!NOTE]
    > Cuando las direcciones IP de ambos lados del viaje se [etiquetan como corporativas](ip-tags.md), el viaje se considera de confianza y se excluye de desencadenar la detección de viajes imposibles. Sin embargo, si la dirección IP de un solo lado del viaje se etiqueta como corporativo, la detección se desencadena como normal.

### <a name="activity-from-infrequent-country"></a>Actividad de un país poco frecuente

* Esta detección tiene en cuenta las ubicaciones de actividad anteriores para determinar las ubicaciones nuevas e infrecuentes. El motor de detección de anomalías almacena información acerca de las ubicaciones anteriores utilizadas por los usuarios de la organización. Una alerta se desencadena cuando se produce una actividad desde una ubicación que no se ha visitado recientemente o nunca por ningún usuario de la organización.

### <a name="malware-detection"></a>Detección de malware

* Esta detección identifica los archivos malintencionados en el almacenamiento en la nube, tanto si proceden de aplicaciones de Microsoft o de terceros. Microsoft Cloud App Security usa la inteligencia de amenazas de Microsoft para reconocer si ciertos archivos están asociados a ataques de malware conocidos y son potencialmente malintencionados. Esta directiva integrada está deshabilitada de forma predeterminada. No se examinan todos los archivos, pero se usa la heurística para buscar archivos que son potencialmente peligrosos. Una vez detectados los archivos, puede ver una lista de **archivos infectados**. Haga clic en el nombre del archivo de malware en el cajón de archivos para abrir un informe de malware que le proporcione información sobre el tipo de malware al que está infectado el archivo.

    > [!NOTE]
    > * Para la detección de malware de Office 365, necesita una licencia válida para la protección contra amenazas avanzada de Office 365 P1.
    > * Cloud App Security admite la detección de malware en las siguientes aplicaciones:
    >   * Box
    >   * Dropbox
    >   * G Suite
    >   * Office 365

### <a name="activity-from-anonymous-ip-addresses"></a>Actividad desde direcciones IP anónimas

* Esta detección identifica que los usuarios estaban activos desde una dirección IP que se ha identificado como una dirección IP de proxy anónima. Estos servidores proxy los usan las personas que desean ocultar la dirección IP de su dispositivo y se pueden usar para fines malintencionados. Esta detección usa un algoritmo de aprendizaje automático que reduce los "falsos positivos", como las direcciones IP con etiquetas no utilizadas ampliamente por los usuarios de la organización.

### <a name="ransomware-activity"></a>Actividad de ransomware

* Cloud App Security amplió sus funcionalidades de detección de ransomware con la detección de anomalías para garantizar una cobertura más completa frente a los ataques sofisticados de ransomware. Al usar nuestra experiencia en investigación de seguridad para identificar patrones de comportamiento que reflejan la actividad de ransomware, Cloud App Security garantiza una protección holística y sólida. Si Cloud App Security identifica, por ejemplo, una alta tasa de cargas de archivos o actividades de eliminación de archivos, puede representar un proceso de cifrado adverso. Estos datos se recopilan en los registros recibidos de las API conectadas y, a continuación, se combinan con los patrones de comportamiento aprendidos y la inteligencia de amenazas, por ejemplo, las extensiones de ransomware conocidas. Para obtener más información sobre cómo Cloud App Security detecta ransomware, consulte [protección de la organización contra ransomware](use-case-ransomware.md).

### <a name="activity-performed-by-terminated-user"></a>Actividad realizada por el usuario Terminado

* Esta detección permite identificar cuándo un empleado terminado continúa realizando acciones en las aplicaciones SaaS. Dado que los datos muestran que el mayor riesgo de la amenaza interna procede de los empleados que dejaron en términos incorrectos, es importante estar atento a la actividad en las cuentas de empleados terminados. A veces, cuando los empleados abandonan una empresa, sus cuentas se desaprovisionan de las aplicaciones corporativas, pero en muchos casos siguen conservando el acceso a determinados recursos corporativos. Esto es aún más importante a la hora de considerar las cuentas con privilegios, ya que el daño potencial que puede hacer un administrador anterior es, de forma inherente, mayor.
Esta detección aprovecha la capacidad de Cloud App Security para supervisar el comportamiento de los usuarios entre aplicaciones, lo que permite la identificación de la actividad normal del usuario, el hecho de que la cuenta se ha terminado y la actividad real en otras aplicaciones. Por ejemplo, un empleado que es Azure AD cuenta se ha terminado pero todavía tiene acceso a la infraestructura de AWS corporativa, tiene la posibilidad de producir daños a gran escala.

La detección busca usuarios cuya cuenta finalizó en Azure AD, pero que siguen realizando actividades en otras plataformas, como AWS o Salesforce. Esto es especialmente importante para los usuarios que usan otra cuenta (no su cuenta principal de inicio de sesión único) para administrar los recursos, ya que estas cuentas no suelen terminar cuando un usuario abandona la empresa.

### <a name="activity-from-suspicious-ip-addresses"></a>Actividad desde direcciones IP sospechosas

* Esta detección identifica que los usuarios estaban activos desde una dirección IP identificada como arriesgada por la inteligencia de amenazas de Microsoft. Estas direcciones IP están implicadas en actividades malintencionadas, como zombi C & C, y pueden indicar una cuenta en peligro. Esta detección usa un algoritmo de aprendizaje automático que reduce los "falsos positivos", como las direcciones IP con etiquetas no utilizadas ampliamente por los usuarios de la organización.

### <a name="suspicious-inbox-forwarding"></a>Reenvío de bandeja de entrada sospechoso

* Esta detección busca reglas de reenvío de correo electrónico sospechosas, por ejemplo, si un usuario creó una regla de bandeja de entrada que reenvía una copia de todos los mensajes de correo electrónico a una dirección externa.

> [!NOTE]
> Cloud App Security solo le alerta por cada regla de reenvío identificada como sospechosa, en función del comportamiento típico del usuario.

### <a name="suspicious-inbox-manipulation-rules"></a>Reglas de manipulación de bandeja de entrada sospechosas

* Esta detección genera un perfil de su entorno y desencadena alertas cuando se establecen reglas sospechosas que eliminan o mueven mensajes o carpetas en la bandeja de entrada de un usuario. Esto puede indicar que la cuenta del usuario se ve comprometida, que los mensajes se están ocultando intencionadamente y que el buzón se usa para distribuir el correo no deseado en la organización.

### <a name="suspicious-email-deletion-activity-preview"></a>Actividad de eliminación de correo electrónico sospechoso (versión preliminar)

* Esta directiva genera perfiles de su entorno y desencadena alertas cuando un usuario realiza actividades de eliminación de correo electrónico sospechosas en una sola sesión. Esta Directiva puede indicar que los buzones de usuario pueden estar en peligro por posibles vectores de ataque, como la comunicación de comando y control (C & C/C2) por correo electrónico.

### <a name="unusual-activities-by-user"></a>Actividades inusuales (por usuario)

Estas detecciones identifican a los usuarios que realizan lo siguiente:

* Actividades de descarga de varios archivos inusuales
* Actividades de recurso compartido de archivos inusuales
* Actividades de eliminación de archivos inusuales
* Actividades suplantadas inusuales
* Actividades administrativas inusuales
* Actividades inusuales de uso compartido de informes de Power BI (versión preliminar)
* Actividades de creación de varias máquinas virtuales inusuales (versión preliminar)
* Actividades inusuales de eliminación de almacenamiento múltiple (versión preliminar)
* Región inusual para el recurso de nube (versión preliminar)

Estas directivas buscan actividades dentro de una sola sesión con respecto a la base de referencia aprendida, lo que podría indicar un intento de infracción. Estas detecciones aprovechan un algoritmo de aprendizaje automático que perfila el patrón de inicio de sesión de los usuarios y reduce los falsos positivos. Estas detecciones forman parte del motor de detección de anomalías heurísticos que genera perfiles de su entorno y desencadena alertas con respecto a una línea base que se aprendió en la actividad de su organización.

### <a name="multiple-failed-login-attempts"></a>Varios intentos de inicio de sesión erróneos

* Esta detección identifica a los usuarios que han producido errores en varios intentos de inicio de sesión en una sola sesión con respecto a la base de referencia aprendida, lo que podría indicar un intento de infracción.

### <a name="data-exfiltration-to-unsanctioned-apps"></a>Filtrado de datos a aplicaciones no autorizadas

* Esta Directiva se habilita automáticamente para avisarle cuando un usuario o una dirección IP usa una aplicación que no está autorizada para realizar una actividad similar a un intento de obtener información de su organización.

### <a name="multiple-delete-vm-activities"></a>Varias actividades de eliminación de máquinas virtuales

* Esta directiva genera perfiles de su entorno y desencadena alertas cuando los usuarios eliminan varias máquinas virtuales en una sola sesión, en relación con la línea de base de su organización. Esto puede indicar un intento de infracción.

## <a name="enable-automated-governance"></a>Habilitación del gobierno automatizado<a name="adp-automated-gov"></a>

Puede habilitar acciones correctivas automatizadas en alertas generadas por directivas de detección de anomalías.

1. En la página **Directiva** , haga clic en el nombre de la Directiva de detección.
1. En la ventana **Editar Directiva de detección de anomalías** que se abre, en **gobierno** , configure las acciones correctivas que desee para cada aplicación conectada o para todas las aplicaciones.
1. Haga clic en **Actualizar**.

## <a name="tune-anomaly-detection-policies"></a>Ajustar las directivas de detección de anomalías

Para influir en el motor de detección de anomalías para suprimir o exponer alertas en función de sus preferencias:

* En la directiva de viaje imposible, puede establecer el control deslizante de sensibilidad para determinar el nivel de comportamiento anómalo necesario antes de que se desencadene una alerta. Por ejemplo, si se establece en Low, se suprimirán las alertas de viaje imposibles de las ubicaciones comunes de un usuario y, si se establece en alto, se mostrarán dichas alertas. Puede elegir entre los siguientes niveles de confidencialidad:

  * **Bajo**: suprimes del sistema, del inquilino y del usuario
  * **Medio**: suprimes del sistema y del usuario
  * **Alto**: solo suprimes del sistema

    Donde:

    | Tipo de supresión | Descripción |
    | --- | --- |
    | **Sistema** | Detecciones integradas que siempre se suprimen. |
    | **Inquilino** | Actividades comunes basadas en la actividad anterior en el inquilino. Por ejemplo, suprime las actividades de un ISP que previamente ha avisado en la organización. |
    | **Usuario** | Actividades comunes basadas en la actividad anterior del usuario específico. Por ejemplo, suprime las actividades de una ubicación que suele usar el usuario. |

* También puede configurar si las alertas de actividad de un país poco frecuente, direcciones IP anónimas, direcciones IP sospechosas y viajes imposibles deben analizar tanto inicios de sesión con errores como correctos o simplemente inicios de sesión correctos.

> [!NOTE]
> De forma predeterminada, los protocolos de inicio de sesión heredados, como los que no usan la autenticación multifactor (por ejemplo, WS-Trust), no se supervisan con la Directiva de viajes imposibles. Si su organización usa protocolos heredados, para evitar que falten actividades relevantes, edite la Directiva y, en **Configuración avanzada**, establezca **analizar las actividades de inicio de sesión** en **todos los inicios de sesión**.

## <a name="scope-anomaly-detection-policies"></a>Directivas de detección de anomalías de ámbito

Cada directiva de detección de anomalías puede tener un ámbito independiente, de modo que solo se aplique a los usuarios y grupos que desee incluir y excluir en la Directiva.
Por ejemplo, puede establecer la actividad a partir de la detección de condados poco frecuentes para omitir un usuario específico que viaja de forma habitual.

Para el ámbito de una directiva de detección de anomalías:

1. Haga clic en **Control** > **directivas**y establezca el filtro de **tipo** en Directiva de **detección de anomalías**.
1. Haga clic en la Directiva que desea incluir en el ámbito.
1. En **ámbito**, cambie la lista desplegable de la configuración predeterminada de **todos los usuarios y grupos**a **usuarios y grupos específicos**.
1. Seleccione **incluir** para especificar los usuarios y grupos a los que se aplicará esta Directiva. Cualquier usuario o grupo que no se seleccione aquí no se considerará una amenaza y no generará una alerta.
1. Seleccione **excluir** para especificar los usuarios a los que no se aplicará esta Directiva. Cualquier usuario seleccionado aquí no se considerará una amenaza y no generará una alerta, incluso si son miembros de grupos seleccionados en **incluir**.

    ![ámbito de detección de anomalías](media/anomaly-detection-scoping.png)

## <a name="triage-anomaly-detection-alerts"></a>Evaluación de las alertas de detección de anomalías

Puede evaluar las distintas alertas desencadenadas por las nuevas directivas de detección de anomalías rápidamente y decidir cuáles deben tomarse en primer lugar. Para ello, necesita el contexto de la alerta, por lo que podrá ver la imagen más grande y comprender si está ocurriendo algo malintencionado.

1. En el **registro de actividad**, puede abrir una actividad para mostrar el cajón de actividades. Haga clic en **usuario** para ver la pestaña información de usuario. Esta pestaña incluye información como el número de alertas, las actividades y el lugar desde el que se han conectado, lo que es importante en una investigación.

    ![detección de anomalías alert1](media/anomaly-alert-user1.png) ![detección de anomalías alert1](media/anomaly-alert-user2.png)

1. Esto le permite comprender cuáles son las actividades sospechosas que el usuario realizó y obtener una mayor confianza en cuanto a si la cuenta se ha puesto en peligro. Por ejemplo, una alerta en varios inicios de sesión erróneos puede ser sospechosa y puede indicar un posible ataque por fuerza bruta, pero también puede ser un error de configuración de la aplicación, lo que provoca que la alerta sea un verdadero positivo benigno. Sin embargo, si ve una alerta de varios inicios de sesión erróneos con actividades sospechosas adicionales, hay una mayor probabilidad de que la cuenta se vea comprometida. En el ejemplo siguiente, puede ver que la alerta de **varios intentos de inicio de sesión incorrectos** fue seguida **de una actividad de una dirección IP de Tor y de una actividad de** **viaje imposible**, ambos indicadores sólidos de peligro (IOC) por sí solos. Si esto no era lo suficientemente sospechoso, puede ver que el mismo usuario realizó una **actividad de descarga masiva**, que suele ser un indicador del atacante que realiza la exfiltración de datos.

    ![detección de anomalías alert1](media/anomaly-alert-user3.png)

1. En el caso de los archivos infectados por malware, después de detectar archivos, puede ver una lista de **archivos infectados**. Haga clic en el nombre del archivo de malware en el cajón de archivos para abrir un informe de malware que le proporcione información sobre el tipo de malware al que está infectado el archivo.

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Actividades diarias para proteger el entorno de nube](daily-activities-to-protect-your-cloud-environment.md)

[!INCLUDE [Open support ticket](includes/support.md)]
