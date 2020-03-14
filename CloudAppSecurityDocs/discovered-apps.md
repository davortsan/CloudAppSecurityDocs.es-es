---
title: Trabajar con aplicaciones detectadas en Cloud App Security
description: En este artículo se describe el proceso de identificación y corrección de aplicaciones de riesgo de Cloud Discovery en Cloud App Security.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 09/25/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: a63546a3404cdf4c48a56b800f5d80d09ee5971e
ms.sourcegitcommit: 4f3883a9e85d0aaf2802b10433b221c3f1838d88
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/13/2020
ms.locfileid: "79285479"
---
# <a name="working-with-discovered-apps"></a>Trabajar con aplicaciones detectadas

*Se aplica a: Microsoft Cloud App Security*

El panel de Cloud Discovery está diseñado para proporcionar más información sobre cómo se usan las aplicaciones en la nube en la organización. Proporciona una visión general de un vistazo sobre los tipos de aplicaciones que se usan, las alertas abiertas y los niveles de riesgo de las aplicaciones de la organización. También muestra quiénes son los usuarios que más usan las aplicaciones y proporciona un mapa de ubicación de la sede central de la aplicación. El panel de Cloud Discovery tiene muchas opciones para filtrar los datos. El filtrado le permite generar vistas específicas en función de lo que más le interese usar gráficos fáciles de entender para proporcionarle la imagen completa de un vistazo.

![panel de Cloud Discovery](media/cloud-discovery-dashboard.png)

## <a name="review-the-cloud-discovery-dashboard"></a>Revisar el panel de Cloud Discovery

Lo primero que debe hacer para obtener una visión general de las aplicaciones Cloud Discovery es revisar la información siguiente en el panel de Cloud Discovery:

1. En primer lugar, consulte el uso general de aplicaciones en la nube en su organización en la **información general sobre el uso de alto nivel**.

1. Después, profundice un nivel para ver cuáles son las **categorías principales** que se usan en la organización para cada uno de los diferentes parámetros de uso. Puede ver qué cantidad de este uso se debe a las aplicaciones autorizadas.

1. Vaya aún más a fondo y vea todas las aplicaciones de una categoría específica en la pestaña **aplicaciones detectadas** .

1. Puede ver los **principales usuarios y las direcciones IP de origen** para identificar los usuarios predominantes de aplicaciones en la nube de la organización.
1. Compruebe cómo se extienden las aplicaciones detectadas según la ubicación geográfica (de acuerdo con su sede central) en el **mapa de la sede central de la aplicación**.

1. Por último, no olvide revisar la puntuación de riesgo de la aplicación detectada en la **información general sobre el riesgo**de la aplicación. Compruebe el **Estado** de las alertas de detección para ver cuántas alertas abiertas debe investigar.

## <a name="deep-dive-into-discovered-apps"></a>Análisis detallado de las aplicaciones detectadas

Si desea profundizar en los datos Cloud Discovery proporciona, use los filtros para revisar qué aplicaciones son arriesgadas y cuáles se usan habitualmente.

Por ejemplo, si quiere identificar las aplicaciones de colaboración y de almacenamiento en la nube que entrañan riesgos y que se usan habitualmente, puede usar la página Aplicaciones detectadas para filtrar las aplicaciones que quiera. Después, puede no [autorizarlas o bloquearlas](governance-discovery.md) de la manera siguiente:

1. En la página **Aplicaciones detectadas**, en **Buscar por categoría**, seleccione **Almacenamiento en la nube** y **Colaboración**.

1. A continuación, use los filtros avanzados y establezca el **factor de riesgo de cumplimiento** en **SOC 2** es igual a **false** .

1. Para el **uso**, establezca **los usuarios** en más de 50 usuarios y el **uso** de **las transacciones** en un valor superior a 100.

1. Establecer el **factor de riesgo de seguridad** para los **datos en el cifrado de REST** no es **compatible**. A continuación, establezca la **puntuación de riesgo** es igual a 6 o inferior.

