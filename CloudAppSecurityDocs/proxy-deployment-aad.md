---
title: Implementación del control de aplicaciones de acceso condicional para aplicaciones de Azure AD
description: En este artículo se ofrece información sobre cómo implementar las características del proxy inverso de control de aplicaciones de acceso condicional de Microsoft Cloud App Security para aplicaciones de Azure AD.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 12/10/2018
ms.topic: conceptual
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 2490c5e5-e723-4fc2-a5e0-d0a3a7d01fc2
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: d7f0041a385a60cde5bc714312435dd2cd6ac389
ms.sourcegitcommit: b86c3afd1093fbc825fec5ba4103e3a95f65758e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/10/2018
ms.locfileid: "53177137"
---
# <a name="deploy-conditional-access-app-control-for-azure-ad-apps"></a>Implementación del control de aplicaciones de acceso condicional para aplicaciones de Azure AD

*Se aplica a: Microsoft Cloud App Security*

>[!div class="step-by-step"]
[« Anterior: Introducción al control de aplicaciones de acceso condicional](proxy-intro-aad.md)<br>
[Siguiente: Cómo crear una directiva de sesión »](session-policy-aad.md)


Haga lo siguiente para configurar aplicaciones de Azure AD de forma que estén controladas por el control de aplicaciones de acceso condicional de Microsoft Cloud App Security.

