# 📘 Endpoint de Reset Password — SmartSave API

**Método:** `POST`  
**Content-Type:** `application/json`  
**Ruta:** `/api/auth/resetPassword`  
**Descripción:** Permite a un usuario autenticado cambiar su contraseña actual por una nueva. Se valida que los campos estén completos, que la nueva contraseña sea segura, que no sea igual a la anterior, y que la contraseña actual ingresada sea correcta.

---

## 📥 Cuerpo de la solicitud

```json
{
  "currentPassword": "string (obligatorio)",
  "newPassword": "string (obligatorio, segura)",
  "confirmNewPassword": "string (obligatorio, igual a newPassword)"
}
```

### 📄 Ejemplo

```json
{
  "currentPassword": "OldPass123",
  "newPassword": "NewStrongPass456",
  "confirmNewPassword": "NewStrongPass456"
}
```

---

## 📤 Respuestas posibles

### ✅ 200 OK  
La contraseña se cambió correctamente.

```json
{
  "message": "Password reseted correctly"
}
```

---

### ❌ 400 Bad Request — Errores de validación

#### Campos vacíos

```json
{
  "status": 400,
  "message": "Every field is required"
}
```

#### Nueva contraseña igual a la anterior

```json
{
  "status": 400,
  "message": "New password must be different"
}
```

#### Nueva contraseña débil

```json
{
  "status": 400,
  "message": "Password must be at least 8 characters and contain uppercase, lowercase and number."
}
```

#### Confirmación de contraseña no coincide

```json
{
  "status": 400,
  "message": "New password and confirm password must be the same."
}
```

#### Contraseña actual incorrecta

```json
{
  "status": 400,
  "message": "That's not the current password."
}
```

---

### ❌ 401 Unauthorized — El usuario no está autenticado

```json
{
  "status": 401,
  "message": "Unauthorized"
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

Este endpoint **requiere autenticación**. El token JWT debe enviarse en el encabezado de autorización:

```
Authorization: Bearer {token}
```
