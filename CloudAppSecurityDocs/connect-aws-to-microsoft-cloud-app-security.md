---
title: Conectar Amazon Web Services con Cloud App Security
description: En este artículo se proporciona información sobre cómo conectar la aplicación de AWS con Cloud App Security mediante el conector de API para la visibilidad y el control del uso.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 8/13/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: a6b4c745-cd5c-4458-819c-80cbe8b25f29
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 34e1c361d5b1a49093f927dfde1ae2391570b958
ms.sourcegitcommit: 254d5be2b002c5658803923aa9ef97240dcdc917
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/25/2019
ms.locfileid: "71083829"
---
# <a name="connect-aws-to-microsoft-cloud-app-security"></a>Conectar AWS con Microsoft Cloud App Security

*Se aplica a: Microsoft Cloud App Security*

En este artículo se proporcionan instrucciones para conectar su cuenta de Amazon Web Services (AWS) existente a Microsoft Cloud App Security mediante las API del conector.

Puede conectar uno o ambos de los siguientes AWS a Cloud App Security conexiones:

- **Auditoría de seguridad**: Esta conexión le ofrece visibilidad y control del uso de la aplicación de AWS.
- **Configuración de seguridad**: Esta conexión ofrece recomendaciones de seguridad fundamentales basadas en la prueba comparativa de Center for Internet Security (CIS) para AWS.

Dado que puede Agregar una o ambas conexiones, los pasos de este artículo se escriben como instrucciones independientes. Si ya ha agregado una de las conexiones, si procede, edite las configuraciones existentes.

## <a name="how-to-connect-aws-security-auditing-to-cloud-app-security"></a>Cómo conectar la auditoría de seguridad de AWS a Cloud App Security

