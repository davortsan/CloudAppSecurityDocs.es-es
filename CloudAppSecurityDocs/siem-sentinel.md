---
title: Integración de Azure Sentinel con Cloud App Security
description: En este artículo se proporciona información sobre cómo integrar el SIEM genérico con Cloud App Security.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 10/28/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: f7664685204a2d2f1965800119c946c85f2cbe49
ms.sourcegitcommit: 094bb42a198fe733cfd3aec79d74487672846dfa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/24/2019
ms.locfileid: "74460388"
---
# <a name="azure-sentinel-integration-preview"></a>Integración de centinela de Azure (versión preliminar)

*Se aplica a: Microsoft Cloud App Security*

Puede integrar Microsoft Cloud App Security con Azure Sentinel (un SIEM escalable y nativo en la nube) para habilitar la supervisión centralizada de alertas y datos de detección. La integración con Azure Sentinel le permite proteger mejor sus aplicaciones en la nube a la vez que mantiene su flujo de trabajo de seguridad habitual, automatiza los procedimientos de seguridad y correlaciona entre eventos basados en la nube y locales.

Las ventajas de usar Azure Sentinel incluyen:

* Retención de datos más larga proporcionada por Log Analytics.
* Visualizaciones preparadas.
* Use herramientas como Microsoft Power BI o libros de Azure Sentinel para crear sus propias visualizaciones de datos de detección que se adapten a las necesidades de su organización.

Entre las soluciones de integración adicionales se incluyen:

