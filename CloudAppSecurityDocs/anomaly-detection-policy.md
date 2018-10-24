---
title: Crear directivas de detección de anomalías en Cloud App Security | Microsoft Docs
description: En este tema se proporciona una descripción de las directivas de detección de anomalías, así como información de referencia sobre los bloques de creación de una directiva de detección de anomalías.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 10/11/2018
ms.topic: conceptual
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: ab9bc377-d2f5-4f4c-a419-f1728a15d1c7
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: dc5249ae183da37293920aade12346aaca46eb32
ms.sourcegitcommit: 82052a88acbc33893f7b9e0d10cc2e8c652ef003
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/16/2018
ms.locfileid: "49349634"
---
*Se aplica a: Microsoft Cloud App Security*

 
# <a name="get-instantaneous-behavioral-analytics-and-anomaly-detection"></a>Obtención de análisis de comportamiento y detección de anomalías instantáneos

Las directivas de detección de anomalías de Microsoft Cloud App Security ofrecen análisis de comportamiento de usuarios y entidades (UEBA) y aprendizaje automático (ML) de serie para que pueda ejecutar inmediatamente la detección de amenazas avanzada en el entorno en la nube. Dado que se habilitan automáticamente, las nuevas directivas de detección de anomalías ofrecen resultados al instante proporcionando detecciones inmediatas, dirigidas a numerosas anomalías de comportamientos entre los usuarios, las máquinas y los dispositivos conectados a la red.  Además, las nuevas directivas exponen más datos a partir del motor de detección de Cloud App Security, lo que le ayuda a agilizar el proceso de investigación y contener las amenazas en curso. 

Las directivas de detección de anomalías se habilitan automáticamente, pero Cloud App Security tiene un período de aprendizaje inicial de siete días durante el cual no todas las alertas de detección de anomalías se generan. Transcurrido este tiempo, cada sesión se compara con la actividad, los momentos en que los usuarios estaban activos, las direcciones IP, los dispositivos, etc., que se detectaron durante el mes anterior y la puntuación de riesgo de estas actividades.  Estas detecciones son parte del motor de detección de anomalías heurístico, que genera perfiles a partir de su entorno y desencadena alertas con respecto a una línea base que se define en función de la actividad de su organización. Estas detecciones también usan algoritmos de aprendizaje automático diseñados para generar perfiles de los usuarios y el patrón de inicio de sesión para reducir los falsos positivos.

Las anomalías se detectan mediante el examen de la actividad del usuario. El riesgo se evalúa mediante el análisis de más de 30 indicadores de riesgo distintos, agrupados por factores de riesgo, que son los siguientes: 
          
 -   Dirección IP de riesgo
 -   Errores de inicio de sesión
 -   Actividad administrativa
 -   Cuentas inactivas
 -   Ubicación  
 -   Viaje imposible
 -   Agente de usuario y dispositivo
 -   Tasa de actividad

Basándose en los resultados de la directiva, se activan alertas de seguridad. Cloud App Security examina todas las sesiones de los usuarios en la nube y le alerta cuando ocurre algo que es diferente a la línea base de la organización o de la actividad normal del usuario. 


## <a name="anomaly-detection-policies"></a>Directivas de detección de anomalías
Puede ver las directivas de detección de anomalías en el portal haciendo clic en **Control** y luego en **Directivas**. Seleccione **Directiva de detección de anomalías** para el tipo de directiva.

 ![nuevas directivas de detección de anomalías](./media/new-anomaly-detection-policies.png)

Están disponibles las directivas de detección de anomalías siguientes:

**Viaje imposible**
-  Esta detección identifica dos actividades de usuario (en una o varias sesiones) que se originan desde ubicaciones distantes geográficamente dentro de un período de tiempo menor que el que el usuario habría necesitado para desplazarse desde la primera hasta la segunda, lo que indica que otro usuario está usando las mismas credenciales. Esta detección usa un algoritmo de aprendizaje automático que omite falsos positivos obvios que contribuyan a la condición de viaje imposible, como las redes privadas virtuales y las ubicaciones que otros usuarios de la organización usen con frecuencia. La detección tiene un período de aprendizaje inicial de siete días durante el cual se memoriza el patrón de actividad de un usuario nuevo.


**Actividad desde un país poco frecuente**
- Esta detección tiene en cuenta las ubicaciones de actividad anteriores para determinar ubicaciones nuevas e infrecuentes. El motor de detección de anomalías almacena información sobre las ubicaciones anteriores que usan los usuarios de la organización. Se desencadena una alerta cuando se produce una actividad desde una ubicación que ningún usuario de la organización ha visitado recientemente o nunca. 

