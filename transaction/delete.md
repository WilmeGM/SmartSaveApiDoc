# 📘 Endpoint de Eliminar Transacción — SmartSave API

**Método:** `DELETE`  
**Ruta:** `/api/transaction/{id}`  
**Descripción:** Permite a un usuario autenticado eliminar una transacción específica por ID. Solo puede eliminar transacciones que le pertenezcan. Si la transacción no existe o pertenece a otro usuario, se devuelve un error controlado.

---

## 🔢 Parámetros

- `id` (en la URL): ID numérico de la transacción a eliminar.

---

## 📤 Respuestas posibles

### ✅ 200 OK  
La transacción fue eliminada correctamente.

```json
{
  "message": "Transaction deleted successfully"
}
```

---

### ❌ 404 Not Found — Transacción no encontrada o no pertenece al usuario

```json
{
  "status": 404,
  "message": "Transaction not found or does not belong to the user."
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
