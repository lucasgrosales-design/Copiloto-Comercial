# Memoria Comercial v1

## Objetivo

Convertir la conversación en una ficha viva de oportunidad. La memoria debe servir para tomar mejores decisiones futuras, no para almacenar texto sin propósito.

## Capas de memoria

### Identidad

Información relativamente estable:
- nombre;
- empresa;
- cargo;
- canales autorizados;
- datos de contacto.

### Contexto comercial

- necesidad;
- problema;
- objetivo;
- solución de interés;
- presupuesto si fue expresado;
- urgencia;
- decisor e involucrados.

### Historial

- últimos contactos;
- resumen de conversaciones;
- propuestas enviadas;
- preguntas relevantes;
- objeciones;
- compromisos;
- decisiones.

### Estado operativo

- etapa;
- score orientativo;
- intención detectada;
- próximo paso;
- fecha del próximo paso;
- responsable;
- motivo de escalamiento;
- motivo de pérdida o pausa.

## Memoria derivada

La IA puede generar hechos estructurados a partir de una conversación, pero cada hecho debe conservar:

- `source_event_id`;
- `created_at`;
- `confidence`;
- `last_confirmed_at`.

Esto evita tratar una inferencia antigua como un hecho permanente.

## Regla de actualización

Una conversación nueva puede:

- agregar información;
- confirmar información existente;
- corregir información anterior;
- invalidar información anterior.

La información más reciente y explícita prevalece sobre una inferencia anterior.

## Resumen vivo

Cada oportunidad debe mantener un resumen corto y actualizado, por ejemplo:

> Empresa B2B. Busca mejorar el seguimiento de consultas recibidas por WhatsApp y web. El dueño gestiona actualmente las oportunidades. Mostró interés y recibió propuesta. Objeción actual: necesita entender implementación. Próximo paso: explicar funcionamiento y resolver dudas.

Este resumen es el contexto principal que consume el asistente antes de intervenir.

## Privacidad y minimización

Guardar únicamente información necesaria para la operación comercial. No almacenar información sensible que no sea necesaria para el servicio. Respetar solicitudes de eliminación y no contacto.

## Uso por el motor

La memoria alimenta:

1. interpretación de nuevas respuestas;
2. personalización del mensaje;
3. elección de la cadencia;
4. detección de oportunidades bloqueadas;
5. alertas al responsable;
6. reportes de evolución.
