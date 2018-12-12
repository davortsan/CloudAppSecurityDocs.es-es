---
title: Crear informes de instantánea del uso de aplicaciones en la nube de Cloud Discovery | Microsoft Docs
description: En este artículo se proporciona información sobre cómo cargar registros manualmente para crear un informe de instantáneas de las aplicaciones de Cloud Discovery.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 12/9/2018
ms.topic: conceptual
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: ecc1949d-c861-4636-952a-c3a260719bb5
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 4704f4ccf93fe369efce5e53d3cf99986ed31eff
ms.sourcegitcommit: c497253a7ab63973bb806607e5f15dece91640be
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/10/2018
ms.locfileid: "53124798"
---
# <a name="create-snapshot-cloud-discovery-reports"></a>Crear informes de instantáneas de Cloud Discovery

*Se aplica a: Microsoft Cloud App Security*

Es importante cargar un registro manualmente y dejar que Microsoft Cloud App Security lo analice antes de intentar usar el recopilador de registros automáticos. Para información sobre cómo funciona el recopilador de registros y el formato de registro esperado, vea [Uso de registros de tráfico para Cloud Discovery](#log-format).

Si aún no tiene un registro y quiere ver un ejemplo del aspecto de su registro, descargue un archivo de registro de ejemplo. Siga este procedimiento para ver el aspecto que debería tener el registro.


Para crear un informe de instantáneas:
  
1. Recopile archivos de registro del firewall y el servidor proxy a través de los cuales los usuarios de la organización acceden a Internet. Asegúrese de recopilar registros durante períodos de tráfico pico que sean representativos de toda la actividad de usuario de la organización.  
  
2. En el portal de Cloud App Security, haga clic en **Detectar** y, después, en **Crear un informe de instantáneas**.  
  
   ![Crear nuevo informe de instantáneas](./media/create-new-snapshot-report.png)
     
3. Escriba un **nombre de informe** y una **descripción**
  
    ![Nuevo informe de instantáneas](./media/new-snapshot-report.png) 

4. Seleccione el **Origen de datos** desde el que quiere cargar los archivos de registro.  
  
5. Compruebe el formato del registro para asegurarse de que es correcto según el registro de ejemplo que puede descargar. Haga clic en **View and verify** (Ver y comprobar) y luego haga clic en **Download sample log** (Descargar registro de ejemplo). Compare su registro con el ejemplo proporcionado para asegurarse de que es compatible. 

   ![Comprobar el formato del registro](./media/cloud-discovery-snapshot-verify.png)  

   > [!NOTE]
   > El formato FTP de ejemplo se admite en las instantáneas y la carga automatizada, mientras que Syslog solo se admite en la carga automatizada.<br></br>
   Si se descarga un registro de ejemplo, se descargará un registro de FTP de ejemplo.


6. **Elija los registros de tráfico** que quiera cargar. Puede cargar hasta 20 archivos a la vez. También se admiten los archivos comprimidos.  
  
7. Haga clic en **Crear**.  

8. Una vez finalizada la carga, aparecerá el mensaje de estado en la esquina superior derecha de la pantalla, que informa de que el registro se ha cargado correctamente.  
  
9. Después de cargar los archivos de registro, pasará algún tiempo hasta que se redistribuyan y se analicen.  
   Una vez completado el procesamiento de los archivos de registro, recibirá un correo electrónico que le notificará que ya está listo. 
  
10. Aparecerá un banner de notificación en la barra de estado en la parte superior del **panel de Cloud Discovery**. El banner actualiza el estado de procesamiento de los archivos de registro.  
    ![barra de menús del archivo de registro de procesamiento](./media/processing-log-file-menu-bar.png) 
   
11. Una vez cargados correctamente los registros, verá una notificación informándole de que el procesamiento de los archivos de registro se ha completado correctamente. En este punto, puede ver el informe. Para ello, haga clic en el vínculo de la barra de estado o vaya al icono de engranaje de configuración y seleccione **Cloud Discovery settings** (Configuración de Cloud Discovery).   
  
     ![Pestaña de configuración de Cloud Discovery](./media/discovery-settings-tab.png)
12. Después, seleccione **Informes de instantáneas** y elija el informe de instantáneas.
 
     ![administración de informes de instantáneas](./media/snapshot-report-managment.png)

  
## Uso de registros de tráfico para Cloud Discovery <a name="log-format"></a>
Cloud Discovery usa los datos de los registros de tráfico. Cuanto más detallado sea el registro, mejor visibilidad se logrará. Cloud Discovery requiere que los datos de tráfico de web tengan los siguientes atributos:
- Fecha de la transacción
- IP de origen
- Usuario de origen: altamente recomendado
- Dirección IP de destino
- Dirección URL de destino: **recomendado** (las direcciones URL proporcionan una mayor precisión para la detección de aplicaciones en la nube que las direcciones IP)
- Cantidad total de datos (la información de datos es muy valiosa)
- Cantidad de datos cargados o descargados (proporciona información sobre los patrones de uso de las aplicaciones en la nube)
- Acción realizada (permitido/bloqueado)

Cloud Discovery no puede mostrar ni analizar los atributos que no estén incluidos en los registros.
Por ejemplo, el formato de registro estándar del **firewall de Cisco ASA** no tiene la **cantidad de bytes cargados por transacción** ni el **nombre de usuario**, y tampoco tiene la **dirección URL de destino** (solo la IP de destino).
Por lo tanto, estos atributos no se mostrarán en los datos de Cloud Discovery de estos registros, y la visibilidad de las aplicaciones en la nube será limitada. En el caso de los firewalls de Cisco ASA, es necesario establecer el nivel de información en 6. 


Para generar correctamente un informe de Cloud Discovery, los registros de tráfico deben cumplir las condiciones siguientes:
1. Se admite el origen de datos (consulte la lista siguiente).
2. El formato de registro coincide con el formato estándar esperado (el formato se comprueba después de la carga mediante la herramienta de registro).
3. Los eventos no tienen más de 90 días.
4. El archivo de registro es válido e incluye información sobre el tráfico saliente.



## Firewalls y servidores proxy compatibles <a name="supported-firewalls-and-proxies"></a>

- Barracuda - Web App Firewall (W3C)
- Blue Coat Proxy SG - registros de acceso (W3C)
- Check Point
- Firewall de Cisco ASA (en el caso de los firewalls de Cisco ASA, es necesario establecer el nivel de información en 6)
- Cisco ASA con FirePOWER
- Cisco IronPort WSA
- Cisco ScanSafe
- Cisco Meraki – Registro de direcciones URL
- Clavister NGFW (Syslog)
- Digital Arts i-FILTER
- Fortinet Fortigate
- iboss Secure Cloud Gateway
- Juniper SRX
- Juniper SSG
- McAfee Secure Web Gateway
- Microsoft Forefront Threat Management Gateway (W3C)
- Firewalls de la serie Palo Alto
- Sonicwall (anteriormente Dell)
- Sophos SG
- Sophos XG
- Sophos Cyberoam
- Squid (Common)
- Squid (Native)
- Websense - Web Security Solutions - Investigative detail report (CSV)
- Websense - Web Security Solutions - Internet activity log (CEF)
- Zscaler

> [!NOTE]
> Cloud Discovery admite tanto direcciones IPv4 como IPv6.

Si el registro no es compatible, seleccione **Otro** como **Origen de datos** y especifique el dispositivo y el registro que está intentando cargar. El equipo de analistas de la nube de Cloud App Security examinará el registro y se le notificará si se ha agregado compatibilidad con el tipo de registro. También puede definir un analizador personalizado que coincida con el formato. Para obtener más información, vea [Uso del analizador de registros personalizado](custom-log-parser.md).


Atributos de datos (según la documentación del proveedor):


|                 Origen de datos                  |    Dirección URL de la aplicación de destino    |    IP de la aplicación de destino     |       Nombre de usuario       |      IP de origen       |    Tráfico total     |    Bytes cargados    |
|----------------------------------------------|----------------------|----------------------|----------------------|----------------------|----------------------|----------------------|
|                  Barracuda                   | <strong>Sí</strong> | <strong>Sí</strong> | <strong>Sí</strong> | <strong>Sí</strong> |          No          |          No          |
|                  Blue Coat                   | <strong>Sí</strong> |          No          | <strong>Sí</strong> | <strong>Sí</strong> | <strong>Sí</strong> | <strong>Sí</strong> |
|                  Checkpoint                  |          No          | <strong>Sí</strong> |          No          | <strong>Sí</strong> |          No          |          No          |
|              Cisco ASA (Syslog)              |          No          | <strong>Sí</strong> |          No          | <strong>Sí</strong> | <strong>Sí</strong> |          No          |
|           Cisco ASA con FirePOWER           | <strong>Sí</strong> | <strong>Sí</strong> | <strong>Sí</strong> | <strong>Sí</strong> | <strong>Sí</strong> | <strong>Sí</strong> |
|                  Cisco FWSM                  |          No          | <strong>Sí</strong> |          No          | <strong>Sí</strong> | <strong>Sí</strong> |          No          |
|              Cisco Ironport WSA              | <strong>Sí</strong> | <strong>Sí</strong> | <strong>Sí</strong> | <strong>Sí</strong> | <strong>Sí</strong> | <strong>Sí</strong> |
|                 Cisco Meraki                 | <strong>Sí</strong> | <strong>Sí</strong> |          No          | <strong>Sí</strong> |          No          |          No          |
|           Clavister NGFW (Syslog)            | <strong>Sí</strong> | <strong>Sí</strong> | <strong>Sí</strong> | <strong>Sí</strong> | <strong>Sí</strong> | <strong>Sí</strong> |
|                SonicWall (anteriormente Dell)                | <strong>Sí</strong> | <strong>Sí</strong> |          No          | <strong>Sí</strong> | <strong>Sí</strong> | <strong>Sí</strong> |
|            Digital Arts i-FILTER             | <strong>Sí</strong> | <strong>Sí</strong> | <strong>Sí</strong> | <strong>Sí</strong> | <strong>Sí</strong> | <strong>Sí</strong> |
|                  FortiGate                   |          No          | <strong>Sí</strong> |          No          | <strong>Sí</strong> | <strong>Sí</strong> | <strong>Sí</strong> |
|                 Juniper SRX                  |          No          | <strong>Sí</strong> |          No          | <strong>Sí</strong> | <strong>Sí</strong> | <strong>Sí</strong> |
|                 Juniper SSG                  |          No          | <strong>Sí</strong> | <strong>Sí</strong> | <strong>Sí</strong> | <strong>Sí</strong> | <strong>Sí</strong> |
|                  McAfee SWG                  | <strong>Sí</strong> |          No          |          No          | <strong>Sí</strong> | <strong>Sí</strong> | <strong>Sí</strong> |
|                    MS TMG                    | <strong>Sí</strong> |          No          | <strong>Sí</strong> | <strong>Sí</strong> | <strong>Sí</strong> | <strong>Sí</strong> |
|              Palo Alto Networks              |          No          | <strong>Sí</strong> | <strong>Sí</strong> | <strong>Sí</strong> | <strong>Sí</strong> | <strong>Sí</strong> |
|                    Sophos                    | <strong>Sí</strong> | <strong>Sí</strong> | <strong>Sí</strong> | <strong>Sí</strong> | <strong>Sí</strong> |          No          |
|                Squid (Common)                | <strong>Sí</strong> |          No          | <strong>Sí</strong> | <strong>Sí</strong> |          No          | <strong>Sí</strong> |
|                Squid (Native)                | <strong>Sí</strong> |          No          | <strong>Sí</strong> | <strong>Sí</strong> |          No          | <strong>Sí</strong> |
| Websense: informe de detalle de investigación (CSV) | <strong>Sí</strong> | <strong>Sí</strong> | <strong>Sí</strong> | <strong>Sí</strong> | <strong>Sí</strong> | <strong>Sí</strong> |
|    Websense: registro de actividad de Internet (CEF)    | <strong>Sí</strong> | <strong>Sí</strong> | <strong>Sí</strong> | <strong>Sí</strong> | <strong>Sí</strong> | <strong>Sí</strong> |
|                   Zscaler                    | <strong>Sí</strong> | <strong>Sí</strong> | <strong>Sí</strong> | <strong>Sí</strong> | <strong>Sí</strong> | <strong>Sí</strong> |
     
 
## <a name="next-steps"></a>Pasos siguientes  
[Controlar las aplicaciones en la nube con directivas](control-cloud-apps-with-policies.md)   

[Los clientes Premier también pueden crear una solicitud de soporte técnico directamente en el portal Premier.](https://premier.microsoft.com/)  
    
      
  