# Registro de decisiones comerciales — Copiloto Comercial

| Fecha | Decisión | Motivo | Estado |
|---|---|---|---|
| 2026-08-24 | Crear un área comercial independiente dentro del repositorio | Centralizar estrategia, precios, competencia, modelo comercial y decisiones | Vigente |
| 2026-08-24 | Utilizar la propia comercialización de Copiloto Comercial como caso de uso/laboratorio | Validar el producto en condiciones reales y generar un caso demostrable | En elaboración |
| 2026-08-24 | Establecer inicialmente WhatsApp, email e Instagram como canales propios | Crear una infraestructura comercial mínima y controlable | En elaboración |
| 2026-08-24 | Priorizar Reel/video corto vertical como formato principal de contenido | Permitir demostrar problemas, situaciones y funcionamiento del producto | Hipótesis |
| 2026-08-24 | Crear un banco inicial de 100 contenidos | Evitar improvisación y convertir el contenido en un sistema comercial medible | Vigente como plan |
| 2026-08-24 | Probar primero un lote piloto de 10 contenidos antes de producir en volumen | Validar temas, hooks, formatos y CTA antes de escalar producción | Próxima acción |
| 2026-08-24 | Consolidar la estrategia comercial y el plan de contenido en `docs/estrategia-comercial-copiloto-v1.md` y `docs/plan-contenido-100-dias-v1.md`, eliminando las versiones previas | Evitar dos fuentes de verdad para el mismo tema | Vigente |
| 2026-08-24 | Mantener el mensaje de salida del flujo de ingreso como borrador y no enviarlo automáticamente | El motor comercial todavía debe analizar la oportunidad antes de decidir qué responder | Vigente |
| 2026-08-24 | Usar `data/event-schema-v1.json` como esquema canónico de eventos del MVP | Evitar divergencias entre workflows y modelos de datos | Vigente |

## Criterio de gobierno

Este archivo funciona como **índice de decisiones comerciales**. Las decisiones relevantes deben registrarse aquí o desarrollarse en documentos específicos dentro de `comercial/` o `docs/` cuando corresponda.

Las ideas e hipótesis **no se consideran decisiones definitivas** hasta contar con validación, evidencia o aprobación explícita.

### Regla de fuente de verdad

Cuando un documento específico desarrolla una decisión registrada aquí, ese documento contiene el detalle operativo y este archivo conserva el estado y el vínculo conceptual. No deben existir dos documentos que compitan como fuente de verdad sobre la misma decisión.

### Regla de implementación

El producto propio debe utilizarse como laboratorio comercial. Toda automatización nueva debe poder probarse sobre este caso real, pero sin convertir hipótesis de negocio en comportamiento automático irreversible.

## Estados

- **Hipótesis:** idea en evaluación; no compromete el producto ni la estrategia definitiva.
- **Próxima acción:** decisión adoptada cuyo siguiente paso todavía debe ejecutarse.
- **En elaboración:** dirección aprobada, pendiente de completar validación o implementación.
- **Vigente:** decisión actualmente adoptada.
- **Descartada:** decisión o hipótesis reemplazada por evidencia o por una decisión posterior.

## Actualización

Este registro debe actualizarse cuando una hipótesis se convierta en decisión, una decisión sea modificada o una línea de trabajo sea descartada por evidencia.
