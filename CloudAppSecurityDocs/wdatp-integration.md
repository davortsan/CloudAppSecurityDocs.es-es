---
title: Integrate Microsoft Defender ATP with Cloud App Security
description: This article describes how to integrate Microsoft Defender Advanced Threat Protection with Cloud App Security for enhanced visibility into Shadow IT and risk management.
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
ms.assetid: b35ca44c-da8e-49ec-89d1-c076d123c14f
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: aeddfb56542309b0ee6b1f0d4cdec85bb36a120e
ms.sourcegitcommit: 094bb42a198fe733cfd3aec79d74487672846dfa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/24/2019
ms.locfileid: "74459431"
---
# <a name="microsoft-defender-advanced-threat-protection-integration-with-microsoft-cloud-app-security"></a>Microsoft Defender Advanced Threat Protection integration with Microsoft Cloud App Security

*Se aplica a: Microsoft Cloud App Security*

Microsoft Cloud App Security integrates with Microsoft Defender Advanced Threat Protection (ATP) natively. La integración simplifica la implementación de Cloud Discovery, amplía las funcionalidades de Cloud Discovery más allá de la red corporativa y habilita la investigación en el equipo. [Microsoft Defender Advanced Threat Protection (ATP)](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/windows-defender-advanced-threat-protection) is a security platform for intelligent protection, detection, investigation, and response. Microsoft Defender ATP protects endpoints from cyber threats, detects advanced attacks and data breaches, automates security incidents, and improves security posture.

Microsoft Cloud App Security uses the traffic information collected by Microsoft Defender ATP about the cloud apps and services being accessed from IT-managed Windows 10 machines. La integración le permite ejecutar Cloud Discovery en cualquier equipo de la red corporativa mediante Wi-Fi pública, mientras está en itinerancia y a través de un acceso remoto. También permite la investigación en el equipo.

Después de identificar un usuario de riesgo, puede comprobar todos los equipos a los que ha accedido el usuario para detectar posibles riesgos. Si identifica un equipo en riesgo, compruebe todos los usuarios que lo han utilizado para detectar posibles riesgos. Los registros de los puntos de conexión que se enrutan a Cloud App Security proporcionan información de usuario para las actividades de tráfico. Microsoft Defender ATP network activity provides device context. Empareje el contexto del dispositivo con el nombre de usuario para proporcionar una imagen completa de toda la red sobre qué usuario ha realizado qué actividad desde qué equipo.

Microsoft Cloud App Security uses the native integration with Microsoft Defender ATP to tap into data about cloud app and service traffic from managed Windows devices. La integración no requiere ninguna implementación adicional y funciona de inmediato. No tiene que redirigir ni reflejar el tráfico desde los puntos de conexión, ni llevar a cabo pasos de integración complejos.

> [!NOTE]
> Want to experience Microsoft Defender ATP? [Suscríbase para disfrutar de una prueba gratuita](https://www.microsoft.com/WindowsForBusiness/windows-atp?ocid=docs-wdatp-assignaccess-abovefoldlink)
>


## <a name="prerequisites"></a>Requisitos previos

- Licencia de Microsoft Cloud App Security
- Microsoft Defender ATP license
- Windows 10 version 1709 (OS Build 16299.1085 with KB4493441), Windows 10 version 1803 (OS Build 17134.704 with KB4493464), Windows 10 version 1809 (OS Build 17763.379 with KB4489899) or later Windows 10 versions
- Pulse en **características en versión preliminar** para habilitar esta característica en Cloud App Security

## <a name="how-it-works"></a>Cómo funciona

Por su cuenta, Cloud App Security recopila registros de los puntos de conexión [usando registros cargados](create-snapshot-cloud-discovery-reports.md) o [configurando la carga automática de registros](discovery-docker.md). Native integration enables you to take advantage of the logs Microsoft Defender ATP's agent creates when it runs on Windows and monitors network transactions. Use esta información para la detección de Shadow IT en los equipos Windows de la red.

To enable you to perform Cloud Discovery across other platforms, it's best to use both the Cloud App Security [log collector](discovery-docker.md), along with Microsoft Defender ATP integration to monitor your Windows 10 machines.

## <a name="how-to-integrate-microsoft-defender-atp-with-cloud-app-security"></a>How to integrate Microsoft Defender ATP with Cloud App Security

To enable integration with Cloud App Security from Microsoft Defender ATP:

1. In the Microsoft Defender ATP portal, from the navigation pane, select **Preferences setup**.
2. En el menú **Configuración**, en **General**, seleccione **Características avanzadas**.
3. Cambie la opción **Microsoft Cloud App Security** a **Activado**.
4. Haga clic en **Guardar preferencias**.

>[!NOTE]
> Los datos tardan en aparecer en Cloud App Security hasta dos horas después de habilitar la integración.
>

   ![Configuración de ATP de WD](./media/wdatp-settings.png)

## <a name="investigate-machines-in-cloud-app-security"></a>Investigar las máquinas de Cloud App Security

After you integrate Microsoft Defender ATP with Cloud App Security, you can investigate discovered machine data in the Cloud Discovery dashboard.

1. En el portal de Cloud App Security, haga clic en **Cloud Discovery** y luego en el **panel de Cloud Discovery**.
2. En la barra de navegación superior, en **Informes continuos**, seleccione **Usuarios del punto de conexión Win10**.
  ![Informe de ATP de WD](./media/win10-dashboard-report.png)
3. En la parte superior, verá el número de equipos detectadas que se ha agregado después de la integración.
4. Haga clic en la pestaña **Máquinas**.
5. Puede explorar en profundidad cada equipo que se muestra y usar las pestañas para ver los datos de la investigación. Busque correlaciones entre los equipos, los usuarios, las direcciones IP y las aplicaciones que estuvieron implicados en incidentes:
   - **Información general**
      - Transactions: Information about the number of transactions that took place on the machine over the selected period of time.
      - Total traffic: Information about the total amount of traffic (in MB) over the selected period of time.
     - Uploads: Information about the total amount of traffic (in MB) uploaded by the machine over the selected period of time.
     - Downloads: Information about the total amount of traffic (in MB) downloaded by the machine over the selected period of time.
   - **Aplicaciones detectadas**<br>
  Enumera todas las aplicaciones detectadas a las que tuvo acceso la máquina.
   - **Historial de usuarios**<br>
    Enumera todos los usuarios que iniciaron sesión en la máquina.
   - **Historial de direcciones IP**<br>
    Enumera todas las direcciones IP que se asignaron a la máquina.
 ![Información general de las máquinas](./media/machines-overview.png)
 
Al igual que con cualquier otro origen de Cloud Discovery, puede exportar los datos del informe de usuarios del punto de conexión Win10 para fines de investigación. 

> [!NOTE]
> - Defender ATP forwards data to Cloud App Security in chunks of ~4 MB (~4000 endpoint transactions)
> - If the 4 MB limit isn't reached within 1 hour, Defender ATP reports all the transactions performed over the last hour.

## <a name="related-videos"></a>Vídeos relacionados

[Shadow IT discovery beyond the corporate network with Microsoft Defender ATP and Cloud App Security](https://www.youtube.com/watch?v=f8hbvbY1Hnc)  

## <a name="next-steps"></a>Pasos siguientes 
[Controlar las aplicaciones en la nube con directivas](control-cloud-apps-with-policies.md) 

[!INCLUDE [Open support ticket](includes/support.md)]  
  
