---
title: Cloud App Security guía de investigación de alertas de detección de anomalías
description: En este artículo se explica cómo investigar las alertas de detección de anomalías de Cloud App Security emitidas cuando se detectan ataques en su organización.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 06/08/2020
ms.topic: how-to
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: itfalcon
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 57d27e6cda7f4750464b4f1c4330c4776aa79467
ms.sourcegitcommit: 5367d8fdf99d61719a395728f2ef4b014604e3bc
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/08/2020
ms.locfileid: "94371134"
---
# <a name="how-to-investigate-anomaly-detection-alerts"></a>Cómo investigar alertas de detección de anomalías

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Microsoft Cloud App Security proporciona detecciones de seguridad y alertas para actividades malintencionadas. El objetivo de esta guía es proporcionarle información general y práctica sobre cada alerta, para ayudarle con las tareas de investigación y corrección. En esta guía se incluye información general sobre las condiciones para desencadenar alertas. Sin embargo, es importante tener en cuenta que, puesto que las detecciones de anomalías son no deterministas por naturaleza, solo se desencadenan cuando hay un comportamiento que se desvía de la norma. Por último, algunas alertas pueden estar en versión preliminar, por lo que debe revisar periódicamente la documentación oficial sobre el estado de alerta actualizado.

## <a name="mitre-attck"></a>MITRE ATT \& CK

Para explicar y facilitar la asignación de la relación entre Cloud App Security las alertas y la conocida matriz de MITRE ATT \& CK, hemos categorizado las alertas por su táctica de Mitre ATT \& CK correspondiente. Esta referencia adicional facilita la comprensión de la técnica de ataques sospechoso que se puede usar cuando se desencadena una alerta Cloud App Security.

En esta guía se proporciona información sobre cómo investigar y corregir Cloud App Security alertas en las siguientes categorías.

