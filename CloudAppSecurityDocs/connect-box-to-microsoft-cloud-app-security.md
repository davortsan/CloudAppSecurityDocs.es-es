---
title: Conectar Box con Microsoft Cloud App Security | Microsoft Docs
description: "En este tema se proporciona información sobre cómo conectar la aplicación Box con Cloud App Security mediante el conector de API."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 10/15/2016
ms.topic: get-started-article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: b3e4713e-986f-4a5e-9fcc-f8de94dd0df7
ms.reviewer: reutam
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: ed4ea71b24767d3602d40894d1cbac7447bcd8a2
ms.openlocfilehash: 849408f84e2a80022623c11f7951e921a95625b6


---

# <a name="connect-box-to-microsoft-cloud-app-security"></a>Conectar Box con Microsoft Cloud App Security
En esta sección se proporcionan instrucciones para conectar Cloud App Security con una cuenta de Box existente mediante las API del conector de aplicaciones.  
  
## <a name="how-to-connect-box-to-cloud-app-security"></a>Cómo conectar Box con Cloud App Security  
  
> [!NOTE]  
>  Si se implementa con una cuenta que no es una cuenta de administrador, se producirá un error en la prueba de la API y no se permitirá a Cloud App Security analizar todos los archivos de Box. Si esto supone un problema, puede implementar con un coadministrador con todos los privilegios verificados, aunque la prueba de la API seguirá generando un error y no se analizarán los archivos que pertenezcan a otros administradores en Box.  
  
1.  Si restringe el acceso de permisos de la aplicación, siga estos pasos. De lo contrario, vaya al paso 2.  
  
    -   En la consola de administrador de Box, haga clic en el icono de configuración y luego en **Configuración empresarial**.  
  
         ![configuración empresarial de Box](./media/box-business-settings.png "box business settings")  
  
    -   Haga clic en la pestaña **Aplicaciones**.  
  
         ![aplicaciones de Box](./media/box-apps.png "box apps")  
  
    -   Si está seleccionado **Unpublished Applications** (Aplicaciones no publicadas), en el cuadro de texto **Except for** (Excepto), agregue el número de serie de la aplicación Cloud App Security: `nduj1o3yavu30dii7e03c3n7p49cj2qh` y haga clic en **Guardar**.  
  
         ![configuración del cuadro Excepto de Box](./media/box-settings-except-for.png "box settings except for")  
  
    > [!NOTE]  
    >  Si es cliente de Adallom y la dirección URL de la consola es de Adallom y no de Cloud App Security, use este número de serie de la aplicación: bwahmilhdlpbqy2ongkl119o3lrkoshc.  
  
2.  En el portal de Cloud App Security, haga clic en **Investigar** y, después, en **Aplicaciones autorizadas**.  
  
3.  En la fila de Box, haga clic en **Conectar** en la columna **Estado del conector de aplicaciones** o haga clic en el botón **Conectar una aplicación** y seleccione **Box**.  
  
     ![conectar Box](./media/connect-box.png "connect box")  
  
4.  En la página **Configuración de Box**, en la pestaña **API**, haga clic en **Siga este vínculo**.  
  
5.  Con esto se abre la página de inicio de sesión de Box. Escriba sus credenciales para permitir que Cloud App Security tenga acceso a la aplicación de Box de su equipo.  
  
6.  Box le preguntará si quiere permitir que Cloud App Security acceda a la información y el registro de actividad de su equipo y que realice actividades como cualquier miembro del equipo. Para continuar, haga clic en **Permitir**.  
  
7.  De vuelta en el portal de Cloud App Security, debería recibir un mensaje que indica que Box se ha conectado correctamente.  
  
8.  Haga clic en **Probar API** para confirmar que la conexión se ha realizado correctamente.  
  
     La prueba puede tardar unos minutos. Cuando reciba la notificación de que se ha realizado correctamente, haga clic en **Cerrar**.  
  
Box ya está conectado a Cloud App Security.  
 
Después de conectar Box, recibirá eventos de 60 días anteriores a la conexión.
  
Después de conectar Box, Cloud App Security realiza un examen completo. En función del número de archivos y los usuarios que tenga, el examen podría tardar en completarse. Para habilitar el examen prácticamente en tiempo real, los archivos en los que se detecta actividad se mueven al principio de la cola de examen. Por ejemplo, si un archivo se está editando, actualizando o compartiendo, se analiza de inmediato y no espera a que lo alcance el proceso de examen normal. Esto no se aplica a los archivos que no se modifican de forma intrínseca, por ejemplo, los archivos que se ven, se consultan en vista previa, se imprimen o se exportan.
  
## <a name="see-also"></a>Consulte también  
[Controlar las aplicaciones en la nube con directivas](control-cloud-apps-with-policies.md)   
[Para obtener soporte técnico, visite la página de soporte técnico asistido de Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Los clientes Premier también pueden elegir Cloud App Security directamente desde el Portal Premier.](https://premier.microsoft.com/)  
  
  


<!--HONumber=Oct16_HO4-->


