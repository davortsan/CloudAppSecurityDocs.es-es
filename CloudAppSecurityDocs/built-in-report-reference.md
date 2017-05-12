---
title: "Descripción de los campos de los informes integrados en Cloud App Security | Microsoft Docs"
description: En este tema se proporciona una lista de los informes integrados y sus usos.
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 3/1/2017
ms.topic: article
ms.prod: 
ms.app: cloud-app-security
ms.technology: 
ms.assetid: 588b3639-f748-45a6-bc4b-a6ee47c1865e
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: d159cb95c9f0468e8c658c13586d07f0f20049ef
ms.sourcegitcommit: 945cb3c047ae1bfc05be20cc7798c43005b27c9b
ms.translationtype: HT
ms.contentlocale: es-ES
---
# <a name="built-in-report-reference"></a>Referencia de informes integrados

CAS proporciona una lista completa de los informes integrados de fábrica que le permiten extraer información y supervisar el modo en que las personas usan la nube. Puede utilizar los filtros de cada informe para personalizar el informe y exportarlos para su comodidad.


En la tabla siguiente se proporciona una lista de informes integrados y los tipos de eventos que puede supervisar mediante dichos informes.  
  
## <a name="built-in-report-list"></a>Lista de informes integrados  
  
|Tipo de informe|Nombre del informe integrado|Descripción|  
|-----------------|---------------------------|-----------------|  
|Seguridad|Actividad por ubicación|En este informe se enumeran los países en los que se originó actividad en las aplicaciones de nube, así como diversos parámetros que representan el volumen de actividad de cada país, como el número de eventos, el número de usuarios, etc. Úselo para obtener una visión general de la distribución geográfica de los usuarios.|  
|Seguridad|Uso del explorador|Los ataques basados en el explorador se encuentran entre los vectores de ataque más comunes. Los proveedores invierten muchos recursos en proteger el software de exploración, para lo que crean un mecanismo de actualización eficaz para distribuir actualizaciones a los extremos. El empleo de exploradores en desuso mucho después de la fecha de vencimiento de su actualización los convierte en un objetivo fácil para los actores de amenazas que usan los kits de vulnerabilidad de seguridad disponibles. En este informe se enumeran los exploradores obsoletos que los usuarios que tienen acceso a las aplicaciones en la nube usaron en los últimos 7 días. El informe también permite saber si ha sido un robot el que ha usado el explorador obsoleto.|  
|Seguridad|Direcciones IP: cuentas con privilegios|En este informe se muestran las direcciones IP que los dispositivos usan para realizar actividades administrativas durante los últimos 7 días en el entorno de nube protegido por Cloud App Security. El informe se basa en los registros de auditoría que acumula Cloud App Security. Las direcciones IP suelen estar asociadas con una ubicación geográfica y una organización de origen. Use este informe para identificar las direcciones IP sospechosas que se conectan con las aplicaciones protegidas. Para ver los registros de auditoría de cada dirección IP, haga clic en ella.|  
|Administración de usuarios|Cuentas inactivas|Las cuentas inactivas son aquellas que tienen acceso a la instancia en la nube, pero no han realizado ningún evento en los últimos 60 días. Esto sugiere que estas cuentas ya no están activas y que deben suspenderse para evitar que en el futuro tengan acceso a ellas agentes de amenaza o empleados que abandonan la organización. Si se sigue esta recomendación no solo mejora la seguridad, sino que se reducen los costos operativos.|  
|Administración de usuarios|Usuarios con privilegios|En este informe se muestran los usuarios de los últimos 7 días que tienen privilegios elevados en las aplicaciones corporativas, como los administradores. Las cuentas con privilegios como estas son el vector de ataque preferido de los actores de amenazas, ya que les permiten tener acceso a información corporativa y a la configuración de red. El hecho de que haya cuentas con privilegios que no se usaron recientemente puede indicar que una empresa no es consciente de la importancia de la seguridad de TI, lo que potencialmente prepara el camino para una oleada de infracciones de datos. Puede investigar en detalle el uso de los privilegios de usuario elevados mediante el registro de auditoría y considerar la posibilidad de revocar los privilegios cuando ya no sean necesarios.|  
|Administración de usuarios|Cuentas con privilegios especiales|Salesforce tiene varios tipos de cuentas con privilegios, incluidos Modificar todos los datos, Ver todos los datos y Administrar todos los usuarios. Las cuentas con privilegios como estas son el vector de ataque preferido de los actores de amenazas, ya que les permiten tener acceso a información corporativa y a la configuración.|  
|Administración de datos|Información general sobre el uso compartido de datos|En este informe se muestra el número de archivos almacenados en las aplicaciones en la nube, divididos en función de los permisos de acceso. El uso compartido se ha convertido en un proceso muy fácil con las aplicaciones en la nube debido a la facilidad de acceso y la ubicuidad.<br /><br /> Los archivos que no se comparten con nadie más que el propietario se denominan archivos privados. Si se comparte un archivo, Cloud App Security distingue cuatro tipos de estados:<br /><br /> Un archivo compartido públicamente (web) es aquel al que se puede tener acceso sin autenticación, incluso a través de los resultados de un motor de búsqueda.<br /><br /> Un archivo compartido públicamente es aquel al que se puede tener acceso sin autenticación a través de un enlace.<br /><br /> Un archivo compartido externamente es aquel al que pueden tener acceso usuarios ajenos a la organización después de autenticarse en la aplicación en la nube.<br /><br /> Un archivo compartido internamente es aquel al que pueden tener acceso todos o algunos de los usuarios de la organización.|  
|Administración de datos|Uso compartido externo por dominio|En este informe se muestran los dominios con los que los empleados comparten archivos corporativos. En el informe se indica para cada dominio qué usuarios corporativos comparten archivos con qué dominio, qué archivos se comparten y quiénes son los colaboradores con los que se comparten los archivos. Se recomienda que administre el uso compartido con estos dominios a través de la pestaña Archivos de la página de cada aplicación en cuestión.|  
|Administración de datos|Propietarios de archivos compartidos|En este informe se muestran los usuarios que comparten archivos corporativos con el exterior. Los archivos compartidos externamente se comparten con colaboradores externos específicos. Los archivos compartidos públicamente son accesibles para cualquier usuario de Internet, a través de un vínculo privado, y solo los pueden encontrar aquellos que están expuestos explícitamente al vínculo. Los archivos compartidos públicamente (Internet) son accesibles para cualquier usuario de Internet, incluso a través de los resultados de un motor de búsqueda.  Si detecta usuarios que comparten una cantidad excesiva de archivos, es recomendable que investigue la naturaleza de este exceso de permisos de uso compartido mediante la pestaña Archivos y que se ponga en contacto con dichos usuarios para comprender mejor este uso compartido externo.|  
  
## <a name="see-also"></a>Consulte también  
[Control](control.md)   
[Para obtener soporte técnico, visite la página de soporte técnico asistido de Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Los clientes Premier también pueden elegir Cloud App Security directamente desde el Portal Premier.](https://premier.microsoft.com/)  
  
  