---
title: "Crear directivas de sesión para obtener visibilidad detallada de las actividades de la sesión del usuario y bloquear las descargas | Microsoft Docs"
description: "En este tema, se describe el procedimiento para configurar una directiva de sesión del proxy de Cloud App Security para obtener visibilidad detallada de las actividades de la sesión del usuario y bloquear las descargas."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 11/13/2017
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: 745df28a-654c-4abf-9c90-203841169f90
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: c955e20b4abd506f5e44659fbdd921bb54def131
ms.sourcegitcommit: eb4e70b6fa15cfff01932a711cecee38f67bc058
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/13/2017
---
# <a name="session-policies"></a>Directivas de sesión 

> [!NOTE]
> Se trata de una característica en vista previa.

Las directivas de sesión de Cloud App Security permiten las supervisiones en tiempo real y en el nivel de sesión, lo que le proporciona una visibilidad granular de las aplicaciones en la nube, así como la posibilidad de realizar distintas acciones según la directiva establecida para una sesión de usuario. En lugar de permitir o bloquear el acceso por completo, con el control de sesión puede permitir el acceso mientras supervisa la sesión y/o limitar determinadas actividades de la sesión. 

Por ejemplo, puede decidir que, desde cualquier dispositivo no administrado o en sesiones que provienen de ubicaciones específicas, quiere permitir el acceso del usuario a la aplicación, pero también limitar la descarga de archivos confidenciales o requerir que algunos documentos estén protegidos al descargarse. Las directivas de sesión permiten establecer estos controles de sesión de usuario. 

## <a name="prerequisites-to-using-session-policies"></a>Requisitos previos para usar directivas de sesión

- Tener una licencia de Azure AD Premium P2.
- Las aplicaciones en cuestión deben estar [implementadas con proxy](proxy-deployment-aad.md).
- Debe haber aplicada una [directiva de acceso condicional de Azure AD](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal) que redirija a los usuarios al proxy de Cloud App Security, tal y como se describe aquí.


## <a name="create-an-azure-ad-conditional-access-policy"></a>Crear una directiva de acceso condicional de Azure AD

Las directivas de acceso condicional de Azure Active Directory y las directivas de sesión de Cloud App Security funcionan conjuntamente para examinar cada sesión de usuario y tomar decisiones de directiva relativas a cada aplicación. Haga lo siguiente para configurar una directiva de acceso condicional en Azure AD:

1. Configure una [directiva de acceso condicional de Azure AD](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal) con asignaciones de usuario o de grupo de usuarios y la aplicación SAML que quiere controlar con el proxy de Cloud App Security. 

  > [!NOTE]
  > Esta directiva afectará únicamente a las aplicaciones que se hayan [implementado con proxy](proxy-deployment-aad.md).

2. Enrute usuarios al proxy de Cloud App Security; para ello, active **Usar las restricciones que exige el proxy** en la hoja **Sesión**.

 ![Acceso condicional de Azure AD con restricciones de proxy](./media/proxy-deploy-restrictions-aad.png)

## <a name="create-a-cloud-app-security-session-policy"></a>Crear una directiva de sesión de Cloud App Security 

Haga lo siguiente para crear una directiva de sesión:

1. En el portal, seleccione **Control** y, después, **Directivas**.
3. En la página **Directivas**, haga clic en **Crear directiva** y seleccione **Directiva de sesión**.  

 ![Creación de directivas de sesión](./media/create-session-policy.png)

4. En la ventana **Directiva de sesión**, especifique un nombre para la directiva, como *Bloquear descarga de documentos confidenciales en Box de usuarios de marketing*.

 ![Nueva directiva de sesión](./media/new-session-policy.png)

5. En el campo **Tipo de control de sesión**, haga lo siguiente: 

    1. Seleccione **Supervisión de todas las actividades** si solo quiere supervisar las actividades de los usuarios.

    2. Seleccione **Supervisión de todas las actividades y control de la descarga de archivos** si quiere supervisar las actividades de los usuarios y, asimismo, tomar otras medidas, como bloquear o proteger las descargas de los usuarios.

    ![Tipo de control de directiva de sesión](./media/session-policy-control-type.png)

