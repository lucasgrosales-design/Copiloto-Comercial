# Proceso Comercial MVP

## Estados de una oportunidad

1. `nuevo` — oportunidad recién recibida.
2. `contacto_inicial` — se realizó el primer contacto.
3. `conversacion` — existe intercambio activo.
4. `calificado` — existe una necesidad y potencial comercial identificados.
5. `propuesta_enviada` — se envió una propuesta o presupuesto.
6. `seguimiento` — se espera respuesta o avance.
7. `negociacion` — existen condiciones, objeciones o ajustes en discusión.
8. `ganado` — venta confirmada.
9. `perdido` — oportunidad descartada.
10. `frio` — no hay respuesta después de la secuencia definida.

## Reglas iniciales

### Nuevo prospecto

- Registrar nombre, empresa, canal, fecha, origen y mensaje inicial.
- Crear una próxima acción.
- Evitar que una oportunidad quede sin responsable o sin próxima acción.

### Contacto inicial

- Registrar el mensaje enviado.
- Programar seguimiento si no existe respuesta.
- Si existe respuesta, detener el seguimiento automático pendiente y procesar el nuevo mensaje.

### Propuesta enviada

- Registrar fecha, monto si corresponde, producto/servicio y versión de propuesta.
- Crear una secuencia de seguimiento.
- No enviar mensajes duplicados.
- Si el prospecto responde, cancelar o recalcular los seguimientos pendientes.

### Respuesta con intención de compra

- Aumentar prioridad.
- Identificar próximo paso.
- Informar al responsable si la oportunidad supera los criterios configurados.

### Objeción

- Clasificar: precio, plazo, producto, confianza, competencia, timing, autoridad u otra.
- Registrar la objeción.
- Aplicar una respuesta permitida o derivar al humano según reglas.

### Oportunidad sin respuesta

- Ejecutar una secuencia limitada.
- Variar el motivo del contacto; no repetir exactamente el mismo mensaje.
- Al superar el máximo de intentos, pasar a `frio` y registrar la última acción.

## Reporte diario

El reporte debe responder, como mínimo:

- Cuántas oportunidades nuevas entraron.
- Cuántas están activas.
- Cuántas no tienen próxima acción.
- Cuántas tienen seguimiento vencido.
- Cuántas respondieron.
- Cuántas propuestas están pendientes.
- Qué oportunidades tienen mayor prioridad.
- Qué vendedores están convirtiendo mejor cuando exista equipo comercial.
- Qué oportunidades requieren intervención humana.

## Regla central

**Toda oportunidad activa debe tener estado, última interacción y próxima acción.**
