---
title: Integración de ATP de Microsoft defender con Cloud App Security
description: En este artículo se describe cómo integrar protección contra amenazas avanzada de Microsoft defender con Cloud App Security para mejorar la visibilidad de la administración de riesgos y de ti.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 09/02/2020
ms.topic: how-to
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 55c3a9f1edfadcaa686a54a3b69f95e319a55320
ms.sourcegitcommit: 740357159d8bc405412ca3c36757647b5f1c7623
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "89316978"
---
# <a name="microsoft-defender-advanced-threat-protection-integration-with-microsoft-cloud-app-security"></a>Integración de protección contra amenazas avanzada de Microsoft defender con Microsoft Cloud App Security

*Se aplica a: Microsoft Cloud App Security*

Microsoft Cloud App Security se integra con protección contra amenazas avanzada (ATP) de Microsoft defender de forma nativa. La integración simplifica la implementación de Cloud Discovery, amplía las funcionalidades de Cloud Discovery más allá de la red corporativa y habilita la investigación en el equipo. [ATP de Microsoft defender](/windows/security/threat-protection/windows-defender-atp/windows-defender-advanced-threat-protection) es una plataforma de seguridad para la protección, la detección, la investigación y la respuesta inteligentes. Microsoft defender ATP protege los puntos de conexión de las amenazas de Cyber, detecta ataques avanzados e infracciones de datos, automatiza incidentes de seguridad y mejora la posición de seguridad.

Cloud App Security usa la información de tráfico recopilada por ATP de Microsoft defender acerca de las aplicaciones y los servicios en la nube a los que se accede desde máquinas de Windows 10 administradas por ti. La integración nativa permite ejecutar Cloud Discovery en cualquier equipo de la red corporativa, mediante Wi-Fi pública, en itinerancia y a través de acceso remoto. También permite la investigación en el equipo.

La integración no requiere ninguna implementación adicional y funciona de inmediato. No tiene que redirigir ni reflejar el tráfico desde los puntos de conexión, ni llevar a cabo pasos de integración complejos. Los registros de los extremos enviados a Cloud App Security proporcionan información de usuario para las actividades de tráfico. La actividad de red de ATP de Microsoft defender proporciona contexto de dispositivo. Emparejar el contexto de dispositivo con el nombre de usuario proporciona una imagen completa a través de la red, lo que le permite determinar qué usuario ejecutó la actividad de la máquina.

Además, al identificar a un usuario de riesgo, puede comprobar todas las máquinas a las que el usuario ha tenido acceso para detectar posibles riesgos. Si identifica una máquina arriesgada, compruebe todos los usuarios que la usaban para detectar posibles riesgos potenciales.

