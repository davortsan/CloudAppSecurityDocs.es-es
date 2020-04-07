---
title: Solución de problemas de errores de Cloud Discovery-Cloud App Security | Microsoft Docs
description: En este artículo se proporciona una lista de Cloud Discovery errores frecuentes y recomendaciones de resolución para cada uno.
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
ms.openlocfilehash: ea537c11bfb94f8f33f467ca04b5d797a3821635
ms.sourcegitcommit: 94f36e81067f05f841bec25bc31dd8983fde18f9
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80675476"
---
# <a name="troubleshooting-cloud-discovery"></a>Solución de problemas de Cloud Discovery

*Se aplica a: Microsoft Cloud App Security*

En este artículo se proporciona una lista de errores de Cloud Discovery y recomendaciones de resolución para cada uno.

## <a name="microsoft-defender-atp-integration"></a>Integración de ATP de Microsoft defender

Si ha integrado ATP de Microsoft defender con Cloud App Security y no ve los resultados de la integración.

|Problema|Solución|
|----|----|
|**Los** informes de usuarios del punto de conexión de Win10 no aparecen en la lista|Asegúrese de que las máquinas a las que se va a conectar son la versión 1809 o posterior de Windows 10 y de que ha esperado las dos horas necesarias para que se pueda tener acceso a los datos.|
|Los informes de detección están vacíos|Si el dispositivo de punto de conexión está detrás de un proxy de reenvío, puede enviar registros desde el proxy de reenvío mediante un compilador de registros.|

## <a name="log-parsing-errors"></a>Errores de análisis de registro

Puede realizar un seguimiento del procesamiento de registros de Cloud Discovery mediante el registro de gobierno. En este artículo se proporcionan las acciones de resolución que se deben realizar para cada error que se puede mostrar allí.

### <a name="governance-log-errors"></a>Errores de registro de gobierno

|Error|Descripción|Solución|
|----|----|----|
|Tipo de archivo no admitido|El archivo cargado no es un archivo de registro válido (por ejemplo, un archivo de imagen).|Cargue un archivo de **texto**, * * ZIP o **gzip** que se haya exportado directamente desde el firewall o el proxy.|
|El formato del registro no coincide|El formato de registro que ha cargado no coincide con el formato de registro esperado para este origen de datos.|1. Compruebe que el registro no esté dañado. <br /> 2. Compare y haga coincidir el registro con el formato de ejemplo que se muestra en la página de carga.|
|Las transacciones tienen más de 90 días de antigüedad|Todas las transacciones tienen más de 90 días de antigüedad y se omiten.|Exporte un nuevo registro con eventos recientes y recárguelo.|
|No hay transacciones para aplicaciones catalogadas en la nube|No se encuentra ninguna transacción en ninguna aplicación en la nube reconocida en el registro.|Compruebe que el registro contiene información sobre el tráfico de salida.|
|Tipo de registro no admitido|Al seleccionar **origen de datos = otro (no compatible)** , no se analiza el registro. En su lugar, se envía para su revisión al equipo técnico de Cloud App Security.|El equipo técnico de Cloud App Security crea un analizador dedicado por cada origen de datos. [Ya se admiten](set-up-cloud-discovery.md)los orígenes de datos más populares. Cada carga de un origen de datos no admitido se revisa y se agrega a la canalización para los nuevos Analizadores de orígenes de datos. Las nuevas notificaciones del analizador se publican como parte de las notas de la [versión](release-notes.md)Cloud App Security.|

## <a name="log-collector-errors"></a>Errores del recopilador de registros

|Problema|Solución|
|----|----|
|No se pudo conectar con el recopilador de registros a través de FTP| 1. Compruebe que está usando credenciales de FTP y no credenciales de SSH. <br />2. Compruebe que el cliente FTP que está utilizando no está establecido en SFTP.  |
|No se pudo actualizar la configuración del recopilador | 1. Compruebe que ha escrito el token de acceso más reciente. <br />2. Compruebe en el firewall que el recopilador de registros puede iniciar el tráfico saliente en el puerto 443.|
|Los registros enviados al Recopilador no aparecen en el portal | 1. Compruebe si hay tareas de análisis erróneas en el registro de gobierno.  <br />  &nbsp;&nbsp;&nbsp;&nbsp;si es así, solucione el error con la tabla de errores de análisis de registro anterior.<br /> 2. Si no es así, compruebe los orígenes de datos y la configuración del recopilador de registros en el portal. <br /> &nbsp;&nbsp;&nbsp;&nbsp;. En la página origen de datos, compruebe que el origen de datos que está usando se haya configurado de forma precisa. <br />&nbsp;&nbsp;&nbsp;&nbsp;b. En la página recopiladores de registros, compruebe que el origen de datos está vinculado al compilador de registros correcto. <br /> 3. Compruebe la configuración local del equipo del recopilador de registros local.  <br />&nbsp;&nbsp;&nbsp;&nbsp;. Inicie sesión en el recopilador de registros a través de SSH y ejecute la utilidad collector_config.<br/>&nbsp;&nbsp;&nbsp;&nbsp;b. Confirme que el firewall o el proxy está enviando registros al recopilador de registros mediante el protocolo que ha definido (syslog/TCP, syslog/UDP o FTP) y que los envía al puerto y al directorio correctos.<br /> &nbsp;&nbsp;&nbsp;&nbsp;c. Ejecute netstat en el equipo y compruebe que recibe conexiones entrantes del firewall o proxy <br /> 4. Compruebe que el recopilador de registros tiene permiso para iniciar el tráfico saliente en el puerto 443. |
|Estado del recopilador de registros: creado | No se completó la implementación del recopilador de registros. Complete los pasos de implementación local de acuerdo con la guía de implementación.|
|Estado del recopilador de registros: desconectado | No se recibieron datos en las últimas 24 horas desde ninguno de los orígenes de datos vinculados. |
|Error al extraer la imagen del recopilador más reciente| Si recibe este error durante la implementación de Docker, podría deberse a que no tiene suficiente memoria en el equipo host. Para comprobarlo, ejecute este comando en el host: `docker pull microsoft/caslogcollector`. Si devuelve este error: `failed to register layer: Error processing tar file(exist status 1): write /opt/jdk/jdk1.8.0_152/src.zip: no space left on device` póngase en contacto con el administrador del equipo host para proporcionar más espacio.|

## <a name="discovery-dashboard-errors"></a>Errores del panel de detección

|Problema|Solución|
|----|----|
|Los datos de detección se cargaron y analizaron correctamente, pero el panel Cloud Discovery aparece vacío|Es posible que el panel se filtre por los datos que no tienen los registros, por lo que no hay datos para mostrar. Intente cambiar los filtros en el panel de Cloud Discovery para mostrar los distintos tipos de datos para ver los resultados.|

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Actividades diarias para proteger el entorno de nube](daily-activities-to-protect-your-cloud-environment.md)

[!INCLUDE [Open support ticket](includes/support.md)]
