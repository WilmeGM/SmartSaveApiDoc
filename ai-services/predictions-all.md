## 📘 Endpoint de Obtener Todas las Predicciones — SmartSave API

**Método:** `GET`  
**Ruta:** `/api/predictions/all`  
**Descripción:** Devuelve un listado de **todas las predicciones financieras** generadas anteriormente por el sistema para el usuario autenticado. Estas predicciones pueden estar relacionadas con ingresos, gastos, o comportamientos financieros futuros.

---

## 📤 Respuestas posibles

### ✅ 200 OK  
Devuelve un arreglo de objetos con las predicciones almacenadas.

```json
[
  {
    "id": 1,
    "userId": 12,
    "predictionMessage": "Se espera un aumento en tus gastos de transporte este mes.",
    "createdAt": "2025-08-06T14:23:00"
  },
  {
    "id": 2,
    "userId": 12,
    "predictionMessage": "Tus ingresos han mostrado una tendencia estable.",
    "createdAt": "2025-08-01T09:15:00"
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

- Las predicciones son generadas previamente y almacenadas.
- Pueden utilizarse para análisis de comportamiento financiero.
- El orden de las predicciones suele ser cronológico (más reciente primero).

---

## 📎 Recomendaciones de uso

- Úsalo para mostrar un **historial de predicciones** en tu app.
- Puede combinarse con visualizaciones gráficas de comportamiento financiero.
