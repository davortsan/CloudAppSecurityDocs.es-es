---
title: "Crear directivas de detección de anomalías en Cloud App Security | Microsoft Docs"
description: "En este tema se proporciona una descripción de las directivas de detección de anomalías, así como información de referencia sobre los bloques de creación de una directiva de detección de anomalías."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 2/5/2018
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: ab9bc377-d2f5-4f4c-a419-f1728a15d1c7
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 9ac466a721a9e5eef13d868d2eae2ce1c2df58c8
ms.sourcegitcommit: 8bfb8236b83f7423e73fe449d662935c084ff844
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/09/2018
---
# <a name="get-instantaneous-behavioral-analytics-and-anomaly-detection"></a>Obtención de análisis de comportamiento y detección de anomalías instantáneos

Las directivas de detección de anomalías de Cloud App Security proporcionan análisis de comportamiento de usuarios y entidades (UEBA) y aprendizaje automático (ML) al instante para que pueda ejecutar inmediatamente la detección de amenazas avanzada en el entorno de nube. Dado que se habilitan automáticamente, las nuevas directivas de detección de anomalías ofrecen resultados al instante proporcionando detecciones inmediatas, dirigidas a numerosas anomalías de comportamientos entre los usuarios, las máquinas y los dispositivos conectados a la red.  Además, las nuevas directivas exponen más datos a partir del motor de detección de Cloud App Security, lo que le ayuda a agilizar el proceso de investigación y contener las amenazas en curso. 

Las directivas de detección de anomalías se habilitan automáticamente, pero Cloud App Security tiene un período de aprendizaje inicial de siete días durante el cual no todas las alertas de detección de anomalías se generan. Transcurrido este tiempo, cada sesión se compara con la actividad, los momentos en que los usuarios estaban activos, las direcciones IP, los dispositivos, etc., que se detectaron durante el mes anterior y la puntuación de riesgo de estas actividades.  Estas detecciones son parte del motor de detección de anomalías heurístico, que genera perfiles a partir de su entorno y desencadena alertas con respecto a una línea base que se define en función de la actividad de su organización. Estas detecciones también aprovechan los algoritmos de aprendizaje automático diseñados para generar perfiles de los usuarios y el patrón de inicio de sesión para reducir los falsos positivos.

Las anomalías se detectan mediante el examen de la actividad del usuario. El riesgo se evalúa mediante el análisis de más de 30 indicadores de riesgo distintos agrupados en varios factores de riesgo, que son los siguientes: 
          
 -   Dirección IP de riesgo
 -   Errores de inicio de sesión
 -   Actividad administrativa
 -   Cuentas inactivas
 -   Ubicación  
 -   Viaje imposible
 -   Agente de usuario y dispositivo
 -   Tasa de actividad

Basándose en los resultados de la directiva, se activan alertas de seguridad. Cloud App Security examina todas las sesiones de los usuarios en la nube y le alerta cuando ocurre algo que es diferente a la línea base de la organización o de la actividad normal del usuario. 


Puede ver las directivas de detección de anomalías en el portal haciendo clic en **Control** y luego en **Directivas**.

 ![nuevas directivas de detección de anomalías](./media/new-anomaly-detection-policies.png)

Están disponibles las directivas de detección de anomalías siguientes:

**Viaje imposible**
-  Esta detección identifica dos actividades de usuario (en una o varias sesiones) que se originan desde ubicaciones distantes geográficamente dentro de un período de tiempo menor que el que el usuario habría necesitado para desplazarse desde la primera hasta la segunda, lo que indica que otro usuario está usando las mismas credenciales. Esta detección usa un algoritmo de aprendizaje automático que omite falsos positivos obvios que contribuyan a la condición de viaje imposible, como las redes privadas virtuales y las ubicaciones que otros usuarios de la organización usen con frecuencia. La detección tiene un período de aprendizaje inicial de siete días durante el cual se memoriza el patrón de actividad de un usuario nuevo.


**Actividad desde un país poco frecuente**
- Esta detección tiene en cuenta las ubicaciones de actividad anteriores para determinar ubicaciones nuevas e infrecuentes. El motor de detección de anomalías almacena información sobre las ubicaciones anteriores que usan los usuarios de la organización. Se desencadena una alerta cuando una actividad se produce en una ubicación que el usuario (o cualquier usuario de la organización) no ha visitado recientemente o nunca. 


