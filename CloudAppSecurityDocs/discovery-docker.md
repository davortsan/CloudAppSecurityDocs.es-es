---
title: Configurar la carga de registros automática para informes continuos | Microsoft Docs
description: En este artículo se describe el proceso de configuración de la carga de registros automática para informes continuos en Cloud App Security.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 12/9/2018
ms.topic: conceptual
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: c75ba963-ad5a-48e6-8d5d-610fc6e0b990
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 0b62a5b7b3270076efd3763488d87b14b8c78632
ms.sourcegitcommit: c497253a7ab63973bb806607e5f15dece91640be
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/10/2018
ms.locfileid: "53123761"
---
# <a name="configure-automatic-log-upload-for-continuous-reports"></a>Configurar la carga de registros automática para informes continuos

*Se aplica a: Microsoft Cloud App Security*

Los recopiladores de registros permiten automatizar fácilmente la carga de registros desde la red. El recopilador de registros se ejecuta en la red y recibe los registros a través de Syslog o FTP. Cada registro se procesa, se comprime y se transmite automáticamente al portal. Los registros de FTP se cargan en Microsoft Cloud App Security una vez que el archivo haya finalizado la transferencia FTP al recopilador de registros. Para Syslog, el recopilador de registros escribe los registros recibidos en el disco. Después el recopilador carga el archivo en Cloud App Security cuando el tamaño de archivo es superior a 40 KB. 

Tras la carga de un registro en Cloud App Security, este se mueve a un directorio de copia de seguridad. El directorio de copia de seguridad almacena los últimos 20 registros. Cuando llegan los nuevos registros, se eliminan los antiguos. Cuando el espacio en disco del recopilador de registros esté lleno, el recopilador descartará los nuevos registros hasta que tenga más espacio libre en disco. Cuando esto ocurra, recibirá una advertencia en la pestaña **Recopiladores de registros** de la configuración **Cargar registros automáticamente**.

Antes de configurar la recopilación de archivos de registro, compruebe que el registro coincide con el tipo de registro esperado. Debe asegurarse de que Cloud App Security puede analizar el archivo específico. Para obtener más información, vea [Uso de registros de tráfico para Cloud Discovery](create-snapshot-cloud-discovery-reports.md#log-format).


> [!NOTE]
>-  Cloud App Security permite el reenvío de registros desde el servidor SIEM al recopilador de registros siempre que estos se reenvíen en su formato original. Aun así, se recomienda encarecidamente integrar el recopilador de registros directamente en el firewall o proxy.
>- El recopilador de registros comprime los datos antes de que se carguen. El tráfico saliente en el recopilador de registros constituirá un 10 % del tamaño de los registros de tráfico que recibe. 
>-  Si el recopilador de registros detecta problemas, recibirá una alerta después de que no se hayan recibido datos durante 48 horas.
>

## <a name="deployment-modes"></a>Modos de implementación

El recopilador de registros admite dos modos de implementación:

-   **Contenedor**: se ejecuta como imagen Docker en [Ubuntu local](discovery-docker-ubuntu.md), [Ubuntu en Azure](discovery-docker-ubuntu-azure.md) o en [RHEL local](discovery-docker-ubuntu.md). 

-   **Aplicación virtual**: [se ejecuta como una imagen a través del hipervisor de Hyper-V o de VMware](configure-automatic-log-upload-for-continuous-reports.md)




## <a name="next-steps"></a>Pasos siguientes
 
[Crear informes de instantáneas de Cloud Discovery](create-snapshot-cloud-discovery-reports.md)

[Trabajar con datos de Cloud Discovery](working-with-cloud-discovery-data.md)

