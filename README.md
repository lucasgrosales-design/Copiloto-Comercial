# Copiloto Comercial

Sistema de asistencia comercial orientado a seguimiento, gestión y conversión de oportunidades de venta.

## Estado

Proyecto en fase de construcción del MVP.

## Objetivo

Evitar que oportunidades comerciales se pierdan por falta de seguimiento y proporcionar al responsable comercial información clara sobre el estado de cada oportunidad.

## Principios

- Seguimiento automático y contextual.
- Comunicación natural con prospectos y clientes.
- Registro de cada interacción.
- Priorización de oportunidades.
- Reportes accionables.
- Intervención humana cuando el contexto lo requiere.
- Arquitectura reutilizable para futuros asistentes especializados.
- No automatizar acciones comerciales irreversibles sin evidencia suficiente.
- Mantener una fuente única de verdad para cada decisión o contrato.

## Primer producto

**Copiloto Comercial** será el primer asistente especializado construido sobre un núcleo común de asistentes inteligentes.

## MVP inicial

1. Recepción y registro de prospectos.
2. Contacto inicial controlado.
3. Planificación de seguimiento.
4. Detección y clasificación de respuestas.
5. Seguimiento contextual.
6. Escalamiento al responsable cuando corresponde.
7. Reporte del estado de las oportunidades.

## Canales propios del MVP de prueba

- WhatsApp
- Email
- Instagram

Los tres forman parte del alcance del modelo de prueba. La implementación técnica puede ser progresiva, manteniendo el núcleo comercial independiente de los adaptadores de canal.

## Estructura real del repositorio

- `docs/` — visión, procesos, especificaciones y contratos operativos.
- `n8n/` — workflows importables; el workflow de ingreso canónico es `n8n/copiloto-ingreso-prospecto-mvp.json`.
- `comercial/` — estrategia, decisiones, contenido, modelo comercial y precios.
- `data/` — schemas y estructuras de datos.

Las credenciales, secretos y configuraciones específicas de cada entorno no deben almacenarse en el repositorio.
