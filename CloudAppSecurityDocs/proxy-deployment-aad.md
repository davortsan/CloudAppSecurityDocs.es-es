---
title: Implementación del control de aplicaciones de acceso condicional para aplicaciones de Azure AD
description: En este artículo se ofrece información sobre cómo implementar las características del proxy inverso de control de aplicaciones de acceso condicional de Microsoft Cloud App Security para aplicaciones de Azure AD.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 7/12/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 2490c5e5-e723-4fc2-a5e0-d0a3a7d01fc2
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: b231e378da12c3b632fb58fb28097e7b49bee852
ms.sourcegitcommit: 8a49c166424fea83853b0a6895212367526abe78
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2019
ms.locfileid: "71085116"
---
# <a name="deploy-conditional-access-app-control-for-featured-apps"></a>Implementación del Control de aplicaciones de acceso condicional para aplicaciones destacadas

*Se aplica a: Microsoft Cloud App Security*

>[!div class="step-by-step"]
[« Anterior: Introducción al control de aplicaciones de acceso condicional](proxy-intro-aad.md)<br>
[Siguiente: Incorporación e implementación de Control de aplicaciones de acceso condicional para cualquier aplicación»](proxy-deployment-any-app.md)

Siga estos pasos para configurar las aplicaciones destacadas que se van a controlar mediante Microsoft Cloud App Security Control de aplicaciones de acceso condicional.