**Paso 1: [vaya al portal de Azure AD, cree una directiva de acceso condicional para las aplicaciones y distribuya la sesión a Cloud App Security](#add-azure-ad).**

**Paso 2: [inicie sesión con un usuario con ámbito en la directiva en las aplicaciones](#sign-in-scoped).**

**Paso 3: [vuelva al portal de Cloud App Security y seleccione la notificación de mensaje emergente para agregar las aplicaciones](#banner-notification).**

**Paso 4: [cree una directiva de acceso](access-policy-aad.md) o [cree una directiva de sesión](session-policy-aad.md) para las aplicaciones en Cloud App Security.**


> [!NOTE]
> Para implementar el control de aplicaciones de acceso condicional para aplicaciones de Azure AD, necesita una [licencia válida de Azure AD Premium P1](https://docs.microsoft.com/azure/active-directory/license-users-groups).

## Paso 1: agregue aplicaciones de Azure AD en Cloud App Security <a name="add-azure-ad"></a>  

1. Cree una directiva de acceso condicional de Azure AD de prueba.

   1. En Azure Active Directory, en **Seguridad**, haga clic en **Acceso condicional**.

      ![Acceso condicional de Azure AD](./media/aad-conditional-access.png)

   2. Haga clic en **Nueva directiva** y cree una directiva. Asegúrese de que en **Sesión** selecciona **Use Conditional Access App Control enforced restrictions** (Usar las restricciones que exige el control de aplicaciones de acceso condicional).

      ![Acceso condicional de Azure AD](./media/proxy-deploy-restrictions-aad.png)

   3. En la sección **Usuarios y grupos** de la directiva de prueba, asigne un usuario de prueba o un usuario que se pueda usar para un inicio de sesión inicial.
    
   4. En la sección **Aplicaciones en la nube** de la directiva de PRUEBA, asigne las aplicaciones que quiera controlar con el control de aplicaciones de acceso condicional. 

      > [!NOTE]
      >Procure elegir aplicaciones que sean compatibles con el control de aplicaciones de acceso condicional. El control de aplicaciones de acceso condicional admite aplicaciones configuradas con SAML y aplicaciones Open ID Connect con inicio de sesión único en Azure AD. 

## Paso 2: inicie sesión con un usuario con ámbito en la directiva en las aplicaciones <a name="sign-in-scoped"></a>

Después de crear la directiva, inicie sesión en cada aplicación configurada en esa directiva. Asegúrese de que inicia sesión con un usuario configurado en la directiva. Asegúrese de cerrar antes cualquier sesión existente.

## Paso 3: vuelva al portal de Cloud App Security y seleccione la notificación de mensaje emergente para agregar las aplicaciones <a name="banner-notification"></a>

1. En el portal de Cloud App Security, vaya al engranaje Configuración y elija **Control de aplicaciones de acceso condicional**. 
    
     ![Menú Proxy](./media/proxy-menu.png)

2. Debería ver un mensaje que informa de que el control de aplicaciones de acceso condicional ha detectado nuevas aplicaciones de Azure AD. Haga clic en el vínculo **Vea las aplicaciones nuevas**.

   ![Vista de nuevas aplicaciones de control de aplicaciones de acceso condicional](./media/proxy-view-new-apps.png)

3. En el cuadro de diálogo que se abre verá todas las aplicaciones en las que inició sesión en el paso anterior. En cada aplicación, haga clic en el signo + y, después, haga clic en **Agregar**.

   ![Nuevas aplicaciones de control de aplicaciones de acceso condicional](./media/proxy-new-app.png)

   > [!NOTE]
   > Si una aplicación no aparece en el catálogo de aplicaciones de Cloud App Security, aparecerá en la sección Aplicación no identificada del cuadro de diálogo junto con la dirección URL de inicio de sesión. Si hace clic en el signo + de estas aplicaciones, tendrá la oportunidad de sugerir que la aplicación se incluya en el catálogo. Una vez que la aplicación esté incluida en el catálogo, vuelva a realizar los pasos para implementarla. 

4. En la tabla de aplicaciones de control de aplicaciones de acceso condicional, fíjese en la columna **Controles disponibles** y confirme que figuran en ella Acceso condicional de Azure AD y Control de sesión. <br></br>Si no aparece el control de sesión para una aplicación, eso significa que aún no está disponible para esa aplicación específica. Verá el vínculo **Solicitar control de sesión** en su lugar. Haga clic en él para abrir un cuadro de diálogo y solicitar la incorporación de la aplicación al control de la sesión. En este escenario, el equipo de Microsoft Cloud App Security procederá a realizar el proceso de incorporación de la aplicación junto con usted.
  
   ![Solicitar control de la sesión](./media/proxy-view-new-apps.png)

5. Opcional: identifique los dispositivos que usan certificados de cliente:

   1. Vaya al engranaje Configuración y elija **Identificación de dispositivos**.

   2. Cargue un certificado raíz.

      ![Identificación de dispositivos](./media/device-identification.png)
 
      Tras cargar el certificado, puede crear directivas de acceso y sesión basadas en la configuración de la opción **Etiqueta de dispositivo** y **Certificado de cliente válido**.
 
      > [!NOTE]
      >Solo se solicitará un certificado a un usuario si la sesión coincide con una directiva que usa el filtro de certificado de cliente válido. 

## <a name="test-the-deployment"></a>Probar la implementación

1. Primero, cierre cualquier sesión existente. Después, intente iniciar sesión en cada aplicación que se ha implementado correctamente. Inicie sesión con un usuario que coincida con la directiva configurada en Azure AD. 

2. En el portal de Cloud App Security en **Investigar**, seleccione **Registro de actividad** y asegúrese de que se capturan las actividades de inicio de sesión de cada aplicación.

3. Puede filtrar haciendo clic en **Avanzadas** y, luego, filtrar estableciendo que **Origen sea igual a Acceso condicional de Azure Active Directory**.

    ![Filtrar por Acceso condicional de Azure AD](./media/sso-logon.png)

4. Se recomienda que inicie sesión en aplicaciones de escritorio y móviles desde dispositivos administrados y no administrados. Esto es para asegurarse de que las actividades se capturan correctamente en el registro de actividad.<br></br>
   Para confirmar que la actividad se captura correctamente, haga clic en un registro de inicio de sesión único en la actividad para abrir el cajón de actividad. Asegúrese de que la propiedad **Etiqueta de agente de usuario** refleja correctamente si el dispositivo es un cliente nativo (es decir, un aplicación de escritorio o móvil) o si es un dispositivo administrado (Compatible, Unido a dominio o Certificado de cliente válido).
 
   ![Comprobar la etiqueta de agente de usuario](./media/domain-joined.png)


Ya tiene todo listo para crear [directivas de acceso](access-policy-aad.md) y [de sesión](session-policy-aad.md) para controlar las aplicaciones del control de aplicaciones de acceso condicional.


>[!div class="step-by-step"]
[« Anterior: Introducción al control de aplicaciones de acceso condicional](proxy-intro-aad.md)<br>
[Siguiente: Cómo crear una directiva de sesión »](session-policy-aad.md)


## <a name="next-steps"></a>Pasos siguientes 
[Trabajo con el control de aplicaciones de acceso condicional de Cloud App Security](proxy-intro-aad.md)   

[Los clientes Premier también pueden crear una solicitud de soporte técnico directamente en el portal Premier.](https://premier.microsoft.com/)  
  