---
title: "Implementar Cloud App Security para la información de uso y el control de aplicaciones en la nube | Microsoft Docs"
description: En este tema se describe el proceso para que Cloud App Security entre en funcionamiento.
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 1/15/2018
ms.topic: get-started-article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: cf040b18-93d1-41e8-a26a-647c56afb00f
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 4526b93a0d95f4bd1cc0a97867ba585002408130
ms.sourcegitcommit: 458e936e1ac548eda37e9bf955b439199bbdd018
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/16/2018
---
# <a name="deploy-cloud-app-security"></a>Implementar Cloud App Security
Cloud App Security le puede ayudar a sacar partido de las ventajas de las aplicaciones en la nube a la vez que mantiene el control de los recursos corporativos. Funciona mejorando la visibilidad de la actividad en la nube y ayuda a aumentar la protección de los datos corporativos. En este tema, le indicaremos los pasos que debe llevar a cabo para configurar Cloud App Security y trabajar con él.  

Su organización debe tener una licencia para utilizar Cloud App Security. Para obtener más información, consulte la sección [Cómo comprar Cloud App Security](https://www.microsoft.com/cloud-platform/cloud-app-security) en la página principal de Cloud App Security.  

>[!NOTE]
>No necesita una licencia de Office 365 para utilizar Cloud App Security.  

## <a name="prerequisites"></a>Requisitos previos  
  
-   Para usar el producto, la organización debe tener una licencia de Cloud App Security. Para obtener más información, consulte la sección [Cómo comprar Cloud App Security](https://www.microsoft.com/cloud-platform/cloud-app-security) en la página principal de Cloud App Security.  
  
     Para obtener soporte para activar inquilinos, vea [Póngase en contacto con el soporte de Office 365 para empresas: ayuda para administradores](https://support.office.com/article/Contact-Office-365-for-business-support-Admin-Help-32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b).  
  
> [!NOTE] 
> No es necesaria una licencia de Office 365 para Cloud App Security.  
  
-   Después de haber adquirido una licencia para Cloud App Security, recibirá un correo electrónico con la información de activación y un vínculo al portal de Cloud App Security.  
  
-   Para configurar Cloud App Security, debe ser un administrador global, un administrador de cumplimiento o un Lector de seguridad de Azure Active Directory u Office 365. Es importante saber que un usuario que tiene asignado un rol de administrador tendrá los mismos permisos en todas las aplicaciones en la nube a las que la organización esté suscrita, independientemente de si el rol se ha asignado en el portal de Office 365, en Portal de Azure clásico o a través el módulo de Azure AD para [Windows PowerShell](https://technet.microsoft.com/library/mt736914.aspx). Para obtener más información, vea [Asignación de roles de administrador en Office 365](https://support.office.com/article/Assigning-admin-roles-in-Office-365-eac4d046-1afd-4f1a-85fc-8219c79e1504) y [Asignación de roles de administrador en Azure Active Directory (Azure AD)](https://azure.microsoft.com/documentation/articles/active-directory-assign-admin-roles/).  
  
-   Para ejecutar el portal de Cloud App Security, use Internet Explorer 11, Microsoft Edge (versión más reciente), Google Chrome (versión más reciente), Mozilla Firefox (versión más reciente) o Apple Safari (versión más reciente).  

## <a name="to-access-the-portal"></a>Para acceder al portal:

Para tener acceso al portal de Cloud App Security, vaya a [https://portal.cloudappsecurity.com](https://portal.cloudappsecurity.com).  
  
También puede acceder al portal a través del **Centro de administración de Office 365**. Para ello, haga clic en el icono Centros de administración ![Icono Centros de administración de O365](./media/o365-admin-centers-icon.png "Icono Centros de administración de O365") seguido de **Cloud App Security**.  
  
![Acceso desde O365](./media/access-from-o365.png "Acceso desde O365")  
  



## <a name="get-started-quickly-with-cloud-app-security"></a>Inicio rápido de Cloud App Security  

 

### <a name="step-1-set-up-cloud-discoveryset-up-cloud-discoverymd"></a>Paso 1. [Configure Cloud Discovery](set-up-cloud-discovery.md).
Tarea necesaria: cargar registros de tráfico **para crear un informe continuo de Cloud Discovery**

 1. Vaya a **Configuración** > **Cloud Discovery settings** (Configuración de Cloud Discovery).
 2. Elija **Cargar registros automáticamente**.
 3. En la ficha **Orígenes de datos**, agregue los orígenes.
 4. En la pestaña **Recopiladores de registros**, configure el recopilador de registros.
 
**Para crear un informe de instantáneas de Cloud Discovery**

 1. Vaya a **Detectar** > **Crear nuevo informe de instantáneas** y siga los pasos.

**¿Por qué se deben configurar los informes de Cloud Discovery?**
Tener visibilidad de la TI en la sombra de la organización es algo esencial.
Después de analizar los registros, podrá detectar fácilmente qué aplicaciones en la nube se usan, qué usuarios lo hacen y en qué dispositivos.


### <a name="step-2-set-instant-visibility-protection-and-governance-actions-for-your-appsenable-instant-visibility-protection-and-governance-actions-for-your-appsmd"></a>Paso 2. [Establezca la visibilidad, la protección y las acciones de gobierno instantáneas para las aplicaciones](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md).
Tarea necesaria: conectar aplicaciones

1. Vaya a **Configuración** > **Conectores de aplicación**.
2. Elija **Conectar aplicación** y seleccione una aplicación.
3. Siga los pasos de configuración para conectar la aplicación.

**¿Por qué conectar una aplicación?**
Después de conectar una aplicación, puede obtener una mayor visión para que pueda investigar actividades, archivos y cuentas para las aplicaciones en su entorno de la nube.


### <a name="step-3-control-cloud-apps-with-policiescontrol-cloud-apps-with-policiesmd"></a>Paso 3. [Controle las aplicaciones en la nube con directivas](control-cloud-apps-with-policies.md).
Tarea necesaria: crear directivas

**Para crear directivas**

1. Vaya a **Control** > **Plantillas**.
2. Seleccione una plantilla de directiva de la lista y elija (+) **Crear directiva**.
3. Personalice la directiva (seleccione filtros, acciones y otras configuraciones) y luego elija **Crear**.
4. En la ficha **Directivas**, elija la directiva para ver las coincidencias relevantes (actividades, archivos y alertas).
 Sugerencia: a fin de cubrir todos los escenarios de seguridad del entorno de la nube, cree una política para cada **categoría de riesgo**.

**¿Cómo pueden las directivas ayudar a la organización?**
Puede utilizar directivas para ayudarle a supervisar tendencias, ver amenazas de seguridad y generar alertas e informes personalizados. Con las directivas se pueden crear acciones de gobierno y establecer controles de uso compartido de archivos y de prevención de pérdida de datos.


### <a name="step-4-personalize-your-experiencemail-settingsmd"></a>Paso 4. [Personalice la experiencia](mail-settings.md).
Tarea necesaria: agregar detalles de su organización

**Para especificar la configuración de correo electrónico**

1. Vaya a **Configuración** > **Configuración de correo**.
2. En **Identidad del emisor de correo electrónico**, escriba las direcciones de correo electrónico y el nombre para mostrar.
3. En **Diseño del correo electrónico**, cargue la plantilla de correo electrónico de la organización.

**Para establecer notificaciones de administrador**

1. En la barra de navegación, seleccione el nombre de usuario y luego vaya a **Configuración de usuario**.
2. En **Notificaciones**, configure los métodos que quiere establecer para las notificaciones del sistema.
3. Elija **Guardar**.

**Para personalizar las métricas de puntuación**

1. Vaya a **Configuración** > **Cloud Discovery settings** (Configuración de Cloud Discovery).
2. En **Configurar métrica de puntuación**, configure la importancia de los distintos valores de riesgo.
3. Elija **Guardar**.

Ahora las puntuaciones de riesgo otorgadas a las aplicaciones detectadas están configuradas exactamente según las necesidades y las prioridades de la organización.

**¿Por qué personalizar el entorno?**
Algunas características funcionan mejor si se personalizan de acuerdo a las necesidades. Ofrezca una mejor experiencia a los usuarios con sus propias plantillas de correo electrónico, decida qué notificaciones recibe y personalice las métricas de puntuación de riesgo de modo que se ajusten a las preferencias de la organización.


### <a name="step-5-organize-the-data-according-to-your-needsip-tagsmd"></a>Paso 5. [Organice los datos de acuerdo a las necesidades](ip-tags.md).
Tarea necesaria: configurar opciones importantes

**Para crear etiquetas de dirección IP**

1. Vaya a **Configuración** > **Etiquetas de dirección IP**.
2. Elija (+) **Agregar intervalo de direcciones IP**.
3. Escriba los **detalles**, la **ubicación**, las **etiquetas** y la **categoría** del intervalo IP.
4. Elija **Crear**.

 Ahora puede usar etiquetas IP cuando cree directivas y cuando filtre y cree informes continuos.

**Para crear informes continuos**

1. Vaya a **Configuración** > **Cloud Discovery settings** (Configuración de Cloud Discovery).
2. En **Administrar informes continuos**, elija **Crear informe**.
3. Siga los pasos de configuración.
4. Elija **Crear**.

Ahora puede ver datos detectados según sus propias preferencias, por ejemplo, unidades de negocio o intervalos IP.

**Para agregar dominios**

1. Vaya a **Configuración** > **Configuración general**.
2. En **Detalles de la organización**, agregue los dominios internos de la organización.
3. Elija **Guardar**.

**¿Por qué se deben configurar estos valores?**
Estos valores le ayudan a controlar mejor las características de la consola. Con las etiquetas IP es más fácil crear directivas adaptadas a las propias necesidades, filtrar con precisión los datos, etc. Use vistas de datos para agrupar los datos en categorías lógicas.
  

## <a name="see-also"></a>Consulte también

Establezca directivas: [Controlar las aplicaciones en la nube con directivas](control-cloud-apps-with-policies.md).    

Los clientes Premier también pueden elegir Cloud App Security directamente desde el [Portal Premier](https://premier.microsoft.com/).   
