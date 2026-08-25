# Estado del proyecto — Copiloto Comercial

**Fecha:** 2026-08-25  
**Fase:** Integración y validación del MVP  
**Estado general:** Construcción activa — núcleo definido, integración real pendiente.

## Diagnóstico ejecutivo

Copiloto Comercial **todavía no es un MVP funcional completo**, pero dejó atrás la etapa de definición conceptual y arquitectura inicial.

El núcleo de ingreso de prospectos ya está formalizado en un workflow canónico de n8n y existen contratos para las entidades principales, reglas de identidad, idempotencia, pipeline, cadencia y asignación. El siguiente trabajo crítico es conectar esos componentes para producir comportamiento comercial real y probarlo sobre los canales propios.

## Lo que ya está resuelto

- Propuesta de valor centrada en gestionar consultas y oportunidades para convertir más prospectos en clientes.
- Arquitectura base y separación entre núcleo comercial y adaptadores de canal.
- Workflow canónico de ingreso de prospecto en `n8n/copiloto-ingreso-prospecto-mvp.json`.
- Validación de entrada e identidad multicanal.
- Reutilización de oportunidad abierta.
- Idempotencia básica de mensajes entrantes.
- Contratos formales para Contact, InboundMessage, Opportunity y OutboundMessage.
- Pipeline comercial definido.
- Política inicial de cadencia de seguimiento.
- Regla inicial de asignación de responsables.
- Política de consentimiento/retención definida como requisito previo a producción con datos reales a escala.
- Alcance de canales propios del MVP de prueba fijado en WhatsApp, Email e Instagram.
- Estrategia comercial propia y plan de contenido documentados.
- Registro de decisiones comerciales y criterio de fuente única de verdad.

## Lo que todavía NO está resuelto

### Crítico para declarar MVP funcional

1. Conectar el ingreso real de WhatsApp al webhook y validar el circuito extremo a extremo.
2. Conectar la inteligencia comercial al ingreso: análisis de intención, temperatura, etapa, información faltante y próxima acción.
3. Persistir la oportunidad y sus eventos en almacenamiento real.
4. Implementar la planificación de seguimiento de acuerdo con la cadencia definida.
5. Implementar el envío real de mensajes mediante el adaptador de canal, inicialmente con control/autorización adecuada.
6. Detener y recalcular la cadencia cuando llega una nueva respuesta.
7. Probar idempotencia y recuperación ante errores con mensajes reales.

### Necesario para salida comercial inicial

- WhatsApp funcionando de extremo a extremo.
- Email funcionando.
- Instagram conectado al núcleo comercial según el alcance definido.
- Persistencia multi-cliente y aislamiento de datos.
- Consentimiento, retención y controles de no contacto implementados.
- Handoff humano operativo.
- Métricas mínimas de oportunidades, seguimientos, respuestas, demos y conversiones.
- Prueba interna usando a Copiloto como su propio caso comercial.
- Oferta comercial y proceso de onboarding suficientemente claros para los primeros clientes.

## Criterio de MVP funcional

No se considerará MVP funcional por tener workflows importables o por demostrar solamente la recepción de un webhook.

El MVP funcional se alcanza cuando una consulta real puede recorrer, como mínimo:

**Canal → Ingreso → Identidad → Oportunidad → Análisis IA → Próxima acción → Seguimiento → Respuesta → Reanálisis**, con registro persistente y sin duplicaciones.

## Criterio de versión comercializable

La primera versión comercializable se alcanza cuando ese circuito puede ejecutarse de forma segura para un cliente real, con canales definidos, persistencia, controles de consentimiento/no contacto, intervención humana, métricas y un proceso de onboarding repetible.

## Próxima sesión en computadora

Orden de trabajo recomendado:

1. Abrir n8n Cloud y verificar/importar el workflow canónico.
2. Configurar WhatsApp como primer canal real.
3. Probar un mensaje real y comprobar ingreso → identidad → oportunidad.
4. Conectar el nodo de inteligencia comercial.
5. Incorporar persistencia real.
6. Implementar la primera versión de la cadencia.
7. Probar el circuito completo con casos controlados.

**Regla:** no ampliar funcionalidades mientras el circuito principal no funcione de extremo a extremo.

## Lectura temporal del proyecto

El proyecto se encuentra aproximadamente en la transición entre **Fase 1 — Core definido** y **Fase 2 — Integración real**. El objetivo inmediato no es agregar más documentación ni más funcionalidades, sino convertir la arquitectura ya definida en un circuito comercial ejecutable y medible.
