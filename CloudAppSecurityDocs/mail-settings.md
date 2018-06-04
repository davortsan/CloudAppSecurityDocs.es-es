---
title: Establecimiento de preferencias de notificación de correo electrónico | Microsoft Docs
description: En este artículo se proporciona información sobre cómo personalizar las notificaciones de correo electrónico que Cloud App Security envía.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 5/29/2018
ms.topic: get-started-article
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 8402cdc9-4969-4150-b567-ccc9d75e5370
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 6d19e90b8eda14868f1b25e6d9a776b030aeedbd
ms.sourcegitcommit: af8fad9709171b200699ca1ed513e2831826ed7e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/04/2018
ms.locfileid: "34568431"
---
*Se aplica a: Microsoft Cloud App Security*


##  <a name="mailsettings"></a> Establecimiento de preferencias de notificación de correo electrónico  

Para establecer los parámetros de las notificaciones de correo enviadas desde Microsoft Cloud App Security a los administradores que solicitan alertas, así como de las notificaciones enviadas a los usuarios finales sobre infracciones en las que puedan haber participado, siga este procedimiento. Para obtener información sobre la dirección IP del servidor de correo electrónico de Microsoft Cloud App Security que debe incluir en la lista de permitidos del servicio de correo electrónico no deseado, vea [Requisitos de red](network-requirements.md). 


1. En la barra de menús, haga clic en el engranaje de configuración ![icono de configuración](./media/settings-icon.png "settings icon"), seleccione **Configuración** y, después, seleccione la pestaña **Configuración de correo electrónico**.  

   ![configuración de correo](./media/mail-settings-config.png)

2. En **Identidad del emisor de correo electrónico**: si va a utilizar la configuración de correo electrónico predeterminada, no necesita cambiar nada en esta sección. Si quiere personalizar la identidad del remitente de correo electrónico, puede aplicar cualquiera de las opciones que se indican a continuación para personalizar el campo que quiera modificar. Puede cambiar todas estas opciones o alguna de ellas: **Nombre para mostrar del campo Desde**, **Dirección de correo electrónico del campo Desde**, **Dirección de correo electrónico del campo Responder a**. Microsoft Cloud App Security lo realiza automáticamente mediante el uso de un servicio de correo de terceros llamado MailChimp®. Asegúrese de revisar y aceptar los términos de servicio y la declaración de privacidad de MailChimp para permitirlo; en caso contrario, Microsoft Cloud App Security enviará las notificaciones con la configuración predeterminada.
   
   > [!NOTE]
   > Solo se admiten caracteres Unicode en el nombre para mostrar y la dirección de correo electrónico de conformidad con el [estándar rfc822](http://www.rfc-editor.org/rfc/rfc822.txt).

  
3. Puede usar **Diseño del correo electrónico** para usar un archivo .html para personalizar y diseñar los mensajes de correo electrónico enviados desde el sistema. El archivo .html que use como plantilla debe incluir lo siguiente:  
  
   -   Todos los archivos CSS de plantilla deben estar alineados en la plantilla.  
  
   -   La plantilla debe tener tres marcadores de posición no modificables:  
  
        %%logo%%: dirección URL que lleva al logotipo de la empresa que se ha cargado en la página de configuración General.  
  
        %%title%%: marcador de posición del título del correo electrónico, según lo establecido por la directiva.  

        %%content%%: marcador de posición del contenido que se incluirá para los usuarios finales, según lo establecido por la directiva.  
     
4. Haga clic en **Cargar una plantilla...** y seleccione el archivo que ha creado. 

5. Luego, haga clic en **Enviar un correo electrónico de prueba** para enviarse a sí mismo un mensaje de prueba para ver un ejemplo de la plantilla creada. El correo se enviará a la cuenta usada para iniciar sesión en el portal. En el correo de prueba podrá ver los campos de metadatos, la plantilla, el asunto del correo, el título en el cuerpo del correo y el contenido.  Esta es una plantilla de correo de ejemplo: 



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

[Los clientes Premier también pueden elegir Cloud App Security directamente desde el Portal Premier.](https://premier.microsoft.com/)  
  
  