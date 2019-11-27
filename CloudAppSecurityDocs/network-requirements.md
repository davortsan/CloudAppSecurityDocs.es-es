---
title: 'Requisitos de red: Cloud App Security | Microsoft Docs'
description: En este artículo se describen las direcciones IP y los puertos que debe abrir para trabajar con Cloud App Security.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 11/01/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 4de606f2-a09e-4e48-a578-e223de8b5e69
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 866aef6b1dd6d01ce6708cab4b723b6868f979e1
ms.sourcegitcommit: 094bb42a198fe733cfd3aec79d74487672846dfa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/24/2019
ms.locfileid: "74460681"
---
# <a name="network-requirements"></a>Requisitos de red

*Se aplica a: Microsoft Cloud App Security*

En este artículo se proporciona una lista de puertos y direcciones IP que es necesario permitir y permitir que la lista funcione con Microsoft Cloud App Security.

## <a name="view-your-data-center"></a>Consultar el centro de datos

Algunos de los siguientes requisitos dependen del centro de datos al que esté conectado.

Para ver el centro de datos al que se está conectando, siga estos pasos:

1. En el portal de Cloud App Security, haga clic en el **icono de signo de interrogación** en la barra de menús. Después, seleccione **Acerca de**.

    ![clic en Acerca de](./media/about-menu.png)

2. En la pantalla de versión de Cloud App Security, podrá ver la región y el centro de datos.

    ![Consultar el centro de datos](./media/data-center.png)

## <a name="portal-access"></a>Acceso al portal

Para acceder al portal de Cloud App Security, agregue el **Puerto de salida 443** para las siguientes direcciones IP y nombres DNS a la lista de permitidos del firewall:

    portal.cloudappsecurity.com
    *.portal.cloudappsecurity.com
    cdn.cloudappsecurity.com
    https://adaproddiscovery.azureedge.net
    *.s-microsoft.com
    *.msecnd.net
    dev.virtualearth.net
    *.cloudappsecurity.com
    flow.microsoft.com
    static2.sharepointonline.com
    dc.services.visualstudio.com
    *.blob.core.windows.net

En el caso de los clientes de la administración pública de Estados Unidos, también es necesario agregar los siguientes nombres DNS a la lista de permitidos del firewall para proporcionar acceso al portal de Cloud App Security GCC High:

    portal.cloudappsecurity.us
    *.portal.cloudappsecurity.us
    cdn.cloudappsecurity.com

Además, estos elementos deben estar en una lista blanca, según el centro de datos que use:
> [!div class="mx-tableFixed"]
>
> |Centro de datos|Direcciones IP|Nombre DNS|
> |----|----|----|
> |Estados Unidos 1|13.64.26.88<br>13.64.29.32<br>13.80.125.22<br>13.91.91.243<br>40.74.1.235<br>40.74.6.204<br>51.143.58.207<br>52.137.89.147<br>52.183.75.62|\*.us.portal.cloudappsecurity.com|
> |US2|13.80.125.22<br>20.36.222.59<br>20.36.222.60<br>40.74.1.235<br>40.74.6.204<br>51.143.58.207<br>52.137.89.147<br>52.183.75.62<br>52.184.165.82|\*.us2.portal.cloudappsecurity.com|
> |US3|13.80.125.22<br>40.74.1.235<br>40.74.6.204<br>40.90.218.196<br>40.90.218.198<br>51.143.58.207<br>52.137.89.147<br>52.183.75.62|*.us3.portal.cloudappsecurity.com|
> |Unión Europea 1|13.80.125.22<br>40.119.154.72<br>40.74.1.235<br>40.74.6.204<br>51.143.58.207<br>52.137.89.147<br>52.157.238.58<br>52.174.56.180<br>52.183.75.62|\*.eu.portal.cloudappsecurity.com<|
> |EU2|13.80.125.22<br>40.74.1.235<br>40.74.6.204<br>40.81.156.154<br>40.81.156.156<br>51.143.58.207<br>52.137.89.147<br>52.183.75.62|*.eu2.portal.cloudappsecurity.com|
> |Estados Unidos 1 gov|13.72.19.4<br>52.227.143.223|*. us1.portal.cloudappsecurity.us|

