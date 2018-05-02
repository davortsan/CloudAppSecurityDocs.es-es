---
title: Trabajar con aplicaciones detectadas en Cloud App Security | Microsoft Docs
description: En este tema se describe el proceso de identificación y corrección de aplicaciones de riesgo de Cloud Discovery en Cloud App Security.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 4/22/2018
ms.topic: get-started-article
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 645fd8c7-06d0-4f93-a85c-2976e7b3766d
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: abec8d49559c7ff29476a5a5291f1920db877b88
ms.sourcegitcommit: 45311f2cafef79483e40d971a4c61c7673834d96
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2018
---
*Se aplica a: Microsoft Cloud App Security*


# <a name="working-with-discovered-apps"></a>Trabajar con aplicaciones detectadas

## <a name="review-the-cloud-discovery-dashboard"></a>Revisar el panel de Cloud Discovery

El panel de Cloud Discovery está diseñado para proporcionar más información sobre cómo se usan las aplicaciones en la nube en la organización. Proporciona una visión general de un vistazo sobre los tipos de aplicaciones que se usan, las alertas abiertas y los niveles de riesgo de las aplicaciones de la organización. También muestra quiénes son los usuarios que más usan las aplicaciones y proporciona un mapa de ubicación de la sede central de la aplicación. El panel de Cloud Discovery tiene numerosas opciones para filtrar los datos, de modo que pueda generar vistas específicas en función de lo que más le interese y gráficos fáciles de entender para que se haga una idea general de un vistazo.

![panel de Cloud Discovery](./media/cloud-discovery-dashboard.png)

Lo primero que debe hacer para obtener una visión general de sus aplicaciones de Cloud Discovery es ir al panel de Cloud Discovery y revisar lo siguiente:
 
1. Primero, consulte el uso general de aplicaciones en la nube de la organización en la **información general sobre el uso de alto nivel**.

2. Después, profundice un nivel para ver cuáles son las **categorías que más se usan** en la organización para cada uno de los diferentes parámetros de uso y qué porcentaje de este uso se debe a aplicaciones autorizadas.

3. Profundice todavía más y vea todas las aplicaciones de una categoría específica en el widget de **aplicaciones detectadas**.

4. Puede ver los **principales usuarios y las direcciones IP de origen** para identificar los usuarios predominantes de aplicaciones en la nube de la organización.
5. Compruebe cómo se extienden las aplicaciones detectadas según la ubicación geográfica (de acuerdo con su sede central) en el **mapa de la sede central de la aplicación**.

6. Por último, no olvide revisar la puntuación de riesgo de la aplicación detectada en la **información general sobre el riesgo de las aplicaciones** y comprobar el **estado de las alertas de detección** para ver cuántas alertas abiertas debe investigar.

## <a name="deep-dive-into-discovered-apps"></a>Análisis detallado de las aplicaciones detectadas
Si quiere profundizar en los datos proporcionados por Cloud Discovery, use los filtros para revisar qué aplicaciones entrañan riesgos y cuáles se usan habitualmente.


Por ejemplo, si quiere identificar las aplicaciones de colaboración y de almacenamiento en la nube que entrañan riesgos y que se usan habitualmente, puede usar la página Aplicaciones detectadas para filtrar las aplicaciones que quiera. Después, puede [no autorizarlas o bloquearlas](governance-discovery.md), como se indica a continuación:

En la página **Aplicaciones detectadas**, en **Buscar por categoría**, seleccione **Almacenamiento en la nube** y **Colaboración**. Después, use los filtros avanzados y establezca **Factor de riesgo de cumplimiento** en **SOC 2** igual a **False**; **Uso** > **Usuarios** en mayor que 50 usuarios; **Uso** > **Transacciones** en mayor que 100; **Factor de riesgo para la seguridad** > **Cifrado de datos en reposo** en igual a **False**; y **Puntuación de riesgo** en igual a menos de 6.

![Filtros de aplicaciones detectadas](./media/discovered-app-filters.png)

Una vez que se han filtrado los resultados, puede [no autorizar y bloquear](governance-discovery.md) las aplicaciones. Para ello, active la casilla de acción masiva para no autorizarlas en una sola acción. Después de no autorizarlas, puede usar un script de bloqueo para impedir que se usen en su entorno.

Cloud Discovery permite profundizar incluso más en el uso de la nube de su organización e identificar instancias específicas que están en uso mediante la investigación de los subdominios detectados.
     
Por ejemplo, puede diferenciar entre los distintos sitios de SharePoint.

