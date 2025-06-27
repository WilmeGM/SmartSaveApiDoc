# 📘 Endpoint de Register — SmartSave API

**Método:** `POST`  
**Content-Type**: `application/json`  
**Ruta:** `/api/auth/register`  
**Descripción:** Permite registrar un nuevo usuario en el sistema. Valida que todos los campos estén completos, que el correo electrónico tenga un formato válido, que la contraseña sea segura y que no exista otro usuario con el mismo correo. Si todo es correcto, guarda el usuario en la base de datos.

---

## 📥 Cuerpo de la solicitud

```json
{
  "firstName": "string (obligatorio)",
  "lastName": "string (obligatorio)",
  "email": "string (obligatorio, formato válido)",
  "password": "string (obligatorio, segura)",
  "confirmPassword": "string (obligatorio, igual a password)"
}
```

### 📄 Ejemplo

```json
{
  "firstName": "Wilme",
  "lastName": "GM",
  "email": "admin@email.com",
  "password": "StrongPass123",
  "confirmPassword": "StrongPass123"
}
```

---

## 📤 Respuestas posibles

### ✅ 200 OK  
El usuario se registró correctamente.  
*No retorna contenido.*

---

### ❌ 400 Bad Request — Errores de validación

#### Campos vacíos

```json
{
  "status": 400,
  "message": "Every field is required"
}
```

#### Correo inválido

```json
{
  "status": 400,
  "message": "Enter a valid email."
}
```

#### Contraseña débil

```json
{
  "status": 400,
  "message": "Password must be at least 8 characters and contain uppercase, lowercase and number."
}
```

#### Contraseñas distintas

```json
{
  "status": 400,
  "message": "Passwords must be the same."
}
```

#### Correo ya registrado

```json
{
  "status": 400,
  "message": "That email is already taken."
}
```

---

### ❌ 500 Internal Server Error — Error inesperado del servidor

```json
{
  "status": 500,
  "message": "An unexpected error occurred."
}
```

---

## 🔐 Seguridad

Este endpoint **no requiere autenticación previa**. Está disponible públicamente para permitir nuevos registros.
