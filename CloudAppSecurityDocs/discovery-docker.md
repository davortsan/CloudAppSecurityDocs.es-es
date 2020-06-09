---
title: Configuración de la carga de registros automática para informes continuos en Cloud App Security
description: En este artículo se describe el proceso de configuración de la carga de registros automática para informes continuos en Cloud App Security.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 7/22/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 73b9f8a7ea1bd3f2b93b4199b58cfb5178f13edc
ms.sourcegitcommit: 72c96b9b2b9f6555e5e20749ebe61593072b1d50
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/08/2020
ms.locfileid: "84487770"
---
# <a name="configure-automatic-log-upload-for-continuous-reports"></a>Configurar la carga de registros automática para informes continuos

*Se aplica a: Microsoft Cloud App Security*

Los recopiladores de registros permiten automatizar fácilmente la carga de registros desde la red. El recopilador de registros se ejecuta en la red y recibe los registros a través de Syslog o FTP. Cada registro se procesa, se comprime y se transmite automáticamente al portal. Los registros de FTP se cargan en Microsoft Cloud App Security una vez que el archivo haya finalizado la transferencia FTP al recopilador de registros. Para Syslog, el recopilador de registros escribe los registros recibidos en el disco. Después el recopilador carga el archivo en Cloud App Security cuando el tamaño de archivo es superior a 40 KB.

Tras la carga de un registro en Cloud App Security, este se mueve a un directorio de copia de seguridad. El directorio de copia de seguridad almacena los últimos 20 registros. Cuando llegan los nuevos registros, se eliminan los antiguos. Cuando el espacio en disco del recopilador de registros esté lleno, el recopilador descartará los nuevos registros hasta que tenga más espacio libre en disco. Cuando esto ocurra, recibirá una advertencia en la pestaña **Recopiladores de registros** de la configuración **Cargar registros automáticamente**.

Antes de configurar la recopilación de archivos de registro, compruebe que el registro coincide con el tipo de registro esperado. Debe asegurarse de que Cloud App Security puede analizar el archivo específico. Para obtener más información, vea [Uso de registros de tráfico para Cloud Discovery](create-snapshot-cloud-discovery-reports.md#log-format).

> [!NOTE]
>
> * Cloud App Security permite el reenvío de registros desde el servidor SIEM al recopilador de registros siempre que estos se reenvíen en su formato original. Aun así, se recomienda encarecidamente integrar el recopilador de registros directamente en el firewall o proxy.
> * El recopilador de registros comprime los datos antes de que se carguen. El tráfico saliente en el recopilador de registros constituirá un 10 % del tamaño de los registros de tráfico que recibe.
> * Si el recopilador de registros detecta problemas, recibirá una alerta después de que no se hayan recibido datos durante 48 horas.

## <a name="deployment-modes"></a>Modos de implementación

El recopilador de registros admite dos modos de implementación:

* **Contenedor**: se ejecuta como una imagen de Docker en [Windows](discovery-docker-windows.md), [Ubuntu on local](discovery-docker-ubuntu.md), [Ubuntu en Azure](discovery-docker-ubuntu-azure.md), [RHEL on local](discovery-docker-ubuntu.md) o de la instalación.

* **Dispositivo virtual**: se ejecuta como una imagen sobre el hipervisor de Hyper-V o VMware (desusado)

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Trabajo con datos de Cloud Discovery](working-with-cloud-discovery-data.md)
