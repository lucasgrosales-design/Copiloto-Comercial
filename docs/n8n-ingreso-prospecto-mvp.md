# Workflow MVP — Ingreso de prospecto

## Propósito

Workflow importable para n8n que recibe una consulta de un prospecto y devuelve un registro comercial inicial sin requerir credenciales ni servicios externos.

## Flujo

```
Webhook POST → Validar y crear oportunidad → Responder JSON
```

El workflow aún **no** envía mensajes reales ni guarda datos de forma persistente. Deja preparado:

- evento normalizado;
- contacto (confirmado o candidato);
- oportunidad en etapa `new`;
- próximo paso;
- borrador de respuesta, pendiente de conectar el canal.

## Importación en n8n

1. Abrí n8n y elegí **Import from File**.
2. Seleccioná `n8n/copiloto-ingreso-prospecto-mvp.json`.
3. Abrí el nodo **Entrada de prospecto** y copiá la URL de prueba.
4. Ejecutá **Listen for test event** y enviá un POST con el ejemplo siguiente.
5. Cuando la prueba responda correctamente, activá el workflow y usá la URL de producción.

## Entrada mínima

```json
{
  "channel": "whatsapp",
  "external_message_id": "msg-001",
  "text": "Hola, quiero saber cómo funciona."
}
```

Campos opcionales: `event_id`, `contact_id`, `opportunity_id`, `received_at`, `sender_id`, `sender`, `owner`.

## Resultado

- Con entrada válida, responde `201` y devuelve `contact`, `opportunity` y `outbound_message_draft`.
- Con `channel`, `external_message_id` o `text` ausente, responde `400`.

## Próximo workflow

Persistir contacto, oportunidad y evento de forma idempotente, y después conectar el adaptador de WhatsApp o email para entregar el borrador autorizado.
