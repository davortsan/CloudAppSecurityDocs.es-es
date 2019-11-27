---
title: Integración de DLP externa de Cloud App Security a través de ICAP seguro
description: En este artículo se proporcionan los pasos necesarios para configurar la conexión ICAP en Cloud App Security y la instalación de Stunnel.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 12/10/2018
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 9656f6c6-7dd4-4c4c-a0eb-f22afce78071
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 26046b25636523aab8494dcb122660d94e3182b9
ms.sourcegitcommit: 094bb42a198fe733cfd3aec79d74487672846dfa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/24/2019
ms.locfileid: "74460726"
---
# <a name="external-dlp-integration"></a>Integración de DLP externa

*Se aplica a: Microsoft Cloud App Security*

Microsoft Cloud App Security puede integrarse con las soluciones DLP existentes para ampliar estos controles a la nube y, al mismo tiempo, conservar una directiva coherente y unificada en las actividades locales y en la nube. La plataforma exporta interfaces fáciles de usar, como API de REST e ICAP, y permite la integración con sistemas de clasificación de contenido, como Symantec Data Loss Prevention (antes conocida como Vontu Data Loss Prevention) o Forcepoint DLP. 

La integración se lleva a cabo mediante el protocolo ICAP estándar, un protocolo semejante a HTTP que se describe en [RFC 3507](https://tools.ietf.org/html/rfc3507). Para proteger ICAP para la transmisión de los datos, es necesario configurar un túnel SSL seguro (Stunnel) entre la solución DLP y Cloud App Security. La instalación de Stunnel proporciona la funcionalidad de cifrado TLS de los datos durante su transmisión entre el servidor DLP y Cloud App Security. 

En este tema se proporcionan los pasos necesarios para configurar la conexión ICAP en Cloud App Security y la instalación de Stunnel para proteger la comunicación a través de él.


## <a name="architecture"></a>Arquitectura
Cloud App Security examina el entorno de nube y, en función de la configuración de la directiva de archivo, decide si debe examinar el archivo con el motor DLP interno o la DLP externa. Si se examina mediante la DLP externa, el archivo se envía a través del túnel seguro al entorno del cliente, donde se retransmite al dispositivo ICAP para obtener el veredicto de la DLP: permitido o bloqueado. Las respuestas se envían de vuelta a Cloud App Security a través de Stunnel, donde la directiva las usa para determinar las acciones posteriores, como las notificaciones, la cuarentena y el control de uso compartido.

![Arquitectura de Stunnel](./media/icap-architecture-stunnel.png)

Dado que Cloud App Security se ejecuta en Azure, las implementaciones en Azure tendrán mejores resultados. Aun así se admiten otras opciones, incluidas otras implementaciones en la nube y locales. La implementación en otros entornos puede afectar al rendimiento, debido a una latencia mayor y un rendimiento inferior. El servidor ICAP y Stunnel deben implementarse juntos en la misma red para garantizar que se cifre el tráfico.

## <a name="prerequisites"></a>Prerequisites
Para que Cloud App Security envíe datos a través de Stunnel al servidor ICAP, abra el firewall de red perimetral a las direcciones IP externas que usa Cloud App Security con un número de puerto de origen dinámico. 

1.  Direcciones de origen: vea la sección [Requisitos previos en Conectar aplicaciones](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md#prerequisites)
2.  Puerto TCP de origen: dinámico
3.  Direcciones de destino: una o dos direcciones IP de Stunnel conectado al servidor ICAP externo que configurará en los pasos siguientes
4.  Puerto TCP de destino: según se defina en su red

> [!NOTE] 
> El número de puerto de Stunnel está establecido de forma predeterminada en 11344. Puede cambiarlo a otro puerto si es necesario, pero no olvide tomar nota del nuevo número de puerto, ya que deberá especificarlo en el paso siguiente.

## <a name="step-1--set-up-icap-server"></a>PASO 1: Configurar el servidor ICAP

Configure un servidor ICAP, anote el número de puerto y asegúrese de establecer **Modo** en **Bloqueo**. El modo de bloqueo establece el servidor ICAP para que retransmita el veredicto de clasificación a Cloud App Security.

Vea la documentación del producto de DLP externa para obtener instrucciones sobre cómo hacerlo. Por ejemplo, vea [Apéndice A: Instalación del servidor ICAP de Forcepoint](#forcepoint) y [Apéndice B: Guía de implementación de Symantec](#symantec).

## <a name="step-2--set-up-your-stunnel-server"></a>PASO 2: Configurar el servidor de Stunnel 

En este paso, configurará la aplicación Stunnel conectada al servidor ICAP. 

>[!NOTE]
> Aunque se recomienda encarecidamente que lo haga, este paso es opcional y puede omitirse en las cargas de trabajo de prueba. 

### <a name="install-stunnel-on-a-server"></a>Instalar Stunnel en un servidor

**Requisitos previos**

- **Un servidor**: un servidor Windows Server o un servidor Linux basado en una distribución principal.

Visite el [sitio web de Stunnel](https://www.stunnel.org/index.html) para obtener más información sobre los tipos de servidores que admiten la instalación de Stunnel. Si usa Linux, puede usar el administrador de distribución de Linux para instalarlo.

#### <a name="install-stunnel-on-windows"></a>Instalar Stunnel en Windows

1. [Descargue la instalación más reciente de Windows Server](https://www.stunnel.org/downloads.html) (esta aplicación debería funcionar en todas las ediciones recientes de Windows Server).
   (instalación predeterminada).

2. Durante la instalación, no cree un certificado autofirmado. Creará un certificado en un paso posterior.

3. Haga clic en **Start server after installation** (Iniciar el servidor después de la instalación).

4. Cree un certificado de una de las siguientes maneras:

   - Use el servidor de administración de certificados para crear un certificado SSL en el servidor ICAP. Después, copie las claves en el servidor que ha preparado para la instalación de Stunnel.
   - O bien, en el servidor de Stunnel, use los siguientes comandos de OpenSSL para generar una clave privada y un certificado autofirmado. Reemplace estas variables:
     - **key.pem** por el nombre de la clave privada
     - **cert.pem** por el nombre del certificado
     - **stunnel-key** por el nombre de la clave recién creada

5. En la ruta de instalación de Stunnel, abra el directorio de configuración. De forma predeterminada es c:\Archivos de programa (x86)\stunnel\config\
6. Ejecute la línea de comandos con permisos de administrador: `..\bin\openssl.exe genrsa -out key.pem 2048 `
      
     ` ..\bin\openssl.exe  req -new -x509 -config ".\openssl.cnf" -key key.pem -out .\cert.pem -days 1095`

7. Concatene cert.pem y key.pem y guárdelos en el archivo: `type cert.pem key.pem >> stunnel-key.pem`

8. [Descargue la clave pública](https://adaprodconsole.blob.core.windows.net/icap/publicCert.pem) y guárdela en esta ubicación **C:\Archivos de programa (x86)\stunnel\config\MCASca.pem**.

9. Agregue las reglas siguientes para abrir el puerto en el firewall de Windows:

       rem Open TCP Port 11344 inbound and outbound
       netsh advfirewall firewall add rule name="Secure ICAP TCP Port 11344" dir=in action=allow protocol=TCP localport=11344
       netsh advfirewall firewall add rule name="Secure ICAP TCP Port 11344" dir=out action=allow protocol=TCP localport=11344

10. Ejecute `c:\Program Files (x86)\stunnel\bin\stunnel.exe` para abrir la aplicación Stunnel. 

11. Haga clic en **Configuración** y en **Editar configuración**.

    ![Editar la configuración de Windows Server](./media/stunnel-windows.png)
 
12. Abra el archivo y pegue las siguientes líneas de configuración de servidor. **DLP Server IP** es la dirección IP del servidor ICAP, **stunnel-key** es la clave creada en el paso anterior y **MCASCAfile** es el certificado público del cliente de Stunnel de Cloud App Security. Elimine todo el texto de ejemplo que vea (en el ejemplo se muestra texto de Gmail) y copie el siguiente texto en el archivo:

        [microsoft-Cloud App Security]
        accept = 0.0.0.0:11344
        connect = **ICAP Server IP**:1344
        cert = C:\Program Files (x86)\stunnel\config\**stunnel-key**.pem
        CAfile = C:\Program Files (x86)\stunnel\config\**MCASCAfile**.pem
        TIMEOUTclose = 0
        client = no
13. Guarde el archivo y haga clic en **Volver a cargar configuración**.

14. Para asegurarse de que todo funciona según lo esperado, desde un símbolo del sistema, ejecute `netstat -nao  | findstr 11344`
 

#### <a name="install-stunnel-on-ubuntu"></a>Instalar Stunnel en Ubuntu

El siguiente ejemplo se basa en una instalación del servidor Ubuntu cuando se inicia sesión como usuario raíz. En el caso de otros servidores, use comandos paralelos. 

En el servidor preparado, descargue e instale la versión más reciente de Stunnel. Ejecute el siguiente comando en el servidor de Ubuntu para instalar Stunnel y OpenSSL:

    apt-get update
    apt-get install openssl -y
    apt-get install stunnel4 -y

Ejecute el siguiente comando desde una consola para comprobar que Stunnel está instalado. Debería obtener el número de versión y una lista de opciones de configuración:

    stunnel-version

### <a name="generate-certificates"></a>Generar certificados

El servidor ICAP y Cloud App Security usan una clave privada y un certificado público para cifrar y autenticar el servidor en Stunnel. Asegúrese de que crea la clave privada sin una frase de contraseña para que Stunnel se pueda ejecutar como un servicio en segundo plano. Además, establezca el permiso de los archivos en **lectura** para el propietario del túnel de SSL y en **ninguno** para todos los demás usuarios.

Puede crear los certificados de una de las maneras siguientes:
- Use el servidor de administración de certificados para crear un certificado SSL en el servidor ICAP. Después, copie las claves en el servidor que ha preparado para la instalación de Stunnel. 
- O bien, en el servidor de Stunnel, use los siguientes comandos de OpenSSL para generar una clave privada y un certificado autofirmado. Reemplace estas variables:
    - **"key.pem"** por el nombre de la clave privada
    - **"cert.pem"** por el nombre del certificado
    - **"stunnel-key"** por el nombre de la clave recién creada
       
            openssl genrsa -out key.pem 2048
            openssl req -new -x509 -key key.pem -out cert.pem -days 1095
            cat key.pem cert.pem >> /etc/ssl/private/stunnel-key.pem

### <a name="download-the-cloud-app-security-stunnel-client-public-key"></a>Descargar la clave pública del cliente de Stunnel de Cloud App Security

Descargue la clave pública de https://adaprodconsole.blob.core.windows.net/icap/publicCert.pem y guárdela en **/etc/ssl/certs/MCASCAfile.pem**.

### <a name="configure-stunnel"></a>Configurar Stunnel 

La configuración de Stunnel se establece en el archivo stunnel.conf.

1. Cree el archivo stunnel.conf en el directorio siguiente: **vim /etc/stunnel/stunnel.conf**.

2. Abra el archivo y pegue las siguientes líneas de configuración de servidor.  **DLP Server IP** es la dirección IP del servidor ICAP, **stunnel-key** es la clave creada en el paso anterior y **MCASCAfile** es el certificado público del cliente de Stunnel de Cloud App Security:

        [microsoft-Cloud App Security]
        accept = 0.0.0.0:11344
        connect = **ICAP Server IP**:1344
        cert = /etc/ssl/private/**stunnel-key**.pem
        CAfile = /etc/ssl/certs/**MCASCAfile**.pem
        TIMEOUTclose = 1
        client = no


### <a name="update-your-ip-table"></a>Actualizar la tabla de direcciones IP
Actualice la tabla de direcciones IP con la siguiente regla de enrutamiento:
   
    iptables -I INPUT -p tcp --dport 11344 -j ACCEPT

Use los siguientes comandos para que la actualización en la tabla de direcciones IP sea persistente:

     sudo apt-get install iptables-persistent
     sudo /sbin/iptables-save > /etc/iptables/rules.v4
 

### <a name="run-stunnel"></a>Ejecutar Stunnel
1. En el servidor de Stunnel, ejecute el siguiente comando:

        vim /etc/default/stunnel4

2. Cambie la variable ENABLED a 1:

        ENABLED=1

3. Reinicie el servicio para que la configuración tenga efecto:

        /etc/init.d/stunnel4 restart

4. Ejecute los comandos siguientes para comprobar que Stunnel se ejecuta correctamente:

        ps -A | grep stunnel

    y que está escuchando en el puerto indicado:

        netstat -anp | grep 11344

5. Asegúrese de que la red en la que se ha implementado el servidor de Stunnel cumple los requisitos previos de la red que se han mencionado anteriormente. Esto es necesario para que las conexiones entrantes desde Cloud App Security lleguen correctamente al servidor.

Si el proceso todavía no se está ejecutando, vea la [documentación de Stunnel](https://www.stunnel.org/docs.html) para solucionar problemas.


## <a name="step-3--connect-to-cloud-app-security"></a>PASO 3: Conectar con Cloud App Security

1. En Cloud App Security, en **Configuración**, seleccione **Extensiones de seguridad** y vaya a la pestaña **DLP externa**.

2. Haga clic en el signo más para agregar una nueva conexión. 

3. En el asistente para **agregar nueva DLP externa**, proporcione un **nombre de conexión** (por ejemplo, Mi conector de Forcepoint), que se usará para identificar el conector.

4. Seleccione el **tipo de conexión**:
    - **Symantec Vontu**: use la integración personalizada para dispositivos Vontu DLP.
    - **Forcepoint DLP**: use la integración personalizada para dispositivos Forcepoint DLP.
    - **Generic ICAP – REQMOD**: use otros dispositivos DLP que usan la [modificación de solicitudes](https://tools.ietf.org/html/rfc3507).
    - **Generic ICAP – RESPMOD**: use otros dispositivos DLP que usan la [modificación de respuestas](https://tools.ietf.org/html/rfc3507).
    ![Conexión ICAP de Cloud App Security](./media/icap-wizard1.png)

5. Vaya al certificado público que generó en los pasos anteriores ("cert.pem") para conectarse con Stunnel. Haga clic en **Siguiente**.

   > [!NOTE]
   > Se recomienda encarecidamente que active la casilla **Use secure ICAP** (Usar ICAP seguro) para configurar una puerta de enlace cifrada de Stunnel. Si va a realizar pruebas o si no dispone de un servidor de Stunnel, puede desactivar esta opción para realizar la integración directamente con el servidor DLP. 

5. En la pantalla **Configuración del servidor**, proporcione la **dirección IP** y el **puerto** del servidor de Stunnel que ha configurado en el paso 2. Para equilibrar la carga, puede configurar la **dirección IP** y el **puerto** en un servidor adicional. Las direcciones IP proporcionadas deben ser las direcciones IP estáticas externas de los servidores.

   ![Conexión ICAP de Cloud App Security](./media/icap-wizard2.png)
6. Haga clic en **Siguiente**. Cloud App Security probará la conectividad con el servidor que ha configurado. Si recibe un error, revise las instrucciones y la configuración de red. Cuando lo haya conectado correctamente, haga clic en **Salir**.

7. Ahora, para dirigir el tráfico a este servidor de DLP externa, cuando cree una **directiva de archivo**, seleccione en **Método de inspección de contenido** la conexión que ha creado. Obtenga más información sobre cómo [crear una directiva de archivo](data-protection-policies.md).


## Apéndice A: Instalación del servidor ICAP de Forcepoint<a name="forcepoint"></a>

En Forcepoint, configure el dispositivo con estos pasos:

1.  En el dispositivo DLP, vaya a **Implementación** > **System Modules** (Módulos del sistema). 

    ![Implementación de ICAP](./media/icap-system-modules.png)

2.  En la pestaña **General**, asegúrese de que **ICAP Server** (Servidor ICAP) está **Habilitado** y el **Puerto** predeterminado está establecido en **1344**. Además, en **Allow connection to this ICAP Server from the following IP addresses** (Permitir la conexión con este servidor ICAP desde las siguientes direcciones IP), seleccione **Cualquier dirección IP**.
 
    ![Configuración de ICAP](./media/icap-ip-address.png)

3.  En la pestaña HTTP/HTTPS, asegúrese de establecer el **Modo** en **Bloqueo**.
 
    ![Bloqueo de ICAP](./media/icap-blocking.png)
 

## Apéndice B: Guía de implementación de Symantec <a name="symantec"></a>

Las versiones de Symantec DLP compatibles son la 11 y las versiones posteriores. 

Como se mencionó anteriormente, debe implementar un servidor de detección en el mismo centro de datos de Azure en que reside el inquilino de Cloud App Security. El servidor de detección se sincroniza con el servidor de cumplimiento a través de un túnel IPsec dedicado. 
 
### <a name="detection-server-installation"></a>Instalación del servidor de detección 
El servidor de detección que Cloud App Security usa es un servidor estándar de Network Prevent for Web. Hay varias opciones de configuración que se deben modificar:
1. Deshabilite **Modo de prueba**:
   1. En **Sistema** > **Servidores y detectores**, haga clic en el destino de ICAP. 
    
      ![Destino de ICAP](./media/icap-target.png)
    
   2. Haga clic en **Configurar**. 
    
      ![Configuración del destino de ICAP](./media/configure-icap-target.png)
    
   3. Deshabilite el **Modo de prueba**.
    
      ![deshabilitar el modo de prueba](./media/icap-disable-trial-mode.png)
    
2. En **ICAP** > **Filtrado de respuesta**, cambie el valor **Omitir respuestas menores que** a 1.


3. Agregue "application/\*" a la lista **Inspect Content Type</em>** (Inspeccionar tipo de contenido).
     ![inspeccionar tipo de contenido](./media/icap-inspect-content-type.png)

4. Haga clic en **Guardar**.


### <a name="policy-configuration"></a>Configuración de directivas
Cloud App Security admite sin problemas todos los tipos de reglas de detección que se incluyen con Symantec DLP, por lo que no es necesario modificar las reglas existentes. Pero hay un cambio de configuración que se debe aplicar a todas las directivas nuevas y existentes para permitir la integración total. Este cambio implica agregar una regla de respuesta específica a todas las directivas. 

Agregue el cambio de configuración a Vontu:

1.  Vaya a **Administrar** > **Directivas** > **Reglas de respuesta** y haga clic en **Agregar regla de respuesta**.
    
    ![agregar regla de respuesta](./media/icap-add-response-rule.png)

2.  Asegúrese de que se seleccionó **Respuesta automatizada** y haga clic en **Siguiente**.

    ![respuesta automatizada](./media/icap-automated-response.png)

3. Escriba un nombre de regla, por ejemplo, **Bloquear HTTP/HTTPS**. En **Acciones**, seleccione **Bloquear HTTP/HTTPS** y haga clic en **Guardar**.

    ![bloquear http](./media/icap-block-http.png)

Agregue la regla que creó a cualquier directiva existente:

1. En cada directiva, vaya a la pestaña **Respuesta**.

2. En la lista desplegable **Regla de respuesta**, seleccione la regla de respuesta de bloqueo que creó anteriormente.

3. Guardar la directiva.
   
    ![deshabilitar el modo de prueba](./media/icap-add-policy.png)

Esta regla se debe agregar a todas las directivas existentes.

>[!NOTE]
> Si utiliza Symantec Vontu para examinar archivos desde Dropbox, CAS mostrará automáticamente el archivo como originario de la siguiente dirección URL: http://misc/filename. Esta dirección URL del marcador de posición no lleva a ninguna parte, pero se utiliza para fines de registro.


## <a name="next-steps"></a>Pasos siguientes 
[Controlar las aplicaciones en la nube con directivas](control-cloud-apps-with-policies.md)   

[!INCLUDE [Open support ticket](includes/support.md)]  
