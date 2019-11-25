---
title: 'Solución de errores de Cloud Discovery: Cloud App Security | Microsoft Docs'
description: En este artículo se proporciona una lista de errores frecuentes de Cloud Discovery y recomendaciones para la solución de cada uno de ellos.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
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
ms.openlocfilehash: cd11c5a35761f21cc928a3debbc05a58ef56b6d1
ms.sourcegitcommit: 094bb42a198fe733cfd3aec79d74487672846dfa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/24/2019
ms.locfileid: "74459982"
---
# <a name="troubleshooting-cloud-discovery"></a>Solución de problemas de Cloud Discovery

*Se aplica a: Microsoft Cloud App Security*

En este artículo se proporciona una lista de errores de Cloud Discovery y recomendaciones para la solución de cada uno de ellos.

## <a name="microsoft-defender-atp-integration"></a>Microsoft Defender ATP integration

If you integrated Microsoft Defender ATP with Cloud App Security, and you don't see the results of the integration - there's not a **Win10 endpoint users** report - make sure the machines you're connecting to are Windows 10 version 1809 or later, and that you waited the necessary two hours that it takes before your data is accessible.


## <a name="log-parsing-errors"></a>Errores de análisis de registro

Puede realizar un seguimiento del procesamiento de registros de Cloud Discovery mediante el registro de gobernanza. En este artículo se proporcionan las acciones para resolver cada uno de los errores que se pueden mostrar allí.

### <a name="governance-log-errors"></a>Errores del registro de gobernanza

|Error de:|Descripción|Solución|
|----|----|----|
|Tipo de archivo no admitido|El archivo cargado no es un archivo de registro válido (por ejemplo, un archivo de imagen).|Cargue un archivo de **texto**, **zip o **gzip** que se haya exportado directamente desde el firewall o el proxy.|
|El formato del registro no coincide|El formato del registro que ha cargado no coincide con el formato esperado para este origen de datos.|1. Verify that the log isn't corrupt. <br /> 2. Compare and match your log to the sample format shown in the upload page.|
|Las transacciones tienen más de 90 días|Todas las transacciones tienen más de 90 días y se omitirán.|Exporte un registro nuevo con eventos recientes y vuelva a cargarlo.|
|No hay transacciones con las aplicaciones de nube catalogadas|No se ha encontrado ninguna transacción con las aplicaciones de nube reconocidas en el registro.|Compruebe que el registro contiene información sobre el tráfico saliente.|
|Tipo de registro no admitido|Al seleccionar **Origen de datos = Otro (no admitido)** , el registro no se analiza. En su lugar, se envía para su revisión al equipo técnico de Cloud App Security.|El equipo técnico de Cloud App Security crea un analizador dedicado por cada origen de datos. Los orígenes de datos más populares [ya se admiten](set-up-cloud-discovery.md). Cada carga de un origen de datos no admitido se revisa y se agrega a la canalización para los analizadores de orígenes de datos nuevos. Las nuevas notificaciones del analizador se publican como parte de las [notas de la versión](release-notes.md) de Cloud App Security.|

## <a name="log-collector-errors"></a>Errores del recopilador de registros

|PROBLEMA | SOLUCIÓN |
|--------|--|
|No se pudo conectar al recopilador de registros a través de FTP| 1. Verify that you are using FTP credentials and not SSH credentials. <br />2. Verify that the FTP client you are using is not set to SFTP.  |
|No se pudo actualizar la configuración del recopilador | 1. Verify that you entered the latest access token. <br />2. Verify in your firewall that the log collector is allowed to initiate outbound traffic on port 443.|
|Los registros enviados al recopilador no aparecen en el portal | 1.  Check to see if there are failed parsing tasks in the Governance log.  <br />  &nbsp;&nbsp;&nbsp;&nbsp;En caso de que las haya, use la anterior tabla Errores de análisis de registro para solucionar el error.<br /> 2. If not, check the data sources and Log collector configuration in the portal. <br /> &nbsp;&nbsp;&nbsp;&nbsp;a. En la página Origen de datos, compruebe que el origen de datos que está usando está configurado de forma precisa. <br />&nbsp;&nbsp;&nbsp;&nbsp;b. En la página Recopiladores de registros, compruebe que el origen de datos está vinculado al recopilador de registros correcto. <br /> 3. Check the local configuration of the on-premises log collector machine.  <br />&nbsp;&nbsp;&nbsp;&nbsp;a. Inicie sesión en el recopilador de registros mediante SSH y ejecute la utilidad collector_config.<br/>&nbsp;&nbsp;&nbsp;&nbsp;b. Confirme que el firewall o proxy envía los registros al recopilador de registros mediante el protocolo definido (Syslog/TCP, Syslog/UDP o FTP) y que los envía al puerto y directorio correctos.<br /> &nbsp;&nbsp;&nbsp;&nbsp;c. Ejecute netstat en la máquina y compruebe que recibe las conexiones entrantes del firewall o proxy. <br /> 4.   Verify that the log collector is allowed to initiate outbound traffic on port 443. |
|Estado del recopilador de registros: Creado | No se ha completado la implementación del recopilador de registros. Complete los pasos de implementación local indicados en la guía de implementación.|
|Estado del recopilador de registros: Desconectado | No se han recibido datos durante las últimas 24 horas de ninguno de los orígenes de datos vinculados. |
|Failed pulling latest collector image| If you get this error during Docker deployment, it could be that you don't have enough memory ont he host machine. To check this, run this command on the host: `docker pull microsoft/caslogcollector`. If it returns this error: `failed to register layer: Error processing tar file(exist status 1): write /opt/jdk/jdk1.8.0_152/src.zip: no space left on device` contact your host machine administrator to provide more space.|

## <a name="discovery-dashboard-errors"></a>Errores del panel de detección

|Problema|Solución|
|----|----|
|Los datos de detección se han cargado y analizado correctamente, pero el panel de Cloud Discovery parece vacío|El panel puede estar filtrado por datos que los registros no tienen, por lo que no hay ningún dato que mostrar. Pruebe a cambiar los filtros del panel de Cloud Discovery para mostrar tipos de datos diferentes para ver los resultados.|

## <a name="next-steps"></a>Pasos siguientes
  
[Actividades diarias para proteger el entorno de nube](daily-activities-to-protect-your-cloud-environment.md)   

[!INCLUDE [Open support ticket](includes/support.md)]  

