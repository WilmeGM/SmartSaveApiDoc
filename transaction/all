# 📘 Endpoint de Obtener Todas las Transacciones — SmartSave API

**Método:** `GET`  
**Ruta:** `/api/transaction/all`  
**Descripción:** Devuelve la lista completa de transacciones asociadas al usuario autenticado. El backend filtra internamente por `UserId`, por lo que no es necesario pasarlo como parámetro.

---

## 📤 Respuestas posibles

### ✅ 200 OK  
Devuelve un arreglo de transacciones pertenecientes al usuario.

```json
[
  {
    "id": 1,
    "amount": 120.00,
    "description": "Coffee shop",
    "date": "2025-06-27",
    "type": 1
  },
  {
    "id": 2,
    "amount": 1500.00,
    "description": "Salary",
    "date": "2025-06-25",
    "type": 0
  }
]
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
