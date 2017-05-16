---
title: "Integración de SIEM con Cloud App Security | Microsoft Docs"
description: "En este tema se proporciona información sobre la integración de SIEM con Cloud App Security."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 5/9/2017
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: 4649423b-9289-49b7-8b60-04b61eca1364
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 5880ea404d6830c5d8f12534c04f123d8c517946
ms.sourcegitcommit: ea8207f412f31127beafd18a0bd028052fbadf90
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/09/2017
---
# <a name="siem-integration"></a>Integración de SIEM
    
Ahora puede integrar Cloud App Security con su servidor SIEM para habilitar la supervisión centralizada de alertas y actividades. La integración de un servicio SIEM le permite proteger mejor sus aplicaciones de nube a la vez que mantiene el flujo de trabajo de seguridad habitual, automatizando así los procedimientos de seguridad y estableciendo correlaciones entre eventos basados en la nube y eventos locales. El agente SIEM de Cloud App Security se ejecuta en el servidor y extrae las alertas y las actividades de Cloud App Security y las transmite al servidor SIEM.

Cuando integre por primera vez su SIEM con Cloud App Security, las actividades y las alertas de los dos últimos días se reenviarán al SIEM, así como todas las actividades y alertas (en función del filtro seleccionado) que se produzcan a partir de entonces. Además, si deshabilita esta característica durante un período prolongado, cuando la habilite de nuevo, se reenviarán las alertas y las actividades de los dos últimos días, así como las que se produzcan a partir de entonces.

La integración con SIEM se realiza en tres pasos:
1. Configuración en el portal de Cloud App Security 
2. Descarga del archivo JAR y ejecución en el servidor
3. Valide que el agente SIEM funcione.

## <a name="prerequisites"></a>Requisitos previos

- Servidor Windows o Linux estándar (puede ser una máquina virtual).
- El servidor debe ejecutar Java 8; no se admiten versiones anteriores.

## <a name="integrating-with-your-siem"></a>Integración con su SIEM

### <a name="step-1-set-it-up-in-the-cloud-app-security-portal"></a>Paso 1: configuración en el portal de Cloud App Security

1. En el portal de Cloud App Security, en el engranaje Configuración, haga clic en **Agentes SIEM**.

2. Haga clic en Agregar agente SIEM para iniciar el asistente.
3. En el asistente, haga clic en **Add SIEM agent** (Agregar agente SIEM).    
4. En el asistente, asigne un nombre, **seleccione el formato SIEM** y establezca la **Configuración avanzada** que esté relacionada con ese formato. Haga clic en **Siguiente**.

   ![Configuración general de SIEM](./media/siem1.png)

5. Escriba la dirección IP del **host de syslog remoto** y el **número de puerto de syslog**. Seleccione TCP o UDP como protocolo de syslog remoto.
Puede trabajar con el administrador de seguridad para obtener estos detalles si no los tiene.
Haga clic en **Siguiente**.
  ![Configuración remota de Syslog](./media/siem2.png)

6. Seleccione los tipos de datos, **Alertas** y **Actividades** que quiera exportar al servidor SIEM. Use el control deslizante para habilitarlas y deshabilitarlas; de forma predeterminada todo está seleccionado. Puede usar el menú desplegable **Apply to** (Aplicar a) para establecer filtros para enviar solo alertas y actividades específicas al servidor SIEM.
Puede hacer clic en **Editar y obtener vista previa de resultados** para comprobar que el filtro funciona según lo esperado. Haga clic en **Siguiente**. 

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



### <a name="step-3-validate-that-the-siem-agent-is-working"></a>Paso 3: validación del correcto funcionamiento del agente SIEM

1. Asegúrese de que el estado del agente SIEM en el portal de Cloud App Security no sea **Error de conexión** o **Desconectado** y de que no haya ninguna notificación del agente. Verá **Error de conexión** si la conexión está inactiva durante más de dos horas y **Desconectado** si la conexión está inactiva durante más de 12 horas.
 ![SIEM desconectado](./media/siem-not-connected.png)
 
   En su lugar, el estado debe ser Conectado, tal como se muestra aquí:  ![SIEM conectado](./media/siem-connected.png).

2. En el servidor Syslog o SIEM, asegúrese de que vea las alertas y actividades procedentes de Cloud App Security.


## <a name="regenerating-your-token"></a>Volver a generar el token
Si pierde el token, siempre puede volver a generarlo haciendo clic en los tres puntos al final de la fila del agente SIEM de la tabla y seleccionando **Regenerar token**.

 ![SIEM: volver a generar el token](./media/siem-regenerate-token.png)

## <a name="editing-your-siem-agent"></a>Editar el agente SIEM 
Si necesita editar el agente SIEM en el futuro, puede hacer clic en los tres puntos al final de la fila del agente SIEM de la tabla y seleccionar **Editar**. Si edita el agente SIEM, no es necesario volver a ejecutar el archivo .jar, ya que se actualiza automáticamente.

![SIEM: edición](./media/siem-edit.png)

## <a name="deleting-your-siem-agent"></a>Eliminación al agente SIEM
Si necesita eliminar el agente SIEM en el futuro, puede hacer clic en los tres puntos al final de la fila del agente SIEM de la tabla y seleccionar **Eliminar**.

![SIEM: eliminación](./media/siem-delete.png)

> [!NOTE]
> Esta característica está en versión preliminar pública.

## <a name="see-also"></a>Consulte también  
[Solución de problemas de integración de SIEM](troubleshooting-siem.md)   
[Para obtener soporte técnico, visite la página de soporte técnico asistido de Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Los clientes Premier también pueden elegir Cloud App Security directamente desde el Portal Premier.](https://premier.microsoft.com/)  
  
  