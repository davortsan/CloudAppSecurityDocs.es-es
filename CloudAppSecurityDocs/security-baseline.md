---
title: Línea base de seguridad de Azure para Microsoft Cloud App Security
description: La base de referencia de seguridad de Microsoft Cloud App Security proporciona instrucciones de procedimientos y recursos para implementar las recomendaciones de seguridad especificadas en el Banco de pruebas de seguridad de Azure.
author: msmbaldwin
ms.service: cloud-app-security
ms.topic: conceptual
ms.date: 12/03/2020
ms.author: mbaldwin
ms.custom: subject-security-benchmark
ms.openlocfilehash: f15795dcc7dca6454a63ee9a430ba70c7046b87c
ms.sourcegitcommit: e69f6e9705c3cf90a3a6b0c60d8adc9ad4818310
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2020
ms.locfileid: "96583873"
---
# <a name="azure-security-baseline-for-microsoft-cloud-app-security"></a>Línea base de seguridad de Azure para Microsoft Cloud App Security

Esta línea de base de seguridad aplica la guía de la [versión 2,0 de Benchmark de seguridad de Azure](https://docs.microsoft.com/azure/security/benchmarks/overview) a Microsoft Cloud App Security. Azure Security Benchmark proporciona recomendaciones sobre cómo puede proteger sus soluciones de nube en Azure. El contenido se agrupa por los **controles de seguridad** definidos por el Banco de pruebas de seguridad de Azure y las instrucciones relacionadas aplicables a Microsoft Cloud App Security. Se han excluido **los controles** no aplicables a Microsoft Cloud App Security.

Para ver cómo Microsoft Cloud App Security se asigna por completo a la prueba comparativa de seguridad de Azure, consulte el [archivo de asignación de línea de base de seguridad Microsoft Cloud App Security completo](https://github.com/MicrosoftDocs/SecurityBenchmarks/tree/master/Azure%20Offer%20Security%20Baselines).

## <a name="network-security"></a>Seguridad de redes

*Para más información, consulte [Azure Security Benchmark: seguridad de red](/azure/security/benchmarks/security-controls-v2-network-security).*

### <a name="ns-6-simplify-network-security-rules"></a>NS-6: simplificación de las reglas de seguridad de red

**Guía**: Use etiquetas de servicio de Virtual Network de Azure para definir controles de acceso a la red en grupos de seguridad de red o Azure Firewall configurados para los recursos de Cloud App Security. Puede utilizar etiquetas de servicio en lugar de direcciones IP específicas al crear reglas de seguridad. Al especificar el nombre de la etiqueta de servicio (por ejemplo: "MicrosoftCloudAppSecurity") en el campo de origen o de destino adecuado de una regla, puede permitir o denegar el tráfico para el servicio correspondiente. Microsoft administra los prefijos de direcciones que la etiqueta de servicio incluye y actualiza automáticamente dicha etiqueta a medida que las direcciones cambian.

- [Descripción y uso de etiquetas de servicio](https://docs.microsoft.com/azure/virtual-network/service-tags-overview)

**Supervisión de Azure Security Center**: no disponible actualmente

**Responsabilidad**: Customer

## <a name="identity-management"></a>Administración de identidades

*Para más información, consulte [Azure Security Benchmark: Administración de identidades](/azure/security/benchmarks/security-controls-v2-identity-management).*

### <a name="im-1-standardize-azure-active-directory-as-the-central-identity-and-authentication-system"></a>IM-1: Unificación en Azure Active Directory como sistema central de identidad y autenticación

**Guía**: Cloud App Security usa Azure Active Directory (Azure ad) como servicio de administración de identidades y accesos predeterminado. Debe unificar Azure AD para controlar la administración de identidades y accesos de la organización en:

- Los recursos de Microsoft Cloud, como Azure Portal, Azure Storage, Azure Virtual Machines (Linux y Windows), Azure Key Vault, PaaS y aplicaciones SaaS.

- Los recursos de su organización, como aplicaciones en Azure o los recursos de la red corporativa.

La protección de Azure AD debe tener máxima prioridad en la práctica de seguridad en la nube de su organización. Azure AD proporciona una puntuación de seguridad de la identidad para ayudarle a evaluar la posición de seguridad de las identidades en relación con los procedimientos recomendados de Microsoft. Use la puntuación para medir el grado de coincidencia de la configuración con los procedimientos recomendados y para hacer mejoras en la posición de seguridad.

Nota: Azure AD admite identidades externas que permiten a los usuarios que no tienen una cuenta de Microsoft iniciar sesión en sus aplicaciones y recursos mediante la identidad externa.

- [Inquilinos en Azure Active Directory](https://docs.microsoft.com/azure/active-directory/develop/single-and-multi-tenant-apps) 

- [Procedimiento para crear y configurar una instancia de Azure AD](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-access-create-new-tenant) 

- [Uso de proveedores de identidades externos para una aplicación](https://docs.microsoft.com/azure/active-directory/b2b/identity-providers) 

- [¿Qué es la puntuación de seguridad de la identidad en Azure Active Directory?](https://docs.microsoft.com/azure/active-directory/fundamentals/identity-secure-score)

**Supervisión de Azure Security Center**: No aplicable

**Responsabilidad**: Customer

### <a name="im-3-use-azure-ad-single-sign-on-sso-for-application-access"></a>IM-3: Uso del inicio de sesión único de Azure AD para acceder a las aplicaciones

**Guía**: Cloud App Security usa Azure Active Directory (Azure ad) para proporcionar administración de identidad y acceso a los recursos de Azure, las aplicaciones en la nube y las aplicaciones locales. Esto incluye no solo las identidades empresariales, como los empleados, sino también las identidades externas, como asociados y proveedores. Esto permite que el inicio de sesión único (SSO) administre y proteja el acceso a los datos y recursos de la organización locales y en la nube. Conecte todos los usuarios, las aplicaciones y los dispositivos al Azure AD para obtener un acceso seguro y sin problemas, y mayor visibilidad y control.

- [Descripción del inicio de sesión único de aplicaciones con Azure AD](https://docs.microsoft.com/azure/active-directory/manage-apps/what-is-single-sign-on)

**Supervisión de Azure Security Center**: No aplicable

**Responsabilidad**: Customer

### <a name="im-4-use-strong-authentication-controls-for-all-azure-active-directory-based-access"></a>IM-4: Uso de controles con autenticación multifactor sólida para todo el acceso basado en Azure Active Directory

**Guía**: Cloud App Security usa Azure Active Directory (Azure ad) que admite controles de autenticación segura a través de la autenticación multifactor y la autenticación con contraseñas.

- Autenticación multifactor: habilite la autenticación multifactor Azure AD y siga Azure Security Center recomendaciones de administración de identidades y acceso para la configuración de la autenticación multifactor. La autenticación multifactor se puede aplicar a todos los usuarios, seleccionar usuarios o a nivel de usuario en función de las condiciones de inicio de sesión y los factores de riesgo.

- Autenticación sin contraseña: hay disponibles tres opciones de autenticación sin contraseña: Windows Hello para empresas, aplicación Microsoft Authenticator y métodos de autenticación locales, como las tarjetas inteligentes.

Para administradores y usuarios con privilegios, asegúrese de que se usa el nivel más alto del método de autenticación sólida, seguido de la implementación de la directiva de autenticación sólida adecuada para otros usuarios.

- [Cómo habilitar la autenticación multifactor en Azure](https://docs.microsoft.com/azure/active-directory/authentication/howto-mfa-getstarted) 

- [Introducción a las opciones de autenticación sin contraseña de Azure Active Directory](https://docs.microsoft.com/azure/active-directory/authentication/concept-authentication-passwordless) 

- [Directiva de contraseñas predeterminada de Azure AD](https://docs.microsoft.com/azure/active-directory/authentication/concept-sspr-policy#password-policies-that-only-apply-to-cloud-user-accounts) 

- [Eliminación de contraseñas incorrectas mediante la Protección con contraseña de Azure AD](https://docs.microsoft.com/azure/active-directory/authentication/concept-password-ban-bad)

**Supervisión de Azure Security Center**: Sí

**Responsabilidad**: Customer

### <a name="im-6-restrict-azure-resource-access-based-on-conditions"></a>IM-6: Restricción del acceso a recursos de Azure en función de las condiciones

**Guía**: Cloud App Security admite el acceso condicional de Azure Active Directory (Azure ad) para un control de acceso más granular basado en condiciones definidas por el usuario, por ejemplo, los inicios de sesión de usuario de determinados intervalos IP deberán usar MFA para el inicio de sesión. Las directivas de administración de sesión de autenticación granular también se pueden usar para diferentes casos de uso.

- [Protección de control de aplicaciones de acceso condicional](https://docs.microsoft.com/cloud-app-security/what-is-cloud-app-security#conditional-access-app-control-protection)

- [Introducción al acceso condicional de Azure](https://docs.microsoft.com/azure/active-directory/conditional-access/overview) 

- [Directivas de acceso condicional habituales](https://docs.microsoft.com/azure/active-directory/conditional-access/concept-conditional-access-policy-common) 

- [Configuración de la administración de las sesiones de autenticación con el acceso condicional](https://docs.microsoft.com/azure/active-directory/conditional-access/howto-conditional-access-session-lifetime)

**Supervisión de Azure Security Center**: No aplicable

**Responsabilidad**: Customer

## <a name="privileged-access"></a>Acceso con privilegios

*Para más información, consulte [Azure Security Benchmark: Acceso con privilegios](/azure/security/benchmarks/security-controls-v2-privileged-access).*

### <a name="pa-1-protect-and-limit-highly-privileged-users"></a>PA-1: Protección y limitación de usuarios con privilegios elevados

**Guía**: Cloud App Security tiene las siguientes cuentas con privilegios elevados:

- Administrador global y Administrador de seguridad: los administradores con Acceso completo tienen permisos completos en Cloud App Security. Pueden agregar administradores, agregar directivas y opciones de configuración, cargar registros y realizar acciones de gobierno.
- Administrador de cumplimiento: tiene permisos de solo lectura y puede administrar alertas. No se puede tener acceso a recomendaciones de seguridad para plataformas en la nube. Puede crear y modificar directivas de archivo, permitir acciones de control de archivos y ver todos los informes integrados en Administración de datos.
- Administrador de datos de cumplimiento: tiene permisos de solo lectura, puede crear y modificar directivas de archivo, permitir acciones de control de archivos y ver todos los informes de detección. No se puede tener acceso a recomendaciones de seguridad para plataformas en la nube.
- Operador de seguridad: tiene permisos de solo lectura y puede administrar alertas.
- Lector de seguridad: tiene permisos de solo lectura y puede administrar alertas. El lector de seguridad no puede realizar las siguientes acciones:
  - Crear directivas o editar y cambiar las existentes
  - Desempeñar acciones de control

  - Cargar registros de detección

  - Prohibición o aprobación de aplicaciones de terceros

  - Obtener acceso a la página de configuración del intervalo de direcciones IP ni verla

  - Acceso y visualización de las páginas de configuración del sistema

  - Obtener acceso a la configuración de detección ni verla

  - Obtener acceso a la página de conectores de aplicaciones ni verla

  - Obtener acceso al registro de gobernanza ni verlo

  - Obtener acceso a la página de informes de instantáneas de administración ni verla

  - Acceso y edición del agente SIEM

- Lector global: tiene acceso de solo lectura completo a todos los aspectos de Cloud App Security. No se puede cambiar la configuración ni realizar ninguna acción.

Limite el número de roles o cuentas con privilegios elevados y proteja estas cuentas en un nivel elevado, ya que los usuarios con este privilegio pueden leer y modificar de forma directa o indirecta cada recurso en el entorno de Azure.

Puede habilitar el acceso con privilegios Just-in-Time (JIT) a los recursos de Azure y Azure AD mediante Azure AD Privileged Identity Management (PIM). JIT concede permisos temporales para realizar tareas con privilegios solo cuando los usuarios lo necesitan. PIM también puede generar alertas de seguridad cuando hay actividades sospechosas o no seguras en la organización de Azure AD.

- [Administrar el acceso de administrador en Cloud App Security](https://docs.microsoft.com/cloud-app-security/manage-admins)

**Supervisión de Azure Security Center**: Sí

**Responsabilidad**: Customer

### <a name="pa-2-restrict-administrative-access-to-business-critical-systems"></a>PA-2: Restricción del acceso administrativo a los sistemas críticos para la empresa

**Guía**: Cloud App Security ofrece control de acceso basado en roles para administradores.

- [Administrar el acceso de administrador de Cloud App Security](https://docs.microsoft.com/cloud-app-security/manage-admins)

**Supervisión de Azure Security Center**: Sí

**Responsabilidad**: Customer

### <a name="pa-3-review-and-reconcile-user-access-regularly"></a>PA-3: Revisión y conciliación de manera periódica del acceso de los usuarios

**Guía**: Cloud App Security usa cuentas de Azure Active Directory (Azure ad) para administrar sus recursos, revisar las cuentas de usuario y obtener acceso a las asignaciones periódicamente para asegurarse de que las cuentas y el acceso sean válidos. Puede usar las revisiones de acceso de Azure AD para revisar las pertenencias a grupos, el acceso a las aplicaciones empresariales y las asignaciones de roles. Los informes de Azure AD pueden proporcionar registros para ayudar a detectar cuentas obsoletas. También puede usar Azure AD Privileged Identity Management para crear un flujo de trabajo de informe de revisión de acceso para facilitar el proceso de revisión.

Además, se puede configurar Azure Privileged Identity Management para enviar una alerta cuando se cree un número de cuentas de administrador excesivo y para identificar las cuentas de administrador que hayan quedado obsoletas o que no estén configuradas correctamente.

Nota: Algunos servicios de Azure admiten usuarios y roles locales que no se administran mediante Azure AD. Estos usuarios deberán administrarse por separado.

- [Creación de una revisión de acceso de los roles de recursos de Azure en Privileged Identity Management (PIM)](https://docs.microsoft.com/azure/active-directory/privileged-identity-management/pim-resource-roles-start-access-review) 

- [Procedimiento para usar las revisiones de acceso e identidades de Azure AD](https://docs.microsoft.com/azure/active-directory/governance/access-reviews-overvie)

**Supervisión de Azure Security Center**: Sí

**Responsabilidad**: Customer

### <a name="pa-4-set-up-emergency-access-in-azure-ad"></a>PA-4: Configuración del acceso de emergencia en Azure AD

**Guía**: Cloud App Security usa Azure Active Directory (Azure ad) para administrar sus recursos. Para evitar que se le bloquee por accidente el acceso a la organización de Azure AD, configure una cuenta de acceso de emergencia para cuando no se puedan usar cuentas administrativas normales. Las cuentas de acceso de emergencia suelen tener privilegios elevados y no deben asignarse a usuarios específicos. Las cuentas de acceso de emergencia se limitan a situaciones "excepcionales" o de emergencia en las que no se pueden usar las cuentas administrativas normales.

Debe asegurarse de que las credenciales (como contraseña, certificado o tarjeta inteligente) para las cuentas de acceso de emergencia se mantengan seguras y solo las conozcan las personas autorizadas para usarlas en caso de emergencia.

- [Administración de cuentas de acceso de emergencia en Azure AD](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-emergency-access)

**Supervisión de Azure Security Center**: No aplicable

**Responsabilidad**: Customer

### <a name="pa-5-automate-entitlement-management"></a>PA-5: Automatización de la administración de derechos 

**Guía**: Cloud App Security se integra con Azure Active Directory (Azure ad) para administrar sus recursos. Use las características de administración de derechos de Azure AD para automatizar los flujos de trabajo de solicitud de acceso, como las asignaciones, las revisiones y la expiración del acceso. También se admite la aprobación en dos o varias fases.

- [¿Qué son las revisiones de acceso de Azure AD?](https://docs.microsoft.com/azure/active-directory/governance/access-reviews-overview) 

- [¿Qué es la administración de derechos de Azure AD?](https://docs.microsoft.com/azure/active-directory/governance/entitlement-management-overview)

**Supervisión de Azure Security Center**: No aplicable

**Responsabilidad**: Customer

### <a name="pa-7-follow-just-enough-administration-least-privilege-principle"></a>PA-7: Seguimiento de solo una administración suficiente (principio de privilegios mínimos) 

**Guía**: Cloud App Security se integra con el control de acceso basado en rol (RBAC) de Azure para administrar sus recursos. Azure RBAC le permite administrar el acceso a los recursos de Azure mediante las asignaciones de roles. Puede asignar estos roles a usuarios, grupos de entidades de servicio e identidades administradas. Hay roles integrados predefinidos para determinados recursos, y estos roles se pueden inventariar o consultar mediante herramientas, como la CLI de Azure, Azure PowerShell o el Azure Portal. Los privilegios que asigne a los recursos a través de Azure RBAC siempre se deben limitar a los requisitos de los roles. Este modelo complementa el enfoque Just-in-Time (JIT) de Azure AD Privileged Identity Management (PIM) y se debe revisar periódicamente.

Use los roles integrados para asignar los permisos, y cree solo los roles personalizados cuando sea necesario.

- [Roles de Office 365 y de Azure AD con acceso a Cloud App Security](https://docs.microsoft.com/cloud-app-security/manage-admins)

Qué es el control de acceso basado en roles de Azure (RBAC de Azure) https://docs.microsoft.com/azure/role-based-access-control/overview 

- [Configuración de RBAC en Azure](https://docs.microsoft.com/azure/role-based-access-control/role-assignments-portal) 

- [Procedimiento para usar las revisiones de acceso e identidades de Azure AD](https://docs.microsoft.com/azure/active-directory/governance/access-reviews-overview)

**Supervisión de Azure Security Center**: Sí

**Responsabilidad**: Customer

## <a name="data-protection"></a>Protección de datos

*Para más información, consulte [Azure Security Benchmark: protección de datos](/azure/security/benchmarks/security-controls-v2-data-protection).*

### <a name="dp-2-protect-sensitive-data"></a>DP-2: Protección de datos confidenciales

**Guía**: Cloud App Security administra los datos confidenciales y utiliza Azure ad roles para controlar los permisos de diferentes tipos de datos.

- [Azure AD roles con acceso a Cloud App Security](https://docs.microsoft.com/cloud-app-security/manage-admins#office-365-and-azure-ad-roles-with-access-to-cloud-app-security)

**Supervisión de Azure Security Center**: Sí

**Responsabilidad**: Customer

### <a name="dp-4-encrypt-sensitive-information-in-transit"></a>DP-4: Cifrado de la información confidencial en tránsito

**Guía**: Cloud App Security admite el cifrado de datos en tránsito con TLS v 1.2 o posterior.

Aunque esto es opcional en el caso del tráfico de redes privadas, es fundamental para el tráfico de redes externas y públicas. Asegúrese de que los clientes que se conectan a los recursos de Azure puedan negociar TLS v1.2 o superior. Para la administración remota, use SSH (para Linux) o RDP/TLS (para Windows) en lugar de un protocolo sin cifrar. Se deben deshabilitar los protocolos y las versiones de SSL, TLS y SSH obsoletos, y los cifrados débiles.

De forma predeterminada, Azure proporciona el cifrado de los datos en tránsito entre los centros de datos de Azure.

- [Seguridad y privacidad de los datos de Microsoft Cloud App Security](https://docs.microsoft.com/cloud-app-security/cas-compliance-trust#encryption)

- [Descripción del cifrado en tránsito con Azure](https://docs.microsoft.com/azure/security/fundamentals/encryption-overview#encryption-of-data-in-transit) 

- [Información sobre la seguridad de TLS](https://docs.microsoft.com/security/engineering/solving-tls1-problem) 

- [Cifrado doble para datos de Azure en tránsito](https://docs.microsoft.com/azure/security/fundamentals/double-encryption#data-in-transit)

**Supervisión de Azure Security Center**: No aplicable

**Responsabilidad**: Compartido

## <a name="asset-management"></a>Administración de recursos

*Para más información, consulte [Azure Security Benchmark: Administración de recursos](/azure/security/benchmarks/security-controls-v2-asset-management).*

### <a name="am-1-ensure-security-team-has-visibility-into-risks-for-assets"></a>AM-1: Asegurarse de que el equipo de seguridad tiene visibilidad sobre los riesgos para los recursos

**Guía**: Asegúrese de que se conceden a los equipos de seguridad permisos de lector de seguridad en el inquilino y las suscripciones de Azure para que puedan supervisar los riesgos de seguridad mediante Azure Security Center. 

En función de la estructura de las responsabilidades del equipo de seguridad, la supervisión de los riesgos de seguridad puede ser responsabilidad del equipo de seguridad central o de un equipo local. Dicho esto, la información y los riesgos de seguridad siempre se deben agregar de forma centralizada dentro de una organización. 

Los permisos de lector de seguridad se pueden aplicar en general a un inquilino completo (grupo de administración raíz) o a grupos de administración o a suscripciones específicas. 

Nota: Es posible que se requieran permisos adicionales para obtener visibilidad de las cargas de trabajo y los servicios. 

- [Introducción al rol de lector de seguridad](https://docs.microsoft.com/azure/role-based-access-control/built-in-roles#security-reader)

- [Información general sobre los grupos de administración de Azure](https://docs.microsoft.com/azure/governance/management-groups/overview)

**Supervisión de Azure Security Center**: no disponible actualmente

**Responsabilidad**: Customer

## <a name="logging-and-threat-detection"></a>registro y detección de amenazas

*Para más información, consulte [Azure Security Benchmark: registro y detección de amenazas](/azure/security/benchmarks/security-controls-v2-logging-threat-protection).*

### <a name="lt-1-enable-threat-detection-for-azure-resources"></a>LT-1: Habilitación de la detección de amenazas para recursos de Azure

**Guía**: reenvíe los registros desde Cloud App Security a su Siem, que se puede usar para configurar detecciones de amenazas personalizadas. Asegúrese de que está supervisando distintos tipos de recursos de Azure para detectar posibles amenazas y anomalías. Céntrese en obtener alertas de alta calidad para reducir los falsos positivos que deben revisar los analistas. Las alertas se pueden crear a partir de datos de registro, agentes u otros datos.

- [Integración de Azure Sentinel](https://docs.microsoft.com/cloud-app-security/siem-sentinel)
- [Integración de SIEM genérica](https://docs.microsoft.com/cloud-app-security/siem)

- [Creación de reglas de análisis personalizadas para detectar amenazas](https://docs.microsoft.com/azure/sentinel/tutorial-detect-threats-custom) 

- [Inteligencia sobre amenazas cibernéticas con Azure Sentinel](https://docs.microsoft.com/azure/architecture/example-scenario/data/sentinel-threat-intelligence)

**Supervisión de Azure Security Center**: No aplicable

**Responsabilidad**: Customer

## <a name="incident-response"></a>Respuesta a los incidentes

*Para más información, consulte [Azure Security Benchmark: respuesta ante incidentes](/azure/security/benchmarks/security-controls-v2-incident-response).*

### <a name="ir-1-preparation--update-incident-response-process-for-azure"></a>IR-1: Preparación: actualización del proceso de respuesta a incidentes para Azure

**Guía**: Asegúrese de que la organización tenga procesos para responder a incidentes de seguridad, que haya actualizado estos procesos para Azure y que los ejercite regularmente para garantizar su disponibilidad.

- [Implementación de la seguridad en todo el entorno empresarial](https://docs.microsoft.com/azure/cloud-adoption-framework/security/security-top-10#4-process-update-incident-response-ir-processes-for-cloud)

- [Guía de referencia de respuesta a incidentes](https://docs.microsoft.com/microsoft-365/downloads/IR-Reference-Guide.pdf)

**Supervisión de Azure Security Center**: No aplicable

**Responsabilidad**: Customer

### <a name="ir-2-preparation--setup-incident-notification"></a>IR-2: Preparación: notificación de incidentes de configuración

**Guía**: Configure la información de contacto en caso de incidentes de seguridad en Azure Security Center. Microsoft utilizará esta información para ponerse en contacto con usted si el Centro de respuestas de seguridad de Microsoft (MSRC) detecta que un tercero no autorizado o ilegal ha accedido a sus datos. También tiene opciones para personalizar las alertas y notificaciones de incidentes en diferentes servicios de Azure en función de sus necesidades de respuesta a incidentes. 

- [Establecimiento del contacto de seguridad de Azure Security Center](https://docs.microsoft.com/azure/security-center/security-center-provide-security-contact-details)

**Supervisión de Azure Security Center**: Sí

**Responsabilidad**: Customer

### <a name="ir-3-detection-and-analysis--create-incidents-based-on-high-quality-alerts"></a>IR-3: Detección y análisis: creación de incidentes en función de alertas de alta calidad

**Guía**: Asegúrese de que cuenta con un proceso para crear alertas de alta calidad y medir la calidad de las alertas. Esto le permite aprender de incidentes anteriores y clasificar las alertas para los analistas, de modo que no pierdan tiempo con falsos positivos. 

Las alertas de alta calidad se pueden crear en función de la experiencia de pasados incidentes, información validada procedente de la comunidad y herramientas diseñadas para generar y limpiar alertas mediante la fusión y correlación de diversos orígenes de la señal. 

Azure Security Center (ASC) proporciona alertas de alta calidad en muchos recursos de Azure. Puede usar el conector de datos de ASC para enviar las alertas a Azure Sentinel. Azure Sentinel le permite crear reglas de alerta avanzadas con el fin de generar automáticamente incidentes para investigar. 

Exporte las alertas y recomendaciones de Azure Security Center mediante la característica de exportación para ayudar a identificar riesgos en los recursos de Azure. Esta exportación puede hacerse de forma manual o de modo continuo.

- [Configuración de la exportación](https://docs.microsoft.com/azure/security-center/continuous-export)

- [Transmisión de alertas a Azure Sentinel](https://docs.microsoft.com/azure/sentinel/connect-azure-security-center)

**Supervisión de Azure Security Center**: no disponible actualmente

**Responsabilidad**: Customer

### <a name="ir-4-detection-and-analysis--investigate-an-incident"></a>IR-4: Detección y análisis: investigación de incidentes

**Guía**: Asegúrese de que los analistas pueden consultar y usar diversos orígenes de datos a medida que investigan posibles incidentes, para conseguir una visión global de lo que ha sucedido. Se deben recopilar diversos registros para realizar un seguimiento de las actividades de un posible atacante en la cadena de eliminación para evitar puntos ciegos.  También debe asegurarse de que se capturan detalles y aprendizajes para otros analistas y para futuras referencias históricas.  

Los orígenes de datos para la investigación incluyen los orígenes de registro centralizados que ya se recopilan de los servicios en el ámbito y los sistemas en ejecución, pero también pueden incluir:

- Datos de red: use registros de flujo de grupos de seguridad de red, Azure Network Watcher y Azure Monitor para capturar registros de flujo de red y otra información de análisis. 

- Instantáneas de sistemas en ejecución: 

    - Use la funcionalidad de instantáneas de la máquina virtual de Azure para crear una instantánea del disco del sistema en ejecución. 

    - Use la funcionalidad de volcado de la memoria nativa del sistema operativo para crear una instantánea de la memoria del sistema en ejecución.

    - Use la característica de instantánea de los servicios de Azure o la propia funcionalidad del software para crear instantáneas de los sistemas en ejecución.

Azure Sentinel proporciona amplios análisis de datos en prácticamente cualquier origen de registro y un portal de administración de casos para administrar todo el ciclo de vida de los incidentes. La información de inteligencia durante una investigación puede asociarse a un incidente con fines de seguimiento e informes. 

- [Instantánea del disco de una máquina Windows](https://docs.microsoft.com/azure/virtual-machines/windows/snapshot-copy-managed-disk)

- [Instantánea del disco de una máquina Linux](https://docs.microsoft.com/azure/virtual-machines/linux/snapshot-copy-managed-disk)

- [Recopilación del volcado de memoria e información de diagnóstico del servicio de soporte técnico de Microsoft Azure](https://azure.microsoft.com/support/legal/support-diagnostic-information-collection/) 

- [Investigación de incidentes con Azure Sentinel](https://docs.microsoft.com/azure/sentinel/tutorial-investigate-cases)

**Supervisión de Azure Security Center**: No aplicable

**Responsabilidad**: Customer

### <a name="ir-5-detection-and-analysis--prioritize-incidents"></a>IR-5: Detección y análisis: clasificar incidentes

**Guía**: Proporcione contexto a los analistas sobre los incidentes en los que deberán centrarse en primer lugar en función de la gravedad de la alerta y la confidencialidad de los recursos. 

Azure Security Center asigna una gravedad a cada alerta para ayudarle a priorizar aquellas que se deben investigar en primer lugar. La gravedad se basa en la confianza que tiene Security Center en la búsqueda o en el análisis utilizados para emitir la alerta, así como en el nivel de confianza de que ha habido un intento malintencionado detrás de la actividad que ha provocado la alerta.

Adicionalmente, marque los recursos con etiquetas y cree un sistema de nomenclatura para identificar y clasificar los recursos de Azure, especialmente los que procesan datos confidenciales.  Es su responsabilidad asignar prioridades a la corrección de las alertas en función de la importancia de los recursos y el entorno de Azure donde se produjo el incidente.

- [Alertas de seguridad en el Centro de seguridad de Azure](https://docs.microsoft.com/azure/security-center/security-center-alerts-overview)

- [Uso de etiquetas para organizar los recursos de Azure](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-using-tags)

**Supervisión de Azure Security Center**: no disponible actualmente

**Responsabilidad**: Customer

### <a name="ir-6-containment-eradication-and-recovery--automate-the-incident-handling"></a>IR-6: Contención, erradicación y recuperación: automatización del control de incidentes

**Guía**: Automatice las tareas repetitivas manuales para acelerar el tiempo de respuesta y reducir la carga de los analistas. Las tareas manuales tardan más tiempo en ejecutarse, ralentizando cada incidente y reduciendo el número de incidentes que un analista puede controlar. Las tareas manuales también aumentan la fatiga del analista, lo que aumenta el riesgo del error humano que produce retrasos y reduce la capacidad de los analistas de centrarse de manera efectiva en tareas complejas. Use las características de automatización de flujo de trabajo de Azure Security Center y Azure Sentinel para desencadenar acciones automáticamente o ejecutar un cuaderno de estrategias para responder a las alertas de seguridad entrantes. El cuaderno de estrategias lleva a cabo acciones, como el envío de notificaciones, la deshabilitación de cuentas y el aislamiento de redes problemáticas. 

- [Configuración de la automatización de flujos de trabajo en Security Center](https://docs.microsoft.com/azure/security-center/workflow-automation)

- [Configuración de respuestas automatizadas frente a amenazas en Azure Security Center](https://docs.microsoft.com/azure/security-center/tutorial-security-incident#triage-security-alerts)

- [Configuración de respuestas automatizadas frente a amenazas en Azure Sentinel](https://docs.microsoft.com/azure/sentinel/tutorial-respond-threats-playbook)

**Supervisión de Azure Security Center**: no disponible actualmente

**Responsabilidad**: Customer

## <a name="posture-and-vulnerability-management"></a>administración de posturas y vulnerabilidades

*Para más información, consulte [Azure Security Benchmark: administración de posturas y vulnerabilidades](/azure/security/benchmarks/security-controls-v2-vulnerability-management).*

### <a name="pv-8-conduct-regular-attack-simulation"></a>PV-8: realización de una simulaciones de ataques periódicas

**Guía**: Según sea necesario, realice pruebas de penetración o actividades de equipo rojo en los recursos de Azure y asegúrese de corregir todos los resultados de seguridad críticos.
siga las reglas de compromiso de la prueba de penetración de Microsoft Cloud para asegurarse de que las pruebas de penetración no infrinjan las directivas de Microsoft. Use la estrategia de Microsoft y la ejecución de las pruebas de penetración del equipo rojo y sitios activos en la infraestructura de nube, los servicios y las aplicaciones administradas por Microsoft.

- [Pruebas de penetración en Azure](https://docs.microsoft.com/azure/security/fundamentals/pen-testing)

- [Reglas de interacción de las pruebas de penetración](https://www.microsoft.com/msrc/pentest-rules-of-engagement?rtc=1) 

- [Equipo rojo de Microsoft Cloud](https://gallery.technet.microsoft.com/Cloud-Red-Teaming-b837392e)

**Supervisión de Azure Security Center**: No aplicable

**Responsabilidad**: Compartido

## <a name="governance-and-strategy"></a>Gobernanza y estrategia

*Para más información, consulte [Azure Security Benchmark: gobernanza y estrategia](/azure/security/benchmarks/security-controls-v2-governance-strategy).*

### <a name="gs-1-define-asset-management-and-data-protection-strategy"></a>GS-1: Definición de la estrategia de protección de datos y administración de recursos 

**Guía**: Asegúrese de documentar y comunicar una estrategia clara para la protección y supervisión continua de sistemas y datos. Dé prioridad a la detección, evaluación, protección y supervisión de los sistemas y datos críticos para la empresa. 

Esta estrategia debe incluir instrucciones, directivas y estándares documentados para los siguientes elementos: 

-   Norma de clasificación de datos de acuerdo con los riesgos empresariales

-   Visibilidad en la organización de seguridad de los riesgos y el inventario de recursos 

-   Aprobación de la organización de seguridad de los servicios de Azure para su uso 

-   Seguridad de los recursos durante su ciclo de vida

-   Estrategia de control de acceso necesaria según la clasificación de datos de la organización

-   Uso de las funcionalidades nativas de Azure y protección de datos de terceros

-   Requisitos de cifrado de datos para casos de uso en tránsito y en reposo

-   Normas criptográficas adecuadas

Para más información, consulte las siguientes referencias:
- [Recomendación para la arquitectura de seguridad de Azure: almacenamiento, datos y cifrado](https://docs.microsoft.com/azure/architecture/framework/security/storage-data-encryption?toc=/security/compass/toc.json&amp;bc=/security/compass/breadcrumb/toc.json)

- [Aspectos básicos de la seguridad de Azure: seguridad, cifrado y almacenamiento de datos de Azure](https://docs.microsoft.com/azure/security/fundamentals/encryption-overview)

- [Cloud Adoption Framework: procedimientos recomendados de cifrado y seguridad de los datos de Azure](https://docs.microsoft.com/azure/security/fundamentals/data-encryption-best-practices?toc=/azure/cloud-adoption-framework/toc.json&amp;bc=/azure/cloud-adoption-framework/_bread/toc.json)

- [Azure Security Benchmark: administración de recursos](https://docs.microsoft.com/azure/security/benchmarks/security-benchmark-v2-asset-management)

- [Azure Security Benchmark: protección de datos](https://docs.microsoft.com/azure/security/benchmarks/security-benchmark-v2-data-protection)

**Supervisión de Azure Security Center**: No aplicable

**Responsabilidad**: Customer

### <a name="gs-2-define-enterprise-segmentation-strategy"></a>GS-2: Definición de una estrategia de segmentación empresarial 

**Guía**: Establezca en toda la empresa una estrategia para segmentar el acceso a los recursos mediante una combinación de identidad, red, aplicación, suscripción, grupo de administración y otros controles.

Equilibre concienzudamente la necesidad de separación de seguridad con la necesidad de habilitar el funcionamiento diario de los sistemas que necesitan comunicarse entre sí y acceder a los datos.

Asegúrese de que la estrategia de segmentación se implementa de forma coherente en todos los tipos de control, como la seguridad de red, los modelos de identidad y acceso, y los modelos de acceso y permisos de las aplicaciones, y los controles de los procesos humanos.

- [Guía de la estrategia de segmentación en Azure (vídeo)](https://docs.microsoft.com/security/compass/microsoft-security-compass-introduction#azure-components-and-reference-model-2151)

- [Guía de la estrategia de segmentación en Azure (documento)](https://docs.microsoft.com/security/compass/governance#enterprise-segmentation-strategy)

- [Alineación de la segmentación de red con la estrategia de segmentación empresarial](https://docs.microsoft.com/security/compass/network-security-containment#align-network-segmentation-with-enterprise-segmentation-strategy)

**Supervisión de Azure Security Center**: No aplicable

**Responsabilidad**: Customer

### <a name="gs-3-define-security-posture-management-strategy"></a>GS-3: Definición de la estrategia de administración de la posición de seguridad

**Guía**: Mida y mitigue continuamente los riesgos de los recursos individuales y el entorno en el que se hospedan. Dé prioridad a los activos de gran valor y a las superficies de ataque muy expuestas, como las aplicaciones publicadas, los puntos de entrada y salida de red, los puntos de conexión de usuario y administrador, etc.

- [Azure Security Benchmark: administración de posturas y vulnerabilidades](https://docs.microsoft.com/azure/security/benchmarks/security-benchmark-v2-posture-vulnerability-management)

**Supervisión de Azure Security Center**: No aplicable

**Responsabilidad**: Customer

### <a name="gs-4-align-organization-roles-responsibilities-and-accountabilities"></a>GS-4: Alineación de los roles y responsabilidades de la organización

**Guía**: Asegúrese de documentar y comunicar una estrategia clara para los roles y las responsabilidades de la organización de seguridad. Dé prioridad a ofrecer una responsabilidad clara en las decisiones de seguridad, a proporcionar a todos los usuarios formación sobre el modelo de responsabilidad compartida y a los equipos técnicos sobre la tecnología para proteger la nube.

- [Procedimiento recomendado de seguridad de Azure 1. Personas: Formación del equipo sobre el recorrido de seguridad de la nube](https://docs.microsoft.com/azure/cloud-adoption-framework/security/security-top-10#1-people-educate-teams-about-the-cloud-security-journey)

- [Procedimiento recomendado de seguridad de Azure 2. Personas: Formación del equipo en tecnología de seguridad de la nube](https://docs.microsoft.com/azure/cloud-adoption-framework/security/security-top-10#2-people-educate-teams-on-cloud-security-technology)

- [Procedimiento recomendado de seguridad de Azure 3. Proceso: Asignación de responsabilidades por las decisiones de seguridad en la nube](https://docs.microsoft.com/azure/cloud-adoption-framework/security/security-top-10#4-process-update-incident-response-ir-processes-for-cloud)

**Supervisión de Azure Security Center**: No aplicable

**Responsabilidad**: Customer

### <a name="gs-5-define-network-security-strategy"></a>GS-5: Definición de la estrategia de seguridad de red

**Guía**: Establezca un enfoque de seguridad de red de Azure como parte de la estrategia de control de acceso de seguridad general de su organización.  

Esta estrategia debe incluir instrucciones, directivas y estándares documentados para los siguientes elementos: 

-   Centralización de la responsabilidad de seguridad y la administración de redes

-   Modelo de segmentación de la red virtual alineado con la estrategia de segmentación empresarial

-   Estrategia de corrección en diferentes escenarios de amenazas y ataques

-   Estrategia de entrada y salida y perimetral de Internet

-   Estrategia de interconectividad entre el entorno local y la nube híbrida

-   Artefactos de seguridad de red actualizados (por ejemplo, diagramas de red y arquitectura de red de referencia)

Para más información, consulte las siguientes referencias:
- [Procedimiento recomendado de seguridad de Azure 11. Arquitectura: Establecimiento de una estrategia de seguridad unificada](https://docs.microsoft.com/azure/cloud-adoption-framework/security/security-top-10#11-architecture-establish-a-single-unified-security-strategy)

- [Azure Security Benchmark: seguridad de red](https://docs.microsoft.com/azure/security/benchmarks/security-benchmark-v2-network-security)

- [Azure Network Security Overview (Información general sobre Azure Network Security)](https://docs.microsoft.com/azure/security/fundamentals/network-overview)

- [Estrategia para la arquitectura de red empresarial](https://docs.microsoft.com/azure/cloud-adoption-framework/ready/enterprise-scale/architecture)

**Supervisión de Azure Security Center**: No aplicable

**Responsabilidad**: Customer

### <a name="gs-6-define-identity-and-privileged-access-strategy"></a>GS-6: Definición de la estrategia de acceso con privilegios e identidades

**Guía**: Establezca una identidad de Azure y enfoques de acceso con privilegios como parte de la estrategia de control de acceso de seguridad general de su organización.  

Esta estrategia debe incluir instrucciones, directivas y estándares documentados para los siguientes elementos: 

-   Un sistema de identidad y autenticación centralizado y su interconectividad con otros sistemas de identidad internos y externos

-   Métodos de autenticación sólida en diferentes casos de uso y condiciones

-   Protección de usuarios con privilegios elevados

-   Supervisión y control de anomalías en las actividades de los usuarios  

-   Proceso de revisión y conciliación del acceso y la identidad de los usuarios

Para más información, consulte las siguientes referencias:

- [Azure Security Benchmark: administración de identidades](https://docs.microsoft.com/azure/security/benchmarks/security-benchmark-v2-identity-management)

- [Azure Security Benchmark: acceso con privilegios](https://docs.microsoft.com/azure/security/benchmarks/security-benchmark-v2-privileged-access)

- [Procedimiento recomendado de seguridad de Azure 11. Arquitectura: Establecimiento de una estrategia de seguridad unificada](https://docs.microsoft.com/azure/cloud-adoption-framework/security/security-top-10#11-architecture-establish-a-single-unified-security-strategy)

- [Información general sobre seguridad de administración de identidades de Azure](https://docs.microsoft.com/azure/security/fundamentals/identity-management-overview)

**Supervisión de Azure Security Center**: No aplicable

**Responsabilidad**: Customer

### <a name="gs-7-define-logging-and-threat-response-strategy"></a>GS-7: Definición de la estrategia de registro y respuesta a amenazas

**Guía**: Establezca una estrategia de registro y respuesta a amenazas para detectar y corregir rápidamente las amenazas mientras cumple los requisitos de cumplimiento. Para dar prioridad, proporcione a los analistas alertas de alta calidad y experiencias sin problemas para que puedan centrarse en las amenazas en lugar de los pasos manuales y de integración. 

Esta estrategia debe incluir instrucciones, directivas y estándares documentados para los siguientes elementos: 

-   Las responsabilidades y el rol de la organización en las operaciones de seguridad (SecOps) 

-   Un proceso de respuesta a incidentes bien definido que esté alineado con NIST u otro marco del sector. 

-   Captura y retención de registros para admitir la detección de amenazas, la respuesta ante incidentes y las necesidades de cumplimiento

-   Visibilidad y correlación centralizada de la información sobre amenazas, mediante SIEM, funcionalidades nativas de Azure y otros orígenes 

-   Plan de comunicación y notificación con sus clientes, proveedores y entidades públicas de interés

-   Uso de plataformas nativas de Azure y de terceros para el tratamiento de incidentes, como el registro y la detección de amenazas, los análisis forenses y la corrección y erradicación de ataques

-   Procesos para controlar incidentes y actividades posteriores a incidentes, como las lecciones aprendidas y la retención de pruebas

Para más información, consulte las siguientes referencias:

- [Azure Security Benchmark: registro y detección de amenazas](https://docs.microsoft.com/azure/security/benchmarks/security-benchmark-v2-logging-threat-detection)

- [Azure Security Benchmark: respuesta a incidentes](https://docs.microsoft.com/azure/security/benchmarks/security-benchmark-v2-incident-response)

- [Procedimiento recomendado de seguridad de Azure 4. Proceso: Actualización de los procesos de respuesta a incidentes para la nube](https://docs.microsoft.com/azure/cloud-adoption-framework/security/security-top-10#4-process-update-incident-response-ir-processes-for-cloud)

- [Guía de decisiones sobre registros e informes en Azure Adoption Framework](https://docs.microsoft.com/azure/cloud-adoption-framework/decision-guides/logging-and-reporting/)

- [Escala, administración y supervisión empresarial de Azure](https://docs.microsoft.com/azure/cloud-adoption-framework/ready/enterprise-scale/management-and-monitoring)

**Supervisión de Azure Security Center**: No aplicable

**Responsabilidad**: Customer

## <a name="next-steps"></a>Pasos siguientes

- Consulte la [Información general sobre Azure Security Benchmark V2](/azure/security/benchmarks/overview).
- Obtenga más información sobre las [líneas de base de seguridad de Azure](/azure/security/benchmarks/security-baselines-overview).
