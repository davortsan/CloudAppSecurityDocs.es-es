---
title: Configurar la carga de registros automática para informes continuos | Microsoft Docs
description: En este tema se describe el proceso de configuración de la carga de registros automática para informes continuos en Cloud App Security.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 6/11/2018
ms.topic: conceptual
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: c75ba963-ad5a-48e6-8d5d-610fc6e0b990
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 06b011e28a293c09f6d3f40e904252178045431d
ms.sourcegitcommit: 0ac08ca7b3140b79f1d36ff7152476c188fa12b3
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/07/2018
ms.locfileid: "44143571"
---
*Se aplica a: Microsoft Cloud App Security*


# <a name="configure-automatic-log-upload-for-continuous-reports"></a>Configurar la carga de registros automática para informes continuos


Los recopiladores de registros permiten automatizar fácilmente la carga de registros desde la red. El recopilador de registros se ejecuta en la red y recibe los registros a través de Syslog o FTP. Cada registro se procesa, se comprime y se transmite automáticamente al portal. Los registros de FTP se cargan en Microsoft Cloud App Security una vez que el archivo haya finalizado la transferencia FTP al recopilador de registros.  En el caso de Syslog, el recopilador de registros escribe los registros recibidos en el disco y carga el archivo en Cloud App Security una vez que el tamaño de archivo sea superior a 40 KB.

Una vez que se ha cargado un registro en Cloud App Security, se mueve a un directorio de copia de seguridad que almacena los últimos 20 registros en un momento dado. Cuando llegan los nuevos registros, se eliminan los antiguos. Cuando el espacio en disco del recopilador de registros esté lleno, el recopilador descartará los nuevos registros hasta que tenga más espacio libre en disco. Cuando esto ocurra, recibirá una advertencia en la pestaña **Recopiladores de registros** de la configuración **Cargar registros automáticamente**.

Antes de configurar la recopilación automática de archivos de registros, compruebe que el registro coincide con el tipo de registro esperado, para asegurarse de que Cloud App Security puede analizar el archivo específico.

> [!NOTE]
>-  Cloud App Security permite el reenvío de registros desde el servidor SIEM al recopilador de registros siempre que estos se reenvíen en su formato original. Aun así, se recomienda encarecidamente integrar el recopilador de registros directamente en el firewall o proxy.
>- El recopilador de registros comprime los datos antes de que se carguen. El tráfico saliente en el recopilador de registros constituirá un 10 % del tamaño de los registros de tráfico que recibe. 

## <a name="deployment-modes"></a>Modos de implementación

El recopilador de registros admite dos modos de implementación:

-   **Contenedor**: se ejecuta como imagen Docker en [Ubuntu local](discovery-docker-ubuntu.md), [Ubuntu en Azure](discovery-docker-ubuntu-azure.md) o en [RHEL local](discovery-docker-ubuntu.md). 

-   **Aplicación virtual**: [se ejecuta como una imagen a través del hipervisor de Hyper-V o de VMware](configure-automatic-log-upload-for-continuous-reports.md)




## <a name="see-also"></a>Consulta también
 
[Crear informes de instantáneas de Cloud Discovery](create-snapshot-cloud-discovery-reports.md)

[Trabajar con datos de Cloud Discovery](working-with-cloud-discovery-data.md)

