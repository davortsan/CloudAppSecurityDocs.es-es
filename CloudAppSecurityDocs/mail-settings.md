---
title: "Establecimiento de preferencias de notificación de correo electrónico | Microsoft Docs"
description: "En este artículo se proporciona información sobre cómo personalizar las notificaciones de correo electrónico que Cloud App Security envía."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 5/23/2017
ms.topic: get-started-article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: 8402cdc9-4969-4150-b567-ccc9d75e5370
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: ce24e4c25ab4d8b85e4ddb6d6d574dd29b8c2003
ms.sourcegitcommit: 2f4474084c7e07ac4853945ab5aa1ea78950675d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/28/2017
---
##  <a name="mailsettings"></a> Establecimiento de preferencias de notificación de correo electrónico  
En la barra de menús, haga clic en el icono de configuración ![icono de configuración](./media/settings-icon.png "icono de configuración") y seleccione **Configuración de correo** para establecer los parámetros de las notificaciones de correo enviadas desde Cloud App Security a los administradores que solicitan alertas, así como de las notificaciones enviadas a los usuarios finales sobre infracciones en las que puedan haber participado.  
  
![menú de configuración de correo](./media/mail-setting-menu.png "menú de configuración de correo")  
  
Configura lo siguiente:  
  
1.  **Dirección de correo electrónico del campo Desde**: cuenta de correo que quiere usar para enviar la notificación.  
  
     **Nombre para mostrar del campo Desde**: nombre que quiere que aparezca en el campo **Desde** del mensaje de correo.  
  
     **Dirección de correo electrónico del campo Responder a**: cuenta de correo que se usará para las respuestas al mensaje.  
  
     ![configuración de las opciones de correo](./media/mail-settings-config.png "configuración de las opciones de correo")  

  >[!NOTE]
  >Para cambiar el campo **Desde la dirección de correo** a un dominio propio, siga las instrucciones que se indican [aquí](https://mandrill.zendesk.com/hc/articles/205582277-How-do-I-add-DNS-records-for-my-sending-domains-).
  
2.  Puede usar **Diseño del correo electrónico** para usar un archivo .html para personalizar y diseñar los mensajes de correo electrónico enviados desde el sistema. El archivo .html que use como plantilla debe incluir lo siguiente:  
  
    -   Todas las CSS de plantilla deben estar alineadas en la plantilla.  
  
    -   La plantilla debe tener tres marcadores de posición no modificables:  
  
         %%logo%%: dirección URL que lleva al logotipo de la empresa que se ha cargado en la página de configuración General.  
  
         %%title%%: marcador de posición del título del correo electrónico, según lo establecido por la directiva.  

         %%content%%: marcador de posición del contenido que se incluirá para los usuarios finales, según lo establecido por la directiva.  
     
3.  Haga clic en **Cargar una plantilla...** y seleccione el archivo que ha creado. 

4. Luego, haga clic en **Enviar un correo electrónico de prueba** para enviarse a sí mismo un mensaje de prueba para ver un ejemplo de la plantilla creada. El correo se enviará a la cuenta usada para iniciar sesión en el portal. En el correo de prueba podrá ver los campos de metadatos, la plantilla, el asunto del correo, el título en el cuerpo del correo y el contenido.  Esta es una plantilla de correo de ejemplo: 



```html
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
  

  
  

  
    
## <a name="see-also"></a>Consulte también  
[Configurar Cloud Discovery](set-up-cloud-discovery.md)   
[Para obtener soporte técnico, visite la página de soporte técnico asistido de Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Los clientes Premier también pueden elegir Cloud App Security directamente desde el Portal Premier.](https://premier.microsoft.com/)  
  
  