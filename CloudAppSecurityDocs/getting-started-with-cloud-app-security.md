---
title: "Introducción a Cloud App Security | Microsoft Docs"
description: En este tema se describe el proceso para que Cloud App Security entre en funcionamiento.
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 10/15/2016
ms.topic: get-started-article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: cf040b18-93d1-41e8-a26a-647c56afb00f
ms.reviewer: reutam
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: ed4ea71b24767d3602d40894d1cbac7447bcd8a2
ms.openlocfilehash: 8b454edde557c408b644c9bff6f7bf6136ba9819


---

# <a name="getting-started-with-cloud-app-security"></a>Introducción a Cloud App Security
Cloud App Security ayuda a los clientes a aprovechar las ventajas de las aplicaciones en la nube sin perder el control gracias a una visibilidad mejorada de la actividad y a una mayor protección de los datos críticos de la empresa.  Esta documentación le guiará por los siguientes pasos para trabajar con Cloud App Security.  
  
Para usar el producto, la organización debe tener una licencia de Cloud App Security. Para obtener más información, vea [How to buy Cloud App Security](https://www.microsoft.com/server-cloud/products/cloud-app-security/default.aspx) (Cómo comprar Cloud App Security) y lea la sección [Licensing resources](https://www.microsoft.com/server-cloud/products/cloud-app-security/default.aspx) (Recursos de licencia).  
  
>[!NOTE]
>No es necesaria una licencia de Office 365 para Cloud App Security.  
  
## <a name="get-started-quickly-with-cloud-app-security"></a>Inicio rápido de Cloud App Security  
  
|Haga lo siguiente:|Tarea|¿Requerido?|Cómo:|Descripción|  
|-------------------------|----------|---------------|-------------|-----------------|  
|PASO 1. [Configure Cloud Discovery](set-up-cloud-discovery.md).|Cargar registros de tráfico|Requerido|**Crear un informe continuo de Cloud Discovery**<br /><br /> 1.   Vaya a **Configuración** -> **Cloud Discovery settings** (Configuración de Cloud Discovery).<br /><br /> 2.    Haga clic en **Cargar registros automáticamente**.<br /><br /> 3.   Agregue los orígenes de datos en la pestaña **Orígenes de datos**.<br /><br /> 4.    Configure el recopilador de registros en la pestaña **Recopiladores de registros**.<br /><br /> Crear un informe de instantáneas de Cloud Discovery<br /><br /> 1.    Vaya a **Detectar** -> **Crear nuevo informe de instantáneas** y siga los pasos.|**¿Por qué se deben configurar los informes de Cloud Discovery?** La visibilidad de la TI en la sombra de la organización es crítica.  <br />Después de analizar los registros, podrá detectar fácilmente qué aplicaciones en la nube se usan, qué usuarios lo hacen y en qué dispositivos.|  
|PASO 2. [Habilite la visibilidad, la protección y las acciones de gobierno instantáneas para las aplicaciones](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md).|Conectar aplicaciones|Requerido|1.   Vaya a **Configuración** -> **Aplicaciones sancionadas**.<br /><br /> 2. Haga clic en **Conectar aplicación** y seleccione una aplicación.<br /><br /> 3. Siga los pasos de configuración para conectar la aplicación.|**¿Por qué conectar una aplicación?**<br /><br /> Solo después de conectar una aplicación podrá obtener una mayor visibilidad para investigar las actividades, los archivos y las cuentas del entorno de nube de las aplicaciones en la nube.|  
|PASO 3. [Controle las aplicaciones en la nube con directivas](control-cloud-apps-with-policies.md).|Crear las directivas|Requerido|**Crear las directivas**<br /><br /> 1.  Vaya a **Control** -> **Plantillas**.<br /><br /> 2.    Seleccione una plantilla de directiva de la lista y haga clic en (+) **Crear directiva**.<br /><br /> 3.  Personalice la directiva de acuerdo a sus necesidades (seleccione filtros, acciones y otras configuraciones) y haga clic en **Crear**.<br /><br /> 4.    En la pestaña **Directivas**, haga clic en la directiva que ha creado para ver las coincidencias relevantes (actividades, archivos, alertas, etc.).<br /><br /> Sugerencia: Cree una directiva para cada **Categoría de riesgo** a fin de cubrir todos los escenarios de seguridad del entorno de nube.|**¿Cómo pueden las directivas ayudar a la organización?**<br /><br /> Las directivas proporcionan las herramientas necesarias para supervisar tendencias, ver amenazas de seguridad y generar alertas e informes personalizados. Con las directivas se pueden crear distintas acciones de gobierno, DLP y controles de uso compartido de archivos.|  
|PASO 4. [Personalice la experiencia](general-setup.md#Adallom_mailsettings).|Agregar detalles de la organización|Recomendado|**Especificar configuración de correo electrónico**<br /><br /> 1. Vaya a **Configuración** -> **Configuración de correo**.<br /><br /> 2.   En **Identidad del emisor de correo electrónico**, escriba las direcciones de correo electrónico y el nombre para mostrar.<br /><br /> 3. En **Diseño del correo electrónico**, cargue la plantilla de correo electrónico de la organización.<br /><br /> **Establecer notificaciones de administrador**<br /><br /> 1.    Haga clic en el nombre de usuario en la barra de navegación y vaya a **Configuración de usuario**.<br /><br /> 2.    En **Notificaciones**, configure los métodos que quiere establecer para las notificaciones del sistema.<br /><br /> 3.  Haga clic en **Guardar**.<br /><br /> **Personalizar las métricas de puntuación**<br /><br /> 1.  Vaya a **Configuración** -> **Cloud Discovery settings** (Configuración de Cloud Discovery).<br /><br /> 2.    En **Configurar métrica de puntuación**, configure la importancia de los distintos valores de riesgo.<br /><br /> 3.    Haga clic en **Guardar**.<br /><br /> Ahora las puntuaciones de riesgo otorgadas a las aplicaciones detectadas están configuradas exactamente según las necesidades y las prioridades de la organización.|**¿Por qué personalizar el entorno?**<br /><br /> Algunas características funcionan mejor si se personalizan de acuerdo a las necesidades.  <br />Ofrezca una mejor experiencia a los usuarios con sus propias plantillas de correo electrónico, decida qué notificaciones recibe y personalice las métricas de puntuación de riesgo de modo que se ajusten a las preferencias de la organización.|  
|PASO 5. [Organice los datos de acuerdo a las necesidades](general-setup.md#IPtagsandRanges).|Configurar valores de configuración importantes|Recomendado|**Crear etiquetas de dirección IP**<br /><br /> 1.   Vaya a **Configuración** -> **Etiquetas de dirección IP**.<br /><br /> 2. Haga clic en (+) **Agregar intervalo de direcciones IP**.<br /><br /> 3.    Escriba los **detalles**, la **ubicación**, las **etiquetas** y la **categoría** del intervalo IP.<br /><br /> 4. Haga clic en **Crear**.<br /><br /> Ahora puede usar etiquetas IP al crear directivas, al filtrar y al crear vistas de datos.<br /><br /> **Crear vistas**<br /><br /> 1.  Vaya a **Configuración** -> **Cloud Discovery settings** (Configuración de Cloud Discovery).<br /><br /> 2.    En **Vistas de datos**, haga clic en (+) **Add data view** (Agregar vista de datos).<br /><br /> 3.  Siga los pasos de configuración.<br /><br /> 4.  Haga clic en **Crear**.<br /><br /> Ahora puede ver datos detectados según sus propias preferencias, por ejemplo, unidades de negocio o intervalos IP.<br /><br /> **Agregar dominios**<br /><br /> 1.    Vaya a **Configuración** -> **Configuración general**.<br /><br /> 2.    En **Detalles de la organización**, agregue los dominios internos de la organización.<br /><br /> 3. Haga clic en **Guardar**.|**¿Por qué se deben configurar estos valores?**<br /><br /> Esta configuración se traduce en un control mejor y más sencillo de distintas características en la consola. Con las etiquetas IP es más fácil crear directivas adaptadas a las propias necesidades, filtrar con precisión los datos, etc. Use vistas de datos para agrupar los datos en categorías lógicas.|  
  
## <a name="see-also"></a>Consulte también  
[Configuración general](general-setup.md)   
[Para obtener soporte técnico, visite la página de soporte técnico asistido de Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Los clientes Premier también pueden elegir Cloud App Security directamente desde el Portal Premier.](https://premier.microsoft.com/)  
  
  


<!--HONumber=Oct16_HO4-->


