---
title: Integración de ATP de Windows Defender con Cloud App Security
description: En este artículo se describe cómo integrar Protección contra amenazas avanzada de Windows Defender con Cloud App Security para conseguir visibilidad mejorada de Shadow IT y administración de riesgos.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 12/14/2018
ms.topic: conceptual
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: b35ca44c-da8e-49ec-89d1-c076d123c14f
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 1741b209e1e76da18297e075dff26d97fb3adcd4
ms.sourcegitcommit: 475dc75456f4683336e3e4875e3155677e4fb827
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/16/2018
ms.locfileid: "53450569"
---
# <a name="windows-defender-advanced-threat-protection-integration-with-microsoft-cloud-app-security"></a>Integración de Protección contra amenazas avanzada de Windows Defender con Microsoft Cloud App Security

*Se aplica a: Microsoft Cloud App Security*

Microsoft Cloud App Security se integra con la Protección contra amenazas avanzada de Windows Defender (ATP) de forma nativa. La integración simplifica la implementación de Cloud Discovery, amplía las funcionalidades de Cloud Discovery más allá de la red corporativa y habilita la investigación en el equipo. [Protección contra amenazas avanzada de Windows Defender (ATP)](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/windows-defender-advanced-threat-protection) es una plataforma de seguridad para la protección inteligente, la detección, la investigación y la respuesta. ATP de Windows Defender protege los puntos de conexión de las amenazas cibernéticas, detecta vulneraciones de datos y ataques avanzadas, automatiza los incidentes de seguridad y mejora la postura de seguridad.

Microsoft Cloud App Security usa la información de tráfico que recopila ATP de Windows Defender sobre los servicios y las aplicaciones en la nube a los que se accede desde equipos con Windows 10 administrados por TI. La integración le permite ejecutar Cloud Discovery en cualquier equipo de la red corporativa mediante Wi-Fi pública, mientras está en itinerancia y a través de un acceso remoto. También permite la investigación en el equipo.

Después de identificar un usuario de riesgo, puede comprobar todos los equipos a los que ha accedido el usuario para detectar posibles riesgos. Si identifica un equipo en riesgo, compruebe todos los usuarios que lo han utilizado para detectar posibles riesgos. Los registros de los puntos de conexión que se enrutan a Cloud App Security proporcionan información de usuario para las actividades de tráfico. La actividad de red de ATP de Windows Defender proporciona el contexto del dispositivo. Empareje el contexto del dispositivo con el nombre de usuario para proporcionar una imagen completa de toda la red sobre qué usuario ha realizado qué actividad desde qué equipo.

Microsoft Cloud App Security usa la integración nativa con ATP de Windows Defender para acceder a datos sobre el tráfico del servicio y la aplicación en la nube desde los dispositivos Windows administrados. La integración no requiere ninguna implementación adicional y funciona de inmediato. No tiene que redirigir ni reflejar el tráfico desde los puntos de conexión, ni llevar a cabo pasos de integración complejos.

> [!NOTE]
> ¿Desea experimentar ATP de Windows Defender? [Suscríbase para disfrutar de una prueba gratuita](https://www.microsoft.com/WindowsForBusiness/windows-atp?ocid=docs-wdatp-assignaccess-abovefoldlink)
>


## <a name="prerequisites"></a>Requisitos previos

- Licencia de Microsoft Cloud App Security
- Licencia de ATP de Windows Defender
- Equipos con Windows 10 que ejecutan la versión 1809 o posterior


## <a name="how-it-works"></a>Cómo funciona

Por su cuenta, Cloud App Security recopila registros de los puntos de conexión [usando registros cargados](create-snapshot-cloud-discovery-reports.md) o [configurando la carga automática de registros](discovery-docker.md). La integración nativa le permite aprovechar las ventajas de los registros que crea el agente de ATP de Windows Defender cuando se ejecuta en Windows y supervisa las transacciones de red. Use esta información para la detección de Shadow IT en los equipos Windows de la red.

Para que pueda realizar Cloud Discovery en otras plataformas, es mejor usar tanto el [recopilador de registros](discovery-docker.md) de Cloud App Security junto con la integración de ATP de Windows Defender para supervisar los equipos con Windows 10.

## <a name="how-to-integrate-windows-defender-atp-with-cloud-app-security"></a>Cómo integrar ATP de Windows Defender con Cloud App Security

Para habilitar la integración con Cloud App Security de ATP de Windows Defender:

1. En el portal de ATP de Windows Defender, desde el panel de navegación, seleccione **Configuración de preferencias**.
2. En el menú **Configuración**, en **General**, seleccione **Características avanzadas**.
3. Cambie la opción **Microsoft Cloud App Security** a **Activado**.
4. Haga clic en **Guardar preferencias**.

>[!NOTE]
> Los datos tardan en aparecer en Cloud App Security hasta dos horas después de habilitar la integración.
>

   ![Configuración de ATP de WD](./media/wdatp-settings.png)

## <a name="investigate-machines-in-cloud-app-security"></a>Investigar las máquinas de Cloud App Security

Después de integrar ATP de Windows Defender con Cloud App Security, puede investigar los datos del equipo detectados en el panel de Cloud Discovery.

1. En el portal de Cloud App Security, haga clic en **Cloud Discovery** y luego en el **panel de Cloud Discovery**.
2. En la barra de navegación superior, en **Informes continuos**, seleccione **Usuarios del punto de conexión Win10**.
  ![Informe de ATP de WD](./media/win10-dashboard-report.png)
3. En la parte superior, verá el número de equipos detectadas que se ha agregado después de la integración.
4. Haga clic en la pestaña **Máquinas**.
5. Puede explorar en profundidad cada equipo que se muestra y usar las pestañas para ver los datos de la investigación. Busque correlaciones entre los equipos, los usuarios, las direcciones IP y las aplicaciones que estuvieron implicados en incidentes:
   - **Información general**
      - Transacciones: información sobre el número de transacciones que han tenido lugar en el equipo durante el período de tiempo seleccionado.
      - Tráfico total: información sobre la cantidad total de tráfico (en MB) durante el período de tiempo seleccionado.
     - Cargas: información sobre la cantidad total de tráfico (en MB) que ha cargado el equipo durante el período de tiempo seleccionado.
     - Descargas: información sobre la cantidad total de tráfico (en MB) que ha descargado el equipo durante el período de tiempo seleccionado.
   - **Aplicaciones detectadas**<br>
  Enumera todas las aplicaciones detectadas a las que tuvo acceso la máquina.
   - **Historial de usuarios**<br>
    Enumera todos los usuarios que iniciaron sesión en la máquina.
   - **Historial de direcciones IP**<br>
    Enumera todas las direcciones IP que se asignaron a la máquina.
 ![Información general de las máquinas](./media/machines-overview.png)
 
Al igual que con cualquier otro origen de Cloud Discovery, puede exportar los datos del informe de usuarios del punto de conexión Win10 para fines de investigación. 


## <a name="related-videos"></a>Vídeos relacionados

[Shadow IT discovery beyond the corporate network with Windows Defender ATP and Cloud App Security](https://www.youtube.com/watch?v=f8hbvbY1Hnc) (Shadow IT Discovery más allá de la red corporativa con ATP de Windows Defender y Cloud App Security)  

## <a name="next-steps"></a>Pasos siguientes 
[Controlar las aplicaciones en la nube con directivas](control-cloud-apps-with-policies.md) 

[Los clientes Premier también pueden crear una solicitud de soporte técnico directamente en el portal Premier.](https://premier.microsoft.com/)  
  
