---
title: Configurar la carga de registros automática para informes continuos en Cloud App Security
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
ms.openlocfilehash: fb79f5515799ad93e456bb3a97bfa26d16416e5c
ms.sourcegitcommit: 4f3883a9e85d0aaf2802b10433b221c3f1838d88
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/13/2020
ms.locfileid: "79285269"
---
# <a name="configure-automatic-log-upload-for-continuous-reports"></a>Configurar la carga de registros automática para informes continuos

*Se aplica a: Microsoft Cloud App Security*

Los recopiladores de registros permiten automatizar fácilmente la carga de registros desde la red. El recopilador de registros se ejecuta en la red y recibe los registros a través de Syslog o FTP. Cada registro se procesa, se comprime y se transmite automáticamente al portal. Los registros de FTP se cargan en Microsoft Cloud App Security después de que el archivo haya finalizado la transferencia FTP al recopilador de registros. En el caso de syslog, el recopilador de registros escribe los registros recibidos en el disco. Después, el recopilador carga el archivo en Cloud App Security cuando el tamaño del archivo es superior a 40 KB.

Una vez cargado un registro en Cloud App Security, se mueve a un directorio de copia de seguridad. El directorio backup almacena los últimos 20 registros. Cuando llegan los nuevos registros, se eliminan los antiguos. Siempre que el espacio en disco del recopilador de registros esté lleno, el recopilador de registros quitará los nuevos registros hasta que tenga más espacio libre en disco. Recibirá una advertencia en la pestaña **recopiladores de registros** de la configuración **cargar automáticamente los registros** cuando esto suceda.

Antes de configurar la recopilación automática de archivos de registro, compruebe que el registro coincide con el tipo de registro esperado. Desea asegurarse de que Cloud App Security pueda analizar el archivo específico. Para obtener más información, consulte [uso de registros de tráfico para Cloud Discovery](create-snapshot-cloud-discovery-reports.md#log-format).

> [!NOTE]
>
> * Cloud App Security permite el reenvío de registros desde el servidor SIEM al recopilador de registros siempre que estos se reenvíen en su formato original. Pero es muy recomendable que se integre el recopilador de registros directamente con el firewall o el proxy.
> * El compilador de registros comprime los datos antes de cargarlos. El tráfico saliente en el recopilador de registros será del 10% del tamaño de los registros de tráfico que recibe.
> * Si el recopilador de registros detecta problemas, recibirá una alerta después de que no se hayan recibido datos durante 48 horas.

## <a name="deployment-modes"></a>Modos de implementación

El recopilador de registros admite dos modos de implementación:

* **Contenedor**: se ejecuta como una imagen de Docker en [Windows](discovery-docker-windows.md), [Ubuntu on local](discovery-docker-ubuntu.md), [Ubuntu en Azure](discovery-docker-ubuntu-azure.md), [RHEL on local](discovery-docker-ubuntu.md) o de la instalación.

* **Dispositivo virtual**: se ejecuta como una imagen sobre el hipervisor de Hyper-V o VMware (desusado)

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Crear informes de instantáneas de Cloud Discovery](create-snapshot-cloud-discovery-reports.md)

> [!div class="nextstepaction"]
> [Trabajar con datos de Cloud Discovery](working-with-cloud-discovery-data.md)
