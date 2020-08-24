---
title: 'Requisitos de red: Cloud App Security'
description: En este artículo se describen las direcciones IP y los puertos que debe abrir para trabajar con Cloud App Security.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 11/01/2019
ms.topic: how-to
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: ffc479ee603ddc6e38b7ba0167fff6f20d9decad
ms.sourcegitcommit: 29a8e66c665f51d831516924ae4d9d8047b39276
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2020
ms.locfileid: "88779481"
---
# <a name="network-requirements"></a>Requisitos de red

*Se aplica a: Microsoft Cloud App Security*

En este artículo se proporciona una lista de puertos y direcciones IP que es necesario permitir y permitir que la lista funcione con Microsoft Cloud App Security.

## <a name="view-your-data-center"></a>Consultar el centro de datos

Algunos de los siguientes requisitos dependen del centro de datos al que esté conectado.

Para ver el centro de datos al que se está conectando, siga estos pasos:

1. En el portal de Cloud App Security, haga clic en el **icono de signo de interrogación** en la barra de menús. Después, seleccione **Acerca de**.

    ![clic en Acerca de](media/about-menu.png)

2. En la pantalla de versión de Cloud App Security, podrá ver la región y el centro de datos.

    ![Consultar el centro de datos](media/data-center.png)

## <a name="portal-access"></a>Acceso al portal

Para acceder al portal de Cloud App Security, agregue el **Puerto de salida 443** para las siguientes direcciones IP y nombres DNS a la lista de permitidos del firewall:

```ini
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
```

En el caso de los clientes de la administración pública de Estados Unidos, también es necesario agregar los siguientes nombres DNS a la lista de permitidos del firewall para proporcionar acceso al portal de Cloud App Security GCC High:

```ini
    portal.cloudappsecurity.us
    *.portal.cloudappsecurity.us
    cdn.cloudappsecurity.com
```

Además, estos elementos deben estar en una lista blanca, según el centro de datos que use:

|Centro de datos|Direcciones IP|Nombre DNS|
|----|----|----|
|Estados Unidos 1|13.64.26.88, 13.64.29.32, 13.80.125.22, 13.91.91.243, 40.74.1.235, 40.74.6.204, 51.143.58.207, 52.137.89.147, 52.183.75.62|\*.us.portal.cloudappsecurity.com|
|US2|13.80.125.22, 20.36.222.59, 20.36.222.60, 40.74.1.235, 40.74.6.204, 51.143.58.207, 52.137.89.147, 52.183.75.62, 52.184.165.82|\*.us2.portal.cloudappsecurity.com|
|US3|13.80.125.22, 40.74.1.235, 40.74.6.204, 40.90.218.196, 40.90.218.198, 51.143.58.207, 52.137.89.147, 52.183.75.62|*.us3.portal.cloudappsecurity.com|
|Unión Europea 1|13.80.125.22, 40.74.1.235, 40.74.6.204, 40.119.154.72, 51.143.58.207, 52.137.89.147, 52.157.238.58, 52.174.56.180, 52.183.75.62|\*.eu.portal.cloudappsecurity.com<|
|EU2|13.80.125.22, 40.74.1.235, 40.74.6.204, 40.81.156.154, 40.81.156.156, 51.143.58.207, 52.137.89.147, 52.183.75.62|*.eu2.portal.cloudappsecurity.com|
|Estados Unidos 1 gov|13.72.19.4, 52.227.143.223|*. us1.portal.cloudappsecurity.us|

> [!NOTE]
> En lugar de un carácter comodín (\*), puede abrir solo la dirección URL del inquilino específico, por ejemplo, de acuerdo con la captura de pantalla anterior, puede abrir: mod244533.us.portal.cloudappsecurity.com

## <a name="access-and-session-controls"></a>Controles de acceso y de sesión

Configure el firewall para el proxy inverso con los valores relevantes para su entorno.

### <a name="commercial-customers"></a>Clientes comerciales

En el caso de los clientes comerciales, para habilitar Cloud App Security proxy inverso, agregue el **Puerto de salida 443** para las siguientes direcciones IP y nombres DNS a la lista de permitidos del firewall:

