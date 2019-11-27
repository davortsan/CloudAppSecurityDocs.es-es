---
title: Solucionar problemas Control de aplicaciones de acceso condicional
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
ms.openlocfilehash: 71126072096d9a2ba156c6c3e6b3c17dc0d619b3
ms.sourcegitcommit: 094bb42a198fe733cfd3aec79d74487672846dfa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/24/2019
ms.locfileid: "74460111"
---
# <a name="troubleshooting-conditional-access-app-control"></a>Solución de problemas Control de aplicaciones de acceso condicional

*Se aplica a: Microsoft Cloud App Security*

En este artículo se prohvides una lista de posibles problemas de Control de aplicaciones de acceso condicional y se proporcionan posibles soluciones.

## <a name="troubleshooting-onboarded-apps"></a>Solución de problemas de aplicaciones incorporadas

### <a name="the-sign-in-to-the-app-is-not-working"></a>El inicio de sesión en la aplicación no funciona

1. En Cloud App Security, en la barra de menús, haga clic en el icono configuración engranaje ![configuración](./media/settings-icon.png "icono de configuración") y seleccione **control de aplicaciones de acceso condicional**.
1. En la lista de aplicaciones, en la fila en la que aparece la aplicación que está configurando, elija los tres puntos al final de la fila y, después, elija **Editar aplicación**.
1. Haga clic en **control de nonce** para expandir la sección y, a continuación, seleccione **Habilitar el control de nonce**.

    ![Captura de pantalla de la opción de control de nonce.](media/troubleshooing-nonce-handling.png)

    > [!NOTE]
    > Si experimenta problemas al navegar a las páginas de la aplicación que no sean la Página principal, consulte [solución de problemas de visitas posteriores a la aplicación no ir a la página esperada](#unexpected-page)

### Las siguientes visitas a la aplicación no van a la página esperada<a name="unexpected-page"></a>

Los pasos siguientes se basan en el uso de Fiddler como la herramienta de registro de tráfico. La experiencia puede ser diferente para otras herramientas. Para obtener más información sobre el uso de Fiddler, consulte la [forma más sencilla de recopilar el registro de Fiddler](https://blogs.msdn.microsoft.com/maheshk/2016/05/03/easy-way-to-collect-fiddler-log-fiddlercap/).

1. Copie la dirección URL de la página de la aplicación que no vaya a la página esperada, ya que la necesitará más adelante.

    > [!NOTE]
    > Asegúrese de que el dominio no incluya el sufijo de la dirección URL del Cloud App Security (por ejemplo, *. US2.CAS.ms*)

1. Use una herramienta de registro de tráfico como Fiddler para supervisar la página.
1. Vaya a la dirección URL que copió anteriormente y autentique si es necesario.
1. En la herramienta de registro de tráfico, busque la solicitud que coincida con el dominio y la ruta de acceso en función del protocolo que esté usando.

    | Protocol | Dominio | Path | Nombre del campo de estado |
    | --- | --- | --- | --- |
    | OIDC | `https://login.microsoftonline.com` | /common/oauth2/authorize | state |
    | SAML 2.0 | `https://login.microsoftonline.com` | *identificador*de //saml2 | RelayState |

1. Seleccione la solicitud y, a continuación, en la pestaña **inspectores** , seleccione **WebForms**.
1. Cree una cadena regex basada en el 

## <a name="next-steps"></a>Pasos siguientes

[Implementar Cloud Discovery](set-up-cloud-discovery.md)

[!INCLUDE [Open support ticket](includes/support.md)]
