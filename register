# 📘 Endpoint de Register — SmartSave API

**Método:** `POST`  
**Content-Type**: `application/json`  
**Ruta:** `/api/auth/register`  
**Descripción:** Permite registrar un nuevo usuario en el sistema. Valida que todos los campos estén completos, que el correo no esté en uso y que las contraseñas coincidan. Si todo es correcto, guarda el usuario en la base de datos.

---

## 📥 Cuerpo de la solicitud

```json
{
  "firstName": "string (obligatorio)",
  "lastName": "string (obligatorio)",
  "email": "string (obligatorio)",
  "password": "string (obligatorio)",
  "confirmPassword": "string (obligatorio)"
}
```

### 📄 Ejemplo

```json
{
  "firstName": "Wilme",
  "lastName": "GM",
  "email": "admin@email.com",
  "password": "1234",
  "confirmPassword": "1234"
}
```

---

## 📤 Respuestas posibles

### ✅ 200 OK  
El usuario se registró correctamente.  
*No retorna contenido.*

---

### ❌ 400 Bad Request — Campos vacíos, contraseñas distintas o correo ya registrado

```json
{
  "status": 400,
  "message": "Every field is required"
}
```

```json
{
  "status": 400,
  "message": "Passwords must be the same."
}
```

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
