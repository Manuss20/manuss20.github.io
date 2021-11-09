+++
author = "Manuel Sanchez"
title = "Azure AD Managed Identity"
date = "2021-11-09"
description="Hoy me gustaría hablaros un poco sobre Azure Active Directory (Azure AD) y explicaros algunos conceptos como gestionar las famosas Managed Identity, desde un perspectiva general de su uso."
tags = [
    "Azure", "AD", "Active Directory", "Managed Identity", "Identity", "Users", "Groups", "Privileges", "Automation", "Cloud"
]
categories = [
    "Azure", "AD", "Active Directory", "Managed Identity", "Identity", "Users", "Groups", "Privileges", "Automation", "Cloud"
]
images  = ["img/posts/Azure-ARM.jpg"]
+++

Hoy me gustaría hablaros un poco sobre Azure Active Directory (Azure AD) y explicaros algunos conceptos como gestionar las famosas Managed Identity, desde un perspectiva general de su uso.

##¿Qué es Azure Active Directory?
Azure Active Directory (también conocido como Azure AD) es un servicio multi-inquilino completamente administrado de Microsoft que ofrece capacidades de identidad y acceso para aplicaciones que se ejecutan en Microsoft Azure y para aplicaciones que se ejecutan en un entorno local. Esto hace que a menudo pueda ser confundido con Active Directory para Windows Server, en realidad esto va mucho más allá de lo que ya estamos familiarizados en entornos Windows. Para resumirlo, no, Azure AD no es Active Directory ejecutándose en máquinas virtuales de Azure.

Además con Azure AD podemos lograr cosas como el inicio de sesión único (SSO) o multifactor, acceso a aplicaciones aplicaciones, consultar los permisos e información de usuarios y grupos, e incluso escribir cambios en el directorio y la mejor parte es que puede integrar Azure AD con Windows Server AD.

Azure AD es un lugar donde se crearán los usuarios y los perfiles. Por lo tanto, los usuarios o empleados de una organización iniciarán sesión con su nombre de usuario y contraseña. Y, por supuesto, a veces puede requerir autenticación multifactor. Y luego, basándonos en esa identidad, proporcionamos acceso a las aplicaciones.

##Autenticación frente a autorización
Antes de continuar, primero me gustaría poder discernir entre dos conceptos que tienden a confundirse; la diferencia entre la autenticación y autorización. Puede que ya lo sepas. Pero de todos modos lo explicaré rápidamente.

El proceso de identificar a alguien a sí mismo se llama autenticación. Es como si vamos por la calle y nos piden que nos identifiquemos - ¡Alto, Policía!, lo que seguramente haremos es mostrar nuestro DNI, Pasaporte o licencia de conducir. Fácil ¿verdad?

Entonces, ¿qué es la autorización?

Si tomamos el ejemplo anterior. Ya hemos demostrado nuestra identidad; la siguiente pregunta inmediata es ¿qué puedo hacer o qué no puedo hacer con esa identidad en una organización o sistema en particular? ¿Estoy en el lugar correcto o me he colado?

Disponer de la autorización oportuna nos permite llegar todo lo lejos que nos permita la autoridad que otorga ese derecho. Siguiendo con nuestro ejemplo, en un concierto, ¿tenemos una entrada que nos permite acceder al recinto o disponemos de un pase VIP que nos da acceso al backstage?

En el contexto de Azure, Autorización es poder responder a la pregunta ¿Cuáles son los diferentes servicios a los que puedo acceder y a los que no tengo acceso?

##Autenticación multifactor
Ahora hablemos un poco de la autenticación multifactor. Estoy seguro que es un término familiar que ya lo has oído antes. Cuando iniciamos sesión en un sitio web en particular, proporcionamos nuestro nombre de usuario y contraseña. Imagina que por alguna razón nuestra contraseña se filtra. Entonces alguien sin acceso autorizado y que tenga nuestra contraseña puede acceder a los datos y servicios que contiene.

Entonces, ¿cómo podemos mitigar este problema? Ahí es cuando necesitamos la autenticación multifactor (MFA). Además del nombre de usuario y la contraseña, también se debe proporcionar la identidad en forma de probablemente una OTP que obtenemos en nuestro teléfono móvil o mediante una llamada telefónica o usando una aplicación móvil instalada en donde confirmamos que somos nosotros los que estamos haciendo inicio de sesión.

La autenticación multifactor funciona al requerir dos o más de los siguientes métodos de autenticación:

- Algo que sepas, normalmente una contraseña.

- Algo que tenga, como un dispositivo confiable que no se pueda duplicar fácilmente. (Por ejemplo: teléfono o llave de hardware)

- Algo que eres: datos biométricos como una huella dactilar o un escaneo facial.

##¿Qué es una identidad administrada?
Las identidades administradas proporcionan una identidad para que las aplicaciones la usen cuando se conectan a recursos que admiten la autenticación de Azure Active Directory (Azure AD). Fundamentalmente, la gestión de credenciales es manejada por la identidad administrada (de ahí la palabra), y no por la aplicación o el desarrollador.