**Actividad desde direcciones IP anónimas**
- Se identifica la actividad de los usuarios desde una dirección IP considerada como dirección IP anónima de proxy. Los usuarios que quieren ocultar la dirección IP de sus dispositivos usan estos servidores proxy, a veces de forma malintencionada. Esta detección usa un algoritmo de aprendizaje automático que reduce los falsos positivos, como las direcciones IP no etiquetadas que los usuarios de la organización usan habitualmente.

**Actividad desde direcciones IP sospechosas**
- Se identifica la actividad de los usuarios desde una dirección IP considerada como de riesgo en Microsoft Threat Intelligence. Estas direcciones IP están implicadas en actividades malintencionadas como Botnet C&C y pueden indicar que la cuenta está en peligro. Esta detección usa un algoritmo de aprendizaje automático que reduce los falsos positivos, como las direcciones IP no etiquetadas que los usuarios de la organización usan habitualmente.


**Actividades inusuales (realizadas por un usuario)**

Estas detecciones identifican a los usuarios que realizan:

 - Varias actividades inusuales de descarga de archivos
 - Actividades inusuales de uso compartido de archivos
 - Actividades inusuales de eliminación de archivos
 - Actividades inusuales de suplantación
 - Actividades inusuales administrativas
 
Estas directivas buscan actividades dentro de una única sesión según la línea base establecida, lo que podría indicar un intento de vulneración. Estas detecciones aprovechan un algoritmo de aprendizaje automático que crea perfiles a partir del patrón de inicio de sesión de los usuarios y reduce los falsos positivos. Estas detecciones son parte del motor de detección de anomalías heurístico, que genera perfiles a partir de su entorno y desencadena alertas con respecto a una línea base que se define en función de la actividad de su organización.

**Varios intentos incorrectos de inicio de sesión**
- Se identifica a los usuarios que intentan iniciar sesión varias veces sin éxito en una única sesión según la línea base establecida, lo que podría indicar un intento de vulneración. 


## <a name="triaging-anomaly-detection-alerts"></a>Evaluación de las alertas de detección de anomalías

Puede evaluar la prioridad de las diversas alertas desencadenadas por las nuevas directivas de detección de anomalías rápidamente y decidir cuáles es necesario atender primero. Para ello, necesita el contexto de la alerta, de forma que pueda ver la imagen más grande y comprender si realmente está ocurriendo algo malintencionado.  

1. En el **registro de actividades**, puede abrir una actividad para mostrar el cajón de actividades. Haga clic en **Usuario** para ver la pestaña de información del usuario. Esto incluye información como el número de alertas, las actividades y desde dónde se han conectado, lo que es importante en una investigación. 

 ![alerta1 de detección de anomalías](./media/anomaly-alert-user1.png)
 ![alerta1 de detección de anomalías](./media/anomaly-alert-user2.png)

 
2. Esto le permite comprender qué actividades sospechosas realizó el usuario y aumentar la confianza en cuanto a si la cuenta se vio comprometida. Por ejemplo, una alerta sobre varios inicios de sesión erróneos realmente puede ser sospechosa y puede indicar posibles ataques por fuerza bruta, pero también puede ser un error de configuración de aplicación, haciendo que la alerta resulte ser verdadera. Sin embargo, si ve una alerta de varios inicios de sesión erróneos con actividades sospechosas adicionales, entonces hay una mayor probabilidad de que la cuenta se vea comprometida. En el ejemplo siguiente, puede ver que, después de la alerta de los **diversos intentos de inicio de sesión erróneos**, hubo **actividad desde una dirección IP TOR** y **actividad de viaje imposible**, ambas buenos indicadores de riesgo (IOC) por sí mismas. Si esto no fue suficientemente sospechoso, puede ver que el mismo usuario realizó una **actividad de descarga masiva**, que suele ser un indicador de que el atacante está realizando exfiltración de datos. 

  ![alerta1 de detección de anomalías](./media/anomaly-alert-user3.png)
  ![alerta1 de detección de anomalías](./media/anomaly-alert-user4.png)

 


  

  
## <a name="see-also"></a>Consulte también  
[Actividades diarias para proteger el entorno de nube](daily-activities-to-protect-your-cloud-environment.md)   

[Los clientes Premier también pueden elegir Cloud App Security directamente desde el Portal Premier.](https://premier.microsoft.com/)  
  
  
