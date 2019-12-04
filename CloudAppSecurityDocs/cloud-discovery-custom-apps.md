---
title: Incorporación de aplicaciones personalizadas a Cloud Discovery en Cloud App Security
description: En este tema se ofrece información sobre cómo agregar aplicaciones personalizadas a Cloud Discovery en Cloud App Security para supervisar Shadow IT.
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
ms.openlocfilehash: 768248178042ecc7c3af5289ea1b6c27aa92b37e
ms.sourcegitcommit: 7c93b6f93d2699d466b172590710ed01697bbdad
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74719239"
---
# <a name="add-custom-apps-to-cloud-discovery"></a>Incorporación de aplicaciones personalizadas a Cloud Discovery

*Se aplica a: Microsoft Cloud App Security*

Cloud Discovery analiza los registros de tráfico en el catálogo de aplicaciones en la nube de Microsoft Cloud App Security. Más de 16 000 aplicaciones de la nube se encuentran en el catálogo de aplicaciones en la nube. El catálogo solo contiene aplicaciones en la nube disponibles públicamente sobre las que Cloud App Security ofrece información de visibilidad y riesgo.

Para obtener una mayor visibilidad de las aplicaciones en la nube que están excluidas del catálogo de aplicaciones en la nube, Cloud App Security permite detectar el uso de aplicaciones personalizadas en la nube (aplicaciones de LOB) que se han desarrollado o asignado específicamente a su organización.

Al agregar una nueva aplicación personalizada en la nube, Cloud App Security puede establecer coincidencias entre los mensajes de registro de tráfico del servidor proxy y el firewall cargados para la aplicación y, luego, ofrecer visibilidad sobre el uso de esta aplicación a través de la organización en las páginas de Cloud Discovery, como, por ejemplo, cuántos usuarios utilizan la aplicación, cuántas direcciones IP de origen único usan y cuánto tráfico se transmite hacia y desde la aplicación.

## <a name="add-a-new-custom-cloud-app"></a>Agregar una nueva aplicación personalizada en la nube

1. En el portal de Cloud App Security, haga clic en **Detectar** y luego en **Cloud Discovery dashboard** (Panel de Cloud Discovery).

    ![menú del panel de Cloud Discovery](media/cloud-discovery-dashboard-menu.png)

2. En la esquina superior derecha, haga clic en los tres puntos y seleccione **Agregar nueva aplicación personalizada**.

    ![menú agregar aplicación personalizada](media/add-custom-app-menu.png)

3. Rellene los campos para definir el registro de la nueva aplicación que se mostrará en el catálogo de aplicaciones en la nube y en Cloud Discovery una vez que se haya detectado en los registros de firewall.

    ![aplicación personalizada](media/add-custom-app.png)

4. En **Dominios**, rellene los dominios únicos que se utilizan al obtener acceso a la aplicación personalizada. Estos dominios se usan para establecer coincidencias entre los mensajes de registro de tráfico y la aplicación. Si el origen de datos que usa no contiene información de la URL de la aplicación, asegúrese de rellenar los campos de direcciones **IPv4** e **IPv6**.
5. Agregue la **plataforma de hospedaje** y el **Id. de suscripción de Azure**. Si quiere, especifique la **unidad de negocio** de la aplicación.
6. Asigne una **puntuación** de riesgo y agregue **notas de la aplicación** para poder realizar un seguimiento de los cambios de este registro.
7. Haga clic en **Crear**.

Una vez creada la aplicación, estará disponible para su uso en el catálogo de aplicaciones en la nube.

Siempre que quiera, puede hacer clic en los tres puntos del final de la fila para editar o eliminar una aplicación personalizada.

>[!NOTE]
> Las aplicaciones personalizadas se etiquetan automáticamente con la etiqueta **Aplicación personalizada** después de agregarlas. Esta etiqueta de la aplicación no se puede quitar.
Para ver todas las aplicaciones personalizadas, establezca el filtro **Etiqueta de aplicación** para que sea igual a "Aplicación personalizada".
<!-- - By default, custom apps have a risk score of 10, but you can use the **Override app score** action to change it at any time.-->

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Directivas de actividad de usuario](user-activity-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]
