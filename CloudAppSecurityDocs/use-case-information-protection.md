---
title: "Aplicar automáticamente etiquetas de clasificación de Azure Information Protection | Microsoft Docs"
description: "En este tema se describe el proceso para aplicar automáticamente etiquetas de clasificación de Azure Information Protection en Microsoft Cloud App Security."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 10/31/2017
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: eac0b192-98d7-4939-9a07-1d4a7f8c39c3
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 6e6c7365be26dc379bcf0269812931387972bc8f
ms.sourcegitcommit: 3bc510959e66a29d474cbef412deac0daefa8a24
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="automatically-apply-azure-information-protection-classification-labels"></a>Aplicar automáticamente etiquetas de clasificación de Azure Information Protection  

En un mundo perfecto, todos los empleados serían plenamente conscientes de la importancia que tiene proteger la información y trabajar respetando las directivas. Pero, en el mundo real, puede suceder que un partner que trabaja en contabilidad cargue un documento en su repositorio de Box con los permisos incorrectos y que, a la semana, se dé cuenta de que se ha filtrado a la competencia información confidencial de su empresa. 

Microsoft Cloud App Security sirve para evitar este tipo de desastres antes de que ocurran.

Cloud App Security identifica que hay permisos públicos en un documento guardado en su cuenta de Box y usa un motor de clasificación para determinar que hay información confidencial en el documento compartido públicamente. Cloud App Security le envía una alerta para avisarle de lo ocurrido y, además, aplica automáticamente la etiqueta de clasificación **Confidencial** de Azure Information Protection para proporcionar un mayor cifrado al archivo. 

>[!NOTE]
> - Aplicar una etiqueta de Azure Information Protection es solo una de las [acciones de gobierno](governance-actions.md) disponibles en una larga lista.
> - Esta característica está disponible en Box, SharePoint y OneDrive para la Empresa.

### <a name="enhanced-data-level-encryption-protection"></a>Mejor protección del cifrado de nivel de datos

La integración de Cloud App Security con Azure Information Protection posibilita un nivel extra de protección, ya que los archivos se cifran automáticamente. Por ejemplo, mientras Azure Information Protection cifra el archivo, las aplicaciones que admiten Azure Information Protection (como Office 365) saben cómo abrir los archivos y respetan los permisos establecidos en las etiquetas de clasificación. Las etiquetas se pueden usar para aplicar reglas de protección concretas. Por ejemplo, un archivo se puede configurar de modo que se pueda abrir, pero no compartir, imprimir, reenviar ni editar. 

Este elevado nivel de protección se conserva en el archivo esté donde esté; es decir, tanto si se envía, se copia o se almacena en una aplicación de almacenamiento en línea, el archivo seguirá estando protegido. Si uno de los empleados ha perdido una unidad de memoria que contiene el archivo, el archivo se bloqueará y, si alguien intenta abrirlo, el propietario del archivo recibirá una alerta. Con Cloud App Security, puede aplicar protección automáticamente. Por ejemplo, todos los archivos que tengan números de tarjeta de crédito o que haya cargado el departamento de finanzas y se compartan de manera externa también se pueden configurar para que se protejan automáticamente con una etiqueta de clasificación. 

## <a name="the-threat"></a>La amenaza 
Un usuario de la organización guarda archivos con información confidencial de los clientes en Box y los configura para que se puedan compartir con todos los usuarios de la organización. Este usuario no es consciente de que, además del equipo que trabaje directamente con esos archivos, todo el personal de soporte técnico, como los proveedores, los colaboradores y los visitantes que accedan a la oficina ocasionalmente, puede acceder a la cuenta de Box. Cualquier persona con acceso a la cuenta de Box de la organización podrá acceder a la información. Aparte de representar un peligro para la organización, puede ir en contra de la legislación sobre información personal de varios países, lo que expone a la organización a problemas legales.

