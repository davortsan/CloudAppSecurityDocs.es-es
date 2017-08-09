---
title: "Implementación del proxy de Cloud App Security | Microsoft Docs"
description: "En este tema se proporciona información sobre cómo implementar el proxy de Cloud App Security."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 7/31/2017
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: 75094bde-e135-47fb-b5c6-7e1168919771
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 245e44cdf56b15795f67340442babcb0f688ea9d
ms.sourcegitcommit: c5a0d07af558239976ce144c14ae56c81642191b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/03/2017
---
# <a name="deploying-the-cloud-app-security-proxy"></a>Implementación del proxy de Cloud App Security

> [!NOTE]
> Se recomienda intentar la instalación en un espacio aislado o en un entorno de prueba antes de instalarlo en un entorno de producción.

Los pasos que se describen a continuación se deben realizar para implementar el proxy de Cloud App Security y permitir tanto el control de acceso como el control de sesión.

## <a name="prerequisites"></a>Requisitos previos

-   Un entorno de trabajo en el que la aplicación de nube esté configurada con un proveedor de identidades. El proceso de instalación implica cambios de configuración tanto en la aplicación como en el proveedor de identidades.
- Asegúrese de tener acceso a la configuración de inicio de sesión en el proveedor de identidades y la aplicación.

## <a name="deploy-the-proxy"></a>Implementación del proxy

Si instala el proxy en un entorno de producción, se recomienda que busque un momento en el que la mayoría de los usuarios no esté usando la aplicación, habitualmente durante la noche o el fin de semana, y que informe a los usuarios que habrá un breve tiempo de inactividad de las aplicaciones.

Antes de que comience a hacer cambios en la configuración, compruebe que la configuración actual funciona. Una vez que lo compruebe, siga estos pasos.

1.  En el portal de Cloud App Security, vaya al engranaje Configuración y elija **Proxy**.

2. En la esquina superior derecha, haga clic en el signo más.

3. En la ventana **Agregar la aplicación al proxy**, seleccione la aplicación que desea agregar y haga clic en **Iniciar el asistente**. 

 ![agregar la aplicación al proxy de Cloud App Security](./media/proxy-add-app.png)

4. Cargue el archivo de metadatos de inicio de sesión único desde la configuración de inicio de sesión único de la aplicación. Si no tiene un archivo de metadatos, haga clic en **Fill in data manually** (Rellenar manualmente los datos) y proporcione los datos solicitados según el asistente. 

 ![agregar el archivo de metadatos de inicio de sesión único al proxy de Cloud App Security](./media/proxy-w-add-app.png)


5. Siga estos pasos en el portal del proveedor de identidades. En la mayoría de los portales de proveedores de identidades, esto se hace en **Aplicaciones**:

    1. Cree una nueva aplicación SAML personalizada. Es necesario crear una nueva aplicación personalizada porque deberá cambiar las direcciones URL y agregar atributos SAML, lo que podría no ser posible en aplicaciones de galerías.
    
    2. Copie la configuración de inicio de sesión único desde la aplicación existente en la lista del proveedor de identidades a la aplicación personalizada nueva. Asegúrese de que el **identificador** (también conocido como identificador de entidad o audiencia) de la aplicación personalizada coincida con el **identificador** de la configuración de inicio de sesión único de la aplicación real. Si el proveedor de identidades no le permite usar el mismo **identificador** para dos aplicaciones distintas, cambie el identificador de la aplicación original después de copiarlo.
    
    3. Asigne a la aplicación personalizada nueva todos los usuarios que actualmente están asignados a la aplicación original.
    
    ![agregar el archivo de metadatos de inicio de sesión único al proxy de Cloud App Security](./media/proxy-w-add-external-config.png)

5. Cargue el archivo de metadatos de inicio de sesión único desde el proveedor de identidades. Si no tiene un archivo de metadatos, haga clic en **Fill in data manually** (Rellenar manualmente los datos) y proporcione los datos solicitados según el asistente.  

 ![agregar el archivo de metadatos de inicio de sesión único al proxy de Cloud App Security](./media/proxy-w-identity-provider.png)

6. Realice los siguientes cambios de configuración externa en el portal del proveedor de identidades y, luego, en la aplicación personalizada nueva que creó, haga lo siguiente:

    1. Copie la dirección URL que se proporcionó en el asistente. Luego, vaya al portal del proveedor de identidades y péguela como la dirección URL de inicio de sesión único (o dirección URL de respuesta) en la aplicación SAML personalizada nueva que creó.
    
    2. Copie los atributos y los valores que se proporcionaron en el asistente del proxy y agréguelos como atributos personalizados de SAML.
    
    3. Asegúrese de que los identificadores de nombre que use la aplicación tengan el formato de dirección de correo electrónico. Esto resulta necesario para permitir que el proxy de Cloud App Security aplique directivas sobre los usuarios.
    
    4. Guarde la configuración de la aplicación personalizada nueva y haga clic en **Siguiente** en el asistente del proxy.
 ![actualizar configuración del proveedor de identidades en el proxy de Cloud App Security](./media/proxy-w-ip-external2.png)

4.  Luego, en la página de configuración de inicio de sesión único de la aplicación, haga lo siguiente:
    1. Cree una copia de seguridad de la configuración actual de la aplicación.
    
    2. Copie la dirección URL del asistente del proxy en la dirección URL de inicio de sesión único de SAML de la aplicación.
    
    3. Descargue el certificado SAML de Cloud App Security para la aplicación.
    
    4. En la aplicación personalizada que creó, cargue este certificado SAML en lugar del original y guarde la configuración.
   
    5. En el asistente del proxy, haga clic en **Finalizar**.


En cuestión de minutos, todas las solicitudes de inicio de sesión a la aplicación se enrutarán a través del proxy de Cloud App Security. 



### <a name="test-the-configuration"></a>Probar la configuración

1.  Intente iniciar sesión en la aplicación. Si se produce un error en el inicio de sesión, asegúrese de haber completado correctamente todos los pasos del asistente del proxy. 

2.  En el portal de Cloud App Security, en **Investigar**, seleccione **Registro de actividad** y asegúrese de que haya eventos de **registro de inicio de sesión único** capturados por el proxy.



## <a name="see-also"></a>Consulte también  
[Trabajo con el proxy de Cloud App Security](proxy-intro.md)   
[Para obtener soporte técnico, visite la página de soporte técnico asistido de Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Los clientes Premier también pueden elegir Cloud App Security directamente desde el Portal Premier.](https://premier.microsoft.com/)  
  