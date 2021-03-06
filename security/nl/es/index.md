{:new_window: target="_blank"}
{:shortdesc: .shortdesc}

# Seguridad de {{site.data.keyword.Bluemix_notm}}
{: #security}
*Última actualización: 7 de diciembre de 2015*

Diseñada con prácticas de ingeniería seguras, la plataforma {{site.data.keyword.Bluemix}} dispone de controles de seguridad de varios niveles de la red y de la infraestructura. {{site.data.keyword.Bluemix_notm}} ofrece una serie de servicios de seguridad que pueden utilizar los desarrolladores de apps para proteger sus apps móviles y web. Estos elementos se combinan para convertir {{site.data.keyword.Bluemix_notm}} en una plataforma con opciones claras para el desarrollo de apps seguras.
{:shortdesc}

{{site.data.keyword.Bluemix_notm}} garantiza la seguridad mediante el cumplimiento con las políticas de seguridad derivadas de prácticas recomendadas en IBM para sistemas, redes e ingeniería segura. Estas políticas incluyen prácticas como exploración de código, exploración dinámica, modelado de amenazas y pruebas de penetración. {{site.data.keyword.Bluemix_notm}} sigue el proceso IBM Product Security Incident Response Team (PSIRT) en cuanto a la gestión de incidentes relacionados con la seguridad. Consulte el sitio [IBM Security Vulnerability Management (PSIRT)](http://www-03.ibm.com/security/secure-engineering/process.html){: new_window} para ver detalles.

{{site.data.keyword.Bluemix_notm}} público y dedicado utiliza los servicios de nube de IBM SoftLayer Infrastructure-as-a-Service (IaaS) y aprovecha su arquitectura de seguridad. SoftLayer IaaS proporciona varias capas de protección solapadas para sus apps y datos. En {{site.data.keyword.Bluemix_notm}} local, usted es el propietario de la seguridad física y proporciona
la infraestructura alojando {{site.data.keyword.Bluemix_notm}} local en su propio centro de datos detrás de un cortafuegos de la empresa. Además, {{site.data.keyword.Bluemix_notm}} incorpora funciones de seguridad en la capa de Plataforma como servicio en distintas categorías: plataforma, datos y app.

## Seguridad de la plataforma {{site.data.keyword.Bluemix_notm}}
{: #platform-security}

{{site.data.keyword.Bluemix_notm}} proporciona seguridad funcional, de infraestructura, operativa y física para la plataforma (a través de IBM SoftLayer) para la plataforma principal. Sin embargo, {{site.data.keyword.Bluemix_notm}} local es exclusivo en el sentido de que el cliente proporciona la infraestructura y el centro de datos, a la vez que es propietario de la seguridad física.

El entorno {{site.data.keyword.Bluemix_notm}} en SoftLayer cumple con los estándares de seguridad de tecnología de la información (TI) más restrictivos de IBM, que se ajustan o superan los estándares del sector. Estos estándares incluyen lo siguiente:
Red, cifrado de datos y control de acceso
 * ACL de aplicación, permisos y pruebas de penetración
 * Identificación, autenticación y autorización
 * Información y protección de datos
 * Integridad y disponibilidad de servicios
 * Gestión de puntos vulnerables y de arreglos
 * Denegación de servicio y detección de ataques sistemáticos
 * Respuesta ante incidencias de seguridad

![Visión general de la seguridad de la plataforma Bluemix](images/platform_sec.svg)

*Figura 1. Visión general de seguridad de la plataforma {{site.data.keyword.Bluemix_notm}}*

Con {{site.data.keyword.Bluemix_notm}} local, puede alojar {{site.data.keyword.Bluemix_notm}} detrás del cortafuegos de la empresa y en el centro de datos. Por lo tanto, usted es responsable de determinados aspectos de seguridad. La imagen siguiente detalla las partes de seguridad que son propiedad del cliente y las partes de seguridad que gestiona y mantiene IBM.

![Visión general de la seguridad de la plataforma Bluemix Local](images/security_local_platform.svg)

*Figura 2. Visión general de seguridad de la plataforma {{site.data.keyword.Bluemix_notm}} Local*

IBM instala, supervisa de forma remota y gestiona {{site.data.keyword.Bluemix_notm}} local en el centro de datos mediante Relay (relé), una funcionalidad de entrega incluida con {{site.data.keyword.Bluemix_notm}} local. El relé se conecta de forma segura con certificados específicos de cada instancia de {{site.data.keyword.Bluemix_notm}} local. Para obtener más información sobre {{site.data.keyword.Bluemix_notm}} local y Relay, consulte [Bluemix local](../local/index.html).

### Seguridad funcional

{{site.data.keyword.Bluemix_notm}} proporciona diversas funciones de seguridad funcional, que incluyen autenticación de usuarios, autorización de accesos, auditoría de operaciones críticas y protección de datos.

<dl>
<dt>Autenticación</dt>
<dd>Los desarrolladores de aplicaciones se autentican ante {{site.data.keyword.Bluemix_notm}} mediante la identidad web de IBM.

Para {{site.data.keyword.Bluemix_notm}} dedicado y local, la autenticación a través LDAP recibe soporte de forma predeterminado. A petición, se puede configurar la autenticación a través de IBM Web Identity en lugar de para {{site.data.keyword.Bluemix_notm}}.
</dd>

<dt>Autorización</dt>
<dd>{{site.data.keyword.Bluemix_notm}} utiliza mecanismos de Cloud Foundry para asegurarse de que cada desarrollador de apps tiene acceso únicamente a las apps e instancias de servicio que ha creado. La autorización sobre los servicios de {{site.data.keyword.Bluemix_notm}} se basa en OAuth. El acceso a los puntos finales internos de la plataforma {{site.data.keyword.Bluemix_notm}} está restringido para los usuarios externos.</dd>

<dt>Auditoría</dt>
<dd>Se crean registros de auditoría sobre todos los intentos correctos o erróneos de autenticación por parte de los desarrolladores de apps. También se crean registros de auditoría sobre el acceso privilegiado a los sistemas Linux que alojan los contenedores donde se ejecutan las apps {{site.data.keyword.Bluemix_notm}}.</dd>

<dt>Protección de los datos</dt>
<dd> Todo el tráfico de {{site.data.keyword.Bluemix_notm}} pasa por IBM WebSphere® DataPower® SOA Appliances, que ofrece funciones de proxy inverso, terminación de SSL y equilibrio de cargas.
Se permiten los siguientes métodos HTTP:
 * DELETE
 * GET
 * HEAD
 * OPTIONS
 * POST
 * PUT
 * TRACE

La inactividad de HTTP supera el tiempo de espera transcurridos 2 minutos.

DataPower rellena las siguientes cabeceras:
<dl>
<dt>$wsis</dt>
<dd>Se establece en true si la conexión del lado del cliente es segura (HTTPS); de lo contrario, se establece en false.</dd>
<dt>$wssc</dt>
<dd>Se establece en uno de los siguientes esquemas de conexión de cliente: https, http, ws o wss.</dd>
<dt>$wssn</dt>
<dd>Se establece en el nombre de host que envía el cliente.</dd>
<dt>$wssp</dt>
<dd>Se establece en el puerto del servidor al que se conecta el cliente.</dd>
<dt>x-client-ip</dt>
<dd>Se establece en la dirección IP del cliente.</dd>
<dt>x-forwarded-proto</dt>
<dd>Se establece en uno de los siguientes esquemas de conexión de cliente: https, http, ws o wss.</dd>
</dl>
</dd>

<dt>Prácticas de desarrollo seguro</dt>
<dd> En {{site.data.keyword.Bluemix_notm}} Público y Dedicado, se realizan exploraciones periódicas de vulnerabilidad de seguridad en diversos componentes de {{site.data.keyword.Bluemix_notm}} mediante IBM Security AppScan® Dynamic Analyzer y ofertas de analizador estático. Se realizan pruebas de modelado de amenazas y penetración a fin de detectar y solucionar cualquier posible vulnerabilidad para todos los tipos de despliegues de {{site.data.keyword.Bluemix_notm}}. Además, los desarrolladores de apps pueden utilizar el servicio AppScan Dynamic Analyzer para proteger sus apps web desplegadas en {{site.data.keyword.Bluemix_notm}}.</dd>
</dl>

### Seguridad de la infraestructura

{{site.data.keyword.Bluemix_notm}} se basa en Cloud Foundry para ofrecer una base robusta en la que ejecutar sus apps. Dentro de la arquitectura, se ofrecen diversos componentes que proporcionan funciones de seguridad y aislamiento. Además se implementan procedimientos de gestión de cambios y de copia de seguridad y recuperación para garantizar la integridad y la disponibilidad.

<dl>
<dt>Segregación del entorno</dt>
<dd> En {{site.data.keyword.Bluemix_notm}} público, los entornos de desarrollo y de producción se han separado para mejorar la estabilidad y la seguridad de las apps.</dd>

<dt>Cortafuegos</dt>
<dd> Se han colocado cortafuegos para restringir el acceso a la red {{site.data.keyword.Bluemix_notm}}. En {{site.data.keyword.Bluemix_notm}}
local, el cortafuegos de su empresa segrega el resto de la red desde la instancia de {{site.data.keyword.Bluemix_notm}}.</dd>

<dt>Protección frente a intrusiones</dt>
<dd>{{site.data.keyword.Bluemix_notm}} público y dedicado permiten la protección frente a intrusiones con el fin de descubrir amenazas para que se puedan solucionar. En los cortafuegos se han activado políticas de protección frente a intrusiones.</dd>

<dt>Gestión segura de contenedores de apps</dt>
<dd>Cada app {{site.data.keyword.Bluemix_notm}} está aislada y se ejecuta en su propio contenedor, que tiene límites específicos de recursos de procesador, memoria y disco.</dd>

<dt>Refuerzo de la seguridad del sistema operativo</dt>
<dd>Los administradores de IBM realizan de forma regular operaciones de refuerzo del sistema operativo y de la red mediante herramientas como IBM punto final Manager.</dd>
</dl>

### Seguridad operativa

{{site.data.keyword.Bluemix_notm}} proporciona un sólido entorno de seguridad operativa con los controles siguientes.

<dl>
<dt>Exploración de vulnerabilidades</dt>
<dd>{{site.data.keyword.Bluemix_notm}} utiliza la herramienta de exploración de vulnerabilidades
Tenable Network Security,
Nessus, para detectar cualquier problema en la configuración de la red y del host a fin de solucionar posibles problemas.</dd>

<dt>Gestión de arreglos automáticos</dt>
<dd>Los administradores de {{site.data.keyword.Bluemix_notm}} garantizan que los sistemas operativos se aplican en frecuencias adecuadas. Los arreglos automáticos se activan mediante IBM Endpoint Manager.</dd>

<dt>Análisis y consolidación de registros de auditoría</dt>
<dd>{{site.data.keyword.Bluemix_notm}} utiliza las herramientas IBMSecurity QRadar® para consolidar los registros de Linux a fin de gestionar el acceso con privilegios en sistemas Linux. {{site.data.keyword.Bluemix_notm}} también utiliza la información de seguridad y gestión de sucesos (SIEM) de IBM QRadar para supervisar los intentos correctos y erróneos de inicio de sesión de los desarrolladores de apps.</dd>

<dt>Gestión de accesos de usuario</dt>
<dd>Dentro de {{site.data.keyword.Bluemix_notm}}, se siguen directrices de separación de responsabilidades para asignar a los usuarios privilegios de acceso granulares y para garantizar que los usuarios solo tienen el acceso que necesitan para realizar su trabajo según el principio de privilegio menor.

En un entorno {{site.data.keyword.Bluemix_notm}} dedicado y local, los administradores asignados pueden gestionar roles y permisos para el usuario de {{site.data.keyword.Bluemix_notm}} en su organización mediante la Consola de administración. Consulte [Gestión de {{site.data.keyword.Bluemix_notm}}](../admin/index.html#mng) para obtener más detalles.
</dd>
</dl>

### Seguridad física

{{site.data.keyword.Bluemix_notm}} público y dedicado se basa en la topología de red dentro de red de SoftLayer para la seguridad de la red física. Esta arquitectura de red dentro de red garantiza que sólo el personal autorizado pueda acceder a los sistemas. En {{site.data.keyword.Bluemix_notm}} local, usted es
el propietario de la seguridad física de la instancia local. El centro de datos está protegido detrás del cortafuegos de la compañía.

En la topología de red dentro de red de SoftLayer, la capa de red pública controla el tráfico público a los sitios web alojados o a los recursos en línea. La capa de red privada permite una verdadera gestión fuera de banda a través de un operador autónomo sobre SSL, PPTP o pasarelas IPSec VPN. La capa de red entre centros de datos proporciona conectividad segura y gratuita entre servidores distribuidos en distintas instalaciones de SoftLayer.

Cada centro de datos de SoftLayer está completamente protegido mediante controles que se ajustan, sin excepción, a los requisitos reconocidos por el sector y a los requisitos de SSAE 16. Para obtener más información, consulte la página de conformidad de seguridad de SoftLayer.

## Seguridad de los datos
{: #data-security}

Con {{site.data.keyword.Bluemix_notm}}, proteger sus datos frente a un acceso no autorizado constituye un esfuerzo conjunto entre {{site.data.keyword.Bluemix_notm}} y usted.

Los datos que asociados a una app en ejecución pueden estar en uno de estos tres estados: data-in-transit (datos en tránsito), data-at-rest (datos en reposo) y data-in-use (datos en uso).

<dl>
<dt>Data-in-transit</dt>
<dd>Datos que se están transfiriendo entre nodos de una red.</dd>

<dt>Data-at-rest</dt>
<dd>Datos que están almacenados.</dd>

<dt>Data-in-use</dt>
<dd>Datos que actualmente no están almacenados y sobre los que se está actuando en un punto final.</dd>
</dl>

Hay que tener en cuenta cada tipo de datos al planificar la seguridad de los datos.

La plataforma {{site.data.keyword.Bluemix_notm}} preserva los datos
data-in-transit protegiendo el acceso del usuario final a la app mediante SSL, a través de la red hasta que los datos alcanzan IBM
DataPower Gateway en el límite de la red interna de {{site.data.keyword.Bluemix_notm}}. IBM DataPower Gateway actúa como proxy inverso y ofrece terminación de SSL.

La seguridad de los datos de tipo data-in-use y data-at-rest es responsabilidad del usuario, que es quien desarrolla la app. Puede aprovechar los diversos servicios relacionados con datos disponibles en el Catálogo de {{site.data.keyword.Bluemix_notm}} para ayudarle con este tema.

## Seguridad de las apps de {{site.data.keyword.Bluemix_notm}}
{: #application-security}

Como desarrollador de apps, debe habilitar las configuraciones de seguridad, incluida la protección de los datos de la app, para las apps que se ejecutan en {{site.data.keyword.Bluemix_notm}}.

Puede utilizar las funciones de seguridad que proporcionan diversos servicios de {{site.data.keyword.Bluemix_notm}} para proteger las apps. Todos los servicios de {{site.data.keyword.Bluemix_notm}} que genera IBM siguen las recomendaciones de desarrollo de ingeniería segura de IBM.

**Nota:** Algunos de los servicios que se describen aquí puede que no se apliquen a las instancias dedicadas o locales de Bluemix.

### Servicio SSO

IBM Single Sign On for {{site.data.keyword.Bluemix_notm}} es un servicio de autenticación basado en política que ofrece capacidad de inicio de sesión única de fácil incorporación para
Node.js o Liberty para apps Java™. Para permitir que un desarrollador de apps pueda incluir la capacidad de inicio de sesión único en una app, el administrador crea instancias de servicio y añade orígenes de identidad.

El servicio Single Sign On da soporte a varios orígenes de identidad donde se almacenan las credenciales de los usuarios:

<dl>
<dt>SAML Enterprise</dt>
<dd>Un registro de usuario con intercambio de señales SAML que completa la autenticación.</dd>

<dt>Directorio de nube</dt>
<dd>Un registro de usuario que está alojado en IBM Cloud.</dd>

<dt>Orígenes de identidad social</dt>
<dd> Los registros de usuarios que mantienen Google, Facebook y LinkedIn.</dd>
</dl>

Para obtener más información, consulte [Guía de iniciación a Single Sign On](../services/SingleSignOn/index.html).

### AppScan Mobile Analyzer

Este servicio proporciona un análisis de seguridad para las apps móviles de Android. Para utilizar este servicio, debe cargar una app de Android compilada como un archivo APK. Una vez realizada la exploración del análisis de seguridad, puede descargar un informe.

Para obtener más información, consulte [Guía de iniciación a AppScan Mobile Analyzer](../services/AppScanMobileAnalyzer/index.html).

### AppScan Dynamic Analyzer

Este servicio proporciona un análisis de seguridad de apps web con una herramienta de análisis dinámico. La herramienta funciona sobre la app web desplegada, no sobre el código fuente de la app, y puede explorar cualquier app web de {{site.data.keyword.Bluemix_notm}} independientemente de su lenguaje o tecnología. Sólo puede explorar las apps de las organizaciones a las que pertenece. Para crear una exploración, debe configurar el URL de la app web y las credenciales de inicio de sesión, si existen. Una vez realizada la exploración, puede descargar un informe.

Para obtener más información, consulte [Guía de iniciación a AppScan Dynamic Analyzer](../services/AppScanDynamicAnalyzer/index.html).

### Mobile Analyzer for iOS (Beta)

El servicio Mobile Analyzer for iOS ofrece el análisis de seguridad dinámico AppScan para apps móviles
iOS. Le ayuda a identificar problemas de seguridad en las apps para móvil iOS.

Para obtener más información, consulte [Guía de iniciación a Mobile Analyzer for iOS](../services/AppScanIOS/index.html).

### Static Analyzer (Beta)

El servicio Static Analyzer habilita las pruebas de seguridad estática de apps en la nube. Le ayuda a encontrar vulnerabilidades del código fuente
en las primeras fases del ciclo de vida del desarrollo de software, para que se puedan arreglar antes del despliegue.

Static Analyzer le permite explorar contenido Java y Java web mediante una interfaz de línea de mandatos (CLI) en el disco local. Además, puede ejecutar un pequeño programa de instalación que añade plug-ins del analizador a Eclipse o Maven. Puede utilizar el programa de utilidad cliente para explorar y recopilar información acerca de los archivos en un archivo que luego puede enviar a la nube para explorar resultados.

Para obtener más información, consulte [Guía de iniciación a IBM Static Analyzer for Bluemix](../services/StaticAnalyzer/index.html).

### Plug-in IBM UrbanCode para la prueba de seguridad de apps

El plug-in IBM Application Security Testing for {{site.data.keyword.Bluemix_notm}} le permite ejecutar exploraciones de seguridad en la web o en las apps Android alojadas en {{site.data.keyword.Bluemix_notm}}. Este plug-in ha sido desarrollado y recibe soporte de IBM UrbanCode™ Deploy Community en la plataforma IBM Bluemix DevOps Services.

Para obtener más información, vaya a [IBM Application Security Testing for Bluemix](https://developer.ibm.com/urbancode/plugindoc/ibmucd/ibm-application-security-testing-bluemix/1-0/){: new_window}.

### SQL Database

El servicio SQL Database incorpora a la app una base de datos relacional con todas sus funciones. Este servicio utiliza IBM Directory Server LDAP para la autenticación e IBM InfoSphere® Guardium® Data Activity Monitor para proteger la base de datos a la que acceden las apps. La conexión entre
las apps y la base de datos está protegida mediante el certificado SSL
firmado por DigiCert.

En determinados planes con este servicio, puede utilizar la consola de SQL Database en {{site.data.keyword.Bluemix_notm}} para obtener informes que contienen la siguiente información:

 * Datos sensible que puedan encontrarse en la base de datos a la que acceden
las apps.
 * Los usuarios de las apps que han accedido a la base de datos en un período especificado.
 * Los usuarios de las apps que acceden a los datos sensibles de la base de datos.

Para enmascarar los datos mediante SQL, las apps pueden llamar a las funciones de enmascaramiento definidas por el usuario (UDF) que se despliegan junto con la base de datos. Por ejemplo, puede enmascarar los datos que desee utilizar en otro lugar para efectuar pruebas. Las UDF implementan los algoritmos de enmascaramiento de datos de IBM Infosphere Optim™.

El plan premium de este servicio también incluye cifrado de datos. Para obtener más información sobre este servicio, consulte [Guía de iniciación a SQL Database](../services/SQLDB/index.html).

### dashDB

El servicio de dashDB utiliza un servidor LDAP incorporado para la autenticación de usuario. La conexión entre
las apps y la base de datos está protegida mediante certificados SSL. Este servicio utiliza la capacidad de cifrado nativo de DB2® para cifrar de forma automática la base de datos desplegada y las copias de seguridad de la base de datos. La rotación de claves maestras se ejecuta automáticamente cada 90 días.

Para obtener más información, consulte [Guía de iniciación a dashDB](../services/dashDB/index.html).

### Cloud Integration

El servicio Cloud Integration le permite integrar datos de la nube y locales. Puede añadir un servicio para que interactúe con las bases de datos de fondo, como por ejemplo DB2, Oracle y SAP. A continuación, puede mover datos o crear API REST para que las apps de {{site.data.keyword.Bluemix_notm}} accedan a ellos y los utilicen. El servicio permite establecer una comunicación segura con conectores seguros locales y deja al descubierto sistemas de fondo de registro como API REST para que los puedan utilizar las apps.

Para obtener más información, consulte [Guía de iniciación a Cloud Integration](../services/CloudIntegration/index.html).

### Secure Gateway

El servicio Secure Gateway le permite conectar de forma segura apps {{site.data.keyword.Bluemix_notm}} con ubicaciones remotas, tanto locales como en la nube. Proporciona conectividad segura y establece un túnel entre la organización {{site.data.keyword.Bluemix_notm}} y la ubicación remota a la que desea conectarse. Puede configurar y crear una pasarela segura mediante la interfaz de usuario de {{site.data.keyword.Bluemix_notm}} o un paquete de API.

Para obtener más información, consulte [Guía de iniciación a Secure Gateway](../services/SecureGateway/index.html).

### Información sobre seguridad y gestión de sucesos

Puede utilizar las herramientas de información de seguridad y gestión de sucesos (SIEM) para analizar las alertas de seguridad en los registros de app. Una de ellas es IBM Security QRadar&reg; SIEM, que proporciona inteligencia de seguridad en entornos de nube. Para obtener información, consulte [IBM QRadar Security Intelligence Platform](http://www-01.ibm.com/support/knowledgecenter/SS42VS/welcome?lang=en){: new_window}.

## Despliegue de la seguridad de {{site.data.keyword.Bluemix_notm}}
{: #security-deployment}

La arquitectura de despliegue de seguridad de {{site.data.keyword.Bluemix_notm}} incluye distintos flujos de información para los usuarios y desarrolladores de apps para garantizar un acceso seguro.

![Arquitectura de despliegue de seguridad de Bluemix](images/sec_deployment.svg)

*Figura 3. Arquitectura de despliegue de seguridad de Bluemix*

Para los usuarios de la app de {{site.data.keyword.Bluemix_notm}} **, el **flujo de usuario de la app** es el siguiente:
 1. A través de un cortafuegos, con prevención de intrusiones y seguridad de la red.
 2. A través de IBM DataPower Gateway, con proxy inverso y proxy de terminación de SSL.
 3. A través del direccionador de la red.
 4. Alcanza el tiempo de ejecución de la app en el agente de ejecución de droplet (DEA).

El *desarrollador de* {{site.data.keyword.Bluemix_notm}} sigue dos flujos principales, para inicio de sesión y para desarrollo y despliegue.
 * El **flujo del desarrollador para inicio de sesión** incluye lo siguiente:
    * Para los desarrolladores que han iniciado una sesión en {{site.data.keyword.Bluemix_notm}} público, el flujo es el siguiente:
      1. A través del servicio IBM Single Sign On.
      2. A través de la identidad web de IBM.
    * Para los desarrolladores que han iniciado una sesión en {{site.data.keyword.Bluemix_notm}} dedicado o local, el flujo se realiza a través de LDAP de empresa.
 * El **flujo de desarrollo y despliegue** es el siguiente:
    1. A través de un cortafuegos, con prevención de intrusiones y seguridad de la red. Esto se aplica únicamente a {{site.data.keyword.Bluemix_notm}} dedicado.
    2. A través de IBM DataPower Gateway, con proxy inverso y proxy de terminación de SSL.
    3. A través del direccionador de la red.
    4. A través de autorización mediante el controlador de nube de Cloud Foundry, para garantizar el acceso solo a las apps e instancias de servicio que ha creado el desarrollador.
  
Para los administradores de {{site.data.keyword.Bluemix_notm}} dedicado y {{site.data.keyword.Bluemix_notm}} local**, el **flujo del administrador** es el siguiente:
 1. A través de un cortafuegos, con prevención de intrusiones y seguridad de la red.
 2. A través de IBM DataPower Gateway, con proxy inverso y proxy de terminación de SSL.
 3. A través del direccionador de la red.
 4. Va a la página Administración de la interfaz de usuario de {{site.data.keyword.Bluemix_notm}}.

Además de los usuarios suscritos a estos métodos, un equipo de operaciones de seguridad de IBM autorizado realiza diversas tareas de seguridad operativa, como las siguientes:
 * Exploraciones de vulnerabilidad. En {{site.data.keyword.Bluemix_notm}} local, usted es el propietario de la seguridad física y de las exploraciones que se realicen en el cortafuegos.
 * Gestión de accesos de usuario.
 * Refuerzo del sistema operativo mediante la app periódica de arreglos con IBM Endpoint Manager.
 * Gestión de riesgos con protección frente a intrusiones.
 * Supervisión de la seguridad con QRadar.
 * Informes de seguridad disponibles mediante la Consola de administración.

## Informes de seguridad
{: #reports}

Con {{site.data.keyword.Bluemix_notm}} local y {{site.data.keyword.Bluemix_notm}} dedicado, {{site.data.keyword.Bluemix_notm}} genera distintos informes de seguridad y registros que puede ver en la página Administración. Para obtener instrucciones para ver y utilizar los informes, consulte [Visualización de informes](../admin/index.html#oc_report).

La tabla siguiente muestra la lista de los informes de seguridad generados para {{site.data.keyword.Bluemix_notm}} local y {{site.data.keyword.Bluemix_notm}} dedicado. 

| **Categoría** | **Informe** | **Descripción** |      
|-----------------|-------------------|---------------------|
| Cortafuegos | Inicios de sesión de cortafuegos | Sucesos relacionados con el inicio de sesión del administrador en los dispositivos de cortafuegos Vyatta. |
| Cortafuegos | Denegaciones de cortafuegos | Sucesos generados por los dispositivos cortafuegos Vyatta cuando se deniega una solicitud de acceso acuerdo con las reglas vigentes del cortafuegos. |
| Sucesos de inicio de sesión del administrador de {{site.data.keyword.Bluemix_notm}} | Inicio de sesión de los administradores de {{site.data.keyword.Bluemix_notm}} | Sucesos generados por el sistema operativo cuando un administrador inicia una sesión SSH en cada sistema {{site.data.keyword.Bluemix_notm}}. |
| Sucesos de inicio de sesión de desarrollador de apps de {{site.data.keyword.Bluemix_notm}} | Inicio de sesión de desarrolladores de apps de {{site.data.keyword.Bluemix_notm}} | Sucesos generados por el componente de inicio de sesión de la plataforma {{site.data.keyword.Bluemix_notm}} cuando un usuario de la plataforma {{site.data.keyword.Bluemix_notm}} inicia sesión mediante la línea de mandatos, las API REST o la interfaz de usuario de {{site.data.keyword.Bluemix_notm}}. |
| Sucesos administrativos del administrador de {{site.data.keyword.Bluemix_notm}} | Sucesos administrativos del sistema operativo de los administradores de {{site.data.keyword.Bluemix_notm}} | Sucesos generados por el sistema operativo cuando un administrador realiza una acción durante una sesión de trabajo actual. |
| Sucesos administrativos de desarrollador de apps de {{site.data.keyword.Bluemix_notm}} | Sucesos administrativos de {{site.data.keyword.Bluemix_notm}} (Cloud Foundry) | Sucesos relacionados con operaciones realizadas por el usuario de la plataforma {{site.data.keyword.Bluemix_notm}} utilizando la línea de mandatos, las API REST o la interfaz de usuario de {{site.data.keyword.Bluemix_notm}}. |
| Sucesos administrativos de la base de datos del administrador de {{site.data.keyword.Bluemix_notm}} | Sucesos administrativos de la base de datos | Sucesos relacionados con las operaciones realizadas por un administrador de bases de datos en las bases de datos internas de {{site.data.keyword.Bluemix_notm}}. |
| Sucesos de administración | Sucesos de gestión de usuarios | Sucesos relacionados con acciones de gestión de usuarios realizadas en la página Administración. |
| Sucesos de administración | Catálogo | Sucesos relacionados con cambios en el catálogo de servicios. |
| Sucesos de administración | Sucesos de gestión de informes de seguridad | Sucesos relacionados con acciones de gestión de informes de seguridad realizadas en la página Administración. |
| Revisiones de acceso | Informe de revisiones de acceso | Revisiones para accesos privilegiados. |
| Gestión de cambios | Gestión de cambios de software | Actividad de gestión de cambios. |
| Gestión de claves | Gestión de certificados SSL personalizados | Certificados SSL personalizados cargados y almacenados. |
| Cifrado | Cifrado data-in-transit (datos en tránsito) | Cifrado data-in-transit (datos en tránsito) configurado. |
| Antivirus | Informe de exploración de antivirus | Software antivirus vigente. |
| Gestión de arreglos de software | Informe de app de parches | Arreglos de software aplicados. |
| Gestión de incidentes de seguridad | Informe de solución de incidentes de seguridad | Pruebas de incidentes de seguridad para la gestión de incidentes de seguridad. |

*Tabla 1. Lista de informes de seguridad de {{site.data.keyword.Bluemix_notm}} local y {{site.data.keyword.Bluemix_notm}} dedicado*

# rellinks
## general 
* [Conformidad de seguridad de SoftLayer](http://www.softlayer.com/security)
* [Guía de iniciación a Single Sign On](../services/SingleSignOn/index.html)