> [!NOTE]
> En lugar de un carácter comodín (\*), puede abrir solo la dirección URL del inquilino específico, por ejemplo, de acuerdo con la captura de pantalla anterior, puede abrir: mod244533.us.portal.cloudappsecurity.com

## <a name="access-and-session-controls"></a>Controles de acceso y de sesión

Para habilitar Cloud App Security proxy inverso, agregue el **Puerto de salida 443** para las siguientes direcciones IP y nombres DNS a la lista de permitidos del firewall:

    *.cas.ms

Además, estos elementos deben estar en una lista blanca, según el centro de datos que use:

> [!div class="mx-tableFixed"]
>
> |Centro de datos|Direcciones IP|||Nombre DNS|
> |----|----|----|----|----|
> |Estados Unidos 1|40.81.63.1<br>40.81.63.4<br>52.142.112.145<br>52.142.116.135<br>51.105.163.8<br>51.105.163.43<br>40.66.60.118<br>40.66.60.200<br>40.65.169.97<br>40.65.169.236<br>40.81.121.111<br>40.81.120.187<br>40.91.114.46<br>40.91.114.47<br>40.81.63.5<br>40.81.63.2<br>20.40.163.133<br>20.40.163.97<br>52.142.116.174<br>52.142.117.183<br>52.142.121.75<br>52.142.121.6<br>51.105.166.102<br>51.105.165.116|51.105.165.37<br>51.105.165.31<br>40.66.60.207<br>40.66.60.208<br>40.66.62.78<br>20.40.134.94<br>40.65.169.46<br>40.65.169.196<br>52.148.116.37<br>52.148.115.238<br>40.81.127.140<br>40.81.121.107<br>51.137.136.14<br>51.137.136.13<br>40.91.114.49<br>40.91.114.44<br>51.143.111.58<br>40.91.127.44<br>40.81.63.8<br>40.81.62.255<br>52.142.112.146<br>52.142.116.250<br>51.105.166.103<br>51.105.164.8|40.66.60.180<br>40.66.60.206<br>40.119.215.167<br>40.65.170.17<br>40.81.121.127<br>40.81.121.108<br>40.91.114.48<br>40.91.114.45<br>20.40.161.119<br>20.40.161.135<br>52.156.197.254<br>52.156.198.196<br>51.105.166.106<br>51.105.165.63<br>40.66.60.185<br>40.66.59.41<br>20.184.63.216<br>20.184.63.232<br>40.81.122.76<br>40.81.123.124<br>40.90.220.37<br>40.91.126.157|\*. us1.cas.ms<br>\*. us1.access-control.cas.ms<br>\*. us1.saml.cas.ms|
> |US2|40.81.63.7<br>40.81.59.90<br>40.67.251.0<br>52.156.206.47<br>40.66.60.209<br>40.66.60.216<br>40.65.170.137<br>40.65.170.26<br>40.81.127.139<br>40.81.127.25<br>104.45.170.184<br>104.45.170.185<br>40.81.58.184<br>40.81.58.180<br>20.40.163.96<br>20.40.163.88<br>52.156.205.222<br>52.156.204.99<br>52.155.166.50<br>52.142.127.127|40.66.60.219<br>40.66.60.215<br>40.66.63.148<br>20.40.132.195<br>40.65.170.125<br>40.65.170.123<br>52.139.245.40<br>52.139.245.48<br>40.81.121.140<br>40.81.121.135<br>51.137.137.121<br>51.137.137.118<br>104.45.170.196<br>104.45.170.182<br>52.151.238.5<br>52.151.237.243<br>40.81.58.193<br>40.81.59.93<br>52.156.197.208<br>52.156.206.46|40.66.60.210<br>40.66.60.217<br>40.65.170.128<br>40.65.170.133<br>40.81.127.230<br>40.81.127.141<br>104.45.170.188<br>104.45.170.194<br>20.40.161.141<br>20.40.161.140<br>52.156.205.226<br>52.156.206.45<br>40.66.62.130<br>40.66.56.158<br>40.119.207.131<br>40.119.207.144<br>40.81.124.185<br>40.81.122.62<br>52.191.238.65<br>52.191.237.188|\*. us2.cas.ms<br>\*. us2.access-control.cas.ms<br>\*. us2.saml.cas.ms|
> |US3|40.81.62.224<br>40.81.62.220<br>40.82.186.168<br>40.82.186.169<br>52.155.180.210<br>52.155.179.84<br>40.66.59.196<br>40.66.60.224<br>40.65.170.80<br>40.65.170.83<br>40.81.127.229<br>40.81.121.66<br>104.45.170.191<br>104.45.170.183<br>40.91.114.40<br>40.91.114.42<br>40.81.62.179<br>40.81.62.223<br>20.40.162.86<br>20.40.162.200<br>40.82.186.182<br>40.82.186.177<br>52.139.21.70<br>52.139.16.105<br>52.155.177.13<br>52.155.180.208<br>52.155.164.131|52.155.167.231<br>40.66.60.226<br>40.66.59.193<br>40.66.61.193<br>40.66.61.158<br>40.65.170.113<br>40.65.170.82<br>52.139.245.1<br>52.139.245.21<br>40.81.120.192<br>40.81.127.239<br>51.137.136.34<br>51.137.137.69<br>104.45.170.70<br>104.45.170.180<br>52.224.190.225<br>52.224.191.62<br>40.91.114.41<br>40.91.78.105<br>52.148.161.45<br>52.148.161.53<br>40.81.62.193<br>40.81.62.162<br>40.82.186.166<br>40.82.186.176<br>52.155.180.209<br>52.155.178.247|40.66.59.246<br>40.66.59.195<br>40.65.170.81<br>40.65.170.112<br>40.81.120.191<br>40.81.123.157<br>104.45.170.186<br>104.45.170.178<br>40.91.114.43<br>40.91.74.37<br>20.40.161.160<br>20.40.161.161<br>52.139.2.0<br>52.139.1.156<br>52.155.180.211<br>52.155.182.138<br>40.66.62.7<br>40.66.62.9<br>20.184.63.158<br>20.184.61.253<br>20.40.106.51<br>20.40.107.84<br>52.224.202.86<br>52.224.202.91<br>51.143.122.59<br>51.143.122.60|\*. us3.cas.ms<br>\*. us3.access-control.cas.ms<br>\*. us3.saml.cas.ms|
> |Unión Europea 1|40.81.57.138<br>40.81.57.157<br>52.156.204.139<br>52.156.205.182<br>52.157.232.147<br>52.157.235.144<br>40.119.207.200<br>40.119.207.174<br>40.81.120.13<br>40.81.120.25<br>104.45.168.114<br>104.45.168.103<br>40.80.222.197<br>40.80.220.215<br>40.81.57.169<br>40.81.57.144<br>20.40.163.178<br>20.40.163.179<br>52.156.204.24<br>52.156.204.51<br>52.155.161.88<br>52.155.161.91<br>52.157.233.205<br>52.157.234.160|51.145.181.214<br>51.145.181.195<br>40.119.207.193<br>40.119.207.164<br>52.148.115.188<br>52.148.115.194<br>40.81.121.78<br>40.81.122.203<br>51.137.137.237<br>51.137.137.200<br>104.45.168.106<br>104.45.168.104<br>52.151.247.27<br>52.151.244.65<br>40.80.219.49<br>40.80.222.91<br>52.153.240.107<br>20.188.72.248<br>40.81.57.164<br>40.81.57.141<br>52.156.203.22<br>52.156.205.137<br>52.157.237.213<br>52.157.237.107|40.119.207.182<br>40.119.207.166<br>40.81.121.76<br>40.81.120.24<br>104.45.168.111<br>104.45.168.108<br>40.80.220.246<br>40.80.221.77<br>20.40.161.132<br>20.40.161.131<br>52.156.203.199<br>40.67.254.233<br>52.157.218.232<br>52.157.218.219<br>52.139.251.219<br>52.139.252.105<br>40.81.122.63<br>20.40.106.50<br>52.224.201.216<br>52.224.201.223<br>52.249.25.165<br>52.249.25.160|\*. eu1.cas.ms<br>\*. eu1.access-control.cas.ms<br>\*. eu1.saml.cas.ms|
> |EU2|40.81.62.222<br>40.81.62.212<br>52.155.182.49<br>52.155.181.181<br>52.157.234.222<br>52.157.236.195<br>40.66.60.221<br>40.66.60.101<br>40.119.203.98<br>40.119.203.208<br>104.45.170.174<br>104.45.170.127<br>40.81.62.221<br>40.81.62.206<br>20.40.160.184<br>20.40.163.130<br>52.155.181.183<br>52.155.168.45<br>52.156.202.7<br>52.142.124.23|52.157.233.49<br>52.157.235.27<br>51.105.164.234<br>51.105.164.241<br>40.66.60.232<br>40.66.60.222<br>20.40.134.79<br>40.66.57.203<br>40.119.203.158<br>40.119.203.209<br>20.184.61.67<br>20.184.60.77<br>104.45.170.173<br>104.45.170.176<br>52.224.188.157<br>52.224.188.168<br>40.81.62.209<br>40.81.62.199<br>52.155.181.180<br>52.155.182.50|52.157.237.255<br>52.157.239.132<br>40.66.60.225<br>40.66.60.220<br>40.119.203.159<br>40.119.203.99<br>104.45.170.161<br>104.45.170.175<br>20.40.161.142<br>20.40.161.143<br>52.155.181.182<br>52.155.182.48<br>40.119.145.130<br>40.119.147.102<br>40.66.62.154<br>40.66.62.225<br>20.184.58.46<br>40.90.191.153<br>52.190.31.62<br>52.190.26.220|\*. eu2.cas.ms<br>\*. eu2.access-control.cas.ms<br>\*. eu2.saml.cas.ms|

