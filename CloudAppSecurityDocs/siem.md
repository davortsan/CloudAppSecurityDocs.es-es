---
title: "Integración de SIEM | Microsoft Docs"
description: "En este tema se proporciona información sobre la integración de SIEM con Cloud App Security."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 1/8/2017
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: 4649423b-9289-49b7-8b60-04b61eca1364
ms.reviewer: reutam
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 4ab3275bdff2ec3aae5b5069c5ae65ba4292e93d
ms.openlocfilehash: f8e3e744cd030777fe82a1edbc1197784f1ac8fa


---

# <a name="siem-integration--public-preview-"></a>Integración de SIEM, versión preliminar pública: 
    
Ahora puede integrar Cloud App Security con su servidor SIEM para habilitar la supervisión centralizada de alertas y actividades. La integración de un servicio SIEM le permite proteger mejor sus aplicaciones de nube a la vez que mantiene el flujo de trabajo de seguridad habitual, automatizando así los procedimientos de seguridad y estableciendo correlaciones entre eventos basados en la nube y eventos locales. El agente SIEM de Cloud App Security se ejecuta en el servidor y extrae las alertas y las actividades de Cloud App Security y las transmite al servidor SIEM.

Cuando integre por primera vez su SIEM con Cloud App Security, las actividades y las alertas de los dos últimos días se reenviarán al SIEM, así como todas las actividades y alertas (en función del filtro seleccionado) que se produzcan a partir de entonces. Además, si deshabilita esta característica durante un período prolongado, cuando la habilite de nuevo, se reenviarán las alertas y las actividades de los dos últimos días, así como las que se produzcan a partir de entonces.

La integración con SIEM se realiza en tres pasos:
1. Configuración en el portal de Cloud App Security 
2. Descarga del archivo JAR y ejecución en el servidor
3. Validación de que el agente SIEM funcione

## <a name="prerequisites"></a>Requisitos previos

- Servidor estándar de Windows o Linux (puede ser una máquina virtual).
- El servidor debe ejecutar Java 8; no se admiten versiones anteriores.

## <a name="integrating-with-your-siem"></a>Integración con su SIEM

### <a name="step-1-set-it-up-in-the-cloud-app-security-portal"></a>Paso 1: configuración en el portal de Cloud App Security

1. En el portal de Cloud App Security, en el engranaje Configuración, haga clic en **SIEM agents** (Agentes SIEM).

2. Haga clic en Add SIEM agent (Agregar agente SIEM) para iniciar al asistente.
3. En el asistente, haga clic en **Add SIEM agent** (Agregar agente SIEM). 
4. En el asistente, asigne un nombre, **seleccione el formato SIEM** y establezca la **Configuración avanzada** que esté relacionada con ese formato. Haga clic en **Siguiente**.

   ![Configuración general de SIEM](./media/siem1.png)

5. Escriba la dirección IP del **Host Syslog remoto** y el **Número de puerto de Syslog**. Seleccione TCP o UDP como Protocolo Syslog remoto.
Puede trabajar con el administrador de seguridad para obtener estos detalles si no los tiene.
Haga clic en **Siguiente**.
  ![Configuración remota de Syslog](./media/siem2.png)

6. Seleccione los tipos de datos, **Alertas** y **Actividades** que quiera exportar al servidor SIEM. Use el control deslizante para habilitarlas y deshabilitarlas; de forma predeterminada todo está seleccionado. Puede usar el menú desplegable **Apply to** (Aplicar a) para establecer filtros para enviar solo alertas y actividades específicas al servidor SIEM.
Puede hacer clic en **Edit and preview results** (Editar y obtener una vista previa de los resultados) para comprobar que el filtro funciona según lo esperado. Haga clic en **Siguiente**. 

  ![Configuración de tipos de datos](./media/siem3.png)

7. Copie el token y guárdelo para más adelante. Después de hacer clic en Finalizar y salir del asistente, en la página SIEM, en la tabla podrá ver al agente SIEM que ha agregado. Mostrará que está **Creado** hasta que se conecte más adelante.

### <a name="step-2-download-the-jar-file-and-run-it-on-your-server"></a>Paso 2: descarga del archivo JAR y ejecución en el servidor

