---
title: Implementar Control de aplicaciones de acceso condicional de Cloud App Security para las aplicaciones
description: En este artículo se proporciona información sobre cómo implementar las características de Microsoft Cloud App Security Control de aplicaciones de acceso condicional proxy inverso para las aplicaciones.
keywords: ''
author: ShlomoSagir-MS
ms.author: shsagir
manager: ShlomoSagir-MS
ms.date: 7/18/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.suite: ems
ms.openlocfilehash: 7b86bc5f344f097c4c4e45c9d25123c5b361ebb2
ms.sourcegitcommit: e9c93f69f280a929b2802619d24f59ea830b783f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2019
ms.locfileid: "68782876"
---
# <a name="onboard-and-deploy-conditional-access-app-control-for-any-app"></a>Incorporación e implementación de Control de aplicaciones de acceso condicional para cualquier aplicación

*Se aplica a: Microsoft Cloud App Security*

>[!div class="step-by-step"]
[« Anterior: Implementar Control de aplicaciones de acceso condicional para aplicaciones destacadas](proxy-deployment-aad.md)<br>
[Siguiente: Cómo crear una directiva de sesión »](session-policy-aad.md)

Los controles de sesión de Microsoft Cloud App Security se pueden configurar para que funcionen con cualquier aplicación Web. En este artículo se describe cómo incorporar e implementar aplicaciones de línea de negocio personalizadas, aplicaciones SaaS no destacadas y aplicaciones locales hospedadas a través del proxy de aplicación de Azure Active Directory (Azure AD) con controles de sesión.

Para obtener una lista de las aplicaciones que se incluyen en Cloud App Security trabajar de forma integrada, consulte [proteger aplicaciones con Microsoft Cloud App Security control de aplicaciones de acceso condicional](proxy-intro-aad.md).

## <a name="prerequisites"></a>Requisitos previos

- Su organización debe tener las licencias siguientes para usar Control de aplicaciones de acceso condicional:

  - Azure Active Directory Premium P1 o superior
  - Microsoft Cloud App Security

- Las aplicaciones deben configurarse con el inicio de sesión único en Azure AD
- Las aplicaciones deben usar los protocolos SAML o Open ID Connect 2,0

## <a name="to-deploy-any-app"></a>Para implementar cualquier aplicación

Siga estos pasos para configurar cualquier aplicación que se controlará Cloud App Security Control de aplicaciones de acceso condicional.

