---
title: 'Investigación de aplicaciones de OAuth de riesgo: Cloud App Security | Microsoft Docs'
description: En este artículo se proporciona información sobre cómo investigar las aplicaciones de riesgo de OAuth en Cloud App Security.
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
ms.openlocfilehash: 45d89b489fe017e0bc3f71c7785a4007b1a447e4
ms.sourcegitcommit: 6eff466c7a6817b14a60d8c3b2c201c7ae4c2e2c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "74720630"
---
# <a name="tutorial-investigate-risky-oauth-apps"></a>Tutorial: Investigación de aplicaciones de riesgo de OAuth

*Se aplica a: Microsoft Cloud App Security*

OAuth es un estándar abierto para autenticación y autorización basadas en tokens. OAuth permite que la información de la cuenta de un usuario sea utilizada por servicios de terceros, sin exponer la contraseña del usuario. OAuth actúa como un intermediario en nombre del usuario, proporcionando al servicio un token de acceso que autoriza el uso compartido de información específica de la cuenta.

Por ejemplo, una aplicación que analiza el calendario del usuario y le da consejos sobre cómo ser más productivo necesita acceder al calendario del usuario. En lugar de proporcionar las credenciales del usuario, OAuth permite a la aplicación acceder a los datos basándose únicamente en un token, que se genera cuando el usuario da su consentimiento a una página, como se puede ver en la siguiente imagen.

![Permiso de aplicación por OAuth](media/oauth-permission.png)

Muchas aplicaciones de terceros que puedan instalar los usuarios profesionales de su organización solicitan permiso para acceder a datos e información de usuario e iniciar sesión en nombre del usuario en otras aplicaciones de nube. Cuando los usuarios instalan estas aplicaciones, a menudo hacen clic en **Aceptar** sin revisar detenidamente los detalles en el mensaje, incluyendo la concesión de permisos a la aplicación. La aceptación de permisos de aplicación de terceros es un riesgo de seguridad potencial para la organización.

Por ejemplo, la siguiente página de consentimiento de aplicación de OAuth puede parecer legítima para el usuario medio; sin embargo, el "explorador de API de Google" no debería necesitar solicitar permisos a Google. Esto indica que la aplicación podría ser un intento de suplantación de identidad, no relacionado en absoluto con Google.

![Suplantación de identidad de OAuth](media/oauth-phishing.png)

Como administrador de seguridad, necesita visibilidad y control sobre las aplicaciones de su entorno, lo que incluye los permisos que tienen. Necesita la capacidad de evitar el uso de aplicaciones que requieren permiso para los recursos que desea revocar. Por lo tanto, Microsoft Cloud App Security le ofrece la capacidad de investigar y supervisar los permisos de aplicaciones que sus usuarios otorgaron. Este artículo pretende ayudarle a investigar las aplicaciones de OAuth de su organización y se centra en las aplicaciones que tienen más probabilidades de ser sospechosas.

Nuestro enfoque recomendado es investigar las aplicaciones utilizando las habilidades y la información proporcionadas en el portal de Cloud App Security para filtrar las aplicaciones con pocas posibilidades de ser de riesgo y centrarnos en las aplicaciones sospechosas.

## <a name="how-to-detect-risky-oauth-apps"></a>Cómo detectar las aplicaciones de OAuth de riesgo

La detección de una aplicación de OAuth de riesgo se puede lograr mediante:

- **Alertas**: Reaccionar a una alerta desencadenada por una directiva existente.
- **Búsqueda**: Buscar una aplicación de riesgo entre todas las aplicaciones disponibles, sin sospechas concretas de riesgo.

### <a name="detect-risky-apps-using-alerts"></a>Detección de aplicaciones de riesgo mediante alertas

Puede establecer directivas para enviar automáticamente notificaciones cuando una aplicación de OAuth cumpla determinados criterios. Por ejemplo, puede establecer una directiva para que le notifique automáticamente cuando se detecte una aplicación que requiera permisos elevados y que se haya autorizado por más de 50 usuarios. Para más información sobre la creación de directivas de OAuth, consulte [Directivas de aplicación de OAuth](app-permission-policy.md).

### <a name="detect-risky-apps-by-hunting"></a>Detección de aplicaciones de riesgo mediante la búsqueda