## <a name="siem-agent-connection"></a>Conexión del agente SIEM

Para habilitar Cloud App Security para conectarse a su SIEM, agregue el **Puerto de salida 443** para las siguientes direcciones IP a la lista de permitidos del firewall:

> [!div class="mx-tableFixed"]
>
> |Centro de datos|Direcciones IP|
> |----|----|
> |Estados Unidos 1|13.64.26.88<br>13.64.29.32<br>13.80.125.22<br>13.91.91.243<br>40.74.1.235<br>40.74.6.204<br>51.143.58.207<br>52.137.89.147<br>52.183.75.62|
> |US2|13.80.125.22<br>20.36.222.59<br>20.36.222.60<br>40.74.1.235<br>40.74.6.204<br>51.143.58.207<br>52.137.89.147<br>52.183.75.62<br>52.184.165.82|
> |US3|13.80.125.22<br>40.74.1.235<br>40.74.6.204<br>40.90.218.196<br>40.90.218.198<br>51.143.58.207<br>52.137.89.147<br>52.183.75.62|
> |Unión Europea 1|13.80.125.22<br>40.119.154.72<br>40.74.1.235<br>40.74.6.204<br>51.143.58.207<br>52.137.89.147<br>52.157.238.58<br>52.174.56.180<br>52.183.75.62|
> |EU2|13.80.125.22<br>40.74.1.235<br>40.74.6.204<br>40.81.156.154<br>40.81.156.156<br>51.143.58.207<br>52.137.89.147<br>52.183.75.62|
> |Estados Unidos 1 gov|13.72.19.4<br>52.227.143.223|

