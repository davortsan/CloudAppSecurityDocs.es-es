---
title: 'Solución de problemas: ¿Qué es cas.ms, mcas.ms o mcas-gov.us?'
description: En este artículo se proporciona información sobre el sufijo de dirección URL cas.ms, mcas.ms o mcas-gov.us que usa Control de aplicaciones de acceso condicional.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 03/18/2020
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.suite: ems
ms.openlocfilehash: c62229f209dc1a7862a2f4b4442a663aacce58bc
ms.sourcegitcommit: 575f2b2efa9ca4477d7e60271d21e225ef2c38ea
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/22/2020
ms.locfileid: "90877121"
---
# <a name="troubleshooting---what-is-casms-mcasms-or-mcas-govus"></a>Solución de problemas: ¿Qué es `*.cas.ms` , `*.mcas.ms` o `*.mcas-gov.us` ?

[!INCLUDE [Banner for top of topics](includes/banner.md)]

En este artículo se proporciona información sobre los `cas.ms` `mcas.ms` `mcas-gov.us` sufijos de dirección URL, y que usa control de aplicaciones de acceso condicional.

## <a name="our-system-flagged-a-new-dns-entry-or-generated-certificate-for-casms-mcasms-or-mcas-govus-but-we-dont-use-cloud-app-security"></a>Nuestro sistema marcó una nueva entrada DNS o un certificado generado para `*.cas.ms` , `*.mcas.ms` o `*.mcas-gov.us` , pero no usamos Cloud App Security

Este es el comportamiento normal y los resultados de Cloud App Security proteger el entorno. Incluso si su organización no usa Cloud App Security, cuando alguien visite su sitio o servicio desde un entorno que lo hace, sus direcciones URL se reescribirán para proteger su acceso.

Por ejemplo, contoso protege su entorno mediante Control de aplicaciones de acceso condicional proporcionado por Cloud App Security. Cuando un usuario de Contoso visita `fabrikam.com` , el usuario se redirige automáticamente a `fabrikam.com.cas.ms` . Como resultado, el equipo de suplantación de identidad (phishing) de Fabrikam verá una nueva entrada DNS y un certificado para `fabrikam.com.cas.ms` .

Por lo tanto, aunque Fabrikam no utiliza realmente Cloud App Security, ven la entrada o el certificado DNS porque contoso sí lo hace.

> [!NOTE]
> También puede ver los siguientes dominios en los registros de transparencia:
>
> - `*.admin-rs-mcas.ms`
> - `*.rs-mcas.ms`
> - `*.admin-rs2-mcas.ms`
> - `*.rs2-mcas.ms`
> - `*.admin-mcas.ms`
> - `*.mcas.ms`
> - `*.admin-mcas-gov.us`

## <a name="heres-why-you-see-casms-mcasms-or-mcas-govus-in-your-url"></a>Este es el motivo por `*.cas.ms` el que ve, `*.mcas.ms` o `*.mcas-gov.us` en su dirección URL.

En primer lugar, no ha sido phish. Se espera este tipo de URL e indica que su organización aplica controles de seguridad adicionales para proteger los datos críticos para la empresa.

Para ello, se usa Cloud App Security, una solución para proteger el entorno de nube de la organización, a fin de reemplazar todas las direcciones URL y cookies pertinentes relacionadas con las aplicaciones en la nube que se usan.

Por lo tanto, cuando intente obtener acceso a una aplicación en la nube, como Salesforce, SharePoint Online o AWS, observará que su dirección URL tiene como sufijo `.cas.ms` , `.mcas.ms` o `.mcas-gov.us` . Por ejemplo, al usar la aplicación XYZ, la dirección URL que se usa para ver los cambios de `XYZ.com` en `XYZ.com.cas.ms` .

Si la dirección URL no coincide exactamente con uno de los patrones de reemplazo (por ejemplo, `<app_site>.com` no se reemplaza por `<app_site>.com.cas.ms` ), o si tiene problemas adicionales, póngase en contacto con el Departamento de ti.
