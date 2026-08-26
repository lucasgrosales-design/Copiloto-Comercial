# Auditoría de integración MVP — Copiloto Comercial

**Fecha:** 2026-08-26
**Estado:** Vigente
**Objetivo:** determinar qué existe realmente, qué es demostración y qué falta para conectar el núcleo comercial con WhatsApp y producir comportamiento comercial real.

## 1. Diagnóstico ejecutivo

El repositorio tiene una base conceptual y de arquitectura sólida, pero los workflows de n8n todavía están separados en piezas de prueba. El flujo canónico de ingreso de prospectos resuelve validación, identidad, oportunidad e idempotencia básica, pero no conecta todavía el motor de inteligencia comercial ni la generación de respuesta contextual.

Por lo tanto, **no debe importarse como si ya fuera el MVP completo**. La prioridad es construir un único circuito ejecutable:

**Canal → Ingreso → Identidad → Oportunidad → Inteligencia comercial → Próxima acción → Respuesta → Persistencia → Seguimiento → Reanálisis.**

## 2. Auditoría de los tres workflows

### A. `copiloto-comercial-mvp-inteligencia-v1.json`

**Estado:** obsoleto / no utilizar como workflow principal.

Problemas:
- No contiene nodo de IA real.
- El nodo `Preparar análisis comercial` solamente construye un prompt.
- `Resultado MVP` devuelve campos vacíos o valores predeterminados.
- Declara que la IA se conectará después.

Conclusión: sirve como antecedente de diseño, no como base de ejecución.

### B. `copiloto-comercial-mvp-inteligencia-v2.json`

**Estado:** prototipo válido del motor de IA, pero no MVP.

Tiene:
- modelo OpenAI;
- cadena LLM;
- parser estructurado;
- análisis de intención, temperatura, etapa, interés, información faltante, próxima acción y respuesta sugerida.

Problemas:
- trabaja con mensaje fijo de prueba;
- no recibe el evento real del workflow canónico;
- no persiste la oportunidad;
- marca explícitamente `not_persisted`;
- no ejecuta envío real;
- todavía no incorpora la personalidad completa ni la capa avanzada de manejo de objeciones/cierre.

Conclusión: **es el embrión del cerebro comercial** y debe reutilizarse, no descartarse.

### C. `copiloto-ingreso-prospecto-mvp.json`

**Estado:** workflow canónico de entrada.

Resuelve:
- webhook;
- validación básica;
- canales permitidos;
- resolución de identidad;
- reutilización de oportunidad abierta;
- idempotencia básica;
- evento de ingreso;
- borrador de salida;
- respuesta HTTP.

Problemas críticos:
- no llama al motor de inteligencia comercial;
- no genera una respuesta contextual real;
- utiliza `$getWorkflowStaticData` como almacenamiento de prueba, no persistencia de producción;
- genera inicialmente un mensaje genérico de salida;
- no implementa todavía la cadencia ni el reanálisis posterior.

### 3. Inconsistencia detectada

El workflow de inteligencia usa `stage: 'nuevo'` en uno de sus resultados de prueba, mientras que el contrato formal de Opportunity utiliza `new`, `contacted`, `engaged`, etc.

**Acción:** normalizar todos los estados al contrato formal. No introducir valores libres.

## 4. Arquitectura objetivo

La implementación siguiente debe separar responsabilidades:

1. **Channel Adapter** — WhatsApp recibe/envía.
2. **Ingreso** — valida evento.
3. **Identity Resolver** — identifica contacto.
4. **Opportunity Manager** — crea o actualiza oportunidad.
5. **Commercial Intelligence** — interpreta conversación.
6. **Conversation Policy** — decide cómo debe comportarse Copiloto.
7. **Response Generator** — redacta la respuesta natural.
8. **Persistence** — guarda contacto, evento, oportunidad y mensajes.
9. **Follow-up Engine** — programa y recalcula seguimiento.
10. **Human Handoff** — deriva cuando corresponde.

## 5. Regla de personalidad

La personalidad debe ser una capa independiente de la lógica técnica.

Copiloto debe sonar como una persona real: natural, claro, cercano, atento y comercialmente competente. La conversación debe evitar respuestas de catálogo, interrogatorios, frases artificiales y presión innecesaria.

La lógica comercial debe conducir la conversación sin destruir esa naturalidad.

## 6. Nueva capa de metodología comercial

Se incorpora una capa conceptual de técnicas de venta y cierre asociadas a Alex Day, junto con los principios ya incorporados de venta consultiva y Jordan Belfort.

La metodología se utilizará como conocimiento y criterio de decisión, **no como colección de guiones rígidos**.

Principios a incorporar:
- descubrimiento antes de recomendación;
- escuchar y preguntar antes de argumentar;
- identificar la preocupación real detrás de una objeción;
- amortiguar/validar cuando corresponda;
- responder con información relevante;
- evaluar si la objeción quedó resuelta;
- cierres de prueba durante el proceso cuando exista señal suficiente;
- alternativas cuando realmente existan alternativas válidas;
- convertir una objeción en información para comprender mejor la decisión;
- pedir el siguiente paso de forma natural;
- utilizar el silencio después de una pregunta de cierre en canales donde tenga sentido;
- nunca manipular, inventar, presionar ni ocultar información relevante.

## 7. Principio diferencial del producto

Copiloto no debe definirse como “una IA que sabe vender”.

Su diferenciación debe ser:

**conocimiento comercial práctico + personalidad humana + memoria contextual + automatización.**

La experiencia comercial del fundador debe convertirse en reglas, criterios, ejemplos, evaluación y prompts reproducibles. El producto no debe depender de imitar literalmente a una persona.

## 8. Próxima implementación

Orden obligatorio:

1. Normalizar contratos y estados.
2. Integrar el workflow canónico con el motor de inteligencia v2.
3. Crear la capa de personalidad/conversación.
4. Crear la capa de objeciones y cierre.
5. Generar respuesta contextual.
6. Conectar persistencia real.
7. Conectar WhatsApp.
8. Probar extremo a extremo.
9. Implementar cadencia y reanálisis.
10. Medir conversión y errores.

**Criterio de avance:** no agregar canales ni funcionalidades nuevas hasta que WhatsApp pueda completar el circuito comercial principal de punta a punta.
