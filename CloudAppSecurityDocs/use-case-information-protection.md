---
title: Aplicación automática de etiquetas de clasificación de Azure Information Protection
description: En este tutorial se describe el proceso para aplicar automáticamente etiquetas de clasificación de Azure Information Protection en Microsoft Cloud App Security.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 3/5/2019
ms.topic: tutorial
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 33078d72d6bbcb5430f207a029c3352d776958ba
ms.sourcegitcommit: 575f2b2efa9ca4477d7e60271d21e225ef2c38ea
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/22/2020
ms.locfileid: "90881128"
---
# <a name="tutorial-automatically-apply-azure-information-protection-classification-labels"></a>Tutorial: Aplicación automática de etiquetas de clasificación de Azure Information Protection

[!INCLUDE [Banner for top of topics](includes/banner.md)]

En un mundo ideal, todos los empleados entienden la importancia de la protección de la información y trabajan dentro de las directivas. Sin embargo, en un mundo real, es probable que un asociado que trabaja con cuentas cargue un documento en el repositorio de Box con los permisos incorrectos. Al cabo de una semana, se da cuenta de que información confidencial de su empresa se ha filtrado a la competencia. Microsoft Cloud App Security ayuda a evitar este tipo de desastre antes de que suceda. Esta característica está disponible para Box, SharePoint y OneDrive para la empresa. Aplicar una etiqueta de Azure Information Protection es una de una larga lista de [acciones de gobernanza](governance-actions.md) disponibles.

Este tutorial le ayuda a identificar qué permisos públicos se establecen en un documento que se guarda en el almacenamiento en la nube, de forma que se le avise cuando se produzca una infracción. Además, puede aplicar automáticamente la etiqueta de clasificación **Confidencial** de Azure Information Protection para proporcionar cifrado adicional a los archivos.

> [!div class="checklist"]
>
> * Configuración de la protección de datos
> * Validación de la directiva

## <a name="enhanced-data-level-encryption-protection"></a>Protección mejorada del cifrado de nivel de datos

La integración de Cloud App Security con Azure Information Protection permite un nivel de protección adicional mediante el cifrado automático de los archivos. Cuando Azure Information Protection cifra los archivos, las aplicaciones que admiten este servicio, como Office 365, saben cómo abrir los archivos y respetan los permisos establecidos en las etiquetas de clasificación. Use etiquetas para aplicar reglas de protección específicas. Por ejemplo, establezca un archivo que se pueda abrir, pero no compartir, imprimir, reenviar ni editar.

Este nivel fuerte de protección acompaña siempre al archivo. El archivo sigue estando protegido tanto si lo envía, lo copia o lo almacena en la aplicación de almacenamiento en línea. Si uno de los empleados pierde una llave de memoria USB que contiene el archivo, este se bloquea. Si alguien intenta abrir el archivo, el propietario del archivo recibirá una alerta. Con Cloud App Security, puede aplicar la protección automáticamente. Por ejemplo, establezca todos los archivos que tengan números de tarjeta de crédito o que haya cargado el departamento de finanzas y se compartan externamente, para que se protejan automáticamente con una etiqueta de clasificación.

## <a name="the-threat"></a>La amenaza

Un usuario de su organización guarda los archivos confidenciales de información del cliente en Box y los configura para que se compartan con todos los usuarios de la organización. El usuario no se da cuenta de que no solo su equipo inmediato tiene acceso a esa cuenta de Box, sino el personal entero de soporte técnico. Este acceso incluye a proveedores, asociados y visitantes que, ocasionalmente, pasan por la oficina. Cualquier persona con acceso a la cuenta de Box de su organización ahora tiene acceso a esa información. Este acceso no solo puede ser peligroso para su organización, sino que puede ir en contra de las normativas de información personal en muchos países/regiones y ocasionar posibles problemas legales.

## <a name="the-solution"></a>La solución