* **Siem genéricos** : Integre Cloud App Security con el servidor de Siem genérico. Para obtener información sobre la integración con un SIEM genérico, consulte [integración de Siem genérica](siem.md).
* **Microsoft Security Graph API** : un servicio intermediario (o agente) que proporciona una única interfaz de programación para conectar varios proveedores de seguridad. Para obtener más información, consulte [integración de soluciones de seguridad con la API de seguridad de Microsoft Graph](https://docs.microsoft.com/graph/security-integration#list-of-connectors-from-microsoft).

## <a name="how-to-integrate"></a>Integración

La integración con SIEM se realiza en dos pasos:

1. Establézcalo en Cloud App Security.
1. Establézcalo en Azure Sentinel.

### <a name="prerequisites"></a>Prerequisites

Para integrar con Azure Sentinel:

* Debe tener una licencia válida de Azure Sentinel
* Debe ser un administrador global o un administrador de seguridad de su inquilino.

### <a name="integrating-with-azure-sentinel"></a>Integración con Azure Sentinel

1. En el portal de Cloud App Security, en el engranaje de **configuración** , haga clic en **extensiones de seguridad**.

1. En la pestaña **agentes Siem** , haga clic en agregar ( **+** ) y, a continuación, elija **centinela de Azure**.

    ![Captura de pantalla que muestra el menú Agregar integración de SIEM](media/siem0.png)

1. En el asistente, seleccione los tipos de datos que quiere reenviar a Azure Sentinel. Puede configurar la integración de la siguiente manera:
    1. **Alertas**: las alertas se activan automáticamente una vez habilitado Azure Sentinel. <!--Use the **Apply to** drop-down to filter which alerts are sent to Azure Sentinel.-->
    1. **Registros de detección**: Use el control deslizante para habilitarlos y deshabilitarlos, de forma predeterminada, todo está seleccionado y, a continuación, use la lista desplegable **aplicar a** para filtrar los registros de detección que se enviarán a Azure Sentinel.

    ![Captura de pantalla que muestra la página de inicio de configuración de la integración de centinela de Azure](media/siem-sentinel-configuration.png)

1. Haga clic en **siguiente**y continúe con Azure Sentinel para finalizar la integración. Para obtener información sobre cómo configurar Azure Sentinel, consulte [https://docs.microsoft.com/azure/sentinel/connect-cloud-app-security](https://docs.microsoft.com/azure/sentinel/connect-cloud-app-security).

    ![Captura de pantalla que muestra la página de finalización de configuración de Azure Sentinel](media/siem-sentinel-configuration-complete.png)

> [!NOTE]
> Los registros de detección comenzarán a reenviarse a Azure Sentinel en un plazo de 15 minutos después de configurarlos en el portal de Cloud App Security.

## <a name="alerts-and-discovery-logs-in-azure-sentinel"></a>Alertas y registros de detección en Azure Sentinel

Una vez completada la integración, puede ver Cloud App Security alertas y registros de detección en Azure Sentinel.

En Azure Sentinel, en **registros**, en **Security Insights**, puede encontrar los registros de los tipos de datos Cloud App Security, como se indica a continuación:

| Tipo de datos | Table |
| --- | --- |
| Registros de detección | McasShadowItReporting |
| Alertas | SecurityAlert |

En la tabla siguiente se describe cada campo del esquema **McasShadowItReporting** :

| Campo | Tipo | Descripción | Ejemplos |
| --- | --- | --- | --- |
| TenantId | String | IDENTIFICADOR del área de trabajo | b459b4u5-912x-46d5-9cb1-p43069212nb4 |
| SourceSystem | String | Sistema de origen: valor estático | Azure |
| TimeGenerated [UTC] | DateTime | Fecha de datos de detección | 2019-07-23T11:00:35.858 Z |
| Nombredeflujo | String | Nombre del flujo específico | Departamento de marketing |
| TotalEvents | Integer | Número total de eventos por sesión | 122 |
| BlockedEvents | Integer | Número de eventos bloqueados | 0 |
| UploadedBytes | Integer | Cantidad de datos cargados | 1\.514.874 |
| TotalBytes | Integer | Cantidad total de datos | 4\.067.785 |
| DownloadedBytes | Integer | Cantidad de datos descargados | 2\.552.911 |
| DirIP | String | Dirección IP de origen | 127.0.0.0 |
| UserName | String | Nombre de usuario | `Raegan@contoso.com` |
| EnrichedUserName | String | Nombre de usuario enriquecido con Azure AD nombre de usuario | `Raegan@contoso.com` |
| Nombreaplicación | String | Nombre de la aplicación en la nube | Microsoft OneDrive para la empresa |
| AppId | Integer | Identificador de aplicación en la nube | 15600 |
| AppCategory | String | Categoría de aplicación en la nube | Almacenamiento en nube |
| AppTags | Matriz de cadenas | Etiquetas personalizadas y integradas definidas para la aplicación | ["autorizada"] |
| AppScore | Integer | La puntuación de riesgo de la aplicación en una escala 0-10, 10 es una puntuación para una aplicación no peligrosa. | 10 |
| Tipo | String | Tipo de registros: valor estático | McasShadowItReporting |

## <a name="use-power-bi-with-cloud-app-security-data-in-azure-sentinel"></a>Uso de Power BI con datos de Cloud App Security en Azure Sentinel

Una vez completada la integración, también puede usar los datos de Cloud App Security almacenados en Azure Sentinel en otras herramientas.

En esta sección se describe cómo puede usar Microsoft Power BI (Power BI) para dar forma a los datos y combinarlos fácilmente para crear informes y paneles que satisfagan las necesidades de su organización.

Puede empezar a trabajar rápidamente con los pasos siguientes:

1. En Power BI, importe consultas desde Azure Sentinel para datos de Cloud App Security. Para obtener más información, consulte [importar datos de registro de Azure monitor en Power BI](https://docs.microsoft.com/azure/azure-monitor/platform/powerbi).
1. [Instale la aplicación de Shadow it Discovery de Cloud App Security](https://aka.ms/MCASShadowITReporting) y [conéctela](#connect-the-cloud-app-security-app) a los datos del registro de detección para ver el panel de Shadow it Discovery integrado.

    > [!NOTE]
    > Actualmente, la aplicación no se publica en Microsoft AppSource. Por lo tanto, es posible que deba ponerse en contacto con el administrador de Power BI para obtener los permisos para instalar la aplicación.

    ![Captura de pantalla que muestra el panel de Shadow IT Discovery](media/siem-sentinel-configuration-powerbi-dashboard.png)

1. Opcionalmente, puede crear paneles personalizados en Power BI Desktop y ajustarlos para ajustarse a los requisitos de informes y análisis visual de su organización.

### <a name="connect-the-cloud-app-security-app"></a>Conexión de la aplicación Cloud App Security

1. En Power BI, haga clic en **aplicaciones**y, a continuación, haga clic en la aplicación **Shadow it Discovery** .

1. En la página **Introducción a la nueva aplicación** , haga clic en **conectar**.

    ![Captura de pantalla que muestra la página conectar datos de la aplicación](media/siem-sentinel-powerbi-connect.png)

1. En la página identificador del área de trabajo, escriba el identificador del área de trabajo de Azure Sentinel tal y como se muestra en la página de información general de log Analytics y, a continuación, haga clic en **siguiente**.

    ![Captura de pantalla que muestra la solicitud de identificador de área de trabajo](media/siem-sentinel-powerbi-workspace-id.png)

1. En la página autenticación, especifique el método de autenticación y el nivel de privacidad y, a continuación, haga clic en **iniciar sesión**.

    ![Captura de pantalla que muestra la página de autenticación](media/siem-sentinel-powerbi-authentication.png)

1. Después de conectar los datos, vaya a la pestaña **conjuntos** de datos del área de trabajo y haga clic en **Actualizar**. Esto actualizará el informe con sus propios datos.

[!INCLUDE [Open support ticket](includes/support.md)]