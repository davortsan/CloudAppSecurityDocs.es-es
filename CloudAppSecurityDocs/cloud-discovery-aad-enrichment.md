---
title: Enriquecimiento de los datos de Cloud App Security Discovery con nombres de usuario de Azure AD
description: En este artículo se proporciona información sobre cómo enriquecer los datos de Cloud App Security Discovery con nombres de usuario de Azure AD.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 12/10/2018
ms.topic: how-to
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: ae44525ae235bd80ce40a80c7c309e20e64cb5a1
ms.sourcegitcommit: 575f2b2efa9ca4477d7e60271d21e225ef2c38ea
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/22/2020
ms.locfileid: "90881586"
---
# <a name="cloud-discovery-enrichment"></a>Enriquecimiento de Cloud Discovery

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Ahora es posible mejorar los datos de Cloud Discovery con datos de nombre de usuario de Azure Active Directory. Cuando se habilita esta característica, el nombre de usuario que se recibe en los registros de tráfico de detección se hace coincidir con el nombre de usuario de Azure AD y se reemplaza por este. Enriquecimiento de Cloud Discovery ofrece estas características:

- Puede investigar el uso de Shadow IT por parte del usuario de Azure Active Directory.
- Puede correlacionar el uso de las aplicaciones en la nube detectadas con las actividades de API recopiladas.
- Después, puede crear registros personalizados en función de los grupos de usuarios de Azure AD. Por ejemplo, un informe de Shadow IT para un departamento de marketing específico.

## <a name="prerequisites"></a>Requisitos previos

- El origen de datos debe proporcionar información sobre el nombre de usuario.
- [Conector de aplicaciones de Office 365](connect-office-365-to-microsoft-cloud-app-security.md) conectado

## <a name="enabling-user-data-enrichment"></a>Habilitar el enriquecimiento de datos del usuario

1. En el engranaje de configuración, seleccione **configuración de Cloud Discovery**.

2. En la pestaña **Enriquecimiento de usuarios**, seleccione **Enriquezca los identificadores de los usuarios detectados con los nombres de usuario de Azure Active Directory**. Esta opción permite a Cloud App Security usar datos de Azure Active Directory para mejorar los nombres de usuarios de forma predeterminada.

3. Haga clic en **Save**(Guardar).

![Enriquecer Cloud App Security Discovery con nombres de usuario de Azure AD](media/discovery-enrichment.png)

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Controlar las aplicaciones en la nube con directivas](control-cloud-apps-with-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]