**Paso 1: [Configure Azure AD Directiva de acceso condicional para enrutar las aplicaciones relevantes a Cloud App Security](#conf-azure-ad)**

**Paso 2: [Configurar los usuarios que van a implementar la aplicación](#conf-users)**

**Paso 3: [Configuración de la aplicación que se está implementando](#conf-app)**

**Paso 4: [Agregar los dominios de la aplicación](#add-domains)**

**Paso 5: [Comprobar que la aplicación funciona correctamente](#verify-app)**

**Paso 6: [Habilitación de la aplicación para su uso en su organización](#enable-app)**

**Paso 7: [Actualización de la Directiva de Azure AD](#update-azure-ad)**

> [!NOTE]
> Para implementar Control de aplicaciones de acceso condicional para aplicaciones de Azure AD, necesita una [licencia válida para Azure Active Directory Premium P1 o superior](https://docs.microsoft.com/azure/active-directory/license-users-groups) , así como una licencia de Cloud App Security.

## Paso 1: Configure Azure AD Directiva de acceso condicional para enrutar las aplicaciones relevantes a Cloud App Security<a name="conf-azure-ad"></a>  

1. En Azure ad, explorador para el**acceso condicional**de **seguridad** > .

1. En la hoja **acceso condicional** , en la barra de herramientas de la parte superior, haga clic en **nueva Directiva**.

1. En la hoja **nuevo** , en el cuadro de texto **nombre** , escriba el nombre de la Directiva.

1. En **asignaciones**, haga clic en **usuarios y grupos**, asigne los usuarios que van a incorporar (inicio de sesión y comprobación iniciales) a la aplicación y, a continuación, haga clic en **listo**.

1. En **asignaciones**, haga clic en **aplicaciones en la nube**, asigne las aplicaciones que quiera controlar con control de aplicaciones de acceso condicional y, a continuación, haga clic en **listo**.

1. En **controles de acceso**, haga clic en **sesión**, seleccione **usar control de aplicaciones de acceso condicional** y elija las directivas integradas (**supervisar solo** o **bloquear descargas**) o **use la directiva personalizada** para establecer una directiva avanzada en la nube. Seguridad de la aplicación y, a continuación, haga clic en **seleccionar**.

   ![Acceso condicional de Azure AD](./media/azure-ad-caac-policy.png)

1. Opcional: Agregue condiciones y conceda controles según sea necesario.

1. Establezca **Habilitar Directiva** en **activado** y, a continuación, haga clic en **crear**.

## Paso 2: Configurar los usuarios que van a implementar la aplicación<a name="conf-users"></a>

1. En Cloud App Security, en la barra de menús, haga clic en el engranaje de configuración ![icono]de configuración icono de(./media/settings-icon.png "configuración") y seleccione **configuración**.

1. En **control de aplicaciones de acceso condicional**, seleccione **incorporación/mantenimiento**de la aplicación.

1. Escriba el nombre principal de usuario o el correo electrónico de los usuarios que van a incorporar la aplicación y, a continuación, haga clic en **Guardar**.

    ![Captura de pantalla de la configuración de incorporación y mantenimiento de la aplicación.](media/app-onboarding-settings.png)

## Paso 3: Configuración de la aplicación que se está implementando<a name="conf-app"></a>

1. Vaya a la aplicación que va a implementar. Si se reconoce el dominio de la aplicación, se le pedirá que continúe con el proceso de configuración de la aplicación. Si no se reconoce el dominio de la aplicación, se le pedirá que configure los dominios de la aplicación. Haga clic en **configurar aplicación** y continúe [agregando los dominios de la aplicación](#add-domains).

    > [!NOTE]
    > En el caso de los dominios de aplicación reconocidos, asegúrese de que la aplicación esté configurada con todos los dominios necesarios para que la aplicación funcione correctamente. Para configurar dominios adicionales, siga [agregando los dominios de la aplicación](#add-domains).

1. Repita los pasos siguientes para instalar la **entidad de certificación actual** y los certificados raíz autofirmados de la **entidad de certificación** .
    1. Seleccione el certificado.
    1. Haga clic en **abrir**y, cuando se le pida, haga clic en **abrir** de nuevo.
    1. Haga clic en **instalar certificado**.
    1. Elija el **usuario actual** o el **equipo local**.
    1. Seleccione **colocar todos los certificados en el siguiente almacén** y, a continuación, haga clic en **examinar**.
    1. Seleccione **entidades de certificación raíz de confianza** y, a continuación, haga clic en **Aceptar**.
    1. Haga clic en **Finalizar**

    > [!NOTE]
    > Para que se reconozcan los certificados, una vez que haya instalado el certificado, debe reiniciar el explorador e ir a la misma página.<!-- You'll see a check-mark by the certificates links confirmation they are installed.-->

1. Haga clic en **Continue**.

## Paso 4: Agregar los dominios de la aplicación<a name="add-domains"></a>

La Asociación de los dominios correctos a una aplicación permite Cloud App Security para aplicar directivas y actividades de auditoría.

Por ejemplo, si ha configurado una directiva que bloquea la descarga de archivos para un dominio asociado, se bloqueará la descarga de archivos por parte de la aplicación de ese dominio. Sin embargo, las descargas de archivos de la aplicación de dominios que no estén asociados a la aplicación no se bloquearán y la acción no se auditará en el registro de actividad.
> [!NOTE]
> Cloud App Security sigue agregando un sufijo a los dominios que no están asociados a la aplicación para garantizar una experiencia de usuario sin problemas.

1. Desde la aplicación, en la barra de herramientas del administrador de Cloud App Security, haga clic en **dominios detectados**.
    > [!NOTE]
    > La barra de herramientas de administración solo es visible para los usuarios con permisos para incorporar o mantener aplicaciones.
1. En el panel dominios detectados, tome nota de los nombres de dominio o exporte la lista como archivo. csv.
    > [!NOTE]
    > El panel muestra una lista de dominios detectados que no están asociados en la aplicación. Los nombres de dominio son completos.
1. Vaya a Cloud App Security, en la barra de menús, haga clic en el engranaje de configuración icono de configuración ![icono]de(./media/settings-icon.png "configuración") y seleccione **control de aplicaciones de acceso condicional**.
1. En la lista de aplicaciones, en la fila en la que aparece la aplicación que va a implementar, elija los tres puntos al final de la fila y, luego, en detalles de la **aplicación**, elija **Editar**.
    > [!TIP]
    > Para ver la lista de los dominios configurados en la aplicación, haga clic en **Ver dominios de aplicación**.
1. En **dominios definidos por el usuario**, escriba todos los dominios que desea asociar a esta aplicación y, a continuación, haga clic en **Guardar**.
    > [!NOTE]
    > Puede usar el carácter comodín * como un marcador de posición para cualquier carácter. Al agregar dominios, decida si desea agregar dominios específicos (`sub1.contoso.com`,`sub2.contoso.com`) o varios dominios (`*.contoso.com`).

## Paso 5: Comprobar que la aplicación funciona correctamente<a name="verify-app"></a>

1. Compruebe que el flujo de inicio de sesión funciona correctamente.
    <!--
    > [!NOTE]
    > Some apps issue a nonce hash during authentication that may break the sign-in process. If this happens, see the Troubleshooting Guide to resolve the issue.-->
1. Una vez que esté en la aplicación, realice las siguientes comprobaciones:
    1. Visite todas las páginas de la aplicación que forman parte del proceso de trabajo de los usuarios y compruebe que las páginas se representan correctamente.
    1. Compruebe que el comportamiento y la funcionalidad de la aplicación no se ven afectados por la realización de acciones comunes, como la descarga y la carga de archivos.
    1. Revise la lista de dominios asociados a la aplicación. Para obtener más información, consulte [Agregar los dominios de la aplicación](#add-domains).

## Paso 6: Habilitación de la aplicación para su uso en su organización<a name="enable-app"></a>

Una vez que esté listo para habilitar la aplicación para su uso en el entorno de producción de su organización, siga estos pasos.

1. En Cloud App Security, en la barra de menús, haga clic en el engranaje de configuración icono de configuración ![icono]de(./media/settings-icon.png "configuración") y seleccione **control de aplicaciones de acceso condicional**.
1. En la lista de aplicaciones, en la fila en la que aparece la aplicación que va a implementar, elija los tres puntos al final de la fila y, después, elija **Editar aplicación**.
1. Seleccione **usar con control de aplicaciones de acceso condicional** y, a continuación, haga clic en **Guardar**.

## Paso 7: Actualización de la Directiva de Azure AD<a name="update-azure-ad"></a>

1. En Azure AD, en **seguridad**, haga clic en **acceso condicional**.
1. Actualice la Directiva que creó anteriormente para incluir los usuarios, los grupos y los controles pertinentes que necesite.
1. En**uso**de **sesión** > control de aplicaciones de acceso condicional, si seleccionó **usar directiva personalizada**, vaya a Cloud App Security y cree una directiva de sesión correspondiente. Para obtener más información, consulte [Directivas de sesión](session-policy-aad.md).

>[!div class="step-by-step"]
[« Anterior: Implementar Control de aplicaciones de acceso condicional para aplicaciones destacadas](proxy-deployment-aad.md)<br>
[Siguiente: Cómo crear una directiva de sesión »](session-policy-aad.md)

## <a name="next-steps"></a>Pasos siguientes 
[Trabajo con el control de aplicaciones de acceso condicional de Cloud App Security](proxy-intro-aad.md)

[Los clientes Premier también pueden crear una solicitud de soporte técnico directamente en el portal Premier.](https://premier.microsoft.com/)