Use Cloud App Security con Azure Information Protection para insertar información de clasificación y protección para la protección continua que acompaña a los datos, de forma que permanezcan protegidos con independencia de dónde se almacenen o con quién se compartan. Esta protección le permite compartir los datos de forma segura con compañeros de trabajo, clientes y asociados. Defina quién puede tener acceso a los datos y qué pueden hacer con ellos. Por ejemplo, permita que los usuarios vean y editen archivos, pero no que los impriman o los reenvíen. También puede agregar a los archivos otras [acciones de gobernanza](governance-actions.md) admitidas por Cloud App Security, como quitar colaboradores y quitar las funcionalidades de uso compartido.

## <a name="prerequisites"></a>Requisitos previos

* [Habilite Cloud App Security y Azure Information Protection](azip-integration.md) para su inquilino.
* [Conecte Box](connect-box-to-microsoft-cloud-app-security.md) a Cloud App Security.

## <a name="set-up-data-protection"></a>Configuración de la protección de datos

Vamos a configurar una directiva que busque los números de tarjeta de crédito en los archivos almacenados en la cuenta de Box. Cuando se encuentren los archivos, aplique automáticamente una etiqueta de Azure Information Protection y controle lo que sucede en todos los archivos con esa etiqueta.

1. Para empezar a proteger los datos que se almacenan en Box, configure una directiva que cifre los datos confidenciales almacenados en Box:

    1. En la pestaña **Control**, haga clic en [**Directivas**](control-cloud-apps-with-policies.md).

    2. Haga clic en **Crear directiva** y seleccione **Directiva de archivo**.

    3. Asigne a la directiva el nombre *Protección de datos de Box*.

    4. En **Crear un filtro para los archivos a los que se aplicará esta directiva**, identifique los datos propietarios y confidenciales.
        * Por ejemplo, seleccione **Parent folder** (Carpeta principal) igual a **Customer data** (Datos de clientes) en Box y seleccione **Owner** (Propietario) igual a equipo financiero.

    5. Dentro de esa carpeta, busque los archivos que contengan información de tarjetas de crédito. En **Método de inspección de contenido**, seleccione **DLP integrado**, elija **Incluir archivos que coincidan con una expresión preestablecida** y, luego, **Todos los países: finanzas, número de tarjeta de crédito**.

    6. En **Gobernanza**, abra la sección **Box** y seleccione **Aplicar etiqueta de clasificación**. Seleccione la etiqueta que quiere aplicar.

    7. Como [Cloud App Security se integra con Azure Information Protection](azip-integration.md), puede seleccionar de la lista existente de etiquetas de clasificación la que se va a usar para proteger los datos.

    8. Haga clic en **Crear**.

   ![Adición de etiquetas de clasificación a la directiva](media/aip-auto-policy.png)

2. Investigación de las coincidencias

    1. En la página **Directivas**, haga clic en el nombre de la directiva para ir al **informe de directivas**. Revise las coincidencias que se desencadenaron para la directiva.

    2. Para investigar la coincidencia, haga clic en una coincidencia determinada para abrir el cajón de archivos. En el cajón, puede ver las otras directivas con las que coincide este archivo.

## <a name="validate-your-policy"></a>Validación de la directiva

1. Para simular una alerta, vaya a la cuenta de Box e intente acceder a un archivo en la carpeta **Customer data** (Datos de clientes).
2. Vaya al informe de directivas. Al poco tiempo aparecerá una coincidencia de la directiva de archivo.
3. Puede hacer clic en ella para ver los archivos que se protegieron. La coincidencia se enmascarará para proteger la información confidencial.

>[!NOTE]
>
> *- Actualmente, Cloud App Security admite la aplicación automática de etiquetas de Azure Information Protection en Box, GSuite, SharePoint y OneDrive para la Empresa.
> *- Cuando un documento se etiqueta con Cloud App Security, no se aplican inmediatamente marcas visuales, sino que se aplican cuando se abre ese documento en una aplicación de Office y se guarda por primera vez. Para más información, consulte [Configuración de una etiqueta para marcas visuales de Azure Information Protection](/information-protection/deploy-use/configure-policy-markings#when-visual-markings-are-applied).

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Actividades diarias para proteger el entorno de nube](daily-activities-to-protect-your-cloud-environment.md)

[!INCLUDE [Open support ticket](includes/support.md)]