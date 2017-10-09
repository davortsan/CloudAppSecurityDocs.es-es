---
title: Integrar Azure Information Protection con Cloud App Security | Microsoft Docs
description: "Este artículo proporciona información sobre cómo sacar provecho de las etiquetas de Azure Information Protection en Cloud App Security para tener un mayor control del uso de aplicaciones de nube de la organización."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 9/24/2017
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: 8168319a-199f-4e6c-ad68-e0f236480803
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: b22d1ad368b05b5cee7d7459f199ce1ff2769cc4
ms.sourcegitcommit: 8759541301241e03784c5ac87b56986f22bd0561
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/28/2017
---
# <a name="azure-information-protection-integration"></a>Integración de Azure Information Protection

Cloud App Security le permite investigar archivos y establecer directivas basadas en etiquetas de clasificación de Azure Information Protection, lo que permite mayor visibilidad y control de sus datos confidenciales en la nube. La integración de Azure Information Protection con Cloud App Security es tan fácil como seleccionar una sola casilla. 

Al integrar Azure Information Protection en Cloud App Security, puede aprovechar todas las funciones de ambos servicios y proteger los archivos en la nube, entre lo que se incluye lo siguiente:
- La capacidad de ver todos los archivos clasificados en una ubicación central.
- La capacidad de realizar la investigación en función del nivel de clasificación y cuantificar la exposición de la información confidencial en las aplicaciones en la nube.
- La capacidad de crear directivas para asegurarse de que los archivos clasificados se controlan correctamente.

> [!NOTE] 
> Para habilitar esta característica, necesita una licencia de Cloud App Security y una licencia para Azure Information Protection Premium P1 o P2. Tan pronto como se activen las licencias, Cloud App Security sincroniza las etiquetas de las organizaciones del servicio Azure Information Protection.

