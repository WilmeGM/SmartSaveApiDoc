# 📘 Endpoint de Editar Meta — SmartSave API

**Método:** `PUT`  
**Ruta:** `/api/goal/{id}`  
**Descripción:** Permite a un usuario autenticado actualizar una meta de ahorro existente. Solo puede editar metas que le pertenezcan. El objeto enviado debe contener todos los campos, incluso si algunos valores permanecen iguales.

---

## 🔢 Parámetros

- `id` (en la URL): ID numérico de la meta a actualizar.

---

## 📥 Cuerpo de la solicitud

```json
{
  "name": "string (obligatorio)",
  "objectiveAmount": decimal (obligatorio, > 0),
  "currentAmount": decimal (obligatorio, ≥ 0),
  "deadline": "yyyy-MM-dd (obligatorio)"
}
```

### 📄 Ejemplo

```json
{
  "name": "Fondo de emergencia",
  "objectiveAmount": 3000.00,
  "currentAmount": 1250.00,
  "deadline": "2026-03-15"
}
```

---

## 📤 Respuestas posibles

### ✅ 200 OK  
La meta fue actualizada exitosamente.

```json
{
  "message": "Meta actualizada satisfactoriamente"
}
```

---

### ❌ 400 Bad Request — Errores de validación

#### Monto objetivo inválido

```json
{
  "status": 400,
  "message": "El monto objetivo debe ser mayor que cero."
}
```

#### Monto actual negativo

```json
{
  "status": 400,
  "message": "El monto actual no puede ser negativo."
}
```

#### Nombre o fecha ausente

```json
{
  "status": 400,
  "message": "El nombre o la fecha son requeridos."
}
```

---

### ❌ 404 Not Found — Meta no encontrada o no pertenece al usuario

```json
{
  "status": 404,
  "message": "Meta no encontrada o no pertenece al usuario."
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
