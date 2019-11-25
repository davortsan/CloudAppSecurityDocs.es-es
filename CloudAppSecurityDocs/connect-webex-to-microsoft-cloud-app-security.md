---
title: Connect Webex to Cloud App Security
description: This article provides information about how to connect your Webex app to Cloud App Security using the API connector  for visibility and control over use.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 04/16/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 2f35d499398f6d538b552678d5c30740e2f5d5ea
ms.sourcegitcommit: 094bb42a198fe733cfd3aec79d74487672846dfa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/24/2019
ms.locfileid: "74460830"
---
# <a name="connect-cisco-webex-to-microsoft-cloud-app-security"></a>Connect Cisco Webex to Microsoft Cloud App Security

*Se aplica a: Microsoft Cloud App Security*

This article provides instructions for connecting Microsoft Cloud App Security to your existing Cisco Webex account using the connector APIs. This connection gives you visibility into and control over Webex users, activities, and files.

## <a name="prerequisites"></a>Requisitos previos

- We suggest that you create a dedicated service account for the connection. This enables you to see that governance actions performed in Webex as being performed from this account, such as delete messages sent in Webex. Otherwise, the name of the admin who connected Cloud App Security to Webex will appear as the user who performed the actions.
- You must have Full administrator **and** Compliance administrator permissions in Webex.

## <a name="how-to-connect-webex-to-cloud-app-security"></a>How to connect Webex to Cloud App Security

1. En la consola de Cloud App Security, haga clic en **Investigar** y, después, en **Aplicaciones conectadas**.

1. In the **App connectors** page, click the plus button followed by **Cisco Webex**.

    ![connect Webex](./media/cisco-webex.png "connect Webex")

1. In the pop-up, enter the instance name of this connector.

1. Click **Connect Cisco Webex**. The Webex sign in page opens. Enter your credentials to allow Cloud App Security access to your team's Webex instance.

1. Webex asks you if you want to allow Cloud App Security access to your team information, activity log, and perform activities as a team member. Para continuar, haga clic en **Permitir**.

1. Back in the Cloud App Security console, you should receive a message that Webex was successfully connected.

1. Haga clic en **Probar API** para asegurarse de que la conexión se ha realizado correctamente.

    La prueba puede tardar unos minutos. Cuando reciba la notificación de que se ha realizado correctamente, haga clic en **Cerrar**.

After connecting Webex, you'll receive events for 7 days prior to connection. Cloud App Security scans events over the past three months. To increase this, you must have a Cisco Webex pro license and open a ticket with Cloud App Security support.

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Controlar las aplicaciones en la nube con directivas](control-cloud-apps-with-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]
