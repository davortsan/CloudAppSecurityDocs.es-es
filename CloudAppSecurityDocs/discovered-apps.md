---
title: Trabajo con aplicaciones detectadas en Cloud App Security
description: En este artículo se describe el proceso de identificación y corrección de aplicaciones de riesgo de Cloud Discovery en Cloud App Security.
ms.date: 09/25/2019
ms.topic: conceptual
ms.openlocfilehash: 72cc84a98f61649ba7b1f15251e001a372d3a56b
ms.sourcegitcommit: 7fc4d916a43d188b1aa4e3cee2e8bd1de230d135
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/14/2021
ms.locfileid: "98206464"
---
# <a name="working-with-discovered-apps"></a>Trabajar con aplicaciones detectadas

[!INCLUDE [Banner for top of topics](includes/banner.md)]

El panel de Cloud Discovery está diseñado para proporcionar más información sobre cómo se usan las aplicaciones en la nube en la organización. Proporciona una visión general de un vistazo sobre los tipos de aplicaciones que se usan, las alertas abiertas y los niveles de riesgo de las aplicaciones de la organización. También muestra quiénes son los usuarios que más usan las aplicaciones y proporciona un mapa de ubicación de la sede central de la aplicación. El panel de Cloud Discovery tiene muchas opciones para filtrar los datos. Con el filtrado se pueden generar vistas específicas en función de lo que más le interese y gráficos fáciles de entender para que se haga una idea general de un vistazo.

![panel de Cloud Discovery](media/cloud-discovery-dashboard.png)

## <a name="review-the-cloud-discovery-dashboard"></a>Revisar el panel de Cloud Discovery

Lo primero que debe hacer para obtener una visión general de sus aplicaciones de Cloud Discovery es ir al panel de Cloud Discovery y revisar esta información:

1. Primero, vea el uso general de aplicaciones en la nube de la organización en la **información general sobre el uso de alto nivel**.

1. Después, profundice un nivel para ver cuáles son las **categorías que más se usan** en la organización para cada uno de los diferentes parámetros de uso. Puede ver qué porcentaje de este uso lo realizan las aplicaciones autorizadas.

1. Profundice todavía más y vea todas las aplicaciones de una categoría específica en la pestaña **Aplicaciones detectadas**.

1. Puede ver los **principales usuarios y las direcciones IP de origen** para identificar los usuarios predominantes de aplicaciones en la nube de la organización.
1. Compruebe cómo se extienden las aplicaciones detectadas según la ubicación geográfica (de acuerdo con su sede central) en el **mapa de la sede central de la aplicación**.

1. Por último, no olvide revisar la puntuación de riesgo de la aplicación detectada en la **información general sobre el riesgo** de la aplicación. Compruebe el **estado de alertas de detección** para ver cuántas alertas abiertas se deben investigar.

## <a name="deep-dive-into-discovered-apps"></a>Análisis detallado de las aplicaciones detectadas

Si quiere profundizar en los datos proporcionados por Cloud Discovery, use los filtros para revisar qué aplicaciones entrañan riesgos y cuáles se usan habitualmente.

Por ejemplo, si quiere identificar las aplicaciones de colaboración y de almacenamiento en la nube que entrañan riesgos y que se usan habitualmente, puede usar la página Aplicaciones detectadas para filtrar las aplicaciones que quiera. Después, puede [no autorizarlas o bloquearlas](governance-discovery.md), como se indica aquí:

1. En la página **Aplicaciones detectadas**, en **Buscar por categoría**, seleccione **Almacenamiento en la nube** y **Colaboración**.

1. Luego use los filtros avanzados y establezca **Factor de riesgo de cumplimiento** en **SOC 2** igual a **False**

1. Para **Uso**, establezca **Usuarios** en más de 50 usuarios y **Uso** para **Transacciones** en más de 100.

1. Establezca el **Factor de riesgo para la seguridad** para **Data at rest encryption** (Cifrado de datos en reposo) igual a **No admitido**. Después, establezca **Puntuación de riesgo** en un valor igual o menor que 6.

![Filtros de aplicaciones detectadas](media/discovered-app-filters.png)

