---
title: Personalizar el portal | Microsoft Docs
description: En este tema se proporcionan los pasos iniciales para personalizar el portal.
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 11/21/2016
ms.topic: get-started-article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: 2e7e57b0-db54-4d75-896c-4700dd9abe48
ms.reviewer: reutam
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 76c705a38ffb0d61b9ad2eeaf3bdb939f5326589
ms.openlocfilehash: 912d3c5065722469c436446ba67511ffc6e44d77


---

# <a name="customize-the-portal"></a>Personalizar el portal
En el siguiente procedimiento se proporcionan instrucciones para personalizar el portal de Cloud App Security.
  
## <a name="set-up-the-portal"></a>Configurar el portal  
  
1.  En la barra de menús del portal de Cloud App Security, haga clic en el icono de configuración ![icono de configuración](./media/settings-icon.png "settings icon") y seleccione **Configuración general** para configurar lo siguiente:  
  
3.  **Detalles de la organización**  
  
     Es importante que indique un **nombre para mostrar de la organización** relativo a su organización. Este nombre se mostrará en los correos electrónicos y páginas web enviados desde el sistema.  
  
     Proporcione un **nombre del entorno** (inquilino). Esto es especialmente importante si administra varios inquilinos.  
  
     Incluya una lista de los **dominios administrados**. Los dominios administrados sirven para que Cloud App Security pueda averiguar qué usuarios son internos y cuáles son externos, así como dónde se deben y no se deben compartir archivos. Esto se usa en los informes y de cara a las alertas.  
> [!NOTE] 
> Los usuarios de dominios que no están configurados como internos se marcarán como externos y no se examinarán en busca de actividades o archivos.
   
También se puede proporcionar un **logotipo**, que se mostrará en las notificaciones de correo electrónico y en las páginas web enviadas desde el sistema. El logotipo tiene que ser un archivo .png con un tamaño máximo de 150x50 píxeles con fondo transparente.  
  
4.  **Configuración de la privacidad de correo electrónico del registro de actividades**  
  
     Cuando se detectan mensajes de correo de Exchange Online, es posible establecer cómo se muestran a fin de preservar la privacidad. Los mensajes de correo se pueden configurar para mostrarse con una **línea de asunto enmascarada**, con una **línea de asunto completa** o con un **identificador solo**.  
  
     ![configuración general](./media/general-settings.png "general settings")  
  
5.  **Configuración de región e idioma**  
  
     Establezca el **idioma** predeterminado que se usará en el portal. Para cambiar el idioma de un administrador específico, vaya a **Configuración de usuario** > **Configuración de la cuenta**.  
  
     ![idioma de la zona horaria](./media/timezone-language.png "timezone language")  
  
     Establezca la **zona horaria principal**. Cloud App Security analiza y agrega datos continuamente. La zona horaria del portal de Cloud App Security está establecida en UTC de forma predeterminada. Es importante establecer la zona horaria principal, ya que permite a Cloud App Security fechar con precisión los incidentes en el sistema. Por ejemplo, en el diagrama de actividad, los datos se organizan por fecha, y estas fechas se ven afectadas por la zona horaria del sistema, por lo que si no ha modificado la zona horaria predeterminada, los datos se organizarán en días de 24 horas según la zona horaria UTC, lo que puede sesgar los datos por muchas horas.  
  
     ![zona horaria principal](./media/master-time-zone.png "master time zone")  
  
6.  Si, en un momento determinado, quiere hacer una copia de seguridad de la configuración del portal, puede hacerlo en esta pantalla. Haga clic en Exportar configuración del portal para crear un archivo .json con todas las opciones de configuración del portal, incluidas las reglas de directivas, los grupos de usuarios y los intervalos de direcciones IP.  
  
     ![consola de copia de seguridad](./media/backup-console.png "backup console")  
  