```ini
    *.cas.ms
    *.mcas.ms
    *.admin-mcas.ms
    mcasproxy.azureedge.net
```

Además, estos elementos deben estar en una lista blanca, según el centro de datos que use:

|Centro de datos|Direcciones IP|Nombre DNS|
|----|----|----|----|----|
|Estados Unidos 1|20.40.134.94, 20.40.161.119, 20.40.161.135, 20.40.163.97, 20.40.163.133, 20.184.63.216, 20.184.63.232, 40.65.169.46, 40.65.169.97, 40.65.169.196, 40.65.169.236, 40.65.170.17, 40.66.59.41, 40.66.60.118, 40.66.60.180, 40.66.60.185, 40.66.60.200, 40.66.60.206, 40.66.60.207, 40.66.60.208, 40.66.62.78, 40.81.62.255, 40.81.63.1, 40.81.63.2, 40.81.63.4, 40.81.63.5, 40.81.63.8, 40.81.120.187, 40.81.121.107, 40.81.121.108, 40.81.121.111, 40.81.121.127, 40.81.122.76, 40.81.123.124, 40.81.127.140, 40.81.227.134, 40.81.227.152, 40.81.227.160, 40.81.227.163, 40.90.220.37, 40.91.114.44, 40.91.114.45, 40.91.114.46, 40.91.114.47, 40.91.114.48, 40.91.114.49, 40.91.126.157, 40.91.127.44, 40.119.215.167, 51.105.163.8, 51.105.163.43, 51.105.164.8, 51.105.165.31, 51.105.165.37, 51.105.165.63, 51.105.165.116, 51.105.166.102, 51.105.166.103, 51.105.166.106, 51.137.136.13, 51.137.136.14, 51.143.111.58, 52.142.112.145, 52.142.112.146, 52.142.116.135, 52.142.116.174, 52.142.116.250, 52.142.117.183, 52.142.121.6, 52.142.121.75, 52.148.115.238, 52.148.116.37, 52.156.197.254, 52.156.198.196|\*. us.cas.ms, \* . us.Access-Control.CAS.ms, \* . us.SAML.CAS.ms|
|US2|20.40.132.195, 20.40.161.140, 20.40.161.141, 20.40.163.88, 20.40.163.96, 40.65.170.26, 40.65.170.123, 40.65.170.125, 40.65.170.128, 40.65.170.133, 40.65.170.137, 40.66.56.158, 40.66.60.209, 40.66.60.210, 40.66.60.215, 40.66.60.216, 40.66.60.217, 40.66.60.219, 40.66.62.130, 40.66.63.148, 40.67.251.0, 40.81.58.180, 40.81.58.184, 40.81.58.193, 40.81.59.90, 40.81.59.93, 40.81.63.7, 40.81.121.135, 40.81.121.140, 40.81.122.62, 40.81.124.185, 40.81.127.25, 40.81.127.139, 40.81.127.141, 40.81.127.230, 40.119.207.131, 40.119.207.144, 51.137.137.118, 51.137.137.121, 52.139.245.40, 52.139.245.48, 52.142.127.127, 52.149.59.151, 52.149.60.12, 52.149.61.128, 52.149.61.214, 52.149.63.211, 52.151.237.243, 52.151.238.5, 52.155.166.50, 52.156.88.69, 52.156.88.173, 52.156.89.175, 52.156.89.188, 52.156.90.38, 52.156.197.208, 52.156.204.99, 52.156.205.222, 52.156.205.226, 52.156.206.45, 52.156.206.46, 52.156.206.47, 52.191.237.188, 52.191.238.65, 104.45.170.182, 104.45.170.184, 104.45.170.185, 104.45.170.188, 104.45.170.194, 104.45.170.196, 191.235.117.31, 191.235.119.253, 191.235.120.17, 191.235.121.69, 191.235.121.164, 191.235.122.60, 191.235.122.101, 191.235.122.224, 191.235.123.114, 191.235.123.242|\*. us2.cas.ms, \* . US2.Access-Control.CAS.ms, \* . US2.SAML.CAS.ms|
|US3|20.40.106.51, 20.40.107.84, 20.40.161.160, 20.40.161.161, 20.40.162.86, 20.40.162.200, 20.184.61.253, 20.184.63.158, 40.65.170.80, 40.65.170.81, 40.65.170.82, 40.65.170.83, 40.65.170.112, 40.65.170.113, 40.66.59.193, 40.66.59.195, 40.66.59.196, 40.66.59.246, 40.66.60.224, 40.66.60.226, 40.66.61.158, 40.66.61.193, 40.66.62.7, 40.66.62.9, 40.81.62.162, 40.81.62.179, 40.81.62.193, 40.81.62.220, 40.81.62.223, 40.81.62.224, 40.81.120.191, 40.81.120.192, 40.81.121.66, 40.81.123.157, 40.81.127.229, 40.81.127.239, 40.82.186.166, 40.82.186.168, 40.82.186.168, 40.82.186.169, 40.82.186.169, 40.82.186.176, 40.82.186.177, 40.82.186.177, 40.82.186.182, 40.82.186.182, 40.91.74.37, 40.91.78.105, 40.91.114.40, 40.91.114.41, 40.91.114.42, 40.91.114.43, 51.137.136.34, 51.137.137.69, 51.143.122.59, 51.143.122.60, 52.139.1.156, 52.139.1.156, 52.139.2.0, 52.139.2.0, 52.139.9.176, 52.139.9.198, 52.139.16.105, 52.139.16.105, 52.139.21.70, 52.139.21.70, 52.139.245.1, 52.139.245.21, 52.148.161.45, 52.148.161.53, 52.155.164.131, 52.155.167.231, 52.155.177.13, 52.155.178.247, 52.155.179.84, 52.155.180.208, 52.155.180.209, 52.155.180.210, 52.155.180.211, 52.155.182.138, 52.224.190.225, 52.224.191.62, 52.224.202.86, 52.224.202.91, 104.45.170.70, 104.45.170.178, 104.45.170.180, 104.45.170.183, 104.45.170.186, 104.45.170.191|\*. us3.cas.ms, \* . US3.Access-Control.CAS.ms, \* . US3.SAML.CAS.ms|
|Unión Europea 1|20.40.106.50, 20.40.161.131, 20.40.161.132, 20.40.163.178, 20.40.163.179, 20.188.72.248, 40.67.254.233, 40.80.219.49, 40.80.220.215, 40.80.220.246, 40.80.221.77, 40.80.222.91, 40.80.222.197, 40.81.57.138, 40.81.57.141, 40.81.57.144, 40.81.57.157, 40.81.57.164, 40.81.57.169, 40.81.120.13, 40.81.120.24, 40.81.120.25, 40.81.121.76, 40.81.121.78, 40.81.122.63, 40.81.122.203, 40.119.207.164, 40.119.207.166, 40.119.207.174, 40.119.207.182, 40.119.207.193, 40.119.207.200, 51.137.137.200, 51.137.137.237, 51.145.181.195, 51.145.181.214, 52.139.251.219, 52.139.252.105, 52.148.115.188, 52.148.115.194, 52.151.244.65, 52.151.247.27, 52.153.240.107, 52.155.161.88, 52.155.161.91, 52.156.203.22, 52.156.203.199, 52.156.204.24, 52.156.204.51, 52.156.204.139, 52.156.205.137, 52.156.205.182, 52.157.218.219, 52.157.218.232, 52.157.232.147, 52.157.233.205, 52.157.234.160, 52.157.235.144, 52.157.237.107, 52.157.237.213, 52.224.201.216, 52.224.201.223, 52.249.25.160, 52.249.25.165, 104.45.168.103, 104.45.168.104, 104.45.168.106, 104.45.168.108, 104.45.168.111, 104.45.168.114|\*. eu1.cas.ms, \* . EU1.Access-Control.CAS.ms, \* . EU1.SAML.CAS.ms|
|EU2|20.40.134.79, 20.40.160.184, 20.40.161.142, 20.40.161.143, 20.40.163.130, 20.184.58.46, 20.184.60.77, 20.184.61.67, 40.66.57.203, 40.66.60.101, 40.66.60.220, 40.66.60.221, 40.66.60.222, 40.66.60.225, 40.66.60.232, 40.66.62.154, 40.66.62.225, 40.81.62.199, 40.81.62.206, 40.81.62.209, 40.81.62.212, 40.81.62.221, 40.81.62.222, 40.90.191.153, 40.119.145.130, 40.119.147.102, 40.119.203.98, 40.119.203.99, 40.119.203.158, 40.119.203.159, 40.119.203.208, 40.119.203.209, 51.105.164.234, 51.105.164.241, 52.142.124.23, 52.155.168.45, 52.155.181.180, 52.155.181.181, 52.155.181.182, 52.155.181.183, 52.155.182.48, 52.155.182.49, 52.155.182.50, 52.156.202.7, 52.157.233.49, 52.157.234.222, 52.157.235.27, 52.157.236.195, 52.157.237.255, 52.157.239.132, 52.190.26.220, 52.190.31.62, 52.224.188.157, 52.224.188.168, 104.45.170.127, 104.45.170.161, 104.45.170.173, 104.45.170.174, 104.45.170.175, 104.45.170.176|\*. eu2.cas.ms, \* . EU2.Access-Control.CAS.ms, \* . EU2.SAML.CAS.ms|

