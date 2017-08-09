---
title: "Creación de directivas para controlar el uso de aplicaciones de nube con el proxy de Cloud App Security | Microsoft Docs"
description: "En este tema se proporciona información sobre cómo crear directivas para controlar el uso de aplicaciones de nube con el proxy de Cloud App Security."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 7/16/2017
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: b419aff0-3f50-4917-9ee2-9ecf7539a5d7
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 4544f5b48484f9341bb85d09d8fdc8d11fd4ba00
ms.sourcegitcommit: c5a0d07af558239976ce144c14ae56c81642191b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/03/2017
---
# <a name="controlling-app-use-with-proxy-control"></a>Control del uso de aplicaciones con el control del proxy

Después de implementar el proxy, puede controlar el acceso y las sesiones en la nube de la organización mediante la creación de directivas para bloquear el comportamiento y acceso no deseados.

## <a name="create-access-control-policies-in-cloud-app-security"></a>Creación de directivas de control de acceso en Cloud App Security

Para crear directivas de control de acceso:

1.  En **Control**, seleccione **Directivas**.

2.  En **Crear directiva**, elija **Directiva de proxy** y, luego, como el **tipo de actividad**, seleccione **Registro de inicio de sesión único**.

3.  Luego elija la aplicación y los filtros que correspondan y la opción de mitigación de su preferencia.

>[!NOTE]
> En los filtros, puede elegir **Etiqueta de dispositivo** y establecerla para que sea igual o no a **Dispositivo administrado**. Consulte a continuación para más información sobre [Dispositivos administrados](#_Managed_devices).

Además, observe que en las **acciones de mitigación** puede elegir **Registrar** o **Bloquear acceso**, o bien elegir si **enrutar a Cloud App Security**, lo que le permitirá supervisar y crear directivas sobre la sesión. Esto se explicará con mayor detalle en [Creación de directivas de control de sesión en Cloud App Security](#_Creating_session_control).

## <a name="create-session-control-policies-in-cloud-app-security"></a>Creación de directivas de control de sesión en Cloud App Security 

Después de implementar el proxy, puede agregar las funcionalidades de control de sesión si define directivas de sesión en el portal de Cloud App Security.

Para comenzar, se recomienda que habilite el control de sesión para un grupo pequeño de usuarios antes de implementarlo en toda la organización. Además, no se recomienda habilitar el control de sesión en todas las sesiones ni en la mayoría de las sesiones. Como el control de sesión se basa en una implementación sin agente que tiene limitaciones, está diseñado para abarcar casos en los cuales tiene un control limitado o ningún control sobre el dispositivo y la aplicación.

Para crear directivas de control de sesión:

1.  Cree una [directiva de acceso](#working-with-proxy-control-features) y, luego, como acción de mitigación, elija **Enrutar a Cloud App Security**.

2.  En **Control**, vaya a **Directivas** y en **Crear directiva**, elija **Directiva de proxy**.

3.  Luego, en el **tipo de actividad**, elija **Descargar archivo** o **Exportar informe**. Elija la aplicación y los filtros que correspondan y la mitigación, según sea necesario.

## <a name="enabling-managedunmanaged-device-control"></a>Habilitación del control de dispositivos administrados y no administrados

### <a name="step-1-deploy-certificates"></a>PASO 1: Implementación de certificados

Con el fin de que Cloud App Security identifique cuáles de los dispositivos que se conectan a la nube están administrados y cuáles no administrados, debe implementar los certificados de cliente. Puede hacerlo de distintas formas, habitualmente usando los certificados de una solución de administración de dispositivos móviles existente o mediante el uso de las directivas de grupo de Active Directory.

### <a name="step-2-upload-the-root-certificate-to-cloud-app-security"></a>PASO 2: Carga del certificado raíz a Cloud App Security

Para habilitar la identificación de dispositivos administrados en el portal de Cloud App Security, primero debe cargar el certificado raíz de entidad de certificación:

1.  Haga clic en el engranaje Configuración y elija **Dispositivos administrados**.

2.  Habilite la **Identificación de dispositivos**.

3. Cargue el certificado raíz.

![certificación de dispositivo administrado del proxy de cloud app security](./media/managed-device-cert.png)

### <a name="step-3-create-managed-device-policies"></a>PASO 3: Creación de directivas de dispositivos administrados

Una vez que se carga el certificado raíz, use el filtro **Etiqueta de dispositivo** equivale o no a **dispositivo administrado** para crear directivas de proxy o para buscar eventos en el registro de actividad.

Cuando se usan certificados de cliente para identificar los dispositivos administrados, se recomienda comenzar en el modo de supervisión antes de intentar bloquear o supervisar la sesión. Esto significa que se define una directiva de acceso con un filtro **Dispositivo administrado** en el que la acción de mitigación es **Solo registro**. Cuando tenga algo de experiencia con los usuarios, puede agregar otras acciones de mitigación, como bloquear el acceso o supervisar la sesión.


## <a name="see-also"></a>Consulte también  
[Trabajo con el proxy de Cloud App Security](proxy-intro.md)   
[Para obtener soporte técnico, visite la página de soporte técnico asistido de Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Los clientes Premier también pueden elegir Cloud App Security directamente desde el Portal Premier.](https://premier.microsoft.com/)  
  