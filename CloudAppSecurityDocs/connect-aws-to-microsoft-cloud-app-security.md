---
title: Conectar AWS con Cloud App Security para la visibilidad y el control del uso | Microsoft Docs
description: En este tema se proporciona información sobre cómo conectar la aplicación AWS con Cloud App Security mediante el conector de API.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 4/22/2018
ms.topic: get-started-article
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: a6b4c745-cd5c-4458-819c-80cbe8b25f29
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 64c3ac8cea662aa1eab69f46f5d226bc585e5e83
ms.sourcegitcommit: 45311f2cafef79483e40d971a4c61c7673834d96
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2018
---
*Se aplica a: Microsoft Cloud App Security*

# <a name="connect-aws-to-microsoft-cloud-app-security"></a>Conectar AWS con Microsoft Cloud App Security
En esta sección se ofrecen instrucciones para conectar Microsoft Cloud App Security con una cuenta de Amazon Web Services existente mediante las API del conector.  
  
## <a name="how-to-connect-amazon-web-services-to-cloud-app-security"></a>Cómo conectar Amazon Web Services con Cloud App Security  
  
1.  En la [consola de Amazon Web Services](https://console.aws.amazon.com/), en **Security, Identity & Compliance** (Seguridad, identidad y cumplimiento), haga clic en **IAM**.  
  
     ![AWS Identity and Access](./media/aws-identity-and-access.png "AWS Identity and Access")  
  
2.  Haga clic en la pestaña **Usuarios** y, después, en **Agregar usuario**.  
  
     ![Usuarios de AWS](./media/aws-users.png "Usuarios de AWS")      
  
4.  En el paso **Detalles**, proporcione un nuevo nombre de usuario para Cloud App Security. Asegúrese de que, en **Tipo de acceso**, selecciona **Acceso mediante programación** y, después, haga clic en **Next Permissions** (Permisos siguientes).  

     ![Crear usuario en AWS](./media/aws-create-user.png "Crear usuario en AWS")

5. Haga clic en la pestaña JSON:

     ![JSON de AWS](./media/aws-json.png "Pestaña JSON de AWS")

6. Pegue el siguiente script en el área proporcionada:

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

     ![Código de AWS](./media/aws-code.png "Código de AWS")
    
6. Haga clic en **Revisar directiva**.

7. Proporcione un **Nombre** y haga clic en **Crear directiva**.

     ![Directiva de nombre de AWS](./media/aws-create-policy.png "Crear directiva de AWS")

9. De nuevo en la pantalla **Agregar usuario**, actualice la lista si es necesario, seleccione el usuario que ha creado y haga clic en **Next Review** (Revisión siguiente).

   ![Revisar directiva de usuario en AWS](./media/aws-review-user.png "Revisar usuario en AWS")

10. Si todos los detalles son correctos, haga clic en **Crear usuario**.

    ![Permisos de usuario en AWS](./media/aws-user-permissions.png "Revisar permisos de usuario en AWS")

11. Cuando obtenga el mensaje de operación correcta, haga clic en **Descargar CSV** para guardar una copia de las credenciales del nuevo usuario, ya que las necesitará más adelante.  

    ![Descargar CSV en AWS](./media/aws-download-csv.png "Descargar CSV en AWS")
  
10. En la consola AWS, haga clic en **Servicios** y, en **Herramientas de administración**, haga clic en **CloudTrail**.  
  
     ![AWS CloudTrail](./media/aws-cloudtrail.png "AWS CloudTrail")  
  
    Si no ha usado nunca CloudTrail, haga clic en **Iniciar** y configúrelo. Para ello, proporcione un nombre, seleccione el depósito de S3 adecuado y haga clic en **Activar**. Para asegurarse de que tiene una cobertura completa, establezca **Apply to all regions** (Aplicar a todas las regiones) en **Sí**.
  
       ![Activar CloudTrail en AWS](./media/aws-turnon-cloudtrail.png "Activar CloudTrail en AWS")
  
    Verá el nuevo nombre de CloudTrail en la lista **Trails** (Seguimientos).
    
      ![Lista de CloudTrail en AWS](./media/aws-cloudtrail-list.png "Lista de CloudTrail en AWS")
  
11. En el portal de Cloud App Security, haga clic en **Investigar** y, después, en **Aplicaciones conectadas**.  
  
12. En la página **Conectores de aplicaciones**, haga clic en el botón del signo más y, después, en **AWS**.  
  
     ![conectar AWS](./media/connect-aws.png "conectar AWS")  
  
13. En el elemento emergente, pegue la **clave de acceso** y la **clave secreta** del archivo CSV en los campos correspondientes y haga clic en **Conectar**.  
   ![Conectar aplicación de AWS](./media/aws-connect-app.png "Conectar aplicación de AWS") 
  
14. Haga clic en **Probar API** para confirmar que la conexión se ha realizado correctamente.  
  
     La prueba puede tardar unos minutos. Cuando haya finalizado, recibirá una notificación que le indicará si se ha realizado correcta o incorrectamente. Cuando reciba la notificación de que se ha realizado correctamente, haga clic en **Listo**.  
  
Después de conectar AWS, recibirá eventos de siete días anteriores a la conexión. Si solo ha habilitado CloudTrail, en cuyo caso recibirá los eventos desde el momento en que habilitó CloudTrail.
  
## <a name="see-also"></a>Consulte también  
[Controlar las aplicaciones en la nube con directivas](control-cloud-apps-with-policies.md)   

[Los clientes Premier también pueden elegir Cloud App Security directamente desde el Portal Premier.](https://premier.microsoft.com/)  
  
  