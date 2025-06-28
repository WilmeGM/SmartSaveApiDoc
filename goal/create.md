# 📘 Endpoint de Crear Meta — SmartSave API

**Método:** `POST`  
**Content-Type:** `application/json`  
**Ruta:** `/api/goal/create`  
**Descripción:** Permite a un usuario autenticado registrar una nueva meta de ahorro. Valida que el monto objetivo sea mayor a cero, que el monto actual no sea negativo y que nombre y fecha estén presentes.

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
  "name": "Viaje a Japón",
  "objectiveAmount": 5000.00,
  "currentAmount": 1000.00,
  "deadline": "2025-12-31"
}
```

---

## 📤 Respuestas posibles

### ✅ 200 OK  
La meta fue creada exitosamente.

```json
{
  "message": "Meta creada satisfactoriamente"
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
