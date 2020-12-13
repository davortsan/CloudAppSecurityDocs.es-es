---
title: Supervisión de alertas generadas en Cloud App Security
description: En este artículo se proporcionan una lista y una descripción de todas las alertas.
ms.date: 12/10/2018
ms.topic: how-to
ms.openlocfilehash: 23a1ea16cb0f733d82b38d0191fed929fbc515d4
ms.sourcegitcommit: 72ddcd0f9a83251d588009abf506676612c50267
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/13/2020
ms.locfileid: "97369963"
---
# <a name="monitor-alerts-in-cloud-app-security"></a>Supervisión de alertas en Cloud App Security

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Las alertas son los puntos de entrada para comprender el entorno de nube en más profundidad. En este artículo se proporcionan una lista y una descripción de todas las alertas.

## <a name="monitoring-your-alerts"></a>Supervisión de las alertas

Revisar todas las alertas es una buena idea. Comprender por qué se produce una alerta le permite usarlas como herramientas para modificar las directivas.

**Para ver las alertas:** En el portal de Microsoft Cloud App Security, haga clic en **alertas**.

![Menú Alertas](media/alert-menu.png)

- **Descarte** una alerta después de verla y determinar que no es interesante.
  - Escriba un **comentario** para explicar por qué ha descartado la alerta.
  - **Envíenos sus comentarios sobre esta alerta** para que nuestro equipo de investigación de seguridad la revise para mejorar las alertas.

- **Resuelva** la alerta si la ha investigado y ha mitigado el riesgo.

  - La alerta ya no se mostrará en la tabla de alertas.
  - **Márquela como no leída** si ha empezado a investigar un problema, pero quiere asegurarse de que no se olvida de continuar trabajando en él.
  - **Ajuste la directiva** que coincidía con la alerta para mejorar las coincidencias de próximas alertas.
  - Al resolver una alerta, puede escribir un comentario y **enviarlo al equipo de Cloud App Security**.

## <a name="deployment-of-our-enhanced-alert-monitoring-and-management-experience"></a>Implementación de nuestra experiencia mejorada de supervisión y administración de alertas

Como parte de las mejoras continuas en la supervisión y la administración de alertas, la página de alertas de Cloud App Security se ha mejorado en función de sus comentarios. En la experiencia mejorada, los Estados **resuelto** y **descartado** se sustituyen por el estado **cerrado** y las alertas cerradas tienen uno de los siguientes tipos de resolución:

- **Verdadero positivo**: una alerta en una actividad malintencionada confirmada
- **Benigna**: una alerta sobre una actividad sospechosa pero no malintencionada, como una prueba de penetración u otra acción sospechosa autorizada.
- **Falso positivo**: una alerta en una actividad no malintencionada

> [!NOTE]
> La experiencia mejorada solo se aplica a las nuevas alertas y no afecta al estado de las alertas existentes (heredadas) que se han **resuelto** o **descartado**.

![Página de alertas mejorada](media/monitor-alerts/enhanced-alerts.png)

### <a name="enhanced-alert-monitoring"></a>Supervisión de alertas mejorada

En la página Alertas mejoradas, la columna **Estado** muestra si se abre o se cierra una alerta y la columna **tipo de resolución** muestra el tipo de resolución que se utiliza al cerrar una alerta. Puede usar el filtro de **Estado** para ayudarle a identificar las alertas abiertas o cerradas y, a continuación, usar el filtro **avanzado** , puede investigar más las alertas cerradas por **tipo de resolución** con tipos de resolución mejorada y heredada.

![Página de alertas mejorada que muestra el filtro avanzado](media/monitor-alerts/enhanced-alerts-advanced-filter.png)

### <a name="enhanced-alert-management"></a>Administración de alertas mejorada

Al cerrar las alertas, elija una de las siguientes opciones de resolución:

- **Cerrar como verdadero positivo**: Si la actividad se confirma como malintencionada
- **Cerrar como benigno**: Si la actividad es sospechosa pero no es una actividad malintencionada, como una prueba de penetración u otra acción sospechosa autorizada
- **Cerrar como falso positivo**: Si la actividad se confirma como no malintencionada

En el menú emergente que aparece, proporcione un motivo para cerrar la alerta y rellene el resto de los detalles según sea necesario y, a continuación, haga clic en **cerrar alerta**.

![Emergente de cierre de alertas mejorada](media/monitor-alerts/enhanced-alerts-close-resolution.png)

## <a name="built-in-alerts"></a>Alertas integradas

Se mostrarán los siguientes tipos de alertas.

