---
title: "Cómo bloquear el acceso a las aplicaciones en la nube desde dispositivos no administrados | Microsoft Docs"
description: "En este tema, se describe el escenario para proteger su organización contra el acceso a aplicaciones en la nube desde dispositivos no administrados."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 8/15/2017
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: 9aec9c6f-c9e2-4a4b-8b6a-2f8e4465ee3f
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: b12fabca53c6174fb674f9de260eadb2c1311775
ms.sourcegitcommit: 84f358a5dd0ab7f362dd3a2cf9999a6184fba856
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/14/2017
---
# <a name="blocking-access-to-cloud-apps-from-unmanaged-devices"></a>Bloquear el acceso a las aplicaciones en la nube desde dispositivos no administrados

En el mundo corporativo, Bring Your Own Device es excelente para que los empleados puedan sacar el máximo partido de sus tabletas y teléfonos personales en el lugar de trabajo. Con todo, muchos administradores de TI, conscientes de las amenazas que esto supone para los datos y la red de una organización, quieren poder bloquear el acceso desde estos dispositivos no administrados a algunas o todas las aplicaciones en la nube de la empresa. 

## <a name="how-does-cloud-app-security-detect-unmanaged-devices"></a>¿Cómo detecta Cloud App Security los dispositivos no administrados?
.

>[!NOTE]
> Este caso de uso se aplica a .

## <a name="the-threat"></a>LA AMENAZA
Una directora de ventas de su organización tiene un dispositivo administrado que usa con regularidad, pero, en ocasiones, quiere comprobar algo en Salesforce en su teléfono móvil personal. El teléfono no está administrado por su organización, lo que significa que puede estar infectado por virus, malware o puede no estar protegido por contraseña y cualquier persona que lo tenga podría acceder a su cuenta de Salesforce.

## <a name="the-solution"></a>LA SOLUCIÓN
Proteja su organización mediante la supervisión del uso de aplicaciones en la nube en Cloud App Security y la creación de una directiva de acceso para controlar y bloquear actividades desde dispositivos no administrados.

## <a name="prerequisites"></a>Requisitos previos

[Implemente](proxy-deployment.md) el proxy de Cloud App Security para Salesforce.

## <a name="set-up-unmanaged-device-detection"></a>Configurar la detección de dispositivos no administrados


## <a name="create-an-access-policy"></a>Crear una directiva de acceso
Las directivas de acceso le permiten supervisar los intentos realizados por los usuarios para iniciar sesión en aplicaciones en la nube y, si es necesario, bloquearlos para que no tengan acceso a la aplicación.


1.  En la consola, haga clic en **Control**, seguido de **Directivas**.  
  
2.  Haga clic en **Crear directiva** y seleccione **Directiva de acceso**.  
  
3.  Asigne un nombre y una descripción a la directiva, por ejemplo, **Bloquear el acceso a Salesforce desde dispositivos no administrados**.  
  
3. Asigne a la directiva una **gravedad**. Si ha configurado Cloud App Security para que le envíe notificaciones cuando se producen coincidencias de directivas para un nivel de gravedad de política específico, esto se usará para determinar si la coincidencia de la directiva desencadenará una notificación o no.

4.  Puede dejar la configuración **Categoría** como **Control de acceso**.  
  
7. En **Origen de la actividad**, haga clic en **Seleccione aplicaciones de la lista siguiente** y seleccione **Salesforce**.

8. En la sección de filtros de actividad, seleccione **Tipo de dispositivo** y, después, **no es igual a** y seleccione **Conforme**, **Unido a dominio** y **Certificado de cliente válido**.
  
10. En esta fase, en **Acciones** que se llevarán a cabo cuando coincida la directiva, seleccione:
    - Permitir: Si selecciona Permitir, los usuarios podrán descargar los archivos. 
    o
    
 
 >[!WARNING]
 >Se recomienda encarecidamente no **Bloquear** las descargas antes de ejecutar la directiva en primer lugar en modo **Permitir** y comprobar que los resultados son como se esperaba. Después de determinar que la directiva no bloquea a ningún usuario sin querer, cambie la directiva para **Bloquear** las descargas.
 
 9. Establezca las alertas que quiera recibir cuando coincida la directiva. Puede establecer un límite para no recibir demasiadas alertas y puede seleccionar si quiere recibir las alertas como un mensaje de correo electrónico, un mensaje de texto o ambos.

10. Para ver las coincidencias de la directiva de acceso, haga clic en **Control** y, después, en **Directivas**. Filtre los resultados para mostrar solo las directivas de acceso con el filtro **Tipo** en la parte superior. Para obtener más información sobre las coincidencias de cada directiva, haga clic en una directiva. Haga clic en la pestaña **Historial** para ver el historial de los 6 meses anteriores con las coincidencias de directiva.     
  
## <a name="validate-your-policy"></a>Validar la directiva

1. Para simular una alerta, desde un dispositivo no administrado, intente iniciar sesión en Salesforce.
3. Vaya al informe de directiva. Una coincidencia de directiva de acceso debe aparecer en breve. 
4. Puede hacer clic en la coincidencia para ver quién ha intentado iniciar sesión en Salesforce y desde qué dispositivo. 

## <a name="blocking-access"></a>Bloquear el acceso

Una vez validada y perfeccionada la directiva, quite posibles falsos positivos que puedan haber coincidido con la directiva. Luego, haga lo siguiente: 

1. Cuando se produce una coincidencia con una directiva de acceso, puede corregirlo al establecer [acciones de gobierno](governance-actions.md) automatizadas.

2. Para ello, edite la directiva que ha creado antes y establezca **Acciones** en **Bloquear** descargas cuando coincida con la directiva. El usuario no podrá acceder a Salesforce desde ningún dispositivo que no esté administrado.
  
 
 ## <a name="see-also"></a>Consulte también  
[Actividades diarias para proteger el entorno de nube](daily-activities-to-protect-your-cloud-environment.md)   
[Para obtener soporte técnico, visite la página de soporte técnico asistido de Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Los clientes Premier también pueden elegir Cloud App Security directamente desde el Portal Premier.](https://premier.microsoft.com/)  
  
  