Esto solo se admite en los firewalls y servidores proxy que contienen datos de dirección URL de destino. Consulte la lista de dispositivos compatibles en [Firewalls y servidores proxy compatibles](set-up-cloud-discovery.md#supported-firewalls-and-proxies).

 ![información de subdominio](./media/discovery-domains.png) 

## <a name="exclude-entities"></a>Excluir entidades  
Si tiene usuarios o direcciones IP del sistema que son especialmente ruidosos y no interesantes o aplicaciones que no son relevantes, es posible que quiera excluir sus datos de los datos de Cloud Discovery que se analizan. Por ejemplo, puede excluir toda la información que se origina en 127.0.0.1 o el host local.  
  
Para crear una exclusión:  
  
1.  En el portal, en el icono de configuración, seleccione **Configuración de Cloud Discovery**.  
  
2.  Haga clic en la pestaña **Excluir entidades**.  
  
3.  Seleccione la pestaña **Usuarios excluidos** o **Direcciones IP excluidas** y haga clic en el botón para **Agregar usuario** o **Agregar dirección IP**.  
  
4.  Agregue un alias de usuario o una dirección IP. Se recomienda agregar información sobre por qué se ha excluido la dirección IP o el usuario.  
  
     ![Excluir usuario](./media/exclude-user.png "excluir usuario")  
  
## <a name="manage-continuous-reports"></a>Administrar informes continuos  
Los informes continuos personalizados proporcionan más granularidad al supervisar los datos de registro de Cloud Discovery de la organización. Al crear informes personalizados, es posible filtrar por ubicaciones geográficas concretas, redes y sitios o unidades organizativas. De forma predeterminada, solo aparecen los informes siguientes en el selector de informes de Cloud Discovery:  
  
-  El **informe global** consolida toda la información del portal de todos los orígenes de datos incluidos en los registros.  
  
- El **informe específico de origen de datos** muestra únicamente la información de un origen de datos concreto.  
  
Para crear un informe continuo:  
  
1.  En el portal, en el icono de configuración, seleccione **Configuración de Cloud Discovery**.  
  
2.  Haga clic en la pestaña **Manage continuous report** (Administrar informe continuo).  
  
3.  Haga clic en el botón **Crear informe**.  
  
4.  Escriba un nombre de informe.  
  
5.  Seleccione los orígenes de datos que quiere incluir (todos u orígenes específicos).  
  
6.  Defina los filtros que quiera en los datos. Pueden ser **Unidades organizativas**, **Etiquetas de dirección IP** o **Intervalos de direcciones IP**. Para obtener más información sobre el trabajo con etiquetas de dirección IP e intervalos de direcciones IP, consulte [Organize the data according to your needs](ip-tags.md) (Organizar los datos de acuerdo a las necesidades).  
  
    ![crear informe continuo personalizado](./media/create-custom-continuous-report.png) 

> [!NOTE]
> Todos los informes personalizados se limitan a un máximo de 1 GB de datos sin comprimir. Si hay más de 1 GB de datos, se exportará el primer GB de datos en el informe.


## <a name="deleting-cloud-discovery-data"></a>Eliminar datos de Cloud Discovery  
Hay una serie de razones por las que puede que quiera eliminar los datos de Cloud Discovery. Se recomienda eliminarlos en los casos siguientes:  
  
-   Si cargó manualmente archivos de registro y ha pasado mucho tiempo desde que actualizó el sistema con nuevos archivos de registro y no quiere que los datos antiguos afecten a los resultados.  
  
-   Cuando se establece una nueva vista de datos personalizada, solo se aplica a los nuevos datos desde ese punto en adelante, por lo que es posible que quiera borrar los datos antiguos y luego volver a cargar los archivos de registro para permitir que la vista de datos personalizada tome los eventos de los datos del archivo de registro.  
  
-   Si hay muchos usuarios o direcciones IP que hayan vuelto a trabajar recientemente después de estar sin conexión durante algún tiempo, su actividad se identificará como anómala y es posible que obtenga muchas infracciones positivas falsas.  
  
Para eliminar datos de Cloud Discovery:  
  
1. En el portal, en el icono de configuración, seleccione **Configuración de Cloud Discovery**.  
  
2. Haga clic en la pestaña **Eliminar datos**.  
  
    Es importante estar seguro de querer eliminar los datos antes de continuar, ya que no se puede deshacer y elimina **todos** los datos de Cloud Discovery del sistema.  
  
3. Haga clic en el botón **Eliminar**.  
  
    ![eliminar datos](./media/delete-data.png "eliminar datos")  
  
   > [!NOTE]  
   >  El proceso de eliminación tarda unos minutos y no es inmediato.  




## <a name="see-also"></a>Consulta también
 
[Crear informes de instantáneas de Cloud Discovery](create-snapshot-cloud-discovery-reports.md)

[Configurar la carga de registros automática para informes continuos](configure-automatic-log-upload-for-continuous-reports.md)

[Trabajar con datos de Cloud Discovery](working-with-cloud-discovery-data.md)

