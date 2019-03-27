---
title: 'Investigación de aplicaciones de OAuth de riesgo: Cloud App Security | Microsoft Docs'
description: En este artículo se proporciona información sobre cómo investigar las aplicaciones de riesgo de OAuth en Cloud App Security.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: barbkess
ms.date: 3/17/2019
ms.topic: tutorial
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 4118681e-362f-4b10-aa08-39691aa7800a
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 664e2ea3e6ce0414d3d55ca18a89e9bf9d889d94
ms.sourcegitcommit: fe4cd2174f6dc83811a2d484f079e8dfbac5d082
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/26/2019
ms.locfileid: "58477012"
---
# <a name="investigate-risky-oauth-apps"></a>Investigación de aplicaciones de riesgo de OAuth

*Se aplica a: Microsoft Cloud App Security*

OAuth es un estándar abierto para autenticación y autorización basadas en tokens. OAuth permite que la información de la cuenta de un usuario sea utilizada por servicios de terceros, sin exponer la contraseña del usuario. OAuth actúa como un intermediario en nombre del usuario, proporcionando al servicio un token de acceso que autoriza el uso compartido de información específica de la cuenta.

Muchas aplicaciones de terceros que puedan instalar los usuarios profesionales de su organización solicitan permiso para acceder a datos e información de usuario e iniciar sesión en nombre del usuario en otras aplicaciones de nube. Cuando los usuarios instalan estas aplicaciones, a menudo hacen clic en **Aceptar** sin revisar detenidamente los detalles en el mensaje, incluyendo la concesión de permisos a la aplicación. Aceptar los permisos de aplicaciones de terceros es un riesgo de seguridad potencial para su organización, por lo tanto, Microsoft Cloud App Security le ofrece la capacidad de investigar y supervisar los permisos de aplicaciones que sus usuarios otorgaron. Este artículo pretende ayudarle a investigar las aplicaciones de OAuth de su organización y se centra en las aplicaciones que tienen más probabilidades de ser sospechosas. 

Nuestro enfoque recomendado es investigar las aplicaciones utilizando las habilidades y la información proporcionadas en el portal de Cloud App Security para filtrar las aplicaciones con pocas posibilidades de ser de riesgo y centrarnos en las aplicaciones sospechosas. 

## <a name="how-to-investigate"></a>Procedimiento de investigación 

1.  En el portal, vaya a **Investigar** y, luego, a **Aplicaciones de OAuth**. Se recomienda consultar con uno de estos filtros: 
    - Seleccione **Nivel de permiso** de alta gravedad y **Uso comunitario** no común. Con este filtro puede centrarse en aplicaciones con un potencial de alto riesgo en las que los usuarios puedan haber subestimado el riesgo. 
    - En **Permisos** seleccione todas las opciones que son potencialmente riesgosas en un contexto específico, por ejemplo, puede seleccionar todos los filtros que proporciona permisos para acceso al correo electrónico, por ejemplo, **Acceso total a todos los buzones de correo** y revise la lista de aplicaciones para asegurarse de que todas necesitan realmente el acceso al correo. Esto le puede ayudar a investigar dentro de un contexto específico y a buscar aplicaciones que parecen legítimas, pero que contienen permisos innecesarios. Esas aplicaciones tiene más probabilidades de ser riesgosas. 
    ![Aplicación de OAuth riesgosa](./media/risky-oauth1.png) 
    - Use la **consulta** que le permite ver las **aplicaciones autorizadas por usuarios externos**. Con este filtro puede encontrar aplicaciones que quizás no estén alineadas con los estándares de seguridad de su empresa. 
2.  Una vez que filtre las aplicaciones, puede centrarse en las aplicaciones de las consultas que parecen ser legítimas, pero que podrían en realidad ser riesgosas, como: 
    - Aplicaciones que están **autorizadas por** un número reducido de usuarios. Si se centra en estas aplicaciones, puede buscar las aplicaciones riesgosas que fueron autorizadas por un usuario en peligro. 
    - Las aplicaciones con permisos que no se ajustan a la finalidad de la aplicación, como una aplicación de reloj con acceso total a todos los buzones. 
    - Haga clic en cada aplicación para abrir el cajón de aplicaciones y compruebe si la aplicación tiene un nombre, editor o sitio web sospechoso.  
    - Vea la lista de aplicaciones y céntrese en las que tengan una fecha de **Última autorización** que no sea reciente. Puede que estas aplicaciones ya no sean necesarias. 
    ![Aplicación de OAuth riesgosa](./media/risky-oauth2.png) 
 
3. Haga clic en la aplicación para abrir el cajón de aplicaciones y luego en el vínculo bajo **Actividades relacionadas**. Se abrirá la página Registro de actividad filtrada según las actividades que realiza la aplicación. Tenga en cuenta que algunas aplicaciones realizan actividades que se registran como si las hubiera hecho un usuario. Estas actividades se filtran automáticamente fuera de los resultados del registro de actividad. Para realizar una investigación más detallada con el registro de actividad, consulte [Registro de actividad](activity-filters.md). 
4. Si una aplicación le resulta sospechosa, le recomendamos investigar el nombre y el editor de la aplicación en distintas tiendas de aplicaciones. Céntrese en las aplicaciones siguientes, que pueden ser sospechosas: 
    - Aplicaciones con un número reducido de descargas.
    - Aplicaciones con una puntuación o clasificación baja o comentarios malos.
    - Aplicaciones con un editor o sitio web sospechoso.
    - Aplicaciones con una fecha de última actualización no reciente. Esto puede indicar que una aplicación ya no se admite. 
    - Aplicaciones con permisos irrelevantes. Esto podría indicar que una aplicación es riesgosa. 
5. Si la aplicación sigue siendo sospechosa, puede investigar la dirección URL, el editor y el nombre de la aplicación en línea. 


 
## <a name="next-steps"></a>Pasos siguientes
[Actividades diarias para proteger el entorno de nube](daily-activities-to-protect-your-cloud-environment.md) 

[Los clientes Premier también pueden crear una solicitud de soporte técnico directamente en el portal Premier.](https://premier.microsoft.com/) 
 