**Detección de malware**
- Esta detección identifica los archivos maliciosos en el almacenamiento en nube, tanto si proceden de aplicaciones de Microsoft como de aplicaciones de terceros. Microsoft Cloud App Security usa la inteligencia sobre amenazas de Microsoft para reconocer si determinados archivos están asociados a ataques de malware conocidos y son potencialmente maliciosos. Esta directiva integrada está deshabilitada de forma predeterminada. No se analizan todos los archivos, pero se usa la heurística para buscar archivos potencialmente peligrosos. Una vez que se han detectado archivos, puede ver una lista de **archivos infectados**. Haga clic en el nombre de archivo de malware en el cajón de archivos para abrir un informe de malware con información sobre el tipo de malware con el que está infectado el archivo.
    
**Actividad desde direcciones IP anónimas**
- Se identifica la actividad de los usuarios desde una dirección IP considerada como dirección IP anónima de proxy. Los usuarios que quieren ocultar la dirección IP de sus dispositivos usan estos servidores proxy, a veces de forma malintencionada. Esta detección usa un algoritmo de aprendizaje automático que reduce los falsos positivos, como las direcciones IP no etiquetadas que los usuarios de la organización usan habitualmente.

**Actividad de ransomware**
-  Cloud App Security ha ampliado sus funcionalidades de detección de ransomware con la detección de anomalías para garantizar una cobertura más completa frente a ataques de ransomware sofisticados. Con nuestra experiencia en investigación de seguridad para identificar patrones de comportamiento que reflejan la actividad de ransomware, Cloud App Security garantiza una protección integral y sólida. Puede que represente un proceso de cifrado adverso si Cloud App Security identifica, por ejemplo, una alta tasa de cargas de archivos o de actividades de eliminación de archivos. Estos datos se recopilan en los registros procedentes de las API conectadas y luego se combinan con los patrones de comportamiento aprendidos y la inteligencia sobre amenazas, por ejemplo, extensiones de ransomware conocidas. Para obtener más información sobre cómo Cloud App Security detecta ransomware, vea [Proteger la organización frente a ransomware](use-case-ransomware.md).

**Actividad realizada por el usuario cancelado**

- Esta detección le permite identificar cuando un empleado que ya no trabaja en la compañía sigue realizando acciones en las aplicaciones SaaS. Dado que los datos muestran que el mayor riesgo de una amenaza interna procede de empleados que se fueron en malos términos, es importante estar atento a la actividad en las cuentas de empleados dados de baja. A veces, cuando los empleados dejan una compañía, sus cuentas se desaprovisionan de las aplicaciones corporativas, pero en muchos casos sigue conservando el acceso a determinados recursos corporativos. Esto es incluso más importante si se tienen en cuenta las cuentas con privilegios, ya que el daño potencial que un ex administrador puede infligir es intrínsecamente mayor.
Esta detección aprovecha las ventajas de capacidad de Cloud App Security para supervisar el comportamiento de usuario entre las aplicaciones, lo que permite la identificación de la actividad normal del usuario, el hecho de que la cuenta se ha cerrado y la actividad real en otras aplicaciones. Por ejemplo, un empleado cuya cuenta de Azure AD se ha cerrado, pero aún tiene acceso a la infraestructura AWS corporativa, tiene el potencial de causar daños a gran escala.  

**Actividad desde direcciones IP sospechosas**
- Se identifica la actividad de los usuarios desde una dirección IP considerada como de riesgo en Microsoft Threat Intelligence. Estas direcciones IP están implicadas en actividades malintencionadas como Botnet C&C y pueden indicar que la cuenta está en peligro. Esta detección usa un algoritmo de aprendizaje automático que reduce los falsos positivos, como las direcciones IP no etiquetadas que los usuarios de la organización usan habitualmente.


**Reenvío sospechoso de la bandeja de entrada**

- Esta detección busca reglas de reenvío de correo electrónico sospechosas, por ejemplo, si un usuario creó una regla de bandeja de entrada que reenvía una copia de todos los correos electrónicos a una dirección externa. 

**Actividades inusuales (realizadas por un usuario)**<br>
Estas detecciones identifican a los usuarios que realizan:

 - Varias actividades inusuales de descarga de archivos
 - Actividades inusuales de uso compartido de archivos
 - Actividades inusuales de eliminación de archivos
 - Actividades inusuales de suplantación
 - Actividades inusuales administrativas
 
Estas directivas buscan actividades dentro de una única sesión según la línea base establecida, lo que podría indicar un intento de vulneración. Estas detecciones aprovechan un algoritmo de aprendizaje automático que crea perfiles a partir del patrón de inicio de sesión de los usuarios y reduce los falsos positivos. Estas detecciones son parte del motor de detección de anomalías heurístico, que genera perfiles a partir de su entorno y desencadena alertas con respecto a una línea base que se define en función de la actividad de su organización.