**Paso 1: [Vaya al portal de Azure AD y cree una directiva de acceso condicional para las aplicaciones y enrute la sesión a Cloud App Security](#add-azure-ad)**

**Paso 2: [Iniciar sesión en cada aplicación con un usuario con ámbito en la Directiva](#sign-in-scoped)**

**Paso 3: Si no seleccionó una directiva de Cloud App Security integrada en Azure AD o si desea aplicar la Directiva a cualquier aplicación, [vaya al portal de Cloud App Security](#portal) .**

[**Paso 4: pruebe la implementación**.](#test)

> [!NOTE]
> Para implementar el Control de aplicaciones de acceso condicional para aplicaciones de Azure AD, necesita una [licencia válida de Azure AD Premium P1](https://docs.microsoft.com/azure/active-directory/license-users-groups) y otra de Cloud App Security.

## Paso 1: Creación de una directiva de acceso condicional de Azure AD de prueba <a name="add-azure-ad"></a>  

1. En Azure Active Directory, en **seguridad**, haga clic en **acceso condicional**.

2. Haga clic en **Nueva directiva** y cree una directiva.

3. En la sección **Usuarios** de la directiva de prueba, asigne un usuario de prueba o uno que se pueda usar para un primer inicio de sesión y su comprobación.

4. En la sección **Aplicaciones en la nube** de la directiva de PRUEBA, asigne las aplicaciones que quiera controlar con el control de aplicaciones de acceso condicional. 

5. En **Sesión**, configure la directiva para que use cualquiera de las directivas integradas, **Solo supervisar** o **Bloquear descargas**. También puede seleccionar **Usar directiva personalizada** para establecer una directiva avanzada en el portal de Cloud App Security. 

6. Opcionalmente, agregue cualquier **asignación de condiciones** o **control de acceso** que corresponda.

   ![Acceso condicional de Azure AD](./media/azure-ad-caac-policy.png)

      > [!NOTE]
      >El Control de aplicaciones de acceso condicional admite aplicaciones SAML u Open ID Connect configuradas con el inicio de sesión único en Azure AD, incluidas estas aplicaciones destacadas. Las aplicaciones no destacadas se pueden configurar con control de acceso en el portal de Cloud App Security mediante una solicitud para incorporarlas con control de sesión. 

7. Haga clic en **Habilitar** y **Guardar**.

## Paso 2: Iniciar sesión en cada aplicación con un usuario con ámbito en la Directiva<a name="sign-in-scoped"></a>

Después de crear la directiva, inicie sesión en cada aplicación configurada en esa directiva. Asegúrese de que inicia sesión con un usuario configurado en la directiva. Asegúrese de cerrar antes cualquier sesión existente.

Cloud App Security sincronizará los detalles de la Directiva con sus servidores para cada nueva aplicación en la que inicie sesión.  Este proceso puede tardar hasta un minuto.

## Paso 3: Configuración de controles avanzados y cualquier aplicación en el portal de Cloud App Security<a name="portal"></a>

Las instrucciones anteriores le han ayudado a crear una directiva integrada de Cloud App Security para aplicaciones destacadas directamente en Azure AD.

Para configurar una directiva avanzada, cree una directiva de [acceso](access-policy-aad.md) o una [Directiva de sesión](session-policy-aad.md) en Cloud App Security.

Para aplicar la Directiva a cualquier aplicación, siga las instrucciones para la [incorporación automática de una aplicación para su uso con control de aplicaciones de acceso condicional](proxy-deployment-any-app.md).

Para solicitar soporte técnico para una aplicación cualquiera:

1. En el portal de Cloud App Security, vaya al engranaje Configuración y elija **Control de aplicaciones de acceso condicional**. Debería ver un mensaje que informa de que el control de aplicaciones de acceso condicional ha detectado nuevas aplicaciones de Azure AD.

    ![Menú del Control de aplicaciones de acceso condicional](./media/caac-menu.png)

2. Haga clic en **Ver nuevas aplicaciones**.

    ![Vista de nuevas aplicaciones del Control de aplicaciones de acceso condicional](./media/caac-view-apps.png)

3. En la pantalla que se abre, verá todas las aplicaciones en las que haya iniciado sesión en el paso anterior. En cada aplicación, haga clic en el signo + y, después, haga clic en **Agregar**.

   > [!NOTE]
   > Si una aplicación no aparece en el catálogo de aplicaciones de Cloud App Security, aparecerá en la sección Aplicación no identificada del cuadro de diálogo junto con la dirección URL de inicio de sesión. Al hacer clic en el signo + en estas aplicaciones, puede incorporarlas como aplicación personalizada.

   ![Aplicaciones de Azure AD detectadas mediante el Control de aplicaciones de acceso condicional](./media/caac-discovered-aad-apps.png)

4. En la tabla de aplicaciones del Control de aplicaciones de acceso condicional, fíjese en la columna **Controles disponibles** y confirme que figuren en ella **Acceso condicional de Azure AD** y **Control de sesión**.

   > [!NOTE]
   > Si no aparece el Control de sesión para una aplicación, significa que aún no está disponible para esa aplicación específica. Verá el vínculo **Solicitar control de sesión** en su lugar.

     ![Solicitud del Control de aplicaciones de acceso condicional](./media/caac-request.png)

5. Haga clic en **Solicitar control de la sesión** para solicitar la incorporación de la aplicación al control de sesión. El equipo de Microsoft Cloud App Security procederá a realizar el proceso de incorporación de la aplicación con usted.

6. Para configurar una directiva para aprovechar la administración de dispositivos mediante certificados de cliente:
    1. Vaya al engranaje Configuración y elija **Identificación de dispositivos**.
    2. Cargue al menos un certificado raíz o intermedio.
    3. Tras cargar el certificado, puede crear directivas de acceso y sesión basadas en la configuración de la opción **Etiqueta de dispositivo** y **Certificado de cliente válido**.

       ![Id. de dispositivo del Control de aplicaciones de acceso condicional](./media/caac-device-id.png)

> [!NOTE]
> Solo se solicita un certificado a un usuario si la sesión coincide con una directiva que use el filtro de certificado de cliente válido.

## Paso 4: pruebe la implementación<a name="test">.</a>

1. Primero, cierre cualquier sesión existente. Después, intente iniciar sesión en cada aplicación que se ha implementado correctamente. Inicie sesión con un usuario que coincida con la directiva configurada en Azure AD.

2. En el portal de Cloud App Security en **Investigar**, seleccione **Registro de actividad** y asegúrese de que se capturan las actividades de inicio de sesión de cada aplicación.

3. Puede filtrar haciendo clic en **Avanzadas** y, luego, mediante la opción **Origen es igual a Acceso condicional**.

    ![Filtrar por Acceso condicional de Azure AD](./media/sso-logon.png)

4. Se recomienda que inicie sesión en aplicaciones de escritorio y móviles desde dispositivos administrados y no administrados. Esto es para asegurarse de que las actividades se capturan correctamente en el registro de actividad.<br>
Para confirmar que la actividad se captura correctamente, haga clic en un registro de inicio de sesión único en la actividad para abrir el cajón de actividad. Asegúrese de que la propiedad **Etiqueta de agente de usuario** refleja correctamente si el dispositivo es un cliente nativo (es decir, un aplicación de escritorio o móvil) o si es un dispositivo administrado (Compatible, Unido a dominio o Certificado de cliente válido).

> [!NOTE]
> Después de implementarse, no se puede quitar una aplicación de la página Control de aplicaciones de acceso condicional. Mientras no establezca una sesión o una directiva de acceso en la aplicación, el Control de aplicaciones de acceso condicional no cambiará el comportamiento de la aplicación.

>[!div class="step-by-step"]
[« Anterior: Introducción al control de aplicaciones de acceso condicional](proxy-intro-aad.md)<br>[Siguiente: Incorporación e implementación de Control de aplicaciones de acceso condicional para cualquier aplicación»](proxy-deployment-any-app.md)

## <a name="next-steps"></a>Pasos siguientes 
[Trabajar con Cloud App Security Control de aplicaciones de acceso condicional](proxy-intro-aad.md)

[Los clientes Premier también pueden crear una solicitud de soporte técnico directamente en el portal Premier.](https://premier.microsoft.com/)