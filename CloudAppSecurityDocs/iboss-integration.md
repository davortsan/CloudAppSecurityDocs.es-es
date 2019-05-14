---
title: Integración de Cloud App Security con iboss
description: En este artículo se describe cómo integrar Microsoft Cloud App Security con iboss Secure Cloud Gateway para que Cloud Discovery funcione sin problemas y automatizar el bloqueo de aplicaciones no autorizadas.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: rkarlin
ms.date: 2/2/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 920d4272-685b-4c4d-9b31-94a2c6f3503e
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 31316c4a8902ed85489e03a82dde3fb3ec7962b8
ms.sourcegitcommit: 9f0c562322394a3dfac7f1d84286e673276a28b1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/14/2019
ms.locfileid: "65568192"
---
# <a name="integrate-cloud-app-security-with-iboss"></a>Integración de Cloud App Security con iboss

*Se aplica a: Microsoft Cloud App Security*

Si trabaja con Cloud App Security y iboss, puede integrar los dos productos para mejorar la experiencia de seguridad de Cloud Discovery. iboss es una puerta de enlace en la nube segura e independiente que supervisa el tráfico de su organización y permite establecer directivas que bloqueen las transacciones. Juntos, Cloud App Security y iboss proporcionan las siguientes funcionalidades:

- Implementación fluida de Cloud Discovery: use iboss para redirigir el tráfico mediante proxy y enviarlo a Cloud App Security. Gracias a esto, se elimina la necesidad de instalar los recopiladores de registros en los puntos de conexión de la red para habilitar Cloud Discovery.
- Las funcionalidades de bloqueo de iboss se aplican automáticamente a las aplicaciones que haya establecido como no autorizadas en Cloud App Security.
- Mejore su portal de administración de iboss gracias a la valoración de riesgos de Cloud App Security de las 100 aplicaciones en la nube más importantes de su organización, que se pueden ver directamente en el portal de administración de iboss.

## <a name="prerequisites"></a>Requisitos previos

- Una licencia válida para Microsoft Cloud App Security
- Una licencia válida para iboss Secure Cloud Gateway (versión 9.1.100.0 o posterior)

## <a name="deployment"></a>Implementación

1. En el portal de Cloud App Security, realice los pasos de integración siguientes:
    1. Haga clic en el engranaje de configuración y seleccione **Configuración de Cloud Discovery**. 
    2. Haga clic en la pestaña **Carga automática del registro** y, luego, en **Agregar origen de datos**.
    3. En la página **Agregar origen de datos**, escriba la siguiente configuración:

       - Nombre: iboss
       - Origen: iboss Secure Cloud Gateway
       - Tipo de receptor = Syslog - UDP

         ![Origen de datos iboss](./media/iboss-integration.png)

    4. Haga clic en **Ver ejemplo de archivo de registro previsto**. A continuación, haga clic en **Descargar registro de ejemplo** para ver un registro de detección de ejemplo y asegúrese de que coincida con los registros.<br>

3. Investigue las aplicaciones en la nube que se han detectado en la red. Para obtener más información y pasos de investigación, consulte [Trabajo con Cloud Discovery](working-with-cloud-discovery-data.md).

4. Las aplicaciones que se establecen como no autorizadas en Cloud App Security recibirán un ping por parte de iboss cada 10 minutos y, luego, iboss las bloqueará automáticamente. Para más información sobre las aplicaciones no autorizadas, consulte [Autorizar o no autorizar una aplicación](governance-discovery.md#BKMK_SanctionApp).

5. Si quiere configurar iboss para enviar registros de tráfico a Microsoft Cloud App Security, póngase en contacto con el equipo de soporte técnico de iboss.

## <a name="next-steps"></a>Pasos siguientes

[Controlar las aplicaciones en la nube con directivas](control-cloud-apps-with-policies.md)

[Los clientes Premier también pueden crear una solicitud de soporte técnico directamente en el portal Premier.](https://premier.microsoft.com/)  
  
