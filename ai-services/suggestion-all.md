## 📘 Endpoint de Obtener Todas las Sugerencias — SmartSave API

**Método:** `GET`  
**Ruta:** `/api/suggestions/all`  
**Descripción:** Devuelve un listado de **todas las sugerencias financieras** que el sistema ha generado anteriormente para el usuario autenticado.

---

## 📤 Respuestas posibles

### ✅ 200 OK  
Devuelve un arreglo de sugerencias almacenadas con su fecha de creación.

```json
[
  {
    "id": 5,
    "userId": 12,
    "suggestionMessage": "Reduce tus gastos en comida rápida para cumplir tu meta de ahorro mensual.",
    "createdAt": "2025-08-05T17:30:00"
  },
  {
    "id": 6,
    "userId": 12,
    "suggestionMessage": "Considera aumentar tu fondo de emergencia en un 10%.",
    "createdAt": "2025-08-03T13:45:00"
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

---

## 💡 Detalles adicionales

- Las sugerencias se generan usando inteligencia artificial.
- Se basan en los ingresos, gastos y metas del usuario.
- Pueden ser útiles como guía para tomar decisiones financieras.

---

## 📎 Recomendaciones de uso

- Mostrar una lista de sugerencias pasadas al usuario.
- Integrarlas con el historial financiero y alertas.
