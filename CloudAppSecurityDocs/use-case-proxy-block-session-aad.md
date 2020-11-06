---
title: Bloqueo de las descargas desde dispositivos no administrados con control de aplicaciones de acceso condicional de Cloud App Security
description: En este tutorial se describe el escenario para proteger su organización frente a las descargas de datos confidenciales por parte de dispositivos no administrados mediante funcionalidades de proxy inverso de Azure AD.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 03/31/2020
ms.topic: tutorial
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 3dec3c1729d63649a754098ace7f638ccc3029bc
ms.sourcegitcommit: e711727f2f00ee3b54e08337a5040449e352ca46
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/02/2020
ms.locfileid: "93185940"
---
# <a name="tutorial-block-download-of-sensitive-information"></a>Tutorial: Bloqueo de la descarga de información confidencial

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Los administradores de TI de hoy en día se encuentran entre la espada y la pared. Por una parte, quiere permitir que los empleados sean productivos. Para ello, hay que permitirles el acceso a aplicaciones, de forma que puedan trabajar en cualquier momento y desde cualquier dispositivo. Pero por otra parte, quiere proteger los activos de la empresa, incluida la información propietaria y con privilegios. ¿Cómo se puede permitir el acceso de los empleados a las aplicaciones en la nube y, al mismo tiempo, proteger los datos? **En este tutorial se describe cómo bloquear las descargas de los usuarios que tienen acceso a datos confidenciales en las aplicaciones en la nube de la empresa desde dispositivos no administrados o ubicaciones de red no corporativas.**

> [!div class="checklist"]
>
> * Creación de una directiva de bloqueo de descarga para dispositivos no administrados
> * Validación de la directiva

## <a name="the-threat"></a>La amenaza

Un administrador de cuentas de la organización quiere consultar algo en Salesforce desde casa durante el fin de semana en su portátil personal. Los datos de Salesforce pueden incluir desde información de la tarjeta de crédito de un cliente hasta información de carácter personal. El equipo doméstico no está administrado. Si descarga los documentos de Salesforce en el equipo, puede estar infectado con malware. En caso de que se pierda el dispositivo o de que alguien lo robe, puede que no esté protegido por contraseña y que cualquier persona que lo encuentre tenga acceso a información confidencial.

## <a name="the-solution"></a>La solución

Proteja su organización: supervise y controle el uso de las aplicaciones en la nube con cualquier solución IdP y el Control de aplicaciones de acceso condicional de Cloud App Security.

## <a name="prerequisites"></a>Requisitos previos

* Una licencia válida para Azure AD Premium P1 o la licencia que requiera la solución del proveedor de identidades (IdP).
* Configure una aplicación en la nube para inicio de sesión único con uno de los siguientes protocolos de autenticación:

    |IdP|Protocolos|
    |---|---|
    |Azure AD|SAML 2.0 u OpenID Connect|
    |Otros|SAML 2.0|
* Asegurarse de que la [aplicación se implementa en Cloud App Security](proxy-deployment-aad.md).

## <a name="create-a-block-download-policy-for-unmanaged-devices"></a>Creación de una directiva de bloqueo de descargas para dispositivos no administrados

Las directivas de sesión de Cloud App Security permiten restringir una sesión en función del estado del dispositivo. Para conseguir controlar una sesión mediante el dispositivo como condición, cree una directiva de acceso condicional Y una directiva de sesión.

### <a name="step-1-configure-your-idp-to-work-with-cloud-app-security"></a>Paso 1: Configurar el IdP para que funcione con Cloud App Security

Asegúrese de que ha configurado la solución IdP para que funcione con Cloud App Security, como se indica a continuación:

