---
title: Controlar las aplicaciones en la nube con directivas | Microsoft Docs
description: "En este tema se proporciona información sobre cómo se usan las directivas y cómo se configuran para controlar el uso de aplicaciones en la nube."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 10/15/2016
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: 14d10238-0f61-43e9-ab96-71534a27d3d4
ms.reviewer: reutam
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: ed4ea71b24767d3602d40894d1cbac7447bcd8a2
ms.openlocfilehash: 10b4a9575951007dbee9003fd061fb5aaa2d3823


---
# <a name="control-cloud-apps-with-policies"></a>Controlar las aplicaciones en la nube con directivas

Las directivas permiten definir la forma en que quiere que los usuarios se comporten en la nube. Permiten detectar comportamientos de riesgo, infracciones o puntos de datos y actividades sospechosos en el entorno de nube y, si fuera necesario, integrar flujos de trabajo de corrección para lograr una mitigación de riesgos completa. Hay varios tipos de directivas que se correlacionan con los diferentes tipos de información que quiere recopilar sobre el entorno de nube y los tipos de acciones correctoras que quizás quiera realizar.  
  
Por ejemplo, si hay una amenaza de infracción de datos que quiere poner en cuarentena, necesitará un tipo de directiva distinto que si quiere bloquear el uso de una aplicación de riesgo en la nube en la organización.  
  
## <a name="policy-types"></a>Tipos de directivas  
Pueden crearse los siguientes tipos de directivas:  
  
|Tipo de directiva|Use|  
|-----------------|---------|  
|Directiva de actividad|Las directivas de actividad permiten aplicar una amplia gama de procesos automatizados, con lo que se aprovechan las API del proveedor de aplicaciones. Estas directivas permiten supervisar actividades concretas realizadas por distintos usuarios o seguir niveles inesperadamente altos de un determinado tipo de actividad.|  
|Directiva de detección de anomalías|Las directivas de detección de anomalías permiten buscar actividades inusuales en la nube según los factores de riesgo que se establezcan aquí para emitir alertas cuando ocurra algo diferente de la línea de base de la organización o de la actividad normal del usuario.|  
|Directiva de detección de anomalías de Cloud Discovery|Las directivas de detección de anomalías de Cloud Discovery examinan los registros que se usan para detectar aplicaciones en la nube y buscan apariciones inusuales. Por ejemplo, cuando un usuario que nunca ha usado Dropbox de repente carga 600 GB o cuando hay muchas más transacciones de lo habitual en una aplicación determinada.|  
|Directiva de detección de aplicaciones|Las directivas de detección de aplicaciones permiten establecer alertas que notifican cuando se detectan nuevas aplicaciones en la organización.|  
|Directiva de archivo|Las directivas de archivo permiten examinar las aplicaciones en la nube para detectar tipos de archivo o archivos concretos (compartidos, compartidos con dominios externos), datos (información de propiedad, información personal, información de tarjeta de crédito, etc.) y aplicar acciones de gobierno a los archivos (las acciones de gobierno son específicas de la aplicación en la nube).|  
  
## <a name="identifying-risk"></a>La identificación de riesgos  
Cloud App Security ayuda a mitigar los distintos riesgos en la nube. Puede configurar cualquier directiva y alerta de modo que esté asociada con uno de los siguientes riesgos:  
  
-   **Control de acceso:** ¿quién accede a qué desde dónde?  
  
     Se supervisa el comportamiento en todo momento, se detectan actividades anómalas (incluidos ataques internos y externos de alto riesgo) y se aplica una directiva para alertar, bloquear o exigir verificación de identidad para cualquier aplicación o acción concreta dentro una aplicación. Se habilitan directivas de control de acceso locales y móviles basadas en el usuario, el dispositivo y la geografía con bloqueo general y vista, edición y bloqueo pormenorizados. Se detectan eventos de inicio de sesión sospechosos, incluidos errores de autenticación multifactor, errores de inicio de sesión de cuentas deshabilitadas y eventos de suplantación.  
  
-   **Cumplimiento normativo:** ¿se infringen los requisitos de cumplimiento normativo?  
  
     Se catalogan y se identifican los datos confidenciales o regulados, incluidos los permisos de uso compartido de cada archivo, almacenados en servicios de sincronización de archivos para garantizar el cumplimiento de normas como PCI, SOX e HIPAA.  
  
