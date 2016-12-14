---
title: Conectar AWS | Microsoft Docs
description: "En este tema se proporciona información sobre cómo conectar la aplicación AWS con Cloud App Security mediante el conector de API."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 10/15/2016
ms.topic: get-started-article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: a6b4c745-cd5c-4458-819c-80cbe8b25f29
ms.reviewer: reutam
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 6beb9041b338406fb5b16f4bd045dbdc4592c6d9
ms.openlocfilehash: a56257b7c149c3ea054f200ef88df0ab41b7e25b


---

# <a name="connect-aws-to-microsoft-cloud-app-security"></a>Conectar AWS con Microsoft Cloud App Security
En esta sección se proporcionan instrucciones para conectar Cloud App Security con una cuenta de Amazon Web Services existente mediante las API del conector.  
  
## <a name="how-to-connect-amazon-web-services-to-cloud-app-security"></a>Cómo conectar Amazon Web Services con Cloud App Security  
  
1.  En la consola de Amazon Web Services, haga clic en **Administración de identidad y acceso**.  
  
     ![identidad y acceso de AWS](./media/aws-identity-and-access.png "aws identity and access")  
  
2.  Haga clic en la pestaña **Usuarios**.  
  
     ![usuarios de AWS](./media/aws-users.png "aws users")  
  
3.  Haga clic en **Crear nuevos usuarios**.  
  
     ![crear usuario de AWS](./media/aws-create-user.png "AWS create user")  
  
4.  Cree un usuario para Cloud App Security y asegúrese de que está activada la casilla **Generate an access key for each user** (Generar una clave de acceso para cada usuario).  
  
5.  Haga clic en **Download Credentials** (Descargar credenciales).  
  
     ![descargar credenciales de AWS](./media/aws-dl-cred.png "aws dl cred")  
  
6.  En la pestaña **Permisos**, haga clic en **Attach Policy** (Adjuntar directiva).  
  
     ![asociar directiva de usuario de AWS](./media/aws-attach-user-policy.png "aws attach user policy")  
  
7.  Se abre la pantalla **Revisar directiva**.
 
     ![revisar directiva](./media/aws-review-policy.png "aws review policy")  
  

8. En **Nombre de directiva**, escriba "AdallomTrustPolicy". 
10. En **Policy Document** (Documento de directiva), copie y pegue lo siguiente:  
  
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
  
9. En el archivo descargado `credentials.csv`, busque las credenciales del usuario nuevo. Más adelante deberá copiarlas.  
  
10. Vuelva a la página principal de la consola de AWS y en la esquina superior derecha seleccione la región principal en la ventana desplegable. Después, haga clic en **CloudTrail** en el menú principal.  
  
     ![CloudTrail de AWS](./media/aws-cloudtrail.png "aws cloudtrail")  
  
    1.  Si no ha usado nunca CloudTrail para esta región, haga clic en el botón **Iniciar** y configúrelo seleccionando el depósito de S3 adecuado.  
  
         Haga clic en la pestaña **Configuración** en la parte superior izquierda de la pantalla. En **Configuración adicional**, haga clic en el icono de edición.  
  
         ![Configuración de CloudTrail de AWS](./media/aws-cloudtrail-config.png "aws cloudtrail config")  
  
    2.  Haga clic en **Sí** cuando se le pregunte si quiere **Include global services** (Incluir servicios globales) y haga clic en **Guardar**. Esto solo se aplica a la región que ha seleccionado.  
  
         ![incluir servicios globales de AWS](./media/aws-include-global-svc.png "aws include global svc")  
  
    3.  Repita el paso 11 para todas las regiones, pero no establezca ninguna otra región para que incluya servicios globales.  
  
11. En el portal de Cloud App Security, haga clic en **Investigar** y, después, en **Aplicaciones conectadas**.  
  
12. En la página **Conectores de aplicaciones**, haga clic en el botón del signo más y, después, en **AWS**.  
  
     ![conectar AWS](./media/connect-aws.png "connect AWS")  
  
13. En el elemento emergente, pegue la **clave de acceso** y la **clave secreta** del archivo csv en los campos de la página de la API y haga clic en **Actualizar clave de acceso**.  
  
14. Haga clic en **Probar API** para confirmar que la conexión se ha realizado correctamente.  
  
     La prueba puede tardar unos minutos. Cuando haya finalizado, recibirá una notificación que le indicará si se ha realizado correcta o incorrectamente. Cuando reciba la notificación de que se ha realizado correctamente, haga clic en **Listo**.  
  
Después de conectar AWS, recibirá eventos de 7 días anteriores a la conexión.
  
## <a name="see-also"></a>Consulte también  
[Controlar las aplicaciones en la nube con directivas](control-cloud-apps-with-policies.md)   
[Para obtener soporte técnico, visite la página de soporte técnico asistido de Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Los clientes Premier también pueden elegir Cloud App Security directamente desde el Portal Premier.](https://premier.microsoft.com/)  
  
  


<!--HONumber=Nov16_HO5-->


