---
title: Conectar aplicaciones para obtener visibilidad y control Cloud App Security | Microsoft Docs
description: En este artículo se describe el proceso para conectar aplicaciones con conectores de API a las aplicaciones de la nube de su organización.
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
ms.openlocfilehash: 0aa55a99017a1768bf58fd2c2a40688c1a5c95e6
ms.sourcegitcommit: 4f3883a9e85d0aaf2802b10433b221c3f1838d88
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/13/2020
ms.locfileid: "79285349"
---
# <a name="connect-apps"></a>Conectar aplicaciones

*Se aplica a: Microsoft Cloud App Security*

Los conectores de aplicaciones usan las API de los proveedores de aplicaciones para permitir una mayor visibilidad y control Microsoft Cloud App Security a través de las aplicaciones a las que se conecta.

Microsoft Cloud App Security aprovecha las API proporcionadas por el proveedor de la nube. Cada servicio tiene su propio marco de trabajo y limitaciones de API, como la limitación de peticiones, los límites de API, las ventanas de API dinámicas de tiempo cambiante y otras. Microsoft Cloud App Security trabajar con los servicios para optimizar el uso de las API y proporcionar el mejor rendimiento. Teniendo en cuenta las diferentes limitaciones que los servicios imponen en las API, los motores de Cloud App Security utilizan la capacidad permitida. Algunas operaciones, como el análisis de todos los archivos del inquilino, requieren numerosas API, por lo que se reparten durante un período más largo. Tenga en cuenta que algunas directivas pueden ejecutarse durante varias horas o varios días.

## <a name="multi-instance-support"></a>Compatibilidad con varias instancias

Cloud App Security admite varias instancias de la misma aplicación conectada. Por ejemplo, si tiene más de una instancia de Salesforce (una para ventas, otra para marketing) puede conectar ambos a Cloud App Security. Puede administrar las distintas instancias desde la misma consola para crear directivas granulares e investigación más profunda. Esta compatibilidad solo se aplica a las aplicaciones conectadas a la API, no a las aplicaciones descubiertas por el proxy ni a las aplicaciones.

> [!NOTE]
> No se admiten instancias múltiples de Office 365 y Azure.

## <a name="how-it-works"></a>Cómo funciona

Cloud App Security se implementa con privilegios de administrador del sistema para permitir el acceso total a todos los objetos del entorno.

El flujo del Conector de aplicaciones es como sigue:

1. Cloud App Security examina y guarda los permisos de autenticación.
2. Cloud App Security solicita la lista de usuarios. La primera vez que se realiza la solicitud, el análisis puede tardar algún tiempo en completarse. Una vez terminado el análisis de los usuarios, Cloud App Security pasa a las actividades y los archivos. En cuanto se inicia el análisis, algunas actividades estarán disponibles en Cloud App Security.
3. Una vez finalizada la solicitud del usuario, Cloud App Security examina periódicamente los usuarios, los grupos, las actividades y los archivos. Todas las actividades estarán disponibles tras el primer análisis completo.

Esta conexión puede tardar algún tiempo en función del tamaño del inquilino, el número de usuarios y el tamaño y el número de archivos que deben analizarse.

En función de la aplicación a la que se conecte, la conexión de API habilita los siguientes elementos:

- **Información** de la cuenta: visibilidad de los usuarios, las cuentas, la información de perfil, los grupos de estado (suspendido, activo, deshabilitado) y los privilegios.

- **Seguimiento de auditoría** : visibilidad de las actividades del usuario, las actividades de administración, la actividad de inicio de sesión.

- **Examen de datos** : exploración de datos no estructurados mediante dos procesos: periódicamente (cada 12 horas) y en tiempo real (se desencadena cada vez que se detecta un cambio).

- **Permisos de aplicación** : visibilidad de los tokens emitidos y sus permisos.

- **Gobierno de cuentas** : capacidad de suspender usuarios, revocar contraseñas, etc.

- **Gobierno de datos** : capacidad de poner archivos en cuarentena, incluidos los archivos de la papelera, y sobrescribir archivos.

- **Gobierno de permisos de aplicación** : capacidad de quitar tokens.

En la siguiente tabla se enumeran, por aplicación en la nube, qué capacidades son compatibles con los conectores de aplicaciones:

