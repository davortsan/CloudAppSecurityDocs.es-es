---
title: Integrar la Protección contra amenazas avanzada de Windows Defender con Cloud App Security | Microsoft Docs
description: En este artículo se proporciona información sobre cómo integrar ATP de Windows Defender con la integración perfecta de Cloud App Security y la visibilidad mejorada de Shadow IT y la administración de riesgos.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 10/3/2018
ms.topic: conceptual
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: b35ca44c-da8e-49ec-89d1-c076d123c14f
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 114e4deeeca06c41132421a748fb95c5c7e7b34d
ms.sourcegitcommit: 53a1c990ff06674c26563a9ebcb1979818c3c063
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/09/2018
ms.locfileid: "48881880"
---
*Se aplica a: Microsoft Cloud App Security*


# <a name="windows-defender-advanced-threat-protection-integration-with-microsoft-cloud-app-security"></a>Integración de Protección contra amenazas avanzada de Windows Defender con Microsoft Cloud App Security

Microsoft Cloud App Security se integra con Protección contra amenazas avanzada de Windows Defender (ATP) de forma nativa, para simplificar la implementación de Cloud Discovery, ampliar las capacidades de Cloud Discovery más allá de la red corporativa, y habilitar la investigación en el equipo. 

[Protección contra amenazas avanzada de Windows Defender (ATP)](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/windows-defender-advanced-threat-protection) es una plataforma de seguridad para la protección inteligente, la detección, la investigación y la respuesta. ATP de Windows Defender protege los puntos de conexión de las amenazas cibernéticas, detecta vulneraciones de datos y ataques avanzadas, automatiza los incidentes de seguridad y mejora la postura de seguridad.

Microsoft Cloud App Security aprovecha la información de tráfico recopilada por Windows Defender ATP acerca de las aplicaciones en la nube y los servicios a los que se obtiene acceso desde equipos Windows 10 administrados por TI. Esto le permite ejecutar Cloud Discovery en cualquier equipo de la red corporativa mediante Wi-Fi pública, mientras está en itinerancia y a través de un acceso remoto. También permite realizar investigación por máquina: después de identificar un usuario peligroso, podrá comprobar todas las máquinas a las que el usuario accedió para detectar posibles riesgos; si identifica una máquina en riesgo, puede comprobar todos los usuarios que la usaron para detectar posibles riesgos. Los registros de los puntos de conexión que se enrutan a Cloud App Security proporcionan información de usuario para las actividades de tráfico. La actividad de red de ATP de Windows Defender proporciona el contexto de dispositivo, que se puede emparejar con el nombre de usuario para proporcionar una imagen completa de qué usuario ha realizado qué actividad desde el equipo, a través de la red. Microsoft Cloud App Security aprovecha la integración nativa con ATP de Windows Defender para obtener acceso a datos sobre el tráfico del servicio y la aplicación en la nube desde los dispositivos de Windows administrados. Esta integración transparente no requiere ninguna implementación adicional y funciona de inmediato. No es necesario redirigir o reflejar el tráfico desde los puntos de conexión, ni llevar a cabo pasos de integración complejos.

> [!NOTE]
> ¿Desea experimentar ATP de Windows Defender? [Suscríbase para disfrutar de una prueba gratuita](https://www.microsoft.com/WindowsForBusiness/windows-atp?ocid=docs-wdatp-assignaccess-abovefoldlink)
>


## <a name="prerequisites"></a>Requisitos previos

- Licencia de Microsoft Cloud App Security
- Licencia de ATP de Windows Defender
- Equipos con Windows 10 que ejecutan la versión 1809 o posterior


## <a name="how-it-works"></a>Cómo funciona

Por su cuenta, Cloud App Security recopila registros de los puntos de conexión [usando registros cargados](create-snapshot-cloud-discovery-reports.md) o [configurando la carga automática de registros](discovery-docker.md). Esta integración nativa le permite aprovechar las ventajas de los registros que crea el agente de ATP de Windows Defender cuando se ejecuta en Windows. Además supervisa las transacciones de red y las utiliza para Shadow IT Discovery a través de las máquinas de Windows en la red. 

Para que pueda realizar Cloud Discovery en otras plataformas, es mejor usar tanto el [recopilador de registros](discovery-docker.md) de Cloud App Security como la integración con ATP de Windows Defender para supervisar las máquinas de Windows 10.


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

Después de integrar ATP de Windows Defender con Cloud App Security, podrá investigar los datos del equipo detectados en el panel de Cloud Discovery.

1. En el portal de Cloud App Security, haga clic en **Cloud Discovery** y luego en el **panel de Cloud Discovery**.
2. En la barra de navegación superior, en **Informes continuos**, seleccione **Usuarios del punto de conexión Win10**.
  ![Informe de ATP de WD](./media/win10-dashboard-report.png)
4. Puede ver que en la parte superior, el número de máquinas detectadas se agregó después de la integración.
5. Haga clic en la pestaña **Máquinas**.
6. Puede profundizar en cada máquina en la lista y utilizar las pestañas para ver los datos de investigación y buscar correlaciones entre las máquinas y los usuarios, las direcciones IP y las aplicaciones que están implicadas en incidentes:
   - **Información general**
      - Transacciones: le proporciona información sobre el número de transacciones que tuvieron lugar en el equipo en el período de tiempo seleccionado.
      - Tráfico total: le proporciona información sobre la cantidad total de tráfico (en MB) en el período de tiempo seleccionado.
     - Cargas: le proporciona información sobre la cantidad total de tráfico (en MB) cargada por la máquina en el período de tiempo seleccionado.
     - Descargas: le proporciona información sobre la cantidad total de tráfico (en MB) descargada por la máquina en el período de tiempo seleccionado.
   - **Aplicaciones detectadas**<br>
  Enumera todas las aplicaciones detectadas a las que tuvo acceso la máquina.
   - **Historial de usuarios**<br>
    Enumera todos los usuarios que iniciaron sesión en la máquina.
   - **Historial de direcciones IP**<br>
    Enumera todas las direcciones IP que se asignaron a la máquina.
 ![Información general de las máquinas](./media/machines-overview.png)
 

Al igual que con cualquier otro origen de Cloud Discovery, puede exportar los datos del informe de usuarios del punto de conexión Win10 para fines de investigación. 


## <a name="related-videos"></a>Vídeos relacionados  
[Shadow IT Discovery más allá de la red corporativa con ATP de Windows Defender y en la nube](https://www.youtube.com/watch?v=f8hbvbY1Hnc)  

## <a name="see-also"></a>Consulte también  
[Controlar las aplicaciones en la nube con directivas](control-cloud-apps-with-policies.md)   

[Los clientes Premier también pueden elegir Cloud App Security directamente desde el Portal Premier.](https://premier.microsoft.com/)  
  
