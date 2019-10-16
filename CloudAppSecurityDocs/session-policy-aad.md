---
title: Creación de directivas de sesión en Cloud App Security
description: En este artículo se describe el procedimiento para configurar una directiva de sesión de control de aplicaciones de acceso condicional de Cloud App Security para obtener visibilidad detallada de las actividades de la sesión del usuario y bloquear descargas por medio de las funciones de proxy inverso.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 12/10/2018
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 745df28a-654c-4abf-9c90-203841169f90
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 0288d0f5e570f8b129c7706fa29ad5c4d361c8bf
ms.sourcegitcommit: c342abeec95359ddabdabcc3a081a0f91d52407c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72336237"
---
# <a name="session-policies"></a>Directivas de sesión 

*Se aplica a: Microsoft Cloud App Security*

>[!div class="step-by-step"]
[«ANTERIOR: incorporación e implementación de Control de aplicaciones de acceso condicional para cualquier aplicación»](proxy-deployment-any-app.md)<br>
[SIGUIENTE: Cómo crear una directiva de acceso »](access-policy-aad.md)


Las directivas de sesión de Microsoft Cloud App Security permiten las supervisiones en tiempo real y en el nivel de sesión, lo que le proporciona una visibilidad granular de las aplicaciones en la nube, así como la posibilidad de realizar distintas acciones según la directiva establecida para una sesión de usuario. En lugar de [permitir o bloquear el acceso por completo](access-policy-aad.md), con el control de sesión, puede permitir el acceso mientras supervisa la sesión o limita determinadas actividades de la sesión usando las funciones de proxy inverso de control de aplicaciones de acceso condicional. 

Por ejemplo, puede decidir que, desde cualquier dispositivo no administrado o en sesiones que provienen de ubicaciones específicas, quiere permitir el acceso del usuario a la aplicación, pero también limitar la descarga de archivos confidenciales o requerir que algunos documentos estén protegidos al descargarse. Las directivas de sesión permiten establecer estos controles de sesión de usuario, ademas del acceso, y le permite realizar lo siguiente:

