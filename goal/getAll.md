# 📘 Endpoint de Obtener Todas las Metas — SmartSave API

**Método:** `GET`  
**Ruta:** `/api/goal/all`  
**Descripción:** Devuelve un listado de todas las metas asociadas al usuario autenticado. No requiere parámetros adicionales, ya que el filtro por usuario se realiza en el backend.

---

## 📤 Respuestas posibles

### ✅ 200 OK  
Devuelve un arreglo con todas las metas del usuario.

```json
[
  {
    "id": 1,
    "name": "Viaje a Japón",
    "objectiveAmount": 5000.00,
    "currentAmount": 1200.00,
    "deadline": "2025-12-31"
  },
  {
    "id": 2,
    "name": "Comprar laptop",
    "objectiveAmount": 1800.00,
    "currentAmount": 500.00,
    "deadline": "2026-03-01"
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
