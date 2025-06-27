# 📘 Endpoint de Login — SmartSave API

**Método:** `POST`
**Content-Type**: `application/json`
**Ruta:** `/api/auth/login`  
**Descripción:** Permite al usuario autenticarse con su correo electrónico y contraseña. Si las credenciales son válidas, devuelve un token JWT junto con los datos del usuario autenticado.

---

## 📥 Cuerpo de la solicitud

```json
{
  "email": "string (obligatorio)",
  "password": "string (obligatorio)"
}
```

### 📄 Ejemplo

```json
{
  "email": "admin@email.com",
  "password": "1234"
}
```

---

## 📤 Respuestas posibles

### ✅ 200 OK

```json
{
  "firstName": "Wilme",
  "email": "admin@email.com",
  "token": "eyJhbGciOiJIUzI1NiIsInR5..."
}
```

---

### ❌ 400 Bad Request — Campos vacíos o inválidos

```json
{
  "status": 400,
  "message": "Every field is required"
}
```

---

### ❌ 401 Unauthorized — Credenciales incorrectas

```json
{
  "status": 401,
  "message": "Invalid email or password."
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

Este endpoint **no requiere autenticación previa**.  
El token JWT recibido debe enviarse en futuras peticiones autenticadas usando el encabezado:

```
Authorization: Bearer {token}
```
