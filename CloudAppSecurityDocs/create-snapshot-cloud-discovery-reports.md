---
title: Creación de informes de instantánea del uso de aplicaciones en la nube de Cloud Discovery
description: En este artículo se proporciona información sobre cómo cargar registros manualmente para crear un informe de instantáneas de las aplicaciones de Cloud Discovery.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 04/07/2019
ms.topic: how-to
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: e458859d0eea99efa6e99c0d1a2f97a50980fe59
ms.sourcegitcommit: a0a8e25bda77fb21f280a0e504896be85b89ed6f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/25/2020
ms.locfileid: "96033538"
---
# <a name="create-snapshot-cloud-discovery-reports"></a>Crear informes de instantáneas de Cloud Discovery

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Es importante cargar un registro manualmente y dejar que Microsoft Cloud App Security lo analice antes de intentar usar el recopilador de registros automáticos. Para información sobre cómo funciona el recopilador de registros y el formato de registro esperado, vea [Uso de registros de tráfico para Cloud Discovery](#log-format).

Si aún no tiene un registro y quiere ver un ejemplo del aspecto de su registro, descargue un archivo de registro de ejemplo. Siga este procedimiento para ver el aspecto que debería tener el registro.

Para crear un informe de instantáneas:

1. Recopile archivos de registro del firewall y el servidor proxy a través de los cuales los usuarios de la organización acceden a Internet. Asegúrese de recopilar registros durante períodos de tráfico pico que sean representativos de toda la actividad de usuario de la organización.

1. En el portal de Cloud App Security, haga clic en **detectar** y, a continuación, haga clic en **crear informe de instantáneas**.

    ![Creación de un informe de instantánea](media/create-new-snapshot-report.png)

1. Escriba un **nombre de informe** y una **Descripción**

    ![Nuevo informe de instantánea](media/new-snapshot-report.png)

1. Seleccione el **origen de datos** desde el que desea cargar los archivos de registro.

1. Compruebe el formato del registro para asegurarse de que es correcto según el registro de ejemplo que puede descargar. Haga clic en **ver y compruebe** , a continuación, en **Descargar registro de ejemplo**. Compare su registro con el ejemplo proporcionado para asegurarse de que es compatible.

    ![Comprobación del formato del registro](media/cloud-discovery-snapshot-verify.png)

    > [!NOTE]
    > Se admite el formato de ejemplo FTP en las instantáneas y en la carga automatizada mientras syslog es compatible únicamente con la carga automatizada. Si se descarga un registro de ejemplo, se descargará un registro de FTP de ejemplo.

1. **Elija los registros de tráfico** que desea cargar. Puede cargar hasta 20 archivos a la vez. También se admiten archivos comprimidos y zip.

1. Haga clic en **Crear**.

1. Una vez finalizada la carga, aparecerá el mensaje de estado en la esquina superior derecha de la pantalla, que informa de que el registro se ha cargado correctamente.

1. Después de cargar los archivos de registro, pasará algún tiempo hasta que se redistribuyan y se analicen.
    Una vez completado el procesamiento de los archivos de registro, recibirá un correo electrónico que le notificará que ya está listo.

1. Aparecerá un banner de notificación en la barra de estado en la parte superior del **panel de Cloud Discovery**. El banner actualiza el estado de procesamiento de los archivos de registro.
    ![barra de menús del archivo de registro de procesamiento](media/processing-log-file-menu-bar.png)

1. Una vez cargados correctamente los registros, verá una notificación informándole de que el procesamiento de los archivos de registro se ha completado correctamente. En este punto, puede ver el informe haciendo clic en el vínculo de la barra de estado, o haciendo clic en el ![icono](media/settings-icon.png "icono de configuración")configuración engranaje de configuración y, después, seleccionando **configuración**.

1. A continuación, en **Cloud Discovery**, seleccione **informes de instantáneas** y seleccione el informe de instantáneas.

    ![administración de informes de instantáneas](media/snapshot-report-managment.png)

## <a name="using-traffic-logs-for-cloud-discovery"></a>Uso de registros de tráfico para Cloud Discovery <a name="log-format"></a>

Cloud Discovery usa los datos de los registros de tráfico. Cuanto más detallado sea el registro, mejor visibilidad se logrará. Cloud Discovery requiere que los datos de tráfico de web tengan los siguientes atributos:

- Fecha de la transacción
- IP de origen
- Usuario de origen: altamente recomendado
- Dirección IP de destino
- Dirección URL de destino: **recomendado** (las direcciones URL proporcionan una mayor precisión para la detección de aplicaciones en la nube que las direcciones IP)
- Cantidad total de datos (la información de datos es muy valiosa)
- Cantidad de datos cargados o descargados (proporciona información sobre los patrones de uso de las aplicaciones en la nube)
- Acción realizada (permitido o bloqueado)

Cloud Discovery no puede mostrar ni analizar los atributos que no estén incluidos en los registros.
Por ejemplo, el formato de registro estándar del **firewall de Cisco ASA** no tiene la **cantidad de bytes cargados por transacción** ni el **nombre de usuario**, y tampoco tiene la **dirección URL de destino** (solo la IP de destino).
Por lo tanto, estos atributos no se mostrarán en los datos de Cloud Discovery de estos registros, y la visibilidad de las aplicaciones en la nube será limitada. En el caso de los firewalls de Cisco ASA, es necesario establecer el nivel de información en 6.

Para generar correctamente un informe de Cloud Discovery, los registros de tráfico deben cumplir las condiciones siguientes:

1. [Se admite el origen de datos](set-up-cloud-discovery.md#supported-firewalls-and-proxies).
2. El formato de registro coincide con el formato estándar esperado (el formato se comprueba después de la carga mediante la herramienta de registro).
3. Los eventos no tienen más de 90 días.
4. El archivo de registro es válido e incluye información sobre el tráfico de salida.

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Controlar las aplicaciones en la nube con directivas](control-cloud-apps-with-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]