- [Supervisión de todas las actividades](#monitor-session)
- [Bloqueo de todas las descargas](#block-download)
- [Bloqueo de actividades específicas](#block-activities)
- [Protección de archivos en la descarga](#protect-download)
 
## <a name="prerequisites-to-using-session-policies"></a>Requisitos previos para usar directivas de sesión

- Tener una licencia de Azure AD Premium P1.
- Las aplicaciones en cuestión deben estar [implementadas con control de aplicaciones de acceso condicional](proxy-deployment-aad.md).
- Debe haber aplicada una [directiva de acceso condicional de Azure AD](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal) que redirija a los usuarios Microsoft Cloud App Security, tal y como se describe aquí.

> [!NOTE]
> Las directivas de sesión también admiten aplicaciones que estén configuradas con proveedores de identidades que no sean Azure AD. Para obtener más información sobre este escenario, envíe un correo electrónico a mcaspreview@microsoft.com.

## <a name="create-an-azure-ad-conditional-access-policy"></a>Crear una directiva de acceso condicional de Azure AD

Las directivas de acceso condicional de Azure Active Directory y las directivas de sesión de Cloud App Security funcionan conjuntamente para examinar cada sesión de usuario y tomar decisiones de directiva relativas a cada aplicación. Haga lo siguiente para configurar una directiva de acceso condicional en Azure AD:

1. Configure una [directiva de acceso condicional de Azure AD](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal) con asignaciones de usuario o de grupo de usuarios, y la aplicación que quiere controlar con el Control de aplicaciones de acceso condicional. 

   > [!NOTE]
   > Esta directiva afectará únicamente a las aplicaciones que se hayan [implementado con control de aplicaciones de acceso condicional](proxy-deployment-aad.md).

2. Enrute usuarios a Microsoft Cloud App Security; para ello, active **Use Conditional Access App Control enforced restrictions** (Usar las restricciones que exige el Control de aplicaciones de acceso condicional) en la página **Sesión**.

## <a name="create-a-cloud-app-security-session-policy"></a>Crear una directiva de sesión de Cloud App Security 

Haga lo siguiente para crear una directiva de sesión:

1. En el portal, seleccione **Control** y, después, **Directivas**.
2. En la página **Directivas**, haga clic en **Crear directiva** y seleccione **Directiva de sesión**.  

3. En la ventana **Directiva de sesión**, especifique un nombre para la directiva, como *Bloquear descarga de documentos confidenciales en Box de usuarios de marketing*.

4. En el campo **Tipo de control de sesión**, haga lo siguiente: 

   1. Seleccione **Monitor only** (Solo supervisar) si solo quiere supervisar las actividades de los usuarios. Esta selección creará una directiva de solo supervisión para las aplicaciones que seleccionó en la que, todos los inicios de sesión, descargas heurísticas y tipos de actividad, se descargarán.

   2. Seleccione **Controlar la descarga de archivos (con DLP)** si quiere supervisar las actividades del usuario. Puede realizar acciones adicionales como bloquear o proteger las descargas para los usuarios.
   
   3. Seleccione **Bloquear actividades** para bloquear actividades específicas que se pueden seleccionar con el filtro **Tipo de actividad**. Todas las actividades de las aplicaciones seleccionadas se supervisarán (y notificarán en el registro de actividad). Las actividades específicas que seleccione se bloquearán si selecciona la acción **Bloquear**. Las actividades específicas que seleccione generarán alertas si selecciona la acción **Probar** y hay alertas activadas.

5. En la sección **Actividades que coinciden con todo lo siguiente** de **Origen de la actividad**, seleccione más filtros de actividad para aplicarlos a la directiva. Los filtros incluyen las siguientes opciones: 

   - **Etiqueta de dispositivo**: use este filtro para identificar los dispositivos no administrados.

   - **Ubicación**: use este filtro para identificar las ubicaciones desconocidas (por tanto, que entrañan riesgo). 

   - **Dirección IP**: use este filtro para filtrar por direcciones IP o usar las etiquetas de dirección IP previamente asignadas. 

   - **Etiqueta de agente de usuario**: use este filtro para habilitar la heurística que permite identificar las aplicaciones de escritorio y móviles. Este filtro se puede establecer en "igual a" o "no es igual a" **Cliente nativo**. Este filtro se debe probar con las aplicaciones de escritorio y móviles para cada aplicación en la nube.
       
 
     >[!NOTE]
     >Las directivas de sesión no admiten aplicaciones de escritorio ni móviles. Las aplicaciones móviles y de escritorio también pueden bloquearse o permitirse con la creación de una directiva de acceso.

6. Si ha seleccionado la opción **Controlar la descarga de archivos (con DLP)**:

   1. En la sección **Archivos que coinciden con todo lo siguiente** de **Origen de la actividad**, seleccione más filtros de archivo para aplicarlos a la directiva. Los filtros incluyen las siguientes opciones:

      - **Etiqueta de clasificación**: use este filtro si la organización usa Azure Information Protection y los datos están protegidos con etiquetas de clasificación. Podrá filtrar los archivos por la etiqueta de clasificación que tengan aplicada. Para obtener más información sobre la integración con Azure Information Protection, vea [Integración de Azure Information Protection](azip-integration.md).

      - **Nombre de archivo**: use este filtro para aplicar la directiva a archivos concretos.

      - **Tipo de archivo**: use este filtro para aplicar la directiva a tipos de archivo concretos, por ejemplo, para bloquear la descarga de cualquier archivo .xls.
       
   2. En la sección **Inspección de contenido**, establezca si quiere permitir que el motor DLP examine documentos y el contenido de los archivos.
 
   3. En **Acciones**, seleccione uno de los siguientes elementos: 

      - **Test (Monitor all activities)** (Probar [supervisar todas las actividades]): establezca esta acción para permitir expresamente las descargas según los filtros de directiva que haya establecido.

      - **Block (Block file download and monitor all activities)** (Bloquear [bloquear descargas de archivos y supervisar todas las actividades]): establezca esta acción para bloquear expresamente las descargas según los filtros de directiva que haya establecido. Para más información, vea [Cómo funciona el bloqueo de descargas](#block-download).

      - **Protect (Apply classification label to download and monitor all activities)** (Proteger [aplicar etiqueta de clasificación para descargar y supervisar todas las actividades]): esta opción solo está disponible si seleccionó **Controlar la descarga de archivos (con DLP)** en **Directiva de sesión**. Si la organización usa Azure Information Protection, puede establecer una **acción** que aplique al archivo una etiqueta de clasificación establecida en Azure Information Protection. Para más información, vea [Cómo funciona la protección de descargas](#protect-download).

7. Puede **Crear una alerta para cada evento coincidente con la gravedad de la directiva** y establecer un límite de alerta. Seleccione si quiere que la alerta se envíe como mensaje de correo electrónico, de texto o ambos.


## Supervisión de todas las actividades <a name="monitor-session"></a>

Cuando se crea una directiva de sesión, cada sesión de usuario que coincida con la directiva se redirige al control de sesión, y no directamente a la aplicación. El usuario verá una notificación de supervisión que le avisa de que sus sesiones se están supervisando.

Si prefiere no avisar al usuario de que se le está supervisando, puede deshabilitar el mensaje de notificación.

1. En el engranaje Configuración, seleccione **Configuración general**. 

2. Después, en **Control de aplicación de acceso condicional**, active **Supervisión de usuarios** y desactive la casilla **Notificar a los usuarios**.

Para mantener al usuario dentro de la sesión, el control de aplicaciones de acceso condicional reemplaza todas las direcciones URL, scripts de Java y cookies pertinentes de la sesión de aplicación por direcciones URL de Microsoft Cloud App Security. Por ejemplo, si la aplicación devuelve una página con vínculos cuyos dominios terminan en miaplicación.com, el Control de aplicaciones de acceso condicional reemplazará esos vínculos por dominios que acaben en algo parecido a miaplicación.com.us.cas.ms. De esta forma, la sesión completa se supervisa por medio de Microsoft Cloud App Security.

El control de aplicaciones de acceso condicional crea registros de tráfico de cada sesión de usuario que pasa a través de él. Los registros de tráfico reflejan la hora, la dirección IP, los agentes de usuario, las direcciones URL visitadas y el número de bytes cargados y descargados. Estos registros se analizan, mientras que un informe constantemente activo denominado **Cloud App Security Conditional Access App Control** (Control de aplicaciones de acceso condicional de Cloud App Security) se agrega a la lista de informes de Cloud Discovery en el panel de Cloud Discovery.

Para exportar estos registros, haga lo siguiente:

1. Vaya al engranaje Configuración y haga clic en **Conditional Access App Control** (Control de aplicaciones de acceso condicional).
2. En el lado derecho de la tabla, haga clic en el botón de exportación.

   ![Botón de exportación](./media/export-button.png)
3. Seleccione el intervalo del informe y haga clic en **Exportar**. Este proceso puede tardar en completarse.

Para descargar el registro exportado:

1. Una vez que el informe esté listo, vaya a **Configuración** y después a **Informes exportados**.
2. En la tabla, seleccione el informe que proceda en la lista de **registros de tráfico del control de aplicaciones de acceso condicional** y haga clic en el botón de descarga.

     ![Botón de descarga](./media/download-button.png)


## Bloqueo de todas las descargas<a name="block-download"></a>

Cuando **Bloquear** es la **Acción** establecida que quiere realizar en la directiva de sesión de Cloud App Security, el control de aplicaciones de acceso condicional impedirá al usuario descargar un archivo de acuerdo con los filtros de archivos de la directiva. Microsoft Cloud App Security reconoce un evento de descarga para cada aplicación cuando un usuario inicia una descarga. El Control de aplicaciones de acceso condicional interviene en tiempo real para evitar que se ejecute. Cuando se recibe la señal de que un usuario ha iniciado una descarga, el control de aplicaciones de acceso condicional devuelve al usuario un mensaje que indica que la **descarga está restringida** y reemplaza el archivo descargado por un archivo de texto. El mensaje de dicho archivo se puede configurar y personalizar para el usuario en la directiva de sesión.  

## Bloqueo de actividades específicas<a name="block-activities"></a>

Cuando **Bloquear actividades** se establece como **Tipo de actividad**, pueden seleccionarse determinadas actividades para bloquear aplicaciones específicas. Todas las actividades de las aplicaciones seleccionadas se supervisarán y notificarán en el registro de actividad. Las actividades específicas que seleccione se bloquearán si selecciona la acción **Bloquear**. Las actividades específicas que seleccione generarán alertas si selecciona la acción **Probar** y hay alertas activadas.

**Bloquee actividades específicas** y aplíquelo a grupos específicos para crear un modo de solo lectura completo para la organización. 

## Protección de archivos en la descarga<a name="protect-download"></a>

Seleccione **Bloquear actividades** para bloquear actividades específicas que se pueden buscar con el filtro **Tipo de actividad**. Todas las actividades de las aplicaciones seleccionadas se supervisarán (y notificarán en el registro de actividad). Las actividades específicas que seleccione se bloquearán si selecciona la acción **Bloquear**. Las actividades específicas que seleccione generarán alertas si selecciona la acción **Probar** y hay alertas activadas.

Cuando **Proteger** es la **Acción** establecida que va a realizarse en la directiva de sesión de Cloud App Security, el control de aplicaciones de acceso condicional exige que el archivo se etiquete y proteja de acuerdo con los filtros de archivos de la directiva. Las etiquetas se configuran en la consola de Azure Information Protection y **Proteger** debe estar seleccionado en la etiqueta para que aparezca como una opción en la directiva de Cloud App Security. Cuando se selecciona una etiqueta y se descarga un archivo que cumple los criterios de la directiva de Cloud App Security, tanto la etiqueta como la protección correspondiente (con permisos) se aplican al archivo de descarga. El archivo original permanece tal cual en la aplicación en la nube, mientras que el archivo descargado ahora está protegido. Los usuarios que intenten acceder al archivo deben cumplir los requisitos de permiso establecidos por la protección aplicada.  
 
>[!div class="step-by-step"]
[«ANTERIOR: incorporación e implementación de Control de aplicaciones de acceso condicional para cualquier aplicación»](proxy-deployment-any-app.md)<br>
[SIGUIENTE: Cómo crear una directiva de acceso »](access-policy-aad.md)

## <a name="next-steps"></a>Pasos siguientes
 
[Blocking downloads on unmanaged devices using Azure AD Conditional Access App Control capabilities](use-case-proxy-block-session-aad.md) (Bloqueo de descargas en dispositivos no administrados con las funciones de control de aplicaciones de acceso condicional de Azure AD)   

[Los clientes Premier también pueden crear una solicitud de soporte técnico directamente en el portal Premier.](https://premier.microsoft.com/)  
  
  
