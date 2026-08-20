# Pipeline Comercial v1

## Etapas

`new → contacted → engaged → qualified → proposal_sent → negotiation → nurture → closed_won / closed_lost`

## Reglas de transición

- `new → contacted`: hubo primer contacto enviado.
- `contacted → engaged`: hubo respuesta con interés o interacción útil.
- `engaged → qualified`: existe necesidad real, encaje y posibilidad razonable de compra.
- `qualified → proposal_sent`: propuesta enviada.
- `proposal_sent → negotiation`: prospecto plantea cambios, precio o condiciones.
- `proposal_sent → closed_won`: compra confirmada.
- cualquier etapa activa → `nurture`: el prospecto pide retomar más adelante o no existe acción inmediata justificable.
- cualquier etapa activa → `closed_lost`: negativa explícita, descalificación o cierre por decisión humana.

## No avanzar automáticamente cuando

- la evidencia es insuficiente;
- hay contradicción entre señales;
- el cambio implica una decisión económica o contractual;
- la identidad del contacto no está confirmada.

## Estado obligatorio

Toda oportunidad activa debe tener:

- etapa;
- responsable;
- próximo paso;
- fecha o condición de próximo paso;
- último evento;
- resumen actualizado.

Si falta el próximo paso, Copiloto lo marca como anomalía.
