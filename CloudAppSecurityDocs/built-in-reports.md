---
title: Cómo generar informes en Microsoft Cloud App Security | Microsoft Docs
description: En este tema se ofrecen instrucciones para generar informes de administración de datos en Microsoft Cloud App Security.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 6/10/2018
ms.topic: conceptual
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 0dcc3c35-f787-4822-84c6-d4dff897dd6c
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 41129ee4329c17b6a87aac367ff91708c5a382f3
ms.sourcegitcommit: e500101377562f4432a5a3c21b97e67a8b788e88
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/21/2018
ms.locfileid: "46563133"
---
*Se aplica a: Microsoft Cloud App Security*



# <a name="generate-data-management-reports"></a>Generar informes de administración de datos

Microsoft Cloud App Security permite generar informes con los que se proporciona una visión general de los archivos que hay en las aplicaciones en la nube.

Para generar estos informes, siga estos pasos:

1. Vaya a **Archivos**. 
2. En la esquina superior derecha, haga clic en los tres puntos y, en **Informes de administración de datos**, seleccione uno de los informes que se indican a continuación.

   ![Informes](./media/reports.png)
## <a name="data-sharing-overview"></a>Información general sobre el uso compartido de datos 

Se muestra el número de archivos almacenados en las aplicaciones en la nube, divididos en función de los permisos de acceso. El uso compartido se ha convertido en un proceso fácil con las aplicaciones en la nube debido a la facilidad de acceso y la ubicuidad. Los archivos que no se comparten con nadie más que el propietario se denominan archivos privados. Si se comparte un archivo, Cloud App Security distingue cuatro tipos de estados: <br> - Un archivo compartido públicamente (web) es aquel al que se puede tener acceso sin autenticación, incluso a través de los resultados de un motor de búsqueda.<br> - Un archivo compartido públicamente es aquel al que se puede tener acceso sin autenticación a través de un enlace.<br> - Un archivo compartido externamente es aquel al que pueden tener acceso usuarios ajenos a la organización después de autenticarse en la aplicación en la nube.<br> - Un archivo compartido internamente es aquel al que pueden tener acceso todos o algunos de los usuarios de la organización.

## <a name="outbound-sharing-by-domain"></a>Uso compartido externo por dominio

Se muestran los dominios con los que los empleados comparten archivos corporativos. En el informe se indica para cada dominio qué usuarios corporativos comparten archivos con qué dominio, qué archivos se comparten y quiénes son los colaboradores con los que se comparten los archivos. Se recomienda que administre el uso compartido con estos dominios a través de la pestaña Archivos de la página de cada aplicación en cuestión.

## <a name="owners-of-shared-files"></a>Propietarios de archivos compartidos

Se muestran los usuarios que comparten archivos corporativos con el exterior. Los archivos compartidos externamente se comparten con colaboradores externos específicos. Los archivos compartidos públicamente son accesibles para cualquier usuario de Internet, a través de un vínculo privado, y solo los pueden encontrar aquellos que están expuestos explícitamente al vínculo. Los archivos compartidos públicamente (Internet) son accesibles para cualquier usuario de Internet, incluso a través de los resultados de un motor de búsqueda. Si detecta usuarios que comparten un número excesivo de archivos, es recomendable que investigue la naturaleza de este exceso de permisos de uso compartido mediante la pestaña Archivos y que se ponga en contacto con dichos usuarios para comprender mejor este uso compartido externo.


  
## <a name="see-also"></a>Consulte también 
[Control](control.md)   

[Los clientes Premier también pueden elegir Cloud App Security directamente desde el Portal Premier.](https://premier.microsoft.com/)  
  
  