---
title: Conexión de Box con Cloud App Security
description: En este artículo se proporciona información sobre cómo conectar la aplicación de Box con Cloud App Security mediante el conector de API para la visibilidad y el control del uso.
ms.date: 12/10/2018
ms.topic: how-to
ms.openlocfilehash: 9de9d9cfdaefc80beb8d5f9bcf4059cb39fe9178
ms.sourcegitcommit: 16a65ab2c8ca778d0b3cfa97b847af4c812363b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/03/2021
ms.locfileid: "97855665"
---
# <a name="connect-box-to-microsoft-cloud-app-security"></a>Conectar Box con Microsoft Cloud App Security

[!INCLUDE [Banner for top of topics](includes/banner.md)]

En este artículo se ofrecen instrucciones para conectar Microsoft Cloud App Security con una cuenta de Box existente mediante la API del conector de aplicaciones. Esta conexión le ofrece visibilidad y control del uso de Box. Para obtener información sobre cómo Cloud App Security protege el cuadro, consulte [proteger Box](protect-box.md).

## <a name="how-to-connect-box-to-cloud-app-security"></a>Cómo conectar Box con Cloud App Security

> [!NOTE]
> Si se implementa con una cuenta que no es una cuenta de administrador, se produce un error en la prueba de la API y no se permite a Cloud App Security analizar todos los archivos de Box. Si esto supone un problema, puede implementar con un coadministrador con todos los privilegios verificados, aunque la prueba de la API seguirá generando un error y no se analizarán los archivos que pertenezcan a otros administradores en Box.

1. Si restringe el acceso de permisos de la aplicación, siga estos pasos. De lo contrario, vaya al paso 2.

    1. Inicie sesión con una cuenta de administrador en su cuenta de Box.
    1. Haga clic en la configuración de aplicaciones personalizadas de **aplicaciones**  >    >  .

         ![aplicaciones de Box](media/box-apps.png "aplicaciones de Box")

    1. Si la **opción deshabilitar aplicaciones no publicadas** está seleccionada de forma predeterminada, en el cuadro **de texto excepto para** , agregue la clave de API de Cloud App Security:

         |Centro de datos|Clave de API de Cloud App Security|
         |----|----|
         |Estados Unidos 1|`nduj1o3yavu30dii7e03c3n7p49cj2qh`|
         |US2|`w0ouf1apiii9z8o0r6kpr4nu1pvyec75`|
         |US3|`dmcyvu1s9284i2u6gw9r2kb0hhve4a0r`|
         |Unión Europea 1|`me9cm6n7kr4mfz135yt0ab9f5k4ze8qp`|
         |EU2|`uwdy5r40t7jprdlzo85v8suw1l4cdsbf`|

        A continuación, haga clic en **Save**(Guardar). Para obtener información sobre cómo ver qué Cloud App Security centro de datos al que está conectado, consulte [visualización del centro de datos](network-requirements.md#view-your-data-center).

        ![configuración del cuadro Excepto de Box](media/box-settings-except-for.png)

        > [!NOTE]
        > Si es un cliente de Adallom existente y la dirección URL de la consola es para Adallom y no Cloud App Security, use este número de serie de la aplicación: `bwahmilhdlpbqy2ongkl119o3lrkoshc` .

2. En el portal de Cloud App Security, haga clic en **Investigar** y, después, en **Aplicaciones conectadas**.

3. En la página **conectores de aplicaciones** , haga clic en el botón de signo más ( **+** ) y seleccione **Box**.

    ![cuadro conectar](media/connect-box.png "conectar Box")

4. En el elemento emergente **Box settings** (Configuración de Box), haga clic en **Follow this link** (Seguir este vínculo).

5. Se abre la página de inicio de sesión de Box. Escriba sus credenciales para permitir que Cloud App Security tenga acceso a la aplicación de Box de su equipo.

6. Box le pregunta si quiere permitir que Cloud App Security acceda a la información y el registro de actividad de su equipo y que realice actividades como cualquier miembro del equipo. Para continuar, haga clic en **Permitir**.

7. De vuelta en el portal de Cloud App Security, debería recibir un mensaje que indica que Box se ha conectado correctamente.

8. Haga clic en **Probar API** para confirmar que la conexión se ha realizado correctamente.

    La prueba puede tardar unos minutos. Cuando reciba la notificación de que se ha realizado correctamente, haga clic en **Cerrar**.

Box ya está conectado a Cloud App Security.

Después de conectar Box, recibirá eventos de 60 días anteriores a la conexión.

Después de conectar Box, Cloud App Security realiza un examen completo. En función del número de archivos y los usuarios que tenga, el examen podría tardar en completarse. Para habilitar el análisis casi en tiempo real, los archivos en los que se detectan actividades se mueven al principio de la cola de análisis. Por ejemplo, un archivo editado, actualizado o compartido se analiza inmediatamente, en lugar de esperar al proceso de análisis normal. El análisis casi en tiempo real no se aplica a los archivos que no se modifican de forma inherente. Por ejemplo, los archivos que se visualizan, previsualizan, imprimen o exportan se analizan como parte del análisis programado habitual.

Si tiene problemas para conectar la aplicación, consulte [solución de problemas de conectores de aplicaciones](troubleshooting-api-connectors-using-error-messages.md).

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Controlar las aplicaciones en la nube con directivas](control-cloud-apps-with-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]