Una vez que se han filtrado los resultados, puede [no autorizar y bloquear](governance-discovery.md) las aplicaciones. Para ello, active la casilla de acción masiva para no autorizarlas en una sola acción. Después de no autorizarlas, puede usar un script de bloqueo para impedir que se usen en su entorno.

Cloud Discovery le permite profundizar incluso más en el uso de la nube de su organización. Puede identificar instancias específicas que se están usando al investigar los subdominios detectados.

Por ejemplo, puede diferenciar entre los distintos sitios de SharePoint.

Esto solo se admite en los firewalls y servidores proxy que contienen datos de dirección URL de destino. Para obtener más información, vea la lista de dispositivos compatibles en [Firewalls y servidores proxy compatibles](set-up-cloud-discovery.md#supported-firewalls-and-proxies).

![información de subdominio](media/discovery-domains.png)

## <a name="discover-resources-and-custom-apps"></a>Detección de recursos y aplicaciones personalizadas

Cloud Discovery también le permite sumergirse en sus recursos IaaS y PaaS. Puede detectar actividad entre plataformas en las que hospede recursos y consultar el acceso a los datos en aplicaciones y recursos autohospedados, como es el caso de las cuentas de almacenamiento, la infraestructura y las aplicaciones personalizadas hospedadas en Azure, Google Cloud Platform y AWS. No solo puede conocer el uso general de sus soluciones IaaS, sino también obtener visibilidad sobre recursos específicos hospedados en ellas y datos sobre el uso general de estos para mitigar el riesgo individual de cada recurso.

Por ejemplo, desde Cloud App Security puede supervisar la actividad en un contexto en el que el volumen de datos es muy grande, así como detectar en qué recurso se efectúa la carga y realizar una exploración en profundidad para conocer el autor de la actividad.

> [!NOTE]
> Esto solo se admite en los firewalls y servidores proxy que contienen datos de dirección URL de destino. Para obtener más información, vea la lista de dispositivos compatibles en [Firewalls y servidores proxy compatibles](set-up-cloud-discovery.md#supported-firewalls-and-proxies).

Para consultar los recursos detectados:

1. En el portal de Cloud App Security, seleccione **Detectar** y, luego, **Recursos detectados**.

    ![Menú de recursos detectados](media/discovered-resources-menu.png)

1. En la página Recursos detectados, puede explorar en profundidad cada recurso y consultar los tipos de interacciones que han tenido lugar y los usuarios que han accedo a ellos. A partir de aquí, continuar con la exploración en profundidad para obtener más información concreta sobre los usuarios.

   ![Recursos de la detección](media/discovery-resources.png)

1. Para las aplicaciones personalizadas, puede hacer clic en los tres botones que verá al final de la fila y seleccionar **Agregar aplicación personalizada**. Esta acción abrirá la ventana **Agregar aplicación personalizada**, donde podrá asignar un nombre a la aplicación e identificarla para poder incluirla en el panel de Cloud Discovery.

## <a name="generate-cloud-discovery-executive-report"></a>Generación de un informe ejecutivo de Cloud Discovery

La mejor manera de obtener información general sobre el uso de Shadow IT en la organización es generar un informe ejecutivo de Cloud Discovery. Este informe permite identificar los principales riesgos posibles y agiliza el planeamiento de un flujo de trabajo para mitigarlos y administrarlos hasta que se resuelvan.

Para generar un informe ejecutivo de Cloud Discovery:

1. En el **Panel de Cloud Discovery**, haga clic en los tres puntos situados en la esquina superior derecha del panel y, a continuación, seleccione **generar Cloud Discovery Informe Ejecutivo**.
1. Opcionalmente, cambie el nombre del informe.
1. Haga clic en **Generar**.

## <a name="exclude-entities"></a>Excluir entidades

Si tiene usuarios del sistema, direcciones IP o dispositivos que son ruidosos pero no interesantes o aplicaciones que no son relevantes, puede que desee excluir sus datos de los Cloud Discovery datos que se analizan. Por ejemplo, puede excluir toda la información que se origina en 127.0.0.1 o el host local.

Para crear una exclusión:

1. En el portal, en el icono de configuración, seleccione **Configuración de Cloud Discovery**.

1. Haga clic en la pestaña **Excluir entidades**.

1. Elija la pestaña **usuarios excluidos**, **direcciones IP excluidas** o **dispositivos excluidos** y haga clic en el botón + para agregar su exclusión.

1. Agregue un alias de usuario, una dirección IP o un nombre de dispositivo. Se recomienda agregar información sobre por qué se ha realizado la exclusión.

    ![excluir usuario](media/exclude-user.png "excluir usuario")

## <a name="manage-continuous-reports"></a>Administrar informes continuos

Los informes continuos personalizados proporcionan más granularidad al supervisar los datos de registro de Cloud Discovery de la organización. Al crear informes personalizados, es posible filtrar por ubicaciones geográficas concretas, redes y sitios o unidades organizativas. De forma predeterminada, solo aparecen los informes siguientes en el selector de informes de Cloud Discovery:

- El **informe global** consolida toda la información del portal de todos los orígenes de datos incluidos en los registros.  El informe global no incluye datos de Microsoft defender para el punto de conexión.

- El **informe específico de origen de datos** muestra únicamente la información de un origen de datos concreto.

Para crear un informe continuo:

1. En el portal, en el icono de configuración, seleccione **Configuración de Cloud Discovery**.

1. Haga clic en la pestaña **Informe continuo**.

1. Haga clic en el botón **Crear informe**.

1. Escriba un nombre de informe.

1. Seleccione los orígenes de datos que quiere incluir (todos u orígenes específicos).

1. Establezca los filtros que quiera sobre los datos. Estos filtros pueden ser **Grupos de usuarios**, **Etiquetas de dirección IP** o **Intervalos de direcciones IP**. Para obtener más información sobre el trabajo con etiquetas de dirección IP e intervalos de direcciones IP, consulte [Organize the data according to your needs](ip-tags.md) (Organizar los datos de acuerdo a las necesidades).

    ![crear informe continuo personalizado](media/create-custom-continuous-report.png)

> [!NOTE]
> Todos los informes personalizados se limitan a un máximo de 1 GB de datos sin comprimir. Si hay más de 1 GB de datos, se exportará el primer GB de datos en el informe.

## <a name="deleting-cloud-discovery-data"></a>Eliminar datos de Cloud Discovery

Hay una serie de razones por las que puede que quiera eliminar los datos de Cloud Discovery. Se recomienda eliminarlos en los casos siguientes:

- Si cargó manualmente archivos de registro y ha pasado mucho tiempo desde que actualizó el sistema con nuevos archivos de registro y no quiere que los datos antiguos afecten a los resultados.

- Cuando se establece una nueva vista de datos personalizada, solo se aplica a los nuevos datos a partir de ese momento. Por eso, es posible que quiera borrar los datos antiguos y luego volver a cargar los archivos de registro para permitir que la vista de datos personalizada tome los eventos de los datos del archivo de registro.

- Si hay muchos usuarios o direcciones IP que hayan vuelto a trabajar recientemente después de estar sin conexión durante algún tiempo, su actividad se identificará como anómala y es posible que obtenga muchas infracciones positivas falsas.

Para eliminar datos de Cloud Discovery:

1. En el portal, en el icono de configuración, seleccione **Configuración de Cloud Discovery**.

1. Haga clic en la pestaña **Eliminar datos**.

    Es importante estar seguro de querer eliminar los datos antes de continuar: esta acción no se puede deshacer y elimina **todos** los datos de Cloud Discovery del sistema.

1. Haga clic en el botón **Eliminar**.

    ![eliminar datos](media/delete-data.png "eliminar datos")

    > [!NOTE]
    > El proceso de eliminación tarda unos minutos y no es inmediato.

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Crear informes de instantáneas de Cloud Discovery](create-snapshot-cloud-discovery-reports.md)

> [!div class="nextstepaction"]
> [Configurar la carga de registros automática para informes continuos](configure-automatic-log-upload-for-continuous-reports.md)

> [!div class="nextstepaction"]
> [Trabajo con datos de Cloud Discovery](working-with-cloud-discovery-data.md)