-   **Control de configuración:** ¿se están realizando cambios no autorizados en la configuración?  
  
     Se supervisan los cambios de configuración, incluida la manipulación de la configuración remota.  
  
-   **Cloud Discovery:** ¿se están usando nuevas aplicaciones sin autorizar en la organización? ¿Tiene un problema de uso de aplicaciones de TI en la sombra del que no es consciente?  
  
     La valoración del riesgo general de cada aplicación en la nube en función de las certificaciones normativas y del sector y  
    los procedimientos recomendados permite supervisar el número de usuarios, actividades, volumen de tráfico y horas de uso típicas de  
    cada aplicación en la nube.  
  
-   **DLP:** ¿se están compartiendo públicamente archivos de su propiedad? ¿Es necesario poner archivos en cuarentena?  
  
     La integración DLP local proporciona integración y corrección de bucle cerrado con soluciones DLP locales existentes.  
  
-   **Cuentas con privilegios:** ¿es necesario supervisar cuentas de administrador?  
  
     Supervisión de actividad en tiempo real e informes de usuarios con privilegios y administradores.  
  
-   **Control de uso compartido:** ¿cómo se comparten los datos en el entorno de nube?  
  
     Inspeccione el contenido de archivos y el contenido en la nube y aplique directivas de uso compartido internas y externas. Supervise la colaboración y aplique directivas de uso compartido, por ejemplo el bloqueo del uso compartido de los archivos fuera de la organización.  
  
-   **Detección de amenazas:** ¿hay actividades sospechosas que amenacen el entorno de nube?  
  
     Reciba notificaciones en tiempo real de cualquier umbral de actividad o infracción de una directiva a través del correo electrónico o un mensaje de texto. La aplicación de algoritmos de aprendizaje automático de Cloud App Security permite detectar comportamientos que podrían indicar que un usuario está haciendo un uso indebido de los datos.  
  
## <a name="how-to-control-risk"></a>Cómo controlar el riesgo  
Siga este proceso para controlar el riesgo con directivas:  
  
1.  Cree una directiva a partir de una plantilla o una consulta.  
  
2.  Ajuste la directiva para lograr los resultados esperados.  
  
3.  Agregue acciones automatizadas para responder a los riesgos y corregirlos automáticamente.  
  
### <a name="create-a-policy"></a>Crear una directiva  
Puede usar plantillas de directiva de Cloud App Security como base para todas las directivas o crear directivas a partir de una consulta.  
  
La plantillas de directiva ayudan a establecer los filtros correctos y las configuraciones necesarias para detectar eventos específicos de interés en el entorno. Las plantillas incluyen directivas de todos los tipos y se pueden aplicar a diversos servicios.  
  
Para crear una directiva a partir de una **plantilla de directiva**, haga lo siguiente:  
  
1.  En la consola, haga clic en **Control** y luego en **Plantillas**.  
  
     ![](./media/create-policy-from-template.png)  
  
2.  Haga clic en **+** en el extremo derecho de la fila de la plantilla que quiere usar. Se abre una página de creación de directivas que contiene la configuración predefinida de la plantilla.  
  
3.  Modifique la plantilla según sea necesario para la directiva personalizada. Cada propiedad y campo de esta nueva directiva basada en plantilla se puede modificar según las propias necesidades.  
> [!NOTE] 
>Al usar filtros de directiva, **Contiene** solo buscará palabras completas separadas por comas, puntos, espacios o caracteres de subrayado. Por ejemplo, si busca **malware** o **virus**, encontrará virus_malware_file.exe, pero no encontrará malwarevirusfile.exe. Si busca **malware.exe**, encontrará TODOS los archivos que contengan malware o exe en el nombre de archivo, mientras que si busca **"malware.exe"** (con comillas) solo encontrará los archivos que contengan exactamente "malware.exe". 
     **Es igual a** solo buscará la cadena completa. Por ejemplo, si busca **malware.exe**, encontrará malware.exe pero no malware.exe.txt.  