1. En el portal, vaya a **Investigar** y, luego, a **Aplicaciones de OAuth**. Utilice los filtros y las consultas para revisar lo que sucede en su entorno:

    - Establezca el filtro en **Nivel de permiso de alta gravedad** y **Uso comunitario no común**. Con este filtro, puede centrarse en aplicaciones con un potencial de alto riesgo en las que los usuarios puedan haber subestimado el riesgo.
    - En **Permisos** seleccione todas las opciones que sean particularmente de riesgo en un contexto específico. Por ejemplo, puede seleccionar todos los filtros que permiten el acceso al correo electrónico, como **Acceso total a todos los buzones de correo** y luego revisar la lista de aplicaciones para asegurarse de que todas realmente necesitan acceso relacionado con el correo. Esto le puede ayudar a investigar dentro de un contexto específico y a buscar aplicaciones que parecen legítimas, pero que contienen permisos innecesarios. Estas aplicaciones tienen más probabilidades de ser de riesgo.

        ![Suplantación de identidad de OAuth](media/oauth-filters.png)

    - Seleccione la consulta guardada **Aplicaciones que han autorizado los usuarios externos**. Con este filtro puede encontrar aplicaciones que quizás no estén alineadas con los estándares de seguridad de su empresa.
1. Una vez que revise las aplicaciones, puede centrarse en las aplicaciones de las consultas que parecen ser legítimas, pero que podrían en realidad ser de riesgo. Use los filtros para buscarlas:
    - Filtro para aplicaciones que están **autorizadas por un número reducido de usuarios**. Si se centra en estas aplicaciones, puede buscar las aplicaciones riesgosas que fueron autorizadas por un usuario en peligro.
    - Las aplicaciones con permisos que no se ajustan a la finalidad de la aplicación, como una aplicación de reloj con acceso total a todos los buzones.
1. Haga clic en cada aplicación para abrir el cajón de aplicaciones y compruebe si la aplicación tiene un nombre, editor o sitio web sospechoso.
1. Vea la lista de aplicaciones y céntrese en las que tengan una fecha de **Última autorización** que no sea reciente. Puede que estas aplicaciones ya no sean necesarias.

    ![Cajón de aplicaciones de OAuth](media/oauth-drawer.png)

## <a name="how-to-investigate"></a>Procedimiento de investigación

Después de determinar que una aplicación es sospechosa y desea investigarla, recomendamos los siguientes principios clave para una investigación eficaz:

- Cuanto más común y utilizada sea una aplicación, ya sea por su organización o en línea, más probable es que sea segura.
- Una aplicación debe requerir solo permisos que estén relacionados con el propósito de la aplicación. Si no es así, la aplicación puede ser de riesgo.
- Las aplicaciones que requieren privilegios elevados o consentimiento del administrador tienen más probabilidades de ser de riesgo.

1. Haga clic en la aplicación para abrir el cajón de aplicaciones y luego en el vínculo bajo **Actividades relacionadas**. Se abrirá la página Registro de actividad filtrada según las actividades que realiza la aplicación. Tenga en cuenta que algunas aplicaciones realizan actividades que se registran como si las hubiera hecho un usuario. Estas actividades se filtran automáticamente fuera de los resultados del registro de actividad. Para realizar una investigación más detallada con el registro de actividad, consulte [Registro de actividad](activity-filters.md).
1. Si una aplicación le resulta sospechosa, le recomendamos que investigue el nombre y el editor de la aplicación en distintas tiendas de aplicaciones. Céntrese en las aplicaciones siguientes, que pueden ser sospechosas:
    - Aplicaciones con un número reducido de descargas.
    - Aplicaciones con una puntuación o clasificación baja o comentarios malos.
    - Aplicaciones con un editor o sitio web sospechoso.
    - Aplicaciones con una fecha de última actualización no reciente. Esto puede indicar que una aplicación ya no se admite.
    - Aplicaciones con permisos irrelevantes. Esto podría indicar que una aplicación es riesgosa.
1. Si la aplicación sigue siendo sospechosa, puede investigar la dirección URL, el editor y el nombre de la aplicación en línea.
1. Puede exportar la auditoría de aplicaciones de OAuth para un análisis más detallado de los usuarios que hayan autorizado una aplicación. Para obtener más información, vea [Auditoría de aplicaciones de OAuth](manage-app-permissions.md#oauth-app-auditing).

## <a name="how-to-remediate"></a>Cómo corregirlo

Después de determinar que una aplicación de OAuth es de riesgo, Cloud App Security ofrece las siguientes opciones de corrección:

- **Corrección manual**: Puede fácilmente [prohibir la revocación de una aplicación desde la página de aplicaciones de OAuth](manage-app-permissions.md#ban-or-approve-an-app).

- **Corrección automática**: Puede crear una directiva que [revoque automáticamente una aplicación o revoque a un usuario específico de una aplicación](app-permission-policy.md).

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Actividades diarias para proteger el entorno de nube](daily-activities-to-protect-your-cloud-environment.md)

[!INCLUDE [Open support ticket](includes/support.md)]
