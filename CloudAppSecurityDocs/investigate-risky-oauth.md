---
title: 'Investigación de las aplicaciones de OAuth de riesgo: Cloud App Security'
description: En este artículo se proporciona información sobre cómo investigar aplicaciones de OAuth de riesgo en Cloud App Security.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 9/1/2019
ms.topic: tutorial
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 2c6b6ffc3b2c89dc107f223e1f0177df4fa8155b
ms.sourcegitcommit: b15034dd50142afd8e95de22a9232f711b1eae6e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2020
ms.locfileid: "85624705"
---
# <a name="tutorial-investigate-risky-oauth-apps"></a>Tutorial: Investigación de aplicaciones de OAuth de riesgo

*Se aplica a: Microsoft Cloud App Security*

OAuth es un estándar abierto para la autenticación y autorización basadas en tokens. OAuth permite usar la información de la cuenta de un usuario por parte de servicios de terceros, sin exponer la contraseña del usuario. OAuth actúa como intermediario en nombre del usuario y proporciona al servicio un token de acceso que autoriza el uso compartido de información específica de la cuenta.

Por ejemplo, una aplicación que analiza el calendario del usuario y le da consejos sobre cómo ser más productivo necesita acceder al calendario del usuario. En lugar de proporcionar las credenciales del usuario, OAuth permite a la aplicación acceder a los datos basándose únicamente en un token, que se genera cuando el usuario da su consentimiento a una página, como se puede ver en la siguiente imagen.

![Permiso de aplicación por OAuth](media/oauth-permission.png)

Muchas aplicaciones de terceros que podrían instalar los usuarios empresariales de la organización, solicitar permiso para acceder a la información y los datos de usuario e iniciar sesión en nombre del usuario en otras aplicaciones en la nube. Cuando los usuarios instalan estas aplicaciones, suelen hacer clic en **aceptar** sin revisar atentamente los detalles en el símbolo del sistema, incluida la concesión de permisos a la aplicación. La aceptación de permisos de aplicación de terceros es un riesgo de seguridad potencial para la organización.

Por ejemplo, la siguiente página de consentimiento de aplicación de OAuth puede parecer legítima para el usuario medio; sin embargo, el "explorador de API de Google" no debería necesitar solicitar permisos a Google. Esto indica que la aplicación podría ser un intento de suplantación de identidad, no relacionado en absoluto con Google.

![Suplantación de identidad de OAuth](media/oauth-phishing.png)

Como administrador de seguridad, necesita visibilidad y control sobre las aplicaciones de su entorno, lo que incluye los permisos que tienen. Necesita la capacidad de evitar el uso de aplicaciones que requieren permiso para los recursos que desea revocar. Por lo tanto, Microsoft Cloud App Security le ofrece la capacidad de investigar y supervisar los permisos de aplicaciones que sus usuarios otorgaron. Este artículo está dedicado a ayudarle a investigar las aplicaciones de OAuth de su organización y a centrarse en las aplicaciones que es más probable que sean sospechosas.

Nuestro enfoque recomendado es investigar las aplicaciones con las funciones y la información que se proporcionan en el portal de Cloud App Security para filtrar las aplicaciones con una baja probabilidad de resultar peligrosas y centrarse en las aplicaciones sospechosas.

## <a name="how-to-detect-risky-oauth-apps"></a>Cómo detectar las aplicaciones de OAuth de riesgo

La detección de una aplicación de OAuth de riesgo se puede lograr mediante:

- **Alertas**: Reaccionar a una alerta desencadenada por una directiva existente.
- **Búsqueda**: Buscar una aplicación de riesgo entre todas las aplicaciones disponibles, sin sospechas concretas de riesgo.

### <a name="detect-risky-apps-using-alerts"></a>Detección de aplicaciones de riesgo mediante alertas

Puede establecer directivas para enviar automáticamente notificaciones cuando una aplicación de OAuth cumpla determinados criterios. Por ejemplo, puede establecer una directiva para que le notifique automáticamente cuando se detecte una aplicación que requiera permisos elevados y que se haya autorizado por más de 50 usuarios. Para más información sobre la creación de directivas de OAuth, consulte [Directivas de aplicación de OAuth](app-permission-policy.md).

### <a name="detect-risky-apps-by-hunting"></a>Detección de aplicaciones de riesgo mediante la búsqueda

