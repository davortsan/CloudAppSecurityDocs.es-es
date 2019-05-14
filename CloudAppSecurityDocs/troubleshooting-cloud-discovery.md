---
title: 'Solución de errores de Cloud Discovery: Cloud App Security | Microsoft Docs'
description: En este artículo se proporciona una lista de errores frecuentes de Cloud Discovery y recomendaciones para la solución de cada uno de ellos.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: rkarlin
ms.date: 04/19/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 76dfaebb-d477-4bdb-b3d7-04cc3fe6431d
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: bc8e477cac15dc9b5bd3338360d7c3953db0e442
ms.sourcegitcommit: 9f0c562322394a3dfac7f1d84286e673276a28b1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/14/2019
ms.locfileid: "65568813"
---
# <a name="troubleshooting-cloud-discovery"></a>Solución de problemas de Cloud Discovery

*Se aplica a: Microsoft Cloud App Security*

En este artículo se proporciona una lista de errores de Cloud Discovery y recomendaciones para la solución de cada uno de ellos.

## <a name="microsoft-defender-atp-integration"></a>Integración de Microsoft Defender ATP

Si integra Microsoft Defender ATP con Cloud App Security, y no ve los resultados de la integración: no hay un **los usuarios del extremo de Win10** report - Asegúrese de que las máquinas que se conecta a Windows 10 versión 1809 o más adelante, y que esperaron las dos horas es necesarias que se tarda antes de los datos son accesible.


## <a name="log-parsing-errors"></a>Errores de análisis de registro

Puede realizar un seguimiento del procesamiento de registros de Cloud Discovery mediante el registro de gobernanza. En este artículo se proporcionan las acciones para resolver cada uno de los errores que se pueden mostrar allí.

### <a name="governance-log-errors"></a>Errores del registro de gobernanza

|Error|Descripción|Solución|
|----|----|----|
|Tipo de archivo no admitido|El archivo cargado no es un archivo de registro válido (por ejemplo, un archivo de imagen).|Cargue un archivo de **texto**, **zip o **gzip** que se haya exportado directamente desde el firewall o el proxy.|
|El formato del registro no coincide|El formato del registro que ha cargado no coincide con el formato esperado para este origen de datos.|1. Compruebe que el registro no esté dañado. <br /> 2. Compare y haga coincidir el registro con el formato de ejemplo que se muestra en la página de carga.|
|Las transacciones tienen más de 90 días|Todas las transacciones tienen más de 90 días y se omitirán.|Exporte un registro nuevo con eventos recientes y vuelva a cargarlo.|
|No hay transacciones con las aplicaciones de nube catalogadas|No se ha encontrado ninguna transacción con las aplicaciones de nube reconocidas en el registro.|Compruebe que el registro contiene información sobre el tráfico saliente.|
|Tipo de registro no admitido|Al seleccionar **Origen de datos = Otro (no admitido)**, el registro no se analiza. En su lugar, se envía para su revisión al equipo técnico de Cloud App Security.|El equipo técnico de Cloud App Security crea un analizador dedicado por cada origen de datos. Los orígenes de datos más populares [ya se admiten](set-up-cloud-discovery.md). Cada carga de un origen de datos no admitido se revisa y se agrega a la canalización para los analizadores de orígenes de datos nuevos. Las nuevas notificaciones del analizador se publican como parte de las [notas de la versión](release-notes.md) de Cloud App Security.|

## <a name="log-collector-errors"></a>Errores del recopilador de registros

|PROBLEMA | SOLUCIÓN |
|--------|--|
|No se pudo conectar al recopilador de registros a través de FTP| 1. Compruebe que está usando credenciales de FTP y no credenciales de SSH. <br />2. Compruebe que el cliente de FTP que está usando no está establecido en SFTP.  |
|No se pudo actualizar la configuración del recopilador | 1. Compruebe que ha especificado el token de acceso más reciente. <br />2. En el firewall, compruebe que el recopilador de registros tiene permiso para iniciar tráfico saliente en el puerto 443.|
|Los registros enviados al recopilador no aparecen en el portal | 1.  Compruebe si hay tareas de análisis con errores en el registro de gobernanza.  <br />  &nbsp;&nbsp;&nbsp;&nbsp;En caso de que las haya, use la anterior tabla Errores de análisis de registro para solucionar el error.<br /> 2. En caso de que no las haya, compruebe los orígenes de datos y la configuración del recopilador de registros en el portal. <br /> &nbsp;&nbsp;&nbsp;&nbsp;a. En la página Origen de datos, compruebe que el origen de datos que está usando está configurado de forma precisa. <br />&nbsp;&nbsp;&nbsp;&nbsp;b. En la página Recopiladores de registros, compruebe que el origen de datos está vinculado al recopilador de registros correcto. <br /> 3. Compruebe la configuración local de la máquina del recopilador de registros local.  <br />&nbsp;&nbsp;&nbsp;&nbsp;a. Inicie sesión en el recopilador de registros mediante SSH y ejecute la utilidad collector_config.<br/>&nbsp;&nbsp;&nbsp;&nbsp;b. Confirme que el firewall o proxy envía los registros al recopilador de registros mediante el protocolo definido (Syslog/TCP, Syslog/UDP o FTP) y que los envía al puerto y directorio correctos.<br /> &nbsp;&nbsp;&nbsp;&nbsp;c. Ejecute netstat en la máquina y compruebe que recibe las conexiones entrantes del firewall o proxy. <br /> 4.   Compruebe que el recopilador de registros tiene permiso para iniciar tráfico saliente en el puerto 443. |
|Estado del recopilador de registros: Creado | No se ha completado la implementación del recopilador de registros. Complete los pasos de implementación local indicados en la guía de implementación.|
|Estado del recopilador de registros: Disconnected | No se han recibido datos durante las últimas 24 horas de ninguno de los orígenes de datos vinculados. |
|No se pudo extraer la imagen más reciente del recopilador| Si recibe este error durante la implementación de Docker, es posible que no tiene suficiente memoria en el equipo host. Para comprobarlo, ejecute este comando en el host: `docker pull microsoft/caslogcollector`. Si devuelve este error: `failed to register layer: Error processing tar file(exist status 1): write /opt/jdk/jdk1.8.0_152/src.zip: no space left on device` póngase en contacto con el administrador del equipo host para proporcionar más espacio.|

## <a name="discovery-dashboard-errors"></a>Errores del panel de detección

|Problema|Solución|
|----|----|
|Los datos de detección se han cargado y analizado correctamente, pero el panel de Cloud Discovery parece vacío|El panel puede estar filtrado por datos que los registros no tienen, por lo que no hay ningún dato que mostrar. Pruebe a cambiar los filtros del panel de Cloud Discovery para mostrar tipos de datos diferentes para ver los resultados.|

## <a name="next-steps"></a>Pasos siguientes
  
[Actividades diarias para proteger el entorno de nube](daily-activities-to-protect-your-cloud-environment.md)   

[Los clientes Premier también pueden crear una solicitud de soporte técnico directamente en el portal Premier.](https://premier.microsoft.com/)  

