---
title: Conectar el cuadro a Cloud App Security
description: En este artículo se proporciona información sobre cómo conectar la aplicación de Box a Cloud App Security mediante el conector de API para la visibilidad y el control del uso.
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
ms.openlocfilehash: 54db3f2b49150e37108fa7d376797df72f23a3d0
ms.sourcegitcommit: be2c558eee71de02ec29632fc58256d49de0f86f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2020
ms.locfileid: "78304867"
---
# <a name="connect-box-to-microsoft-cloud-app-security"></a>Conectar el cuadro a Microsoft Cloud App Security

*Se aplica a: Microsoft Cloud App Security*

En este artículo se proporcionan instrucciones para conectar Microsoft Cloud App Security a su cuenta de Box existente mediante las API del conector de aplicaciones. Esta conexión le proporciona visibilidad y control sobre el uso de Box. Para obtener información sobre cómo Cloud App Security protege el cuadro, consulte [proteger Box](protect-box.md).

## <a name="how-to-connect-box-to-cloud-app-security"></a>Cómo conectar Box a Cloud App Security

> [!NOTE]
> La implementación con una cuenta que no es una cuenta de administrador conduce a un error en la prueba de la API y no permite que Cloud App Security examine todos los archivos de Box. Si se trata de un problema, puede implementar con un coadministrador con todos los privilegios comprobados, pero la prueba de la API seguirá generando un error y no se examinarán los archivos que pertenezcan a otros administradores en Box.

1. Si restringe el acceso de permisos de la aplicación, siga este paso. En caso contrario, vaya al paso 2.

    - En la consola de administración de Box, haga clic en el icono de configuración seguido de configuración **empresarial** o **configuración empresarial**.

         ![configuración empresarial de Box](media/box-business-settings.png "configuración empresarial de Box")

    - Haga clic en la pestaña **aplicaciones** .

         ![aplicaciones de Box](media/box-apps.png "aplicaciones de Box")

    - Si se selecciona **aplicaciones sin publicar** , en el cuadro **de texto excepto para** , agregue el número de serie de la aplicación Cloud App Security:

         |Centro de datos|Microsoft Cloud App Security número de serie|
         |----|----|
         |Estados Unidos 1| `nduj1o3yavu30dii7e03c3n7p49cj2qh`|
         |EE. UU. 2|`w0ouf1apiii9z8o0r6kpr4nu1pvyec75`|
         |US3|`dmcyvu1s9284i2u6gw9r2kb0hhve4a0r`|
         |Unión Europea 1|`me9cm6n7kr4mfz135yt0ab9f5k4ze8qp`|
         |EU2|`uwdy5r40t7jprdlzo85v8suw1l4cdsbf`|

        A continuación, haga clic en **Guardar**. Para obtener información sobre cómo ver qué Cloud App Security centro de datos al que está conectado, consulte [visualización del centro de datos](network-requirements.md#view-your-data-center).

    ![configuración de Box excepto](media/box-settings-except-for.png)

    > [!NOTE]
    > Si es un cliente de Adallom existente y la dirección URL de la consola es para Adallom y no Cloud App Security, use este número de serie de la aplicación: bwahmilhdlpbqy2ongkl119o3lrkoshc.

2. En el portal de Cloud App Security, haga clic en **investigar** y, a continuación, en **aplicaciones conectadas**.

3. En la página **conectores de aplicaciones** , haga clic en el botón de signo más y seleccione **Box**.

    ![cuadro conectar](media/connect-box.png "cuadro conectar")

4. En el menú emergente **configuración de Box** , haga clic en **seguir este vínculo**.

5. Se abre la página de inicio de sesión de Box. Escriba sus credenciales para permitir el acceso Cloud App Security a la aplicación de Box del equipo.

6. Box le pregunta si desea permitir el acceso Cloud App Security a la información del equipo, el registro de actividad y realizar actividades como un miembro del equipo. Para continuar, haga clic en **Permitir**.

7. De vuelta en el portal de Cloud App Security, debería recibir un mensaje que indica que el cuadro se ha conectado correctamente.

8. Haga clic en **Probar API** para confirmar que la conexión se ha realizado correctamente.

    La prueba puede tardar unos minutos. Después de recibir un aviso de éxito, haga clic en **cerrar**.

Box ahora está conectado a Cloud App Security.

Después de conectar el cuadro, recibirá eventos de 60 días antes de la conexión.

Después de conectar el cuadro, Cloud App Security realiza un examen completo. Dependiendo de cuántos archivos y usuarios tenga, completar el examen completo puede tardar unos minutos. Para habilitar el análisis casi en tiempo real, los archivos en los que se detectan actividades se mueven al principio de la cola de examen. Por ejemplo, un archivo editado, actualizado o compartido se analiza inmediatamente en lugar de esperar al proceso de examen normal. El análisis casi en tiempo real no se aplica a los archivos que no se modifican de forma inherente. Por ejemplo, los archivos que se ven, se muestran en la vista previa, se imprimen o exportan se analizan como parte del examen programado periódicamente.

Si tiene problemas para conectar la aplicación, consulte [solución de problemas de conectores de aplicaciones](troubleshooting-api-connectors-using-error-messages.md).

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Controlar las aplicaciones en la nube con directivas](control-cloud-apps-with-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]
