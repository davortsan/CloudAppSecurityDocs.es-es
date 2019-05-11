---
title: 'Fe de sus aplicaciones: Cloud App Security | Microsoft Docs'
description: Este artículo proporcionan instrucciones para la certificación de las aplicaciones en Cloud App Security.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: barbkess
ms.date: 29/04/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 3536c0a5-fa56-4931-9534-cc7cc4b4dfb0
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 0799073e7bd82570fd298c1080960170648b7ac1
ms.sourcegitcommit: 9553aed06ebb2378d44bb5685439ae5cba605171
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/06/2019
ms.locfileid: "65048408"
---
# <a name="attest-your-app"></a>Comprobaciones sobre la aplicación

Microsoft Cloud App Security le permite dar fe de la aplicación, por lo que asegúrese de que el cumplimiento de normas y los detalles de seguridad que se usa para clasificar la aplicación en nuestro catálogo de aplicaciones de nube están actualizados.

Si la aplicación ya aparece en el catálogo de aplicaciones en la nube, o que es nuevo, envíe un cuestionario de atestación automática. Para obtener más información sobre el proceso de atestación automática y a obtener el cuestionario, póngase en contacto con casfeedback@microsoft.com.

Siga los atributos de servicio se describe a continuación para completar correctamente el envío del cuestionario:

