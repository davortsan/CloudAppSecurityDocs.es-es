---
title: Usar datos de Cloud Discovery para detectar comportamientos de riesgo | Microsoft Docs
description: "En este tema se proporcionan instrucciones sobre cómo trabajar con datos de Cloud Discovery, lo que incluye trabajar con la puntuación de riesgo de la aplicación."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 3/19/2017
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: cf94b290-b7ef-4fee-854e-c8ff8d11dea9
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 90a8354c8ec3c757ee145be29599b88b5eb7e58f
ms.sourcegitcommit: 0d4748ea2a71e6ee2b0fa1c0498d9219bfbda29a
translationtype: HT
---
# <a name="working-with-cloud-discovery"></a>Trabajo con Cloud Discovery
## <a name="review-the-cloud-discovery-dashboard"></a>Revisar el panel de Cloud Discovery

El panel de Cloud Discovery está diseñado para proporcionar más información sobre cómo se usan las aplicaciones en la nube en la organización. Proporciona una visión general de un vistazo sobre los tipos de aplicaciones que se usan, las alertas abiertas y los niveles de riesgo de las aplicaciones de la organización. También muestra quiénes son los usuarios que más usan las aplicaciones y proporciona un mapa de ubicación de la sede central de la aplicación. El panel de Cloud Discovery tiene numerosas opciones para filtrar los datos, de modo que pueda generar vistas específicas en función de lo que más le interese y gráficos fáciles de entender para que se haga una idea general de un vistazo.

![panel de Cloud Discovery](./media/cloud-discovery-dashboard.png)

Lo primero que debe hacer para obtener una visión general de sus aplicaciones de Cloud Discovery es ir al panel de Cloud Discovery y revisar lo siguiente:
 
1. Primero, consulte el uso general de aplicaciones en la nube de la organización en la información general sobre el uso de alto nivel.

2. Después, profundice un nivel para ver cuáles son las categorías que más se usan en la organización para cada uno de los diferentes parámetros de uso y qué porcentaje de este uso se debe a aplicaciones autorizadas.

3. Profundice todavía más y vea todas las aplicaciones de una categoría específica en el widget de aplicaciones detectadas.

4. Puede ver los principales usuarios y las direcciones IP de origen para identificar los usuarios predominantes de aplicaciones en la nube de la organización.
5. Compruebe cómo se extienden las aplicaciones detectadas según la ubicación geográfica (de acuerdo con su sede central) en el mapa de la sede central de la aplicación.

6. Por último, no olvide revisar la puntuación de riesgo de la aplicación detectada en la **información general sobre el riesgo de las aplicaciones** y comprobar el estado de las alertas de detección para ver cuántas alertas abiertas debe investigar.


## <a name="customize-the-risk-score"></a>Personalizar la puntuación de riesgo  
Cloud Discovery proporciona datos importantes sobre la credibilidad y la confianza de las aplicaciones en la nube que se usan en el entorno. En el portal, cada aplicación detectada se muestra junto a una puntuación total que representa la evaluación de Cloud App Security de la madurez de uso de esta aplicación en concreto para las empresas. La puntuación total de cualquier aplicación es un promedio ponderado de tres subpuntuaciones relacionadas con las tres subcategorías que Cloud App Security tiene en cuenta al evaluar la confiabilidad:  
  
-   **General**: esta categoría se refiere a aspectos básicos sobre la empresa que produce la aplicación, incluidos su dominio, año de fundación y popularidad. Estos campos están diseñados para reflejar la estabilidad de la empresa en el nivel más básico.  
  
-   **Seguridad**: la categoría de seguridad tiene en cuenta todos los estándares relacionados con la seguridad física de los datos usados por la aplicación detectada. Esto incluye campos como autenticación multifactor, cifrado, clasificación de los datos y propiedad de los datos.  
  
-   **Cumplimiento normativo**: esta categoría muestra qué estándares comunes de cumplimiento de procedimientos recomendados cumple la empresa que produce la aplicación. La lista de especificaciones incluye estándares como HIPAA, CSA y PCI-DSS.  
  
Cada una de las categorías se compone de muchas propiedades específicas. Según el algoritmo de puntuación, cada propiedad recibe una puntuación preliminar de entre 0 y 10, en función del valor. En consecuencia, los valores True/False recibirán 10 o 0, mientras que propiedades continuas como la antigüedad del dominio recibirán un valor determinado del espectro. La puntuación de cada propiedad se pondera con todos los demás campos existentes en la categoría para crear la subpuntuación de esta. Si encuentra una aplicación sin puntuar, eso normalmente indica que sus propiedades son desconocidas y que, por lo tanto, no se ha puntuado.  
  
Es importante dedicar un minuto a revisar y modificar las ponderaciones predeterminadas otorgadas a la configuración de puntuación de Cloud Discovery. De forma predeterminada, todos los distintos parámetros evaluados tienen la misma ponderación. Si hay determinados parámetros que son más o menos importantes para la organización, es importante cambiarlos de la siguiente forma:  
  
1.  En el portal, en el icono de configuración, seleccione **Configuración de Cloud Discovery**.  
  
2.  En **Configurar métrica de puntuación**, deslice el valor **Importancia** para cambiar la ponderación del campo a **Omitido**, **Bajo**, **Medio**, **Alto** o **Muy alto**.  
  
3.  Además, puede establecer si determinados valores no están disponibles o no son aplicables en el cálculo de la puntuación. Cuando se incluyen, los valores no aplicables tienen una contribución negativa a la puntuación calculada.  
  
     ![puntuación](./media/score.png "puntuación")  
  
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
  
6.  Defina los filtros que quiera en los datos. Pueden ser **Unidades organizativas**, **Etiquetas de dirección IP** o **Intervalos de direcciones IP**. Para obtener más información sobre el trabajo con etiquetas de dirección IP e intervalos de direcciones IP, consulte [Organize the data according to your needs](general-setup.md#IPtagsandRanges) (Organizar los datos de acuerdo a las necesidades).  
  
    ![crear informe continuo personalizado](./media/create-custom-continuous-report.png) 
  
## <a name="exclude-entities"></a>Excluir entidades  
Si tiene usuarios o direcciones IP del sistema que son especialmente ruidosos y no interesantes o aplicaciones que no son relevantes, es posible que quiera excluir sus datos de los datos de Cloud Discovery que se analizan. Por ejemplo, puede excluir toda la información que se origina en 127.0.0.1 o el host local.  
  
Para crear una exclusión:  
  
1.  En el portal, en el icono de configuración, seleccione **Configuración de Cloud Discovery**.  
  
2.  Haga clic en la pestaña **Excluir entidades**.  
  
3.  Seleccione la pestaña **Usuarios excluidos** o **Direcciones IP excluidas** y haga clic en el botón para **Agregar usuario** o **Agregar dirección IP**.  
  
4.  Agregue un alias de usuario o una dirección IP. Se recomienda agregar información sobre por qué se ha excluido la dirección IP o el usuario.  
  
     ![Excluir usuario](./media/exclude-user.png "excluir usuario")  
  
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



 
## <a name="see-also"></a>Consulte también  
[Actividades diarias para proteger el entorno de nube](daily-activities-to-protect-your-cloud-environment.md)   
[Para obtener soporte técnico, visite la página de soporte técnico asistido de Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Los clientes Premier también pueden elegir Cloud App Security directamente desde el Portal Premier.](https://premier.microsoft.com/)  
  
  