> [!NOTE]
> Si no especificó un proxy al configurar el agente de SIEM de Cloud App Security, debe permitir que las conexiones http http://ocsp.msocsp.com/ y ocsp.digicert.com en el puerto 80. Esto sirve para comprobar el estado de revocación de certificado al conectarse al portal de Cloud App Security.

## <a name="app-connector"></a>Conector de la aplicación

Se pueden usar estas direcciones IP para que Cloud App Security pueda acceder a algunas aplicaciones de terceros. Las direcciones IP permiten a Cloud App Security recopilar registros y proporcionan acceso a la consola de Cloud App Security.

> [!NOTE]
>Puede que vea estas direcciones IP en los registros de actividad del proveedor, ya que Cloud App Security realiza acciones de gobernanza y exámenes desde ellas.

Para conectarse a aplicaciones de terceros, habilite Cloud App Security para permitir la conexión desde estas direcciones IP:

> [!div class="mx-tableFixed"]
>
> |Centro de datos|Direcciones IP||
> |----|----|----|
> |Estados Unidos 1|13.64.196.27<br>13.64.198.19<br>13.64.198.97<br>13.64.199.41<br>13.64.26.88<br>13.64.29.32<br>13.64.30.117<br>13.64.30.118<br>13.64.30.76<br>13.64.31.116<br>13.68.76.47|13.86.176.189<br>13.86.176.211<br>13.91.61.249<br>13.91.91.243<br>13.91.98.185<br>13.93.216.68<br>13.93.233.42<br>40.118.211.172<br>104.42.54.148<br>104.209.35.177<br><br>|
> |US2|13.68.76.47<br>20.36.222.59<br>20.36.222.60<br>40.67.152.91<br>40.67.154.160<br>40.67.155.146<br>40.67.159.55<br>40.84.2.83<br>40.84.4.119<br>40.84.4.93|52.184.165.82<br>52.232.224.227<br>52.232.225.84<br>104.46.116.211<br>104.46.116.211<br>104.46.121.72<br>104.46.121.72<br>104.46.122.189<br>104.42.54.148<br>104.46.122.189<br>|
> |US3|13.68.76.47<br>40.90.218.196<br>40.90.218.197<br>40.90.218.198<br>40.90.218.203<br>40.90.220.190<br>40.90.220.196<br>51.143.120.236<br>51.143.120.242<br>104.42.54.148||
> |Unión Europea 1|13.80.22.71<br>13.95.29.177<br>13.95.30.46<br>40.114.217.8<br>40.114.217.8<br>40.115.24.65<br>40.115.24.65<br>40.115.25.50<br>40.115.25.50<br>40.119.154.72|40.67.219.133<br>51.105.55.62<br>51.105.179.157<br>51.137.200.32<br>52.157.232.110<br>52.157.233.133<br>52.157.233.92<br>52.157.238.58<br>52.157.239.110<br>52.174.56.180|
> |EU2|40.81.152.171<br>40.81.152.172<br>40.81.156.153<br>40.81.156.154<br>40.81.156.155<br>40.81.156.156<br>51.105.55.62<br>51.137.200.32<br>51.145.108.227<br>51.145.108.250|
> |Estados Unidos 1 gov|52.227.138.248<br>52.227.142.192<br>52.227.143.223|