![Filtros de aplicaciones detectadas](media/discovered-app-filters.png)

Una vez que se han filtrado los resultados, puede [no autorizar y bloquear](governance-discovery.md) las aplicaciones. Para ello, active la casilla de acción masiva para no autorizarlas en una sola acción. Una vez no autorizadas, puede usar un script de bloqueo para impedir que se usen en su entorno.

Cloud Discovery le permite profundizar incluso más en el uso de la nube de su organización. Puede identificar instancias específicas que están en uso mediante la investigación de los subdominios detectados.

Por ejemplo, puede diferenciar entre diferentes sitios de SharePoint.

Esto solo se admite en firewalls y servidores proxy que contienen datos de la dirección URL de destino. Para obtener más información, consulte la lista de dispositivos compatibles en [firewalls y servidores proxy compatibles](set-up-cloud-discovery.md#supported-firewalls-and-proxies).

![información de subdominio](media/discovery-domains.png)

## <a name="discover-resources-and-custom-apps"></a>Detección de recursos y aplicaciones personalizadas

Cloud Discovery también le permite sumergirse en sus recursos IaaS y PaaS. Puede detectar actividad entre plataformas en las que hospede recursos y consultar el acceso a los datos en aplicaciones y recursos autohospedados, como es el caso de las cuentas de almacenamiento, la infraestructura y las aplicaciones personalizadas hospedadas en Azure, Google Cloud Platform y AWS. No solo puede conocer el uso general de sus soluciones IaaS, sino también obtener visibilidad sobre recursos específicos hospedados en ellas y datos sobre el uso general de estos para mitigar el riesgo individual de cada recurso.

Por ejemplo, desde Cloud App Security puede supervisar la actividad en un contexto en el que el volumen de datos es muy grande, así como detectar en qué recurso se efectúa la carga y realizar una exploración en profundidad para conocer el autor de la actividad.

> [!NOTE]
> Esto solo se admite en firewalls y servidores proxy que contienen datos de la dirección URL de destino. Para obtener más información, consulte la lista de dispositivos compatibles en [firewalls y servidores proxy compatibles](set-up-cloud-discovery.md#supported-firewalls-and-proxies).

Para consultar los recursos detectados:

1. En el portal de Cloud App Security, seleccione **Detectar** y, luego, **Recursos detectados**.

    ![Menú de recursos detectados](media/discovered-resources-menu.png)

1. En la página Recursos detectados, puede explorar en profundidad cada recurso y consultar los tipos de interacciones que han tenido lugar y los usuarios que han accedo a ellos. A partir de aquí, continuar con la exploración en profundidad para obtener más información concreta sobre los usuarios.

   ![Recursos de la detección](media/discovery-resources.png)

1. Para las aplicaciones personalizadas, puede hacer clic en los tres botones que verá al final de la fila y seleccionar **Agregar aplicación personalizada**. Esta acción abrirá la ventana **Agregar aplicación personalizada**, donde podrá asignar un nombre a la aplicación e identificarla para poder incluirla en el panel de Cloud Discovery.

## <a name="generate-cloud-discovery-executive-report"></a>Generar Cloud Discovery Informe Ejecutivo

La mejor manera de obtener información general sobre el uso de instantáneas en toda la organización es mediante la generación de una Cloud Discovery Informe Ejecutivo. Este informe identifica los principales riesgos potenciales y ayuda a planear un flujo de trabajo para mitigar y administrar los riesgos hasta que se resuelvan.

Para generar una Cloud Discovery informe ejecutivo:

1. En el **Panel de Cloud Discovery**, haga clic en los tres puntos situados en la esquina superior derecha del panel y, a continuación, seleccione **generar Cloud Discovery Informe Ejecutivo**.
1. Opcionalmente, cambie el nombre del informe.
1. Haga clic en **Generar**.

## <a name="exclude-entities"></a>Excluir entidades

Si tiene usuarios del sistema, direcciones IP o máquinas que son ruidosos pero no interesantes o aplicaciones que no son relevantes, puede que desee excluir sus datos de los Cloud Discovery datos que se analizan. Por ejemplo, puede excluir toda la información que se origina en 127.0.0.1 o el host local.

Para crear una exclusión:

1. En el portal, en el icono de configuración, seleccione **Configuración de Cloud Discovery**.

1. Haga clic en la pestaña **Excluir entidades**.

1. Elija la pestaña **usuarios excluidos**, **direcciones IP excluidas**o **máquinas excluidas** y haga clic en el botón + para agregar su exclusión.

1. Agregue un alias de usuario, una dirección IP o un nombre de equipo. Se recomienda agregar información sobre por qué se realizó la exclusión.

    ![excluir usuario](media/exclude-user.png "excluir usuario")

## <a name="manage-continuous-reports"></a>Administrar informes continuos

Los informes continuos personalizados proporcionan más granularidad al supervisar los datos de registro de Cloud Discovery de la organización. Al crear informes personalizados, es posible filtrar por ubicaciones geográficas, redes y sitios específicos, o unidades organizativas. De forma predeterminada, solo aparecen los informes siguientes en el selector de informes de Cloud Discovery:

- El **informe global** consolida toda la información del portal de todos los orígenes de datos incluidos en los registros.  El informe global no incluye datos de Microsoft Defender ATP.

- El **informe específico de origen de datos** muestra únicamente la información de un origen de datos concreto.

Para crear un informe continuo:

1. En el portal, en el icono de configuración, seleccione **Configuración de Cloud Discovery**.

1. Haga clic en la pestaña **Informe continuo** .

1. Haga clic en el botón **Crear informe**.

1. Escriba un nombre de informe.

1. Seleccione los orígenes de datos que quiere incluir (todos u orígenes específicos).

1. Establezca los filtros que desee en los datos. Estos filtros pueden ser **grupos de usuarios**, **etiquetas de dirección IP**o **intervalos de direcciones IP**. Para obtener más información sobre el trabajo con etiquetas de dirección IP e intervalos de direcciones IP, consulte [Organize the data according to your needs](ip-tags.md) (Organizar los datos de acuerdo a las necesidades).

    ![crear informe continuo personalizado](media/create-custom-continuous-report.png)

> [!NOTE]
> Todos los informes personalizados están limitados a un máximo de 1 GB de datos sin comprimir. Si hay más de 1 GB de datos, los primeros 1 GB de datos se exportarán en el informe.

## <a name="deleting-cloud-discovery-data"></a>Eliminar datos de Cloud Discovery

Hay una serie de razones por las que puede que quiera eliminar los datos de Cloud Discovery. Se recomienda eliminarlos en los casos siguientes:

- Si cargó manualmente archivos de registro y ha pasado mucho tiempo desde que actualizó el sistema con nuevos archivos de registro y no quiere que los datos antiguos afecten a los resultados.

- Cuando se establece una nueva vista de datos personalizada, solo se aplica a los nuevos datos desde ese punto hacia delante. Por lo tanto, puede que quiera borrar los datos antiguos y luego volver a cargar los archivos de registro para permitir que la vista de datos personalizada seleccione eventos en los datos del archivo de registro.

- Si muchos usuarios o direcciones IP empezaron a trabajar recientemente después de estar sin conexión durante algún tiempo, su actividad se identificará como anómala y puede proporcionarle infracciones de falsos positivos.

Para eliminar datos de Cloud Discovery:

1. En el portal, en el icono de configuración, seleccione **Configuración de Cloud Discovery**.

1. Haga clic en la pestaña **Eliminar datos**.

    Es importante asegurarse de que desea eliminar los datos antes de continuar, ya que no se puede deshacer y elimina **todos los** Cloud Discovery datos del sistema.

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
> [Trabajar con datos de Cloud Discovery](working-with-cloud-discovery-data.md)
