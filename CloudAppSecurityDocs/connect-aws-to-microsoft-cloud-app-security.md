---
title: Conectar AWS con Cloud App Security para la visibilidad y el control del uso | Microsoft Docs
description: "En este tema se proporciona información sobre cómo conectar la aplicación AWS con Cloud App Security mediante el conector de API."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 3/19/2017
ms.topic: get-started-article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: a6b4c745-cd5c-4458-819c-80cbe8b25f29
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 68d4c221626706ca641a5d3e1986da543771561a
ms.sourcegitcommit: 0d4748ea2a71e6ee2b0fa1c0498d9219bfbda29a
translationtype: HT
---
# <a name="connect-aws-to-microsoft-cloud-app-security"></a>Conectar AWS con Microsoft Cloud App Security
En esta sección se proporcionan instrucciones para conectar Cloud App Security con una cuenta de Amazon Web Services existente mediante las API del conector.  
  
## <a name="how-to-connect-amazon-web-services-to-cloud-app-security"></a>Cómo conectar Amazon Web Services con Cloud App Security  
  
1.  En la [consola de Amazon Web Services](https://console.aws.amazon.com/), en **Security, Identity & Compliance** (Seguridad, identidad y cumplimiento), haga clic en **IAM**.  
  
     ![identidad y acceso de AWS](./media/aws-identity-and-access.png "identidad y acceso de AWS")  
  
2.  Haga clic en la pestaña **Usuarios** y, después, en **Agregar usuario**.  
  
     ![usuarios de AWS](./media/aws-users.png "usuarios de AWS")      
  
4.  En el paso **Detalles**, proporcione un nombre de usuario nuevo para Cloud App Security, asegúrese de que en **Tipo de acceso** selecciona **Acceso mediante programación** y haga clic en **Next Permissions** (Siguiente: permisos).  

     ![crear usuario de AWS](./media/aws-create-user.png "crear usuario de AWS")

5. En el paso **Permisos**, seleccione **Attach existing policies directly** (Adjuntar las directivas existentes directamente) y haga clic en **Crear directiva**.

   ![asociar directiva de usuario de AWS](./media/aws-attach-user-policy.png "asociar directiva existente de AWS")

6.  En **Crear directiva**, seleccione **Create Your Own Policy** (Crear su propia directiva).
 
    ![crear su propia directiva de AWS](./media/aws-create-own-policy.png "crear directiva de AWS")
 
7.  En **Revisar directiva**, proporcione un **Nombre de directiva**, por ejemplo, CloudAppSecurityPolicy.

    ![revisar directiva de AWS](./media/aws-review-policy.png "revisar directiva de AWS")

8. Después, pegue lo siguiente en el campo **Policy Document** (Documento de directiva) y haga clic en **Crear directiva**:
  
    ```     
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
            "iam:Get*"  
          ],  
          "Effect" : "Allow",  
          "Resource" : "*"  
        }  
      ]  
     }  
  
    ```  
  
9. De nuevo en la pantalla **Agregar usuario**, actualice la lista si es necesario, seleccione el usuario que acaba de crear y haga clic en **Next Review** (Siguiente: revisión).

   ![revisar directiva de usuario de AWS](./media/aws-review-user.png "revisar directiva de usuario de AWS")

10. Si todos los detalles son correctos, haga clic en **Crear usuario**.

    ![permisos de usuario AWS](./media/aws-user-permissions.png "revisar permisos de usuario de AWS")

11. Cuando obtenga el mensaje de operación correcta, haga clic en **Descargar CSV** para guardar una copia de las credenciales del nuevo usuario, ya que las necesitará más adelante.  

    ![descargar CSV de AWS](./media/aws-download-csv.png "descargar CSV de AWS")
  
10. En la consola AWS, haga clic en **Servicios** y, en **Herramientas de administración**, haga clic en **CloudTrail**.  
  
     ![CloudTrail de AWS](./media/aws-cloudtrail.png "CloudTrail de AWS")  
  
    Si no ha usado nunca CloudTrail, haga clic en **Iniciar** y configúrelo. Para ello, proporcione un nombre, seleccione el depósito de S3 adecuado y haga clic en **Activar**. Para asegurarse de que tiene una cobertura completa, establezca **Apply to all regions** (Aplicar a todas las regiones) en **Sí**.
  
       ![activar CloudTrail de AWS](./media/aws-turnon-cloudtrail.png "activar CloudTrail de AWS")
  
    Verá el nuevo nombre de CloudTrail en la lista **Trails** (Seguimientos).
    
      ![lista de CloudTrail de AWS](./media/aws-cloudtrail-list.png "lista de CloudTrail de AWS")
  
11. En el portal de Cloud App Security, haga clic en **Investigar** y, después, en **Aplicaciones conectadas**.  
  
12. En la página **Conectores de aplicaciones**, haga clic en el botón del signo más y, después, en **AWS**.  
  
     ![conectar AWS](./media/connect-aws.png "conectar AWS")  
  
13. En el elemento emergente, pegue la **clave de acceso** y la **clave secreta** del archivo CSV en los campos correspondientes y haga clic en **Conectar**.  
   ![conectar aplicación de AWS](./media/aws-connect-app.png "AWS connect app") 
  
14. Haga clic en **Probar API** para confirmar que la conexión se ha realizado correctamente.  
  
     La prueba puede tardar unos minutos. Cuando haya finalizado, recibirá una notificación que le indicará si se ha realizado correcta o incorrectamente. Cuando reciba la notificación de que se ha realizado correctamente, haga clic en **Listo**.  
  
Después de conectar AWS, recibirá eventos de los siete días previos a la conexión, a menos que acabe de habilitar CloudTrail, en cuyo caso recibirá eventos a partir del momento en que habilitó CloudTrail.
  
## <a name="see-also"></a>Consulte también  
[Controlar las aplicaciones en la nube con directivas](control-cloud-apps-with-policies.md)   
[Para obtener soporte técnico, visite la página de soporte técnico asistido de Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Los clientes Premier también pueden elegir Cloud App Security directamente desde el Portal Premier.](https://premier.microsoft.com/)  
  
  