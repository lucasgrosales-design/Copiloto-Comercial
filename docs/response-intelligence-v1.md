# Motor de Interpretación Comercial v1

## Objetivo
Convertir cada respuesta del prospecto en señales estructuradas que permitan actualizar memoria, pipeline y próxima acción.

## Salida
- `intent`: purchase_signal | interest | question | objection | not_now | negative | unclear | support
- `objection_type`: price | timing | trust | fit | implementation | authority | other | null
- `sentiment`: positive | neutral | negative | mixed
- `urgency`: high | medium | low | unknown
- `stage_recommendation`: qualified | proposal_sent | negotiation | nurture | closed_won | closed_lost | unchanged
- `human_required`: boolean
- `reason`
- `recommended_next_action`
- `confidence`: 0..1

## Reglas

1. Una señal explícita de compra tiene prioridad.
2. Una solicitud de no contacto detiene toda automatización.
3. Una objeción económica o contractual relevante requiere humano.
4. Una respuesta ambigua no debe provocar una acción irreversible.
5. La IA no inventa intención; si la evidencia es insuficiente, devuelve `unclear`.
6. La recomendación nunca reemplaza las reglas de seguridad ni las políticas de canal.

## Ejemplos

### Compra
“Perfecto, ¿cómo hacemos para contratar?”
→ `purchase_signal`, `human_required=true`, prioridad alta.

### Precio
“Me interesa, pero está caro.”
→ `objection`, `objection_type=price`, `human_required=true`.

### Más adelante
“Ahora no, escribime el mes que viene.”
→ `not_now`, `nurture`, programar próximo contacto.

### Negativa
“No me interesa, gracias.”
→ `negative`, cerrar y detener seguimiento.

### Pregunta
“¿Cuánto demora la implementación?”
→ `question`; responder solamente si la información está autorizada.
