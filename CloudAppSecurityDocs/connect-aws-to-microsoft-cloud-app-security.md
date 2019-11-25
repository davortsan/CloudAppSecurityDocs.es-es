---
title: Connect Amazon Web Services with Cloud App Security
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
ms.openlocfilehash: 387a9a9184bb805db7659d6f67eae26239f812f3
ms.sourcegitcommit: 094bb42a198fe733cfd3aec79d74487672846dfa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/24/2019
ms.locfileid: "74461066"
---
# <a name="connect-aws-to-microsoft-cloud-app-security"></a>Conectar AWS con Microsoft Cloud App Security

*Se aplica a: Microsoft Cloud App Security*

This article provides instructions for connecting your existing Amazon Web Services (AWS) account to Microsoft Cloud App Security using the connector APIs.

You can connect one or both of the following AWS to Cloud App Security connections:

- **Security auditing**: This connection gives you visibility into and control over AWS app use.
- **Security configuration**: This connection gives you fundamental security recommendations based on the Center for Internet Security (CIS) benchmark for AWS.

Since you can add either or both of the connections, the steps in this article are written as independent instructions. If you have already added one of the connections, where relevant edit the existing configurations.

## <a name="how-to-connect-aws-security-auditing-to-cloud-app-security"></a>How to connect AWS Security auditing to Cloud App Security

