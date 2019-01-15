---
title: Trabajo con aplicaciones detectadas en Cloud App Security
description: Este inicio rápido describe el proceso de identificación y corrección de aplicaciones de riesgo de Cloud Discovery en Cloud App Security.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 1/10/2019
ms.topic: quickstart
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 645fd8c7-06d0-4f93-a85c-2976e7b3766d
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 589f0d11d7fac47a4080926f6aa4f654c17deb34
ms.sourcegitcommit: 076705cc9684fe5fb35c33a51e3319ba2ccfd24e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/07/2019
ms.locfileid: "54060180"
---
# <a name="quickstart-work-with-discovered-apps"></a>Inicio rápido: Trabajo con aplicaciones detectadas

*Se aplica a: Microsoft Cloud App Security*

Este inicio rápido proporciona información introductoria sobre la supervisión y la administración de las aplicaciones detectadas. El panel de Cloud Discovery está diseñado para proporcionar más información sobre cómo se usan las aplicaciones en la nube en la organización. Proporciona una visión general de un vistazo sobre los tipos de aplicaciones que se usan, las alertas abiertas y los niveles de riesgo de las aplicaciones de la organización. También muestra quiénes son los usuarios que más usan las aplicaciones y proporciona un mapa de ubicación de la sede central de la aplicación. El panel de Cloud Discovery tiene muchas opciones para filtrar los datos. Con el filtrado se pueden generar vistas específicas en función de lo que más le interese y gráficos fáciles de entender para que se haga una idea general de un vistazo.

![panel de Cloud Discovery](./media/cloud-discovery-dashboard.png)

## <a name="review-the-cloud-discovery-dashboard"></a>Revisar el panel de Cloud Discovery

Lo primero que debe hacer para obtener una visión general de sus aplicaciones de Cloud Discovery es ir al panel de Cloud Discovery y revisar esta información:
 
1. Primero, vea el uso general de aplicaciones en la nube de la organización en la **información general sobre el uso de alto nivel**.

2. Después, profundice un nivel para ver cuáles son las **categorías que más se usan** en la organización para cada uno de los diferentes parámetros de uso. Puede ver qué porcentaje de este uso lo realizan las aplicaciones autorizadas.

3. Profundice todavía más y vea todas las aplicaciones de una categoría específica en la pestaña **Aplicaciones detectadas**.

4. Puede ver los **principales usuarios y las direcciones IP de origen** para identificar los usuarios predominantes de aplicaciones en la nube de la organización.
5. Compruebe cómo se extienden las aplicaciones detectadas según la ubicación geográfica (de acuerdo con su sede central) en el **mapa de la sede central de la aplicación**.

6. Por último, no olvide revisar la puntuación de riesgo de la aplicación detectada en el **App risk overview** (Información general sobre el riesgo de la aplicación). Compruebe el **estado de alertas de detección** para ver cuántas alertas abiertas se deben investigar.

## <a name="deep-dive-into-discovered-apps"></a>Análisis detallado de las aplicaciones detectadas

Si quiere profundizar en los datos proporcionados por Cloud Discovery, use los filtros para revisar qué aplicaciones entrañan riesgos y cuáles se usan habitualmente.


Por ejemplo, si quiere identificar las aplicaciones de colaboración y de almacenamiento en la nube que entrañan riesgos y que se usan habitualmente, puede usar la página Aplicaciones detectadas para filtrar las aplicaciones que quiera. Después, puede [no autorizarlas o bloquearlas](governance-discovery.md), como se indica aquí:

1. En la página **Aplicaciones detectadas**, en **Buscar por categoría**, seleccione **Almacenamiento en la nube** y **Colaboración**.
2. Luego use los filtros avanzados y establezca **Factor de riesgo de cumplimiento** en **SOC 2** igual a **False**
3. Para **Uso**, establezca **Usuarios** en más de 50 usuarios y **Uso** para **Transacciones** en más de 100.
4. Establezca el **Factor de riesgo para la seguridad** para **Data at rest encryption** (Cifrado de datos en reposo) igual a **No admitido**. Después, establezca **Puntuación de riesgo** en un valor igual o menor que 6.

![Filtros de aplicaciones detectadas](./media/discovered-app-filters.png)

Una vez que se han filtrado los resultados, puede [no autorizar y bloquear](governance-discovery.md) las aplicaciones. Para ello, active la casilla de acción masiva para no autorizarlas en una sola acción. Después de no autorizarlas, puede usar un script de bloqueo para impedir que se usen en su entorno.

Cloud Discovery permite profundizar incluso más en el uso de la nube de la organización. Puede identificar instancias específicas que se están usando al investigar los subdominios detectados.
     
Por ejemplo, puede diferenciar entre los distintos sitios de SharePoint.