6. En la sección **Actividades que coinciden con todo lo siguiente** de **Origen de la actividad**, seleccione más filtros de actividad para aplicarlos a la directiva. Las opciones son las siguientes: 

     - **Etiqueta de dispositivo**: use este filtro para identificar los dispositivos no administrados.

     - **Ubicación**: use este filtro para identificar las ubicaciones desconocidas (por tanto, que entrañan riesgo). 

     - **Dirección IP**: use este filtro para filtrar por direcciones IP o usar las etiquetas de dirección IP previamente asignadas. 

     - **Etiqueta de agente de usuario**: use este filtro para habilitar la heurística que permite identificar las aplicaciones de escritorio y móviles. Este filtro se puede establecer como igual o no igual a **Cliente nativo**, y conviene comprobarlo con las aplicaciones de escritorio y móviles de cada aplicación en la nube.
         
         ![Compatibilidad de cliente nativo](./media/user-agent-tag.png)

       >[!NOTE]
       >Las directivas de sesión no admiten aplicaciones de escritorio ni móviles. Asegúrese de probar las directivas de sesión para ver que no interfieren con la funcionalidad de este tipo de aplicaciones. Si es necesario, excluya de las directivas de sesión las aplicaciones de escritorio y móviles.

     ![Origen de actividad de directiva de sesión](./media/session-policy-activity-filters.png)