Dicho de otro modo, la aplicación usa la identidad administrada para obtener un token de Azure AD. Este token se puede usar para acceder a otros recursos de Azure, comúnmente Azure Key Vault o Azure Storage.

Inicio de sesión único (SSO)

La misma identidad se puede utilizar en varias aplicaciones. Y esa función se denomina inicio de sesión único. Inicia sesión una vez, y con ese inicio de sesión en particular, intenta acceder a todos los recursos.

Gestión de aplicaciones

Como mencioné antes, cuando creamos y configuramos múltiples aplicaciones para Azure AD. Estas aplicaciones solo pueden ser utilizadas por usuarios dentro de nuestra organización o, en ciertos casos, por algunos usuarios  invitados pertenecientes a otra organización. Por lo tanto, podemos invitar a usuarios de otra organización. Eso significa que hay un inquilino AD más donde existe la identidad del usuario. Pero en nuestro AD, va a existir como invitado.

Una vez que el usuario invitado se agrega a nuestro Directorio Activo, junto con nuestros otros usuarios, a este usuario en particular también se le pueden otorgar permisos como cualquier otro usuario dentro de la misma organización.

Gestión de dispositivos

Ya por último, podemos proporcionar administración de dispositivos mediante Azure AD uniendo nuestros dispositivos móviles u ordenadores portátiles al inquilino de Azure. A través del inquilino, podemos controlar el dispositivo. Un ejemplo práctico es cuando pierdes tu dispositivo y luego puedes bloquear tu cuenta o más concretamente el acceso mediante ese dispositivo. Por lo tanto, en el dispositivo, nadie más puede iniciar sesión y robar tus datos.

##Agregando usuarios a Azure AD
Tras las explicaciones previas, ahora vamos a agregar nuestro primer usuario. Para ello debemos seguir los siguientes pasos:

Inicia sesión en Azure Portal como administrador de usuarios para tu organización.

En la barra superior, busca y selecciona Azure Active Directory.

Selecciona Usuarios y, a continuación, selecciona Nuevo usuario.

En la página Usuario puedes definir la información relativa para este usuario:

- Nombre. Nombre y apellidos del nuevo usuario. Por ejemplo, Mary Poppins.
- Nombre de usuario. Nombre de usuario del nuevo usuario. Por ejemplo, mary@contoso.com.
En la parte del dominio del nombre de usuario debemos usar el nombre de dominio predeterminado inicial, <yourdomainname>.onmicrosoft.com o un nombre de dominio personalizado, como de contoso.com.

- Grupos. Podemos agregar el usuario a uno o varios de los grupos existentes.
- Rol del directorio. Aquí podemos definir alguno de los permisos administrativos de Azure AD para el usuario
- Información del trabajo. Podemos agregar más información sobre el usuario aquí o hacerlo más adelante.
- Copia la contraseña generada automáticamente proporcionada en el cuadro de texto Contraseña. Esta será la contraseña que debemos proporcionar al usuario para iniciar sesión por primera vez.

Selecciona Crear. El usuario queda así definido y se agrega a la organización de Azure AD.

También podemos invitar a un usuario invitado nuevo a colaborar con nuestra organización si selecciona Invitar usuario en la página Nuevo usuario. El usuario recibirá una invitación por correo electrónico que debe aceptar para empezar a colaborar.

##Asignación de roles
Lo comentaba antes pero quizá es mejor dedicarle unas líneas adicionales. En Azure es posible administrar usuarios asignándoles alguno de los diferentes roles disponibles. En Azure Active Directory (Azure AD), por ejemplo, si uno de los usuarios necesita permiso para administrar recursos de Azure AD, debemos asignarlo a un rol que proporcione los permisos que necesita.

Esta asignación de roles se realiza desde la página Roles siguiendo unos sencillos pasos:

- Accedemos con nuestro usuario de administrador global a Azure Portal.
- En la barra superior busca y selecciona Azure Active Directory.
- Selecciona Usuarios.
- Ahora seleccionamos el usuario que obtiene la asignación de roles. Por ejemplo, Alain Charon.
- En la página Alain Charon - Perfil, selecciona Roles asignados.
- Y aquí podemos ver los roles que están asignados para este usuario. Si queremos darle roles de administrador de aplicaciones, por ejemplo, debemos seleccionar este rol y pulsamos en añadir (Add).

##Creación masiva de usuarios en Azure Active Directory
En este punto seguro que adivino si piensas que todo esto es muy bonito pero es un lento, lento, lento proceso que no puedes asumir si tenemos que ir usuario a usuario. Y tienes toda la razón.

Azure Active Directory (Azure AD) admite operaciones de creación y eliminación de usuarios en lotes y la descarga de listas de usuarios. Solo necesitamos rellenar una plantilla .CSV que se puede descargar en el portal de Azure AD.

##Grupos de usuarios
Un grupo Azure AD permite organizar a los usuarios, facilitando la gestión de los permisos. Los grupos permiten al propietario del recurso (o al propietario de Azure AD-Directory) asignar un conjunto de permisos de acceso a todos los miembros del grupo.

