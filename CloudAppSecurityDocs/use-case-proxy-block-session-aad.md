---
title: Cómo bloquear las descargas de datos confidenciales en dispositivos no administrados con el proxy de Cloud App Security | Microsoft Docs
description: En este tema se describe el escenario donde usar las capacidades del proxy de Azure AD para proteger la organización de descargas de datos confidenciales con dispositivos no administrados.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 4/22/2018
ms.topic: article
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 06238ebc-2088-4372-9412-96cceaf3b145
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: eb0e0eef92181f14d83f6c4c5eaf30023b5d80da
ms.sourcegitcommit: 45311f2cafef79483e40d971a4c61c7673834d96
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2018
---
*Se aplica a: Microsoft Cloud App Security*


# <a name="blocking-downloads-of-sensitive-information-using-the-microsoft-cloud-app-security-proxy"></a>Bloqueo de descargas de información confidencial con el proxy de Microsoft Cloud App Security


Hoy día, los administradores de TI se encuentran entre la espada y la pared: los empleados deben ser productivos. Para ello, hay que permitirles el acceso a aplicaciones, de forma que puedan trabajar en cualquier momento y desde cualquier dispositivo. Por otra parte, quiere proteger los activos de la empresa, y eso incluye la información propietaria y con privilegios. ¿Cómo se puede permitir el acceso de los empleados a las aplicaciones en la nube y, al mismo tiempo, proteger los datos? **En este caso de uso se describe cómo bloquear las descargas de los usuarios que tienen acceso a los datos confidenciales en las aplicaciones en la nube de la empresa desde dispositivos no administrados o ubicaciones de red no corporativas.**


## <a name="the-threat"></a>La amenaza
Un administrador de cuentas de la organización quiere consultar algo en Salesforce desde casa durante el fin de semana en su portátil personal. Esos datos de Salesforce pueden ser desde información de la tarjeta de crédito de un cliente a información de carácter personal. El equipo doméstico no está administrado, lo que significa que, si descarga los documentos de Salesforce en él, puede estar infectado con malware o, si se pierde o lo roban, puede no estar protegido por contraseña y cualquier persona que lo encuentre tendrá acceso a información confidencial. 

## <a name="the-solution"></a>La solución
Para proteger la organización, supervise y controle el uso de la aplicación en la nube usando el acceso condicional de Azure AD y el proxy de Cloud App Security.  

## <a name="prerequisites"></a>Requisitos previos

- Una licencia válida de Azure AD Premium P2
- Haber configurado una aplicación en la nube para SSO en Azure AD  
- Haber [implementado la aplicación en Cloud App Security](proxy-deployment-aad.md)

## <a name="create-a-block-download-policy-for-unmanaged-devices"></a>Crear una directiva de bloqueo de descarga en dispositivos no administrados  

Las directivas de sesión de Cloud App Security permiten restringir aún más una sesión según el estado del dispositivo. Cuando quiera controlar una sesión especificando el dispositivo como condición, es preciso crear TANTO una directiva de acceso condicional COMO una directiva de sesión para ello.  

### <a name="step-1-create-an-azure-ad-conditional-access-policy"></a>Paso 1: Crear una directiva de acceso condicional de Azure AD

1. Cree una directiva de acceso condicional de Azure AD con usuarios asignados y una aplicación.
2. Active **Usar las restricciones que exige el proxy** en los controles de sesión de la directiva de acceso condicional.   

   ![Acceso condicional de Azure AD](./media/proxy-deploy-restrictions-aad.png)

Tras completar esta tarea, vaya al portal de Cloud App Security y cree una directiva de sesión para supervisar y controlar las descargas de archivos en la sesión.

### <a name="step-2-create-a-session-policy"></a>Paso 2: Crear una directiva de sesión

1. En el portal de Cloud App Security, seleccione **Control** y, después, **Directivas**. 

2. En la página **Directivas**, haga clic en **Crear directiva** y, después, en **Directiva de sesión**.
 
   ![Creación de directivas de sesión](./media/create-session-policy.png)

3. En la página **Creación de directivas de sesión**, especifique un nombre y una descripción para la directiva. Por ejemplo, **Bloquear descargas desde Salesforce con dispositivos no administrados**.

4. Asigne una **Gravedad de directiva** y una **Categoría**.

   ![Nueva directiva de sesión](./media/new-session-policy.png)

