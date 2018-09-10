---
title: Información general sobre el escenario de protección contra amenazas | Microsoft Docs
description: En este tema se describe el escenario para proteger su organización contra amenazas en su entorno en la nube.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 4/29/2018
ms.topic: conceptual
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 7a06a243-9ec2-4a11-8db2-bc065cdfef64
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 5fd6cf54012d148261e98f0058109420cb55e9fa
ms.sourcegitcommit: 0ac08ca7b3140b79f1d36ff7152476c188fa12b3
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/07/2018
ms.locfileid: "44143877"
---
*Se aplica a: Microsoft Cloud App Security*


# <a name="protecting-your-organization-from-ransomware"></a>Proteger la organización frente a ransomware

En el ataque de ransomware masivo más reciente, WannaCry asestó un duro golpe al mundo cibernético, ya que infectó aproximadamente 200 000 equipos en 150 países. Con el aumento de los ataques de ransomware en los últimos años, con una media de 25 000 ataques al mes en 2015 y 56 000 en 2016, es imprescindible para la ciberseguridad ser proactivos a la hora de asegurarse de que la red y la nube no están en peligro. En este artículo se explica cómo se puede usar Cloud App Security para supervisar la nube, detectar y mitigar las amenazas y aplicar los procedimientos recomendados para proteger el entorno contra el ransomware.

## <a name="what-is-ransomware"></a>¿Qué es el ransomware?
El ransomware es un ataque cibernético en el que el atacante envía un archivo que puede bloquear el acceso al equipo y cifrar los archivos. A menudo, el atacante conserva los archivos para pedir un rescate y no los descifra hasta que recibe el pago, tras lo cual restaura el acceso al equipo, los archivos o aplicaciones LOB críticas. Los ataques de ransomware pueden afectar a cualquier equipo, hogar, oficina, red o servidor. De hecho, dado que las grandes organizaciones están integradas por numerosos usuarios que pueden abrir accidentalmente un archivo que libera ransomware en la red, son estas las que corren un mayor riesgo de tener que pagar al atacante para detener el ransomware y restaurar el acceso a los archivos o los equipos.

>[!NOTE]
> Este caso de uso se aplica a Office 365, G Suite, Box y Dropbox.

## <a name="the-threat"></a>LA AMENAZA
Un usuario de la organización es víctima de un ataque de ransomware. Es posible que, sin saberlo, el usuario haya abierto un correo electrónico infectado y haya ejecutado ransomware que infecta todos sus archivos, incluidos los archivos sincronizados en la nube.

## <a name="the-solution"></a>LA SOLUCIÓN
Detecte el posible ransomware en el entorno en la nube. Para ello, cree una directiva para notificarle en caso de que detecte actividad sospechosa y configure acciones automatizadas para impedir que los archivos de ransomware se guarden en la nube.

## <a name="out-of-the-box-protection"></a>Protección de serie

[Conecte](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md) al menos una aplicación en la nube (Office 365, G Suite, Box y Dropbox) con Cloud App Security.

1.  De forma predeterminada, Cloud App Security examina la red para establecer una base de referencia. Esto permite identificar los patrones de actividad habitual de sus usuarios en la nube, tanto el hecho en sí como el momento en el que actúen. 

2. Las [directivas de detección de amenazas](anomaly-detection-policy.md) automatizadas de Cloud App Security inician su ejecución en segundo plano desde el momento en que se conecta. Una de estas directivas busca actividad de ransomware para garantizar la cobertura más completa frente a ataques de ransomware sofisticados. Con nuestra experiencia en investigación de seguridad para identificar patrones de comportamiento que reflejan la actividad de ransomware, Cloud App Security garantiza una protección integral y sólida. Puede que represente un proceso de cifrado adverso si Cloud App Security identifica, por ejemplo, una alta tasa de cargas de archivos o de actividades de eliminación de archivos. Estos datos se recopilan en los registros procedentes de las API conectadas y luego se combinan con los patrones de comportamiento aprendidos y la inteligencia sobre amenazas, por ejemplo, extensiones de ransomware conocidas. 




   ## <a name="see-also"></a>Consulte también  
   [Actividades diarias para proteger el entorno de nube](daily-activities-to-protect-your-cloud-environment.md)   

[Los clientes Premier también pueden elegir Cloud App Security directamente desde el Portal Premier.](https://premier.microsoft.com/)  
  
  