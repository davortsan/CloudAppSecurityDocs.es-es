---
title: Búsqueda de informes integrados en desuso en Cloud App Security
description: En este artículo se ofrecen instrucciones para generar informes en desuso en Cloud App Security.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 12/10/2018
ms.topic: conceptual
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: a9660e5b-d5bd-4a32-8cb9-0de70af6f1e9
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: d0dbd2d945660ce57c832e8ff5678008268403a4
ms.sourcegitcommit: b86c3afd1093fbc825fec5ba4103e3a95f65758e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/10/2018
ms.locfileid: "53176793"
---
# <a name="how-to-find-built-in-deprecating-reports"></a>Búsqueda de informes integrados en desuso

*Se aplica a: Microsoft Cloud App Security*

Estamos actualizando la funcionalidad de informes integrados insertándola en otras partes del portal. La actualización de esta funcionalidad está en curso para mejorar los informes de Microsoft Cloud App Security.

## <a name="deprecating-reports"></a>Informes en desuso

Esta tabla le ayudará a ver la información proporcionada por los informes en desuso mediante otra funcionalidad de Cloud App Security:

| Tipo de informe | Nombre del informe integrado | Descripción | Nueva ubicación de los datos |
|----|----|----|----|
| Seguridad | Actividad | Este informe permite ver una lista con los países desde los que se originó una actividad en las aplicaciones en la nube. El informe muestra distintos parámetros que revelan el volumen de actividad de cada país, como el número de eventos, el número de usuarios y así sucesivamente. Ayuda a obtener una visión general de la distribución geográfica de los usuarios. | Esta información está disponible para aplicaciones, usuarios y direcciones IP concretos. Para cada aplicación, haga clic en la aplicación. Desde allí puede ver el mapa de actividad con todas las ubicaciones. Para cada usuario, haga clic en el usuario y luego, en el cajón de información de usuario. Pueden verse las ubicaciones usadas recientemente, así como el número de direcciones IP y de ISP que se usan. Para cada dirección IP, haga clic en la dirección IP específica. En el cajón de direcciones IP puede ver cuántos usuarios y administradores la usan. |
| Seguridad | Uso del explorador | Los ataques basados en el explorador se encuentran entre los vectores de ataque más comunes. Los proveedores invierten muchos recursos en proteger el software de exploración, para lo que crean un mecanismo de actualización eficaz para publicar actualizaciones en los puntos de conexión. El empleo de exploradores en desuso mucho después de la fecha de vencimiento de su actualización los convierte en un objetivo fácil para los actores de amenazas que usan los kits de vulnerabilidad de seguridad disponibles. Esta funcionalidad permite obtener una lista de los exploradores obsoletos que los usuarios con acceso a las aplicaciones en la nube usaron en los últimos siete días. También permite saber si ha sido un robot el que ha usado el explorador obsoleto. | Vaya a **Registro de actividad** y abra **Filtros avanzados**. Después, establezca el filtro de **Etiqueta de agente de usuario** igual a **Explorador obsoleto** y **Sistema operativo obsoleto** para ver una lista de los exploradores y los SO obsoletos en uso. |
| Seguridad | Direcciones IP: cuentas con privilegios| En este informe se muestran las direcciones IP que usaron los dispositivos realizando actividades administrativas durante los últimos siete días en el entorno de nube protegido por Cloud App Security. La fecha se basa en los registros de auditoría que acumula Cloud App Security. Las direcciones IP están asociadas con una ubicación geográfica y una organización de origen. Esta información permite identificar las direcciones IP sospechosas que se conectan con las aplicaciones protegidas. Para ver los registros de auditoría de cada dirección IP, haga clic en ella. | Haga clic en un usuario concreto. Después, en el cajón de información de usuario, se pueden ver las ubicaciones usadas recientemente, así como el número de direcciones IP y de ISP que se usan. |
| Administración de usuarios | Cuentas inactivas | Las cuentas inactivas son aquellas que tienen acceso a la instancia en la nube, pero no han realizado ningún evento en los últimos 60 días. La falta de acción sugiere que estas cuentas ya no están activas y que deben suspenderse para evitar que en el futuro tengan acceso a ellas agentes de amenaza o empleados que abandonan la organización. Si se sigue esta recomendación no solo mejora la seguridad, sino que se reducen los costos operativos. | Vaya a la página **Usuarios y cuentas** y use el filtro **Visto por última vez** para generar una lista de todos los usuarios que no han realizado ninguna actividad recientemente. |
| Administración de usuarios | Usuarios con privilegios | En este informe se muestran los usuarios de los últimos 7 días que tienen privilegios elevados en las aplicaciones corporativas, como los administradores. Las cuentas con privilegios como estas son el vector de ataque preferido de los actores de amenazas, ya que les permiten tener acceso a información corporativa y a la configuración de red. El hecho de que haya cuentas con privilegios que no se usaron recientemente puede indicar que una empresa no es consciente de la importancia de la seguridad de TI, lo que potencialmente prepara el camino para una oleada de infracciones de datos. Puede investigar en detalle el uso de los privilegios de usuario elevados mediante el registro de auditoría y plantearse la posibilidad de revocar los privilegios cuando ya no sean necesarios. | Vaya a la página **Usuarios y cuentas** y utilice el filtro **Grupos** para generar una lista de los usuarios con privilegios que pertenecen al grupo de administradores. |
| Administración de usuarios | Cuentas con privilegios especiales | Salesforce tiene varios tipos de cuentas con privilegios, incluidos Modificar todos los datos, Ver todos los datos y Administrar todos los usuarios. Dado que las cuentas con privilegios como estas son el vector de ataque preferido de los actores de amenazas, ya que les permiten tener acceso a la información corporativa y a las configuraciones, resulta útil ver una lista de las cuentas con privilegios. | Vaya a Salesforce. Haga clic en la pestaña **Cuentas con privilegios especiales**. |
| Administración de datos | Información general sobre el uso compartido de datos | En este informe se muestra el número de archivos almacenados en las aplicaciones en la nube, divididos en función de los permisos de acceso. El uso compartido se ha convertido en un proceso fácil con las aplicaciones en la nube debido a la facilidad de acceso y la ubicuidad. Los archivos que no se comparten con nadie más que el propietario se denominan archivos privados. Si se comparte un archivo, Cloud App Security distingue cuatro tipos de estados: <br> - Un archivo compartido públicamente (web) es aquel al que se puede tener acceso sin autenticación, incluso a través de los resultados de un motor de búsqueda.<br> - Un archivo compartido públicamente es aquel al que se puede tener acceso sin autenticación a través de un enlace.<br> - Un archivo compartido externamente es aquel al que pueden tener acceso usuarios ajenos a la organización después de autenticarse en la aplicación en la nube.<br> - Un archivo compartido internamente es aquel al que pueden tener acceso todos o algunos de los usuarios de la organización.|Vaya a **Archivos**. En la esquina superior derecha, haga clic en los tres puntos y, en **Informes de administración de datos**, seleccione **Información general sobre el uso compartido de datos**. |
| Administración de datos | Uso compartido externo por dominio | En este informe se muestran los dominios con los que los empleados comparten archivos corporativos. En el informe se indica para cada dominio qué usuarios corporativos comparten archivos con qué dominio, qué archivos se comparten y quiénes son los colaboradores con los que se comparten los archivos. Se recomienda que administre el uso compartido con estos dominios a través de la pestaña Archivos de la página de cada aplicación en cuestión. | Vaya a **Archivos**. En la esquina superior derecha, haga clic en los tres puntos y, en **Informes de administración de datos**, seleccione **Uso compartido externo por dominio**. |
| Administración de datos | Propietarios de archivos compartidos | Se muestran los usuarios que comparten archivos corporativos con el exterior. Los archivos compartidos externamente se comparten con colaboradores externos específicos. Los archivos compartidos públicamente son accesibles para cualquier usuario de Internet, a través de un vínculo privado, y solo los pueden encontrar aquellos que están expuestos explícitamente al vínculo. Los archivos compartidos públicamente (Internet) son accesibles para cualquier usuario de Internet, incluso a través de los resultados de un motor de búsqueda. Si detecta usuarios que comparten un número excesivo de archivos, es recomendable que investigue la naturaleza de este exceso de permisos de uso compartido mediante la pestaña Archivos y que se ponga en contacto con dichos usuarios para comprender mejor este uso compartido externo. | Vaya a **Archivos**. En la esquina superior derecha, haga clic en los tres puntos y, en **Informes de administración de datos**, seleccione **Propietarios de archivos compartidos**. |



  
## <a name="next-steps"></a>Pasos siguientes 
[Control](control.md)   

[Los clientes Premier también pueden crear una solicitud de soporte técnico directamente en el portal Premier.](https://premier.microsoft.com/)  
  
  