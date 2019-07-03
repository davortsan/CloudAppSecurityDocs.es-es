---
title: Solución de problemas de Control de aplicaciones de acceso condicional
description: En este artículo se proporciona una lista de posibles problemas de Control de aplicaciones de acceso condicional y proporciona soluciones posibles.
keywords: ''
author: ShlomoSagir-MS
ms.author: shsagir
manager: ShlomoSagir-MS
ms.date: 6/30/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.suite: ems
ms.openlocfilehash: e051d00c118b8e41142f8c0d9cc726675dcea27d
ms.sourcegitcommit: ee00e0033bf45a5f795bfd3e1d71fa1f70f97acb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/02/2019
ms.locfileid: "67515046"
---
# <a name="troubleshooting-conditional-access-app-control"></a>Solución de problemas de Control de aplicaciones de acceso condicional

*Se aplica a: Microsoft Cloud App Security*

Prohvides de este artículo, una lista de posibles Conditional Access App Control emite y proporciona soluciones posibles.

## <a name="troubleshooting-onboarded-apps"></a>Solucionar problemas de aplicaciones incorporadas

### <a name="the-sign-in-to-the-app-is-not-working"></a>El inicio de sesión a la aplicación no funciona

1. En Cloud App Security, en la barra de menús, haga clic en el engranaje de configuración ![icono configuración](./media/settings-icon.png "icono configuración") y seleccione **Conditional Access App Control**.
1. En la lista de aplicaciones, en la fila en la que aparece la aplicación que está configurando, elija los tres puntos al final de la fila y, a continuación, elija **Editar aplicación**.
1. Haga clic en **Nonce control** para expandir la sección y, a continuación, seleccione **habilita el control de nonce**.

    ![Captura de pantalla de opción de control de nonce.](media/troubleshooing-nonce-handling.png)

    > [!NOTE]
    > Si experimenta problemas navegando a páginas de aplicación distinto de la página principal, consulte [Troubleshooting visitas posteriores a la aplicación no vaya a la página esperada](#unexpected-page)

### Visitas posteriores a la aplicación no vaya a la página esperada<a name="unexpected-page"></a>

Los pasos siguientes se basan en el uso de Fiddler como la herramienta de registro de tráfico. La experiencia puede ser diferente de otras herramientas. Para obtener más información sobre el uso de Fiddler, consulte [manera fácil para recopilar el registro de fiddler](https://blogs.msdn.microsoft.com/maheshk/2016/05/03/easy-way-to-collect-fiddler-log-fiddlercap/).

1. Copie la dirección URL de página en la aplicación que no vaya a la página esperada; lo necesitará más adelante.

    > [!NOTE]
    > Asegúrese de que el dominio no incluye el sufijo de dirección URL de Cloud App Security (por ejemplo, *. us2.cas.ms*)

1. Usar una herramienta de registro de tráfico como Fiddler para supervisar la página.
1. Vaya a la dirección URL que copió anteriormente y autenticar si es necesario.
1. En la herramienta de registro de tráfico, busque la solicitud correspondiente al dominio y la ruta de acceso basada en el protocolo que usa.

    | Protocol | Dominio | Path | Nombre del campo de estado |
    | --- | --- | --- | --- |
    | OIDC | `https://login.microsoftonline.com` | /Common/oauth2/Authorize | state |
    | SAML 2.0 | `https://login.microsoftonline.com` | /*id*/saml2 | RelayState |

1. Seleccione la solicitud y, a continuación, en el **inspectores** ficha, seleccione **WebForms**.
1. Crear una cadena de expresión regular basándose en la 

## <a name="next-steps"></a>Pasos siguientes

[Implementar Cloud Discovery](set-up-cloud-discovery.md)

[Los clientes Premier también pueden elegir Cloud App Security directamente desde el Portal Premier](https://premier.microsoft.com/).