Los grupos permiten definir una política y luego añadir y eliminar usuarios específicos. De este modo, se puede conceder o denegar el acceso con un esfuerzo mínimo.

Aún mejor, Azure AD ofrece la posibilidad de definir la afiliación en función de reglas, como el departamento en el que trabaja un usuario o el cargo que ocupa.

En Azure AD podemos definir dos tipos diferentes de grupos:

- Grupos de seguridad. Son los grupos de seguridad más comunes y se utilizan para gestionar el acceso de los miembros y de los ordenadores a los recursos compartidos por un grupo de usuarios. Por ejemplo, puede crear un grupo de seguridad para una política de seguridad específica. De esta manera, puede dar un conjunto de permisos a todos los miembros a la vez en lugar de añadir permisos individualmente para cada miembro. Esta opción requiere un administrador de Azure AD.
- Grupos de Microsoft 365. Estos grupos ofrecen oportunidades de colaboración al dar a los miembros acceso a una bandeja de entrada, un calendario y archivos compartidos, SharePoint y más. Esta opción también le permite dar acceso al grupo a personas ajenas a su organización. Esta opción está disponible tanto para los usuarios como para los administradores.

##Grupos dinámico en Azure AD
En Azure Active Directory (Azure AD), también podemos usar reglas para determinar la pertenencia a grupos según las propiedades de usuario o dispositivo. La pertenencia dinámica es compatible con grupos de seguridad o grupos de Microsoft 365. Cuando se aplica una regla de pertenencia a grupos, se evalúan los atributos de usuario y dispositivo para ver si coinciden con la regla de pertenencia. Cuando cambian los atributos de un usuario o dispositivo, se procesan todos los cambios de pertenencia de las reglas de grupo dinámico de la organización.

##Control de acceso basado en rol de Azure (RBAC)
En términos de computación en la nube, el control de acceso juega un papel vital para administrar los permisos de manera efectiva. Azure RBAC es un sistema de autorización basado en Azure Resource Manager que proporciona administración de acceso específico a los recursos de Azure. La administración de acceso de los recursos en la nube es una función importantísima para cualquier organización. Azure RBAC ayuda a administrar quién tiene acceso a los recursos de Azure, qué pueden hacer con esos recursos y a qué áreas puede acceder.

##Algunos escenarios para Azure Access Control (Azure RBAC)
- Otorgar acceso a diferentes recursos de Azure con uno o varios roles. Ejemplo: permitir que un usuario administre la aplicación de Azure y el servicio SQL de Azure. Podemos dar Contributor, Reader, owner, Manage role, Monitor reader/contributor, website contributor etc.
- Del mismo modo, otorgar acceso a nivel de suscripción. Ejemplo: permitir que un usuario cree solo una máquina virtual en una suscripción específica. O permita que el usuario cree el servicio de aplicaciones de Azure, así como servicios lógicos (múltiples) con rol de contribución, lectura o propietario.
- Dar diferentes accesos a diferentes ámbitos como grupo de administración, suscripciones, grupo de recursos o recursos.
- Otorgar acceso a una aplicación para acceder a los recursos también.
- Podemos hacer de muchas a muchas relaciones entre roles, ámbitos y usuarios o grupo (principal de seguridad).

Hay tres componentes principales que se deben comprender para el control de acceso basado en roles de Azure: entidad de seguridad (quién), rol (qué) y alcance (dónde).

El director de seguridad básicamente representa quién obtendrá el acceso, como usuarios, grupo, director de servicio e identidad administrada. (Quien es)

Ámbito es el conjunto de recursos al que se aplica el acceso. Cuando se asigna un rol, es posible limitar aún más las acciones permitidas si se define un ámbito. Esto resulta útil si desea convertir a alguien en Colaborador del sitio web, pero solo para un grupo de recursos.

En Azure, puede especificar un ámbito en cuatro niveles: grupo de administración, suscripción, grupo de recursos o recurso. Los ámbitos se estructuran en una relación de elementos primarios y secundarios. Puede asignar roles en cualquiera de estos niveles de ámbito.

Diagrama que muestra los niveles de ámbito de una asignación de roles.

Las relaciones entre el principio de seguridad, la definición de rol y el alcance son una especie de muchos a muchos.

Podemos asignar roles a un usuario o grupo en un cierto alcance para el control de acceso y nuevamente podemos revocarlos eliminando una asignación de roles.
Podemos asignar el mismo rol a múltiples usuarios, grupos o identidad administrada en recursos iguales o diferentes (alcance).
Podemos asignar roles utilizando Azure Portal, Azure SDK, Azure CLI, Azure PowerShell o API REST.
La forma más fácil de manejar el control de acceso basado en roles es mediante el Portal de Azure.

Encontraremos una pestaña común en todos los recursos de Azure que es Control de acceso (IAM) como se muestra, y a partir de aquí podemos realizar nuestra asignación a medida.