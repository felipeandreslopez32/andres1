DNIntegra - Recuperación de Contraseña
 Descripción
Este proyecto corresponde a la implementación del módulo de recuperación de contraseña en la aplicación DNIntegra, desarrollada en ASP.NET Web API 4.5 con base de datos en SQL Server.
La solución permite a los usuarios restablecer su contraseña de forma segura mediante el envío de un enlace con token único a su correo electrónico.

Objetivo
Implementar un mecanismo seguro que permita a los usuarios recuperar el acceso a la plataforma mediante:
•	Validación de identidad a través del correo electrónico
•	Generación de un token único de recuperación
•	Restablecimiento de contraseña bajo políticas de seguridad

Alcance
La implementación incluye:
•	Modificaciones en la interfaz de usuario (Frontend)
•	Desarrollo de endpoints en el backend
•	Configuración de envío de correos (SMTP)
•	Implementación de validaciones de seguridad
•	Gestión de tokens de recuperación


Funcionalidades
•	Botón de “Restablecer contraseña” 
•	Formulario para validación de correo
•	Envío de correo con token seguro
•	Formulario para actualización de contraseña
•	Validación avanzada de contraseñas
•	Tokens con expiración (20 minutos)
•	Limpieza de sesión al hacer logout

Tecnologías utilizadas
•	ASP.NET Web API 4.5
•	AngularJS
•	SQL Server
•	SMTP (Office 365)

 Flujo de recuperación de contraseña
1.	El usuario hace clic en “Restablecer contraseña”
2.	Ingresa su correo electrónico
3.	El sistema valida el correo
4.	Se envía un email con un enlace seguro
5.	El usuario accede al enlace (con token)
6.	Ingresa una nueva contraseña
7.	El sistema valida y actualiza la contraseña

 Frontend
 Botón de recuperación
Ubicación:
DNIntegra.Logistica/views/pages/signin.html
Función:
•	Redirige a la vista de recuperación de contraseña

 Formulario de recuperación
Ubicación:
views/pages/recuperacion.html
Funcionalidad:
•	Captura el correo del usuario
•	Valida formato
•	Envía solicitud al backend

 Formulario de actualización
Ubicación:
views/pages/actualizarContrasena.html
Validaciones:
•	Contraseña mínima de 8 caracteres
•	Mayúscula, minúscula, número y carácter especial
•	Confirmación de contraseña

 Backend
 Endpoint: Recuperar contraseña
POST /api/accounts/recuperar
Funcionalidad:
•	Valida el correo
•	Genera token
•	Envía email con enlace de recuperación
Respuesta:
•	Token generado
•	URL de recuperación

 Endpoint: Reset password
POST /api/accounts/reset-password
Funcionalidad:
•	Valida token y usuario
•	Valida nueva contraseña
•	Actualiza contraseña en base de datos

 Seguridad
•	Token de un solo uso
•	Expiración de token: 20 minutos
•	Validación de caracteres no permitidos
•	Actualización de SecurityStamp en errores
•	Uso de TLS 1.2
•	Validación personalizada de contraseñas

 Configuración
 SMTP (Web.config)
Se configuró envío de correos mediante:
•	Host: smtp.office365.com
•	Puerto: 587
•	SSL habilitado

 Validaciones de contraseña
El sistema incluye un validador personalizado que exige:
•	Longitud mínima: 8 caracteres
•	Longitud máxima: 16 caracteres
•	Al menos:
o	1 mayúscula
o	1 minúscula
o	1 número
o	1 carácter especial
•	No permite:
o	Caracteres especiales restringidos (&, <, >, etc.)
o	Secuencias numéricas (123, 456)
o	Secuencias alfabéticas (abc, def)

 Manejo de sesión
Al cerrar sesión:
•	Se limpian:
•	localStorage
•	sessionStorage
•	Se elimina el token de autorización
•	Se recarga completamente la aplicación

 Estructura relevante
DNIntegra.API/
Controllers/
AccountsController.cs
Services/
EmailService.cs
Infraestructure/
ApplicationUserManager.cs

DNIntegra.Logistica/
 views/pages/
scripts/auth/
scripts/

 Autor
Felipe Andrés Lopez Rubio

 Notas adicionales
•	El sistema depende de la correcta configuración del SMTP
•	Los tokens son sensibles al tiempo de expiración
Conclusión
La implementación del módulo de recuperación de contraseña fortalece la seguridad y usabilidad de la aplicación DNIntegra, alineándose con buenas prácticas en gestión de accesos y protección de la información.
