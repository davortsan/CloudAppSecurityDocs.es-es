---
title: " Establecimiento de preferencias de notificación de correo electrónico"
description: En este artículo se proporciona información sobre cómo personalizar las notificaciones de correo electrónico que Cloud App Security envía.
ms.date: 2/4/2019
ms.topic: how-to
ms.openlocfilehash: e98a587f78892d255736f3c2328ac0ae195c725d
ms.sourcegitcommit: d87372b47ca98e942c2bf94032a6a61902627d69
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/30/2020
ms.locfileid: "96315045"
---
# <a name="email-notification-preferences"></a>Preferencias de notificación de correo electrónico

[!INCLUDE [Banner for top of topics](includes/banner.md)]

En este artículo se proporciona información sobre cómo personalizar las notificaciones de correo electrónico que Cloud App Security envía a los usuarios cuando se detecta una infracción de seguridad.

> [!NOTE]
> Esta personalización solo afecta a las notificaciones enviadas a los usuarios finales, no a las que se envían a los administradores de Cloud App Security.

## <a name="set-email-notification-preferences"></a><a name="mailsettings"></a> Establecimiento de preferencias de notificación de correo electrónico

 Microsoft Cloud App Security permite personalizar las notificaciones de correo electrónico enviadas a los usuarios finales implicados en las infracciones de seguridad. Para establecer los parámetros para las notificaciones de correo electrónico, siga este procedimiento. Para obtener información sobre el Microsoft Cloud App Security dirección IP del servidor de correo electrónico que debe permitir en el servicio anti-spam, consulte [requisitos de red](network-requirements.md).

1. En la barra de menús, haga clic en el engranaje de configuración, seleccione **Configuración** y después la pestaña **Configuración de correo electrónico**.

    ![configuración de correo](media/mail-settings-config.png)

2. En **Identidad del emisor de correo electrónico**: si va a usar la configuración de correo electrónico predeterminada, no necesita cambiar nada en esta sección. Si quiere personalizar la identidad del remitente de correo electrónico, puede aplicar cualquiera de las opciones que se indican a continuación para personalizar el campo que quiera modificar. Puede cambiar todas estas opciones o alguna de ellas: **Nombre para mostrar del campo Desde**, **Dirección de correo electrónico del campo Desde**, **Dirección de correo electrónico del campo Responder a**. Microsoft Cloud App Security realiza la personalización mediante el uso de un servicio de correo de terceros llamado MailChimp &reg; . Asegúrese de revisar y aceptar los Términos de servicio y la Declaración de privacidad de MailChimp para habilitar la personalización. En caso contrario, Microsoft Cloud App Security enviará las notificaciones mediante la configuración predeterminada.

    > [!NOTE]
    > Solo se admiten caracteres Unicode en el nombre para mostrar y la dirección de correo electrónico de conformidad con el [estándar rfc822](https://www.rfc-editor.org/rfc/rfc822.txt).

3. Puede usar **Diseño del correo electrónico** para usar un archivo .html para personalizar y diseñar los mensajes de correo electrónico enviados desde el sistema. El archivo .html que use como plantilla debe incluir los siguientes elementos:

    - Todos los archivos CSS de plantilla deben estar alineados en la plantilla.

    - La plantilla debe tener tres marcadores de posición no modificables:

        - **%%logo%%**: dirección URL que lleva al logotipo de la empresa que se ha cargado en la página de configuración General.

        - **%%title%%**: marcador de posición del título del correo electrónico, según lo establecido por la directiva.

        - **%%content%%**: marcador de posición del contenido que se incluirá para los usuarios finales, según lo establecido por la directiva.

4. Haga clic en **Cargar una plantilla...** y seleccione el archivo que ha creado.

5. Haga clic en **Enviar un correo electrónico de prueba** para enviarse a su propia dirección un correo para ver un ejemplo de la plantilla creada. El correo se enviará a la cuenta usada para iniciar sesión en el portal. En el correo electrónico de prueba, verá y comprobará los siguientes elementos:
    - Los campos de metadatos
    - La plantilla
    - El asunto del correo electrónico
    - El título en el cuerpo del correo electrónico
    - El contenido

## <a name="sample-email-template"></a>Plantilla de correo electrónico de ejemplo

A continuación se muestra una plantilla de correo electrónico de ejemplo:

```html
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "https://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
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

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Configuración de Cloud Discovery](set-up-cloud-discovery.md)

[!INCLUDE [Open support ticket](includes/support.md)]