1. En la [consola de Amazon Web Services](https://console.aws.amazon.com/), en **seguridad, identidad & cumplimiento**, haga clic en **IAM**.

    ![AWS Identity and Access](media/aws-identity-and-access.png "AWS Identity and Access")

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

     ![Código de AWS](media/aws-code.png "Código de AWS")

1. Haga clic en **Revisar directiva**.

1. Proporcione un **Nombre** y haga clic en **Crear directiva**.

    ![Proporcionar el nombre] de la Directiva de AWS (media/aws-create-policy.png "Proporcionar el nombre") de la Directiva de AWS

1. De nuevo en la pantalla **Agregar usuario**, actualice la lista si es necesario, seleccione el usuario que ha creado y haga clic en **Next Review** (Revisión siguiente).

    ![Asociación de una directiva existente en AWS](media/aws-attach-policy.png "Asociación de una directiva existente en AWS")

1. Si todos los detalles son correctos, haga clic en **Crear usuario**.

    ![Permisos de usuario en AWS](media/aws-user-permissions.png "Revisar permisos de usuario en AWS")

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

1. En el portal de Cloud App Security, haga clic en **Investigar** y, después, en **Aplicaciones conectadas**.

1. En la página **conectores de aplicaciones** , para proporcionar las credenciales del conector de AWS, realice una de las acciones siguientes:

    **Para un nuevo conector**

    1. Haga clic en el signo más seguido de **Amazon Web Services**.

        ![conectar AWS](media/connect-aws.png "conectar AWS")

    1. En el elemento emergente, proporcione un nombre para el conector y, a continuación, haga clic en **conectar Amazon Web Services**.

        ![Nombre del conector de AWS](media/aws-connect-name.png)

    1. En la página conectar Amazon Web Services, seleccione **Auditoría de seguridad**, pegue la **clave de acceso** y la **clave secreta** del archivo. csv en los campos correspondientes y haga clic en **conectar**.

        ![Conexión de la auditoría de seguridad de aplicaciones AWS](media/aws-connect-app-audit.png "Conexión de la auditoría de seguridad de aplicaciones AWS")

    **Para un conector existente**

    1. En la lista de conectores, en la fila en la que aparece el conector de AWS, haga clic en **conectar auditoría de seguridad**.

        ![Captura de pantalla de la página aplicaciones conectadas, donde se muestra el vínculo editar auditoría de seguridad](media/aws-connect-app-edit-audit.png)

    1. En la página conectar Amazon Web Services, pegue la **clave de acceso** y la **clave secreta** del archivo. csv en los campos correspondientes y haga clic en **conectar**.

        ![Conexión de la auditoría de seguridad de aplicaciones AWS](media/aws-connect-app-edit-audit-creds.png "Conexión de la auditoría de seguridad de aplicaciones AWS")

1. Haga clic en **Probar API** para confirmar que la conexión se ha realizado correctamente.  

    La prueba puede tardar unos minutos. Cuando haya finalizado, recibirá una notificación que le indicará si se ha realizado correcta o incorrectamente. Cuando reciba la notificación de que se ha realizado correctamente, haga clic en **Listo**.

## <a name="how-to-connect-aws-security-configuration-to-cloud-app-security"></a>Cómo conectar la configuración de seguridad de AWS a Cloud App Security

Siga los pasos de [Auditoría de seguridad de AWS](#how-to-connect-aws-security-auditing-to-cloud-app-security) para llegar a la página de [permisos](#set-permissions) .

1. En la página permisos, haga clic en **asociar directivas existentes directamente**, aplique las directivas **AWSSecurityHubReadOnlyAccess** y **SecurityAudit** y, a continuación, haga clic en **etiquetas siguientes**.

    ![Asociación de una directiva existente en AWS](media/aws-attach-policy.png "Asociación de una directiva existente en AWS")

1. Opcional: Agregue etiquetas al usuario.

    ![Agregar etiquetas al usuario en AWS](media/aws-add-tags.png)

    > [!NOTE]
    > Agregar etiquetas al usuario no afectará a la conexión.

1. Haga clic en **siguiente revisión**.

1. Si todos los detalles son correctos, haga clic en **Crear usuario**.

    ![Permisos de usuario en AWS](media/aws-user-permissions.png "Revisar permisos de usuario en AWS")

1. Cuando obtenga el mensaje de operación correcta, haga clic en **download. csv** para guardar una copia del identificador de la **clave de acceso** y la **clave de acceso secreta**.

    ![Descargar CSV en AWS](media/aws-download-csv.png "Descargar CSV en AWS")

1. En el portal de Cloud App Security, haga clic en **Investigar** y, después, en **Aplicaciones conectadas**.

1. En la página **conectores de aplicaciones** , para proporcionar las credenciales del conector de AWS, realice una de las acciones siguientes:

    **Para un nuevo conector**
    1. Haga clic en el signo más seguido de **Amazon Web Services**.<br>

        ![conectar AWS](media/connect-aws.png "conectar AWS")

    1. En el elemento emergente, proporcione un nombre para el conector y, a continuación, haga clic en **conectar Amazon Web Services**.

        ![Nombre del conector de AWS](media/aws-connect-name.png)

    1. En la página conectar Amazon Web Services, seleccione **configuración de seguridad**, pegue la clave de **acceso** y la **clave secreta** del archivo. csv en los campos correspondientes y haga clic en **conectar**.

        Conexión de la configuración de seguridad de la ![aplicación AWS] Conexión de la configuración de seguridad de la (media/aws-connect-app-config.png "aplicación AWS")

    **Para un conector existente**
    1. En la lista de conectores, en la fila en la que aparece el conector de AWS, haga clic en **conectar configuración de seguridad**.

        ![Captura de pantalla de la página aplicaciones conectadas, donde se muestra el vínculo Editar configuración de seguridad](media/aws-connect-app-edit-config.png)

    1. En la página conectar Amazon Web Services, pegue la **clave de acceso** y la **clave secreta** del archivo. csv en los campos correspondientes y haga clic en **conectar**.

        Conexión de la configuración de seguridad de la ![aplicación AWS] Conexión de la configuración de seguridad de la (media/aws-connect-app-edit-config-creds.png "aplicación AWS")

1. Haga clic en **Probar API** para confirmar que la conexión se ha realizado correctamente.  

    La prueba puede tardar unos minutos. Cuando haya finalizado, recibirá una notificación que le indicará si se ha realizado correcta o incorrectamente. Cuando reciba la notificación de que se ha realizado correctamente, haga clic en **Listo**.

## <a name="next-steps"></a>Pasos siguientes

[Controlar las aplicaciones en la nube con directivas](control-cloud-apps-with-policies.md)

[Los clientes Premier también pueden crear una solicitud de soporte técnico directamente en el portal Premier.](https://premier.microsoft.com/)