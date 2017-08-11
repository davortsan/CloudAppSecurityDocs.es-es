---
title: Trabajar con aplicaciones detectadas en Cloud App Security | Microsoft Docs
description: "En este tema se describe el proceso de identificación y corrección de aplicaciones de riesgo de Cloud Discovery en Cloud App Security."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 8/6/2017
ms.topic: get-started-article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: 645fd8c7-06d0-4f93-a85c-2976e7b3766d
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 683815d0db528ac65b0d547cd8e5ab09ea64321f
ms.sourcegitcommit: f9851779aa15b11f559e56ac818f1333f027c000
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/07/2017
---
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

## <a name="discovered-app-filters"></a>Filtros de aplicaciones detectadas

Hay filtros de aplicaciones detectadas básicos y avanzados. Para aplicar un filtro complejo (como en el ejemplo anterior), use la opción avanzada, que incluye lo siguiente:

![Aplicaciones detectadas](./media/discovered-apps.png)  


- **Etiqueta de aplicación**: seleccione si la aplicación se ha autorizado o no y si no está etiquetada. Además, puede crear una etiqueta personalizada para la aplicación y usarla para filtrar tipos específicos de aplicaciones. 
- **Aplicaciones y dominios**: permite buscar aplicaciones específicas o aplicaciones usadas en dominios concretos. 
- **Categorías**: el filtro de categorías, que se encuentra a la izquierda de la página, permite buscar tipos de aplicaciones en función de categorías de aplicaciones, como aplicaciones de redes sociales, aplicaciones de almacenamiento en la nube, etc. Puede seleccionar varias categorías a la vez o una sola categoría y, después, aplicarles los filtros básicos y avanzados.
- **Factor de riesgo de cumplimiento**: permite buscar normas, certificaciones y compatibilidades específicas que puede cumplir la aplicación (HIPAA, ISO 27001, SOC 2, PCI-DSS, etc.).
- **Factor de riesgo general**: permite buscar factores de riesgo generales, como la popularidad entre los consumidores, la configuración regional del centro de datos, etc.
- **Puntuación de riesgo**: permite filtrar las aplicaciones según su puntuación de riesgo, de modo que pueda centrarse, por ejemplo, en revisar únicamente las aplicaciones de mucho riesgo. También puede reemplazar la puntuación de riesgo establecida por Cloud App Security. Para obtener más información, vea [Trabajo con la puntuación de riesgo](risk-score.md).
- **Factor de riesgo para la seguridad**: permite filtrar en función de medidas de seguridad específicas (por ejemplo, cifrado en reposo, autenticación multifactor, etc.).
- **Uso**: permite filtrar en función de las estadísticas de uso de la aplicación, como aplicaciones con menos o más **cargas de datos** que la cantidad especificada, o aplicaciones con menos o más de un número específico de **usuarios**.

## <a name="creating-and-managing-custom-app-tags"></a>Crear y administrar etiquetas de aplicación personalizadas

Puede crear etiquetas de aplicación personalizadas. Estas etiquetas pueden usarse como filtros para profundizar un poco más en los tipos de aplicaciones específicos que quiere investigar. Por ejemplo, lista de supervisión personalizada, asignación a una unidad de negocio específica o aprobaciones personalizadas (por ejemplo, "aprobado por el departamento legal").

Para crear una etiqueta de aplicación personalizada:

1. En el engranaje de **Configuración** seleccione **Cloud Discovery** y en la pestaña **Manage app tags** (Administrar etiquetas de aplicación) haga clic en el icono ![icono más](./media/plus-icon.png). 

![Crear una etiqueta de aplicación personalizada](./media/create-app-tag.png)

2. Puede usar la tabla **Manage app tags** (Administrar etiquetas de aplicación) para ver qué aplicaciones están etiquetadas con cada etiqueta de aplicación y puede eliminar las etiquetas de aplicación que no se usan.

3. Para aplicar una etiqueta de aplicación, en la pestaña **Aplicaciones detectadas**, haga clic en los tres puntos situados a la derecha de la tabla y seleccione la etiqueta de aplicación que quiere aplicar. 

> [!NOTE]
>También puede crear una etiqueta de aplicación directamente en la tabla **Aplicaciones detectadas**. Para ello, haga clic en **Create app tag** (Crear etiqueta de aplicación) después de seleccionar los tres puntos situados a la derecha de cualquier aplicación seleccionada. También puede tener acceso a la pantalla **Manage app tags** (Administrar etiquetas de aplicación). Para ello, haga clic en el vínculo situado en la esquina de la ventana emergente **Create app tag** (Crear etiqueta de aplicación).

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

## <a name="deleting-cloud-discovery-data"></a>Eliminar datos de Cloud Discovery  
Hay una serie de razones por las que puede que quiera eliminar los datos de Cloud Discovery. Se recomienda eliminarlos en los casos siguientes:  
  
-   Si cargó manualmente archivos de registro y ha pasado mucho tiempo desde que actualizó el sistema con nuevos archivos de registro y no quiere que los datos antiguos afecten a los resultados.  
  
-   Cuando se establece una nueva vista de datos personalizada, solo se aplica a los nuevos datos desde ese punto en adelante, por lo que es posible que quiera borrar los datos antiguos y luego volver a cargar los archivos de registro para permitir que la vista de datos personalizada tome los eventos de los datos del archivo de registro.  
  
-   Si hay muchos usuarios o direcciones IP que hayan vuelto a trabajar recientemente después de estar sin conexión durante algún tiempo, su actividad se identificará como anómala y es posible que obtenga muchas infracciones positivas falsas.  
  
Para eliminar datos de Cloud Discovery:  
  
1.  En el portal, en el icono de configuración, seleccione **Configuración de Cloud Discovery**.  
  
2.  Haga clic en la pestaña **Eliminar datos**.  
  
     Es importante estar seguro de querer eliminar los datos antes de continuar, ya que no se puede deshacer y elimina **todos** los datos de Cloud Discovery del sistema.  
  
3.  Haga clic en el botón **Eliminar**.  
  
     ![eliminar datos](./media/delete-data.png "eliminar datos")  
  
   > [!NOTE]  
   >  El proceso de eliminación tarda unos minutos y no es inmediato.  




## <a name="see-also"></a>Vea también
 
[Crear informes de instantáneas de Cloud Discovery](create-snapshot-cloud-discovery-reports.md)

[Configurar la carga de registros automática para informes continuos](configure-automatic-log-upload-for-continuous-reports.md)

[Trabajar con datos de Cloud Discovery](working-with-cloud-discovery-data.md)

