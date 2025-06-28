# 📘 Endpoint de Obtener Meta por ID — SmartSave API

**Método:** `GET`  
**Ruta:** `/api/goal/{id}`  
**Descripción:** Devuelve los detalles de una meta específica asociada al usuario autenticado. Si la meta no existe o no pertenece al usuario, se devuelve un error 404 controlado.

---

## 🔢 Parámetros

- `id` (en la URL): ID numérico de la meta a consultar.

---

## 📤 Respuestas posibles

### ✅ 200 OK  
Devuelve los detalles de la meta solicitada.

```json
{
  "id": 3,
  "name": "Renovación del hogar",
  "objectiveAmount": 12000.00,
  "currentAmount": 4500.00,
  "deadline": "2026-06-30"
}
```

---

### ❌ 404 Not Found — Meta no encontrada o no pertenece al usuario

```json
{
  "status": 404,
  "message": "Meta no encontrada"
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
