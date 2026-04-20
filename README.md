# DNIntegra – Recuperación de Contraseña

## 📄 Descripción
Este proyecto corresponde a la implementación del módulo de **recuperación de contraseña** en la aplicación **DNIntegra**, desarrollada en **ASP.NET Web API 4.5** con base de datos **SQL Server**.

La solución permite a los usuarios restablecer su contraseña de forma segura mediante el envío de un **enlace con token único** a su correo electrónico.

---

## 🎯 Objetivo
Implementar un mecanismo seguro que permita a los usuarios recuperar el acceso a la plataforma mediante:

- Validación de identidad a través del correo electrónico  
- Generación de un token único de recuperación  
- Restablecimiento de contraseña bajo políticas de seguridad  

---

## 📦 Alcance
La implementación incluye:

- Modificaciones en la interfaz de usuario (Frontend)
- Desarrollo de endpoints en el backend
- Configuración de envío de correos (SMTP)
- Implementación de validaciones de seguridad
- Gestión de tokens de recuperación

---

## ⚙️ Funcionalidades
- Botón de **“Restablecer contraseña”**
- Formulario para validación de correo
- Envío de correo con token seguro
- Formulario para actualización de contraseña
- Validación avanzada de contraseñas
- Tokens con expiración (20 minutos)
- Limpieza de sesión al hacer logout

---

## 🛠️ Tecnologías utilizadas
- ASP.NET Web API 4.5
- AngularJS
- SQL Server
- SMTP (Office 365)

---

## 🔄 Flujo de recuperación de contraseña
1. El usuario hace clic en **“Restablecer contraseña”**
2. Ingresa su correo electrónico
3. El sistema valida el correo
4. Se envía un email con un enlace seguro
5. El usuario accede al enlace (con token)
6. Ingresa una nueva contraseña
7. El sistema valida y actualiza la contraseña

---

## 🎨 Frontend

### Botón de recuperación
**Ubicación:**  
`DNIntegra.Logistica/views/pages/signin.html`

**Función:**
- Redirige a la vista de recuperación de contraseña

---

### Formulario de recuperación
**Ubicación:**  
`views/pages/recuperacion.html`

**Funcionalidad:**
- Captura el correo del usuario
- Valida el formato del correo
- Envía la solicitud al backend

---

### Formulario de actualización de contraseña
**Ubicación:**  
`views/pages/actualizarContrasena.html`

**Validaciones:**
- Contraseña mínima de 8 caracteres
- Uso de mayúscula, minúscula, número y carácter especial
- Confirmación de contraseña

---

## 🔙 Backend

### Endpoint: Recuperar contraseña
```http
POST /api/accounts/recuperar
