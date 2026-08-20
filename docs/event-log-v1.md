# Event Log v1

## Objetivo

Registrar cada hecho relevante del proceso comercial como un evento inmutable. La memoria y el pipeline son estados derivados; el log permite reconstruir qué ocurrió y cuándo.

## Eventos mínimos

- `prospect_created`
- `identity_linked`
- `message_received`
- `message_sent`
- `response_classified`
- `memory_updated`
- `stage_changed`
- `proposal_sent`
- `follow_up_scheduled`
- `follow_up_sent`
- `human_required`
- `human_notified`
- `won`
- `lost`
- `consent_updated`
- `do_not_contact`
- `error`

## Campos obligatorios

- `event_id`: identificador único;
- `event_type`;
- `occurred_at`;
- `contact_id` cuando exista;
- `opportunity_id` cuando exista;
- `channel` cuando corresponda;
- `source`;
- `payload` mínimo necesario;
- `schema_version`.

## Inmutabilidad

No se editan eventos históricos. Una corrección genera un nuevo evento que referencia al anterior.

## Idempotencia

`event_id` funciona como clave de idempotencia. Si el mismo evento llega nuevamente, se registra como duplicado técnico o se ignora según la implementación, pero nunca vuelve a ejecutar una acción comercial.

## Auditoría

Las acciones automáticas deben poder responder:

- qué ocurrió;
- qué contexto tenía el asistente;
- qué regla se aplicó;
- qué acción produjo;
- cuándo ocurrió;
- si fue automática o humana.

No guardar secretos ni credenciales en eventos.
