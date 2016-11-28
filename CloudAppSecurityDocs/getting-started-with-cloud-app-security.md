---
title: "Introducción a Cloud App Security | Microsoft Docs"
description: En este tema se describe el proceso para que Cloud App Security entre en funcionamiento.
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 11/21/2016
ms.topic: get-started-article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: cf040b18-93d1-41e8-a26a-647c56afb00f
ms.reviewer: reutam
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 3c342e019dfca316ee89f68de60886d848abdb17
ms.openlocfilehash: 7137b7f362718f36a416d3c8e33040d208a92126


---

# <a name="getting-started-with-cloud-app-security"></a>Introducción a Cloud App Security
Cloud App Security le puede ayudar a sacar partido de las ventajas de las aplicaciones en la nube y a mantener a la vez el control de los recursos corporativos. Funciona mejorando la visibilidad de la actividad en la nube y ayuda a aumentar la protección de los datos corporativos. En este tema, le indicaremos los pasos que debe llevar a cabo para configurar Cloud App Security y trabajar con él.  

Su organización debe tener una licencia para utilizar Cloud App Security. Para obtener más información, consulte la sección Recursos sobre licencia en [Cómo comprar Cloud App Security](https://www.microsoft.com/en-us/cloud-platform/cloud-app-security).  

>[!NOTE]
>No necesita una licencia de Office 365 para utilizar Cloud App Security.  

## <a name="get-started-quickly-with-cloud-app-security"></a>Inicio rápido de Cloud App Security  

|Haga lo siguiente|Tarea|¿Requerido?|Cómo|Descripción|  
|-------------------------|----------|---------------|-------------|-----------------|  
|Paso 1. [Configure Cloud Discovery](set-up-cloud-discovery.md).|Cargar registros de tráfico|Requerido|**Para crear un informe continuo de Cloud Discovery**<br /><br /> 1. Vaya a **Configuración** > **Cloud Discovery settings** (Configuración de Cloud Discovery).<br /><br /> 2. Elija **Cargar registros automáticamente**.<br /><br /> 3. En la ficha **Orígenes de datos**, agregue los orígenes.<br /><br /> 4. En la pestaña **Recopiladores de registros**, configure el recopilador de registros.<br /><br /> **Para crear un informe de instantáneas de Cloud Discovery**<br /><br /> 1. Vaya a **Detectar** > **Crear nuevo informe de instantáneas** y siga los pasos.|**¿Por qué se deben configurar los informes de Cloud Discovery?**<br /> Tener visibilidad de la TI en la sombra de la organización es algo esencial. <br />Después de analizar los registros, podrá detectar fácilmente qué aplicaciones en la nube se usan, qué usuarios lo hacen y en qué dispositivos.|
|Paso 2. [Establezca la visibilidad, la protección y las acciones de gobierno instantáneas para las aplicaciones](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md).|Conectar aplicaciones|Requerido|1. Vaya a **Configuración** > **Conectores de aplicación**.<br /><br /> 2. Elija **Conectar aplicación** y seleccione una aplicación.<br /><br /> 3. Siga los pasos de configuración para conectar la aplicación.|**¿Por qué conectar una aplicación?**<br />Después de conectar una aplicación, puede obtener una mayor visión para que pueda investigar actividades, archivos y cuentas para las aplicaciones en su entorno de la nube.|
|Paso 3. [Controle las aplicaciones en la nube con directivas](control-cloud-apps-with-policies.md).|Crear las directivas|Requerido|**Para crear directivas**<br /><br /> 1. Vaya a **Control** > **Plantillas**.<br /><br /> 2. Seleccione una plantilla de directiva de la lista y elija (+) **Crear directiva**.<br /><br /> 3. Personalice la directiva (seleccione filtros, acciones y otras configuraciones) y luego elija **Crear**.<br /><br /> 4. En la ficha **Directivas**, elija la directiva para ver las coincidencias relevantes (actividades, archivos y alertas).<br /><br /> Sugerencia: a fin de cubrir todos los escenarios de seguridad del entorno de la nube, cree una política para cada **categoría de riesgo**.|**¿Cómo pueden las directivas ayudar a la organización?**<br />Puede utilizar directivas para ayudarle a supervisar tendencias, ver amenazas de seguridad y generar alertas e informes personalizados. Con las directivas se pueden crear acciones de gobierno y establecer controles de uso compartido de archivos y de prevención de pérdida de datos.|
|Paso 4. [Personalice la experiencia](general-setup.md#Adallom_mailsettings).|Agregar detalles de la organización|Recomendado|**Para especificar la configuración de correo electrónico**<br /><br /> 1. Vaya a **Configuración** > **Configuración de correo**.<br /><br /> 2. En **Identidad del emisor de correo electrónico**, escriba las direcciones de correo electrónico y el nombre para mostrar.<br /><br /> 3. En **Diseño del correo electrónico**, cargue la plantilla de correo electrónico de la organización.<br /><br /> **Para establecer notificaciones de administrador**<br /><br /> 1. En la barra de navegación, seleccione el nombre de usuario y luego vaya a **Configuración de usuario**.<br /><br /> 2. En **Notificaciones**, configure los métodos que quiere establecer para las notificaciones del sistema.<br /><br /> 3. Elija **Guardar**.<br /><br /> **Para personalizar las métricas de puntuación**<br /><br /> 1. Vaya a **Configuración** > **Cloud Discovery settings** (Configuración de Cloud Discovery).<br /><br /> 2. En **Configurar métrica de puntuación**, configure la importancia de los distintos valores de riesgo.<br /><br /> 3. Elija **Guardar**.<br /><br /> Ahora las puntuaciones de riesgo otorgadas a las aplicaciones detectadas están configuradas exactamente según las necesidades y las prioridades de la organización.|**¿Por qué personalizar el entorno?**<br />Algunas características funcionan mejor si se personalizan de acuerdo a las necesidades. <br />Ofrezca una mejor experiencia a los usuarios con sus propias plantillas de correo electrónico, decida qué notificaciones recibe y personalice las métricas de puntuación de riesgo de modo que se ajusten a las preferencias de la organización.|
|Paso 5. [Organice los datos de acuerdo a las necesidades](general-setup.md#IPtagsandRanges).|Configurar valores de configuración importantes|Recomendado|**Para crear etiquetas de dirección IP**<br /><br /> 1. Vaya a **Configuración** > **Etiquetas de dirección IP**.<br /><br /> 2. Elija (+) **Agregar intervalo de direcciones IP**.<br /><br /> 3. Escriba los **detalles**, la **ubicación**, las **etiquetas** y la **categoría** del intervalo IP.<br /><br /> 4. Elija **Crear**.<br /><br /> Ahora puede utilizar etiquetas IP al crear directivas y al filtrar y crear vistas de datos.<br /><br /> **Para crear vistas**<br /><br /> 1. Vaya a **Configuración** > **Cloud Discovery settings** (Configuración de Cloud Discovery).<br /><br /> 2. En **Vistas de datos**, elija (+) **Agregar vista de datos**.<br /><br /> 3. Siga los pasos de configuración.<br /><br /> 4. Elija **Crear**.<br /><br /> Ahora puede ver datos detectados según sus propias preferencias, por ejemplo, unidades de negocio o intervalos IP.<br /><br /> **Para agregar dominios**<br /><br /> 1. Vaya a **Configuración** > **Configuración general**.<br /><br /> 2. En **Detalles de la organización**, agregue los dominios internos de la organización.<br /><br /> 3. Elija **Guardar**.|**¿Por qué se deben configurar estos valores?**<br />Estos valores le ayudan a controlar mejor las características de la consola. Con las etiquetas IP es más fácil crear directivas adaptadas a las propias necesidades, filtrar con precisión los datos, etc. Use vistas de datos para agrupar los datos en categorías lógicas.|  

## <a name="see-also"></a>Consulte también

Consulte los aspectos básicos en [Introducción a Cloud App Security](getting-started-with-cloud-app-security.md).    
Para obtener soporte técnico, visite la página de [soporte técnico asistido de Cloud App Security](http://support.microsoft.com/oas/default.aspx?prid=16031).   
Los clientes Premier también pueden elegir Cloud App Security directamente desde el [Portal Premier](https://premier.microsoft.com/).   



<!--HONumber=Nov16_HO4-->


