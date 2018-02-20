---
title: Implementar el proxy de Cloud App Security para aplicaciones de Azure AD | Microsoft Docs
description: "En este tema encontrará información sobre cómo implementar el proxy de Microsoft Cloud App Security para aplicaciones de Azure AD."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 1/15/2018
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: 2490c5e5-e723-4fc2-a5e0-d0a3a7d01fc2
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 8825f83de2bb7b7cb2ff236f0bffeeaeddf4c7f6
ms.sourcegitcommit: 458e936e1ac548eda37e9bf955b439199bbdd018
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/16/2018
---
# <a name="deploy-proxy-for-azure-ad-apps"></a>Implementar el proxy para aplicaciones de Azure AD

> [!NOTE]
> Se trata de una característica en vista previa.

Haga lo siguiente para configurar aplicaciones de Azure AD de forma que estén controladas por el proxy de Cloud App Security.

> [!NOTE]
> Si quiere implementar el proxy de Cloud App Security para aplicaciones de Azure AD, necesita una [licencia de Azure AD Premium P2](https://docs.microsoft.com/azure/active-directory/license-users-groups) válida.

## <a name="step-1-add-azure-ad-apps-in-cloud-app-security"></a>Paso 1: Agregar aplicaciones de Azure AD en Cloud App Security  

1. Cree una directiva de acceso condicional de Azure AD de prueba.

    1. En Azure Active Directory, en **Seguridad**, haga clic en **Acceso condicional**.

     ![Acceso condicional de Azure AD](./media/aad-conditional-access.png)

    2. Haga clic en **Nueva directiva** y cree una directiva asegurándose de que en **Sesión** selecciona **Usar las restricciones que exige el proxy**.

     ![Acceso condicional de Azure AD](./media/proxy-deploy-restrictions-aad.png)

    3. En la sección **Usuarios y grupos** de la directiva de prueba, asigne un usuario de prueba o un usuario que se pueda usar para un inicio de sesión inicial.
    
    4. En la sección **Aplicaciones en la nube** de la directiva de prueba, asigne las aplicaciones que quiera controlar con el proxy. 

     > [!NOTE]
     >Procure elegir aplicaciones que sean compatibles con el proxy. El proxy admite aplicaciones configuradas con un inicio de sesión único en SAML en Azure AD. Por ejemplo, las aplicaciones de Office 365 no están configuradas con SAML, por lo que no son compatibles actualmente.


2.  Una vez creada la directiva, inicie sesión en cada aplicación configurada en ella con un usuario también configurado en ella. Asegúrese de cerrar antes cualquier sesión existente.

3.  En el portal de Cloud App Security, vaya al engranaje Configuración y elija **Proxy**. 
    
      ![Menú Proxy](./media/proxy-menu.png)

4.  Debería ver un mensaje que informa de que el proxy ha detectado nuevas aplicaciones de Azure AD. Haga clic en el vínculo **Vea las aplicaciones nuevas**.

 ![Vínculo Vea las aplicaciones nuevas de proxy](./media/proxy-view-new-apps.png)

5.  En el cuadro de diálogo que se abre verá todas las aplicaciones en las que inició sesión en el paso anterior. En cada aplicación, haga clic en el signo + y, después, haga clic en **Agregar**.

 ![Nuevas aplicaciones de proxy](./media/proxy-new-app.png)

 > [!NOTE]
 > Si una aplicación no aparece en el catálogo de aplicaciones de Cloud App Security, aparecerá en la sección Aplicación no identificada del cuadro de diálogo junto con la dirección URL de inicio de sesión. Si hace clic en el signo + de estas aplicaciones, tendrá la oportunidad de sugerir que la aplicación se incluya en el catálogo. Una vez que la aplicación esté incluida en el catálogo, vuelva a realizar los pasos para implementarla. 

6.  En la tabla de aplicaciones de proxy, fíjese en la columna **Controles disponibles** y confirme que figuran en ella Acceso condicional de Azure AD y Control de sesión. <br></br>Si Control de sesión no aparece para una aplicación, significa que aún no está disponible para esa aplicación específica y, en su lugar, verá el vínculo **Solicitar control de la sesión**. Haga clic en él para abrir un cuadro de diálogo y solicitar la incorporación de la aplicación al control de la sesión. Durante el período de versión preliminar pública del proxy, el equipo de Cloud App Security procederá a realizar el proceso de incorporación de la aplicación junto con usted.
  
 ![Solicitar control de la sesión](./media/request-session-control.png)

7. Opcional: identifique los dispositivos que usan certificados de cliente:

      1. Vaya al engranaje Configuración y elija **Identificación de dispositivos**.

      2. Cargue un certificado raíz.

        ![Identificación de dispositivos](./media/device-identification.png)
 
       Tras cargar el certificado, puede crear directivas de acceso y sesión basadas en la configuración de la opción **Etiqueta de dispositivo** como igual a o no igual a **Certificado de cliente válido**.
 
      > [!NOTE]
      >Solo se solicitará un certificado a un usuario si la sesión coincide con una directiva que usa el filtro de certificado de cliente válido. 

## <a name="step-2-test-the-deployment"></a>Paso 2: Probar la implementación

1. Primero, cierre cualquier sesión existente. Luego, pruebe a iniciar sesión en cada aplicación implementada correctamente con un usuario que coincida con la directiva configurada en Azure AD. 

2.  En el portal de Cloud App Security en **Investigar**, seleccione **Registro de actividad** y asegúrese de que se capturan las actividades de inicio de sesión de cada aplicación.

3.  Puede filtrar haciendo clic en **Avanzadas** y, luego, filtrar estableciendo que **Origen sea igual a Acceso condicional de Azure Active Directory**.

     ![Filtrar por Acceso condicional de Azure AD](./media/sso-logon.png)

3. Es recomendable iniciar sesión en aplicaciones tanto de escritorio como móviles desde dispositivos administrados y no administrados para, de este modo, asegurarse de que las actividades se capturan correctamente en el registro de actividad.<br></br>
Para confirmar que la actividad se captura correctamente, haga clic en un registro de inicio de sesión único en la actividad para abrir el cajón de actividad y, después, asegúrese de que la propiedad **Etiqueta de agente de usuario** refleja correctamente si el dispositivo es un cliente nativo (es decir, un aplicación de escritorio o móvil) o si es un dispositivo administrado (Compatible, Unido a dominio o Certificado de cliente válido).
 
 ![Comprobar la etiqueta de agente de usuario](./media/domain-joined.png)


Ya está listo para crear [directivas de acceso](access-policy-aad.md) y [de sesión](session-policy-aad.md) para controlar las aplicaciones proxy.



## <a name="see-also"></a>Consulte también  
[Trabajo con el proxy de Cloud App Security](proxy-intro-aad.md)   

[Los clientes Premier también pueden elegir Cloud App Security directamente desde el Portal Premier.](https://premier.microsoft.com/)  
  