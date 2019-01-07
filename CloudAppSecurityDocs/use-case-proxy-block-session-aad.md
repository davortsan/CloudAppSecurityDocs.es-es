---
title: Bloqueo de las descargas desde dispositivos no administrados con el control de aplicaciones de acceso condicional de Cloud App Security
description: En este artículo se describe el escenario donde usar las funciones de proxy inverso de Azure AD para proteger la organización de descargas de información confidencial con dispositivos no administrados.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 12/14/2018
ms.topic: conceptual
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 06238ebc-2088-4372-9412-96cceaf3b145
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: aab9063ad057abfe3dce3860494b1d20abe74f0f
ms.sourcegitcommit: 420a0119513e3f4a8651f6a9e66c56fe442a31c0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/13/2018
ms.locfileid: "53347345"
---
# <a name="block-downloads-of-sensitive-information-using-microsoft-cloud-app-security-conditional-access-app-control"></a>Bloqueo de descargas de información confidencial con el control de aplicaciones de acceso condicional de Microsoft Cloud App Security

*Se aplica a: Microsoft Cloud App Security*

>[!div class="step-by-step"]
[« ANTERIOR: Cómo crear una directiva de acceso](access-policy-aad.md)

Los administradores de TI de hoy en día se encuentran entre la espada y la pared. Quiere permitir que los empleados sean productivos. Para ello, hay que permitirles el acceso a aplicaciones, de forma que puedan trabajar en cualquier momento y desde cualquier dispositivo. Pero quiere proteger los activos de la empresa, incluida la información propietaria y con privilegios. ¿Cómo se puede permitir el acceso de los empleados a las aplicaciones en la nube y, al mismo tiempo, proteger los datos? **En este caso de uso se describe cómo bloquear las descargas de los usuarios que tienen acceso a los datos confidenciales en las aplicaciones en la nube de la empresa desde dispositivos no administrados o ubicaciones de red no corporativas.**

## <a name="the-threat"></a>La amenaza

Un administrador de cuentas de la organización quiere consultar algo en Salesforce desde casa durante el fin de semana en su portátil personal. Los datos de Salesforce pueden incluir desde información de la tarjeta de crédito de un cliente hasta información de carácter personal. El equipo doméstico no está administrado. Si descarga los documentos de Salesforce en el equipo, puede estar infectado con malware. En caso de que se pierda el equipo o de que alguien lo robe, puede que no esté protegido por contraseña y que cualquier persona que lo encuentre tenga acceso a información confidencial.

## <a name="the-solution"></a>La solución

Para proteger la organización, supervise y controle el uso de la aplicación en la nube usando el acceso condicional de Azure AD y el control de aplicaciones de acceso condicional de Microsoft Cloud App Security.  

## <a name="prerequisites"></a>Requisitos previos

- Una licencia válida de Azure AD Premium P1
- Haber configurado una aplicación en la nube para SSO en Azure AD  
- Haber [implementado la aplicación en Cloud App Security](proxy-deployment-aad.md)

## <a name="create-a-block-download-policy-for-unmanaged-devices"></a>Crear una directiva de bloqueo de descarga en dispositivos no administrados  

Las directivas de sesión de Cloud App Security le permiten restringir una sesión según el estado del dispositivo. Para conseguir controlar una sesión mediante el dispositivo como condición, cree tanto una directiva de acceso condicional COMO una directiva de sesión.

### <a name="step-1-create-an-azure-ad-conditional-access-policy"></a>Paso 1: Crear una directiva de acceso condicional de Azure AD

1. Cree una directiva de acceso condicional de Azure AD con usuarios asignados y una aplicación.
2. Active **Use Conditional Access App Control enforced restrictions** (Usar las restricciones que exige el control de aplicaciones de acceso condicional) en los controles de sesión de la directiva de acceso condicional.

Tras completar esta tarea, vaya al portal de Cloud App Security y cree una directiva de sesión para supervisar y controlar las descargas de archivos en la sesión.

### <a name="step-2-create-a-session-policy"></a>Paso 2: Crear una directiva de sesión

1. En el portal de Cloud App Security, seleccione **Control** y, después, **Directivas**. 