### <a name="us-government-gcc-high-customers"></a>Clientes de la administración pública de Estados Unidos GCC

Para los clientes de la administración pública de Estados Unidos GCC, para habilitar Cloud App Security proxy inverso, agregue el **Puerto de salida 443** para los siguientes nombres DNS a la lista de permitidos del firewall:

```ini
    *.mcas-gov.us
    *.admin-mcas-gov.us
    mcasproxy.azureedge.net
```

## <a name="siem-agent-connection"></a>Conexión del agente SIEM

Para habilitar Cloud App Security para conectarse a su SIEM, agregue el **Puerto de salida 443** para las siguientes direcciones IP a la lista de permitidos del firewall:

|Centro de datos|Direcciones IP|
|----|----|
|Estados Unidos 1|13.64.26.88, 13.64.29.32, 13.80.125.22, 13.91.91.243, 40.74.1.235, 40.74.6.204, 51.143.58.207, 52.137.89.147, 52.183.75.62|
|US2|13.80.125.22, 20.36.222.59, 20.36.222.60, 40.74.1.235, 40.74.6.204, 51.143.58.207, 52.137.89.147, 52.183.75.62, 52.184.165.82|
|US3|13.80.125.22, 40.74.1.235, 40.74.6.204, 40.90.218.196, 40.90.218.198, 51.143.58.207, 52.137.89.147, 52.183.75.62|
|Unión Europea 1|13.80.125.22, 40.74.1.235, 40.74.6.204, 40.119.154.72, 51.143.58.207, 52.137.89.147, 52.157.238.58, 52.174.56.180, 52.183.75.62|
|EU2|13.80.125.22, 40.74.1.235, 40.74.6.204, 40.81.156.154, 40.81.156.156, 51.143.58.207, 52.137.89.147, 52.183.75.62|
|Estados Unidos 1 gov|13.72.19.4, 52.227.143.223|

