# 📘 Endpoint de Obtener Predicción Financiera — SmartSave API

**Método:** `GET`  
**Ruta:** `/api/aiservices/prediction`  
**Descripción:** Devuelve una **predicción generada por inteligencia artificial** sobre la posibilidad de que el usuario cumpla sus metas financieras, según sus ingresos, gastos y objetivos actuales. No requiere parámetros adicionales, ya que la información del usuario se obtiene del token de autenticación.

---

## 📤 Respuestas posibles

### ✅ 200 OK  
Devuelve un objeto con una predicción personalizada basada en los datos financieros del usuario.

```json
{
  "predictionMessage": "Si mantienes tu nivel actual de ahorro mensual, podrás alcanzar tu meta de 'Viaje a Japón' antes del plazo establecido. Sin embargo, deberías considerar aumentar el ahorro destinado a 'Comprar laptop'."
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

---

## 💡 Detalles adicionales

- La predicción es generada por un modelo de IA (Mistral 7B) alojado en OpenRouter.
- Se basa en el análisis de metas y transacciones actuales del usuario.
- La predicción es almacenada en la base de datos para futuros análisis.

---

## 📎 Recomendaciones de uso

- Consumir este endpoint cuando el usuario quiera conocer su **progreso financiero estimado**.
- Útil para generar alertas o notificaciones sobre el cumplimiento de metas.
- Ideal como complemento visual en dashboards financieros de la aplicación.
