# 📘 Endpoint de Editar Transacción — SmartSave API

**Método:** `PUT`  
**Ruta:** `/api/transaction/edit/{id}`  
**Descripción:** Permite a un usuario autenticado actualizar por completo una transacción existente. Los datos deben enviarse completos, incluso si solo se modifica un campo. Solo puede editar transacciones que le pertenezcan.

---

## 🔢 Parámetros

- `id` (en la URL): ID numérico de la transacción a actualizar.

---

## 📥 Cuerpo de la solicitud

```json
{
  "amount": decimal (obligatorio, mayor a 0),
  "description": "string (obligatorio)",
  "date": "yyyy-MM-dd (obligatorio)",
  "type": int (obligatorio: 0 = Income, 1 = Expense)
}
```

### 📄 Ejemplo

```json
{
  "amount": 350.00,
  "description": "Updated grocery bill",
  "date": "2025-06-28",
  "type": 1
}
```

---

## 📤 Respuestas posibles

### ✅ 200 OK  
La transacción fue actualizada exitosamente.

```json
{
  "message": "Transaction updated successfully"
}
```

---

### ❌ 400 Bad Request — Errores de validación

#### Monto inválido

```json
{
  "status": 400,
  "message": "Amount must be greater than 0."
}
```

#### Falta la descripción o la fecha

```json
{
  "status": 400,
  "message": "Description or date are required."
}
```

#### Tipo de transacción inválido

```json
{
  "status": 400,
  "message": "Invalid transaction type. Must be either 'Income (0)' or 'Expense (1)'."
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