> [!NOTE]
> Si no especificó un proxy al configurar el agente de Cloud App Security SIEM, debe permitir las conexiones http a http://ocsp.msocsp.com/ y OCSP.DigiCert.com en el puerto 80. Esto sirve para comprobar el estado de revocación de certificado al conectarse al portal de Cloud App Security.

## <a name="app-connector"></a>Conector de la aplicación

Se pueden usar estas direcciones IP para que Cloud App Security pueda acceder a algunas aplicaciones de terceros. Las direcciones IP permiten a Cloud App Security recopilar registros y proporcionan acceso a la consola de Cloud App Security.

> [!NOTE]
> Puede que vea estas direcciones IP en los registros de actividad del proveedor, ya que Cloud App Security realiza acciones de gobernanza y exámenes desde ellas.

Para conectarse a aplicaciones de terceros, habilite Cloud App Security para permitir la conexión desde estas direcciones IP:

|Centro de datos|Direcciones IP|
|----|----|----|
|Estados Unidos 1|13.64.26.88, 13.64.29.32, 13.64.30.76, 13.64.30.117, 13.64.30.118, 13.64.31.116, 13.64.196.27, 13.64.198.19, 13.64.198.97, 13.64.199.41, 13.68.76.47, 13.86.176.189, 13.86.176.211, 13.91.61.249, 13.91.91.243, 13.91.98.185, 13.93.216.68, 13.93.233.42, 40.118.211.172, 104.42.54.148, 104.209.35.177|
|US2|13.68.76.47, 20.36.222.59, 20.36.222.60, 40.67.152.91, 40.67.154.160, 40.67.155.146, 40.67.159.55, 40.84.2.83, 40.84.4.93, 40.84.4.119, 52.184.165.82, 52.232.224.227, 52.232.225.84, 104.42.54.148, 104.46.116.211, 104.46.116.211, 104.46.121.72, 104.46.121.72, 104.46.122.189, 104.46.122.189|
|US3|13.68.76.47, 40.90.218.196, 40.90.218.197, 40.90.218.198, 40.90.218.203, 40.90.220.190, 40.90.220.196, 51.143.120.236, 51.143.120.242, 104.42.54.148|
|Unión Europea 1|13.80.22.71, 13.95.29.177, 13.95.30.46, 40.67.219.133, 40.114.217.8, 40.114.217.8, 40.115.24.65, 40.115.24.65, 40.115.25.50, 40.115.25.50, 40.119.154.72, 51.105.55.62, 51.105.179.157, 51.137.200.32, 52.157.232.110, 52.157.233.92, 52.157.233.133, 52.157.238.58, 52.157.239.110, 52.174.56.180|
|EU2|40.81.152.171, 40.81.152.172, 40.81.156.153, 40.81.156.154, 40.81.156.155, 40.81.156.156, 51.105.55.62, 51.137.200.32, 51.145.108.227, 51.145.108.250|
|Estados Unidos 1 gov|52.227.138.248, 52.227.142.192, 52.227.143.223|

