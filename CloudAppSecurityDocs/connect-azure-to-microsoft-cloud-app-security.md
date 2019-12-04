---
title: Conexión de Azure con Cloud App Security
description: En este artículo se proporciona información sobre cómo conectar Azure con Cloud App Security mediante el conector de API para la visibilidad y el control del uso.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 12/10/2018
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: aff0d6d0b554f6b26501591bc03c1e39db789349
ms.sourcegitcommit: 7c93b6f93d2699d466b172590710ed01697bbdad
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74720046"
---
# <a name="connect-azure-to-microsoft-cloud-app-security"></a>Conectar Azure con Microsoft Cloud App Security

*Se aplica a: Microsoft Cloud App Security*

En este artículo se ofrecen instrucciones para conectar Microsoft Cloud App Security con una cuenta de Azure existente mediante la API del conector de aplicaciones. Esta conexión le ofrece visibilidad y control del uso de Azure.

## <a name="how-to-connect-azure-to-cloud-app-security"></a>Cómo conectar Azure con Cloud App Security

> [!NOTE]
>
> - Es necesario ser administrador global de Azure AD para poder conectar Azure con Microsoft Cloud App Security.
> - Cloud App Security muestra las actividades de **todas** las suscripciones.
> - Actualmente, Cloud App Security solo supervisa las actividades ARM.

1. En la página **Aplicaciones conectadas**, haga clic en el botón del signo más y seleccione **Microsoft Azure**.

    ![Conectar Azure](media/connect-azure-menu.png)

2. En el menú emergente de Azure, haga clic en **Conectar con Microsoft Azure**.

    ![Conectar Azure](media/connect-azure.png)

> [!NOTE]
> Se extraerán los datos una vez que conecte Azure. Verá los datos correspondientes a partir de ese momento.

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Controlar las aplicaciones en la nube con directivas](control-cloud-apps-with-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]