> [!div class="checklist"]
>
> - [Acceso inicial](#initial-access-alerts)
> - [Ejecución](#execution-alerts)
> - [Persistencia](#persistence-alerts)
> - [Elevación de privilegios](#privilege-escalation-alerts)
> - [Acceso a credenciales](#credential-access-alerts)
> - [Colección](#collection-alerts)
> - [Exfiltración](#exfiltration-alerts)
> - [Impacto](#impact-alerts)

## <a name="security-alert-classifications"></a>Clasificaciones de las alertas de seguridad

Tras una investigación adecuada, todas las alertas de Cloud App Security se pueden clasificar como uno de los siguientes tipos de actividad:

- **Verdadero positivo (TP)** : una alerta en una actividad malintencionada confirmada.
- **Verdadero positivo benigno (B-TP)** : una alerta de actividad sospechosa pero no malintencionada, como una prueba de penetración u otra acción sospechosa autorizada.
- **Falso positivo (FP)** : una alerta en una actividad no malintencionada.

## <a name="general-investigation-steps"></a>Pasos de investigación generales

Debe usar las siguientes directrices generales al investigar cualquier tipo de alerta para obtener una descripción más clara de la posible amenaza antes de aplicar la acción recomendada.

- Revise la puntuación de [prioridad](tutorial-ueba.md#understand-the-investigation-priority-score) de la investigación del usuario y compárelo con el resto de la organización. Esto le ayudará a identificar qué usuarios de su organización suponen el mayor riesgo.
- Si identifica un **TP** , revise todas las actividades del usuario para comprender el impacto.
- Revise toda la actividad de los usuarios para ver otros indicadores de riesgo y explore el origen y el ámbito de impacto. Por ejemplo, revise la siguiente información del dispositivo de usuario y compárela con la información de dispositivo conocida:
  - Sistema operativo y versión
  - Explorador y versión
  - Dirección IP y ubicación

## <a name="initial-access-alerts"></a>Alertas de acceso inicial

En esta sección se describen las alertas que indican que un actor malintencionado puede estar intentando obtener un punto inicial de la organización.

### <a name="activity-from-anonymous-ip-address"></a>Actividad de la dirección IP anónima

**Descripción**

Actividad de una dirección IP identificada como dirección IP de proxy anónima de Microsoft Threat Intelligence o de su organización. Estos proxys se pueden usar para ocultar la dirección IP de un dispositivo y se pueden usar para actividades malintencionadas.

**TP** , **B-TP** o **FP** ?

Esta detección usa un algoritmo de aprendizaje automático que reduce los incidentes **de B-TP** , como las direcciones IP con etiquetas no utilizadas ampliamente por los usuarios de la organización.

1. **TP** : si es capaz de confirmar que la actividad se realizó desde una dirección IP anónima o de Tor.

    **Acción recomendada** : suspender al usuario, marcar el usuario como comprometido y restablecer su contraseña.
1. **B-TP** : si se sabe que un usuario usa direcciones IP anónimas en el ámbito de sus tareas. Por ejemplo, cuando un analista de seguridad realiza pruebas de seguridad o de penetración en nombre de la organización.

    **Acción recomendada** : descartar la alerta.

**Comprender el ámbito de la vulneración de seguridad**

- Revise todas las alertas y la actividad de los usuarios para ver más indicadores de riesgo. Por ejemplo, si la alerta iba seguida de otra alerta sospechosa, como una [descarga de archivos inusual (por el usuario)](#unusual-file-download-by-user) o una alerta [sospechosa de reenvío de bandeja de entrada](#suspicious-inbox-forwarding) , esto suele indicar que un atacante está intentando realizar el filtrado de datos.

### <a name="activity-from-infrequent-country"></a>Actividad desde un país poco frecuente

Actividad de un país o región que podría indicar actividad malintencionada. Esta directiva genera perfiles de su entorno y desencadena alertas cuando se detecta actividad en una ubicación que no se ha visitado nunca por ningún usuario de la organización.

De forma predeterminada, la Directiva está configurada para incluir solo las actividades de inicio de sesión correctas, pero se puede configurar para que incluya cualquier actividad de inicio de sesión. La Directiva se puede limitar aún más a un subconjunto de usuarios o puede excluir a los usuarios que se sabe que viajan a ubicaciones remotas.

**Período de aprendizaje**

La detección de ubicaciones anómalas requiere un período de aprendizaje inicial de siete días durante el cual no se desencadenan alertas para las nuevas ubicaciones.

**TP** , **B-TP** o **FP** ?

1. **TP** : si es capaz de confirmar que un usuario legítimo no ha realizado la actividad.

    **Acción recomendada** :
    1. Suspenda al usuario, restablezca la contraseña e identifique el momento adecuado para volver a habilitar la cuenta de forma segura.
    1. Opcional: cree una guía de uso de Power Automatic para ponerse en contacto con los usuarios detectados como la conexión desde ubicaciones poco frecuentes y sus administradores para comprobar su actividad.
1. **B-TP** : si se sabe que un usuario está en esta ubicación. Por ejemplo, cuando un usuario viaja con frecuencia y actualmente está en la ubicación especificada.

    **Acción recomendada** :
    1. Descartar la alerta y modificar la Directiva para excluir al usuario.
    1. Crear un grupo de usuarios para viajeros frecuentes, importar el grupo en Cloud App Security y excluir a los usuarios de esta alerta
    1. Opcional: cree una guía de uso de Power Automatic para ponerse en contacto con los usuarios detectados como la conexión desde ubicaciones poco frecuentes y sus administradores para comprobar su actividad.

**Comprender el ámbito de la vulneración de seguridad**

- Revise qué recursos pueden estar en peligro, como las posibles descargas de datos.

### <a name="activity-from-suspicious-ip-addresses"></a>Actividad desde direcciones IP sospechosas

Actividad de una dirección IP identificada como arriesgada por Microsoft Threat Intelligence o por su organización. Estas direcciones IP se identifican como implicadas en actividades malintencionadas, como el comando y el control de zombi (C&C), y pueden indicar una cuenta en peligro.

**TP** , **B-TP** o **FP** ?

1. **TP** : si es capaz de confirmar que un usuario legítimo no ha realizado la actividad.

    **Acción recomendada** : suspender al usuario, marcar el usuario como comprometido y restablecer su contraseña.
1. **B-TP** : si se sabe que un usuario usa la dirección IP en el ámbito de sus tareas. Por ejemplo, cuando un analista de seguridad realiza pruebas de seguridad o de penetración en nombre de la organización.

    **Acción recomendada** : descartar la alerta.

**Comprender el ámbito de la vulneración de seguridad**

1. Revise el registro de actividad y busque actividades de la misma dirección IP.
1. Revise qué recursos pueden estar en peligro, como posibles descargas de datos o modificaciones administrativas.
1. Cree un grupo para que los analistas de seguridad activen voluntariamente estas alertas y las excluyan de la Directiva.

### <a name="impossible-travel"></a>Viaje imposible

Actividad del mismo usuario en ubicaciones diferentes dentro de un período de tiempo menor que el tiempo de viaje esperado entre las dos ubicaciones. Esto puede indicar una infracción de credenciales; sin embargo, también es posible que la ubicación real del usuario esté enmascarada, por ejemplo, mediante una VPN.

Para mejorar la precisión y alertar solo cuando hay una indicación fuerte de una infracción, Cloud App Security establece una línea base en cada usuario de la organización y solo avisará cuando se detecte el comportamiento inusual. La Directiva de viaje imposible puede ajustarse a sus requisitos.

**Período de aprendizaje**

El establecimiento del patrón de actividad de un usuario nuevo requiere un período de aprendizaje inicial de siete días durante el cual no se desencadenan alertas para las nuevas ubicaciones.

**TP** , **B-TP** o **FP** ?

Esta detección usa un algoritmo de aprendizaje automático que omite las condiciones **de TP de B** obvias, como cuando las direcciones IP de ambos lados del viaje se consideran seguras, el viaje es de confianza y se excluye de desencadenar la detección de viajes imposibles. Por ejemplo, ambos lados se consideran seguros si se [etiquetan como corporativos](ip-tags.md). Sin embargo, si la dirección IP de un solo lado del viaje se considera segura, la detección se desencadena como normal.

1. **TP** : si se puede confirmar que la ubicación de la alerta de viaje imposible es improbable para el usuario.

    **Acción recomendada** : suspender al usuario, marcar el usuario como comprometido y restablecer su contraseña.
1. **FP** (viaje de usuario no detectado): si puede confirmar que el usuario ha viajado recientemente al destino mencionado en la alerta. Por ejemplo, si el teléfono de un usuario que está en modo de avión sigue conectado a servicios como Exchange online en la red corporativa mientras viaja a una ubicación diferente. Cuando el usuario llega a la nueva ubicación, el teléfono se conecta a Exchange Online y desencadena la alerta de viaje imposible.

    **Acción recomendada** : descartar la alerta.
1. **FP** (VPN sin etiquetar): si es capaz de confirmar que el intervalo de direcciones IP procede de una VPN autorizada.

    **Acción recomendada** : descartar la alerta y [Agregar el intervalo de direcciones IP de la VPN](ip-tags.md#create-an-ip-address-range) a Cloud App Security y usarlo para etiquetar el intervalo de direcciones IP de la VPN.

**Comprender el ámbito de la vulneración de seguridad**

1. Revise el registro de actividad para obtener una descripción de las actividades similares en la misma ubicación y dirección IP.
1. Si ve que el usuario realizó otras actividades de riesgo, como la descarga de un gran volumen de archivos desde una nueva ubicación, esto sería una indicación fuerte de un posible riesgo.
1. Agregue los intervalos de direcciones IP y VPN corporativas.
1. Cree una guía con Power Automatic y póngase en contacto con el administrador del usuario para ver si el usuario está viajando de forma legítima.
1. Considere la posibilidad de crear una base de datos de viaje conocida para los informes de viajes de la organización hasta el minuto y usarla para realizar una referencia cruzada a la actividad de viaje.

### <a name="misleading-oauth-app-name"></a>Nombre de aplicación OAuth engañoso

El nombre de la aplicación OAuth engañosa identifica las aplicaciones con caracteres, como letras extranjeras, similares a las letras latinas. Esto puede indicar un intento de disfrazar una aplicación malintencionada como una aplicación conocida y de confianza para que los atacantes puedan engañar a los usuarios para que descarguen su aplicación malintencionada.

**TP** , **B-TP** o **FP** ?

1. **TP** : si es capaz de confirmar que la aplicación tiene un nombre engañoso.

    **Acción recomendada** : Revise el nivel de permiso que solicita esta aplicación y a qué usuarios se les ha concedido acceso. En función de la investigación, puede optar por prohibir el acceso a esta aplicación.

Para prohibir el acceso a la aplicación, en la página de **aplicaciones de OAuth** , en la fila en la que aparece la aplicación que desea vetar, haga clic en el icono de veto.
    - Puede elegir si quiere indicar a los usuarios que se ha prohibido la aplicación que han instalado y autorizado. La notificación informa a los usuarios de que la aplicación estará deshabilitada y no tendrán acceso a la aplicación conectada. Si no quiere que lo sepan, anule la selección de **Enviar una notificación a los usuarios que hayan concedido permiso a esta aplicación prohibida** en el cuadro de diálogo.
    - Se recomienda permitir que los usuarios de la aplicación sepan que se ha prohibido el uso de la aplicación.

1. **FP** : Si va a confirmar que la aplicación tiene un nombre engañoso pero tiene un uso empresarial legítimo en la organización.

    **Acción recomendada** : descartar la alerta.

**Comprender el ámbito de la vulneración de seguridad**

- Siga el tutorial sobre cómo [investigar aplicaciones de OAuth de riesgo](investigate-risky-oauth.md).

### <a name="misleading-publisher-name-for-an-oauth-app"></a>Nombre de publicador engañoso para una aplicación de OAuth

El nombre del publicador de OAuth engañoso para una aplicación de OAuth identifica aplicaciones con caracteres, como letras extranjeras, similares a las letras latinas. Esto puede indicar un intento de disfrazar una aplicación malintencionada como una aplicación conocida y de confianza para que los atacantes puedan engañar a los usuarios para que descarguen su aplicación malintencionada.

**TP** , **B-TP** o **FP** ?

1. **TP** : si es capaz de confirmar que la aplicación tiene un nombre de publicador engañoso.

    **Acción recomendada** : Revise el nivel de permiso que solicita esta aplicación y a qué usuarios se les ha concedido acceso. En función de la investigación, puede optar por prohibir el acceso a esta aplicación.
1. **FP** : Si va a confirmar que la aplicación tiene un nombre de publicador engañoso, pero es un publicador legítimo.

    **Acción recomendada** : descartar la alerta.

**Comprender el ámbito de la vulneración de seguridad**

1. En la página **aplicaciones de OAuth** , haga clic en la aplicación para abrir el cajón de la **aplicación** y, a continuación, haga clic en **actividad relacionada**. Se abrirá la página del **registro de actividad** que se ha filtrado para las actividades realizadas por la aplicación. Tenga en cuenta que algunas aplicaciones realizan actividades que se registran como realizadas por un usuario. Estas actividades se filtran automáticamente de los resultados del registro de actividad. Para investigar más sobre el uso del registro de actividad, consulte [Registro de actividad](activity-filters.md).
1. Si sospecha que una aplicación es sospechosa, se recomienda que investigue el nombre y el publicador de la aplicación en diferentes tiendas de aplicaciones. Al comprobar las tiendas de aplicaciones, céntrese en los siguientes tipos de aplicaciones:
    - Aplicaciones con un número reducido de descargas.
    - Aplicaciones con una clasificación o puntuación baja o con comentarios negativos.
    - Aplicaciones con un editor o sitio web sospechoso.
    - Aplicaciones que no se han actualizado recientemente. Esto podría ser signo de una aplicación que ya no se admite.
    - Aplicaciones que tienen permisos no pertinentes. Esto podría indicar que una aplicación es de riesgo.
1. Si todavía sospecha que una aplicación es sospechosa, puede investigar el nombre de la aplicación, el editor y la dirección URL en línea.

## <a name="execution-alerts"></a>Alertas de ejecución

En esta sección se describen las alertas que indican que un actor malintencionado puede estar intentando ejecutar código malintencionado en su organización.

### <a name="multiple-storage-deletion-activities"></a>Varias actividades de eliminación de almacenamiento

Actividades en una sola sesión que indica que un usuario ha realizado un número inusual de almacenamiento en la nube o de eliminaciones de la base de datos de recursos como Azure blobs, AWS S3 bucket o Cosmos DB en comparación con la base de referencia aprendida. Esto puede indicar un intento de infracción de la organización.

**Período de aprendizaje**

El establecimiento del patrón de actividad de un usuario nuevo requiere un período de aprendizaje inicial de siete días durante el cual no se desencadenan alertas para las nuevas ubicaciones.

**TP** , **B-TP** o **FP** ?

1. **TP** : Si va a confirmar que las eliminaciones no se autorizaron.

    **Acción recomendada** : suspenda al usuario, restablezca la contraseña y examine todos los dispositivos en busca de amenazas malintencionadas. Revise toda la actividad de los usuarios para ver otros indicadores de riesgo y explore el ámbito de impacto.
1. **FP** : Si después de la investigación, puede confirmar que el administrador está autorizado para realizar estas actividades de eliminación.

    **Acción recomendada** : descartar la alerta.

**Comprender el ámbito de la vulneración de seguridad**

1. Póngase en contacto con el usuario y confirme la actividad.
1. Revise el registro de actividad para ver otros indicadores de riesgo y vea quién realizó el cambio.
1. Revise las actividades del usuario en busca de cambios en otros servicios.

### <a name="multiple-vm-creation-activities"></a>Actividades de creación de varias máquinas virtuales

Actividades en una única sesión que indica que un usuario ha realizado un número inusual de acciones de creación de máquinas virtuales en comparación con la base de referencia aprendida. La creación de varias máquinas virtuales en una infraestructura de nube infringida podría indicar un intento de ejecutar operaciones de minería de datos criptográficas desde dentro de la organización.

**Período de aprendizaje**

El establecimiento del patrón de actividad de un usuario nuevo requiere un período de aprendizaje inicial de siete días durante el cual no se desencadenan alertas para las nuevas ubicaciones.

**TP** , **B-TP** o **FP** ?

Para mejorar la precisión y alertar solo cuando hay una indicación fuerte de una infracción, esta detección establece una línea base en cada entorno de la organización para reducir los incidentes **B-TP** , como un administrador creó legítimamente más máquinas virtuales que la línea base establecida y solo alerta cuando se detecta el comportamiento inusual.

- **TP** : si es capaz de confirmar que las actividades de creación no fueron realizadas por un usuario legítimo.

    **Acción recomendada** : suspenda al usuario, restablezca la contraseña y examine todos los dispositivos en busca de amenazas malintencionadas. Revise toda la actividad de los usuarios para ver otros indicadores de riesgo y explore el ámbito de impacto. Además, póngase en contacto con el usuario, confirme sus acciones legítimas y, a continuación, asegúrese de deshabilitar o eliminar las máquinas virtuales en peligro.
- **B-TP** : Si después de la investigación, puede confirmar que el administrador está autorizado para realizar estas actividades de creación.

    **Acción recomendada** : descartar la alerta.

**Comprender el ámbito de la vulneración de seguridad**

1. Revise toda la actividad de los usuarios para ver otros indicadores de riesgo.
1. Revise los recursos creados o modificados por el usuario y compruebe que cumplen con las directivas de su organización.

### <a name="suspicious-creation-activityfor-cloudregion-preview"></a>Actividad de creación sospechosa para la región de nube (versión preliminar)

Actividades que indican que un usuario ha realizado una acción de creación de recursos inusual en una región de AWS no común en comparación con la base de referencia aprendida. La creación de recursos en regiones en la nube poco frecuentes podría indicar un intento de realizar una actividad malintencionada, como operaciones de minería de datos de cifrado de dentro de su organización.

**Período de aprendizaje**

El establecimiento del patrón de actividad de un usuario nuevo requiere un período de aprendizaje inicial de siete días durante el cual no se desencadenan alertas para las nuevas ubicaciones.

**TP** , **B-TP** o **FP** ?

Para mejorar la precisión y alertar solo cuando hay una indicación fuerte de una infracción, esta detección establece una línea base en cada entorno de la organización para reducir los incidentes **B-TP** .

- **TP** : si es capaz de confirmar que las actividades de creación no fueron realizadas por un usuario legítimo.

    **Acción recomendada** : suspenda al usuario, restablezca la contraseña y examine todos los dispositivos en busca de amenazas malintencionadas. Revise toda la actividad de los usuarios para ver otros indicadores de riesgo y explore el ámbito de impacto. Además, póngase en contacto con el usuario, confirme sus acciones legítimas y, a continuación, asegúrese de deshabilitar o eliminar los recursos en peligro en la nube.
- **B-TP** : Si después de la investigación, puede confirmar que el administrador está autorizado para realizar estas actividades de creación.

    **Acción recomendada** : descartar la alerta.

**Comprender el ámbito de la vulneración de seguridad**

1. Revise toda la actividad de los usuarios para ver otros indicadores de riesgo.
1. Revise los recursos creados y compruebe que cumplen con las directivas de su organización.

## <a name="persistence-alerts"></a>Alertas de persistencia

En esta sección se describen las alertas que indican que un actor malintencionado puede estar intentando mantener su punto de la organización.

### <a name="activity-performed-by-terminated-user"></a>Actividad realizada por el usuario cancelado

La actividad realizada por un usuario Terminado puede indicar que un empleado terminado que todavía tiene acceso a los recursos corporativos está intentando realizar una actividad malintencionada. Cloud App Security perfiles a los usuarios de la organización y desencadena una alerta cuando un usuario Terminado realiza una actividad.

**TP** , **B-TP** o **FP** ?

1. **TP** : si se puede confirmar que el usuario terminado todavía tiene acceso a determinados recursos corporativos y está realizando actividades.

    **Acción recomendada** : deshabilitar el usuario.
1. **B-TP** : si se puede determinar que el usuario se ha deshabilitado temporalmente o se ha eliminado y se ha vuelto a registrar.

    **Acción recomendada** : descartar la alerta.

**Comprender el ámbito de la vulneración de seguridad**

1. Registros de recursos humanos de referencia cruzada para confirmar que el usuario ha finalizado.
1. Valide la existencia de la cuenta de usuario de Azure Active Directory (Azure AD).
    > [!NOTE]
    > Si usa Azure AD Connect, valide el objeto de Active Directory local y confirme un ciclo de sincronización correcto.
1. Identifique todas las aplicaciones a las que el usuario Terminado tenía acceso y retirar las cuentas.
1. Actualice los procedimientos de retirada.

### <a name="suspicious-change-of-cloudtrail-logging-service"></a>Cambio sospechoso del servicio de registro de CloudTrail

Actividades en una única sesión que indica que un usuario ha realizado cambios sospechosos en el servicio de registro de CloudTrail de AWS. Esto puede indicar un intento de infracción de la organización. Al deshabilitar CloudTrail, ya no se registran los cambios operativos. Un atacante puede realizar actividades malintencionadas al tiempo que evita un evento de auditoría CloudTrail, como la modificación de un cubo S3 de privado a público.

**TP** , **B-TP** o **FP** ?

1. **TP** : si es capaz de confirmar que un usuario legítimo no ha realizado la actividad.

    **Acción recomendada** : suspender al usuario, restablecer la contraseña e invertir la actividad CloudTrail.
1. **FP** : si es capaz de confirmar que el usuario ha deshabilitado de forma legítima el servicio CloudTrail.

    **Acción recomendada** : descartar la alerta.

**Comprender el ámbito de la vulneración de seguridad**

1. Revise el registro de actividad para ver otros indicadores de riesgo y vea quién realizó el cambio en el servicio CloudTrail.
1. Opcional: cree una guía de uso de Power Automatic para ponerse en contacto con los usuarios y sus administradores para comprobar su actividad.

### <a name="suspicious-email-deletion-activity-by-user"></a>Actividad de eliminación de correo electrónico sospechoso (por usuario)

Actividades en una única sesión que indica que un usuario realizó eliminaciones de correo electrónico sospechosas. Esto puede indicar un intento de infracción de la organización, por ejemplo, que los atacantes intentan enmascarar las operaciones mediante la eliminación de correos electrónicos relacionados con las actividades de correo no deseado.

**TP** , **B-TP** o **FP** ?

1. **TP** : si es capaz de confirmar que un usuario legítimo no ha realizado la actividad.

    **Acción recomendada** : suspender al usuario, marcar el usuario como comprometido y restablecer su contraseña.
1. **FP** : si es capaz de confirmar que el usuario ha creado legítimamente una regla para eliminar mensajes.

    **Acción recomendada** : descartar la alerta.

**Comprender el ámbito de la vulneración de seguridad**

- Revise toda la actividad de los usuarios para ver indicadores adicionales de riesgo, como la alerta de [reenvío de bandeja de entrada sospechosa](#suspicious-inbox-forwarding) seguido de una alerta de [viaje imposible](#impossible-travel) . Buscar:

    1. Nuevas reglas de reenvío de SMTP, como se indica a continuación:
        - Compruebe los nombres de las reglas de reenvío malintencionado. Los nombres de las reglas pueden variar con respecto a nombres simples, como "reenviar todos los mensajes de correo electrónico" y "reenviar automáticamente", o nombres engañosos, como un "." apenas visible. Los nombres de las reglas de reenvío pueden estar incluso vacíos y el destinatario del reenvío puede ser una sola cuenta de correo electrónico o una lista completa. También se pueden ocultar reglas malintencionadas de la interfaz de usuario. Una vez detectado, puede usar esta [entrada de blog](/archive/blogs/hkong/how-to-delete-corrupted-hidden-inbox-rules-from-a-mailbox-using-mfcmapi) útil para eliminar reglas ocultas de los buzones.
        - Si detecta una regla de reenvío no reconocida en una dirección de correo electrónico interna o externa desconocida, puede suponer que la cuenta de bandeja de entrada se ha puesto en peligro.
    1. Nuevas reglas de bandeja de entrada, como "eliminar todo", "trasladar mensajes a otra carpeta" o aquellas con convenciones de nomenclatura ocultas, por ejemplo "...".
    1. Aumento en los mensajes de correo electrónico enviados.

### <a name="suspicious-inbox-manipulation-rule"></a>Regla de manipulación de bandeja de entrada sospechosa

Actividades que indican que un atacante ha obtenido acceso a la bandeja de entrada de un usuario y ha creado una regla sospechosa. Las reglas de manipulación, como eliminar o mover mensajes, o carpetas, desde la bandeja de entrada de un usuario pueden ser un intento de pasar información de la organización. De forma similar, pueden indicar un intento de manipular la información que un usuario ve o para usar su bandeja de entrada para distribuir correo no deseado, correos electrónicos de suplantación de identidad (phishing) o malware. Cloud App Security genera perfiles de su entorno y desencadena alertas cuando se detectan reglas de manipulación de bandeja de entrada sospechosas en la bandeja de entrada de un usuario. Esto puede indicar que la cuenta del usuario está en peligro.

**TP** , **B-TP** o **FP** ?

1. **TP** : si es capaz de confirmar que se ha creado una regla de bandeja de entrada malintencionada y que la cuenta se ha puesto en peligro.

    **Acción recomendada** : suspenda al usuario, restablezca la contraseña y quite la regla de reenvío.
1. **FP** : si es capaz de confirmar que un usuario ha creado la regla de forma legítima.

    **Acción recomendada** : descartar la alerta.

**Comprender el ámbito de la vulneración de seguridad**

1. Revise toda la actividad de los usuarios para ver indicadores adicionales de riesgo, como la alerta de [reenvío de bandeja de entrada sospechosa](#suspicious-inbox-forwarding) seguido de una alerta de [viaje imposible](#impossible-travel) . Buscar:
    - Nuevas reglas de reenvío de SMTP.
    - Nuevas reglas de bandeja de entrada, como "eliminar todo", "trasladar mensajes a otra carpeta" o aquellas con convenciones de nomenclatura ocultas, por ejemplo "...".
1. Recopilar información de dirección IP y ubicación para la acción.
1. Revise las actividades realizadas desde la dirección IP utilizada para crear la regla para detectar otros usuarios en peligro.

## <a name="privilege-escalation-alerts"></a>Alertas de escalado de privilegios

En esta sección se describen las alertas que indican que un actor malintencionado puede estar intentando obtener permisos de nivel superior en la organización.

### <a name="unusual-administrative-activity-by-user"></a>Actividad administrativa inusual (por usuario)

Actividades que indican que un atacante ha puesto en peligro una cuenta de usuario y ha realizado acciones administrativas que no son comunes para ese usuario. Por ejemplo, un atacante puede intentar cambiar una configuración de seguridad para un usuario, una operación que es relativamente poco habitual para un usuario común. Cloud App Security crea una línea base basada en el comportamiento del usuario y desencadena una alerta cuando se detecta el comportamiento inusual.

**Período de aprendizaje**

El establecimiento del patrón de actividad de un usuario nuevo requiere un período de aprendizaje inicial de siete días durante el cual no se desencadenan alertas para las nuevas ubicaciones.

**TP** , **B-TP** o **FP** ?

1. **TP** : si es capaz de confirmar que un administrador legítimo no ha realizado la actividad.

    **Acción recomendada** : suspender al usuario, marcar el usuario como comprometido y restablecer su contraseña.
1. **FP** : si es capaz de confirmar que un administrador ha realizado legítimamente el volumen inusual de actividades administrativas.

    **Acción recomendada** : descartar la alerta.

**Comprender el ámbito de la vulneración de seguridad**

1. Revise toda la actividad de los usuarios para ver indicadores adicionales de riesgo, como el [reenvío de bandeja de entrada sospechoso](#suspicious-inbox-forwarding) o un [viaje imposible](#impossible-travel).
1. Revise otros cambios de configuración, como la creación de una cuenta de usuario que pueda usarse para la persistencia.

## <a name="credential-access-alerts"></a>Alertas de acceso de credenciales

En esta sección se describen las alertas que indican que un actor malintencionado puede estar intentando robar nombres de cuenta y contraseñas de su organización.

### <a name="multiple-failed-login-attempts"></a>Varios intentos incorrectos de inicio de sesión

Los intentos de inicio de sesión erróneos podrían indicar un intento de incumplimiento de una cuenta. Sin embargo, los inicios de sesión erróneos también pueden ser un comportamiento normal. Por ejemplo, cuando un usuario escribió una contraseña incorrecta por equivocación. Para lograr precisión y alertar solo cuando hay una indicación fuerte de una infracción inesperada, Cloud App Security establece una línea base de hábitos de inicio de sesión para cada usuario de la organización y solo alerta cuando se detecta el comportamiento inusual.

**Período de aprendizaje**

El establecimiento del patrón de actividad de un usuario nuevo requiere un período de aprendizaje inicial de siete días durante el cual no se desencadenan alertas para las nuevas ubicaciones.

**TP** , **B-TP** o **FP** ?

Esta Directiva se basa en el aprendizaje del comportamiento normal de inicio de sesión de un usuario. Cuando se detecta una desviación de la norma, se desencadena una alerta. Si la detección comienza para ver que el mismo comportamiento continúa, la alerta solo se genera una vez.

1. **TP** (error de MFA): si es capaz de confirmar que MFA funciona correctamente, podría ser un signo de un ataque por fuerza bruta intentada.

    **Acciones recomendadas** :
    1. Suspenda al usuario, marque el usuario como comprometido y restablezca la contraseña.
    1. Busque la aplicación que realizó las autenticaciones con errores y vuelva a configurarla.
    1. Busque otros usuarios que hayan iniciado sesión en torno a la hora de la actividad, ya que también pueden estar en peligro. Suspenda al usuario, marque el usuario como comprometido y restablezca la contraseña.
1. **B-TP** (error de MFA): si es capaz de confirmar que la alerta se debe a un problema con MFA.

    **Acción recomendada** : cree una guía con Power Automate para ponerse en contacto con el usuario y comprobar si hay problemas con MFA.
1. **B-TP** (aplicación configurada de forma incorrecta): si es capaz de confirmar que una aplicación mal configurada está intentando conectarse a un servicio varias veces con credenciales expiradas.

    **Acción recomendada** : descartar la alerta.
1. **B-TP** (contraseña modificada): si es capaz de confirmar que un usuario ha cambiado recientemente su contraseña, pero no ha afectado a las credenciales a través de recursos compartidos de red.

    **Acción recomendada** : descartar la alerta.
1. **B-TP** (prueba de seguridad): si es capaz de confirmar que los analistas de seguridad llevan a cabo una prueba de seguridad o penetración en nombre de la organización.

    **Acción recomendada** : descartar la alerta.

**Comprender el ámbito de la vulneración de seguridad**

1. Revise toda la actividad de los usuarios en busca de indicadores adicionales de riesgo, como la alerta va seguida de una de las siguientes alertas: [viaje imposible](#impossible-travel), [actividad de la dirección IP anónima](#activity-from-anonymous-ip-address)o [actividad del país poco frecuente](#activity-from-infrequent-country).
1. Revise la siguiente información del dispositivo de usuario y compárela con la información de dispositivo conocida:
    - Sistema operativo y versión
    - Explorador y versión
    - Dirección IP y ubicación
1. Identifique la dirección IP de origen o la ubicación en la que se ha producido el intento de autenticación.
1. Identifique si el usuario ha cambiado recientemente su contraseña y asegúrese de que todas las aplicaciones y dispositivos tienen la contraseña actualizada.

## <a name="collection-alerts"></a>Alertas de recopilación

En esta sección se describen las alertas que indican que un actor malintencionado puede estar intentando recopilar datos de interés para su objetivo de su organización.

### <a name="multiple-power-bi-report-sharing-activities"></a>Varias actividades de uso compartido de informes Power BI

Actividades en una única sesión que indica que un usuario ha realizado un número inusual de actividades de informe de recursos compartidos en Power BI en comparación con la base de referencia aprendida. Esto puede indicar un intento de infracción de la organización.

**Período de aprendizaje**

El establecimiento del patrón de actividad de un usuario nuevo requiere un período de aprendizaje inicial de siete días durante el cual no se desencadenan alertas para las nuevas ubicaciones.

**TP** , **B-TP** o **FP** ?

1. **TP** : si es capaz de confirmar que un usuario legítimo no ha realizado la actividad.

    **Acción recomendada** : quitar el acceso compartido de Power BI. Si es capaz de confirmar que la cuenta está en peligro, suspenda al usuario, marque el usuario como comprometido y restablezca la contraseña.
1. **FP** : si es capaz de confirmar que el usuario tenía una justificación comercial para compartir estos informes.

    **Acción recomendada** : descartar la alerta.

**Comprender el ámbito de la vulneración de seguridad**

1. Revise el registro de actividad para obtener una mejor comprensión de otras actividades realizadas por el usuario. Fíjese en la dirección IP desde la que ha iniciado sesión y los detalles del dispositivo.
1. Póngase en contacto con su equipo de Power BI o Information Protection equipo para comprender las directrices para compartir informes interna y externamente.

### <a name="suspicious-power-bi-report-sharing"></a>Uso compartido de informe de Power BI sospechoso

Actividades que indican que un usuario ha compartido un informe de Power BI que puede contener información confidencial identificada mediante NLP para analizar los metadatos del informe. El informe se ha compartido con una dirección de correo electrónico externa, se ha publicado en la web o se ha entregado una instantánea a una dirección de correo electrónico suscrita externamente. Esto puede indicar un intento de infracción de la organización.

**TP** , **B-TP** o **FP** ?

1. **TP** : si es capaz de confirmar que un usuario legítimo no ha realizado la actividad.

    **Acción recomendada** : quitar el acceso compartido de Power BI. Si es capaz de confirmar que la cuenta está en peligro, suspenda al usuario, marque el usuario como comprometido y restablezca la contraseña.
1. **FP** : si es capaz de confirmar que el usuario tenía una justificación comercial para compartir estos informes.

    **Acción recomendada** : descartar la alerta.

**Comprender el ámbito de la vulneración de seguridad**

1. Revise el registro de actividad para obtener una mejor comprensión de otras actividades realizadas por el usuario. Fíjese en la dirección IP desde la que ha iniciado sesión y los detalles del dispositivo.
1. Póngase en contacto con su equipo de Power BI o Information Protection equipo para comprender las directrices para compartir informes interna y externamente.

### <a name="unusual-impersonated-activity-by-user"></a>Actividad suplantada inusual (por usuario)

En cierto software, hay opciones para permitir que otros usuarios suplanten a otros usuarios. Por ejemplo, los servicios de correo electrónico permiten que un usuario autorice a otros a enviar correos electrónicos en su nombre. Esta actividad la suelen usar los atacantes para crear mensajes de correo electrónico de suplantación de identidad en un intento de extraer información acerca de su organización. Cloud App Security crea una línea base basada en el comportamiento del usuario y crea una actividad cuando se detecta una actividad de suplantación inusual.

**Período de aprendizaje**

El establecimiento del patrón de actividad de un usuario nuevo requiere un período de aprendizaje inicial de siete días durante el cual no se desencadenan alertas para las nuevas ubicaciones.

**TP** , **B-TP** o **FP** ?

1. **TP** : si es capaz de confirmar que un usuario legítimo no ha realizado la actividad.

    **Acción recomendada** : suspender al usuario, marcar el usuario como comprometido y restablecer su contraseña.
1. **FP** (comportamiento inusual): si es capaz de confirmar que el usuario ha realizado legítimamente las actividades inusuales o más actividades que la línea base establecida.

    **Acción recomendada** : descartar la alerta.
1. **FP** : si es capaz de confirmar que las aplicaciones, como los equipos, suplantan al usuario de forma legítima.

    **Acción recomendada** : Revise las acciones y descartar la alerta si es necesario.

**Comprender el ámbito de la vulneración de seguridad**

1. Revise todas las alertas y la actividad de los usuarios para ver más indicadores de riesgo.
1. Revise las actividades de suplantación para identificar posibles actividades malintencionadas.
1. Revise la configuración de acceso delegado.

## <a name="exfiltration-alerts"></a>Alertas de filtración

En esta sección se describen las alertas que indican que un actor malintencionado puede estar intentando robar datos de la organización.

### <a name="suspicious-inbox-forwarding"></a>Reenvío sospechoso desde la bandeja de entrada

Actividades que indican que un atacante ha obtenido acceso a la bandeja de entrada de un usuario y ha creado una regla sospechosa. Las reglas de manipulación, como reenviar todos los mensajes o correos electrónicos específicos a otra cuenta de correo electrónico, pueden tratar de transmitir información de su organización. Cloud App Security genera perfiles de su entorno y desencadena alertas cuando se detectan reglas de manipulación de bandeja de entrada sospechosas en la bandeja de entrada de un usuario. Esto puede indicar que la cuenta del usuario está en peligro.

**TP** , **B-TP** o **FP** ?

1. **TP** : si es capaz de confirmar que se ha creado una regla de reenvío de bandeja de entrada malintencionada y que la cuenta se ha puesto en peligro.

    **Acción recomendada** : suspenda al usuario, restablezca la contraseña y quite la regla de reenvío.
1. **FP** : si es capaz de confirmar que el usuario ha creado una regla de reenvío en una cuenta de correo electrónico externa nueva o personal por motivos legítimos.

    **Acción recomendada** : descartar la alerta.

**Comprender el ámbito de la vulneración de seguridad**

1. Revise toda la actividad de los usuarios para ver indicadores adicionales de riesgo, como la alerta va seguida de una alerta de [viaje imposible](#impossible-travel) . Buscar:

    1. Nuevas reglas de reenvío de SMTP, como se indica a continuación:
        - Compruebe los nombres de las reglas de reenvío malintencionado. Los nombres de las reglas pueden variar con respecto a nombres simples, como "reenviar todos los mensajes de correo electrónico" y "reenviar automáticamente", o nombres engañosos, como un "." apenas visible. Los nombres de las reglas de reenvío pueden estar incluso vacíos y el destinatario del reenvío puede ser una sola cuenta de correo electrónico o una lista completa. También se pueden ocultar reglas malintencionadas de la interfaz de usuario. Una vez detectado, puede usar esta [entrada de blog](/archive/blogs/hkong/how-to-delete-corrupted-hidden-inbox-rules-from-a-mailbox-using-mfcmapi) útil para eliminar reglas ocultas de los buzones.
        - Si detecta una regla de reenvío no reconocida en una dirección de correo electrónico interna o externa desconocida, puede suponer que la cuenta de bandeja de entrada se ha puesto en peligro.
    1. Nuevas reglas de bandeja de entrada, como "eliminar todo", "trasladar mensajes a otra carpeta" o aquellas con convenciones de nomenclatura ocultas, por ejemplo "...".
1. Revise las actividades realizadas desde la dirección IP utilizada para crear la regla para detectar otros usuarios en peligro.
1. Revise la lista de mensajes reenviados mediante el seguimiento de mensajes de Exchange Online.

### <a name="unusual-file-download-by-user"></a>Descarga de archivos inusuales (por usuario)

Actividades que indican que un usuario ha realizado un número inusual de descargas de archivos desde una plataforma de almacenamiento en la nube en comparación con la base de referencia aprendida. Esto puede indicar un intento de obtener información acerca de la organización. Cloud App Security crea una línea base basada en el comportamiento del usuario y desencadena una alerta cuando se detecta el comportamiento inusual.

**Período de aprendizaje**

El establecimiento del patrón de actividad de un usuario nuevo requiere un período de aprendizaje inicial de siete días durante el cual no se desencadenan alertas para las nuevas ubicaciones.

**TP** , **B-TP** o **FP** ?

1. **TP** : si es capaz de confirmar que un usuario legítimo no ha realizado la actividad.

    **Acción recomendada** : suspender al usuario, marcar el usuario como comprometido y restablecer su contraseña.
1. **FP** (comportamiento inusual): si puede confirmar que el usuario ha realizado legítimamente más actividades de descarga de archivos que la línea base establecida.

    **Acción recomendada** : descartar la alerta.
1. **FP** (sincronización de software): si se puede confirmar que el software, como OneDrive, está sincronizado con una copia de seguridad externa que produjo la alerta.

    **Acción recomendada** : descartar la alerta.

**Comprender el ámbito de la vulneración de seguridad**

1. Revise las actividades de descarga y cree una lista de archivos descargados.
1. Revise la confidencialidad de los archivos descargados con el propietario del recurso y valide el nivel de acceso.

### <a name="unusual-file-share-activity-by-user"></a>Actividad de recurso compartido de archivos inusual (por usuario)

Actividades que indican que un usuario ha realizado un número inusual de acciones de uso compartido de archivos desde una plataforma de almacenamiento en la nube en comparación con la base de referencia aprendida. Esto puede indicar un intento de obtener información acerca de la organización. Cloud App Security crea una línea base basada en el comportamiento del usuario y desencadena una alerta cuando se detecta el comportamiento inusual.

**Período de aprendizaje**

El establecimiento del patrón de actividad de un usuario nuevo requiere un período de aprendizaje inicial de siete días durante el cual no se desencadenan alertas para las nuevas ubicaciones.

**TP** , **B-TP** o **FP** ?

1. **TP** : si es capaz de confirmar que un usuario legítimo no ha realizado la actividad.

    **Acción recomendada** : suspender al usuario, marcar el usuario como comprometido y restablecer su contraseña.
1. **FP** (comportamiento inusual): si es capaz de confirmar que el usuario ha realizado legítimamente más actividades de uso compartido de archivos que la línea base establecida.

    **Acción recomendada** : descartar la alerta.

**Comprender el ámbito de la vulneración de seguridad**

1. Revise las actividades de uso compartido y cree una lista de archivos compartidos.
1. Revise la confidencialidad de los archivos compartidos con el propietario del recurso y valide el nivel de acceso.
1. Cree una directiva de archivo para documentos similares para detectar el uso compartido de archivos confidenciales en el futuro.

## <a name="impact-alerts"></a>Alertas de impacto

En esta sección se describen las alertas que indican que un actor malintencionado puede estar intentando manipular, interrumpir o destruir los sistemas y datos de la organización.

### <a name="multiple-delete-vm-activities"></a>Varias actividades de eliminación de VM

Actividades en una única sesión que indica que un usuario ha realizado un número inusual de eliminaciones de la máquina virtual en comparación con la base de referencia aprendida. La eliminación de varias máquinas virtuales puede indicar un intento de interrumpir o destruir un entorno. Sin embargo, hay muchos escenarios normales en los que se eliminan las máquinas virtuales.

**TP** , **B-TP** o **FP** ?

Para mejorar la precisión y alertar solo cuando hay una indicación fuerte de una infracción, esta detección establece una línea base en cada entorno de la organización para reducir los incidentes **B-TP** y solo alerta cuando se detecta el comportamiento inusual.

**Período de aprendizaje**

El establecimiento del patrón de actividad de un usuario nuevo requiere un período de aprendizaje inicial de siete días durante el cual no se desencadenan alertas para las nuevas ubicaciones.

- **TP** : si es capaz de confirmar que las eliminaciones no se autorizaron.

    **Acción recomendada** : suspenda al usuario, restablezca la contraseña y examine todos los dispositivos en busca de amenazas malintencionadas. Revise toda la actividad de los usuarios para ver otros indicadores de riesgo y explore el ámbito de impacto.
- **B-TP** : Si después de la investigación, puede confirmar que el administrador está autorizado para realizar estas actividades de eliminación.

    **Acción recomendada** : descartar la alerta.

**Comprender el ámbito de la vulneración de seguridad**

1. Póngase en contacto con el usuario y confirme la actividad.
1. Revise toda la actividad de los usuarios en busca de indicadores adicionales de riesgo, como la alerta va seguida de una de las siguientes alertas: [viaje imposible](#impossible-travel), [actividad de la dirección IP anónima](#activity-from-anonymous-ip-address)o [actividad del país poco frecuente](#activity-from-infrequent-country).

### <a name="ransomware-activity"></a>Actividad de ransomware

Ransomware es un cyberattack en el que un atacante bloquea a las víctimas fuera de sus dispositivos o impide que tengan acceso a sus archivos hasta que el víctima pague un Ransom. Ransomware puede distribuirse mediante un archivo compartido malintencionado o una red en peligro. Cloud App Security usa la experiencia de investigación de seguridad, la inteligencia de amenazas y los patrones de comportamiento aprendidos para identificar la actividad de ransomware. Por ejemplo, una alta tasa de cargas de archivos, o eliminaciones de archivos, puede representar un proceso de cifrado que es común entre las operaciones de ransomware.

Esta detección establece una línea base de los patrones de trabajo normales de cada usuario de la organización, por ejemplo, cuando el usuario accede a la nube y lo que hace normalmente en la nube.

Las directivas de detección de amenazas automatizadas de Cloud App Security empiezan a ejecutarse en segundo plano desde el momento en que se conecta. El uso de nuestra experiencia en investigación de seguridad para identificar patrones de comportamiento que reflejan la actividad de ransomware en nuestra organización, Cloud App Security ofrece una completa cobertura frente a ataques de ransomware sofisticados.

**Período de aprendizaje**

El establecimiento del patrón de actividad de un usuario nuevo requiere un período de aprendizaje inicial de siete días durante el cual no se desencadenan alertas para las nuevas ubicaciones.

**TP** , **B-TP** o **FP** ?

1. **TP** : si es capaz de confirmar que el usuario no ha realizado la actividad.

    **Acción recomendada** : suspender al usuario, marcar el usuario como comprometido y restablecer su contraseña.
1. **FP** (comportamiento inusual): el usuario realizó legítimamente varias actividades de eliminación y carga de archivos similares en un breve período de tiempo.

    **Acción recomendada** : después de revisar el registro de actividad y confirmar que las extensiones de archivo no son sospechosas, descartar la alerta.
1. **FP** (extensión de archivo de ransomware común): si es capaz de confirmar que las extensiones de los archivos afectados coinciden con una extensión de ransomware conocida.

    **Acción recomendada** : póngase en contacto con el usuario y confirme que los archivos son seguros y, a continuación, descarte la alerta.

**Comprender el ámbito de la vulneración de seguridad**

1. Revise el registro de actividad para ver otros indicadores de riesgo, como la descarga masiva o la eliminación masiva de archivos.
1. Si usa Microsoft defender para el punto de conexión, revise las alertas del equipo del usuario para ver si se detectaron archivos malintencionados.
1. Busque en el registro de actividad actividades de uso compartido y carga de archivos malintencionadas.

### <a name="unusual-file-deletion-activity-by-user"></a>Actividad de eliminación de archivos inusual (por usuario)

Actividades que indican que un usuario realizó una actividad de eliminación de archivos inusual en comparación con la base de referencia aprendida. Esto puede indicar un ataque por ransomware. Por ejemplo, un atacante puede cifrar los archivos de un usuario y eliminar todos los originales, con solo las versiones cifradas que se pueden utilizar para forzar a la víctima de pagar un Ransom. Cloud App Security crea una línea base basada en el comportamiento normal del usuario y desencadena una alerta cuando se detecta el comportamiento inusual.

**Período de aprendizaje**

El establecimiento del patrón de actividad de un usuario nuevo requiere un período de aprendizaje inicial de siete días durante el cual no se desencadenan alertas para las nuevas ubicaciones.

**TP** , **B-TP** o **FP** ?

1. **TP** : si es capaz de confirmar que un usuario legítimo no ha realizado la actividad.

    **Acción recomendada** : suspender al usuario, marcar el usuario como comprometido y restablecer su contraseña.
1. **FP** : si es capaz de confirmar que el usuario ha realizado legítimamente más actividades de eliminación de archivos que la línea base establecida.

    **Acción recomendada** : descartar la alerta.

**Comprender el ámbito de la vulneración de seguridad**

1. Revise las actividades de eliminación y cree una lista de los archivos eliminados. Si es necesario, recupere los archivos eliminados.
1. Opcionalmente, puede crear una guía mediante la automatización de la energía para ponerse en contacto con los usuarios y sus administradores para comprobar la actividad.

## <a name="see-also"></a>Vea también

> [!div class="nextstepaction"]
> [Tutorial: Investigación de usuarios de riesgo](tutorial-ueba.md)