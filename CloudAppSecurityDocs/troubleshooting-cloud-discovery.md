---
title: "Solución de errores de Cloud Discovery en Cloud App Security | Microsoft Docs"
description: "En este tema se proporciona una lista de errores frecuentes de Cloud Discovery y recomendaciones para la solución de cada uno de ellos."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 1/23/2017
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: 76dfaebb-d477-4bdb-b3d7-04cc3fe6431d
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 1cd697631f776c55fbedcec9a0ed34a3b68d8ac0
ms.sourcegitcommit: 355226ee21981563066d637e7db0bff0d53c2da6
translationtype: HT
---
# <a name="troubleshooting-cloud-discovery"></a>Solución de problemas de Cloud Discovery
## <a name="log-parsing-errors"></a>Errores de análisis de registro

Puede realizar un seguimiento del procesamiento de registros de Cloud Discovery mediante el registro de gobierno. En esta guía se proporcionan las acciones de resolución que se deben tomar para cada uno de los errores que se pueden mostrar allí.

### <a name="governance-log-errors"></a>Errores del registro de gobierno
|ERROR|DESCRIPCIÓN|SOLUCIÓN|
|----|----|----|
|Tipo de archivo no admitido|El archivo cargado no es un archivo de registro válido (por ejemplo, un archivo de imagen).|Cargue un archivo de **texto**, **zip** o **gzip** que se haya exportado directamente desde el firewall o el proxy.|
|Error interno.|Se ha detectado un error de recurso interno.|Haga clic en **Reintentar** para volver a ejecutar la tarea.|
|El formato del registro no coincide|El formato del registro que ha cargado no coincide con el formato esperado para este origen de datos.|1. Compruebe que el registro no está dañado. <br /> 2. Compare y haga coincidir el registro con el formato de ejemplo que se muestra en la página de carga.|
|Las transacciones tienen más de 90 días|Todas las transacciones tienen más de 90 días y, por lo tanto, se omitirán.|Exporte un registro nuevo con eventos recientes y vuelva a cargarlo.|
|No hay transacciones con las aplicaciones de nube catalogadas|No se ha encontrado en el registro ninguna transacción con las aplicaciones de nube reconocidas.|Compruebe que el registro contiene información sobre el tráfico saliente.|
|Tipo de registro no admitido|Al seleccionar **Origen de datos = Otro (no admitido)**, el registro no se analiza. En su lugar, se envía para su revisión al equipo técnico de Cloud App Security.|El equipo técnico de Cloud App Security crea un analizador dedicado por cada origen de datos. Los orígenes de datos más populares [ya se admiten](set-up-cloud-discovery.md). Cada carga de un origen de datos no admitido se revisa y se agrega a la canalización para los analizadores de orígenes de datos nuevos. Las nuevas notificaciones del analizador se publican como parte de las notas de la versión de Cloud App Security.|
## <a name="log-collector-errors"></a>Errores del recopilador de registros

|PROBLEMA|SOLUCIÓN|
|----|----|
|No se pudo conectar al recopilador de registros a través de FTP|1. Compruebe que está usando credenciales de FTP y no credenciales de SSH. <br />2. Compruebe que el cliente de FTP que está usando no está establecido en SFTP.|
|No se pudo actualizar la configuración del recopilador|1. Compruebe que ha especificado el token de acceso más reciente. <br />2. En el firewall, compruebe que el recopilador de registros tiene permiso para iniciar tráfico saliente en el puerto 443.|
|Los registros enviados al recopilador no aparecen en el portal|1.  Compruebe si hay tareas de análisis con errores en el registro de gobierno.  <br />  &nbsp;&nbsp;&nbsp;&nbsp;En caso de que las haya, use la anterior tabla Errores de análisis de registro para solucionar el error.<br /> 2. En caso de que no las haya, compruebe los orígenes de datos y la configuración del recopilador de registros en el portal. <br /> &nbsp;&nbsp;&nbsp;&nbsp;a. En la página Origen de datos, compruebe que el origen de datos que está usando está configurado de forma precisa. <br />&nbsp;&nbsp;&nbsp;&nbsp;b. En la página Recopiladores de registros, compruebe que el origen de datos está vinculado al recopilador de registros correcto. <br /> 3. Compruebe la configuración local de la máquina del recopilador de registros local.  <br />&nbsp;&nbsp;&nbsp;&nbsp;a. Inicie sesión en el recopilador de registros mediante SSH y ejecute la utilidad collector_config.<br/>&nbsp;&nbsp;&nbsp;&nbsp;b. Confirme que el firewall o proxy envía los registros al recopilador de registros mediante el protocolo definido (Syslog/TCP, Syslog/UDP o FTP) y que los envía al puerto y directorio correctos.<br /> &nbsp;&nbsp;&nbsp;&nbsp;c. Ejecute netstat en la máquina y compruebe que recibe las conexiones entrantes del firewall o proxy. <br /> 4.   Compruebe que el recopilador de registros tiene permiso para iniciar tráfico saliente en el puerto 443.|

## <a name="see-also"></a>Consulte también  
[Actividades diarias para proteger el entorno de nube](daily-activities-to-protect-your-cloud-environment.md)   
[Para obtener soporte técnico, visite la página de soporte técnico asistido de Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Los clientes Premier también pueden elegir Cloud App Security directamente desde el Portal Premier.](https://premier.microsoft.com/)  
  
  