|Nombre de la alerta|Id. de alerta|Descripción|
|----|----|----|
|Nueva ubicación|ALERT_GEOLOCATION_NEW_COUNTRY|Se ha detectado una nueva ubicación desde que comenzó el examen (hasta 6 meses). Esta alerta solo se muestra una vez para cada país o región de toda la organización. |
|Nuevo usuario administrador|ALERT_ADMIN_USER|Se ha detectado un nuevo administrador de una aplicación específica. Puede tratarse de una persona que es un administrador de una aplicación y ahora es un administrador de otra aplicación. Esta alerta está relacionada con el tipo de administrador específico, por lo que se mostrará cada vez que cambie el tipo de administrador. Si un usuario había perdido los privilegios de administrador y los ha recuperado, se mostrará esta alerta.|
|Cuenta inactiva|ALERT_ZOMBIE_USER|Si un usuario está inactivo durante 60 días por aplicación (por ejemplo, si alguien está activo en Box pero no ha tocado Google Workspace durante 60 días), el usuario se considerará inactivo en el área de trabajo de Google. Se agrega una etiqueta a estos usuarios, por lo que se pueden buscar cuentas inactivas.|
|Ubicación de administrador inesperada|ALERT_NEW_ADMIN_LOCATION|Se ha detectado una nueva ubicación de los administradores desde que comenzó el examen (hasta 6 meses). Esta alerta solo se muestra una vez para cada país o región de cualquier administrador de la organización. |
|Cuenta en peligro|ALERT_COMPROMISED_ACCOUNT|Si se ha producido una infracción en una aplicación y se publica la lista de cuentas que se han infringido, Cloud App Security descarga la lista y la compara con la lista de usuarios, incluidos los usuarios internos, los usuarios externos y las cuentas personales. |

## <a name="custom-alerts"></a>Alertas personalizadas

Se mostrarán los siguientes tipos de alertas.

|Nombre de la alerta|Id. de alerta|Descripción|
|----|----|----|
|Alerta de actividad sospechosa|ALERT_SUSPICIOUS_ACTIVITY|Las actividades sospechosas se puntúan según lo sospechosa que sea la actividad anómala (¿hay una cuenta inactiva implicada?, ¿Se trata de una nueva ubicación?) Estos criterios se calculan juntos para proporcionar una puntuación de riesgo en función de los siguientes factores de riesgo: <br />El usuario es un administrador <br />Usuario estrictamente remoto<br />Proxy anónimo<br /> Todos los inicios de sesión son erróneos<br />Numerosos inicios de sesión fallidos<br />Nuevo (administrador)<br />IP/ISP/país/agente de usuario para usuario/inquilino<br /> IP/ISP/país/agente de usuario usado solo por el usuario (administrador)<br />Primera actividad de usuario (administrador) tras un tiempo<br />Primera vez que se realiza esta actividad administrativa tras un tiempo<br />Esta actividad administrativa no es común o no se había realizado nunca<br />Esta dirección IP solo tuvo inicios de sesión erróneos en el pasado<br />Viaje imposible|
|Alerta de uso sospechoso de la nube|ALERT_DISCOVERY_ANOMALY_DETECTION|La detección de anomalías de Cloud Discovery comprueba el patrón de comportamiento normal y busca los usuarios o las aplicaciones que se usan de manera inusual. |
|Infracción de directiva de actividad|ALERT_CABINET_EVENT_MATCH_AUDIT|Esta alerta le informa cuando se detecta una coincidencia de directiva.|
|Infracción de directiva de archivo|ALERT_CABINET_EVENT_MATCH_FILE|Esta alerta le informa cuando se detecta una coincidencia de directiva.|
|Infracción de directiva de proxy|ALERT_CABINET_INLINE_EVENT_MATCH|Esta alerta le informa cuando se detecta una coincidencia de directiva.|
|Infracción de directiva de campo|ALERT_CABINET_EVENT_MATCH_OBJECT|Esta alerta le informa cuando se detecta una coincidencia de directiva.|
|Nuevo servicio detectado|ALERT_CABINET_DISCOVERY_NEW_SERVICE|Se ha detectado una nueva aplicación.|
|Uso de cuenta personal|ALERT_PERSONAL_USER_SAGE|El motor de detección busca cuentas personales en función de los recursos compartidos de archivos y los nombres de usuario. |

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Actividades diarias para proteger el entorno de nube](daily-activities-to-protect-your-cloud-environment.md)

[!INCLUDE [Open support ticket](includes/support.md)]
