---
title: Incorporación de aplicaciones personalizadas a Cloud Discovery en Cloud App Security | Microsoft Docs
description: En este tema se ofrece información sobre cómo agregar aplicaciones personalizadas a Cloud Discovery en Cloud App Security para supervisar Shadow IT.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 5/27/2018
ms.topic: conceptual
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 98b0d841-b33d-4ae9-b48b-d9ee77785eaa
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: e1fc6388107a33bf42aada57e17153a3d7b8437e
ms.sourcegitcommit: 0ac08ca7b3140b79f1d36ff7152476c188fa12b3
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/07/2018
ms.locfileid: "44142483"
---
*Se aplica a: Microsoft Cloud App Security*

# <a name="add-custom-apps-to-cloud-discovery"></a>Incorporación de aplicaciones personalizadas a Cloud Discovery
    
Cloud Discovery analiza los registros de tráfico en el catálogo de aplicaciones en la nube de Microsoft Cloud App Security de más de 16 000 aplicaciones en la nube. El catálogo solo contiene aplicaciones en la nube disponibles públicamente sobre las que Cloud App Security ofrece información de visibilidad y riesgo.

Para obtener una mayor visibilidad en aplicaciones en la nube que están excluidas del catálogo de aplicaciones en la nube, Cloud App Security permite detectar el uso de aplicaciones personalizadas en la nube (aplicaciones de LOB) que se han desarrollado o asignado específicamente a su organización.

Al agregar una nueva aplicación personalizada en la nube, Cloud App Security puede establecer coincidencias entre los mensajes de registro de tráfico del servidor proxy y el firewall cargados y, luego, ofrecer visibilidad sobre el uso de esta aplicación a través de la organización en las páginas de Cloud Discovery, como, por ejemplo, cuántos usuarios utilizan la aplicación, cuántas direcciones IP de origen único usan y cuánto tráfico se transmite hacia y desde la aplicación. 

Para agregar una nueva aplicación personalizada en la nube:

1. En el portal de Cloud App Security, haga clic en **Detectar** y luego en **Cloud Discovery dashboard** (Panel de Cloud Discovery). 
  
   ![menú del panel de Cloud Discovery](./media/cloud-discovery-dashboard-menu.png)

2. En la esquina superior derecha, haga clic en los tres puntos y seleccione **Agregar nueva aplicación personalizada**. 

   ![menú agregar aplicación personalizada](./media/add-custom-app-menu.png)

3. Rellene los campos para definir el registro de la nueva aplicación que se mostrará en el catálogo de aplicaciones en la nube y en Cloud Discovery una vez detectada en los registros de firewall.

   ![aplicación personalizada](./media/add-custom-app.png)

4. En **Dominios**, rellene los dominios únicos que se utilizan al obtener acceso a la aplicación personalizada. Estos dominios se usan para establecer coincidencias entre los mensajes de registro de tráfico y la aplicación. Si el origen de datos que usa no contiene información de dirección URL de la aplicación, asegúrese de rellenar los campos de direcciones **IPv4** y **IPv6**.
5. Se recomienda agregar notas que le permitan realizar un seguimiento de cambios de este registro.

Una vez creada la aplicación, está disponible para usted en el catálogo de aplicaciones en la nube.

Siempre que quiera, puede hacer clic en los tres puntos al final de la fila para editar o eliminar una aplicación personalizada.

>[!NOTE]
> - Las aplicaciones personalizadas se etiquetan automáticamente con la etiqueta **Aplicación personalizada** después de agregarlas. Esta etiqueta de la aplicación no se puede quitar.
Para ver todas las aplicaciones personalizadas, establezca el filtro **Etiqueta de aplicación** para que sea igual a "Aplicación personalizada". 
> - De forma predeterminada, las aplicaciones personalizadas tienen una puntuación de riesgo de 10, pero puede usar la acción **Reemplazar puntuación de la aplicación** para cambiarla cuando quiera.

  
## <a name="see-also"></a>Consulte también  
[Directivas de actividad de usuario](user-activity-policies.md)   

[Los clientes Premier también pueden elegir Cloud App Security directamente desde el Portal Premier.](https://premier.microsoft.com/)  
  
  