1. [Descargue el archivo .zip desde el Centro de descarga de Microsoft](https://go.microsoft.com/fwlink/?linkid=838596) y descomprímalo.

2. Extraiga el archivo .jar desde el archivo .zip y ejecútelo en el servidor.
 Después de ejecutar el archivo, ejecute lo siguiente:
    
      java -jar mcas-siemagent-0.87.20-signed.jar [--logsDirectory NOMBRE_DIRECTORIO] [--proxy DIRECCIÓN[:PUERTO]] --token TOKEN
> [!NOTE]
> - El nombre de archivo puede diferir dependiendo de la versión del agente SIEM.
> - Los parámetros entre corchetes [] son opcionales y solo deben usarse si procede.

Se usan las variables siguientes:
- NOMBRE_DIRECTORIO es la ruta de acceso al directorio que quiere usar para los registros de depuración del agente local.
- DIRECCIÓN[:PUERTO] es la dirección del servidor proxy y el puerto que usa el servidor para conectarse a Internet.
- TOKEN es el token del agente SIEM que ha copiado en el paso anterior.

Puede escribir -h en cualquier momento para obtener ayuda.



### <a name="step-3-validate-that-the-siem-agent-is-working"></a>Paso 3: validación de que el agente SIEM funcione

1. Asegúrese de que el estado del agente SIEM en el portal de Cloud App Security no sea Desconectado y de que no haya ninguna notificación del agente. 
 ![SIEM desconectado](./media/siem-not-connected.png)
 
   En su lugar, el estado debe ser Conectado, tal como se muestra aquí:  ![SIEM conectado](./media/siem-connected.png).

2. En el servidor Syslog o SIEM, asegúrese de que vea las alertas y actividades procedentes de Cloud App Security.


## <a name="regenerating-your-token"></a>Volver a generar el token
Si pierde el token, siempre puede volver a generarlo haciendo clic en los tres puntos al final de la fila del agente SIEM de la tabla y seleccionando **Regenerate token** (Volver a generar token).

 ![SIEM: volver a generar el token](./media/siem-regenerate-token.png)

## <a name="editing-your-siem-agent"></a>Editar el agente SIEM 
Si necesita editar el agente SIEM en el futuro, puede hacer clic en los tres puntos al final de la fila del agente SIEM de la tabla y seleccionar **Editar**. Si edita el agente SIEM, no es necesario volver a ejecutar el archivo .jar, ya que se actualiza automáticamente.

![SIEM: edición](./media/siem-edit.png)

## <a name="deleting-your-siem-agent"></a>Eliminación al agente SIEM
Si necesita eliminar el agente SIEM en el futuro, puede hacer clic en los tres puntos al final de la fila del agente SIEM de la tabla y seleccionar **Eliminar**.

![SIEM: eliminación](./media/siem-delete.png)


## <a name="troubleshooting-the-siem-agent"></a>Solución de problemas del agente SIEM

Si ve alguno de los errores siguientes en el símbolo del sistema mientras se ejecuta al agente, siga estos pasos para corregir el problema:

|Error|Descripción|Solución|
|----|----|----|
|Error general durante el arranque|Error inesperado durante el arranque del agente.|Póngase en contacto con el soporte técnico.|
|Demasiados errores críticos|Se han producido demasiados errores críticos al conectar la consola. Apagando el equipo.|Póngase en contacto con el soporte técnico.|
|Token no válido|El token proporcionado no es válido.|Asegúrese de que haya copiado el token adecuado. Puede usar el proceso anterior para volver a generar el token.|
|Dirección de proxy no válida|La dirección de proxy proporcionada no es válida.|Asegúrese de que haya escrito el proxy y el puerto correctos.|


Después de crear el agente, si ve una de las siguientes **Notificaciones de agente** en el portal de Cloud App Security en la página del agente SIEM, siga estos pasos para corregir el problema:

|Error|Descripción|Solución|
|----|----|----|
|**Error interno**|Se ha producido un problema desconocido con el agente SIEM.|Póngase en contacto con el soporte técnico.|
|**Error de envío del servidor de datos**|Este error puede aparecer si está trabajando con un servidor de Syslog sobre TCP. El agente SIEM no puede conectarse a su servidor de Syslog.  Si recibe este error, el agente dejará de extraer nuevas actividades hasta que se corrija, por lo que debe asegurarse de seguir los pasos de corrección hasta que el error deje de aparecer.|1. Asegúrese de que se haya definido correctamente el servidor de Syslog: en la interfaz de Cloud App Security, edite el agente SIEM como se ha descrito anteriormente, asegúrese de que haya escrito correctamente el nombre del servidor y establezca el puerto correcto. </br>2. Compruebe la conectividad con el servidor de Syslog: asegúrese de que el firewall no esté bloqueando la comunicación.| 
|**Error de conexión del servidor de datos**| Este error puede aparecer si está trabajando con un servidor de Syslog sobre TCP. El agente SIEM no puede conectarse a su servidor de Syslog.  Si recibe este error, el agente dejará de extraer nuevas actividades hasta que se corrija, por lo que debe asegurarse de seguir los pasos de corrección hasta que el error deje de aparecer.|1. Asegúrese de que se haya definido correctamente el servidor de Syslog: en la interfaz de Cloud App Security, edite el agente SIEM como se ha descrito anteriormente, asegúrese de que haya escrito correctamente el nombre del servidor y establezca el puerto correcto. </br>2. Compruebe la conectividad con el servidor de Syslog: asegúrese de que el firewall no esté bloqueando la comunicación.| 

## <a name="see-also"></a>Consulte también  
[Directivas de actividad de usuario](user-activity-policies.md)   
[Para obtener soporte técnico, visite la página de soporte técnico asistido de Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Los clientes Premier también pueden elegir Cloud App Security directamente desde el Portal Premier.](https://premier.microsoft.com/)  
  
  


<!--HONumber=Jan17_HO2-->