## <a name="third-party-dlp-integration"></a>Integración de DLP de terceros

Para permitir que Cloud App Security envíe datos a través de Stunnel al servidor ICAP, abra el firewall de red perimetral a estas direcciones IP con un número de puerto de origen dinámico.

1. **Direcciones de origen**: estas direcciones deben incluirse en la lista de admitidas como se detalla anteriormente para las aplicaciones de conector de la API de terceros
2. **Puerto TCP de origen**: dinámico
3. **Direcciones de destino**: una o dos direcciones IP del servidor Stunnel conectado al servidor ICAP externo
4. **Puerto TCP de destino**: según se defina en la red

> [!NOTE]
> - El número de puerto de Stunnel está establecido de forma predeterminada en 11344. Si es necesario, puede cambiarlo y usar otro, pero no olvide anotar el número de puerto nuevo.
> - Puede que vea estas direcciones IP en los registros de actividad del proveedor, ya que Cloud App Security realiza acciones de gobernanza y exámenes desde ellas.

Para conectar aplicaciones de terceros e integrar soluciones de DLP externas, habilite la conexión de Cloud App Security desde estas direcciones IP:

> [!div class="mx-tableFixed"]
>
> |Centro de datos|Direcciones IP||
> |----|----|----|
> |Estados Unidos 1|13.64.196.27<br>13.64.198.19<br>13.64.198.97<br>13.64.199.41<br>13.64.26.88<br>13.64.29.32<br>13.64.30.117<br>13.64.30.118<br>13.64.30.76<br>13.64.31.116|13.86.176.189<br>13.86.176.211<br>13.91.61.249<br>13.91.91.243<br>13.91.98.185<br>13.93.216.68<br>13.93.233.42<br>40.118.211.172<br>104.209.35.177<br><br>|
> |US2|20.36.222.59<br>20.36.222.60<br>40.67.152.91<br>40.67.154.160<br>40.67.155.146<br>40.67.159.55<br>40.84.2.83<br>40.84.4.119<br>40.84.4.93|52.184.165.82<br>52.232.224.227<br>52.232.225.84<br>104.46.116.211<br>104.46.116.211<br>104.46.121.72<br>104.46.121.72<br>104.46.122.189<br>104.46.122.189|
> |US3|40.90.218.196<br>40.90.218.197<br>40.90.218.198<br>40.90.218.203<br>40.90.220.190<br>40.90.220.196<br>51.143.120.236<br>51.143.120.242||
> |Unión Europea 1|13.80.22.71<br>13.95.29.177<br>13.95.30.46<br>40.67.219.133<br>40.114.217.8<br>40.114.217.8<br>40.115.24.65<br>40.115.24.65<br>40.115.25.50|40.119.154.72<br>51.105.179.157<br>52.157.232.110<br>52.157.233.133<br>52.157.233.92<br>52.157.238.58<br>52.157.239.110<br>52.174.56.180<br><br>|
> |EU2|40.81.152.171<br>40.81.152.172<br>40.81.156.153<br>40.81.156.154<br>40.81.156.155<br>40.81.156.156<br>51.145.108.227<br>51.145.108.250||

