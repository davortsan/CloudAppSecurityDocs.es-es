---
title: Conectar aplicaciones para obtener una mayor visibilidad y control con Cloud App Security | Microsoft Docs
description: En este tema se describe el proceso para conectar aplicaciones con las aplicaciones en la nube de la organización mediante conectores de API.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 1/15/2018
ms.topic: get-started-article
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 3b15ba46-ac9c-4b4f-aefc-137edc903bc1
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: c14ba598a593dd8711151eb58e0eab75d0ea8791
ms.sourcegitcommit: 716699286f8ebb33327eac28ca9b7bf9742daf32
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2018
---
# <a name="connect-apps"></a>Conectar aplicaciones 
Los conectores de aplicaciones aprovechan las API de los proveedores de aplicaciones para permitir mediante Cloud App Security una mayor visibilidad y control de las aplicaciones a las que se conecta.  
  
Cloud App Security aprovecha las API que proporciona el proveedor de nube. Cada servicio tiene su propio marco de trabajo y limitaciones de API. Cloud App Security funciona con los servicios para optimizar el uso de las API y garantizar el máximo rendimiento. Teniendo en cuenta las diferentes limitaciones que los servicios imponen a las API (como la limitación de peticiones, los límites de API, las ventanas de API dinámicas de tiempo cambiante, etc.), los motores de Cloud App Security aprovechan la capacidad permitida. Algunas operaciones, como el análisis de todos los archivos del inquilino, requieren numerosas API y, por lo tanto, se reparten a lo largo de un período de tiempo mayor. Tenga en cuenta que algunas directivas pueden ejecutarse durante varias horas o varios días.  
  
## <a name="multi-instance-support"></a>Compatibilidad con varias instancias

Cloud App Security admite varias instancias de la misma aplicación conectada. Si tiene varias instancias de, por ejemplo, Salesforce (una para venta y otra para marketing) podrá conectarlas a Cloud App Security y administrarlas desde la misma consola para crear directivas granulares y una investigación más a fondo. Esta compatibilidad solo se aplica a las aplicaciones conectadas a API, no a aplicaciones conectadas por proxy ni detectadas por Cloud App Security.

## <a name="how-it-works"></a>Cómo funciona  
Cloud App Security se implementa con privilegios de administrador del sistema para permitir el acceso total a todos los objetos del entorno.  
  
El flujo del Conector de aplicaciones es como sigue:
1. Cloud App Security analiza y guarda los permisos de autenticación.
2.  Cloud App Security solicita la lista de usuarios. La primera vez que se realiza esto, el análisis puede tardar algún tiempo en completarse. Una vez terminado el análisis de los usuarios, Cloud App Security pasa a las actividades y los archivos. En cuanto se inicia el análisis, algunas actividades estarán disponibles en Cloud App Security. 
4. Una vez completada solicitud del usuario, Cloud App Security analiza periódicamente los usuarios, los grupos, las actividades y los archivos. Todas las actividades estarán disponibles tras el primer análisis completo. 
 
Esto puede tardar algún tiempo, dependiendo del tamaño de los inquilinos, el número de usuarios y el tamaño y número de archivos que deben analizarse. 
 
En función de la aplicación a la que se conecte (consulte la tabla siguiente), la conexión de API permite lo siguiente:  
  
-   **Información de cuenta:**  
  
     Visibilidad de los usuarios, cuentas, información de perfil, estado (suspendido, activo, deshabilitado), grupos y privilegios.  
  
-   **Traza de auditoría:**  
  
     Visibilidad de las actividades del usuario, las actividades del administrador y la actividad de inicio de sesión.  
  
-   **Examen de datos:**  
  
     Examen de datos no estructurados mediante dos procesos: periódicamente (cada 12 horas) y en tiempo real (se desencadena cada vez que se detecta un cambio).  
  
-   **Permisos de aplicación:**  
  
     Visibilidad de los tokens emitidos y sus permisos.  
  
-   **Regulación de cuenta:**  
  
     Capacidad de suspender usuarios, revocar contraseñas, etc.  
  
-   **Regulación de datos:**  
  
     Capacidad de poner archivos en cuarentena, incluidos los de la Papelera, y sobrescribir archivos.  
  
-   **Regulación de permisos de aplicación:**  
  
     Capacidad de eliminar tokens.  
  
En la siguiente tabla se enumeran, por aplicación en la nube, qué capacidades son compatibles con los conectores de aplicaciones:  

