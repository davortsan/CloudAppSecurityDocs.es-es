---
title: "Configurar la carga de registros automática para informes continuos | Microsoft Docs"
description: "En este tema se describe el proceso para configurar la carga de registros automática para informes continuos en Cloud App Security."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 7/9/2017
ms.topic: get-started-article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: c75ba963-ad5a-48e6-8d5d-610fc6e0b990
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 9f17366c62b202432d8b0c750290b4915f64c929
ms.sourcegitcommit: b2e3af9d0a62dcb6410cc3992183c2888bdf6a2f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/09/2017
---
# <a name="configure-automatic-log-upload-for-continuous-reports"></a>Configurar la carga de registros automática para informes continuos


Los recopiladores de registros permiten automatizar fácilmente la carga de registros desde la red. El recopilador de registros se ejecuta en la red y recibe los registros a través de Syslog o FTP. Cada registro se procesa, se comprime y se transmite automáticamente al portal. Los registros de FTP se cargan en Cloud App Security después de que el archivo finaliza la transferencia FTP al recopilador de registros.  Para Syslog, el recopilador de registros escribe los registros recibidos en el disco y carga el archivo en Cloud App Security cuando el tamaño del archivo es mayor de 40 KB.

Una vez que se ha cargado un registro en Cloud App Security, se mueve a un directorio de copia de seguridad que almacena los últimos 20 registros en un momento dado. Cuando llegan los nuevos registros, se eliminan los antiguos. Cuando el espacio en disco del recopilador de registros esté lleno, el recopilador descartará los nuevos registros hasta que tenga más espacio libre en disco.

Antes de configurar la recopilación automática de archivos de registros, compruebe que el registro coincide con el tipo de registro esperado, para asegurarse de que Cloud App Security puede analizar el archivo específico.

> [!NOTE]
> Cloud App Security permite el reenvío de registros desde el servidor SIEM al recopilador de registros siempre que estos se reenvíen en su formato original. Pero es muy recomendable que se integre el recopilador de registros directamente con el firewall o el proxy.

## <a name="deployment-modes"></a>Modos de implementación

El recopilador de registros admite dos modos de implementación:

-   **Contenedor** (*basado en Docker CE*): se ejecuta como una imagen de Docker en [Windows](discovery-docker-windows.md) y [Ubuntu](discovery-docker-ubuntu.md), ya sea de forma local o en Azure.

-   **Dispositivo virtual** (*en desuso*): [se ejecuta como una imagen a través del hipervisor de Hyper-V o VMware](configure-automatic-log-upload-for-continuous-reports.md).




## <a name="see-also"></a>Consulte también
 
[Crear informes de instantáneas de Cloud Discovery](create-snapshot-cloud-discovery-reports.md)

[Trabajar con datos de Cloud Discovery](working-with-cloud-discovery-data.md)