## <a name="mail-server"></a>Servidor de correo

Para habilitar las notificaciones para que se envíen desde la plantilla y la configuración predeterminadas, agregue estas direcciones IP a la lista de permitidos de anti-spam. Las direcciones IP de correo electrónico dedicadas de Cloud App Security son:

- 65.55.234.192/26
- 207.46.200.0/27
- 65.55.52.224/27
- 94.245.112.0/27
- 111.221.26.0/27
- 207.46.50.192/26

Si quiere personalizar la identidad del remitente de correo electrónico, Microsoft Cloud App Security permite la personalización mediante MailChimp®, un servicio de correo electrónico de terceros. Para facilitar el trabajo en el portal de Microsoft Cloud App Security, vaya a **Configuración**. Seleccione **Configuración de correo** y revise la declaración de privacidad y los términos de servicio de MailChimp. Después, conceda permiso a Microsoft para usar MailChimp en su nombre.

Si no personaliza la identidad del remitente, las notificaciones de correo electrónico se enviarán con todos los valores predeterminados.

Para trabajar con MailChimp, agregue esta dirección IP a la lista de permitidos de bloqueo de correo no deseado para permitir el envío de notificaciones: 198.2.134.139 (mail1.cloudappsecurity.com)

## <a name="log-collector"></a>Recopilador de registros

Para habilitar características de Cloud Discovery por medio de un recopilador de registros y detectar Shadow TI en la organización, abra los siguientes elementos:

- Permita que el recopilador de registros reciba tráfico entrante de FTP y Syslog.
- Permita que el recopilador de registros inicie tráfico saliente al portal (por ejemplo, contoso.cloudappsecurity.com) en el puerto 443.
- Permita que el recopilador de registros inicie tráfico saliente a Azure Blog Storage en el puerto 443:

  | Centro de datos |                        Dirección URL                                 |
  |-------------|------------------------------------------------------------|
  |     Estados Unidos 1     | https:\//adaprodconsole.blob.core.windows.net/             |
  |     US2     | https:\//prod03use2console1.blob.core.windows.net/         |
  |     US3     | https:\//prod5usw2console1.blob.core.windows.net/          |
  |     Unión Europea 1     | https:\//prod02euwconsole1.blob.core.windows.net/          |
  |     EU2     | https:\//prod4uksconsole1.blob.core.windows.net/           |
  |   Estados Unidos 1 gov   | https:\//gprd1usgvconsole1.blob.core.usgovcloudapi.net/    |

> [!NOTE]
> - Si el firewall requiere una lista de acceso de dirección IP estática y no admite la creación de listas de permitidos basadas en direcciones URL, permita que el recopilador de registros enrute el tráfico saliente hacia los [intervalos IP del centro de datos de Microsoft Azure](https://www.microsoft.com/download/details.aspx?id=41653) a través del puerto 443.
>- Permita que el recopilador de registros inicie tráfico saliente al portal de Cloud App Security.
>- Si no especificó un proxy al configurar el recopilador de registros, debe permitir que las conexiones http http://ocsp.msocsp.com/ y ocsp.digicert.com en el puerto 80. Esto sirve para comprobar el estado de revocación de certificado al conectarse al portal de Cloud App Security.

## <a name="next-steps"></a>Pasos siguientes

[Actividades diarias para proteger el entorno de nube](daily-activities-to-protect-your-cloud-environment.md)

[!INCLUDE [Open support ticket](includes/support.md)]