7. Si ha seleccionado la opción **Supervisión de todas las actividades y control de la descarga de archivos**:

    1. En la sección **Archivos que coinciden con todo lo siguiente** de **Origen de la actividad**, seleccione más filtros de archivo para aplicarlos a la directiva. Las opciones son las siguientes:

        - **Etiqueta de clasificación**: use este filtro si la organización usa Azure Information Protection y los datos están protegidos con etiquetas de clasificación. Si es así, aquí podrá filtrar los archivos por la etiqueta de clasificación que tengan aplicada. Para más información sobre la integración entre Cloud App Security y Azure Information Protection, vea [Integración de Azure Information Protection](azip-integration.md).

        - **Nombre de archivo**: use este filtro para aplicar la directiva a archivos concretos.

        - **Tipo de archivo**: use este filtro para aplicar la directiva a tipos de archivo concretos, por ejemplo, para bloquear la descarga de cualquier archivo .xls.

         ![Filtros de archivo de directiva de sesión](./media/session-policy-file-filters.png)

        
    2. En la sección **Inspección de contenido**, establezca si quiere permitir que el motor DLP examine documentos y el contenido de los archivos.
 
     ![Inspección de contenido de directiva de sesión](./media/session-policy-content-inspection.png)

    3. En **Acciones**, seleccione una de las siguientes opciones: 

        - **Permitir**: establezca esta acción para permitir expresamente las descargas según los filtros de directiva que haya establecido.

        - **Bloquear**: establezca esta acción para bloquear expresamente las descargas según los filtros de directiva que haya establecido. Para más información, vea [Cómo funciona el bloqueo de descargas](#block-download).

        - **Proteger**: si la organización usa Azure Information Protection, puede establecer una **acción** que aplique al archivo una etiqueta de clasificación establecida en Azure Information Protection. Para más información, vea [Cómo funciona la protección de descargas](#protect-download).

         ![Acciones de directiva de sesión](./media/session-policy-actions.png)

10. Puede **crear una alerta para cada evento que coincida con la gravedad de directiva**, establecer un límite de alerta y seleccionar si quiere que la alerta llegue como un correo electrónico, como un mensaje de texto o ambas.

    ![Alerta de directiva de sesión](./media/session-policy-alert.png)


## <a name="how-session-monitoring-works"></a>Cómo funciona la supervisión de sesión

Cuando se crea una directiva de sesión, cada sesión de usuario que coincida con la directiva se redirige al control de sesión de proxy, y no directamente a la aplicación. El usuario verá una notificación de supervisión que le avisa de que sus sesiones se están supervisando.

   ![Aviso de supervisión de sesión](./media/session-monitoring-notice.png)

Si prefiere no avisar al usuario de que se le está supervisando, puede deshabilitar el mensaje de notificación.

1. En el engranaje Configuración, seleccione **Configuración general**. 

2. Después, en Configuración del proxy de Cloud App Security, desactive la casilla **Notificar a los usuarios**.

    ![Deshabilitar el aviso de supervisión de sesión](./media/disable-session-monitoring-notice.png)

Para mantener al usuario dentro de la sesión, el proxy reemplaza todas las direcciones URL, scripts de Java y cookies pertinentes de la sesión de aplicación por direcciones URL del proxy. Por ejemplo, si la aplicación devuelve una página con vínculos cuyos dominios terminan en myapp.com, el proxy reemplazará esos vínculos por dominios que terminan en algo parecido a myapp.com.us.cas.ms. De esta forma, la sesión completa se supervisa por medio del proxy.

El proxy registra los registros de tráfico de cada sesión de usuario que pasa a través de él. Los registros de tráfico reflejan la hora, la dirección IP, los agentes de usuario, las direcciones URL visitadas y el número de bytes cargados y descargados. Estos registros se analizan, mientras que un informe constantemente activo denominado **Proxy de Cloud App Security** se agrega a la lista de informes de Cloud Discovery en el panel de Cloud Discovery.

![Informe de proxy](./media/proxy-report.png)


Para exportar estos registros, haga lo siguiente:

1. Vaya al engranaje Configuración y haga clic en **Proxy**.
2. En el lado derecho de la tabla, haga clic en el botón de exportación. ![Botón de exportación](./media/export-button.png). 
3. Seleccione el intervalo del informe y haga clic en **Exportar**. Este proceso puede tardar en completarse.

Para descargar el registro exportado:

1. Cuando el informe esté listo, vaya a **Investigar** y, luego, a **Informes personalizados**.
2. En la tabla, seleccione el informe que proceda en la lista de **registros de tráfico del proxy** y haga clic en el ![botón de descarga](./media/download-button.png). 


## Cómo funciona el bloqueo de descargas <a name="block-download"></a>

Cuando **Bloquear** es la **Acción** establecida que quiere realizar en la directiva de sesión del proxy de Cloud App Security, el proxy impedirá al usuario descargar un archivo de acuerdo con los filtros de archivos de la directiva. El proxy identifica un evento de descarga de cada aplicación SAML y, cuando un usuario inicia este evento, el proxy interviene en tiempo real para evitar que se ejecute. Cuando se recibe la señal de que un usuario ha iniciado una descarga, el proxy devuelve al usuario un mensaje que indica que la **descarga está restringida**, y reemplaza el archivo descargado por un archivo de texto que contiene un mensaje personalizable para el usuario, que se puede configurar en la directiva de sesión del proxy.  

## Cómo funciona la protección de descargas <a name="protect-download"></a>

Cuando **Proteger** es la **Acción** establecida que va a realizarse en la directiva de sesión del proxy de Cloud App Security, el proxy exige que el archivo se etiquete y proteja de acuerdo con los filtros de archivos de la directiva. Las etiquetas se configuran en la consola de Azure Information Protection en Azure, y **Proteger** debe estar seleccionado en la etiqueta para que dicha etiqueta aparezca como una opción en la directiva de Cloud App Security. Cuando se selecciona una etiqueta y se descarga un archivo que cumple los criterios de la directiva de Cloud App Security, tanto la etiqueta como la protección correspondiente (con permisos) se aplican al archivo de descarga. El archivo original permanece tal cual en la aplicación en la nube, mientras que el archivo descargado ahora está protegido. Los usuarios que traten de tener acceso al archivo deben cumplir los requisitos de permiso establecidos por la protección aplicada.  
 
 
## <a name="see-also"></a>Consulte también  
[Bloqueo de descargas de información confidencial con el proxy de Microsoft Cloud App Security](use-case-proxy-block-session-aad.md)   
[Para obtener soporte técnico, visite la página de soporte técnico asistido de Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Los clientes Premier también pueden elegir Cloud App Security directamente desde el Portal Premier.](https://premier.microsoft.com/)  
  
  