| Campo | Categoría de información | Tipo | Valores aceptados | Descripción |
|------|-------|------|---------|----------|
| Nombre de la aplicación | General | String | Texto sin formato | El nombre de la aplicación tal y como debe aparecer en el catálogo de aplicaciones en la nube. |
| Descripción | General | String | Texto sin formato | Breve explicación de lo que la aplicación permite a los usuarios ni alcanzar. |
| Category| General | String | Cerrar lista - proporcionada en el cuestionario | Clasificación de la aplicación según el campo al que se relaciona. |
| Oficina central | General | Código de país | Cerrar lista - proporcionada en el cuestionario | El país de la sede central del proveedor.|
| Centro de datos| General | Matriz de código de país * | Cerrar lista - proporcionada en el cuestionario (selección múltiple) | El país en el que reside su centro de datos (puede ser varias ubicaciones) |
| Empresa de hospedaje | General | String | Texto sin formato | El nombre de la compañía que proporciona hospedaje de servidor para la aplicación. |
| Fundado | General | Entero | AAAA (posterior a 2019 no) | El año en el que se fundó el proveedor. |
| Que contiene | General | String | Private, Public | Muestra si el proveedor es una empresa pública o privada |
| Dominio de aplicación | General | Matriz de dirección URL *. | Texto sin formato | La lista de dominios que se usan para interactuar con el servicio (por ejemplo, ' teams.microsoft.com' para Microsoft Teams) |
| Condiciones del servicio | General | Dirección URL | Texto sin formato | ¿Esta aplicación proporciona un conjunto de reglamentos que los usuarios deben aceptar cumplir para poder usar la aplicación? |
| Directiva de privacidad | General | Dirección URL | Texto sin formato | Un vínculo a un legalmente documento relativo a cómo este proveedor controla la información de empleado, cliente o cliente recopilada como parte de la aplicación. |
| Dirección URL de inicio de sesión | General | Matriz de dirección URL *. | Texto sin formato | La dirección URL a través de qué usuarios inician sesión en la aplicación. |
| Proveedor | General | String | Texto sin formato | El nombre del proveedor que ofrece esta aplicación. |
| Tipos de datos | General | String | Cerrar lista - proporcionada en el cuestionario | ¿Qué tipos de datos se pueden cargar por el usuario a la aplicación?|
| Página principal | General | Dirección URL | Texto sin formato | Dirección URL de página principal del proveedor. |
| Infracción más reciente | Seguridad | Fecha | MMM-dd-aaaa | Incidente más reciente en la que se ven, robados o utilizados por un individuo no autorizado a hacerlo, protegidos, datos confidenciales o que pertenecen a la aplicación. |
| Método de cifrado de datos en reposo | Seguridad | String | Cerrar lista - proporcionada en el cuestionario | El tipo de cifrado de datos en reposo se realiza en la aplicación. |
| Multi-factor Authentication | Seguridad | Boolean | True, False | ¿Admite esta aplicación soluciones de autenticación multifactor? |
| Restricción de direcciones IP | Seguridad | Boolean | True, False | ¿Admite esta aplicación la restricción de direcciones IP concretas por la aplicación? |
| Traza de auditoría de usuario | Seguridad | Boolean | True, False | ¿Admite esta aplicación la disponibilidad de auditoría por cuenta de usuario? |
| Pista de auditoría de administración | Seguridad | Boolean | True, False | ¿Admite esta aplicación la disponibilidad de una pista de auditoría de administración en la aplicación? |
| Traza de auditoría de datos | Seguridad | Boolean | True, False | ¿Admite esta aplicación la disponibilidad de una pista de auditoría de datos en la aplicación? |
| El usuario puede cargar datos | Seguridad | Boolean | True, False | ¿Esta aplicación admite datos de usuario cargado? |
| Clasificación de datos | Seguridad | Boolean | True, False | ¿Habilita la opción para la clasificación de los datos cargados en la aplicación de esta aplicación? |
| Recordar contraseña | Seguridad | Boolean | True, False | ¿Habilita la opción de recordar y guardar las contraseñas de usuario en la aplicación de esta aplicación? |
| Compatibilidad con funciones de usuario | Seguridad | Boolean | True, False | ¿Admite esta aplicación la distribución de usuarios por roles y niveles de permiso? |
| Uso compartido de archivos | Seguridad | Boolean | True, False | ¿Esta aplicación incluye características que permiten compartir archivos entre los usuarios? |
| Nombre de certificado válido | Seguridad | Boolean | True, False | ¿Ofrece el servidor un certificado SSL que coincida con el nombre de dominio? |
| Certificado de confianza | Seguridad | Boolean | True, False | ¿Ofrece el servidor un certificado SSL de confianza (cadena de firma no expirados, comprobado y de confianza, etcetera)? |
| Protocolo de cifrado | Seguridad | String | Cerrar lista - proporcionada en el cuestionario | La última versión de protocolo de capa de transporte (TLS) cifrado compatible entre el proveedor de punto de conexión y la aplicación de usuario. Si el certificado del servidor que no existe o no es válido, el cifrado se considera no compatible.|
| Heartbleed corregido | Seguridad | Boolean | True, False | ¿Es la implementación de SSL del servidor que se han revisado para el error heartbleed y así reducir la vulnerabilidad? |
| Encabezados de seguridad HTTP: Strict-Transport-Security | Seguridad | Boolean | True, False | ¿Es HTTP Strict-Transport-Security encabezados implementados la aplicación en su sitio Web? |
| Encabezados de seguridad HTTP: Content-Security-Policy | Seguridad | Boolean | True, False | ¿Es HTTP Content-Security-Policy encabezados implementados la aplicación en su sitio Web? |
| Encabezados de seguridad HTTP: X-Frame-Options | Seguridad | Boolean | True, False | ¿Los encabezados HTTP X-Frame-Options implementados por la aplicación en su sitio Web? |
| Encabezados de seguridad HTTP: X-Content-Type-Options | Seguridad | Boolean | True, False | ¿Los encabezados HTTP X-Content-Type-Options implementados por la aplicación en su sitio Web? |
| Encabezados de seguridad HTTP: X-XSS-Protection | Seguridad | Boolean | True, False | ¿Es HTTP X-XSS-Protection encabezados implementados la aplicación en su sitio Web? |
| Admite SAML | Seguridad | Boolean | True, False | ¿Admite esta aplicación el estándar SAML para intercambiar datos de autenticación y autorización? |
| Protegido frente a DROWN | Seguridad | Boolean | True, False | ¿Los servidores de aplicaciones están protegidos frente a ataques DROWN? |
| Pruebas de penetración | Seguridad | Boolean | True, False | ¿Esta aplicación realizar pruebas de penetración para detectar y evaluar las vulnerabilidades de red? |
| Requiere autenticación del usuario | Seguridad | Boolean | True, False | ¿Esta aplicación requieren autenticación y deshabilita el uso anónimo? |
| Directiva de contraseñas: Límite de longitud de contraseña | Seguridad | Boolean | True, False | ¿Esta aplicación exige un límite de longitud de la creación de contraseñas? |
| Directiva de contraseñas: Combinación de caracteres | Seguridad | Boolean | True, False | ¿Esta aplicación aplica una combinación de caracteres en la creación de contraseñas? |
| Directiva de contraseñas: Período de cambio de contraseñas | Seguridad | Boolean | True, False | ¿Esta aplicación exige a los usuarios para restablecer la contraseña periódicamente? |
| Directiva de contraseñas: Reutilización y el historial de contraseñas | Seguridad | Boolean | True, False | ¿Esta aplicación impedir la reutilización de contraseñas anteriores? |
| Directiva de contraseñas: Uso de información personal | Seguridad | Boolean | True, False | ¿Esta aplicación prohibir el uso de información personal en las contraseñas? |
| Directiva de contraseñas | Seguridad | Boolean | True, False | ¿Esta aplicación aplica una directiva de contraseña que cumpla con los procedimientos recomendados? |
| FINRA | Cumplimiento | Boolean | True, False, N/D | ¿Esta aplicación ofrece conforme a FINRA, un conjunto de estándares para organizaciones sin ánimo de lucro autorizado por el congreso que regula y exige la mejora de las medidas de seguridad de los inversores e integridad del mercado? |
| FISMA | Cumplimiento | Boolean | True, False, N/D | ¿Esta aplicación se ofrece conforme a FISMA, la legislación estadounidense que define un marco completo para proteger información gubernamental, operaciones y recursos dentro de las agencias federales frente a amenazas? |
| GAAP | Cumplimiento | Boolean | True, False, N/D | ¿Esta aplicación se ofrece conforme a GAAP, una colección de reglas de contabilidad normalmente seguido y estándares para los informes financieros? |
| HIPAA | Cumplimiento | Boolean | True, False, N/D | ¿Cumple esta aplicación con HIPAA, la legislación estadounidense que establece estándares para proteger la confidencialidad y la seguridad de la información de mantenimiento identificable individualmente? |
| ISAE 3402 | Cumplimiento | Boolean | True, False, N/D | ¿Esta aplicación se ofrece conforme a ISAE 3402, el estándar global que se garantice que una organización de servicio posee los controles adecuados en su lugar? |
| ISO 27001 | Cumplimiento | Boolean | True, False, N/D | ¿Es esta aplicación certificada ISO 27001, un certificado que se concede a las empresas respetar reconocidas internacionalmente directrices y principios generales para iniciar, implementar, mantener y mejorar la administración de seguridad de información dentro de una organización? |
| ITAR | Cumplimiento | Boolean | True, False, N/D | ¿Esta aplicación se ofrece conforme a ITAR, reglamentos que controlan la exportación e importación de artículos relacionados con la defensa y servicios que se encuentra en la lista militar de Estados Unidos de nosotros? |
| SOC 1 | Cumplimiento | Boolean | True, False, N/D | ¿Esta aplicación se ofrece conforme a SOC 1, informar sobre los controles de una organización de servicio que son relevantes para el control interno de las entidades de usuario sobre informes financieros? |
| SOC 2 | Cumplimiento | Boolean | True, False, N/D | ¿Esta aplicación se ofrece conforme a SOC 2, procesamiento no financiero según uno o varios de los criterios de servicio de confianza en seguridad, privacidad, disponibilidad, confidencialidad y la integridad de procesamiento de informes? |
| SOC 3 | Cumplimiento | Boolean | True, False, N/D | ¿Esta aplicación se ofrece conforme a SOC 3, con informes según los criterios de servicio de confianza, que se pueden distribuir libremente y solo contienen la aserción de administración que se han cumplido los requisitos de los criterios seleccionados? |
| SOX | Cumplimiento | Boolean | True, False, N/D | ¿Cumple esta aplicación con la ley SOX, la legislación de Estados Unidos cuyo objetivo es proteger accionistas y el público general frente a fraudes y errores de contabilidad, así como mejorar la exactitud de las divulgaciones corporativas? |
| SP 800-53 | Cumplimiento | Boolean | True, False, N/D | ¿Esta aplicación se ofrece conforme a SP80053, se recomienda a los controles de seguridad para las organizaciones y sistemas de información federales? |
| SSAE 16 | Cumplimiento | Boolean | True, False, N/D | ¿Cumple esta aplicación con el estándar SSAE 16 para la auditoría de los controles de cumplimiento internos de una organización de servicios y procesos de informes? |
| Versión de PCI DSS | Cumplimiento | String | 1, 2, 3, 3.1, 3.2, N/A | La versión del protocolo PCI-DSS son compatible con esta aplicación. |
| ISO 27018 | Cumplimiento | Boolean | True, False, N/D | ¿Cumple esta aplicación a la norma ISO 27018, que establece comúnmente aceptados controles y directrices para el procesamiento y la protección de información de identificación personal (PII) públicas entorno informático de nube? |
| GLBA | Cumplimiento | Boolean | True, False, N/D | ¿Cumple esta aplicación con la ley de Gramm-Leach-Bliley (GLBA), lo que requiere que las instituciones financieras establezcan estándares para proteger la seguridad y confidencialidad de información personal de los clientes? |
| Nivel de FedRAMP | Cumplimiento | String | Alto, moderado, bajo, N/D | El nivel de la solución conforme a FedRAMP proporcionado por esta aplicación. |
| Nivel CSA STAR | Cumplimiento | String | Autoevaluación, certificación, atestación, evaluación C-STAR, supervisión continua, N/D | El nivel del programa CSA STAR en el que está certificada la aplicación |
| entre la Unión Europea y Estados Unidos | Cumplimiento | Boolean | True, False, N/D | ¿Cumple esta aplicación con el marco del escudo de privacidad UE-EE. UU., que impone obligaciones más estrictas a las empresas estadounidenses para proteger datos personales europeos? |
| ISO 27017 | Cumplimiento | Boolean | True, False, N/D | ¿Cumple esta aplicación con la norma ISO 27017, que establece los controles comúnmente aceptados y directrices para procesar y proteger la información de usuario en un entorno de informática en nube público? |
| COBIT | Cumplimiento | Boolean | True, False, N/D | ¿Cumple esta aplicación con COBIT, que establece los procedimientos recomendados para el gobierno y el control de los sistemas de información y la tecnología y alinea la TI con los principios del negocio? |
| COPPA | Cumplimiento | Boolean | True, False, N/D | ¿Cumple esta aplicación con COPPA, que define los requisitos en el sitio Web y los operadores de servicios en línea que proporcionan contenido a niños de menos de 13 años de edad? |
| FERPA | Cumplimiento | Boolean | True, False, N/D | ¿Cumple esta aplicación con la ley FERPA, una ley federal que protege la privacidad de los expedientes académicos? |
| GAPP | Cumplimiento | Boolean | True, False, N/D | ¿Cumple esta aplicación con GAPP, una colección de reglas seguido normalmente que abordan los riesgos de privacidad en una organización? |
| CSF HITRUST | Cumplimiento | Boolean | True, False, N/D | ¿Cumple esta aplicación con CSF HITRUST, un conjunto de controles que armoniza los requisitos de los estándares y normativas de seguridad de información? |
| Jericho foro mandamientos | Cumplimiento | Boolean | True, False, N/D | ¿Esta aplicación sigue Jericho foro mandamientos, un conjunto si la operación en entornos de desaprovisionamiento perimeterized segura de los principios que se deben observar al diseñar sistemas para? |
| ISO 27002 | Cumplimiento | Boolean | True, False, N/D | ¿Esta aplicación se ofrece conforme a ISO 27002, que establece instrucciones comunes para los estándares de seguridad de información de la organización y prácticas de administración de seguridad de información? |
| FFIEC | Cumplimiento | Boolean | True, False, N/D | ¿Cumple esta aplicación con instrucciones Federal financieros instituciones examen del Consejo sobre los controles de administración de riesgos necesarios para autenticar los servicios en un entorno de banca de Internet? |
| Propiedad de los datos | Legal | Boolean | True, False | ¿Conserva esta aplicación completamente la propiedad del usuario de datos cargados? |
| DMCA | Legal | Boolean | True, False | ¿Cumple esta aplicación con el Digital Millennium Copyright Act (DMCA), que criminaliza cualquier intento de acceder ilegalmente a material con derechos de autor? |
| Directiva de retención de datos | Legal | Boolean | True, False | ¿Qué es Directiva de la aplicación para la retención de datos de usuario después de la terminación de la cuenta? |
| Instrucción de preparación de RGPD | Legal | Dirección URL | Texto sin formato | Un vínculo a su sitio Web, cuando proceda, relacionado con cómo este proveedor tiene previsto controlar el cumplimiento del RGPD. |
| GDPR: derecho a borrado | Legal | Boolean | True, False, N/D | ¿Esta aplicación deje de procesar y eliminar datos personales de un individuo a petición? |
| GDPR - las infracciones de datos de informe | Legal | Boolean | True, False, N/D | ¿Hace que este las infracciones de datos de aplicación informes a las autoridades de supervisión y las personas afectadas por la infracción, dentro de 72 horas de detección de brechas? |
| GDPR: evaluación del impacto | Legal | Boolean | True, False, N/D | ¿Esta aplicación realiza la valoración del impacto de protección de datos para identificar el riesgo a las personas? |
| GDPR: control de datos segura borde cruzado | Legal | Boolean | True, False, N/D | ¿Esta aplicación de forma segura transferir datos entre distintos países? |
| GDPR: responsable de la protección de datos | Legal | Boolean | True, False, N/D | ¿Esta aplicación designa a datos de un responsable de la protección para supervisar el cumplimiento del RGPD y la estrategia de seguridad de datos? |
| GDPR - directamente al objeto | Legal | Boolean | True, False, N/D | ¿Esta aplicación ofrece a las personas con la capacidad de objeto para el procesamiento de sus datos personales en determinadas circunstancias? |
| GDPR - derecho de acceso a | Legal | Boolean | True, False, N/D | ¿Esta aplicación ofrece a las personas con la capacidad, previa solicitud, saber qué datos personales que se está usando una empresa y cómo se usa? |
| GDPR - directamente en datos fiabilidad | Legal | Boolean | True, False, N/D | ¿Esta aplicación ofrece a las personas con la capacidad de obtener y reutilizar sus datos personales para sus propios fines en distintos servicios tras la solicitud? |
| GDPR: derecho para mantenerse informado | Legal | Boolean | True, False, N/D | ¿Esta aplicación informar a los individuos de las medidas de seguridad adecuados que toma cuando se transfieren datos personales a un país que no sea Europa o a una organización internacional? |
| GDPR - directamente a la restricción de procesamiento | Legal | Boolean | True, False, N/D | ¿Esta aplicación ofrece a las personas con la capacidad de bloquear o suprimir el procesamiento de datos personales? |
| Derechos de RGPD - relacionados con decisiones automatizadas | Legal | Boolean | True, False, N/D | ¿Esta aplicación ofrece a las personas con la posibilidad de optar por no estar sujeto a una decisión que se basa únicamente en el procesamiento automatizado? Esto incluye la generación de perfiles, que puede tener consecuencias legales. |
| GDPR - lícita base para el procesamiento | Legal | Boolean | True, False, N/D | ¿Esta aplicación procese los datos personales legalmente de acuerdo con su consentimiento, contrato, obligaciones legales en materia, intereses esenciales, intereses legítimos, categoría especial, datos y datos delito? |
| GDPR: derecho a rectificación | Legal | Boolean | True, False, N/D | ¿Esta aplicación ofrece a las personas con la capacidad de corregir sus datos personales? El controlador debe responder a todas las solicitudes de sus asuntos de datos dentro de un mes. |


\* Los campos de tipo *matriz* deben separarse con punto y coma (;).

## <a name="next-steps"></a>Pasos siguientes 
[Actividades diarias para proteger el entorno de nube](daily-activities-to-protect-your-cloud-environment.md)

[Los clientes Premier también pueden crear una solicitud de soporte técnico directamente en el portal Premier.](https://premier.microsoft.com/) 