1. En el portal, vaya a **Investigar** y, a continuación, **Aplicaciones de OAuth**. Utilice los filtros y las consultas para revisar lo que sucede en su entorno:

    - Establezca el filtro en **Nivel de permiso de alta gravedad** y **Uso comunitario no común**. Con este filtro, puede centrarse en aplicaciones con un potencial de alto riesgo en las que los usuarios puedan haber subestimado el riesgo.
    - En **Permisos** seleccione todas las opciones que sean particularmente de riesgo en un contexto específico. Por ejemplo, puede seleccionar todos los filtros que permiten el acceso al correo electrónico, como **Acceso total a todos los buzones de correo** y luego revisar la lista de aplicaciones para asegurarse de que todas realmente necesitan acceso relacionado con el correo. Esto le puede ayudar a investigar dentro de un contexto específico y a buscar aplicaciones que parecen legítimas, pero que contienen permisos innecesarios. Estas aplicaciones tienen más probabilidades de ser de riesgo.

        ![Suplantación de identidad de OAuth](media/oauth-filters.png)

    - Seleccione la consulta guardada **Aplicaciones que han autorizado los usuarios externos**. Con este filtro puede encontrar aplicaciones que quizás no estén alineadas con los estándares de seguridad de su empresa.
1. Una vez que revise las aplicaciones, puede centrarse en las aplicaciones de las consultas que parecen ser legítimas, pero que podrían en realidad ser de riesgo. Use los filtros para buscarlas:
    - Filtro para aplicaciones que están **autorizadas por un número reducido de usuarios**. Si se centra en estas aplicaciones, puede buscar aplicaciones de riesgo autorizadas por un usuario en peligro.
    - Aplicaciones que tienen permisos que no coinciden con el propósito de la aplicación, por ejemplo, una aplicación de reloj con acceso completo a todos los buzones.
1. Haga clic en cada aplicación para abrir el cajón de aplicaciones y compruebe si la aplicación tiene un nombre, editor o sitio web sospechoso.
1. Consulte la lista de aplicaciones y las aplicaciones de destino que tienen una fecha en **Última autorización** que no es reciente. Es posible que estas aplicaciones ya no sean necesarias.

    ![Cajón de aplicaciones de OAuth](media/oauth-drawer.png)

## <a name="how-to-investigate"></a>Investigación

Después de determinar que una aplicación es sospechosa y desea investigarla, recomendamos los siguientes principios clave para una investigación eficaz:

- Cuanto más común y utilizada sea una aplicación, ya sea por su organización o en línea, más probable es que sea segura.
- Una aplicación debe requerir solo permisos que estén relacionados con el propósito de la aplicación. Si no es así, la aplicación puede ser de riesgo.
- Las aplicaciones que requieren privilegios elevados o consentimiento del administrador tienen más probabilidades de ser de riesgo.

1. Haga clic en la aplicación para abrir el cajón de la aplicación y haga clic en el vínculo situado en **Actividades relacionadas**. Se abrirá la página del registro de actividad filtrada para las actividades realizadas por la aplicación. Tenga en cuenta que algunas aplicaciones realizan actividades que se registran como realizadas por un usuario. Estas actividades se quedan fuera automáticamente de los resultados del registro de actividad una vez aplicado el filtro. Para investigar más sobre el uso del registro de actividad, consulte [Registro de actividad](activity-filters.md).
1. Si una aplicación le resulta sospechosa, le recomendamos que investigue el nombre y el editor de la aplicación en distintas tiendas de aplicaciones. Céntrese en las siguientes aplicaciones, que podrían ser sospechosas:
    - Aplicaciones con un número reducido de descargas.
    - Aplicaciones con una clasificación o puntuación baja o con comentarios negativos.
    - Aplicaciones con un editor o sitio web sospechoso.
    - Aplicaciones con una fecha de última actualización no reciente. Esto podría ser signo de una aplicación que ya no se admite.
    - Aplicaciones que tienen permisos no pertinentes. Esto podría indicar que una aplicación es de riesgo.
1. Si la aplicación sigue siendo sospechosa, puede investigar el nombre de la aplicación, el editor y la dirección URL en línea.
1. Puede exportar la auditoría de aplicaciones de OAuth para un análisis más detallado de los usuarios que hayan autorizado una aplicación. Para obtener más información, vea [Auditoría de aplicaciones de OAuth](manage-app-permissions.md#oauth-app-auditing).

## <a name="how-to-remediate"></a>Cómo corregirlo

Después de determinar que una aplicación de OAuth es de riesgo, Cloud App Security ofrece las siguientes opciones de corrección:

- **Corrección manual**: Puede fácilmente [prohibir la revocación de una aplicación desde la página de aplicaciones de OAuth](manage-app-permissions.md#ban-or-approve-an-app).

- **Corrección automática**: Puede crear una directiva que [revoque automáticamente una aplicación o revoque a un usuario específico de una aplicación](app-permission-policy.md).

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Actividades diarias para proteger el entorno de nube](daily-activities-to-protect-your-cloud-environment.md)

[!INCLUDE [Open support ticket](includes/support.md)]
