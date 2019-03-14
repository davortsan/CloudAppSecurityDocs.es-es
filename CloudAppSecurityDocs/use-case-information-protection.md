---
title: Aplicar automáticamente etiquetas de clasificación de Azure Information Protection
description: En este tutorial se describe cómo aplicar automáticamente etiquetas de clasificación de Azure Information Protection en Microsoft Cloud App Security.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: barbkess
ms.date: 1/27/2019
ms.topic: tutorial
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: eac0b192-98d7-4939-9a07-1d4a7f8c39c3
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 9da835fc1f1a9c3fc85035d83a0b2e8415ebc337
ms.sourcegitcommit: 8ef0438fa35916c48625ff750cb85e9628d202f2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/15/2019
ms.locfileid: "56281855"
---
# <a name="tutorial-automatically-apply-azure-information-protection-classification-labels"></a>Tutorial: Aplicar automáticamente etiquetas de clasificación de Azure Information Protection

*Se aplica a: Microsoft Cloud App Security*

En un mundo perfecto, todos los empleados serían plenamente conscientes de la importancia que tiene proteger la información y trabajar respetando las directivas. Pero en el mundo real es probable que un asociado que trabaja en contabilidad cargue un documento en su repositorio de Box con los permisos incorrectos. Una semana más adelante se da cuenta de que se ha filtrado información confidencial de su empresa a la competencia. Microsoft Cloud App Security sirve para evitar este tipo de desastres antes de que ocurran. Esta característica está disponible en Box, SharePoint y OneDrive para la Empresa. Aplicar una etiqueta de Azure Information Protection es solo una de las [acciones de gobernanza](governance-actions.md) disponibles en una larga lista.

Este tutorial le ayudará a identificar qué permisos públicos se establecen en un documento guardado en el almacenamiento en la nube, de modo que reciba una alerta cuando se produzca una infracción. Además, puede aplicar automáticamente la etiqueta de clasificación **Confidencial** de Azure Information Protection para proporcionar un mayor cifrado a los archivos.

> [!div class="checklist"]
> * Configuración de la protección de datos 
> * Validar la directiva


## <a name="enhanced-data-level-encryption-protection"></a>Mejor protección del cifrado de nivel de datos

La integración de Cloud App Security con Azure Information Protection posibilita un nivel extra de protección, ya que los archivos se cifran automáticamente. Cuando Azure Information Protection cifra los archivos, las aplicaciones que admiten Azure Information Protection (como Office 365) saben cómo abrir los archivos y respetan los permisos establecidos en las etiquetas de clasificación. Use etiquetas para aplicar reglas de protección concretas. Por ejemplo, establezca que un archivo se puede abrir, pero no compartir, imprimir, reenviar ni editar.

Este nivel elevado de protección va con el archivo. El archivo seguirá estando protegido si lo envía, lo copia o lo almacena en su aplicación de almacenamiento en línea. Si uno de sus empleados pierde una unidad USB con el archivo en ella, este se bloqueará. Si alguien intenta abrir el archivo, el propietario recibirá una alerta. Con Cloud App Security, puede aplicar protección automáticamente. Por ejemplo, establezca que todos los archivos que tengan números de tarjetas de crédito o que haya cargado el departamento de finanzas y se compartan de manera externa también se protejan automáticamente con una etiqueta de clasificación.

## <a name="the-threat"></a>La amenaza

Un usuario de la organización guarda archivos con información confidencial de los clientes en Box y los configura para que se puedan compartir con todos los usuarios de la organización. El usuario no es consciente de que no solo su equipo directo, sino también todo el personal de soporte técnico tiene acceso a esa cuenta de Box. Este acceso incluye los proveedores, asociados y visitantes que ocasionalmente pasan por la oficina. Cualquier persona con acceso a la cuenta de Box de la organización podrá acceder a la información. Aparte de representar un peligro para la organización, ese acceso puede ir en contra de la legislación sobre información personal de varios países, lo que expone a la organización a problemas legales.

## <a name="the-solution"></a>La solución