## <a name="how-it-works"></a>Cómo funciona
Probablemente esté familiarizado con las etiquetas de clasificación de archivos de [Azure Information Protection](https://docs.microsoft.com/information-protection/). Puede ver las etiquetas de clasificación de Azure Information Protection en Cloud App Security. Al integrar Cloud App Security con Azure Information Protection, Cloud App Security examina los archivos del modo siguiente:
1. Cloud App Security recupera la lista de todas las etiquetas de clasificación que se hayan usado en su inquilino. Esta acción se realiza cada hora para mantener la lista actualizada.
2. Después, Cloud App Security examina los archivos en busca de etiquetas de clasificación de la manera siguiente: a. Si ha habilitado el examen automático (consulte la información a continuación), todos los archivos nuevos o modificados se agregan a la cola de examen.
    b. Si ha establecido una directiva de archivo (consulte la información a continuación) para buscar etiquetas de clasificación, estos archivos se agregan a la cola de examen de etiquetas de clasificación.
3. Como se mencionó anteriormente, estos exámenes son para las etiquetas de clasificación detectadas en el examen inicial que Cloud App Security lleva a cabo para ver qué etiquetas de clasificación se usan en el inquilino. Las etiquetas externas, es decir, las etiquetas de clasificación establecidas por una persona externa al inquilino, se agregan a la lista de etiquetas de clasificación. Si no quiere que se examinen, seleccione la casilla **Only scan files for Azure Information Protection classification labels from this tenant** (Examinar solo archivos en busca de etiquetas de clasificación de Azure Information Protection en este inquilino); consulte la información siguiente.
4. Después de habilitar Azure Information Protection en Cloud App Security, también se examinarán en busca de etiquetas de clasificación todos los archivos nuevos que se agreguen a Office 365.

## <a name="how-to-integrate-azure-information-protection-with-cloud-app-security"></a>Cómo integrar Azure Information Protection con Cloud App Security
  
### <a name="enable-azure-information-protection"></a>Habilitar Azure Information Protection

Lo único que debe hacer para integrar Azure Information Protection con Cloud App Security es habilitar el examen automático para permitir la búsqueda de etiquetas de clasificación de Azure Information Protection en los archivos de Office 365 sin necesidad de crear una directiva. Después de habilitarlo, si tiene archivos en su entorno de nube con etiquetas de clasificación de Azure Information Protection, los verá en Cloud App Security.

Para permitir que Cloud App Security examine archivos que tengan la inspección de contenido habilitada en busca de etiquetas de clasificación:

1. En Cloud App Security, en el engranaje de configuración, seleccione la página **Configuración general**.
2. En Azure Information Protection, seleccione **Analizar automáticamente los archivos en busca de etiquetas de clasificación de Azure Information Protection**. 

Después de habilitar Azure Information Protection, podrá ver los archivos que tengan etiquetas de clasificación y filtrarlos por etiqueta en Cloud App Security.

 ![habilitar azure information protection](./media/enable-azip.png)

> [!NOTE] 
> El examen automático no examina los archivos existentes hasta que se vuelvan a modificar. Para examinar los archivos existentes en busca de etiquetas de clasificación de Azure Information Protection, debe tener al menos una **directiva de archivos de inspección de contenido**. Si no tiene ninguna, cree una nueva **directiva de archivos**, elimine todos los filtros predeterminados, marque la opción **Inspección de contenido**. A continuación, en **Inspección de contenido**, haga clic en **Incluir archivos que coincidan con una expresión preestablecida** y seleccione un valor predefinido. Después, guarde la directiva. Esto habilita la inspección de contenido, que detecta automáticamente etiquetas de clasificación de Azure Information Protection.

### <a name="set-internal-and-external-tags"></a>Establecer etiquetas internas y externas
De forma predeterminada, Cloud App Security examina las etiquetas de clasificación que se han definido en su organización, así como las externas que han definido otras organizaciones. 

Para ignorar las etiquetas de clasificación establecidas por una persona externa a la organización, en el portal de Cloud App Security, vaya a **Configuración general** y, después, a **Configuración de seguridad de Azure** y seleccione **Ignorar las etiquetas de clasificación de Azure Information Protection de otros inquilinos**.
 
![ignorar las etiquetas](./media/azip-ignore.png)

### <a name="control-file-exposure"></a>Controlar la exposición del archivo
- Si este es el documento en el que ha incluido una etiqueta de clasificación de Azure Information Protection:

![Pantalla de ejemplo de Azure Information Protection](./media/azip-screen.png)

- Puede ver este archivo en Cloud App Security en la página **Archivos**. Para ello, filtre la etiqueta de clasificación:

![Comparación de Cloud App Security con Azure Information Protection](./media/cas-compared-azip.png)

- Puede obtener más información sobre estos archivos y sus etiquetas de clasificación en el cajón de archivos.

- En la página **Archivos**, haga clic en el archivo correspondiente para ver si tiene etiquetas de clasificación:

![cajón de archivo](./media/azip-file-drawer.png)

- Puede hacer clic en la etiqueta de clasificación para ver más información o para ver la lista completa de etiquetas de clasificación:
 
![lista de etiquetas](./media/azip-tags-list.png)

- Después, puede crear directivas de archivos en Cloud App Security para controlar los archivos que se comparten de forma inapropiada y los archivos que están etiquetados y se han modificado recientemente.
- Además, puede desencadenar alertas en las actividades relacionadas con archivos clasificados.

![etiquetas de azure information protection en cloud app security](./media/azip-tags-in-cas.png)

> [!Note]
> Cuando las etiquetas de Azure Identity Protection están deshabilitadas en un archivo, las etiquetas deshabilitadas aparecen como deshabilitadas en Cloud App Security. No se muestran las etiquetas eliminadas.


**Directiva 1: datos confidenciales que se comparten externamente en Box:**

1.  Cree una directiva de archivo.
2.  Establezca el nombre, la gravedad y la categoría de la directiva.
3.  Agregue los siguientes filtros para buscar todos los datos confidenciales que se comparten externamente en Box:

![directiva de confidencialidad](./media/azip-confidentiality-policy.png) 

**Directiva 2: datos restringidos que se han modificado recientemente fuera de la carpeta Finanzas en SharePoint:**

1.  Cree una directiva de archivo.
2.  Establezca el nombre, la gravedad y la categoría de la directiva.
3.  Agregue los siguientes filtros para buscar todos los datos restringidos que se han modificado recientemente y agregue una exclusión para la carpeta Finanzas en la opción de selección de carpeta: 
 
![directiva de datos restringidos](./media/azip-restricted-data-policy.png) 

También puede establecer alertas, notificaciones al usuario o emprender acciones inmediatas para estas directivas.
Obtenga más información sobre [acciones de gobierno](governance-actions.md).

Obtenga más información sobre [Azure Information Protection](https://docs.microsoft.com/en-us/information-protection/understand-explore/what-is-information-protection) y consulte su [Tutorial de inicio rápido](https://docs.microsoft.com/en-us/information-protection/get-started/infoprotect-quick-start-tutorial).


## <a name="integration-with-azure-rights-management"></a>Integración con Azure Rights Management

Su organización debe tener Azure Rights Management con licencia y activado para integrar entre Cloud App Security y Azure RMS.  Estos dos pasos independientes se pueden encontrar en [Activar Azure Rights Management](https://docs.microsoft.com/information-protection/deploy-use/activate-service).

Actualmente, Cloud App Security admite la protección nativa para archivos de Office (2016 y versiones posteriores). Los archivos PDF y de imagen estarán disponibles en versiones futuras. 

Esta característica está disponible actualmente para los archivos que se almacenan en SharePoint Online y OneDrive para la Empresa. Se admitirán más aplicaciones en la nube en futuras versiones.

Después de que Cloud App Security se conecte al servicio de Office 365, podrá usar las características de integración de RMS de Cloud App Security que le permiten proteger documentos con RMS directamente en el portal de Cloud App Security, como se indica a continuación:

1. En la página **Archivos**, seleccione el archivo que desea proteger y luego haga clic en los tres puntos al final de la fila del archivo y elija **Proteger**. 
![protección de la aplicación](./media/protect-app.png)
>[!NOTE]
>Azure Information Protection protege los archivos con un tamaño máximo de 50 MB. 

2. Se le pide que elija una de las etiquetas de clasificación de su organización para usarla para proteger el archivo; luego, haga clic en **Proteger**. 
![etiqueta de clasificación de protección](./media/protect-template.png)
3. Después de elegir una etiqueta de clasificación y hacer clic en Proteger, Cloud App Security aplicará la etiqueta de clasificación y protegerá el archivo original. T
> [!NOTE]
>   Se recomienda aplicar etiquetas de clasificación de RMS que abarquen toda la compañía en los archivos, de forma que todos los usuarios de la organización puedan acceder a estos archivos, incluido el propietario original del archivo. El propietario del archivo, la directiva de uso compartido del archivo y la lista de usuarios que ya tienen acceso a él no cambian cuando el archivo pasa a estar protegido.

4. Si los usuarios desean tener acceso al archivo protegido, necesitan tener la aplicación RMS sharing instalada en sus dispositivos. Para más información, consulte [Información general técnica de la aplicación Microsoft Rights Management sharing](https://docs.microsoft.com/information-protection/rms-client/sharing-app-admin-guide-technical).

5. Puede revertir esta acción en cualquier momento en el **Registro de gobierno** haciendo clic en el botón **Revertir** situado en el extremo de la fila de la acción Proteger tomada previamente. 


Para obtener más información sobre cómo funcionan conjuntamente Cloud App Security y Azure Information Protection, consulte [Protección de datos frente a errores de los usuarios](https://docs.microsoft.com/enterprise-mobility-security/solutions/protect-data-user-mistake).

 
## <a name="related-videos"></a>Vídeos relacionados  
[Cloud App Security + Azure Information Protection Integrations](https://channel9.msdn.com/Shows/Microsoft-Security/MCAS--AIP-Integrations) (Integraciones de Cloud App Security y Azure Information Protection)  

## <a name="see-also"></a>Consulte también  
[Controlar las aplicaciones en la nube con directivas](control-cloud-apps-with-policies.md)   
[Para obtener soporte técnico, visite la página de soporte técnico asistido de Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Los clientes Premier también pueden elegir Cloud App Security directamente desde el Portal Premier.](https://premier.microsoft.com/)  
  
