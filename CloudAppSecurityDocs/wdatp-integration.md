---
title: Integración de ATP de Microsoft defender con Cloud App Security
description: En este artículo se describe cómo integrar protección contra amenazas avanzada de Microsoft defender con Cloud App Security para mejorar la visibilidad de la administración de riesgos y de ti.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 7/11/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 90efa85fccd71e488f80db290b09b1636013304b
ms.sourcegitcommit: 7c93b6f93d2699d466b172590710ed01697bbdad
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74720387"
---
# <a name="microsoft-defender-advanced-threat-protection-integration-with-microsoft-cloud-app-security"></a>Integración de protección contra amenazas avanzada de Microsoft defender con Microsoft Cloud App Security

*Se aplica a: Microsoft Cloud App Security*

Microsoft Cloud App Security se integra con protección contra amenazas avanzada (ATP) de Microsoft defender de forma nativa. La integración simplifica la implementación de Cloud Discovery, amplía las funcionalidades de Cloud Discovery más allá de la red corporativa y habilita la investigación en el equipo. [Protección contra amenazas avanzada (ATP) de Microsoft defender](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/windows-defender-advanced-threat-protection) es una plataforma de seguridad para protección, detección, investigación y respuesta inteligentes. Microsoft defender ATP protege los puntos de conexión de las amenazas de Cyber, detecta ataques avanzados e infracciones de datos, automatiza incidentes de seguridad y mejora la posición de seguridad.

Microsoft Cloud App Security usa la información de tráfico recopilada por ATP de Microsoft defender acerca de las aplicaciones y los servicios en la nube a los que se accede desde máquinas de Windows 10 administradas por ti. La integración le permite ejecutar Cloud Discovery en cualquier equipo de la red corporativa mediante Wi-Fi pública, mientras está en itinerancia y a través de un acceso remoto. También permite la investigación en el equipo.

Después de identificar un usuario de riesgo, puede comprobar todos los equipos a los que ha accedido el usuario para detectar posibles riesgos. Si identifica un equipo en riesgo, compruebe todos los usuarios que lo han utilizado para detectar posibles riesgos. Los registros de los puntos de conexión que se enrutan a Cloud App Security proporcionan información de usuario para las actividades de tráfico. La actividad de red de ATP de Microsoft defender proporciona contexto de dispositivo. Empareje el contexto del dispositivo con el nombre de usuario para proporcionar una imagen completa de toda la red sobre qué usuario ha realizado qué actividad desde qué equipo.

Microsoft Cloud App Security usa la integración nativa con Microsoft defender ATP para acceder a los datos sobre el tráfico de aplicaciones y servicios en la nube desde dispositivos Windows administrados. La integración no requiere ninguna implementación adicional y funciona de inmediato. No tiene que redirigir ni reflejar el tráfico desde los puntos de conexión, ni llevar a cabo pasos de integración complejos.

> [!NOTE]
> ¿Quiere experimentar ATP de Microsoft defender? [Suscríbase para disfrutar de una prueba gratuita](https://www.microsoft.com/WindowsForBusiness/windows-atp?ocid=docs-wdatp-assignaccess-abovefoldlink)

## <a name="prerequisites"></a>Requisitos previos

- Licencia de Microsoft Cloud App Security
- Licencia de ATP de Microsoft defender
- Windows 10 versión 1709 (compilación del sistema operativo 16299,1085 con KB4493441), Windows 10 versión 1803 (compilación de SO 17134,704 con KB4493464), Windows 10 versión 1809 (sistema operativo compilación 17763,379 con KB4489899) o versiones posteriores de Windows 10
- Pulse en **características en versión preliminar** para habilitar esta característica en Cloud App Security

## <a name="how-it-works"></a>Cómo funciona

Por su cuenta, Cloud App Security recopila registros de los puntos de conexión [usando registros cargados](create-snapshot-cloud-discovery-reports.md) o [configurando la carga automática de registros](discovery-docker.md). La integración nativa permite aprovechar los registros que crea el agente de ATP de Microsoft defender cuando se ejecuta en Windows y supervisa las transacciones de red. Use esta información para la detección de Shadow IT en los equipos Windows de la red.

Para que pueda realizar Cloud Discovery en otras plataformas, es mejor usar el compilador de [registros](discovery-docker.md)de Cloud App Security, junto con la integración de ATP de Microsoft defender para supervisar sus máquinas con Windows 10.

## <a name="how-to-integrate-microsoft-defender-atp-with-cloud-app-security"></a>Cómo integrar ATP de Microsoft defender con Cloud App Security

Para habilitar la integración con Cloud App Security de ATP de Microsoft defender:

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

1. En el portal de Cloud App Security, haga clic en **Cloud Discovery** y luego en el **panel de Cloud Discovery**.
2. En la barra de navegación superior, en **Informes continuos**, seleccione **Usuarios del punto de conexión Win10**.
  ![Informe de ATP de WD](media/win10-dashboard-report.png)
3. En la parte superior, verá el número de equipos detectadas que se ha agregado después de la integración.
4. Haga clic en la pestaña **Máquinas**.
5. Puede explorar en profundidad cada equipo que se muestra y usar las pestañas para ver los datos de la investigación. Busque correlaciones entre los equipos, los usuarios, las direcciones IP y las aplicaciones que estuvieron implicados en incidentes:

    - **Información general**
        - Transacciones: información sobre el número de transacciones que tuvieron lugar en el equipo durante el período de tiempo seleccionado.
        - Tráfico total: información acerca de la cantidad total de tráfico (en MB) durante el período de tiempo seleccionado.
        - Cargas: información acerca de la cantidad total de tráfico (en MB) que carga el equipo durante el período de tiempo seleccionado.
        - Descargas: información acerca de la cantidad total de tráfico (en MB) que descarga el equipo durante el período de tiempo seleccionado.
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
> - La ATP de defender reenvía datos a Cloud App Security en fragmentos de ~ 4 MB (transacciones de punto de conexión ~ 4000)
> - Si no se alcanza el límite de 4 MB en 1 hora, el NNC de defender notifica todas las transacciones realizadas en la última hora.
> - Si el dispositivo de punto de conexión está detrás de un proxy de reenvío, el volumen de tráfico no será visible para ATP de Microsoft defender y, por tanto, no se incluirá en Cloud Discovery informes. Para obtener más información, vea [supervisar la conexión de red detrás del proxy de reenvío](https://techcommunity.microsoft.com/t5/Microsoft-Defender-ATP/MDATP-Monitoring-network-connection-behind-forward-proxy-Public/ba-p/758274).

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Controlar las aplicaciones en la nube con directivas](control-cloud-apps-with-policies.md)

## <a name="related-videos"></a>Vídeos relacionados

> [!div class="nextstepaction"]
> [Detección de instantáneas de TI más allá de la red corporativa](https://www.youtube.com/watch?v=f8hbvbY1Hnc)

[!INCLUDE [Open support ticket](includes/support.md)]
