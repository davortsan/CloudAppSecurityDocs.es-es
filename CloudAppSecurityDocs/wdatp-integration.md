---
title: Integrar Microsoft Defender ATP con Cloud App Security
description: En este artículo se describe cómo integrar Microsoft Defender Advanced Threat Protection con Cloud App Security para la visibilidad mejorada de Shadow IT y administración de riesgos.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: rkarlin
ms.date: 12/14/2018
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: b35ca44c-da8e-49ec-89d1-c076d123c14f
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: b49ab77b33548d6fd188eadde97294ceb6c62ca5
ms.sourcegitcommit: 235b7d5f1f49075c199b154abc38e51326c0493e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/23/2019
ms.locfileid: "66173516"
---
# <a name="microsoft-defender-advanced-threat-protection-integration-with-microsoft-cloud-app-security"></a>Integración de Microsoft Defender Advanced Threat Analytics con Microsoft Cloud App Security

*Se aplica a: Microsoft Cloud App Security*

Microsoft Cloud App Security se integra con Defender Advanced Threat Protection (ATP) de Microsoft de forma nativa. La integración simplifica la implementación de Cloud Discovery, amplía las funcionalidades de Cloud Discovery más allá de la red corporativa y habilita la investigación en el equipo. [Protección de amenazas avanzada de Microsoft Defender (ATP)](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/windows-defender-advanced-threat-protection) es una plataforma de seguridad para la protección inteligente, detección, investigación y respuesta. Microsoft Defender ATP protege los puntos de conexión de las amenazas cibernéticas, detecta infracciones de datos y los ataques avanzadas, automatiza los incidentes de seguridad y mejora la postura de seguridad.

Microsoft Cloud App Security usa la información de tráfico recopilada por Microsoft Defender ATP acerca de las aplicaciones en la nube y los servicios que se obtiene acceso desde equipos Windows 10 administrados por TI. La integración le permite ejecutar Cloud Discovery en cualquier equipo de la red corporativa mediante Wi-Fi pública, mientras está en itinerancia y a través de un acceso remoto. También permite la investigación en el equipo.

Después de identificar un usuario de riesgo, puede comprobar todos los equipos a los que ha accedido el usuario para detectar posibles riesgos. Si identifica un equipo en riesgo, compruebe todos los usuarios que lo han utilizado para detectar posibles riesgos. Los registros de los puntos de conexión que se enrutan a Cloud App Security proporcionan información de usuario para las actividades de tráfico. Actividad de red de Microsoft Defender ATP proporciona el contexto de dispositivo. Empareje el contexto del dispositivo con el nombre de usuario para proporcionar una imagen completa de toda la red sobre qué usuario ha realizado qué actividad desde qué equipo.

Microsoft Cloud App Security usa la integración nativa con Microsoft Defender ATP para aprovechar datos sobre el tráfico de aplicación y servicio en la nube desde dispositivos Windows administrados. La integración no requiere ninguna implementación adicional y funciona de inmediato. No tiene que redirigir ni reflejar el tráfico desde los puntos de conexión, ni llevar a cabo pasos de integración complejos.

> [!NOTE]
> ¿Desea experimentar Microsoft Defender ATP? [Suscríbase para disfrutar de una prueba gratuita](https://www.microsoft.com/WindowsForBusiness/windows-atp?ocid=docs-wdatp-assignaccess-abovefoldlink)
>


## <a name="prerequisites"></a>Requisitos previos

- Licencia de Microsoft Cloud App Security
- Licencia de Microsoft Defender ATP
- Equipos con Windows 10 que ejecutan la versión 1809 o posterior
- Pulse en **características en versión preliminar** para habilitar esta característica en Cloud App Security

## <a name="how-it-works"></a>Cómo funciona

Por su cuenta, Cloud App Security recopila registros de los puntos de conexión [usando registros cargados](create-snapshot-cloud-discovery-reports.md) o [configurando la carga automática de registros](discovery-docker.md). Integración nativa le permite aprovechar las ventajas de los registros del agente de Microsoft Defender ATP crea cuando se ejecuta en Windows y supervisa las transacciones de red. Use esta información para la detección de Shadow IT en los equipos Windows de la red.

Para que pueda realizar la detección de la nube en otras plataformas, es mejor usar tanto la seguridad de la aplicación en la nube [recopilador de registros](discovery-docker.md), junto con la integración de Microsoft Defender ATP para supervisar las máquinas de Windows 10.

## <a name="how-to-integrate-microsoft-defender-atp-with-cloud-app-security"></a>Cómo integrar Microsoft Defender ATP con Cloud App Security

Para habilitar la integración con Cloud App Security desde Microsoft Defender ATP:

1. En el portal de Microsoft Defender ATP, desde el panel de navegación, seleccione **el programa de instalación de preferencias**.
2. En el menú **Configuración**, en **General**, seleccione **Características avanzadas**.
3. Cambie la opción **Microsoft Cloud App Security** a **Activado**.
4. Haga clic en **Guardar preferencias**.

>[!NOTE]
> Los datos tardan en aparecer en Cloud App Security hasta dos horas después de habilitar la integración.
>

   ![Configuración de ATP de WD](./media/wdatp-settings.png)

## <a name="investigate-machines-in-cloud-app-security"></a>Investigar las máquinas de Cloud App Security

Después de integrar Microsoft Defender ATP con Cloud App Security, puede investigar los datos de la máquina detectada en el panel de Cloud Discovery.

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

> [!NOTE]
> - Defender ATP reenvía los datos con Cloud App Security en fragmentos de ~ 4 MB (transacciones de punto de conexión de unas 4000)
> - Si no se alcanza el límite de 4 MB en 1 hora, los informes de ATP de Defender todas las transacciones realizan durante la última hora.

## <a name="related-videos"></a>Vídeos relacionados

[Shadow IT discovery más allá de la red corporativa con Microsoft Defender ATP y Cloud App Security](https://www.youtube.com/watch?v=f8hbvbY1Hnc)  

## <a name="next-steps"></a>Pasos siguientes 
[Controlar las aplicaciones en la nube con directivas](control-cloud-apps-with-policies.md) 

[Los clientes Premier también pueden crear una solicitud de soporte técnico directamente en el portal Premier.](https://premier.microsoft.com/)  
  
