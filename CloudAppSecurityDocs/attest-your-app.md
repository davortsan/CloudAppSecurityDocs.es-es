---
title: 'Atestar las aplicaciones: Cloud App Security | Microsoft Docs'
description: En este artículo se proporcionan instrucciones para la atestación de las aplicaciones en Cloud App Security.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 6/20/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 3536c0a5-fa56-4931-9534-cc7cc4b4dfb0
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 681ce6935353ab25968bb8955873188e0c839c3e
ms.sourcegitcommit: 2e8488efcc2253e0b5fa33db308e4986a9cdefd5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/07/2019
ms.locfileid: "71997369"
---
# <a name="attest-your-app"></a>Comprobaciones sobre la aplicación

Microsoft Cloud App Security le permite atestiguar su aplicación para asegurarse de que los detalles de cumplimiento y seguridad que usamos para clasificar la aplicación en el catálogo de aplicaciones en la nube están actualizados.

Si la aplicación ya aparece en el catálogo de aplicaciones en la nube o es nueva, envíe un [cuestionario de atestación automática](https://go.microsoft.com/fwlink/?linkid=2106624). Para obtener más información sobre el proceso de atestación automática, póngase en contacto con casfeedback@microsoft.com.

Siga los atributos de servicio que se describen a continuación para completar correctamente el envío del cuestionario:

| Campo | Categoría de información | Tipo | Valores aceptados | Descripción |
|------|-------|------|---------|----------|
| Nombre de la aplicación | General | String | Texto libre | El nombre de la aplicación tal como debe aparecer en el catálogo de aplicaciones en la nube. |
| Descripción | General | String | Texto libre | Breve explicación de lo que la aplicación permite a los usuarios realizar o conseguir. |
| Category| General | String | Cerrar lista: se proporciona en el cuestionario | Clasificación de la aplicación según el campo con el que se relaciona. |
| Oficina central | General | Código de país | Cerrar lista: se proporciona en el cuestionario | El país de la sede del proveedor.|
| Centro de datos| General | Matriz de código de país * | Cerrar lista: se proporciona en cuestionario (selección múltiple) | El país en el que reside el centro de datos (puede ser varias ubicaciones) |
| Empresa de hospedaje | General | String | Texto libre | El nombre de la empresa que proporciona hospedaje de servidor para la aplicación. |
| Constitución | General | Integer | AAAA (no posterior a 2019) | Año en el que se fundó el proveedor. |
| Esa | General | String | Privado, público | Muestra si el proveedor es una empresa privada o públicamente |
| Dominio de aplicación | General | Matriz de direcciones URL * | Texto libre | La lista de dominios que se usan para interactuar con el servicio (por ejemplo, "teams.microsoft.com" para Microsoft Teams) |
| Condiciones del servicio | General | Dirección URL | Texto libre | ¿Esta aplicación proporciona un conjunto de normas que los usuarios deben aceptar para poder usar la aplicación? |
| Directiva de privacidad | General | Dirección URL | Texto libre | Un vínculo a un documento de enlace legalmente relacionado con el modo en que este proveedor controla la información del cliente, el cliente o el empleado que se recopila como parte de la aplicación. |
| URL de inicio de sesión | General | Matriz de direcciones URL * | Texto libre | La dirección URL a través de la que los usuarios inician sesión en la aplicación. |
| Proveedor | General | String | Texto libre | Nombre del proveedor que proporciona esta aplicación. |
| Tipos de datos | General | String | Cerrar lista: se proporciona en el cuestionario | ¿Qué tipos de datos puede cargar el usuario en la aplicación?|
| Página principal | General | Dirección URL | Texto libre | Dirección URL de la Página principal del proveedor. |
| Plan de recuperación ante desastres | General | Boolean | True, False | ¿Esta aplicación tiene un plan de recuperación ante desastres que incluye una estrategia de copia de seguridad y restauración? |
| Última infracción | Seguridad | Fecha | MMM-DD-YYYY | Incidente más reciente en el que los datos confidenciales, protegidos o confidenciales que pertenecen a la aplicación se han visto, robado o utilizado por una persona no autorizada para ello. |
| Método de cifrado de datos en reposo | Seguridad | String | Cerrar lista: se proporciona en el cuestionario | El tipo de cifrado de datos en reposo realizado en la aplicación. |
| Multi-factor Authentication | Seguridad | Boolean | True, False | ¿Admite esta aplicación soluciones de autenticación multifactor? |
| Restricción de dirección IP | Seguridad | Boolean | True, False | ¿Esta aplicación admite la restricción de direcciones IP específicas de la aplicación? |
| Seguimiento de auditoría de usuario | Seguridad | Boolean | True, False | ¿Esta aplicación admite la disponibilidad de la traza de auditoría por cuenta de usuario? |
| Seguimiento de auditoría de administración | Seguridad | Boolean | True, False | ¿Esta aplicación admite la disponibilidad de una pista de auditoría de administrador en la aplicación? |
| Traza de auditoría de datos | Seguridad | Boolean | True, False | ¿Esta aplicación admite la disponibilidad de una traza de auditoría de datos en la aplicación? |
| El usuario puede cargar datos | Seguridad | Boolean | True, False | ¿Admite esta aplicación datos cargados por el usuario? |
| Clasificación de datos | Seguridad | Boolean | True, False | ¿Esta aplicación habilita la opción para la clasificación de los datos cargados en la aplicación? |
| Recordar contraseña | Seguridad | Boolean | True, False | ¿Esta aplicación habilita la opción para recordar y guardar contraseñas de usuario en la aplicación? |
| Compatibilidad con roles de usuario | Seguridad | Boolean | True, False | ¿Esta aplicación admite la distribución de usuarios por roles y niveles de permiso? |
| Uso compartido de archivos | Seguridad | Boolean | True, False | ¿Esta aplicación incluye características que permiten el uso compartido de archivos entre usuarios? |
| Nombre del certificado válido | Seguridad | Boolean | True, False | ¿El servidor proporciona un certificado SSL que coincide con el nombre de dominio? |
| Certificado de confianza | Seguridad | Boolean | True, False | ¿El servidor proporciona un certificado SSL de confianza (no ha expirado, comprobado y una cadena de firma de confianza, etc.)? |
| Protocolo de cifrado | Seguridad | String | Cerrar lista: se proporciona en el cuestionario | La versión más reciente del Protocolo de cifrado de seguridad de la capa de transporte (TLS) compatible entre el punto de conexión de usuario y el proveedor de aplicaciones. Si el certificado del servidor no existe o no es válido, se considera que el cifrado no es compatible.|
| Heartbleed revisado | Seguridad | Boolean | True, False | ¿La implementación de SSL del servidor revisado para el error de Heartbleed para reducir la vulnerabilidad? |
| Encabezados de seguridad HTTP: STRICT-Transport-seguridad | Seguridad | Boolean | True, False | ¿Son los encabezados HTTP STRICT-Transport-Security implementados por la aplicación en su sitio web? |
| Encabezados de seguridad HTTP: Directiva de seguridad de contenido | Seguridad | Boolean | True, False | ¿Son los encabezados HTTP Content-Security-Policy implementados por la aplicación en su sitio web? |
| Encabezados de seguridad HTTP: X-Frame-Options | Seguridad | Boolean | True, False | ¿Son los encabezados HTTP X-Frame-Options implementados por la aplicación en su sitio web? |
| Encabezados de seguridad HTTP: X-Content-Type-Options | Seguridad | Boolean | True, False | ¿Son los encabezados HTTP X-Content-Type-Options implementados por la aplicación en su sitio web? |
| Encabezados de seguridad HTTP: Protección de X-XSS | Seguridad | Boolean | True, False | ¿Son los encabezados HTTP X-XSS-Protection implementados por la aplicación en su sitio web? |
| Admite SAML | Seguridad | Boolean | True, False | ¿Esta aplicación admite el estándar SAML para intercambiar datos de autenticación y autorización? |
| Protegido contra AHOGAdo | Seguridad | Boolean | True, False | ¿Los servidores de aplicaciones están protegidos frente a ataques dirigidos? |
| Pruebas de penetración | Seguridad | Boolean | True, False | ¿Esta aplicación lleva a cabo pruebas de penetración para detectar y evaluar vulnerabilidades de red? |
| Requiere autenticación de usuario | Seguridad | Boolean | True, False | ¿Esta aplicación requiere autenticación y no permite el uso anónimo? |
| Directiva de contraseñas: Límite de longitud de la contraseña | Seguridad | Boolean | True, False | ¿Esta aplicación impone un límite de longitud en la creación de contraseñas? |
| Directiva de contraseñas: Combinación de caracteres | Seguridad | Boolean | True, False | ¿Aplica esta aplicación una combinación de caracteres en la creación de contraseñas? |
| Directiva de contraseñas: Cambiar el período de la contraseña | Seguridad | Boolean | True, False | ¿Esta aplicación exige a los usuarios que restablezcan su contraseña periódicamente? |
| Directiva de contraseñas: Historial de contraseñas y reutilización | Seguridad | Boolean | True, False | ¿Esta aplicación no permite la reutilización de contraseñas antiguas? |
| Directiva de contraseñas: Uso de la información personal | Seguridad | Boolean | True, False | ¿Esta aplicación no permite el uso de la información personal en las contraseñas? |
| Directiva de contraseñas | Seguridad | Boolean | True, False | ¿Esta aplicación aplica una directiva de contraseñas que cumple con los procedimientos recomendados? |
| FINRA | Cumplimiento | Boolean | True, false, N/A | ¿Esta aplicación cumple con FINRA, un conjunto estándar para organizaciones sin ánimo de lucro autorizadas por el Congreso que regula y aplica la mejora de las medidas de seguridad del inversor y la integridad del mercado? |
| FISMA | Cumplimiento | Boolean | True, false, N/A | ¿Esta aplicación cumple con FISMA, la legislación estadounidense que define un marco integral para proteger la información de la administración pública, las operaciones y los activos dentro de las agencias federales, frente a las amenazas? |
| CUMPLE | Cumplimiento | Boolean | True, false, N/A | ¿Esta aplicación cumple con los GAAP, una colección de reglas y estándares de contabilidad seguidos para la elaboración de informes financieros? |
| HIPAA | Cumplimiento | Boolean | True, false, N/A | ¿Esta aplicación cumple con HIPAA, la legislación de EE. UU. que establece estándares para proteger la confidencialidad y la seguridad de la información de estado que se identifica de forma individual? |
| ISAE 3402 | Cumplimiento | Boolean | True, false, N/A | ¿Esta aplicación cumple con ISAE 3402, el estándar global que proporciona la garantía de que una organización de servicio tiene los controles adecuados en su lugar? |
| ISO 27001 | Cumplimiento | Boolean | True, false, N/A | ¿Se ha certificado esta aplicación ISO 27001, un certificado dado a las empresas que mantienen directrices y principios generales reconocidos internacionalmente para iniciar, implementar, mantener y mejorar la administración de la seguridad de la información dentro de una organización? |
| ITAR | Cumplimiento | Boolean | True, false, N/A | ¿Esta aplicación cumple con ITAR, las regulaciones que controlan la exportación y la importación de artículos y servicios relacionados con la defensa que se encuentran en la lista de municiones de EE. UU.? |
| SOC 1 | Cumplimiento | Boolean | True, false, N/A | ¿Esta aplicación cumple con SOC 1, informa sobre los controles de una organización de servicio que son relevantes para el control interno de las entidades de usuario sobre los informes financieros? |
| SOC 2 | Cumplimiento | Boolean | True, false, N/A | ¿Esta aplicación cumple con SOC 2, que informa sobre el procesamiento no financiero basado en uno o más de los criterios de servicio de confianza sobre seguridad, privacidad, disponibilidad, confidencialidad y integridad de procesamiento? |
| SOC 3 | Cumplimiento | Boolean | True, false, N/A | ¿Esta aplicación cumple con SOC 3, con informes basados en los criterios de servicio de confianza, que se pueden distribuir libremente y solo contienen aserciones de administración que han cumplido los requisitos de los criterios elegidos? |
| LEY | Cumplimiento | Boolean | True, false, N/A | ¿Esta aplicación cumple con las leyes SOX, EE. UU. dirigidas a proteger a los accionistas y al público general de los errores y fraudes de cuentas, así como a mejorar la precisión de las divulgaciones corporativas? |
| SP 800-53 | Cumplimiento | Boolean | True, false, N/A | ¿Esta aplicación cumple con SP80053, los controles de seguridad recomendados para las organizaciones y los sistemas de información federales? |
| SSAE 16 | Cumplimiento | Boolean | True, false, N/A | ¿Esta aplicación cumple con el estándar SSAE 16 para la auditoría de los controles de cumplimiento y los procesos de informes internos de una organización de servicio? |
| Versión de PCI DSS | Cumplimiento | String | 1, 2, 3, 3,1, 3,2, N/A | La versión del protocolo PCI-DSS compatible con esta aplicación. |
| ISO 27018 | Cumplimiento | Boolean | True, false, N/A | ¿Esta aplicación cumple con ISO 27018, que establece los controles y las directrices que se aceptan comúnmente para procesar y proteger la información de identificación personal (PII) en un entorno de informática en la nube pública? |
| GLBA | Cumplimiento | Boolean | True, false, N/A | ¿Esta aplicación cumple con la Ley Gramm-Leach-Bliley (GLBA), que requiere que las instituciones financieras establezcan estándares para proteger la seguridad y confidencialidad de la información personal de los clientes? |
| Nivel de FedRAMP | Cumplimiento | String | Alta, moderada, baja, N/A | Nivel de la solución compatible con FedRAMP proporcionada por esta aplicación. |
| Nivel de estrella de CSA | Cumplimiento | String | Evaluación automática, certificación, atestación, evaluación de C-STAR, supervisión continua, N/A | El nivel de programa CSA STAR en el que la aplicación está certificada |
| entre la Unión Europea y Estados Unidos | Cumplimiento | Boolean | True, false, N/A | ¿Esta aplicación cumple la plataforma de protección de la privacidad de la Unión Europea-EE. UU., que impone mayores obligaciones en las empresas de EE. UU. para proteger los datos personales de europeans? |
| ISO 27017 | Cumplimiento | Boolean | True, false, N/A | ¿Esta aplicación cumple con ISO 27017, que establece los controles y las directrices que se aceptan comúnmente para procesar y proteger la información de usuario en un entorno de informática en la nube pública? |
| COBIT | Cumplimiento | Boolean | True, false, N/A | ¿Esta aplicación cumple COBIT, que establece las prácticas recomendadas para el gobierno y el control de la tecnología y los sistemas de información, y la alinea con los principios empresariales? |
| COPPA | Cumplimiento | Boolean | True, false, N/A | ¿Esta aplicación cumple con COPPA, que define los requisitos en el sitio web y los operadores de servicios en línea que proporcionan contenido a los niños en menos de 13 años de edad? |
| FERPA | Cumplimiento | Boolean | True, false, N/A | ¿Esta aplicación cumple con FERPA, una ley federal que protege la privacidad de los registros educativos de estudiantes? |
| SEPARACIÓN | Cumplimiento | Boolean | True, false, N/A | ¿Esta aplicación cumple con ESPACIAdo, una colección de reglas seguidas que abordan riesgos de privacidad en una organización? |
| HITRUST CSF | Cumplimiento | Boolean | True, false, N/A | ¿Esta aplicación cumple con HITRUST CSF, un conjunto de controles que armoniza los requisitos de las normas y los estándares de seguridad de la información? |
| Comandos del Foro de Jericho | Cumplimiento | Boolean | True, false, N/A | ¿Sigue esta aplicación los comandos de foros de Jericho, un conjunto de principios que se deben observar al diseñar sistemas para una operación segura en entornos sin uso medido? |
| ISO 27002 | Cumplimiento | Boolean | True, false, N/A | ¿Esta aplicación cumple con ISO 27002, que establece directrices comunes para los estándares de seguridad de la información de la organización y las prácticas de administración de seguridad de la información? |
| FFIEC | Cumplimiento | Boolean | True, false, N/A | ¿Esta aplicación cumple con las instrucciones del Consejo de análisis de las instituciones financieras federales sobre los controles de administración de riesgos necesarios para autenticar servicios en un entorno de banca por Internet? |
| Propiedad de los datos | Legal | Boolean | True, False | ¿Esta aplicación conserva por completo la propiedad del usuario de los datos cargados? |
| DMCA | Legal | Boolean | True, False | ¿Esta aplicación cumple con la ley de derechos de propiedad intelectual de DMCA), que criminalizes cualquier intento de acceder ilegalmente a material protegido por copyright? |
| Directiva de retención de datos | Legal | Boolean | True, False | ¿Cuál es la Directiva de la aplicación para la retención de datos de usuario después de la finalización de la cuenta? |
| RGPD Readiness (instrucción) | Legal | Dirección URL | Texto libre | Un vínculo a su sitio web, si procede, relacionando el modo en que este proveedor tiene previsto controlar el cumplimiento de RGPD. |
| RGPD: derecho a eliminación | Legal | Boolean | True, false, N/A | ¿Deja esta aplicación el procesamiento y elimina los datos personales de un individuo en el momento de la solicitud? |
| RGPD: infracciones de datos del informe | Legal | Boolean | True, false, N/A | ¿La aplicación informa de las infracciones de datos a las autoridades de supervisión y a los individuos afectados por la infracción en 72 horas de detección de brechas? |
| RGPD: evaluación del impacto | Legal | Boolean | True, false, N/A | ¿Esta aplicación realiza evaluaciones de impacto en la protección de datos para identificar el riesgo para los usuarios? |
| RGPD: control de datos de borde cruzado seguro | Legal | Boolean | True, false, N/A | ¿Esta aplicación transfiere datos de forma segura a través de los bordes? |
| RGPD: responsable de protección de datos | Legal | Boolean | True, false, N/A | ¿Esta aplicación designa un responsable de protección de datos para supervisar la estrategia de seguridad de los datos y el cumplimiento de RGPD? |
| RGPD: derecho a objeto | Legal | Boolean | True, false, N/A | ¿Esta aplicación proporciona a los usuarios la capacidad de objeto de procesar sus datos personales en determinadas circunstancias? |
| RGPD: derecho a acceder | Legal | Boolean | True, false, N/A | ¿Esta aplicación proporciona a los usuarios la capacidad de conocer, previa solicitud, qué datos personales usa una empresa y cómo se usa? |
| RGPD: derecho a datos portablility | Legal | Boolean | True, false, N/A | ¿Esta aplicación proporciona a los usuarios la capacidad de obtener y reutilizar sus datos personales para sus propios propósitos a través de diferentes servicios a petición? |
| RGPD: derecho a ser informado | Legal | Boolean | True, false, N/A | ¿Esta aplicación informa a los usuarios de las medidas de seguridad adecuadas que se aplican cuando los datos personales se transfieren a un país no perteneciente a la UE o a una organización internacional? |
| RGPD: derecho a la restricción de procesamiento | Legal | Boolean | True, false, N/A | ¿Esta aplicación proporciona a los usuarios la capacidad de bloquear o suprimir el procesamiento de los datos personales? |
| RGPD: derechos relacionados con la toma de decisiones automatizadas | Legal | Boolean | True, false, N/A | ¿Esta aplicación proporciona a los usuarios la capacidad de elegir no estar sujeta a una decisión basada únicamente en el procesamiento automatizado? Esto incluye la generación de perfiles, que puede tener consecuencias legales. |
| RGPD: legal base de procesamiento | Legal | Boolean | True, false, N/A | ¿Esta aplicación procesa los datos personales legalmente de acuerdo con el consentimiento, el contrato, la obligación legal, los intereses vitales, los intereses legítimos, la categoría especial, los datos y los datos de ofensa Penal? |
| RGPD: derecho a rectificación | Legal | Boolean | True, false, N/A | ¿Esta aplicación proporciona a los usuarios la capacidad de rectificar sus datos personales? El controlador debe responder a todas las solicitudes de sus asuntos de datos en un mes. |


Los campos \* de la *matriz* de tipo deben separarse con punto y coma (;).

## <a name="next-steps"></a>Pasos siguientes 
[Actividades diarias para proteger el entorno de nube](daily-activities-to-protect-your-cloud-environment.md)

[Los clientes Premier también pueden crear una solicitud de soporte técnico directamente en el portal Premier.](https://premier.microsoft.com/) 