4.  Después de crear la nueva directiva basada en plantilla, aparece un vínculo a la nueva directiva en la columna **Directivas vinculadas** de la tabla de plantillas de directivas situada junto a la plantilla a partir de la que se ha creado la directiva.  
     Puede crear tantas directivas como quiera a partir de cada plantilla y todas estarán vinculadas a la plantilla original, lo que permite realizar un seguimiento de todas las directivas creadas con la misma plantilla.  
  
También puede **crear una directiva durante la investigación**. Si está investigando el **Registro de actividades**, los **Archivos** o las **Cuentas** y los explora en profundidad en busca de algo concreto, puede crear una nueva directiva basada en los resultados de la investigación en cualquier momento.  
  
Por ejemplo, si está mirando el **Registro de actividades** y ve que se está iniciando sesión con una de las cuentas de administrador desde una ubicación geográfica inesperada, puede filtrar los resultados del **Registro de actividades** para mostrar todos los registros en actividades de dicho administrador y luego crear un informe que le avise la siguiente vez que se detecte actividad de ese usuario.  
  
Para crear una directiva basada en los resultados de la investigación, haga lo siguiente:  
  
1.  En la consola, haga clic en **Investigar** y luego en **Registro de actividades**, **Archivos** o **Cuentas**.  
  
2.  Use los filtros de la parte superior de la página para limitar los resultados de búsqueda al área sospechosa, por ejemplo, en la página Registro de actividades, haga clic en **Usuario** y seleccione el administrador cuya cuenta está registrando actividad inusual. Después, en **Actividad**, seleccione **Copiar carpeta** y **Copiar archivo**.  
  
     ![](./media/create-file-from-investigation.png)  
  
3.  En la esquina superior derecha de la consola, haga clic en **Nueva directiva a partir de búsqueda**![](./media/new-policy-from-search-button.png).  
  
4.  Se abre una página de creación de directivas que contiene los filtros usados en la investigación.  
  
5.  Modifique la plantilla según sea necesario para la directiva personalizada. Cada propiedad y campo de esta nueva directiva basada en investigación se puede modificar según las propias necesidades.  
   
> [!NOTE] 
> Al usar filtros de directiva, **Contiene** solo buscará palabras completas separadas por comas, puntos, espacios o caracteres de subrayado. Por ejemplo, si busca **malware** o **virus**, encontrará virus_malware_file.exe, pero no encontrará malwarevirusfile.exe.  
     **Es igual a** solo buscará la cadena completa. Por ejemplo, si busca **malware.exe**, encontrará malware.exe pero no malware.exe.txt.  
  
 
 
![crear directiva de actividad basada en investigación](./media/create-activity-policy-from-investigation.png)
 
 
  
> [!NOTE]  
>  Para obtener más información sobre la configuración de los campos de la directiva, consulte la documentación correspondiente de la directiva:  
>   
>  [Directivas de actividad de usuario](user-activity-policies.md)  
>   
>  [Directivas de protección de datos](data-protection-policies.md)  
>   
>  [Directivas de Cloud Discovery](cloud-discovery-policies.md)  
  
### <a name="policy-conflicts"></a>Conflictos de directivas
Después de crear varias directivas, puede darse el caso de que las directivas se superpongan. Si es así, Cloud App Security procesará las directivas de la manera siguiente:
* Si dos directivas contienen acciones que están contenidas en la otra directiva (por ejemplo, **Quitar recursos compartidos externos** se incluye en **Hacer privado**), Cloud App Security resolverá el conflicto y se aplicará la acción más fuerte.
* Si las acciones no tienen ninguna relación (por ejemplo, **Enviar una notificación al propietario** y **Hacer privado**), se llevarán a cabo ambas acciones.
* Si las acciones entran en conflicto (por ejemplo **Cambiar el propietario al usuario A** y **Cambiar el propietario al usuario B**), pueden darse resultados diferentes para cada coincidencia. Es importante cambiar las directivas para evitar conflictos, ya que pueden producir cambios no deseados en la unidad que serán difíciles de detectar. 


## <a name="see-also"></a>Consulte también  
[Actividades diarias para proteger el entorno de nube](daily-activities-to-protect-your-cloud-environment.md)   
[Para obtener soporte técnico, visite la página de soporte técnico asistido de Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Los clientes Premier también pueden elegir Cloud App Security directamente desde el Portal Premier.](https://premier.microsoft.com/)  
  


<!--HONumber=Oct16_HO4-->

