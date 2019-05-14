---
title: Conexión de Box con Cloud App Security
description: En este artículo se proporciona información sobre cómo conectar la aplicación de Box con Cloud App Security mediante el conector de API para la visibilidad y el control del uso.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: rkarlin
ms.date: 12/10/2018
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: b3e4713e-986f-4a5e-9fcc-f8de94dd0df7
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 5d9a5835473eb6a6012c315a1313fbf05cd9ced5
ms.sourcegitcommit: 9f0c562322394a3dfac7f1d84286e673276a28b1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/14/2019
ms.locfileid: "65568121"
---
# <a name="connect-box-to-microsoft-cloud-app-security"></a>Conectar Box con Microsoft Cloud App Security

*Se aplica a: Microsoft Cloud App Security*

En este artículo se ofrecen instrucciones para conectar Microsoft Cloud App Security con una cuenta de Box existente mediante la API del conector de aplicaciones. Esta conexión le ofrece visibilidad y control del uso de Box.
  
## <a name="how-to-connect-box-to-cloud-app-security"></a>Cómo conectar Box con Cloud App Security  
  
> [!NOTE]  
>  Si se implementa con una cuenta que no es una cuenta de administrador, se produce un error en la prueba de la API y no se permite a Cloud App Security analizar todos los archivos de Box. Si esto supone un problema, puede implementar con un coadministrador con todos los privilegios verificados, aunque la prueba de la API seguirá generando un error y no se analizarán los archivos que pertenezcan a otros administradores en Box.  
  
1.  Si restringe el acceso de permisos de la aplicación, siga estos pasos. De lo contrario, vaya al paso 2.  
  
    -   En la consola de administrador de Box, haga clic en el icono de configuración y luego en **Business settings** (Configuración de Business) o **Enterprise settings** (Configuración de Enterprise).  
  
         ![configuración empresarial de Box](./media/box-business-settings.png "configuración empresarial de Box")  
  
    -   Haga clic en la pestaña **Aplicaciones**.  
  
         ![aplicaciones de Box](./media/box-apps.png "aplicaciones de Box")  
  
    -   Si ha seleccionado **Aplicaciones no publicadas**, en el cuadro de texto **Excepto**, agregue el número de serie de la aplicación Cloud App Security:
     
         |Centro de datos|Número de serie de Microsoft Cloud App Security|
         |----|----|    
         |Estados Unidos 1| `nduj1o3yavu30dii7e03c3n7p49cj2qh`|
         |US2|`w0ouf1apiii9z8o0r6kpr4nu1pvyec75`|
         |US3|`dmcyvu1s9284i2u6gw9r2kb0hhve4a0r`|
         |Unión Europea 1|`me9cm6n7kr4mfz135yt0ab9f5k4ze8qp`|
         |EU2|`uwdy5r40t7jprdlzo85v8suw1l4cdsbf`|

        Después, haga clic en **Guardar**. Para más información sobre cómo consultar con qué centros de datos de Cloud App Security tiene conexión, vea [Tokens de API](api-tokens.md). 
  
         ![configuración del cuadro Excepto de Box](./media/box-settings-except-for.png "configuración del cuadro Excepto de Box")  
  
    > [!NOTE]  
    >  Si es cliente de Adallom y la dirección URL de la consola es de Adallom y no de Cloud App Security, use este número de serie de la aplicación: bwahmilhdlpbqy2ongkl119o3lrkoshc.  
  
2.  En el portal de Cloud App Security, haga clic en **Investigar** y, después, en **Aplicaciones conectadas**.  
  
3.  En la página **Conectores de aplicaciones**, haga clic en el botón del signo más y seleccione **Box**.  
  
     ![conectar Box](./media/connect-box.png "conectar Box")  
  
4.  En el elemento emergente **Box settings** (Configuración de Box), haga clic en **Follow this link** (Seguir este vínculo).  
  
5.  Se abre la página de inicio de sesión de Box. Escriba sus credenciales para permitir que Cloud App Security tenga acceso a la aplicación de Box de su equipo.  
  
6.  Box le pregunta si quiere permitir que Cloud App Security acceda a la información y el registro de actividad de su equipo y que realice actividades como cualquier miembro del equipo. Para continuar, haga clic en **Permitir**.  
  
7.  De vuelta en el portal de Cloud App Security, debería recibir un mensaje que indica que Box se ha conectado correctamente.  
  
8.  Haga clic en **Probar API** para confirmar que la conexión se ha realizado correctamente.  
  
     La prueba puede tardar unos minutos. Cuando reciba la notificación de que se ha realizado correctamente, haga clic en **Cerrar**.  
  
Box ya está conectado a Cloud App Security.  
 
Después de conectar Box, recibirá eventos de 60 días anteriores a la conexión.
  
Después de conectar Box, Cloud App Security realiza un examen completo. En función del número de archivos y los usuarios que tenga, el examen podría tardar en completarse. Para habilitar el análisis casi en tiempo real, los archivos en los que se detectan actividades se mueven al principio de la cola de análisis. Por ejemplo, un archivo editado, actualizado o compartido se analiza inmediatamente, en lugar de esperar al proceso de análisis normal. El análisis casi en tiempo real no se aplica a los archivos que no se modifican de forma inherente. Por ejemplo, los archivos que se visualizan, previsualizan, imprimen o exportan se analizan como parte del análisis programado habitual.
  
## <a name="next-steps"></a>Pasos siguientes 
[Controlar las aplicaciones en la nube con directivas](control-cloud-apps-with-policies.md)   

[Los clientes Premier también pueden crear una solicitud de soporte técnico directamente en el portal Premier.](https://premier.microsoft.com/)  
  
  
