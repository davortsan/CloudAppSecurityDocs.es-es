---
title: Diferencias de capacidad de detección en Cloud App Security y Azure AD
description: En este artículo se describen las diferencias entre las capacidades de detección de Microsoft Cloud App Security y Azure AD.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 8/29/2019
ms.topic: overview
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 7007f8aad61c1f504a73855360fad40f0c58bcc4
ms.sourcegitcommit: 138d435905eaf29584f50d6dac30489d2104189a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/06/2020
ms.locfileid: "93415426"
---
# <a name="what-are-the-differences-in-discovery-capabilities-for-azure-active-directory-and-microsoft-cloud-app-security"></a>¿Qué diferencias hay en las funcionalidades de detección de Azure Active Directory y Microsoft Cloud App Security?

[!INCLUDE [Banner for top of topics](includes/banner.md)]

En este artículo se explican las diferencias entre las funciones de detección de Microsoft Cloud App Security y Azure Active Directory (Azure AD).

Para información sobre las licencias, consulte la [hoja de datos de licencias de Microsoft Cloud App Security](https://aka.ms/mcaslicensing).

## <a name="microsoft-cloud-app-security"></a>Microsoft Cloud App Security

Microsoft Cloud App Security es una solución completa entre SaaS que proporciona visibilidad detallada, controles de datos seguros y protección contra amenazas mejorada a las aplicaciones en la nube. Cloud Discovery es una de las características de Cloud App Security, que le permite obtener visibilidad de Shadow IT al detectar aplicaciones en la nube en uso.

## <a name="enhanced-cloud-app-discovery-in-azure-active-directory"></a>Cloud App Discovery mejorado en Azure Active Directory

Azure Active Directory Premium P1 incluye [Cloud App Discovery de Azure Active Directory](./set-up-cloud-discovery.md) sin costo adicional. Esta característica se basa en las funciones de Microsoft Cloud App Security Cloud Discovery que proporcionan una mayor visibilidad en el uso de las aplicaciones en la nube en sus organizaciones. [Actualice a Microsoft Cloud App Security](https://www.microsoft.com/cloud-platform/cloud-app-security) para recibir el conjunto completo de funciones de Cloud App Security Broker (CASB) que ofrece Microsoft Cloud App Security.

### <a name="feature-comparison"></a>Comparación de características

La siguiente tabla compara las capacidades de detección de Microsoft Cloud App Security y Azure AD.

|Capacidad|Característica|Microsoft Cloud App Security|Azure AD Cloud App Discovery|
|----|----|----|----|
|Cloud Discovery|Aplicaciones detectadas|Más de 16 000 aplicaciones en la nube|Más de 16 000 aplicaciones en la nube|
||Implementación para análisis de detección|Carga de registros manual y automática|Carga de registros manual y automática|
||Anonimización de registros para la privacidad del usuario|Sí|Sí|
||Acceso al catálogo completo de aplicaciones en la nube|Sí|Sí|
||Valoración del riesgo de las aplicaciones en la nube|Sí|Sí|
||Análisis del uso de la nube por aplicación, usuario y dirección IP|Sí|Sí|
||Informes y análisis en curso|Sí|Sí|
||Detección de anomalías en las aplicaciones detectadas|Sí||
|Protección de la información|Compatibilidad con la prevención de pérdida de datos (DLP)|Control de uso compartido de datos y DLP entre SaaS||
||Permisos de aplicación y capacidad para revocar el acceso (aplicaciones de OAuth)|Sí||
||Configuración y cumplimiento de directivas|Sí||
||Integración con Azure Information Protection |Sí||
||Integración con soluciones DLP de terceros|Sí||
|Detección de amenazas|Detección de anomalías y análisis del comportamiento|Para aplicaciones entre SaaS||
||Corrección manual y automática de alertas|Sí||
||Conector SIEM|Sí. Alertas y registros de actividad para aplicaciones entre SaaS.||
||Integración con Microsoft Intelligent Security Graph|Sí||
||Directivas de actividad|Sí||

## <a name="next-steps"></a>Pasos siguientes

Consulte los aspectos básicos en [Introducción a Cloud App Security](getting-started-with-cloud-app-security.md).

[!INCLUDE [Open support ticket](includes/support.md)].