Use Cloud App Security con Azure Information Protection para insertar información de clasificación y protección para proteger los datos de manera persistente, de forma que sigan estando protegidos independientemente de dónde estén almacenados o con quién se compartan. Esta protección también le permite compartir los datos de forma segura con sus compañeros de trabajo, clientes y asociados. Defina quién puede acceder a los datos y qué puede hacer con ellos. Por ejemplo, permita a los usuarios que vean y editen archivos, pero no que los impriman ni reenvíen. También puede agregar otras [acciones de gobernanza](governance-actions.md) que admite Cloud App Security a los archivos, como quitar colaboradores y quitar las funcionalidades de uso compartido.

## <a name="prerequisites"></a>Requisitos previos

- [Habilite Cloud App Security y Azure Information Protection](azip-integration.md) en el inquilino.
- [Conecte Box](connect-box-to-microsoft-cloud-app-security.md) a Cloud App Security.

## <a name="set-up-data-protection"></a>Configuración de la protección de datos

Vamos a configurar una directiva que busque números de tarjeta de crédito en los archivos almacenados en su cuenta de Box. Cuando se encuentran los archivos, se aplicará automáticamente una etiqueta de Azure Information Protection y se controlará lo que ocurre con todos los archivos que tengan esa etiqueta.

1. Empiece a proteger los datos que guarda en Box mediante una directiva que cifre todos los datos confidenciales de Box:

    1. En la pestaña **Control**, haga clic en [**Directivas**](control-cloud-apps-with-policies.md). 

    2. Haga clic en **Crear directiva** y seleccione **Directiva de archivo**.

    3. Llame a la directiva *Protección de datos de Box*.

    4. En **Crear un filtro para los archivos a los que se aplicará esta directiva**, defina como objetivo los datos de su propiedad y confidenciales.
        - Por ejemplo, seleccione **Datos del cliente** como **Carpeta principal** en Box y su equipo financiero como **Propietario**.

    5. En esa carpeta, busque los archivos que contengan información de tarjetas de crédito. En **Método de inspección de contenido** seleccione **DLP integrado**, **Incluir los elementos archivos que coincidan con una expresión preestablecida** y **Todos los países: finanzas, número de tarjeta de crédito**.

    6. En **Gobernanza**, abra la sección **Box** y seleccione **Aplicar etiqueta de clasificación**. Seleccione la etiqueta que quiera aplicar.

    7. Puesto que [Cloud App Security se integra con Azure Information Protection](azip-integration.md), puede seleccionar las opciones de su lista de etiquetas de clasificación para proteger los datos.

    8. Haga clic en **Crear**. 

   ![Agregar etiqueta de clasificación a la directiva](./media/aip-auto-policy.png)

2. Investigación de las coincidencias

    1. En la página **Directivas**, haga clic en el nombre de la directiva para ir al **informe de la directiva**. Compruebe las coincidencias que se han activado para la directiva.

    2. Puede investigar la coincidencia haciendo clic en una coincidencia específica para abrir el cajón de archivos. En el cajón, puede ver las otras directivas que coincidan con este archivo.

## <a name="validate-your-policy"></a>Validar la directiva

1. Para simular una alerta, vaya a su cuenta de Box e intente acceder a un archivo en la carpeta **Datos del cliente**.
2. Vaya al informe de directiva. Una coincidencia de directiva de archivo debe aparecer en breve. 
3. Puede hacer clic en la coincidencia para ver qué archivos se han protegido. La propia coincidencia se enmascarará para proteger los datos confidenciales.

>[!NOTE]
>
> - Actualmente, Cloud App Security admite la aplicación automática de etiquetas de Azure Information Protection en Box, SharePoint y OneDrive para la Empresa.
> - Cuando un documento se etiqueta con Cloud App Security, no se aplican inmediatamente marcas visuales, sino que se aplican cuando se abre ese documento en una aplicación de Office y se guarda por primera vez. Para obtener más información, consulte [Configuración de una etiqueta para marcas visuales de Azure Information Protection](https://docs.microsoft.com/information-protection/deploy-use/configure-policy-markings#when-visual-markings-are-applied).

## <a name="next-steps"></a>Pasos siguientes

[Actividades diarias para proteger el entorno de nube](daily-activities-to-protect-your-cloud-environment.md)   

[Los clientes Premier también pueden crear una solicitud de soporte técnico directamente en el portal Premier.](https://premier.microsoft.com/)  
  
  
