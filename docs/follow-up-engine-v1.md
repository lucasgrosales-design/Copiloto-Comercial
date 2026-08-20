# Motor de Seguimiento Comercial v1

## Objetivo

Mantener activas las oportunidades sin convertir el sistema en una máquina de spam. Cada seguimiento debe tener un motivo comercial, contexto y límite.

## Entradas

- etapa actual;
- último evento;
- último contacto;
- cantidad de seguimientos;
- intención detectada;
- objeciones;
- próximo paso acordado;
- canal preferido/autorizado;
- reglas de cadencia;
- solicitudes de no contacto.

## Decisión

El motor evalúa en este orden:

1. **No contacto** → detener cualquier seguimiento automático.
2. **Humano requerido** → no enviar automáticamente; generar alerta.
3. **Respuesta pendiente de nosotros** → priorizar respuesta.
4. **Próximo paso acordado** → ejecutar cuando llegue la fecha/hora.
5. **Propuesta enviada sin respuesta** → seguimiento contextual.
6. **Interés sin próximo paso** → pedir definición del siguiente paso.
7. **Oportunidad inactiva** → aplicar reactivación limitada.
8. **Sin potencial suficiente** → no insistir.

## Cadencia MVP

Valores iniciales de prueba:

- primer seguimiento: 24 horas después de una propuesta sin respuesta;
- segundo seguimiento: 72 horas después;
- tercer seguimiento: 7 días después;
- luego: detener seguimiento automático y pasar a nurture o cierre según contexto.

Son defaults de prueba, no reglas universales. Cada cliente podrá configurar su cadencia por canal y tipo de oportunidad.

## Personalización

Nunca enviar solamente “¿viste mi mensaje?”. El seguimiento debe usar el contexto disponible.

Ejemplo:

> Hola María. Quería saber qué te pareció la propuesta que te enviamos. Si hubo algún punto que no quedó claro, decime y lo revisamos para ver si podemos encontrar la mejor solución para lo que necesitan.

## Límites

- respetar solicitudes de no contacto;
- respetar ventanas, límites y políticas aplicables del canal;
- no prometer descuentos o condiciones no autorizadas;
- no reiniciar la cadencia indefinidamente;
- si el prospecto responde, detener el seguimiento programado y volver a interpretar la conversación.

## Resultado del motor

```json
{
  "decision":"follow_up|wait|notify_human|close|nurture|respond",
  "reason":"...",
  "channel":"whatsapp",
  "scheduled_at":"...",
  "message_intent":"proposal_follow_up",
  "priority":"high|medium|low"
}
```

El motor decide **qué corresponde hacer**. Un adaptador de canal decide **cómo entregarlo**.