## <a name="the-solution"></a>La solución
Use Cloud App Security con Azure Information Protection para insertar información de clasificación y protección para proteger los datos de manera persistente, asegurándose además de que sigan estando protegidos independientemente de dónde estén almacenados o con quién se compartan. Esto también permite compartir los datos de forma segura con los compañeros de trabajo, así como con los clientes y partners. Defina quién puede tener acceso a los datos y lo que se puede hacer con ellos (como permitir a los usuarios ver y editar archivos, pero no imprimirlos ni reenviarlos), además de otras [acciones de gobierno](governance-actions.md) compatibles con Cloud App Security (como quitar colaboradores o quitar funcionalidades de uso compartido).

## <a name="prerequisites"></a>Requisitos previos

- Tener habilitados Cloud App Security y Azure Information Protection en el inquilino.
- [Conecte Box](connect-box-to-microsoft-cloud-app-security.md) a Cloud App Security.

## <a name="setting-up-data-protection"></a>Configuración de la protección de datos

Vamos a configurar una directiva que busque números de tarjeta de crédito en los archivos almacenados en su cuenta de Box y, cuando los encuentre, .

1. Empiece a proteger los datos que guarda en Box mediante una directiva que cifre todos los datos confidenciales de Box:

    1. En la pestaña **Control**, haga clic en [**Directivas**](control-cloud-apps-with-policies.md). 
    
    2. Haga clic en **Crear directiva** y seleccione **Directiva de archivo**.
    
    3. Llame a la directiva *Protección de datos de Box*.
    
    4. En **Crear un filtro para los archivos a los que se aplicará esta directiva**, defina como objetivo los datos de su propiedad y confidenciales.<br></br>
    Por ejemplo, seleccione **Datos del cliente** como **Carpeta principal** en Box y su equipo financiero como **Propietario**.
    
    4. Dentro de esa carpeta, busque los archivos que contengan información de tarjeta de crédito del siguiente modo: en **Método de inspección de contenido** seleccione **DLP integrado** y, después, seleccione **Incluir archivos que coincidan con una expresión preestablecida** y **Todos los países:Finanzas:Número de tarjeta de crédito**.
    
    5. En **Gobierno**, abra la sección **Box**, seleccione **Aplicar etiqueta de clasificación** y seleccione la etiqueta que quiera aplicar.
    
    6. Puesto que [Cloud App Security se integra con Azure Information Protection](azip-integration.md), puede seleccionar las opciones de su lista de etiquetas de clasificación para proteger los datos.
 
    7. Haga clic en **Crear**. 
   
   ![Agregar etiqueta de clasificación a la directiva](./media/aip-auto-policy.png)
     
2. Investigación de las coincidencias
    
    1. En la página **Directivas**, haga clic en el nombre de directiva para ir a **Informe la directiva** y revise las coincidencias que se activaron para la directiva.

    2. Puede investigar la coincidencia haciendo clic en una coincidencia específica para abrir el cajón de archivos. En el cajón, puede ver las otras directivas que coincidan con este archivo. 
     
## <a name="validating-your-policy"></a>Validación de la directiva

1. Para simular una alerta, vaya a su cuenta de Box e intente acceder a un archivo en la carpeta **Datos del cliente**.
3. Vaya al informe de directiva. Una coincidencia de directiva de archivo debe aparecer en breve. 
4. Puede hacer clic en la coincidencia para ver qué archivos se han protegido. La propia coincidencia se enmascarará para proteger los datos confidenciales. 

>[!NOTE]
>Actualmente, Cloud App Security admite la aplicación automática de etiquetas de Azure Information Protection en Box, SharePoint y OneDrive para la Empresa.


 ## <a name="see-also"></a>Consulte también  
[Actividades diarias para proteger el entorno de nube](daily-activities-to-protect-your-cloud-environment.md)   
[Para obtener soporte técnico, visite la página de soporte técnico asistido de Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Los clientes Premier también pueden elegir Cloud App Security directamente desde el Portal Premier.](https://premier.microsoft.com/)  
  
  