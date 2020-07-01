---
title: Integración adicional con Cloud App Security
description: En este artículo se proporciona información sobre la integración de soluciones de terceros con Cloud App Security.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 06/28/2020
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: ca393149f9a0ae9a87ec087c6e94baba63ed9c91
ms.sourcegitcommit: 7811a0d33e1756782222f20df02acae2f3ea4afe
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2020
ms.locfileid: "85795846"
---
# <a name="additional-integrations-with-external-solutions"></a>Integraciones adicionales con soluciones externas

*Se aplica a: Microsoft Cloud App Security*

Puede integrar Microsoft Cloud App Security con sus otras inversiones de seguridad para aprovechar y mejorar un ecosistema de protección integrado. Por ejemplo, puede integrar con soluciones de administración de dispositivos móviles externas, soluciones de UEBA y fuentes externas de inteligencia de amenazas.

La sólida plataforma de Cloud App Security le permite integrarse con una amplia variedad de soluciones de seguridad externas, entre las que se incluyen:

- **Fuentes de inteligencia de amenazas (TI) (traiga su propiedad)**  
    Puede usar el Cloud App Security [API de intervalo de direcciones IP](api-data-enrichment.md) para agregar nuevos intervalos de direcciones IP de riesgo identificados por soluciones de TI de terceros. Una vez definidos, los intervalos de direcciones IP permiten etiquetar, clasificar y personalizar la forma en que se muestran e investigan los registros y las alertas.

- **Soluciones de administración de dispositivos móviles (MDM) y Mobile Threat Defense (MTD)**  
    Cloud App Security proporciona controles de sesión granulares en tiempo real. Un factor clave en la evaluación y protección de las sesiones es el dispositivo que usa el usuario, lo que ayuda a crear una identidad completa. El estado de administración de un dispositivo se puede identificar directamente a través del estado de administración de dispositivos en [Azure Active Directory (Azure ad)](/azure/active-directory/conditional-access/overview), [Microsoft Intune](/intune/mobile-threat-defense)o de forma más genérica a través del análisis de certificados de cliente que permiten la integración con una variedad de soluciones MDM y MTD de terceros.

    Cloud App Security puede aprovechar las señales de las soluciones MDM y MTD externas para aplicar los controles de sesión en función del [Estado de administración de un dispositivo](proxy-intro-aad.md#managed-device-identification).

- **Soluciones UEBA**  
    Puede usar varias soluciones UEBA para satisfacer diferentes cargas de trabajo y escenarios, donde cada solución de UEBA se basa en varios orígenes de datos para identificar el comportamiento de los usuarios sospechosos y anómalos. Las soluciones de UEBA externas se pueden integrar con el ecosistema de seguridad de Microsoft a través de Azure AD Identity Protection.

    Una vez integradas, las directivas se pueden usar para identificar a los usuarios de riesgo, aplicar controles adaptables y corregir automáticamente los usuarios de riesgo estableciendo el nivel de riesgo del usuario en alto. Una vez que un usuario está establecido en alto, se aplican las acciones de directiva pertinentes, como restablecer la contraseña de un usuario, requerir la autenticación MFA o forzar a un usuario a usar un dispositivo administrado.

    Cloud App Security permite que los equipos de seguridad confirmen de forma automática o manual a un usuario como comprometido, para garantizar una corrección rápida de los usuarios en peligro.

    Para obtener más información, consulte [Azure ad ¿cómo usan los comentarios de riesgo](/azure/active-directory/identity-protection/howto-identity-protection-risk-feedback#how-does-azure-ad-use-my-risk-feedback) y [las acciones de gobierno](accounts.md#governance-actions)?

[!INCLUDE [Open support ticket](includes/support.md)]
