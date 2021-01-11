---
title: Implementación de Cloud App Security
description: En este inicio rápido se describe el proceso de empezar a trabajar con Cloud App Security para tener el control de las aplicaciones en la nube, información sobre ellas y usarlas.
ms.date: 06/07/2020
ms.topic: quickstart
ms.openlocfilehash: f17608329facabe6f48ae20938c44f3e8ef1b05a
ms.sourcegitcommit: 16a65ab2c8ca778d0b3cfa97b847af4c812363b2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/03/2021
ms.locfileid: "97855547"
---
# <a name="quickstart-get-started-with-microsoft-cloud-app-security"></a>Inicio rápido: Introducción a Microsoft Cloud App Security

[!INCLUDE [Banner for top of topics](includes/banner.md)]

En este inicio rápido se proporcionan los pasos necesarios para empezar a trabajar con Cloud App Security. Microsoft Cloud App Security puede ayudarle a aprovechar las ventajas de las aplicaciones en la nube a la vez que mantiene el control de los recursos corporativos. Lo que hace es mejorar la visibilidad de la actividad en la nube y ayuda a aumentar la protección de los datos corporativos. En este artículo, le guiaremos por los pasos que debe seguir para configurar y trabajar con Microsoft Cloud App Security.

Su organización debe tener una licencia para usar Cloud App Security. Para obtener más información sobre precios, vea la [Hoja de datos de licencias de Cloud App Security](https://aka.ms/mcaslicensing).

>[!NOTE]
>Cloud App Security no requiere ninguna licencia de Office 365.

## <a name="prerequisites"></a>Requisitos previos

- Su organización debe tener una licencia para usar Cloud App Security. Para obtener más información sobre precios, vea la [Hoja de datos de licencias de Cloud App Security](https://aka.ms/mcaslicensing).

    Para obtener soporte técnico sobre la activación de los inquilinos, vea [Formas de contactar al soporte técnico para productos empresariales: ayuda para administradores](https://support.office.com/article/Contact-Office-365-for-business-support-Admin-Help-32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b).
- Una vez que tenga una licencia para Cloud App Security, recibirá un correo electrónico con la información de activación y un vínculo al portal de Cloud App Security.

- Para configurar Cloud App Security, debe ser administrador global o administrador de seguridad de Azure Active Directory u Office 365. Es importante comprender que un usuario que tenga asignado un rol de administrador tendrá los mismos permisos en todas las aplicaciones en la nube a las que se haya suscrito la organización. Esto es así independientemente de si se asigna el rol en el centro de administración de Microsoft 365, en el portal de Azure clásico o mediante el módulo de Azure AD para [Windows PowerShell](/microsoft-365/enterprise/assign-roles-to-user-accounts-with-microsoft-365-powershell?view=o365-worldwide&preserve-view=true). Para obtener más información, vea [Asignación de roles de administrador](https://support.office.com/article/Assigning-admin-roles-in-Office-365-eac4d046-1afd-4f1a-85fc-8219c79e1504) y [Asignación de roles de administrador en Azure Active Directory](/azure/active-directory/users-groups-roles/directory-assign-admin-roles).

- Para ejecutar el portal de Cloud App Security, use Internet Explorer 11, Microsoft Edge (versión más reciente), Google Chrome (versión más reciente), Mozilla Firefox (versión más reciente) o Apple Safari (versión más reciente).

## <a name="to-access-the-portal"></a>Acceso al portal

Para acceder al portal de Cloud App Security, vaya a [https://portal.cloudappsecurity.com](https://portal.cloudappsecurity.com). También puede acceder al portal a través del **[Centro de administración de Microsoft 365](https://security.microsoft.com)** , como se indica a continuación:

1. En el Centro de administración de Microsoft 365, en el menú lateral, haga clic en **Mostrar todo** y seleccione **Seguridad**.

    ![Acceso desde el Centro de administración de Microsoft 365](media/access-from-o365.png)

1. En la página de seguridad de Microsoft 365, haga clic en **Más recursos** y, luego, seleccione **Cloud App Security**.

    ![Seleccionar Cloud App Security](media/access-from-o365-s2.png)

## <a name="step-1-set-instant-visibility-protection-and-governance-actions-for-your-apps"></a>Paso 1. [Establecimiento de las acciones instantáneas de gobernanza, protección y visibilidad para las aplicaciones](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md)

Tarea necesaria: Conectar aplicaciones

1. En el engranaje de configuración, seleccione **Conectores de aplicaciones**.
1. Haga clic en el signo más ( **+** ) para agregar una aplicación y seleccione una aplicación.
1. Siga los pasos de configuración para conectar la aplicación.

**¿Por qué conectar una aplicación?**
Después de conectar una aplicación, puede obtener una mayor visibilidad para poder investigar las actividades, los archivos y las cuentas de las aplicaciones en su entorno de nube.

## <a name="step-2-control-cloud-apps-with-policies"></a>Paso 2. [Controlar las aplicaciones en la nube con directivas](control-cloud-apps-with-policies.md)

Tarea necesaria: Crear directivas

### <a name="to-create-policies"></a>Creación de directivas

1. Vaya a **Control** > **Plantillas**.
1. Seleccione una plantilla de directiva de la lista y haga clic en **Crear directiva**.
1. Personalice la directiva (seleccione filtros, acciones y otras opciones) y, luego, elija **Crear**.
1. En la pestaña **Directivas**, elija la directiva para ver las coincidencias pertinentes (actividades, archivos y alertas).
 Sugerencia: Para abarcar todos los escenarios de seguridad del entorno de nube, cree una directiva para cada **categoría de riesgo**.

### <a name="how-can-policies-help-your-organization"></a>¿Cómo pueden las directivas ayudar a su organización?

Puede usar directivas para ayudarle a supervisar tendencias, ver amenazas de seguridad y generar alertas e informes personalizados. Con las directivas, puede crear acciones de gobernanza y establecer controles de uso compartido de archivos y prevención de pérdida de datos.

## <a name="step-3-set-up-cloud-discovery"></a>Paso 3. [Configurar Cloud Discovery](set-up-cloud-discovery.md)

Tarea necesaria: Habilitar Cloud App Security para ver el uso de las aplicaciones en la nube

1. [Integración con Microsoft Defender ATP](mde-integration.md) para habilitar automáticamente Cloud App Security y supervisar los dispositivos Windows 10 dentro y fuera de la empresa.
1. Si usa [Zscaler, intégrelo](zscaler-integration.md) con Cloud App Security.
1. Para conseguir una cobertura completa, cree un informe de Cloud Discovery continuo.

    1. En el engranaje de configuración, seleccione **Cloud Discovery settings** (Configuración de Cloud Discovery).
    1. Elija **Carga automática de registros**.
    1. En la pestaña **Orígenes de datos**, agregue los orígenes.
    1. En la pestaña **Recopiladores de registros**, configure el recopilador de registros.

### <a name="to-create-a-snapshot-cloud-discovery-report"></a>Para crear un informe de instantáneas de Cloud Discovery

 Vaya a **Detectar** > **Informe de instantáneas** y siga los pasos que se muestran.

### <a name="why-should-you-configure-cloud-discovery-reports"></a>¿Por qué es importante configurar los informes de Cloud Discovery?

Es muy importante tener visibilidad sobre Shadow IT en la organización.
Después de analizar los registros, puede encontrar fácilmente qué aplicaciones en la nube se usan, por qué personas y en qué dispositivos.

## <a name="step-4-personalize-your-experience"></a>Paso 4. [Personalización de la experiencia](mail-settings.md)

Tarea recomendada: Agregar los datos de la organización

### <a name="to-enter-email-settings"></a>Para especificar la configuración del correo electrónico

1. En el engranaje de configuración, seleccione **Configuración de correo**.
1. En **Identidad del emisor de correo electrónico**, escriba las direcciones de correo electrónico y el nombre para mostrar.
1. En **Diseño del correo electrónico**, cargue la plantilla de correo electrónico de su organización.

### <a name="to-set-admin-notifications"></a>Para establecer notificaciones de administrador

1. En la barra de navegación, elija su nombre de usuario y, luego, vaya a **Configuración de usuario**.
1. En **Notificaciones**, configure los métodos que quiere establecer para las notificaciones del sistema.
1. Elija **Guardar**.

### <a name="to-customize-the-score-metrics"></a>Para personalizar las métricas de puntuación

1. En el engranaje de configuración, seleccione **Cloud Discovery settings** (Configuración de Cloud Discovery).
1. En el engranaje de configuración, seleccione **Cloud Discovery settings** (Configuración de Cloud Discovery).
1. En **Métricas de puntuación**, configure la importancia de los distintos valores de riesgo.
1. Elija **Guardar**.

Ahora, las puntuaciones de riesgo asignadas a las aplicaciones detectadas se configuran de forma precisa según las necesidades y las prioridades de la organización.

### <a name="why-personalize-your-environment"></a>¿Por qué personalizar el entorno?

Algunas características funcionan mejor si se personalizan según sus necesidades.
Ofrezca una mejor experiencia a los usuarios con sus propias plantillas de correo electrónico. Decida qué notificaciones recibe y personalice la métrica de puntuación de riesgo para ajustarse a las preferencias de la organización.

## <a name="step-5-organize-the-data-according-to-your-needs"></a>Paso 5. [Organización de los datos según las necesidades](ip-tags.md)

Tarea recomendada: Configurar los valores importantes

### <a name="to-create-ip-address-tags"></a>Para crear etiquetas de direcciones IP

1. En el engranaje de configuración, seleccione **Cloud Discovery settings** (Configuración de Cloud Discovery).
1. En el engranaje de configuración, seleccione **Intervalos de direcciones IP**.
1. Haga clic en el signo más ( **+** ) para agregar un intervalo de direcciones IP.
1. Escriba los **detalles**, la **ubicación**, las **etiquetas** y la **categoría** del intervalo IP.
1. Elija **Crear**.

    Ahora puede usar etiquetas IP al crear directivas y al filtrar y crear informes continuos.

### <a name="to-create-continuous-reports"></a>Para crear informes continuos

1. En el engranaje de configuración, seleccione **Cloud Discovery settings** (Configuración de Cloud Discovery).
1. En **Informes continuos**, elija **Crear informe**.
1. Siga los pasos de configuración.
1. Elija **Crear**.

Ahora puede ver los datos detectados según sus propias preferencias, como las unidades de negocio o los intervalos IP.

### <a name="to-add-domains"></a>Para agregar dominios

1. En el engranaje de configuración, seleccione **Configuración**.
1. En **Detalles de la organización**, agregue los dominios internos de la organización.
1. Elija **Guardar**.

### <a name="why-should-you-configure-these-settings"></a>¿Por qué es importante configurar estos parámetros?

Estas opciones de configuración le proporcionan un mayor control de las características de la consola. Con etiquetas IP, es más fácil crear directivas que se adapten a sus necesidades, filtrar datos de forma precisa y mucho más. Use vistas de datos para agrupar los datos en categorías lógicas.

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Control de aplicaciones en la nube con directivas](control-cloud-apps-with-policies.md).

[!INCLUDE [Open support ticket](includes/support.md)].