1. In your [Amazon Web Services console](https://console.aws.amazon.com/), under **Security, Identity & Compliance**, click **IAM**.

    ![AWS identity and access](media/aws-identity-and-access.png "AWS identity and access")

1. Select **Users** and then click **Add user**.

    ![AWS users](media/aws-users.png "AWS users")

1. En el paso **Detalles**, proporcione un nuevo nombre de usuario para Cloud App Security. Make sure that under **Access type** you select **Programmatic access** and click **Next Permissions**.<a name="set-permissions"></a>

    ![Create user in AWS](media/aws-create-user.png "Create user in AWS")

1. Click on the **JSON** tab:

    ![AWS JSON tab](media/aws-json.png "AWS JSON tab")

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

     ![AWS code](media/aws-code.png "AWS code")

1. Haga clic en **Revisar directiva**.

1. Proporcione un **Nombre** y haga clic en **Crear directiva**.

    ![Provide AWS policy name](media/aws-create-policy.png "Provide AWS policy name")

1. De nuevo en la pantalla **Agregar usuario**, actualice la lista si es necesario, seleccione el usuario que ha creado y haga clic en **Next Review** (Revisión siguiente).

    ![Attach existing policy in AWS](media/aws-attach-policy.png "Attach existing policy in AWS")

1. Si todos los detalles son correctos, haga clic en **Crear usuario**.

    ![User permissions in AWS](media/aws-user-permissions.png "Review user permissions in AWS")

1. Cuando obtenga el mensaje de operación correcta, haga clic en **Descargar CSV** para guardar una copia de las credenciales del nuevo usuario, ya que las necesitará más adelante.

    ![Download csv in AWS](media/aws-download-csv.png "Download csv in AWS")

1. En la consola AWS, haga clic en **Servicios** y, en **Herramientas de administración**, haga clic en **CloudTrail**.

    ![AWS CloudTrail](media/aws-cloudtrail.png "AWS CloudTrail")

    Si no ha usado nunca CloudTrail, haga clic en **Iniciar** y configúrelo. Para ello, proporcione un nombre, seleccione el depósito de S3 adecuado y haga clic en **Activar**. Para asegurarse de que tiene una cobertura completa, establezca **Apply to all regions** (Aplicar a todas las regiones) en **Sí**.

    ![Turn on CloudTrail in AWS](media/aws-turnon-cloudtrail.png "Turn on CloudTrail in AWS")

    Verá el nuevo nombre de CloudTrail en la lista **Trails** (Seguimientos).

    ![CloudTrail list in AWS](media/aws-cloudtrail-list.png "CloudTrail list in AWS")

    > [!NOTE]
    > Después de conectarse a AWS, recibirá eventos de siete días anteriores a la conexión. If you just enabled CloudTrail, you'll receive events from the time you enabled CloudTrail.

1. En el portal de Cloud App Security, haga clic en **Investigar** y, después, en **Aplicaciones conectadas**.

1. In the **App connectors** page, to provide the AWS connector credentials, do one of the following:

    **For a new connector**

    1. Click the plus sign followed by **Amazon Web Services**.

        ![connect AWS](media/connect-aws.png "conectar AWS")

    1. In the pop-up, provide a name for the connector, and then click **Connect Amazon Web Services**.

        ![AWS connector name](media/aws-connect-name.png)

    1. On the Connect Amazon Web services page, select **Security auditing**, paste the **Access key** and **Secret key** from the .csv file into the relevant fields, and click **Connect**.

        ![Connect AWS app security auditing](media/aws-connect-app-audit.png "Connect AWS app security auditing")

    **For an existing connector**

    1. In the list of connectors, on the row in which the AWS connector appears, click **Connect security auditing**.

        ![Screenshot of the Connected Apps page, showing edit Security Auditing link](media/aws-connect-app-edit-audit.png)

    1. On the Connect Amazon Web Services page, paste the **Access key** and **Secret key** from the .csv file into the relevant fields, and click **Connect**.

        ![Connect AWS app security auditing](media/aws-connect-app-edit-audit-creds.png "Connect AWS app security auditing")

1. Haga clic en **Probar API** para asegurarse de que la conexión se ha realizado correctamente.  

    La prueba puede tardar unos minutos. Cuando haya finalizado, recibirá una notificación que le indicará si se ha realizado correcta o incorrectamente. Cuando reciba la notificación de que se ha realizado correctamente, haga clic en **Listo**.

## <a name="how-to-connect-aws-security-configuration-to-cloud-app-security"></a>How to connect AWS Security configuration to Cloud App Security

Follow the [How to connect AWS Security auditing](#how-to-connect-aws-security-auditing-to-cloud-app-security) steps to get to the [permissions](#set-permissions) page.

1. On the permissions page, click **Attach existing policies directly**, apply the **AWSSecurityHubReadOnlyAccess** and **SecurityAudit** policies, and then click **Next Tags**.

    ![Attach existing policy in AWS](media/aws-attach-policy.png "Attach existing policy in AWS")

1. Optional: Add tags to the user.

    ![Add tags to user in AWS](media/aws-add-tags.png)

    > [!NOTE]
    > Adding tags to the user won't affect the connection.

1. Click **Next Review**.

1. Si todos los detalles son correctos, haga clic en **Crear usuario**.

    ![User permissions in AWS](media/aws-user-permissions.png "Review user permissions in AWS")

1. When you get the success message, click **Download .csv** to save a copy of the **Access key ID** and the **Secret access key**, you need these later.

    ![Download csv in AWS](media/aws-download-csv.png "Download csv in AWS")

1. En el portal de Cloud App Security, haga clic en **Investigar** y, después, en **Aplicaciones conectadas**.

1. In the **App connectors** page, to provide the AWS connector credentials, do one of the following:

    **For a new connector**
    1. Click the plus sign followed by **Amazon Web Services**.<br>

        ![connect AWS](media/connect-aws.png "conectar AWS")

    1. In the pop-up, provide a name for the connector, and then click **Connect Amazon Web Services**.

        ![AWS connector name](media/aws-connect-name.png)

    1. On the Connect Amazon Web services page, select **Security configuration**, paste the **Access key** and **Secret key** from the .csv file into the relevant fields, and click **Connect**.

        ![Connect AWS app security configuration](media/aws-connect-app-config.png "Connect AWS app security configuration")

    **For an existing connector**
    1. In the list of connectors, on the row in which the AWS connector appears, click **Connect security configuration**.

        ![Screenshot of the Connected Apps page, showing edit Security Configuration link](media/aws-connect-app-edit-config.png)

    1. On the Connect Amazon Web Services page, paste the **Access key** and **Secret key** from the .csv file into the relevant fields, and click **Connect**.

        ![Connect AWS app security configuration](media/aws-connect-app-edit-config-creds.png "Connect AWS app security configuration")

1. Haga clic en **Probar API** para asegurarse de que la conexión se ha realizado correctamente.  

    La prueba puede tardar unos minutos. Cuando haya finalizado, recibirá una notificación que le indicará si se ha realizado correcta o incorrectamente. Cuando reciba la notificación de que se ha realizado correctamente, haga clic en **Listo**.

## <a name="next-steps"></a>Pasos siguientes

[Controlar las aplicaciones en la nube con directivas](control-cloud-apps-with-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]