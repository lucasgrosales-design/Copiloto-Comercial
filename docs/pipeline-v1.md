# Pipeline Comercial v1

## Propósito

El pipeline es la fuente operativa de verdad de cada oportunidad. Debe permitir saber qué pasó, quién debe actuar y cuál es el próximo paso sin revisar conversaciones manualmente.

## Etapas

`new` → `contacted` → `engaged` → `qualified` → `proposal_sent` → `negotiation` → `won/lost`

Carril alternativo: `nurture`.

Carril de control: `human_required`.

## Campos mínimos

- `id`
- `created_at`
- `updated_at`
- `company_name`
- `contact_name`
- `email`
- `phone`
- `source`
- `owner_id`
- `status`
- `lead_score`
- `potential_value`
- `last_contact_at`
- `next_follow_up_at`
- `follow_up_count`
- `last_intent`
- `last_objection`
- `human_required`
- `human_reason`
- `last_message_summary`
- `next_action`
- `lost_reason`

## Sin vendedor

`owner_id` puede ser `null`. En ese caso el propio Copiloto ejecuta la gestión automatizada y escala al dueño/responsable cuando sea necesario.

## Con vendedores

Cada oportunidad puede tener un `owner_id`. El sistema registra las acciones del vendedor y compara resultados sin modificar la lógica central de seguimiento.

## Regla de responsabilidad

Toda oportunidad activa debe tener un próximo paso o una razón explícita para estar esperando. Una oportunidad activa sin `next_follow_up_at` ni `human_required` se considera una anomalía y debe aparecer en el reporte.

## Score inicial

El score MVP es orientativo, no predictivo. Puede sumar señales:

- +30 señal explícita de compra;
- +20 presupuesto solicitado;
- +15 problema/necesidad claramente identificada;
- +10 urgencia alta;
- +10 respuesta reciente;
- -15 ausencia prolongada de respuesta;
- -30 negativa explícita.

El score nunca reemplaza el criterio comercial ni debe presentarse como una probabilidad estadística real de compra.

## Reporte ejecutivo

El sistema debe priorizar excepciones:

1. oportunidades con señal fuerte de compra;
2. oportunidades de alto valor sin seguimiento;
3. propuestas enviadas sin respuesta;
4. oportunidades bloqueadas por una objeción;
5. oportunidades sin próximo paso;
6. vendedores con oportunidades atrasadas;
7. conversiones y pérdidas.

La finalidad del reporte no es llenar una pantalla de métricas. Es decirle al responsable dónde está el dinero y dónde se está perdiendo.
