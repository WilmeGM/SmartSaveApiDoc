# 📘 Endpoint de Eliminar Meta — SmartSave API

**Método:** `DELETE`  
**Ruta:** `/api/goal/{id}`  
**Descripción:** Permite a un usuario autenticado eliminar una meta existente por su ID. Solo se puede eliminar metas que pertenezcan al usuario autenticado.

---

## 🔢 Parámetros

- `id` (en la URL): ID numérico de la meta a eliminar.

---

## 📤 Respuestas posibles

### ✅ 200 OK  
La meta fue eliminada exitosamente.

```json
{
  "message": "Meta eliminada satisfactoriamente"
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
