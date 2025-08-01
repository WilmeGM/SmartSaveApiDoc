# 📘 Endpoint de Obtener Sugerencia Financiera — SmartSave API

**Método:** `GET`  
**Ruta:** `/api/aiservices/suggestion`  
**Descripción:** Devuelve una **sugerencia financiera personalizada** generada por inteligencia artificial. Se basa en los ingresos, gastos y metas asociadas al usuario autenticado. El procesamiento se realiza en el backend, por lo que no requiere parámetros adicionales.

---

## 📤 Respuestas posibles

### ✅ 200 OK  
Devuelve un objeto con una sugerencia personalizada para mejorar las finanzas personales del usuario.

```json
{
  "suggestionMessage": "Podrías reducir tus gastos en entretenimiento y destinar más fondos a tu meta de 'Comprar laptop'. Considera ahorrar un monto fijo mensual para alcanzar tu objetivo antes del plazo establecido."
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

- La sugerencia es generada por un modelo de IA (Mistral 7B) alojado en OpenRouter.
- Se utilizan los datos actuales del usuario (metas y transacciones) para construir el *prompt*.
- La respuesta se guarda en la base de datos para su posterior análisis o consulta.

---

\## 📎 Recomendaciones de uso

- Consumir este endpoint **después de tener registradas transacciones y metas**.
- Usarlo como parte de una funcionalidad de asesoría o resumen financiero dentro de la aplicación.