Esto solo se admite en los firewalls y servidores proxy que contienen datos de dirección URL de destino. Para obtener más información, vea la lista de dispositivos compatibles en [Firewalls y servidores proxy compatibles](create-snapshot-cloud-discovery-reports.md#supported-firewalls-and-proxies).

 ![información de subdominio](./media/discovery-domains.png) 

## <a name="generate-cloud-discovery-executive-report"></a>Generación de un informe ejecutivo de Cloud Discovery

La mejor manera de obtener información general sobre el uso de Shadow IT en la organización es generar un informe ejecutivo de Cloud Discovery. Este informe permite identificar los principales riesgos posibles y agiliza el planeamiento de un flujo de trabajo para mitigarlos y administrarlos hasta que se resuelvan.

Para generar un informe ejecutivo de Cloud Discovery: 

En el **panel de Cloud Discovery**, haga clic en los puntos suspensivos que encontrará en la esquina superior derecha del menú y seleccione **Generar informe ejecutivo de Cloud Discovery**.

## <a name="exclude-entities"></a>Excluir entidades

Si tiene usuarios del sistema, direcciones IP o máquinas que son ruidosos y no interesantes, o aplicaciones que no son relevantes, es posible que quiera excluir sus datos de los datos de Cloud Discovery que se analizan. Por ejemplo, puede excluir toda la información que se origina en 127.0.0.1 o el host local.  
  
Para crear una exclusión:  
  
1. En el portal, en el icono de configuración, seleccione **Configuración de Cloud Discovery**.  
2. Haga clic en la pestaña **Excluir entidades**.  
3. Seleccione la pestaña **Usuarios excluidos**, **Direcciones IP excluidas** o **Máquinas excluidas** y haga clic en el botón + para agregar la exclusión.
4. Agregue un alias de usuario, una dirección IP o un nombre de máquina. Se recomienda agregar información sobre por qué se ha realizado la exclusión.
  
     ![Excluir usuario](./media/exclude-user.png "excluir usuario")  
  
## <a name="manage-continuous-reports"></a>Administrar informes continuos

Los informes continuos personalizados proporcionan más granularidad al supervisar los datos de registro de Cloud Discovery de la organización. Al crear informes personalizados, es posible filtrar por ubicaciones geográficas concretas, redes y sitios o unidades organizativas. De forma predeterminada, solo aparecen los informes siguientes en el selector de informes de Cloud Discovery:  
  
- El **informe global** consolida toda la información del portal de todos los orígenes de datos incluidos en los registros.  
  
- El **informe específico de origen de datos** muestra únicamente la información de un origen de datos concreto.  
  
Para crear un informe continuo:  
  
1. En el portal, en el icono de configuración, seleccione **Configuración de Cloud Discovery**.  
  
2. Haga clic en la pestaña **Informe continuo**.  
  
3. Haga clic en el botón **Crear informe**.  
  
4. Escriba un nombre de informe.  
  
5. Seleccione los orígenes de datos que quiere incluir (todos u orígenes específicos).  
  
6. Establezca los filtros que quiera sobre los datos. Estos filtros pueden ser **Grupos de usuarios**, **Etiquetas de dirección IP** o **Intervalos de direcciones IP**. Para obtener más información sobre el trabajo con etiquetas de dirección IP e intervalos de direcciones IP, consulte [Organize the data according to your needs](ip-tags.md) (Organizar los datos de acuerdo a las necesidades).  
  
    ![crear informe continuo personalizado](./media/create-custom-continuous-report.png) 

> [!NOTE]
> Todos los informes personalizados se limitan a un máximo de 1 GB de datos sin comprimir. Si hay más de 1 GB de datos, se exportará el primer GB de datos en el informe.


## <a name="deleting-cloud-discovery-data"></a>Eliminar datos de Cloud Discovery

Hay una serie de razones por las que puede que quiera eliminar los datos de Cloud Discovery. Se recomienda eliminarlos en los casos siguientes:  
  
- Si cargó manualmente archivos de registro y ha pasado mucho tiempo desde que actualizó el sistema con nuevos archivos de registro y no quiere que los datos antiguos afecten a los resultados.  
  
- Cuando se establece una nueva vista de datos personalizada, solo se aplica a los nuevos datos a partir de ese momento. Por eso, es posible que quiera borrar los datos antiguos y luego volver a cargar los archivos de registro para permitir que la vista de datos personalizada tome los eventos de los datos del archivo de registro.  
  
- Si hay muchos usuarios o direcciones IP que hayan vuelto a trabajar recientemente después de estar sin conexión durante algún tiempo, su actividad se identificará como anómala y es posible que obtenga muchas infracciones positivas falsas.  
  
Para eliminar datos de Cloud Discovery:  
  
1. En el portal, en el icono de configuración, seleccione **Configuración de Cloud Discovery**.  
  
2. Haga clic en la pestaña **Eliminar datos**.  
  
    Es importante estar seguro de querer eliminar los datos antes de continuar: esta acción no se puede deshacer y elimina **todos** los datos de Cloud Discovery del sistema.  
  
3. Haga clic en el botón **Eliminar**.  
  
    ![eliminar datos](./media/delete-data.png "eliminar datos")  
  
   > [!NOTE]  
   >  El proceso de eliminación tarda unos minutos y no es inmediato.

## <a name="next-steps"></a>Pasos siguientes
 
[Crear informes de instantáneas de Cloud Discovery](create-snapshot-cloud-discovery-reports.md)

[Configurar la carga de registros automática para informes continuos](configure-automatic-log-upload-for-continuous-reports.md)

[Trabajar con datos de Cloud Discovery](working-with-cloud-discovery-data.md)

