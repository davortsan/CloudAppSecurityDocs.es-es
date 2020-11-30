---
title: Conectar Amazon Web Services con Cloud App Security
description: En este artículo se proporciona información sobre cómo conectar la aplicación de AWS con Cloud App Security mediante el conector de API para la visibilidad y el control del uso.
ms.date: 06/24/2020
ms.topic: how-to
ms.openlocfilehash: a6ca3938c93e9b1eda2bd518c48443bbad46ad70
ms.sourcegitcommit: d87372b47ca98e942c2bf94032a6a61902627d69
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/30/2020
ms.locfileid: "96313294"
---
# <a name="connect-aws-to-microsoft-cloud-app-security"></a>Conectar AWS con Microsoft Cloud App Security

[!INCLUDE [Banner for top of topics](includes/banner.md)]

En este artículo se proporcionan instrucciones para conectar su cuenta de Amazon Web Services (AWS) existente a Microsoft Cloud App Security mediante las API del conector. Para obtener información sobre cómo Cloud App Security protege AWS, consulte [protección](protect-aws.md)de AWS.

Puede conectar uno o ambos de los siguientes AWS a Cloud App Security conexiones:

- **Auditoría de seguridad**: esta conexión le proporciona visibilidad y control sobre el uso de aplicaciones de AWS.
- **Configuración de seguridad**: esta conexión ofrece recomendaciones de seguridad fundamentales basadas en la prueba comparativa del centro de seguridad de Internet (CIS) para AWS.

Dado que puede Agregar una o ambas conexiones, los pasos de este artículo se escriben como instrucciones independientes. Si ya ha agregado una de las conexiones, si procede, edite las configuraciones existentes.

## <a name="how-to-connect-aws-security-auditing-to-cloud-app-security"></a>Cómo conectar la auditoría de seguridad de AWS a Cloud App Security

Siga los pasos que se indican a continuación para configurar la auditoría de AWS y conectarla a Cloud App Security.

### <a name="step-1-configure-amazon-web-services-auditing"></a>Paso 1: configurar la auditoría de Amazon Web Services