> [!div class="mx-tableFixed"]
||**Office 365**|**Box**|**Okta**|**G Suite**|**Service Now**|**Salesforce**|**Dropbox**|**AWS**|  
|-|-|-|-|-|-|-|-|-|  
|**Cuentas de lista**|✔|✔|✔|✔|✔|✔|✔|✔|  
|**Grupo**|✔|✔|✔|✔|✔|✔|✔|✔|  
|**Privilegios**|✔|✔|No es compatible con el proveedor|✔|✔|✔|✔||  
|**Regulación de usuario**|✔|✔||✔|Próximamente|Próximamente|Próximamente||  
|**Actividad de inicio de sesión**|✔|✔|✔|✔|✔|✔|✔|✔|  
|**Actividad del usuario**|✔*|✔|✔|✔ (requiere Google Unlimited)|Parcial|Compatible con Salesforce Shield|✔|No disponible|  
|**Actividad administrativa**|✔|✔|✔|✔|Parcial|✔|✔|✔|  
|**Examen periódico de archivos**|✔|✔|No disponible|✔|✔|✔|✔|No disponible|  
|**Examen de archivos prácticamente en tiempo real**|✔|✔|No disponible|✔ (requiere Google Unlimited)|||Próximamente||  
|**Control de uso compartido**|✔|✔|No disponible|✔|No disponible||✔||  
|**Cuarentena**|✔|✔|No disponible|Próximamente|||Próximamente||  
|**Ver permisos de aplicación**|✔|No es compatible con el proveedor|No disponible|✔||✔|No es compatible con el proveedor||  
|**Revocar permisos de aplicación**|✔||No disponible|✔||✔|No disponible||  
|**Aplicación de etiquetas de Azure Information Protection**|✔|✔|||||||  
  
## <a name="prerequisites"></a>Requisitos previos  

- En el caso de algunas aplicaciones, puede que sea necesario agregar las direcciones IP a la lista de permitidos para habilitar Cloud App Security de modo que recopile registros y proporcione acceso a la consola de Cloud App Security. Para obtener más información, consulte [Requisitos de red](network-requirements.md).

- Se recomienda crear una cuenta de servicio de administración dedicada a Cloud App Security por cada aplicación que quiera conectar con la integración de la API de Cloud App Security.  
  
> [!NOTE]  
>  Para obtener actualizaciones cuando las direcciones URL y las direcciones IP cambien, suscríbase al RSS como se explica en: [URL de Office 365 e intervalos de direcciones IP](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2).  
  
Para usar los conectores de aplicaciones, debe asegurarse de que tiene lo siguiente para cada aplicación específica:  
  
|Aplicación|Tipo de licencia|Usuario|  
|---------|------------------|----------|  
|Cuadro|Enterprise|Se recomienda encarecidamente que se conecte a Box como administrador. Si se conecta como coadministrador, la visibilidad de los datos será parcial. En caso de que se conecte como coadministrador, asegúrese de seleccionar todos los permisos.|  
|G Suite|G Suite Unlimited (preferido)<br /><br /> G Suite Enterprise (como mínimo)|Superadministrador|  
|Office 365||Administrador global|  
|AWS||Usuario creado recientemente|  
|Dropbox|Empresa/Enterprise|Administración|  
|Okta|Enterprise (no versión de prueba)|Administración|  
|Exchange||Administrador global|  
|ServiceNow|Eureka o versión posterior|Administrador + rol de API de REST|  
|Salesforce||Administración|  
  

**ExpressRoute**  
  
Cloud App Security se ha implementado en Azure y está totalmente integrado con [ExpressRoute](https://azure.microsoft.com/documentation/articles/expressroute-introduction/). Todas las interacciones con las aplicaciones de Cloud App Security y el tráfico enviado a Cloud App Security, incluida la carga de registros de detección, se enrutan a través del **emparejamiento público** de ExpressRoute para mejorar la latencia, el rendimiento y la seguridad. No hay ningún paso de configuración necesario en el lado cliente.  
Para obtener más información sobre el emparejamiento público, vea [Circuitos ExpressRoute y dominios de enrutamiento](https://azure.microsoft.com/documentation/articles/expressroute-circuit-peerings/).  
  
## <a name="see-also"></a>Consulte también  
[Actividades diarias para proteger el entorno de nube](daily-activities-to-protect-your-cloud-environment.md)   

[Los clientes Premier también pueden elegir Cloud App Security directamente desde el Portal Premier.](https://premier.microsoft.com/)  
  

## <a name="check-out-this-video"></a>Eche un vistazo a este vídeo.
[Microsoft Cloud App Security: API de REST y tokens](https://channel9.msdn.com/Shows/Microsoft-Security/Microsoft-Cloud-App-Security--REST-APIs-and-Tokens)  
   