7.  Para agregar más administradores a Cloud App Security, haga clic en el engranaje de configuración ![icono de configuración](./media/settings-icon.png "settings icon") y, luego, en **Administrar acceso de administrador**. Agregue los administradores que deben tener acceso a Cloud App Security y haga clic en **Cerrar**.  
>[!NOTE]
>Cualquier usuario no invitado (con un rol adecuado, como administrador global, de seguridad o de cumplimiento), puede invitar a otros usuarios a Cloud App Security.
  
![administrar el acceso de administrador](./media/manage-admin-access.png "manage admin access")  
  
##  <a name="a-nameadminsettingsa-customize-your-admin-settings"></a><a name="Adminsettings"></a> Personalizar la configuración de administración  
Para configurar sus preferencias como un administrador de Cloud App Security, haga clic en su nombre en la barra de menús del portal y seleccione **Configuración de usuario** para establecer lo siguiente:  
  
1.  Haga clic en **Configuración de la cuenta**. Aquí puede personalizar el idioma del portal para verlo según su elección. Se puede establecer para mostrar el portal en el idioma predeterminado o bien en un idioma diferente de su preferencia.  
  
     ![configuración de usuario personalizada](./media/custom-user-settings.png "custom user settings")  
  
2.  Haga clic en **Notificaciones** y establezca las preferencias de notificación de texto y correo electrónico para los mensajes recibidos del sistema.  Puede establecer la gravedad de las alertas y las infracciones para las que quiera recibir correos electrónicos. La gravedad se establece por directiva, por lo que cuando se produzcan infracciones, recibirá una notificación de correo según esta configuración y la configuración de gravedad de la directiva que se ha infringido. Los correos se enviarán al alias asociado con la cuenta de usuario de administrador que se ha usado para iniciar sesión en Cloud App Security. Escriba un número de teléfono para permitir que Cloud App Security le envíe mensajes de texto cuando se envíen alertas y notificaciones y establezca el nivel de gravedad a partir del cual quiera recibir notificaciones por mensaje de texto.  
  
> [!NOTE] 
> El número máximo de alertas que se enviarán por mensaje de texto es de 10 al día por número de teléfono. Tenga en cuenta que el día se calcula según la zona horaria UTC. 
  
  ![configuración de notificación](./media/notification-settings.png "notification settings")  
  
  
3. Haga clic en **Guardar** cuando acabe.  
  
##  <a name="a-nameiptagsandrangesa-organize-the-data-according-to-your-needs"></a><a name="IPtagsandRanges"></a> Organizar los datos de acuerdo a las necesidades  
Para identificar fácilmente las direcciones IP conocidas, como las direcciones IP de la oficina física, es necesario establecer los intervalos de direcciones IP que permiten etiquetar y clasificar adecuadamente, así como personalizar la forma en que los registros y alertas se muestran e investigan.   
Cada grupo de intervalos IP se puede clasificar en función de una lista predeterminada de categorías IP o etiquetarse con etiquetas IP de creación propia. Además, esta configuración permite invalidar la información de geolocalización pública según su conocimiento de la red interna.  
  
Se admite tanto IPv4 como IPv6.  
  
En la barra de menús, haga clic en el icono de configuración ![icono de configuración](./media/settings-icon.png "settings icon") y seleccione **Intervalos de direcciones IP**. Haga clic en **+Agregar intervalo de direcciones IP** y configure lo siguiente:  
  
> [!NOTE]  
>  La ubicación y el ISP registrado invalidarán los valores predeterminados.   
> Las etiquetas IP, por contra, se agregan a la actividad sin invalidar datos.  
  
1.  Dé un **nombre** al intervalo IP. El nombre no aparecerá en el registro de actividades, sino que solo se usará para administrar el intervalo IP.  
  
     Para incluir el intervalo IP en una categoría IP, seleccione una categoría del menú desplegable.  
  
2.  Escriba el **intervalo de direcciones IP** que quiera configurar y, después, haga clic en el botón "+". Puede agregar cuantas direcciones IP y subredes quiera mediante la notación de prefijos de red (también conocida como notación CIDR), por ejemplo, 192.168.1.0/32.  
  
