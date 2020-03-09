---
title: 'Solución de problemas: ¿Qué es cas.ms?'
description: En este artículo se proporciona información sobre el sufijo cas.ms de la dirección URL que usa Control de aplicaciones de acceso condicional.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 03/08/2020
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.suite: ems
ms.openlocfilehash: e08fc2af75d59ac5697593a47e3a002dfb4986f9
ms.sourcegitcommit: 3f6ef6b97a0953470135d115323a00cf11441ab7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/08/2020
ms.locfileid: "78927883"
---
# <a name="troubleshooting---what-is-casms"></a>Solución de problemas: ¿Qué es cas.ms?

*Se aplica a: Microsoft Cloud App Security*

En este artículo se proporciona información sobre el `cas.ms` sufijo de dirección URL que usa Control de aplicaciones de acceso condicional.

## <a name="our-system-flagged-a-new-dns-entry-or-generated-certificate-for-casms-but-we-dont-use-cloud-app-security"></a>Nuestro sistema marcó una nueva entrada DNS o un certificado generado para `*.cas.ms`, pero no usamos Cloud App Security

Este es el comportamiento normal y los resultados de Cloud App Security proteger el entorno. Incluso si su organización no usa Cloud App Security, cuando alguien visite su sitio o servicio desde un entorno que lo hace, sus direcciones URL se reescribirán para proteger su acceso.

Por ejemplo, contoso protege su entorno mediante Control de aplicaciones de acceso condicional proporcionado por Cloud App Security. Cuando un usuario de Contoso visita `fabrikam.com`, el usuario se redirige automáticamente a `fabrikam.com.<region>.cas.ms`. Como resultado, el equipo de suplantación de identidad (phishing) de Fabrikam verá una nueva entrada DNS y un certificado para `fabrikam.com.<region>.cas.ms`.

Por lo tanto, aunque Fabrikam no utiliza realmente Cloud App Security, ven la entrada o el certificado DNS porque contoso sí lo hace.

## <a name="heres-why-you-see-casms-in-your-url"></a>Este es el motivo por el que ve `*.cas.ms` en la dirección URL

En primer lugar, no ha sido phish. Se espera este tipo de URL e indica que su organización aplica controles de seguridad adicionales para proteger los datos críticos para la empresa.

Para ello, se usa Cloud App Security, una solución para proteger el entorno de nube de la organización, a fin de reemplazar todas las direcciones URL y cookies pertinentes relacionadas con las aplicaciones en la nube que usa.

Por lo tanto, cuando intente obtener acceso a una aplicación en la nube, como Salesforce, SharePoint Online o AWS, observará que su dirección URL tiene el sufijo `<region>.cas.ms`. Por ejemplo, al usar la aplicación XYZ, la dirección URL que se usa para ver los cambios de `XYZ.com` a `XYZ.com.<region>.cas.ms`.

Si la dirección URL no coincide exactamente con el patrón de reemplazo (por ejemplo, `<app_site>.com` no se sustituye por `<app_site>.com.<region>.cas.ms`) o si tiene problemas adicionales, póngase en contacto con el Departamento de ti.
