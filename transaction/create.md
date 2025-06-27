# 📘 Endpoint de Crear Transacción — SmartSave API

**Método:** `POST`  
**Content-Type:** `application/json`  
**Ruta:** `/api/transaction/create`  
**Descripción:** Permite a un usuario autenticado registrar una nueva transacción. Se validan campos requeridos, valor positivo, tipo permitido y se guarda la transacción asociada al usuario.

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
  "amount": 1500.00,
  "description": "Freelance payment",
  "date": "2025-06-27",
  "type": 0
}
```

---

## 📤 Respuestas posibles

### ✅ 200 OK  
La transacción fue creada exitosamente.

```json
{
  "message": "Transaction created successfully"
}
```

---

### ❌ 400 Bad Request — Errores de validación

#### Monto menor o igual a cero

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
