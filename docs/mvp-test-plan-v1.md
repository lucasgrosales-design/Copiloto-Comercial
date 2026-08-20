# Plan de Prueba MVP v1

## Objetivo

Validar el comportamiento del sistema antes de conectar canales externos.

## Escenarios mínimos

1. Presupuesto sin respuesta → seguimiento contextual.
2. Señal explícita de compra → alerta humana.
3. Objeción de precio → no negociar automáticamente; escalar.
4. Prospecto que pide retomar más adelante → nurture programado.
5. Negativa → cerrar y detener seguimiento.
6. Pregunta normal → responder si existe información autorizada.
7. Mensaje ambiguo → pedir aclaración o escalar.
8. Oportunidad activa sin próximo paso → alerta de anomalía.

## Criterios de aceptación

- cada evento tiene identificador único;
- no se duplican acciones ante eventos repetidos;
- cada oportunidad activa termina con un próximo paso o estado de espera explícito;
- el asistente no inventa información comercial;
- las objeciones sensibles llegan a humano;
- las negativas detienen el seguimiento;
- la memoria se actualiza después de cada evento relevante;
- el reporte identifica excepciones en vez de limitarse a mostrar métricas.

## Orden de implementación

1. Ejecutar escenarios con payloads simulados.
2. Corregir reglas.
3. Agregar persistencia real.
4. Agregar modelo de IA.
5. Agregar WhatsApp.
6. Probar con conversaciones internas.
7. Probar con primeros prospectos reales bajo supervisión.

## Resultado esperado

Un ciclo comercial reproducible que pueda demostrarse en una reunión: crear oportunidad → simular conversación → observar actualización de memoria/pipeline → ver decisión → ver seguimiento o alerta.