## <a name="third-party-dlp-integration"></a>Integración de DLP de terceros

Para permitir que Cloud App Security envíe datos a través de Stunnel al servidor ICAP, abra el firewall de red perimetral a estas direcciones IP con un número de puerto de origen dinámico.

1. **Direcciones de origen**: estas direcciones deben incluirse en la lista de admitidas como se detalla anteriormente para las aplicaciones de conector de la API de terceros
2. **Puerto TCP de origen**: dinámico
3. **Direcciones de destino**: una o dos direcciones IP del servidor Stunnel conectado al servidor ICAP externo
4. **Puerto TCP de destino**: según se defina en la red

> [!NOTE]
>
> - El número de puerto de Stunnel está establecido de forma predeterminada en 11344. Si es necesario, puede cambiarlo y usar otro, pero no olvide anotar el número de puerto nuevo.
> - Puede que vea estas direcciones IP en los registros de actividad del proveedor, ya que Cloud App Security realiza acciones de gobernanza y exámenes desde ellas.

Para conectar aplicaciones de terceros e integrar soluciones de DLP externas, habilite la conexión de Cloud App Security desde estas direcciones IP:

|Centro de datos|Direcciones IP|
|----|----|----|
|Estados Unidos 1|13.64.26.88, 13.64.29.32, 13.64.30.76, 13.64.30.117, 13.64.30.118, 13.64.31.116, 13.64.196.27, 13.64.198.19, 13.64.198.97, 13.64.199.41, 13.86.176.189, 13.86.176.211, 13.91.61.249, 13.91.91.243, 13.91.98.185, 13.93.216.68, 13.93.233.42, 40.118.211.172, 104.209.35.177|
|US2|20.36.222.59, 20.36.222.60, 40.67.152.91, 40.67.154.160, 40.67.155.146, 40.67.159.55, 40.84.2.83, 40.84.4.93, 40.84.4.119, 52.184.165.82, 52.232.224.227, 52.232.225.84, 104.46.116.211, 104.46.116.211, 104.46.121.72, 104.46.121.72, 104.46.122.189, 104.46.122.189|
|US3|40.90.218.196, 40.90.218.197, 40.90.218.198, 40.90.218.203, 40.90.220.190, 40.90.220.196, 51.143.120.236, 51.143.120.242|
|Unión Europea 1|13.80.22.71, 13.95.29.177, 13.95.30.46, 40.67.219.133, 40.114.217.8, 40.114.217.8, 40.115.24.65, 40.115.24.65, 40.115.25.50, 40.119.154.72, 51.105.179.157, 52.157.232.110, 52.157.233.92, 52.157.233.133, 52.157.238.58, 52.157.239.110, 52.174.56.180|
|EU2|40.81.152.171, 40.81.152.172, 40.81.156.153, 40.81.156.154, 40.81.156.155, 40.81.156.156, 51.145.108.227, 51.145.108.250|