1. En la [consola de Amazon Web Services](https://console.aws.amazon.com/), en **seguridad, identidad & cumplimiento**, haga clic en **IAM**.

    ![Identidad y acceso de AWS](media/aws-identity-and-access.png "Identidad y acceso de AWS")

1. Seleccione **usuarios** y, a continuación, haga clic en **Agregar usuario**.

    ![Usuarios de AWS](media/aws-users.png "Usuarios de AWS")

1. En el paso **Detalles**, proporcione un nuevo nombre de usuario para Cloud App Security. Asegúrese de que en **tipo de acceso** seleccione **acceso mediante programación** y haga clic en **permisos siguientes**.<a name="set-permissions"></a>

    ![Crear usuario en AWS](media/aws-create-user.png "Crear usuario en AWS")

1. Haga clic en la pestaña **JSON** :

    ![Pestaña JSON de AWS](media/aws-json.png "Pestaña JSON de AWS")

1. Pegue el siguiente script en el área proporcionada:

    ```json
    {
      "Version" : "2012-10-17",
      "Statement" : [{
          "Action" : [
            "cloudtrail:DescribeTrails",
            "cloudtrail:LookupEvents",
            "cloudtrail:GetTrailStatus",
            "cloudwatch:Describe*",
            "cloudwatch:Get*",
            "cloudwatch:List*",
            "iam:List*",
            "iam:Get*",
            "s3:ListAllMyBuckets",
            "s3:PutBucketAcl",
            "s3:GetBucketAcl",
            "s3:GetBucketLocation"
          ],
          "Effect" : "Allow",
          "Resource" : "*"
        }
      ]
     }
    ```

     ![Código AWS](media/aws-code.png "Código AWS")

1. Haga clic en **Review policy** (Revisar directiva).

1. Proporcione un **Nombre** y haga clic en **Crear directiva**.

    ![Proporcionar el nombre de la Directiva de AWS](media/aws-create-policy.png "Proporcionar el nombre de la Directiva de AWS")

1. De nuevo en la pantalla **Agregar usuario**, actualice la lista si es necesario, seleccione el usuario que ha creado y haga clic en **Next Review** (Revisión siguiente).

    ![Asociación de una directiva existente en AWS](media/aws-attach-policy.png "Asociación de una directiva existente en AWS")

1. Si todos los detalles son correctos, haga clic en **Crear usuario**.

    ![Permisos de usuario en AWS](media/aws-user-permissions.png "Revisar los permisos de usuario en AWS")

1. Cuando obtenga el mensaje de operación correcta, haga clic en **Descargar CSV** para guardar una copia de las credenciales del nuevo usuario, ya que las necesitará más adelante.

    ![Descargar CSV en AWS](media/aws-download-csv.png "Descargar CSV en AWS")

1. En la consola AWS, haga clic en **Servicios** y, en **Herramientas de administración**, haga clic en **CloudTrail**.

    ![AWS CloudTrail](media/aws-cloudtrail.png "AWS CloudTrail")

    Si no ha usado nunca CloudTrail, haga clic en **Iniciar** y configúrelo. Para ello, proporcione un nombre, seleccione el depósito de S3 adecuado y haga clic en **Activar**. Para asegurarse de que tiene una cobertura completa, establezca **Apply to all regions** (Aplicar a todas las regiones) en **Sí**.

    ![Activar CloudTrail en AWS](media/aws-turnon-cloudtrail.png "Activar CloudTrail en AWS")

    Verá el nuevo nombre de CloudTrail en la lista **Trails** (Seguimientos).

    ![Lista de CloudTrail en AWS](media/aws-cloudtrail-list.png "Lista de CloudTrail en AWS")

    > [!NOTE]
    > Después de conectarse a AWS, recibirá eventos de siete días anteriores a la conexión. Si acaba de habilitar CloudTrail, recibirá eventos a partir del momento en que habilitó CloudTrail.

### <a name="step-2-connect-amazon-web-services-auditing-to-cloud-app-security"></a>Paso 2: conectar Amazon Web Services auditoría a Cloud App Security

1. En el portal de Cloud App Security, haga clic en **Investigar** y, después, en **Aplicaciones conectadas**.

1. En la página **conectores de aplicaciones** , para proporcionar las credenciales del conector de AWS, realice una de las acciones siguientes:

    **Para un nuevo conector**

    1. Haga clic en el signo más seguido de **Amazon Web Services**.

        ![conexión de la auditoría de AWS](media/connect-aws.png "conectar AWS")

    1. En el elemento emergente, proporcione un nombre para el conector y, a continuación, haga clic en **conectar Amazon Web Services**.

        ![Nombre del conector de auditoría de AWS](media/connect-aws-name.png)

    1. En la página conectar Amazon Web Services, seleccione **Auditoría de seguridad**, pegue la **clave de acceso** y la **clave secreta** del archivo. csv en los campos correspondientes y haga clic en **conectar**.

        ![Conexión de la auditoría de seguridad de aplicaciones AWS para nuevo conector](media/aws-connect-app-audit.png "Conexión de la auditoría de seguridad de aplicaciones AWS")

    **Para un conector existente**

    1. En la lista de conectores, en la fila en la que aparece el conector de AWS, haga clic en **conectar auditoría de seguridad**.

        ![Captura de pantalla de la página aplicaciones conectadas, donde se muestra el vínculo editar auditoría de seguridad](media/aws-connect-app-edit-audit.png)

    1. En la página conectar Amazon Web Services, pegue la **clave de acceso** y la **clave secreta** del archivo. csv en los campos correspondientes y haga clic en **conectar**.

        ![Conexión de la auditoría de seguridad de aplicaciones AWS para el conector existente](media/aws-connect-app-edit-audit-creds.png "Conexión de la auditoría de seguridad de aplicaciones AWS")

1. Haga clic en **probar API** para asegurarse de que la conexión se ha realizado correctamente.

    La prueba puede tardar unos minutos. Cuando haya terminado, recibirá una notificación de éxito o de error. Cuando reciba la notificación de que se ha realizado correctamente, haga clic en **Listo**.

## <a name="how-to-connect-aws-security-configuration-to-cloud-app-security"></a>Cómo conectar la configuración de seguridad de AWS a Cloud App Security

La conexión de la configuración de seguridad de AWS ofrece información sobre las recomendaciones de seguridad fundamentales basadas en el benchmark Center for Internet Security (CIS) para AWS.

Siga estos pasos para conectar la configuración de seguridad de AWS a Cloud App Security.

> [!div class="checklist"]
>
> - [Configuración del centro de seguridad de AWS](#set-up-aws-security-hub)
> - [Conexión de la configuración de seguridad de AWS a Cloud App Security](#connect-aws-security-configuration-to-cloud-app-security)

### <a name="set-up-aws-security-hub"></a>Configuración del centro de seguridad de AWS

Para ver recomendaciones de seguridad para varias regiones, repita los pasos siguientes para cada región pertinente.

> [!NOTE]
> Si usa una cuenta maestra, repita estos pasos para configurar la cuenta maestra y todas las cuentas de miembro conectadas en todas las regiones pertinentes.

1. Habilite [AWS Config](https://docs.aws.amazon.com/config/latest/developerguide/gs-console.html) (Configuración de AWS).
1. Habilite [AWS Security Hub](https://docs.aws.amazon.com/securityhub/latest/userguide/securityhub-settingup.html).
1. Compruebe que hay datos que fluyen a Security Hub.

    > [!NOTE]
    > La primera vez que se habilita Security Hub, los datos pueden tardar varias horas en estar disponibles.

### <a name="connect-aws-security-configuration-to-cloud-app-security"></a>Conexión de la configuración de seguridad de AWS a Cloud App Security

Antes de poder conectar la configuración de seguridad de AWS, asegúrese de que ha [configurado el entorno de AWS](#set-up-aws-security-hub) para recopilar recomendaciones fundamentales de seguridad y cumplimiento.

> [!NOTE]
> Si usa una [cuenta maestra de AWS](https://aws.amazon.com/security-hub/faqs/), siga estos pasos para conectar la cuenta maestra. La conexión de su cuenta maestra le permite recibir recomendaciones para todas las cuentas de miembro en todas las regiones.

### <a name="step-1-configure-amazon-web-services-security-configuration"></a>Paso 1: configurar la configuración de seguridad de Amazon Web Services

1. Siga los pasos de *Auditoría de seguridad de AWS* para llegar a la página de [permisos](#set-permissions) .

1. En la página permisos, haga clic en **asociar directivas existentes directamente**, aplique las directivas **AWSSecurityHubReadOnlyAccess** y **SecurityAudit** y, a continuación, haga clic en **etiquetas siguientes**.

    ![Asociación de una directiva existente en AWS](media/aws-attach-policy.png "Asociación de una directiva existente en AWS")

1. Opcional: agregar etiquetas al usuario.

    ![Agregar etiquetas al usuario en AWS](media/aws-add-tags.png)

    > [!NOTE]
    > Agregar etiquetas al usuario no afectará a la conexión.

1. Haga clic en **siguiente revisión**.

1. Si todos los detalles son correctos, haga clic en **Crear usuario**.

    ![Permisos de usuario en AWS](media/aws-user-permissions.png "Revisar los permisos de usuario en AWS")

1. Cuando obtenga el mensaje de operación correcta, haga clic en **download. csv** para guardar una copia del identificador de la **clave de acceso** y la **clave de acceso secreta**.

    ![Descargar CSV en AWS](media/aws-download-csv.png "Descargar CSV en AWS")

### <a name="step-2-connect-amazon-web-services-security-configuration-to-cloud-app-security"></a>Paso 2: conectar Amazon Web Services configuración de seguridad a Cloud App Security

1. En Cloud App Security, haga clic en **investigar** y, a continuación, seleccione **aplicaciones conectadas**.

1. En la pestaña **aplicaciones de configuración de seguridad** , haga clic en el botón más y, a continuación, seleccione **Amazon Web Services**.

    ![conexión de la configuración de seguridad de AWS](media/connect-aws-security-configuration.png)

1. En la página **nombre de instancia** , elija el tipo de instancia y, a continuación, haga clic en **siguiente**.

    - Para un conector existente, elija la instancia pertinente.

        ![Selección de instancia de AWS](media/connect-aws-existing-instance.png)

    - Para un nuevo conector, proporcione un nombre para la instancia.

        ![Nombre del conector de configuración de seguridad de AWS](media/aws-connect-name.png)

1. En la **página Detalles** de la cuenta, pegue la **clave de acceso** y la **clave secreta** del archivo. csv en los campos correspondientes y, a continuación, haga clic en **siguiente**.

    ![Conexión de los detalles de la cuenta de AWS](media/aws-connect-account-details.png)

1. En la página **finalizado** , asegúrese de que la conexión se ha realizado correctamente y, a continuación, haga clic en **finalizado**.

Si tiene problemas para conectar la aplicación, consulte [solución de problemas de conectores de aplicaciones](troubleshooting-api-connectors-using-error-messages.md).

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Controlar las aplicaciones en la nube con directivas](control-cloud-apps-with-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]
