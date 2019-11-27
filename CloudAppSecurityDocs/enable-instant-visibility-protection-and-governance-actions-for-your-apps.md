---
title: 'Conexión de aplicaciones para obtener visibilidad y control: Cloud App Security | Microsoft Docs'
description: En este artículo se describe el proceso para conectar aplicaciones con las aplicaciones en la nube de la organización mediante conectores de API.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 11/12/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: e22b7d7f1b59c49470426080bf822fa070a1af6d
ms.sourcegitcommit: 094bb42a198fe733cfd3aec79d74487672846dfa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/24/2019
ms.locfileid: "74458177"
---
# <a name="connect-apps"></a>Conectar aplicaciones

*Se aplica a: Microsoft Cloud App Security*

Los conectores de aplicaciones usan las API de los proveedores de aplicaciones para permitir mediante Microsoft Cloud App Security una mayor visibilidad y control de las aplicaciones a las que se conecta.

Microsoft Cloud App Security usa las API proporcionadas por el proveedor de nube. Cada servicio tiene su propio marco de trabajo y limitaciones de API como limitación, límites de API, ventanas de API de tiempo cambiante dinámicas, etc. Microsoft Cloud App Security funciona con los servicios para optimizar el uso de las API y proporcionar el máximo rendimiento. Los motores de Cloud App Security usan la capacidad permitida teniendo en cuenta las diferentes limitaciones que los servicios imponen a las API. Algunas operaciones, como el análisis de todos los archivos del inquilino, requieren numerosas API y, por tanto, se reparten a lo largo de un período de tiempo mayor. Tengan en cuenta que algunas directivas pueden ejecutarse durante varias horas o varios días.

## <a name="multi-instance-support"></a>Compatibilidad con varias instancias

Cloud App Security admite varias instancias de la misma aplicación conectada. Por ejemplo, si tiene más de una instancia de Salesforce (una para venta y otra para marketing) puede conectarlas con Cloud App Security. Puede administrar las distintas instancias desde la misma consola para crear directivas pormenorizadas y una investigación más exhaustiva. Esta compatibilidad solo se aplica a las aplicaciones conectadas a API, no a aplicaciones conectadas por proxy ni detectadas por Cloud App Security.

> [!NOTE]
> No se admiten instancias múltiples de Office 365 y Azure.

## <a name="how-it-works"></a>Cómo funciona

Cloud App Security se implementa con privilegios de administrador del sistema para permitir el acceso total a todos los objetos del entorno.

El flujo del Conector de aplicaciones es como sigue:

1. Cloud App Security analiza y guarda los permisos de autenticación.
2. Cloud App Security solicita la lista de usuarios. La primera vez que se realiza la petición, el análisis puede tardar algún tiempo en completarse. Una vez terminado el análisis de los usuarios, Cloud App Security pasa a las actividades y los archivos. En cuanto se inicia el análisis, algunas actividades estarán disponibles en Cloud App Security.
3. Una vez completada la solicitud del usuario, Cloud App Security analiza periódicamente los usuarios, los grupos, las actividades y los archivos. Todas las actividades estarán disponibles tras el primer análisis completo.

Esta conexión puede tardar algún tiempo, en función del tamaño de los inquilinos, el número de usuarios y el tamaño y número de archivos que deben analizarse.

En función de la aplicación a la que se conecte, la conexión de API habilita los siguientes elementos:

- **Información de cuenta**: ofrece visibilidad sobre los usuarios, las cuentas, la información de perfil, el estado (suspendido, activo, deshabilitado), los grupos y los privilegios.

- **Pista de auditoría**: ofrece visibilidad de las actividades del usuario, las actividades del administrador y la actividad de inicio de sesión.

- **Análisis de datos**: examen de datos no estructurados mediante dos procesos, periódicamente (cada 12 horas) y en tiempo real (se desencadena cada vez que se detecta un cambio).

- **Permisos de aplicación**: ofrece visibilidad de los tokens emitidos y sus permisos.

- **Gobernanza de cuenta**: permite suspender usuarios, revocar contraseñas, etc.

- **Gobernanza de datos**: permite poner archivos en cuarentena, incluidos los de la Papelera, y sobrescribir archivos.

- **Regulación de permisos de aplicación**: permite quitar los tokens.

En la siguiente tabla se enumeran, por aplicación en la nube, qué capacidades son compatibles con los conectores de aplicaciones:

> [!div class="mx-tableFixed"]
>
> | | AWS | Cuadro | Dropbox | GCP | G Suite | Office 365 | Okta | Servicio ahora | Salesforce | Webex | Workday |
> |-|-|-|-|-|-|-|-|-|-|-|-|
> | **Cuentas de lista** | ✔ | ✔ | ✔ | Conexión de asunto G Suite | ✔ | ✔ | ✔ | ✔ | ✔ | ✔ | ✔ |
> | **Lista de grupos** | ✔ | ✔ | ✔ | Conexión de asunto G Suite | ✔ | ✔ | ✔ | ✔ | ✔ | | No es compatible con el proveedor |
> | **Lista de privilegios** | | ✔ | ✔ | Conexión de asunto G Suite | ✔ | ✔ | No es compatible con el proveedor | ✔ | ✔ | ✔ | No pported por el proveedor |
> | **Regulación de usuario** | | ✔ | Próximamente | Conexión de asunto G Suite | ✔ | ✔ | | Próximamente | ✔ | Próximamente | t compatible con el proveedor |
> | **Actividad de inicio de sesión** | ✔ | ✔ | ✔ | Conexión de asunto G Suite | ✔ | ✔ | ✔ | ✔ | ✔ | ✔ | ✔ |
> | **Actividad del usuario** | No aplicable | ✔ | ✔ | ✔ | ✔ - requiere Google Business o Enterprise | ✔ | ✔ | Parcial | Compatible con lesforce Shield | ✔ | ✔ |
> | **Actividad administrativa** | ✔ | ✔ | ✔ | ✔ | ✔ | ✔ | ✔ | Parcial | ✔ | ✔ | No es compatible con el proveedor |
> | **DLP: examen periódico** | | ✔ | Próximamente | No aplicable | ✔ | ✔ | No aplicable | | | | No compatible con ovider |
> | **Análisis de DLP casi en tiempo real** | | ✔ | ✔ | No aplicable | ✔: requiere Google Business Enterprise | ✔ | No aplicable | ✔ | ✔ | ✔ | No es compatible con el proveedor |
> | **Control de uso compartido** | ✔ | ✔ | ✔ | No aplicable | ✔ | ✔ | No aplicable | No aplicable | | ✔ | No compatible con ovider |
> | **Regulación de archivos** | ✔ | ✔ | ✔ | No aplicable | ✔ | ✔ | No aplicable | | ✔ | | No es compatible con el proveedor |
> | **Ver permisos de aplicación** | No aplicable | No es compatible con el proveedor | Próximamente | No aplicable | ✔ | ✔ | No aplicable | | ✔ | No aplicable | No aplicable |
> | **Revocar permisos de aplicación** | No aplicable | No es compatible con el proveedor | en breve | No aplicable | ✔ | ✔ | No aplicable | | ✔ | No aplicable | No aplicable |
> | **Aplicación de etiquetas de Azure Information Protection** | No aplicable | ✔ | | No aplicable | ✔ | ✔ | No aplicable | | | No aplicable | No aplicable |

## <a name="prerequisites"></a>Prerequisites

- En el caso de algunas aplicaciones, puede que sea necesario agregar las direcciones IP a la lista blanca para habilitar Cloud App Security de modo que recopile registros y proporcione acceso a la consola de Cloud App Security. Para obtener más información, vea [Requisitos de red](network-requirements.md).

- Se recomienda crear una cuenta de servicio de administración dedicada a Cloud App Security por cada aplicación que quiera conectar con la integración de la API de Cloud App Security.

> [!NOTE]
> Para obtener actualizaciones cuando las direcciones URL y las direcciones IP cambien, suscríbase al RSS como se explica en: [URL de Office 365 e intervalos de direcciones IP](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2).

Para usar los conectores de aplicaciones, debe asegurarse de que tiene lo siguiente para cada aplicación específica:

| Aplicación | Tipo de licencia | Usuario |
|-----|--------------|------|
| Azure | | Administrador global |
| AWS | | Usuario creado recientemente |
| Cuadro | Enterprise | Se recomienda encarecidamente que se conecte a Box como administrador. La conexión como coadmin dará como resultado una visibilidad de datos parcial. En caso de que se conecte como coadministrador, asegúrese de seleccionar todos los permisos. |
| Dropbox | Empresa/Enterprise | Administración |
| GCP | | Consulte los [requisitos previos de Connect GCP](connect-google-gcp-to-microsoft-cloud-app-security.md#prerequisites) |
| G Suite | Se prefiere G Suite Business o Enterprise<br /><br />G Suite Enterprise (como mínimo) | Superadministrador |
| Office 365 | | Administrador global |
| Okta | Enterprise (no versión de prueba) | Administración |
| Salesforce | | Administración |
| ServiceNow | Eureka o versión posterior | Rol de administrador + RestAPI |
| Webex | | Administrador + administrador de cumplimiento |
| Workday | | Consulte los [requisitos previos de Connect WorkDay](connect-workday-to-microsoft-cloud-app-security.md#prerequisites) |

### <a name="expressroute"></a>ExpressRoute

Cloud App Security se ha implementado en Azure y está totalmente integrado con [ExpressRoute](https://azure.microsoft.com/documentation/articles/expressroute-introduction/). Todas las interacciones con las aplicaciones de Cloud App Security y el tráfico enviado a Cloud App Security, incluida la carga de registros de detección, se enrutan a través del **emparejamiento público** de ExpressRoute para mejorar la latencia, el rendimiento y la seguridad. No hay ningún paso de configuración necesario en el lado cliente.
Para obtener más información sobre el emparejamiento público, consulte [Circuitos ExpressRoute y dominios de enrutamiento](https://azure.microsoft.com/documentation/articles/expressroute-circuit-peerings/).

## <a name="next-steps"></a>Pasos siguientes

[Actividades diarias para proteger el entorno de nube](daily-activities-to-protect-your-cloud-environment.md)

[!INCLUDE [Open support ticket](includes/support.md)]

## <a name="check-out-this-video"></a>Eche un vistazo a este vídeo.

[Microsoft Cloud App Security: API de REST y tokens](https://channel9.msdn.com/Shows/Microsoft-Security/Microsoft-Cloud-App-Security--REST-APIs-and-Tokens)