> [!div class="mx-tableFixed"]
>
> | | AWS | Box | Dropbox | GCP | G Suite | Office 365 | Okta | Service Now | Salesforce | Webex | Workday |
> |-|-|-|-|-|-|-|-|-|-|-|-|
> | **Cuentas de lista** | ✔ | ✔ | ✔ | Conexión de asunto G Suite | ✔ | ✔ | ✔ | ✔ | ✔ | ✔ | ✔ |
> | **Lista de grupos** | ✔ | ✔ | ✔ | Conexión de asunto G Suite | ✔ | ✔ | ✔ | ✔ | ✔ | | No es compatible con el proveedor |
> | **Lista de privilegios** | | ✔ | ✔ | Conexión de asunto G Suite | ✔ | ✔ | No es compatible con el proveedor | ✔ | ✔ | ✔ | No pported por el proveedor |
> | **Gobernanza de usuario** | | ✔ | Próximamente | Conexión de asunto G Suite | ✔ | ✔ | | Próximamente | ✔ | Próximamente | t compatible con el proveedor |
> | **Actividad de inicio de sesión** | ✔ | ✔ | ✔ | Conexión de asunto G Suite | ✔ | ✔ | ✔ | ✔ | ✔ | ✔ | ✔ |
> | **Actividad del usuario** | No disponible | ✔ | ✔ | ✔ | ✔: requiere Google Business o Enterprise | ✔ | ✔ | Parcial | Compatible con lesforce Shield | ✔ | ✔ |
> | **Actividad administrativa** | ✔ | ✔ | ✔ | ✔ | ✔ | ✔ | ✔ | Parcial | ✔ | ✔ | No es compatible con el proveedor |
> | **DLP: examen periódico** | | ✔ | Próximamente | No disponible | ✔ | ✔ | No disponible | | | | No compatible con ovider |
> | **Análisis de DLP casi en tiempo real** | | ✔ | ✔ | No disponible | ✔: requiere Google Business Enterprise | ✔ | No disponible | ✔ | ✔ | ✔ | No es compatible con el proveedor |
> | **Control de uso compartido** | ✔ | ✔ | ✔ | No disponible | ✔ | ✔ | No disponible | No disponible | | ✔ | No compatible con ovider |
> | **Regulación de archivos** | ✔ | ✔ | ✔ | No disponible | ✔ | ✔ | No disponible | | ✔ | | No es compatible con el proveedor |
> | **Ver permisos de aplicación** | No disponible | No es compatible con el proveedor | Próximamente | No disponible | ✔ | ✔ | No disponible | | ✔ | No disponible | No disponible |
> | **Revocar permisos de aplicación** | No disponible | No es compatible con el proveedor | en breve | No disponible | ✔ | ✔ | No disponible | | ✔ | No disponible | No disponible |
> | **Aplicar etiquetas de Azure Information Protection** | No disponible | ✔ | | No disponible | ✔ | ✔ | No disponible | | | No disponible | No disponible |

## <a name="prerequisites"></a>Requisitos previos

- En el caso de algunas aplicaciones, puede que sea necesario poner en blanco las direcciones IP para habilitar Cloud App Security para recopilar registros y proporcionar acceso a la consola de Cloud App Security. Para obtener más información, consulte [requisitos de red](network-requirements.md).

- Se recomienda crear una cuenta de servicio de administración dedicada a Cloud App Security por cada aplicación que quiera conectar con la integración de la API de Cloud App Security.

> [!NOTE]
> Para obtener actualizaciones cuando las direcciones URL y las direcciones IP cambien, suscríbase al RSS como se explica en: [URL de Office 365 e intervalos de direcciones IP](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2).

Para usar los conectores de aplicaciones, debe asegurarse de que tiene lo siguiente para cada aplicación específica:

| Aplicación | Tipo de licencia | Usuario |
|-----|--------------|------|
| Azure | | Administrador global |
| AWS | | Usuario creado recientemente |
| Box | Enterprise | Se recomienda encarecidamente que se conecte a Box como administrador. La conexión como coadmin dará como resultado una visibilidad de datos parcial. Si se conecta como coadministrador, asegúrese de seleccionar todos los permisos. |
| Dropbox | Empresa/Enterprise | Admin |
| GCP | | Consulte los [requisitos previos de Connect GCP](connect-google-gcp-to-microsoft-cloud-app-security.md#prerequisites) |
| G Suite | G Suite Business o Enterprise preferida<br /><br />G Suite Enterprise (como mínimo) | Superadministrador |
| Office 365 | | Administrador global |
| Okta | Enterprise (no versión de prueba) | Admin |
| Salesforce | | Admin |
| ServiceNow | Eureka o versión posterior | Rol de administrador + RestAPI |
| Webex | | Administrador + administrador de cumplimiento |
| Workday | | Consulte los [requisitos previos de Connect WorkDay](connect-workday-to-microsoft-cloud-app-security.md#prerequisites) |

### <a name="expressroute"></a>ExpressRoute

Cloud App Security se ha implementado en Azure y está totalmente integrado con [ExpressRoute](https://azure.microsoft.com/documentation/articles/expressroute-introduction/). Todas las interacciones con las aplicaciones Cloud App Security y el tráfico enviado a Cloud App Security, incluida la carga de registros de detección, se enrutan a través **del emparejamiento público** de ExpressRoute para mejorar la latencia, el rendimiento y la seguridad. No hay ningún paso de configuración necesario en el lado cliente.
Para obtener más información sobre el emparejamiento público, vea [Circuitos ExpressRoute y dominios de enrutamiento](https://azure.microsoft.com/documentation/articles/expressroute-circuit-peerings/).

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Actividades diarias para proteger el entorno de nube](daily-activities-to-protect-your-cloud-environment.md)

[!INCLUDE [Open support ticket](includes/support.md)]

## <a name="check-out-this-video"></a>Consulte este vídeo.

> [!div class="nextstepaction"]
> [Microsoft Cloud App Security: tokens y API de REST](https://channel9.msdn.com/Shows/Microsoft-Security/Microsoft-Cloud-App-Security--REST-APIs-and-Tokens)