5. En **Tipo de control de sesión**, seleccione **Controlar la descarga de archivos (con DLP)**. Esto le confiere la capacidad de supervisar todo lo que hacen los usuarios en una sesión de Salesforce, así como control para bloquear y proteger las descargas en tiempo real.

   ![Tipo de control de directiva de sesión](./media/session-policy-control-type.png)

6. En la sección **Actividades que coinciden con todo lo siguiente** de **Origen de la actividad**, seleccione estos filtros: 
    
   - **Etiqueta de dispositivo**: seleccione **No es igual a** y, después, seleccione **Compatible**, **Unido a dominio** o **Certificado de cliente válido**, según cuál sea el método empleado en su organización para identificar dispositivos administrados. 
    
   - **Aplicación**: seleccione la aplicación que quiera controlar.  

   - **Usuarios**: seleccione los usuarios que quiera supervisar.  
    
7. Si lo que quiere es bloquear las descargas en ubicaciones que no formen parte de su red corporativa, establezca los siguientes filtros en la sección **Actividades que coinciden con todo lo siguiente** de **Origen de la actividad**: 

   - **Dirección IP** o **Ubicación**: puede usar cualquiera de estos dos parámetros para identificar las ubicaciones desconocidas o no corporativas desde las que un usuario podría estar intentando tener acceso a datos confidenciales.

     > [!NOTE]
     > Si quiere bloquear las descargas TANTO en dispositivos no administrados COMO en ubicaciones no corporativas, será necesario crear dos directivas de sesión, una que tenga **Origen de la actividad** configurado en la ubicación y otra que tenga **Origen de la actividad** configurado en dispositivos no administrados.
 
   - **Aplicación**: seleccione la aplicación que quiera controlar.    
   
   - **Usuarios**: seleccione los usuarios que quiera supervisar.  

8. Establezca los siguientes filtros en la sección **Archivos que coinciden con todo lo siguiente** de **Origen de la actividad**: 
   
   - **Etiquetas de clasificación**: le servirá si usa etiquetas de clasificación de Azure Information Protection y quiere filtrar los archivos por una etiqueta de clasificación concreta de Azure Information Protection.
   
   - Seleccione **Nombre de archivo** o **Tipo de archivo** para aplicar restricciones basadas en alguna de estas cuestiones.
 
     ![Filtros de archivo de directiva de sesión](./media/session-policy-file-filters.png)

9. Habilite **Inspección de contenido** para permitir que la DLP interna examine los archivos en busca de contenido confidencial. 

   ![Inspección de contenido de directiva de sesión](./media/session-policy-content-inspection.png)

10. En **Acciones**, seleccione **bloquear**. Personalice el mensaje de bloqueo que los usuarios verán cuando no puedan descargar archivos.  

    ![Acciones de directiva de sesión](./media/session-policy-actions.png)

11. Establezca las alertas que quiera recibir cuando coincida la directiva. Puede establecer un límite para no recibir demasiadas alertas y seleccionar si quiere recibirlas como un mensaje de correo electrónico, un mensaje de texto o ambos.

    ![Alertas de directiva de sesión](./media/session-policy-alert.png)


12. Haga clic en **Crear**.  
 

## <a name="validate-your-policy"></a>Validar la directiva 

1. Para simular la descarga de archivo bloqueada, inicie sesión en la aplicación desde un dispositivo no administrado o una ubicación de red no corporativa e intente descargar un archivo. 

2. El archivo debería estar bloqueado y debería recibir el mensaje que configuró en **Personalizar el mensaje de bloqueo**. 

   ![Mensaje de bloqueo de descarga](./media/block-download-message.png)

3. En el portal de Cloud App Security, haga clic en **Control** y **Directivas** y, después, en la directiva que ha creado para ver el informe de directiva. Una coincidencia de directiva de sesión debe aparecer en breve. 
 
   ![Informe de directiva de sesión](./media/session-policy-report.png)

4. En el informe de directiva puede ver los inicios de sesión que se han redirigido al proxy para someterlos a un control de sesión, así como los archivos que se han descargado o bloqueado en las sesiones supervisadas.




## <a name="see-also"></a>Consulte también  
[Creación de directivas de sesión](session-policy-aad.md)   

[Los clientes Premier también pueden elegir Cloud App Security directamente desde el Portal Premier.](https://premier.microsoft.com/)  
  
  