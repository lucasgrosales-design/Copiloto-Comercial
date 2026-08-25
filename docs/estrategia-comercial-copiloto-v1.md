# Estrategia comercial — Copiloto Comercial v1

**Fecha:** 2026-08-24  
**Estado:** En elaboración  
**Propósito:** definir el sistema comercial mínimo viable y utilizar la propia comercialización de Copiloto como laboratorio.

## 1. Objetivo

Construir un sistema comercial simple, medible y replicable capaz de generar conversaciones, administrar oportunidades y ejecutar seguimiento sin perder el control humano sobre las decisiones comerciales relevantes.

El primer caso real será la comercialización del propio Copiloto Comercial.

## 2. Qué vendemos

Copiloto no se posiciona como chatbot, bot o colección de funcionalidades técnicas. La propuesta de valor es ayudar a una empresa a gestionar mejor sus consultas y oportunidades para convertir una mayor proporción en clientes, reduciendo oportunidades perdidas y mejorando el seguimiento.

La tecnología es el medio; el resultado comercial es lo que comunicamos.

## 3. Canales iniciales

Los canales propios iniciales son:

- WhatsApp.
- Email.
- Instagram.

No se amplía el universo de canales hasta validar el sistema básico.

## 4. Flujo comercial MVP

**Canal → evento → contacto → oportunidad → análisis → próxima acción → seguimiento → resultado.**

El sistema debe cubrir progresivamente:

1. Captación de prospectos.
2. Ingreso y validación de mensajes.
3. Resolución de identidad.
4. Creación o reutilización de oportunidades.
5. Clasificación de intención y situación comercial.
6. Determinación de próxima acción.
7. Seguimiento.
8. Escalamiento a humano cuando corresponda.
9. Registro de resultados.
10. Medición y aprendizaje.

## 5. Regla de automatización

Copiloto no debe responder automáticamente por el simple hecho de recibir un mensaje.

El ingreso crea contexto y oportunidad. El motor comercial debe analizar la conversación y determinar la acción. Los mensajes generados durante la etapa MVP pueden mantenerse como borradores hasta conectar y validar el canal de salida.

Esto evita automatizar respuestas genéricas antes de disponer del criterio comercial del producto.

## 6. Arquitectura de datos y workflow

Los eventos se normalizan mediante `data/event-schema-v1.json`.

El workflow inicial de ingreso se conserva en `n8n/copiloto-ingreso-prospecto-mvp-v3.json`.

El workflow implementa en esta etapa:

- validación de canal y campos mínimos;
- idempotencia básica por canal + ID externo del mensaje;
- resolución de identidad;
- creación o reutilización de oportunidad abierta;
- generación del evento `message_received`;
- creación de un borrador de salida sin envío automático.

La persistencia actual mediante static data de n8n es temporal. Debe reemplazarse por persistencia real antes de considerar el flujo listo para producción.

## 7. Laboratorio comercial propio

La propia comercialización de Copiloto debe utilizarse para validar:

- qué problemas generan más interés;
- qué mensajes generan respuesta;
- qué contenido genera conversaciones calificadas;
- qué objeciones aparecen;
- qué seguimiento convierte;
- cuánto tiempo requiere una oportunidad;
- qué parte del proceso conviene automatizar.

Los aprendizajes deben convertirse en decisiones registradas en `comercial/DECISIONES.md`.

## 8. Contenido

El objetivo comercial es construir un banco inicial de 100 piezas, pero la producción comienza con un **lote piloto de 10 contenidos**.

El formato principal bajo hipótesis es Reel/video corto vertical.

Cada pieza debe tener:

- problema específico;
- público específico;
- hook;
- mensaje central;
- CTA;
- métrica objetivo.

No se escala producción hasta medir el lote piloto.

## 9. Métrica principal

El alcance es una métrica secundaria. La métrica comercial prioritaria es la generación de **conversaciones comerciales calificadas**, seguida por demos, oportunidades y clientes originados.

## 10. Gobierno de la estrategia

`comercial/DECISIONES.md` funciona como índice maestro de decisiones comerciales.

Los documentos específicos contienen el detalle operativo. No deben coexistir documentos duplicados que compitan como fuente de verdad sobre la misma decisión.

Las hipótesis deben permanecer identificadas como tales hasta que exista evidencia o aprobación suficiente para convertirlas en decisiones.

## 11. Prioridad del MVP

**Primero producto funcional; después optimización comercial y de contenido.**

El núcleo del MVP es:

**ingreso de prospecto → identificación → análisis → oportunidad → siguiente acción → respuesta/seguimiento controlado → registro.**

Todo lo que no contribuya directamente a completar y validar este circuito queda fuera del núcleo del MVP.

## 12. Secuencia de validación

**Producto funcional → canales propios → 10 contenidos piloto → conversaciones → análisis comercial → seguimiento → medición → aprendizaje → ajuste → escala.**
