# Auditoría V4 — WhatsApp

## Objetivo

Dejar un workflow importable y testeable por Claude Code antes de volver a configurar nodo por nodo en n8n.

Archivo: `n8n/04-copiloto-comercial-v4-whatsapp-audit-ready.json`

## Fallas bloqueantes detectadas en V3

1. **Faltaba la verificación GET de Meta en el JSON del workflow.** V3 tenía solo `POST /copiloto/meta`. V4 incorpora `GET /copiloto/meta` para la verificación y mantiene `POST /copiloto/meta` para mensajes.
2. **Los Code nodes tenían riesgo de código contaminado con barras invertidas** cuando el JSON se copiaba/pegaba. V4 contiene JavaScript limpio.
3. **La normalización de WhatsApp no tomaba correctamente el timestamp del mensaje.** V4 usa `m.timestamp` con fallback.
4. **La persistencia de criterio tenía SQL incorrecto para valores de texto/JSON cuando se usaba `JSON.stringify()` directamente como literal SQL.** V4 convierte explícitamente strings en literales SQL escapados y JSON en `jsonb`.
5. **El flujo V3 no estaba preparado para validar la ruta completa de WhatsApp desde webhook hasta respuesta sin revisar primero el ingreso.** V4 mantiene una cadena única y explícita para WhatsApp.
6. **Las credenciales y secretos siguen fuera del repositorio.** El workflow usa placeholders para Postgres y variables de entorno para Meta/OpenAI.

## Contrato de prueba WhatsApp

Entrada esperada de Meta:

- `entry[0].changes[0].value.messages[0].from`
- `entry[0].changes[0].value.messages[0].id`
- `entry[0].changes[0].value.messages[0].text.body`
- `entry[0].changes[0].value.messages[0].timestamp`

Salida de normalización esperada:

```json
{
  "route": "candidate",
  "event_input": {
    "channel": "whatsapp",
    "sender_id": "<sender>",
    "external_message_id": "<message_id>",
    "text": "<text>",
    "occurred_at": "<timestamp>"
  }
}
```

## Pruebas que Claude debe ejecutar

1. Validar que el JSON importa correctamente en n8n.
2. Validar que todos los nodos tienen conexiones de salida esperadas.
3. Validar que existen dos webhooks `/copiloto/meta`: GET para verificación y POST para mensajes.
4. Ejecutar prueba unitaria de normalización con un payload realista de WhatsApp.
5. Ejecutar prueba de mensaje inválido sin `sender_id`, sin `message_id` y sin texto.
6. Ejecutar prueba de evento duplicado y confirmar `route=duplicate`.
7. Validar SQL de creación de tablas.
8. Validar SQL de identidad/deduplicación contra PostgreSQL/Supabase de prueba.
9. Validar que la persistencia de criterio no genere errores de sintaxis SQL.
10. Mockear la respuesta de OpenAI y comprobar el parseo/validación del criterio.
11. Verificar que `auto_respond` solo sea verdadero con confianza >= 0.85, respuesta presente y sin handoff.
12. Verificar payload final de Meta para envío de WhatsApp.
13. Verificar que ninguna credencial, token o secreto aparezca en el JSON.

## Variables necesarias en runtime

- `META_VERIFY_TOKEN`
- `META_ACCESS_TOKEN`
- `META_PHONE_NUMBER_ID`
- `OPENAI_API_KEY`
- `COPILOTO_AI_MODEL` (opcional; fallback definido en workflow)

## Criterio de aceptación MVP

No avanzar a Instagram/Email ni a nuevas funciones hasta que Claude confirme que el recorrido WhatsApp completo es ejecutable:

`GET verificación → POST mensaje → normalización → validación → DB → deduplicación → IA → persistencia → decisión → respuesta WhatsApp`

La configuración de credenciales reales se realiza después de aprobar el workflow estructural.