## <a name="mail-server"></a>Servidor de correo

Para habilitar las notificaciones para que se envíen desde la plantilla y la configuración predeterminadas, agregue estas direcciones IP a la lista de permitidos de anti-spam. Las direcciones IP de correo electrónico dedicadas de Cloud App Security son:

- 65.55.234.192/26
- 207.46.50.192/26
- 65.55.52.224/27
- 94.245.112.0/27
- 111.221.26.0/27
- 207.46.200.0/27

Si desea personalizar la identidad del remitente de correo electrónico, Microsoft Cloud App Security habilita la personalización mediante MailChimp &reg; , un servicio de correo electrónico de terceros. Para facilitar el trabajo en el portal de Microsoft Cloud App Security, vaya a **Configuración**. Seleccione **configuración de correo** y revise los términos de servicio y la declaración de privacidad de Mailchimp. Después, conceda permiso a Microsoft para usar MailChimp en su nombre.

Si no Personaliza la identidad del remitente, las notificaciones por correo electrónico se enviarán con la configuración predeterminada.

Para trabajar con MailChimp, agregue esta dirección IP a la lista de permitidos de bloqueo de correo no deseado para permitir el envío de notificaciones: 198.2.134.139 (mail1.cloudappsecurity.com)

## <a name="log-collector"></a>Recopilador de registros

Para habilitar características de Cloud Discovery por medio de un recopilador de registros y detectar Shadow TI en la organización, abra los siguientes elementos:

- Permita que el recopilador de registros reciba tráfico entrante de FTP y Syslog.
- Permita que el recopilador de registros inicie tráfico saliente al portal (por ejemplo, contoso.cloudappsecurity.com) en el puerto 443.
- Permita que el recopilador de registros inicie tráfico saliente a Azure Blog Storage en el puerto 443:

  | Centro de datos |                        URL                                 |
  |-------------|------------------------------------------------------------|
  |     Estados Unidos 1     | https: \/ /adaprodconsole.BLOB.Core.Windows.net/             |
  |     US2     | https: \/ /prod03use2console1.BLOB.Core.Windows.net/         |
  |     US3     | https: \/ /prod5usw2console1.BLOB.Core.Windows.net/          |
  |     Unión Europea 1     | https: \/ /prod02euwconsole1.BLOB.Core.Windows.net/          |
  |     EU2     | https: \/ /prod4uksconsole1.BLOB.Core.Windows.net/           |
  |   Estados Unidos 1 gov   | https: \/ /gprd1usgvconsole1.BLOB.Core.usgovcloudapi.net/    |

> [!NOTE]
>
> - Si el Firewall requiere una lista de acceso de dirección IP estática y no admite la inclusión en listas blancas basadas en direcciones URL, permita que el recopilador de registros inicie el tráfico saliente a los [Microsoft Azure intervalos IP del centro](https://www.microsoft.com/download/details.aspx?id=56519) de seguridad en el puerto 443.
> - Permita que el recopilador de registros inicie tráfico saliente al portal de Cloud App Security.
> - Si no especificó un proxy al configurar el recopilador de registros, debe permitir las conexiones http a http://ocsp.msocsp.com/ y OCSP.DigiCert.com en el puerto 80. Esto sirve para comprobar el estado de revocación de certificado al conectarse al portal de Cloud App Security.

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Actividades diarias para proteger el entorno de nube](daily-activities-to-protect-your-cloud-environment.md)

[!INCLUDE [Open support ticket](includes/support.md)]
