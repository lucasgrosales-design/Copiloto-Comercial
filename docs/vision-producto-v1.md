# Visión del Producto v1

## Problema

Las empresas reciben consultas y oportunidades comerciales que se enfrían o se pierden porque el seguimiento depende de la memoria, disciplina y disponibilidad de una persona.

El problema existe tanto en empresas con vendedores como en empresas donde el dueño o responsable comercial atiende personalmente las oportunidades.

## Solución

Copiloto Comercial es un asistente especializado que registra oportunidades, ejecuta seguimientos definidos por contexto, interpreta respuestas, mantiene el historial y avisa al responsable cuando una oportunidad necesita intervención humana.

No reemplaza al vendedor. Reemplaza la falta de sistema y reduce el trabajo repetitivo de seguimiento.

## Usuario objetivo inicial

- Dueños de pequeñas y medianas empresas.
- Responsables comerciales.
- Equipos comerciales pequeños.
- Empresas que reciben consultas por WhatsApp, email, formularios u otros canales y no tienen un seguimiento consistente.

## Caso de uso principal

1. Entra una consulta.
2. El asistente registra el prospecto.
3. Se identifica el contexto y el estado comercial.
4. Se define el próximo paso.
5. El asistente realiza el seguimiento correspondiente.
6. Si el prospecto responde, interpreta la respuesta y actualiza el estado.
7. Si aparece una objeción o una oportunidad de alto valor, informa al responsable.
8. Si no hay respuesta, continúa la secuencia según las reglas definidas.
9. El responsable recibe reportes y alertas accionables.

## Ejemplo: presupuesto sin respuesta

Después de enviar un presupuesto, el asistente controla el estado. Si no hay respuesta dentro de la ventana configurada, puede enviar un mensaje natural para confirmar recepción. Si continúa sin respuesta, realiza un segundo contacto con otro enfoque. Si detecta una respuesta, deja de ejecutar mensajes automáticos incompatibles con la conversación y pasa a interpretar el nuevo contexto.

## Principios de diseño

- Natural antes que robótico.
- Seguimiento antes que simple notificación.
- Contexto antes que mensajes genéricos.
- Acción antes que reportes decorativos.
- Humano en el circuito cuando el riesgo o valor de la oportunidad lo justifica.
- Configurable por empresa.
- Medible por resultados.

## Arquitectura conceptual

El producto se construye sobre un núcleo común de asistentes especializados:

**Core de Asistentes → memoria/contexto → motor de decisiones → automatización → canales → reporting**

Copiloto Comercial es el primer producto especializado de ese núcleo.

## MVP

El MVP no intenta resolver todo. Debe demostrar una sola cosa: que el sistema puede evitar oportunidades perdidas por falta de seguimiento y hacer visible el estado comercial sin que el responsable tenga que perseguir manualmente cada caso.