2. En la página **Directivas**, haga clic en **Crear directiva** y, después, en **Directiva de sesión**.
 
3. En la página **Creación de directivas de sesión**, especifique un nombre y una descripción para la directiva. Por ejemplo, **Bloquear descargas desde Salesforce con dispositivos no administrados**.

4. Asigne una **Gravedad de directiva** y una **Categoría**.

5. En **Tipo de control de sesión**, seleccione **Controlar la descarga de archivos (con DLP)**. Esta configuración le proporciona la capacidad de supervisar todo lo que hacen los usuarios en una sesión de Salesforce, así como control para bloquear y proteger las descargas en tiempo real.

6. En **Origen de actividad** en la sección **Actividades que coinciden con todo lo siguiente**, seleccione estos filtros: 

   - **Etiqueta de dispositivo**: seleccione **No es igual a** y después seleccione **Conforme**, **Unido a dominio** o **Certificado de cliente válido**. La selección depende del método que se usa en su organización para identificar los dispositivos administrados. 

   - **Aplicación**: seleccione la aplicación que quiera controlar.  

   - **Usuarios**: seleccione los usuarios que quiera supervisar.  

7. Como alternativa, puede bloquear las descargas desde ubicaciones que no forman parte de la red corporativa. En **Origen de actividad** en la sección **Actividades que coinciden con todo lo siguiente**, establezca los siguientes filtros:

   - **Dirección IP** o **Ubicación**: puede usar cualquiera de estos dos parámetros para identificar las ubicaciones desconocidas o no corporativas desde las que un usuario podría estar intentando acceder a información confidencial.

     > [!NOTE]
     > Si quiere bloquear las descargas TANTO desde dispositivos no administrados como desde ubicaciones no corporativas, tendrá que crear dos directivas de sesión. Establezca en una directiva el **Origen de actividad** mediante la ubicación. Establezca en la otra directiva el **Origen de actividad** en dispositivos no administrados.

   - **Aplicación**: seleccione la aplicación que quiera controlar.

   - **Usuarios**: seleccione los usuarios que quiera supervisar.  

8. Establezca los siguientes filtros en la sección **Archivos que coinciden con todo lo siguiente** de **Origen de la actividad**: 

   - **Etiquetas de clasificación**: si usa etiquetas de clasificación de Azure Information Protection, filtre los archivos por una etiqueta de clasificación concreta de Azure Information Protection.

   - Seleccione **Nombre de archivo** o **Tipo de archivo** para aplicar restricciones basadas en el nombre o el tipo de archivo.
9. Habilite **Inspección de contenido** para permitir que la DLP interna examine los archivos en busca de contenido confidencial. 

10. En **Acciones**, seleccione **bloquear**. Personalice el mensaje de bloqueo que verán los usuarios cuando no puedan descargar archivos.  

11. Establezca las alertas que quiera recibir cuando coincida la directiva. Puede establecer un límite para no recibir demasiadas alertas. Seleccione si quiere recibir las alertas como mensaje de correo electrónico, de texto o ambos.

12. Haga clic en **Crear**.  

## <a name="validate-your-policy"></a>Validar la directiva

1. Para simular la descarga de archivos bloqueada, inicie sesión en la aplicación desde un dispositivo no administrado o una ubicación de red no corporativa. Después, intente descargar un archivo.

2. El archivo debería estar bloqueado y debería recibir el mensaje que configuró en **Personalizar el mensaje de bloqueo**. 

3. En el portal de Cloud App Security, haga clic en **Control** y **Directivas** y, después, en la directiva que ha creado para ver el informe de directiva. Una coincidencia de directiva de sesión debe aparecer en breve. 

4. En el informe de directiva puede ver los inicios de sesión que se han redirigido a Microsoft Cloud App Security para someterlos a un control de sesión, así como los archivos que se han descargado o bloqueado en las sesiones supervisadas.

>[!div class="step-by-step"]
[« ANTERIOR: Cómo crear una directiva de acceso](access-policy-aad.md)

## <a name="next-steps"></a>Pasos siguientes
  
[Creación de directivas de sesión](session-policy-aad.md)   

[Los clientes Premier también pueden crear una solicitud de soporte técnico directamente en el portal Premier.](https://premier.microsoft.com/)  
  
  