# 📘 Endpoint de Obtener Transacción por ID — SmartSave API

**Método:** `GET`  
**Ruta:** `/api/transaction/{id}`  
**Descripción:** Permite a un usuario autenticado obtener los detalles de una transacción específica mediante su ID. Si la transacción no existe, se devuelve un mensaje de error claro.

---

## 🔢 Parámetros

- `id` (en la URL): ID numérico de la transacción a consultar.

---

## 📤 Respuestas posibles

### ✅ 200 OK  
Devuelve los detalles de la transacción solicitada.

```json
{
  "id": 12,
  "amount": 340.75,
  "description": "Restaurant dinner",
  "date": "2025-06-26",
  "type": 1
}
```

---

### ❌ 404 Not Found — La transacción no fue encontrada

```json
{
  "status": 404,
  "message": "Transaction not found"
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
