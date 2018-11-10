---
title: Cómo generar informes en Microsoft Cloud App Security | Microsoft Docs
description: En este tema se ofrecen instrucciones para generar informes de administración de datos en Microsoft Cloud App Security.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 10/11/2018
ms.topic: conceptual
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 0dcc3c35-f787-4822-84c6-d4dff897dd6c
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 7684e6e3172076d8f7e8a4d69b1ddd70d322a200
ms.sourcegitcommit: 82052a88acbc33893f7b9e0d10cc2e8c652ef003
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/16/2018
ms.locfileid: "49349515"
---
*Se aplica a: Microsoft Cloud App Security*



# <a name="generate-data-management-reports"></a>Generar informes de administración de datos

Microsoft Cloud App Security permite generar informes con los que se proporciona una visión general de los archivos que hay en las aplicaciones en la nube.

Para generar estos informes, siga estos pasos:

1. Vaya a **Archivos**. 
2. En la esquina superior derecha, haga clic en los tres puntos y, en **Informes de administración de datos**, seleccione uno de los informes que se indican a continuación.

 ![informes](./media/reports.png)

## <a name="data-sharing-overview"></a>Información general sobre el uso compartido de datos 

En este informe se muestra el número de archivos (por permisos de acceso) almacenados en cada aplicación en la nube. El uso compartido de archivos se ha convertido en un proceso fácil con las aplicaciones en la nube debido a la facilidad de acceso y la ubicuidad. Los archivos **privados** no se comparten con nadie más que su propietario. Si se comparte un archivo, Cloud App Security distingue cuatro tipos de estados:
- Los archivos **compartidos públicamente (Internet)** son aquellos a los que se puede acceder sin autenticación, incluso a través de los resultados de un motor de búsqueda.
 - Los archivos **compartidos públicamente** son aquellos a los que se puede acceder sin autenticación a través de un vínculo.
 - Los archivos **compartidos externamente** son aquellos a los que pueden acceder los usuarios ajenos a la organización después de autenticarse en la aplicación en la nube.
- Los archivos **compartidos internamente** son aquellos a los que pueden acceder todos o algunos de los usuarios de la organización.

## <a name="outbound-sharing-by-domain"></a>Uso compartido externo por dominio

En este informe se muestran los dominios con los que los empleados comparten archivos corporativos. Para cada dominio, el informe muestra qué usuarios comparten archivos con ese dominio. El informe también muestra qué archivos se comparten y con quién se comparten los archivos de colaboradores. Es recomendable que usted administre el uso compartido con estos dominios. Puede hacerlo mediante la pestaña Archivos de la página de cada aplicación en cuestión.

## <a name="owners-of-shared-files"></a>Propietarios de archivos compartidos

Se muestran los usuarios que comparten archivos corporativos con el exterior. Los archivos compartidos externamente son aquellos que se comparten con colaboradores externos específicos. Todos los usuarios de Internet pueden acceder mediante un vínculo a los archivos compartidos públicamente. Estos archivos solo los pueden encontrar las personas que tienen el vínculo correspondiente. Los archivos compartidos públicamente (Internet) son accesibles para cualquier usuario de Internet, incluso a través de los resultados de un motor de búsqueda. Si detecta usuarios que comparten una cantidad excesiva de archivos, le recomendamos que investigue por qué. Para investigarlo, puede utilizar la pestaña Archivos y, después, ponerse en contacto con esos usuarios para obtener más información sobre su uso compartido externo.


  
## <a name="next-steps"></a>Pasos siguientes 
[Control](control.md)   

[Los clientes Premier también pueden elegir Cloud App Security directamente desde el Portal Premier.](https://premier.microsoft.com/)  
  
  