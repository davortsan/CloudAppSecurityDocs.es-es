---
title: Solucionar problemas de Control de aplicaciones de acceso condicional
description: En este artículo se proporciona una lista de posibles problemas de Control de aplicaciones de acceso condicional y se proporcionan posibles soluciones.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 6/30/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.suite: ems
ms.openlocfilehash: 6e43990b3ee3d3c5f33119643329381001707724
ms.sourcegitcommit: e8c40ab8901744314af19ede50e9017a92111721
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/24/2020
ms.locfileid: "91205541"
---
# <a name="troubleshooting-conditional-access-app-control-issues"></a>Solución de problemas de Control de aplicaciones de acceso condicional

*Se aplica a: Microsoft Cloud App Security*

En este artículo se proporciona una lista de posibles problemas de Control de aplicaciones de acceso condicional y se proporcionan posibles soluciones.

## <a name="our-system-flagged-a-new-dns-entry-or-generated-a-certificate-for-casms-but-we-dont-use-microsoft-cloud-app-security"></a>Nuestro sistema marcó una nueva entrada DNS o generó un certificado para *. cas.ms, pero no usamos Microsoft Cloud App Security

Este es el comportamiento normal y los resultados de Cloud App Security proteger el entorno. Incluso si su organización no usa Cloud App Security, cuando alguien visite su sitio o servicio desde un entorno protegido por Control de aplicaciones de acceso condicional de Cloud App Security, se reescribirán sus direcciones URL para proteger su acceso.

Por ejemplo, cuando un usuario de Contoso, una empresa protegida por Cloud App Security, visita fabrikam.com, el usuario se redirige automáticamente a fabrikam.com.us.cas.ms. Como resultado, el equipo de suplantación de identidad (phishing) de Fabrikam verá una nueva entrada DNS y un certificado para fabrikam.com.us.cas.ms.

En este ejemplo puede ver que, aunque Fabrikam no utiliza realmente Cloud App Security, dado que contoso sí lo hace, se crean la entrada y el certificado DNS.

**TBD [ALEX]:??? ¿CÓMO RESOLVERLO? ¿Contacto con MS? ¿Agregar excepciones????**

## <a name="i-see-casms-in-my-url-have-i-been-phished"></a>Veo *. cas.ms en mi dirección URL. ¿He sido phish?

En primer lugar, no ha sido phish. Se espera este tipo de URL e indica que su organización aplica controles de seguridad adicionales para proteger los datos críticos para la empresa.

Lo hacen mediante...

Al intentar obtener acceso a las aplicaciones en la nube, como Salesforce, SharePoint Online o AWS, observará que la dirección URL tiene el sufijo `*.cas.ms` . Por ejemplo, cuando se usa la aplicación XYZ, la dirección URL que se usa para ver tendrá cambios de `XYZ.com` en `XYZ.com.us.cas.ms` .

Si la dirección URL no coincide exactamente con el patrón de reemplazo (por ejemplo, redirigiendo *. com a *. com).* cas.ms) o, si tiene más problemas, póngase en contacto con el Departamento de ti.