3.  Escriba un nuevo valor para **invalidar los campos de ubicación** u organización (ISP) de estas direcciones. Por ejemplo, si tiene una dirección IP que se considera públicamente como perteneciente a Irlanda, pero sabe que está en Estados Unidos, puede invalidar esta configuración.  
  
4.  Escriba un **ISP registrado**. Esto invalidará los datos de sus actividades.  
  
5.  Especifique una etiqueta para **etiquetar** las actividades de estas direcciones IP. La etiqueta se creará si escribe una palabra en el cuadro. Con la etiqueta ya configurada, puede agregarla a más intervalos IP seleccionándola de la lista. Puede agregar tantas etiquetas IP como quiera para cada intervalo. Las etiquetas IP se pueden usar al crear directivas.  
  
     Las **etiquetas IP** de Cloud App Security integradas están configuradas para direcciones que entrañan riesgo y se actualizan constantemente. Estas etiquetas incluyen servidores proxy anónimos, proveedores por satélite, nodos de salida de Tor y la red proxy de Cloud App Security. Estas etiquetas integradas no son visibles.  
  
6.  Las **categorías IP** sirven para reconocer fácilmente las actividades de las direcciones IP interesantes. Las categorías están disponibles en el portal, pero requieren una configuración de usuario para saber qué direcciones IP están incluidas en cada categoría, excepto la categoría de "De riesgo", que incluye dos etiquetas IP: proxy anónimo y Tor.  
  
     Las siguientes categorías IP están disponibles:  
  
    -   **Administrativo**: deben ser todas las direcciones IP de los administradores.  
  
    -   **Interno**: deben ser todas las direcciones IP de la red interna, las sucursales y las direcciones de itinerancia de Wi-Fi.  
  
    -   **De riesgo**: deben ser todas las direcciones IP que se consideran que entrañan riesgos. Puede englobar direcciones IP sospechosas detectadas en el pasado, direcciones IP en las redes de la competencia, etc.  
  
    -   **VPN**: deben ser las direcciones IP que se usan en los trabajos remotos.  
  
    -   **Proxy en la nube**: debe ser la dirección IP del proxy en la nube.  
  
7.  Haga clic en **Crear** cuando acabe.  
  
     ![nuevo intervalo de direcciones IP](./media/newipaddress-range.png "newipaddress range")  
  
##  <a name="a-nameadallommailsettingsa-personalize-your-experience"></a><a name="Adallom_mailsettings"></a>Personalizar la experiencia  
En la barra de menús, haga clic en el icono de configuración ![icono de configuración](./media/settings-icon.png "settings icon") y seleccione **Configuración de correo** para establecer los parámetros de las notificaciones de correo enviadas desde Cloud App Security a los administradores que solicitan alertas, así como de las notificaciones enviadas a los usuarios finales sobre infracciones en las que puedan haber participado.  
  
![menú de configuración de correo](./media/mail-setting-menu.png "mail setting menu")  
  
Configura lo siguiente:  
  
1.  **Dirección de correo electrónico del campo Desde**: cuenta de correo que quiere usar para enviar la notificación.  
  
     **Nombre para mostrar del campo Desde**: nombre que quiere que aparezca en el campo **Desde** del mensaje de correo.  
  
     **Dirección de correo electrónico del campo Responder a**: cuenta de correo que se usará para las respuestas al mensaje.  
  
     ![configuración de las opciones de correo](./media/mail-settings-config.png "mail settings config")  
  