**Varios intentos incorrectos de inicio de sesión**
- Se identifica a los usuarios que intentan iniciar sesión varias veces sin éxito en una única sesión según la línea base establecida, lo que podría indicar un intento de vulneración. 

## Habilitación del gobierno automatizado<a name="adp-automated-gov"></a>

Puede habilitar acciones de corrección automatizadas en las alertas generadas por directivas de detección de anomalías. 

1. Haga clic en el nombre de la directiva de detección en la página **Directiva**.
2. En la ventana **Editar directiva de detección de anomalías** que se abre, en **Gobierno**, establezca las acciones de corrección que quiera para cada aplicación conectada o para todas las aplicaciones. 
3. Haga clic en **Actualizar**.

 
## <a name="scope-anomaly-detection-policies"></a>Ámbito de directivas de detección de anomalías

Se puede establecer un ámbito para cada directiva de detección de anomalías por separado para que se aplique solo a los usuarios y grupos que desea incluir y excluir en la directiva.
Por ejemplo, puede establecer la actividad desde la detección de condado poco frecuente hasta omitir un usuario específico que viaja con frecuencia. 

Para establecer el ámbito de una directiva de detección de anomalías:
1. Haga clic en **Control** > **Directivas** y establezca el filtro **Tipo** en **Directiva de detección de anomalías**.
2. Haga clic en la directiva cuyo ámbito desea establecer.
3. En **Ámbito**, cambie la lista desplegable de la configuración predeterminada de **Todos los usuarios y grupos** a **Usuarios y grupos específicos**. 
4. Seleccione **Incluir** para especificar los usuarios y grupos para los que se aplicará esta directiva. Cualquier usuario o grupo que no se seleccione aquí no se considerará una amenaza y no generará una alerta.
5. Seleccione **Excluir** para especificar los usuarios para los que no se aplicará esta directiva. Cualquier usuario que seleccione aquí no se considerará una amenaza y no generará una alerta, incluso si es miembro de los grupos seleccionados en **Incluir**.

 ![ámbito de detección de anomalías](./media/anomaly-detection-scoping.png)
## <a name="triage-anomaly-detection-alerts"></a>Evaluación de las alertas de detección de anomalías

Puede evaluar la prioridad de las diversas alertas desencadenadas por las nuevas directivas de detección de anomalías rápidamente y decidir cuáles es necesario atender primero. Para ello, necesita el contexto de la alerta, de forma que pueda ver la imagen más grande y comprender si realmente está ocurriendo algo malintencionado.  

1. En el **registro de actividades**, puede abrir una actividad para mostrar el cajón de actividades. Haga clic en **Usuario** para ver la pestaña de información del usuario. Esta pestaña incluye información como el número de alertas, las actividades y desde dónde se han conectado, lo que es importante en una investigación. 

   ![alerta1 de detección de anomalías](./media/anomaly-alert-user1.png)
   ![alerta1 de detección de anomalías](./media/anomaly-alert-user2.png)
 
2. Esto le permite comprender qué actividades sospechosas realizó el usuario y aumentar la confianza en cuanto a si la cuenta se vio comprometida. Por ejemplo, una alerta sobre varios inicios de sesión erróneos realmente puede ser sospechosa y puede indicar posibles ataques por fuerza bruta, pero también puede ser un error de configuración de aplicación, haciendo que la alerta resulte ser verdadera. Sin embargo, si ve una alerta de varios inicios de sesión erróneos con actividades sospechosas adicionales, entonces hay una mayor probabilidad de que la cuenta se vea comprometida. En el ejemplo siguiente, puede ver que, después de la alerta de los **diversos intentos de inicio de sesión erróneos**, hubo **actividad desde una dirección IP TOR** y **actividad de viaje imposible**, ambas buenos indicadores de riesgo (IOC) por sí mismas. Si esto no fue suficientemente sospechoso, puede ver que el mismo usuario realizó una **actividad de descarga masiva**, que suele ser un indicador de que el atacante está realizando exfiltración de datos. 

   ![alerta de detección de anomalías 1](./media/anomaly-alert-user3.png)


3. En el caso de los archivos infectados con malware, una vez que se han detectado, puede ver una lista de **archivos infectados**. Haga clic en el nombre de archivo de malware en el cajón de archivos para abrir un informe de malware con información sobre el tipo de malware con el que está infectado el archivo. 


  

  
## <a name="next-steps"></a>Pasos siguientes 
[Actividades diarias para proteger el entorno de nube](daily-activities-to-protect-your-cloud-environment.md)   

[Los clientes Premier también pueden elegir Cloud App Security directamente desde el Portal Premier.](https://premier.microsoft.com/)  
  
  
