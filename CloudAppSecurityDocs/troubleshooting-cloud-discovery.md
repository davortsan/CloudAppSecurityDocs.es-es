---
title: Solución de problemas de errores de Cloud Discovery
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
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 7ec0338c725ccee9656984fbdcdd4bf2fd39d132
ms.sourcegitcommit: a0a8e25bda77fb21f280a0e504896be85b89ed6f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/25/2020
ms.locfileid: "96034116"
---
# <a name="troubleshooting-cloud-discovery"></a>Solución de problemas de Cloud Discovery

[!INCLUDE [Banner for top of topics](includes/banner.md)]

En este artículo se proporciona una lista de errores de Cloud Discovery y recomendaciones para la solución de cada uno de ellos.

## <a name="microsoft-defender-atp-integration"></a>Integración de Microsoft Defender ATP

Si ha integrado ATP de Microsoft defender con Cloud App Security y no ve los resultados de la integración.

|Problema|Resolución|
|----|----|
|**Los** informes de usuarios del punto de conexión de Win10 no aparecen en la lista|Asegúrese de que los dispositivos a los que se va a conectar son Windows 10 versión 1809 o posterior y de que ha esperado las dos horas necesarias para que se pueda tener acceso a los datos.|
|Los informes de detección están vacíos|Si el dispositivo de punto de conexión está detrás de un proxy de reenvío, puede enviar registros desde el proxy de reenvío mediante un compilador de registros.|

## <a name="log-parsing-errors"></a>Errores de análisis de registro

Puede realizar un seguimiento del procesamiento de registros de Cloud Discovery mediante el registro de gobernanza. En este artículo se proporcionan las acciones para resolver cada uno de los errores que se pueden mostrar allí.

### <a name="governance-log-errors"></a>Errores del registro de gobernanza

|Error|Descripción|Resolución|
|----|----|----|
|Tipo de archivo no admitido|El archivo cargado no es un archivo de registro válido (por ejemplo, un archivo de imagen).|Cargue un archivo de **texto**, * * ZIP o **gzip** que se haya exportado directamente desde el firewall o el proxy.|
|El formato del registro no coincide|El formato del registro que ha cargado no coincide con el formato esperado para este origen de datos.|1. Compruebe que el registro no esté dañado. <br /> 2. Compare y haga coincidir el registro con el formato de ejemplo que se muestra en la página de carga.|
|Las transacciones tienen más de 90 días|Todas las transacciones tienen más de 90 días y se omitirán.|Exporte un registro nuevo con eventos recientes y vuelva a cargarlo.|
|No hay transacciones con las aplicaciones de nube catalogadas|No se ha encontrado ninguna transacción con las aplicaciones de nube reconocidas en el registro.|Compruebe que el registro contiene información sobre el tráfico saliente.|
|Tipo de registro no admitido|Al seleccionar **Origen de datos = Otro (no admitido)**, el registro no se analiza. En su lugar, se envía para su revisión al equipo técnico de Cloud App Security.|El equipo técnico de Cloud App Security crea un analizador dedicado por cada origen de datos. Los orígenes de datos más populares [ya se admiten](set-up-cloud-discovery.md). Cada carga de un origen de datos no admitido se revisa y se agrega a la canalización para los analizadores de orígenes de datos nuevos. Las nuevas notificaciones del analizador se publican como parte de las [notas de la versión](release-notes.md) de Cloud App Security.|

## <a name="log-collector-errors"></a>Errores del recopilador de registros

|Problema|Resolución|
|----|----|
|No se pudo conectar al recopilador de registros a través de FTP| 1. Compruebe que está usando credenciales de FTP y no credenciales de SSH. <br />2. Compruebe que el cliente FTP que está utilizando no está establecido en SFTP.  |
|No se pudo actualizar la configuración del recopilador | 1. Compruebe que ha escrito el token de acceso más reciente. <br />2. Compruebe en el firewall que el recopilador de registros puede iniciar el tráfico saliente en el puerto 443.|
|Los registros enviados al recopilador no aparecen en el portal | 1. Compruebe si hay tareas de análisis erróneas en el registro de gobierno.  <br />  &nbsp;&nbsp;&nbsp;&nbsp;En caso de que las haya, use la anterior tabla Errores de análisis de registro para solucionar el error.<br /> 2. Si no es así, compruebe los orígenes de datos y la configuración del recopilador de registros en el portal. <br /> &nbsp;&nbsp;&nbsp;&nbsp;a. En la página origen de datos, compruebe que el nombre del origen de datos es **NSS** y que está configurado correctamente. <br />&nbsp;&nbsp;&nbsp;&nbsp;b. En la página Recopiladores de registros, compruebe que el origen de datos está vinculado al recopilador de registros correcto. <br /> 3. Compruebe la configuración local del equipo del recopilador de registros local.  <br />&nbsp;&nbsp;&nbsp;&nbsp;a. Inicie sesión en el recopilador de registros mediante SSH y ejecute la utilidad collector_config.<br/>&nbsp;&nbsp;&nbsp;&nbsp;b. Confirme que el firewall o proxy envía los registros al recopilador de registros mediante el protocolo definido (Syslog/TCP, Syslog/UDP o FTP) y que los envía al puerto y directorio correctos.<br /> &nbsp;&nbsp;&nbsp;&nbsp;c. Ejecute netstat en la máquina y compruebe que recibe las conexiones entrantes del firewall o proxy. <br /> 4. Compruebe que el recopilador de registros tiene permiso para iniciar el tráfico saliente en el puerto 443. |
|Estado del recopilador de registros: Creado | No se ha completado la implementación del recopilador de registros. Complete los pasos de implementación local indicados en la guía de implementación.|
|Estado del recopilador de registros: Desconectado | No se han recibido datos durante las últimas 24 horas de ninguno de los orígenes de datos vinculados. |
|Error al extraer la imagen del recopilador más reciente| Si recibe este error durante la implementación de Docker, podría deberse a que no tiene suficiente memoria en el host. Para comprobarlo, ejecute este comando en el host: `docker pull mcr.microsoft.com/mcas/logcollector` . Si devuelve este error: `failed to register layer: Error processing tar file(exist status 1): write /opt/jdk/jdk1.8.0_152/src.zip: no space left on device` póngase en contacto con el administrador del equipo host para proporcionar más espacio.|

## <a name="discovery-dashboard-errors"></a>Errores del panel de detección

|Problema|Resolución|
|----|----|
|Los datos de detección se han cargado y analizado correctamente, pero el panel de Cloud Discovery parece vacío|El panel puede estar filtrado por datos que los registros no tienen, por lo que no hay ningún dato que mostrar. Pruebe a cambiar los filtros del panel de Cloud Discovery para mostrar tipos de datos diferentes para ver los resultados.|

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Actividades diarias para proteger el entorno de nube](daily-activities-to-protect-your-cloud-environment.md)

[!INCLUDE [Open support ticket](includes/support.md)]
