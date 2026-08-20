# Motor de Seguimiento Comercial v1

## Objetivo

Convertir el seguimiento comercial en un proceso sistemático, persistente y contextual. El asistente debe ejecutar el próximo paso sin depender de que un director comercial recuerde cada tarea.

## Principio central

El asistente no manda mensajes por mandar. Cada contacto debe tener un motivo, un contexto y una condición de salida.

## Estados

1. `new` — prospecto recibido, todavía sin contacto.
2. `contacted` — se realizó el primer contacto.
3. `engaged` — el prospecto respondió o mostró interés.
4. `qualified` — existe una necesidad y oportunidad comercial identificable.
5. `proposal_sent` — se envió una propuesta o presupuesto.
6. `follow_up_due` — corresponde realizar seguimiento.
7. `negotiation` — existe conversación comercial activa.
8. `won` — venta concretada.
9. `lost` — oportunidad perdida con motivo registrado.
10. `nurture` — no está listo ahora, pero puede reactivarse.
11. `human_required` — requiere intervención humana.

## Motor de decisión

Para cada oportunidad el sistema evalúa:

- estado actual;
- última interacción;
- respuesta del prospecto;
- tiempo transcurrido desde el último contacto;
- próximo paso programado;
- intención detectada;
- objeciones detectadas;
- valor potencial;
- urgencia;
- cantidad de seguimientos realizados;
- existencia de una condición que requiera humano.

El resultado siempre debe ser una de estas acciones:

- `wait` — todavía no contactar;
- `send_follow_up` — enviar seguimiento;
- `change_stage` — actualizar etapa;
- `schedule_task` — programar acción futura;
- `notify_human` — avisar al responsable;
- `close` — cerrar como ganada/perdida/nurture.

## Cadencia inicial MVP

### Después del primer contacto

- Si responde: procesar respuesta y continuar conversación.
- Si no responde: seguimiento 1 después del intervalo configurado.
- Si continúa sin respuesta: seguimiento 2 con un enfoque diferente.
- Si continúa sin respuesta: seguimiento 3 y luego pasar a `nurture` salvo que el valor/urgencia justifique revisión humana.

### Después de enviar presupuesto

- Confirmar recepción.
- Si no hay respuesta: seguimiento contextual, no genérico.
- Si aparece una objeción: clasificarla y responder dentro de las reglas configuradas.
- Si la conversación muestra intención de compra: pasar a `negotiation` y notificar al humano.
- Si pide cambios en precio, alcance, condiciones o una excepción: `human_required`.

## Regla de naturalidad

No se utilizará una cadencia rígida idéntica para todos. El mensaje debe considerar la última interacción y evitar repetir información que el prospecto ya conoce.

El asistente puede cambiar el tono y el ángulo del seguimiento, pero nunca debe inventar información, descuentos, condiciones comerciales o compromisos no autorizados.

## Escalamiento humano

Se escala cuando:

- el prospecto solicita una persona;
- hay negociación sensible de precio o condiciones;
- existe una objeción fuera del conocimiento disponible;
- el prospecto muestra alta intención de compra;
- hay una oportunidad de alto valor;
- el asistente no tiene suficiente información para responder con seguridad.

## Registro obligatorio

Cada acción debe dejar registro de:

- fecha y hora;
- oportunidad;
- canal;
- acción realizada;
- mensaje enviado o resumen de la interacción;
- resultado;
- nuevo estado;
- próximo paso;
- fecha del próximo paso;
- motivo de escalamiento, si corresponde.

## Métricas MVP

El sistema debe poder reportar:

- prospectos recibidos;
- prospectos contactados;
- respuestas;
- oportunidades calificadas;
- presupuestos enviados;
- seguimientos pendientes;
- seguimientos realizados;
- oportunidades sin seguimiento;
- conversiones;
- oportunidades perdidas;
- motivos de pérdida;
- tiempo promedio hasta respuesta;
- desempeño por vendedor cuando exista equipo comercial.

## WhatsApp ejecutivo

El asistente debe poder generar un resumen operativo para el responsable. Ejemplo:

> Detecté 5 oportunidades con potencial que llevan más tiempo del esperado sin una acción comercial. 2 recibieron presupuesto, 2 están esperando respuesta y 1 mostró interés pero quedó sin próximo paso. Preparé las acciones sugeridas para cada una.

El responsable no tiene que pedirle al asistente que revise el pipeline: el sistema debe detectar situaciones relevantes y comunicarlas proactivamente.

## Límite del MVP

La primera versión prioriza seguimiento, registro, clasificación y alertas. No intenta automatizar toda la venta. La intervención humana permanece disponible en los puntos donde una decisión comercial puede comprometer dinero, margen, condiciones o relación con el cliente.
