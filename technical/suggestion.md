# 📘 Documentación Técnica: Endpoint `/suggestion`

## 📂 Archivo
`AIServicesController.cs`

## 📌 Descripción General
Este endpoint forma parte del controlador `AIServicesController` y se encarga de generar una **sugerencia financiera personalizada** para el usuario autenticado, basándose en sus ingresos, gastos y metas registradas. Utiliza IA a través de OpenRouter para procesar los datos del usuario y devolver una respuesta útil.

---

## 🧠 Flujo General del Endpoint

1. Obtiene el `userId` desde el token de autenticación.
2. Consulta todas las metas (`Goals`) y transacciones (`Transactions`) del usuario.
3. Construye un *prompt* con esos datos usando `PromptBuilder.BuildSuggestionPrompt()`.
4. Envía el *prompt* a OpenRouter a través de `OpenRouterApiService.SendMessageAsync()`.
5. Recibe una sugerencia generada por IA.
6. Guarda esa sugerencia en la base de datos mediante `AIServicesService.SaveSuggestionAsync()`.
7. Devuelve un objeto `GetSuggestionDto` con el mensaje generado.

---

## 📥 Ruta del Endpoint

```csharp
[HttpGet("suggestion")]
public async Task<IActionResult> GetSuggestion()
```

---

## ✅ Respuesta Exitosa

- Código: `200 OK`
- Tipo: `GetSuggestionDto`
- Estructura:

```json
{
  "suggestionMessage": "Tu sugerencia personalizada generada por IA..."
}
```

---

## ❌ Posibles Errores

- Código: `500 InternalServerError`
- Mensaje: Error interno si falla alguna de las operaciones (consultas, IA, guardado, etc.)

---

## 🛠️ Clases Clave

### 1. `PromptBuilder.cs`

Genera el texto del *prompt* que se le envía a la IA:

```csharp
public static string BuildSuggestionPrompt(IEnumerable<GetGoalDto> goals, IEnumerable<GetTransactionDto> transactions)
```

Resumen de lógica:
- Suma ingresos y gastos mensuales.
- Calcula el ahorro mensual (`savings`).
- Lista metas si existen.
- Construye el mensaje solicitando sugerencias financieras.

---

### 2. `OpenRouterApiService.cs`

```csharp
public async Task<string> SendMessageAsync(string prompt)
```

- Envia el *prompt* a OpenRouter API.
- Usa el modelo `mistralai/mistral-7b-instruct`.
- Retorna el contenido del mensaje generado por la IA.

---

### 3. `AIServicesService.cs`

Guarda la sugerencia en la base de datos:

```csharp
public async Task SaveSuggestionAsync(GetSuggestionDto dto, DateTime now, int userId)
```

Convierte el DTO en una entidad `Suggestion` y lo persiste usando el repositorio.

---

### 4. `AIServicesRepository.cs`

Accede directamente al `DbContext` para guardar:

```csharp
public async Task SaveSuggestionAsync(Suggestion suggestion)
```

---

## 🧾 Entidades

### `Suggestion`

- `UserId`: Identificador del usuario.
- `SuggestionMessage`: Texto generado por IA.
- `CreatedAt`: Fecha y hora del registro.

---

## 🧪 Pruebas y Consideraciones

- El endpoint requiere autenticación.
- Asegurarse de que el usuario tenga transacciones registradas.
- Si no hay metas, igual se genera el *prompt* indicando que no tiene metas definidas.

---

## 🧩 Dependencias

- `IGoalService`
- `ITransactionService`
- `IOpenRouterApiService`
- `IAIServicesService`

---

## 🚀 Recomendaciones

- Evitar el hardcoding de la API key en el servicio `OpenRouterApiService`.
- Implementar manejo de errores más específico en el `catch`.

---