2.  Puede usar un archivo .html para personalizar y diseñar los mensajes de correo enviados desde el sistema. El archivo .html que use como plantilla debe incluir lo siguiente:  
  
    -   Todas las CSS de plantilla deben estar alineadas en la plantilla.  
  
    -   La plantilla debe tener tres marcadores de posición no modificables:  
  
         %%logo%%: dirección URL que lleva al logotipo de la empresa que se ha cargado en la página de configuración General.  
  
         %%title%%: marcador de posición del título del correo electrónico, según lo establecido por la directiva.  
  
         %%content%%: marcador de posición del contenido que se incluirá para los usuarios finales, según lo establecido por la directiva.  
  
     Esta es una plantilla de correo de ejemplo:  
  
    ```  
    <!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">  
    <html>  
    <head>  
      <meta http-equiv="Content-Type" content="text/html; charset=UTF-8"/>  
      <meta name="viewport" content="width=device-width, initial-scale=1.0"/>  
    </head>  
    <body class="end-user">  
    <table border="0" cellpadding="20%" cellspacing="0" width="100%" id="background-table">  
      <tr>  
        <td align="center">  
          <!--[if (gte mso 9)|(IE)]>  
          <table width="600" align="center" cellpadding="0" cellspacing="0" border="0">  
            <tr>  
              <td>  
          <![endif]-->  
          <table bgcolor="#ffffff" align="center" border="0" cellpadding="0" cellspacing="0" style="padding-bottom: 40px;" id="container-table">  
            <tr>  
              <td align="right" id="header-table-cell">  
                <img src="%%logo%%" alt="Microsoft Cloud App Security" id="org-logo" />  
              </td>  
            </tr>  
            <tr>  
              <td style="padding-top: 58px;" align="center" valign="top">  
                <table width="100%" cellpadding="12">  
                  <tr>  
                    <td align="center" class="round-title">  
                      %%title%%  
                    </td>  
                  </tr>  
                </table>  
              </td>  
            </tr>  
            <tr>  
              <td style="padding: 0 40px 79px 40px;" class="content-table-cell" align="left" valign="top">  
                  %%content%%  
              </td>  
            </tr>  
            <tr>  
              <td class="last-row"></td>  
            </tr>  
          </table>  
          <!--[if (gte mso 9)|(IE)]>  
          </td>  
          </tr>  
          </table>  
          <![endif]-->  
        </td>  
      </tr>  
    </table>  
    </body>  
    </html>  
  
    ```  
  
3.  Haga clic en **Cargar una plantilla...** y seleccione el archivo que ha creado.  
  
     Luego, haga clic en **Enviar un correo electrónico de prueba** para enviarse a sí mismo un mensaje de prueba para ver un ejemplo de la plantilla creada.  
     El correo se enviará a la cuenta usada para iniciar sesión en el portal. En el correo de prueba podrá ver los campos de metadatos, la plantilla, el asunto del correo, el título en el cuerpo del correo y el contenido.  
  
## <a name="single-sign-on"></a>Inicio de sesión único  
Cloud App Security está acoplado a Azure Active Directory para la autenticación, el aprovisionamiento y la concesión de licencias de las actividades relacionadas. Para obtener información sobre cómo administrar el inicio de sesión único, consulte [Lista de compatibilidad de federación de Azure Active Directory: proveedores de identidades de terceros que se pueden utilizar para implementar el inicio de sesión único](https://msdn.microsoft.com/library/azure/jj679342.aspx).  


> [!NOTE] 
> Si utiliza ExpressRoute, Cloud App Security se ha implementado en Azure y está totalmente integrado con [ExpressRoute](https://azure.microsoft.com/documentation/articles/expressroute-introduction/). Todas las interacciones con las aplicaciones de Cloud App Security y el tráfico enviado a Cloud App Security, incluida la carga de registros de detección, se enrutan a través del **emparejamiento público** de ExpressRoute para mejorar la latencia, el rendimiento y la seguridad. No hay ningún paso de configuración necesario en el lado cliente.  
    Para obtener más información sobre el emparejamiento público, vea [Circuitos ExpressRoute y dominios de enrutamiento](https://azure.microsoft.com/documentation/articles/expressroute-circuit-peerings/).  
    
## <a name="see-also"></a>Consulte también  
[Configurar Cloud Discovery](set-up-cloud-discovery.md)   
[Para obtener soporte técnico, visite la página de soporte técnico asistido de Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Los clientes Premier también pueden elegir Cloud App Security directamente desde el Portal Premier.](https://premier.microsoft.com/)  
  
  


<!--HONumber=Nov16_HO5-->