* En el caso del [acceso condicional de Azure AD](/azure/active-directory/active-directory-conditional-access-azure-portal), consulte [Configuración de la integración con Azure AD](proxy-deployment-aad.md#configure-integration-with-azure-ad).
* Para información sobre otras soluciones IdP, consulte [Configuración de la integración con otras soluciones IdP](proxy-deployment-aad.md#configure-integration-with-other-idp-solutions).

Después de completar esta tarea, vaya al portal de Cloud App Security y cree una directiva de sesión para supervisar y controlar las descargas de archivos en la sesión.

### <a name="step-2-create-a-session-policy"></a>Paso 2: Crear una directiva de sesión

1. En el portal de Cloud App Security, seleccione **Control** seguido de **Directivas**.

2. En la página **Directivas** , haga clic en **Crear directiva** seguido de **Directiva de sesión**.

3. En la página **Crear directiva de sesión** , asigne un nombre y una descripción a la directiva. Por ejemplo, **Bloquear descargas de Salesforce para dispositivos no administrados**.

4. Asigne una **gravedad de directiva** y una **categoría**.

5. En **Tipo de control de sesión** , seleccione **Controlar la descarga de archivos (con inspección)** . Esta configuración le permite supervisar todo lo que hacen los usuarios en una sesión de Salesforce y le ofrece control para bloquear y proteger las descargas en tiempo real.

6. En **Origen de actividad** en la sección **Actividades que coinciden con todo lo siguiente** , seleccione los filtros:

   * **Etiquetas de dispositivo** : seleccione **No es igual a** y, después, seleccione **Conforme con Intune** , **Unidos a Azure AD híbrido** o **Certificado de cliente válido**. La selección depende del método que se use en su organización para identificar los dispositivos administrados.

   * **Aplicación** : Seleccione la aplicación que desea controlar.

   * **Usuarios** : seleccione los usuarios que desea supervisar.

7. También puede bloquear las descargas de ubicaciones que no forman parte de la red corporativa. En **Origen de actividad** en la sección **Actividades que coinciden con todo lo siguiente** , configure los filtros siguientes:

   * **Dirección IP** o **Ubicación** : puede usar cualquiera de estos dos parámetros para identificar las ubicaciones desconocidas o no corporativas desde las que un usuario podría estar intentando acceder a información confidencial.

     > [!NOTE]
     > Si quiere bloquear las descargas TANTO desde dispositivos no administrados COMO desde ubicaciones no corporativas, tendrá que crear dos directivas de sesión. Una directiva establece el **origen de la actividad** de mediante la ubicación. La otra directiva establece el **origen de la actividad** en dispositivos no administrados.

   * **Aplicación** : Seleccione la aplicación que desea controlar.

   * **Usuarios** : seleccione los usuarios que desea supervisar.

8. En **Origen de actividad** en la sección **Archivos que coinciden con todo lo siguiente** , configure los filtros siguientes:

   * **Etiquetas de clasificación** : si usa etiquetas de clasificación de Azure Information Protection, filtre los archivos por una etiqueta de clasificación concreta de Azure Information Protection.

   * Seleccione **Nombre de archivo** o **Tipo de archivo** para aplicar las restricciones según el nombre o el tipo de archivo.
9. Habilite **Inspección de contenido** para permitir que la DLP interna examine los archivos en busca de contenido confidencial.

10. En **Acciones** seleccione **Bloquear**. Personalice el mensaje de bloqueo que verán los usuarios cuando no puedan descargar archivos.

11. Establezca las alertas que quiera recibir cuando coincida la directiva. Puede establecer un límite para no recibir demasiadas alertas. Seleccione si quiere recibir las alertas como mensaje de correo electrónico, de texto o ambos.

12. Haga clic en **Crear**.

## <a name="validate-your-policy"></a>Validación de la directiva

1. Para simular la descarga de archivos bloqueada, inicie sesión en la aplicación desde un dispositivo no administrado o una ubicación de red no corporativa. A continuación, intente descargar un archivo.

2. El archivo debería estar bloqueado y debería recibir el mensaje que configuró al **personalizar el mensaje de bloqueo**.

3. En el portal de Cloud App Security, haga clic en **Control** y **Policies** (Directivas) y, luego, en la directiva que ha creado para ver el informe de directiva. En breve debe aparecer una coincidencia de directiva de sesión.

4. En el informe de directiva puede ver los inicios de sesión que se han redirigido a Microsoft Cloud App Security para someterlos a un control de sesión, así como los archivos que se han descargado o bloqueado en las sesiones supervisadas.

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Procedimiento ara crear una directiva de acceso](access-policy-aad.md)

> [!div class="nextstepaction"]
> [Procedimiento ara crear una directiva de sesión](session-policy-aad.md)

[!INCLUDE [Open support ticket](includes/support.md)]