Una vez recopilada la información de tráfico, está listo para [profundizar](discovered-apps.md#deep-dive-into-discovered-apps) en el uso de aplicaciones en la nube en su organización. Cloud App Security aprovecha las funcionalidades de protección de red de ATP de Microsoft defender para bloquear el acceso de los dispositivos de punto de conexión a las aplicaciones en la nube. Puede bloquear las aplicaciones si las [etiqueta como no **autorizadas** ](governance-discovery.md#BKMK_SanctionApp) en el portal. En función de la evaluación de riesgos y uso integral de cada aplicación no autorizada, los dominios de la aplicación se usan para crear [indicadores de dominio](/windows/security/threat-protection/microsoft-defender-atp/manage-indicators#create-indicators-for-ips-and-urlsdomains-preview) en el portal de ATP de Microsoft defender. Antivirus de Microsoft defender, que se ejecuta en dispositivos de punto de conexión, usa los indicadores de dominio para bloquear el acceso a estas aplicaciones.

> [!NOTE]
> ¿Quiere experimentar ATP de Microsoft defender? [Regístrese para obtener una evaluación gratuita](https://www.microsoft.com/WindowsForBusiness/windows-atp?ocid=docs-wdatp-assignaccess-abovefoldlink).

## <a name="prerequisites"></a>Requisitos previos

- Licencia de Microsoft Cloud App Security
- Licencia de ATP de Microsoft defender
- Windows 10 versión 1709 (compilación del sistema operativo 16299,1085 con KB4493441), Windows 10 versión 1803 (compilación de SO 17134,704 con KB4493464), Windows 10 versión 1809 (sistema operativo compilación 17763,379 con KB4489899) o versiones posteriores de Windows 10
- Antivirus de Microsoft Defender
  - [protección en tiempo real habilitada](/windows/security/threat-protection/windows-defender-antivirus/configure-real-time-protection-windows-defender-antivirus)
  - [protección entregada en la nube habilitada](/windows/security/threat-protection/windows-defender-antivirus/enable-cloud-protection-windows-defender-antivirus)
  - [Protección de red habilitada y configurada para el modo de bloqueo](/windows/security/threat-protection/microsoft-defender-atp/enable-network-protection)

## <a name="how-it-works"></a>Funcionamiento

Por su cuenta, Cloud App Security recopila registros de los puntos de conexión [usando registros cargados](create-snapshot-cloud-discovery-reports.md) o [configurando la carga automática de registros](discovery-docker.md). La integración nativa permite aprovechar los registros que crea el agente de ATP de Microsoft defender cuando se ejecuta en Windows y supervisa las transacciones de red. Use esta información para la detección de Shadow IT en los equipos Windows de la red.

Para que pueda realizar Cloud Discovery en otras plataformas, es mejor usar el compilador de [registros](discovery-docker.md)de Cloud App Security, junto con la integración de ATP de Microsoft defender para supervisar sus máquinas con Windows 10.

[Vea nuestros vídeos](#related-videos) en los que se muestran las ventajas de usar ATP de Microsoft Defender con Cloud App Security.

## <a name="how-to-integrate-microsoft-defender-atp-with-cloud-app-security"></a>Cómo integrar ATP de Microsoft defender con Cloud App Security

Para habilitar la integración de Microsoft defender ATP con Cloud App Security:

1. En el portal de ATP de Microsoft defender, en el panel de navegación, seleccione **preferencias configuración**.
2. En el menú **Configuración**, en **General**, seleccione **Características avanzadas**.
3. Cambie la opción **Microsoft Cloud App Security** a **Activado**.
4. Haga clic en **Guardar preferencias**.

>[!NOTE]
> Los datos tardan en aparecer en Cloud App Security hasta dos horas después de habilitar la integración.
>

![Configuración de ATP de WD](media/wdatp-settings.png)

## <a name="investigate-machines-in-cloud-app-security"></a>Investigar las máquinas de Cloud App Security

Después de integrar ATP de Microsoft defender con Cloud App Security, puede investigar los datos de la máquina detectada en el panel de Cloud Discovery.

1. En Cloud App Security, haga clic en **Cloud Discovery** y **Cloud Discovery panel**.
2. En la barra de navegación superior, en **Informes continuos**, seleccione **Usuarios del punto de conexión Win10**.
  ![Informe de ATP de WD](media/win10-dashboard-report.png)
3. En la parte superior, verá el número de equipos detectadas que se ha agregado después de la integración.
4. Haga clic en la pestaña **Máquinas**.
5. Puede explorar en profundidad cada equipo que se muestra y usar las pestañas para ver los datos de la investigación. Busque correlaciones entre los equipos, los usuarios, las direcciones IP y las aplicaciones que estuvieron implicados en incidentes:

    - **Información general**
        - **Nivel de riesgo del equipo**: muestra el riesgo de que el perfil del equipo sea relativo a otras máquinas de la organización, tal y como indica la gravedad (alta, media, baja e informativa). Cloud App Security usa perfiles de equipo de ATP de Microsoft defender para cada equipo basado en análisis avanzado. La actividad que es anómala en la línea de base de un equipo se evalúa y determina el nivel de riesgo de la máquina. Use el nivel de riesgo del equipo para determinar qué máquinas se deben investigar en primer lugar.
        - **Transacciones**: información sobre el número de transacciones que tuvieron lugar en el equipo durante el período de tiempo seleccionado.
        - **Tráfico total**: información acerca de la cantidad total de tráfico (en MB) durante el período de tiempo seleccionado.
        - Cargas: información acerca de la cantidad total de tráfico (en MB) que carga el equipo durante el período de tiempo seleccionado.
        - **Descargas**: información acerca de la cantidad total de tráfico (en MB) que descarga el equipo durante el período de tiempo seleccionado.
    - **Aplicaciones detectadas**  
    Enumera todas las aplicaciones detectadas a las que tuvo acceso la máquina.
    - **Historial de usuarios**  
    Enumera todos los usuarios que iniciaron sesión en la máquina.
    - **Historial de direcciones IP**  
    Enumera todas las direcciones IP que se asignaron a la máquina.
 ![Información general de las máquinas](media/machines-overview.png)

Al igual que con cualquier otro origen de Cloud Discovery, puede exportar los datos del informe de usuarios del punto de conexión Win10 para fines de investigación.

> [!NOTE]
>
> - ATP de Microsoft defender reenvía datos a Cloud App Security en fragmentos de ~ 4 MB (transacciones de punto de conexión ~ 4000)
> - Si no se alcanza el límite de 4 MB en 1 hora, ATP de Microsoft defender notifica todas las transacciones realizadas durante la última hora.
> - Si el dispositivo de punto de conexión está detrás de un proxy de reenvío, los datos de tráfico no estarán visibles para ATP de Microsoft defender y, por tanto, no se incluirán en Cloud Discovery informes. Para obtener más información, vea [supervisar la conexión de red detrás del proxy de reenvío](https://techcommunity.microsoft.com/t5/Microsoft-Defender-ATP/MDATP-Monitoring-network-connection-behind-forward-proxy-Public/ba-p/758274).

## <a name="investigate-device-network-events-in-microsoft-defender-atp"></a>Investigación de eventos de red de dispositivo en ATP de Microsoft defender

Siga estos pasos para obtener una visibilidad más granular de la actividad de red del dispositivo en ATP de Microsoft defender:

1. En Cloud App Security, en **detección** y, a continuación, seleccione **equipos**.
1. Seleccione el equipo que desea investigar y, a continuación, en la parte superior derecha, haga clic **en la vista de ATP de Microsoft defender**.
1. En Microsoft defender Security Center, en **dispositivos** > {dispositivo seleccionado}, seleccione **escala de tiempo**.
1. En **filtros**, seleccione **eventos de red**.
1. Investigue los eventos de red del dispositivo según sea necesario.

![Captura de pantalla que muestra la escala de tiempo del dispositivo en Microsoft defender Security Center](media/mdatp-selected-device.png)

## <a name="investigate-app-usage-in-microsoft-defender-atp-with-advanced-hunting"></a>Investigar el uso de aplicaciones en ATP de Microsoft defender con la búsqueda avanzada

Siga estos pasos para obtener una visibilidad más granular sobre los eventos de red relacionados con la aplicación en ATP de Microsoft defender:

1. En Cloud App Security, en **detección** y, a continuación, seleccione **detectado**.
1. Haga clic en la aplicación que desea investigar para abrir su cajón.
1. Haga clic en la lista de **dominios** de la aplicación y copie la lista de dominios.
1. En Microsoft defender Security Center, en **dispositivos**, seleccione **búsqueda avanzada**.
1. Pegue la siguiente consulta y sustitúyala `<DOMAIN_LIST>` por la lista de dominios que copió anteriormente.

    ```kusto
    DeviceNetworkEvents
    | where RemoteUrl in ("<DOMAIN_LIST>")
    | order by Timestamp desc
    ```

1. Ejecute la consulta e investigue los eventos de red para esta aplicación.

![Captura de pantalla que muestra la búsqueda avanzada de Microsoft defender Security Center](media/mdatp-advanced-hunting.png)

## <a name="block-access-to-unsanctioned-cloud-apps"></a>Bloquear el acceso a aplicaciones no autorizadas en la nube

Cloud App Security usa la etiqueta de aplicación integrada no [**autorizada**](governance-discovery.md#BKMK_SanctionApp) para marcar las aplicaciones en la nube como prohibidas para su uso, disponibles tanto en las páginas del catálogo de aplicaciones de Cloud Discovery como en la nube. Al habilitar la integración con ATP de Microsoft defender, puede bloquear sin problemas el acceso a aplicaciones no autorizadas con un solo clic en el portal de Cloud App Security.

### <a name="how-blocking-works"></a>Cómo funciona el bloqueo

Las aplicaciones marcadas como no **autorizadas** en Cloud App Security se sincronizan automáticamente con ATP de Microsoft defender, normalmente en pocos minutos. Más concretamente, los dominios usados por estas aplicaciones no autorizadas se propagan a los dispositivos de punto de conexión para que los bloqueen antivirus de Microsoft defender en el acuerdo de nivel de servicio de protección de red.

### <a name="how-to-enable-cloud-app-blocking-with-microsoft-defender-atp"></a>Habilitación del bloqueo de aplicaciones en la nube con ATP de Microsoft defender

Siga estos pasos para habilitar el control de acceso para aplicaciones en la nube:

1. En Cloud App Security, en el engranaje de configuración, seleccione **configuración**, en **Cloud Discovery** seleccione **ATP de Microsoft defender**y, a continuación, seleccione **bloquear aplicaciones no autorizadas**.

    ![Captura de pantalla que muestra cómo habilitar el bloqueo con ATP de Microsoft defender](media/defender-atp-integration.png)

1. En Microsoft defender Security Center, vaya a **configuración**  >  **características avanzadas**y, a continuación, seleccione **indicadores de red personalizados**. Para obtener información acerca de los indicadores de red, consulte [crear indicadores para direcciones IP y direcciones URL y dominios](/windows/security/threat-protection/microsoft-defender-atp/manage-indicators#create-indicators-for-ips-and-urlsdomains-preview).

    Esto le permite aprovechar las capacidades de protección de la red antivirus de Microsoft defender para bloquear el acceso a un conjunto predefinido de direcciones URL mediante Cloud App Security, ya sea asignando manualmente [etiquetas de aplicación](governance-discovery.md#BKMK_SanctionApp) a aplicaciones específicas o usando automáticamente una directiva de [detección de aplicaciones](cloud-discovery-policies.md#creating-an-app-discovery-policy).

    ![Captura de pantalla que muestra cómo habilitar los indicadores de red personalizados en ATP de Microsoft defender](media/defender-atp-custom-network-indicators.png)

## <a name="investigate-unsanctioned-apps-in-microsoft-defender-security-center"></a>Investigue las aplicaciones no autorizadas en Microsoft defender Security Center

Cada intento de acceder a una aplicación no autorizada desencadena una alerta en Microsoft defender Security Center con detalles detallados acerca de toda la sesión. Esto le permite realizar investigaciones más profundas en los intentos de acceso a aplicaciones no autorizadas, así como proporcionar información adicional relevante para su uso en la investigación de dispositivos de punto de conexión.

A veces, no se bloquea el acceso a una aplicación no autorizada, ya sea porque el dispositivo de punto de conexión no está configurado correctamente o si la Directiva de cumplimiento no se ha propagado todavía al punto de conexión. En esta instancia, los administradores de ATP de Microsoft defender recibirán una alerta en Microsoft defender Security Center que la aplicación no autorizada no se bloqueó.

![Captura de pantalla que muestra la alerta de aplicación no autorizada de ATP de Microsoft defender](media/defender-atp-unsanctioned-app-alert.png)

> [!NOTE]
>
> - Se tarda hasta dos horas después de etiquetar una aplicación como no **autorizada** para que los dominios de aplicación se propaguen a los dispositivos de punto de conexión.
> - De forma predeterminada, las aplicaciones y los dominios marcados como no **autorizados** en Cloud App Security se bloquearán para todos los dispositivos de punto de conexión de la organización.
> - Actualmente, no se admiten direcciones URL completas para aplicaciones no autorizadas. Por lo tanto, cuando no se autorizan las aplicaciones configuradas con direcciones URL completas, no se propagan a ATP de Microsoft defender y no se bloquearán. Por ejemplo, `google.com/drive` no se admite, mientras que `drive.google.com` es compatible.
> - Las notificaciones en el explorador pueden variar entre distintos exploradores.

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Controlar las aplicaciones en la nube con directivas](control-cloud-apps-with-policies.md)

## <a name="related-videos"></a>Vídeos relacionados

> [!div class="nextstepaction"]
> [Detección y bloqueo de la sombra mediante ATP de Microsoft defender](https://www.youtube.com/watch?v=MsHkTOoqSQo)

> [!div class="nextstepaction"]
> [Detección de shadow IT más allá de la red corporativa](https://www.youtube.com/watch?v=f8hbvbY1Hnc)

[!INCLUDE [Open support ticket](includes/support.md)]
