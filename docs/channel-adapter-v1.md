# Adaptadores de Canales v1

## Decisión de arquitectura

Todos los canales deben convertirse al mismo formato interno `InboundMessage` y todas las salidas deben utilizar `OutboundMessage`.

El núcleo comercial no conoce detalles de WhatsApp, email o redes sociales.

## InboundMessage

```json
{
  "event_id":"evt-123",
  "channel":"whatsapp",
  "external_message_id":"msg-456",
  "contact_id":"contact-123",
  "opportunity_id":"opp-123",
  "received_at":"2026-08-20T12:00:00Z",
  "text":"Perfecto, ¿cómo seguimos?",
  "attachments":[],
  "metadata":{}
}
```

## Canales previstos

- `whatsapp`
- `email`
- `instagram`
- `facebook`
- `linkedin`
- `webchat`
- `other`

## OutboundMessage

```json
{
  "opportunity_id":"opp-123",
  "channel":"whatsapp",
  "recipient":"external-id",
  "text":"...",
  "reply_to_external_message_id":"msg-456",
  "idempotency_key":"out-789"
}
```

## Reglas

1. Un contacto puede interactuar por varios canales.
2. Los canales no crean oportunidades duplicadas si ya existe una oportunidad identificable.
3. El núcleo decide qué decir y qué hacer; el adaptador solamente entrega/recibe.
4. Cada mensaje debe conservar canal y `external_message_id`.
5. Los errores de un canal no deben romper el pipeline comercial completo.
6. Las preferencias y solicitudes de no contacto se aplican transversalmente cuando corresponda.

## MVP de prueba propio

El modelo de prueba de Copiloto Comercial conectará inicialmente los tres canales propios definidos para el MVP:

- WhatsApp
- email
- Instagram

La implementación puede realizarse por etapas técnicas, pero los tres forman parte del alcance del MVP de prueba. El núcleo comercial debe permanecer independiente de los adaptadores para que una demora o error de un canal no obligue a modificar memoria, inteligencia o pipeline.
