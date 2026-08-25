# Política de cadencia de seguimiento v1

**Estado:** MVP / hipótesis operativa inicial

## Objetivo

Evitar que una oportunidad activa quede sin próxima acción, sin convertir el seguimiento en contacto excesivo o automático sin criterio.

## Cadencia por defecto

Salvo que la empresa configure una cadencia distinta y siempre respetando las preferencias del contacto y las reglas del canal:

| Momento | Acción |
|---|---|
| Inmediato | Respuesta inicial o confirmación de recepción cuando corresponda. |
| +1 día | Primer seguimiento si no hubo respuesta y la oportunidad sigue activa. |
| +3 días | Segundo seguimiento si no hubo respuesta. |
| +7 días | Tercer seguimiento con una propuesta clara de próximo paso. |
| +14 días | Último seguimiento de la secuencia activa. |
| +30 días o posterior | Pasar a `nurture` y utilizar una cadencia separada, si existe autorización y sentido comercial. |

Estos intervalos son **defaults de MVP**, no reglas universales. Deben poder configurarse por cliente/rubro en una etapa posterior.

## Reglas de seguridad comercial

1. No enviar seguimiento si el contacto pidió no ser contactado.
2. No enviar seguimiento si existe una respuesta pendiente de análisis o una intervención humana en curso.
3. No duplicar un seguimiento por reintentos técnicos: cada envío debe tener una `idempotency_key`.
4. Si el prospecto responde, la cadencia automática se detiene y la conversación vuelve a análisis comercial.
5. Si el prospecto expresa una intención negativa clara, la oportunidad no continúa automáticamente.
6. Si aparece una contradicción, una decisión económica/contractual o una situación sensible, requerir intervención humana.
7. No avanzar una oportunidad de etapa solamente porque transcurrió el tiempo.

## Estados al finalizar la secuencia

Si después del último seguimiento no hay respuesta:

- mantener el historial completo;
- registrar el último intento;
- mover a `nurture` cuando corresponda;
- dejar una condición/fecha de próxima revisión;
- no continuar enviando mensajes indefinidamente.

## Métricas

Registrar al menos:

- seguimientos programados;
- seguimientos enviados;
- respuestas obtenidas;
- oportunidades recuperadas;
- reuniones/demos generadas;
- conversiones;
- bajas o solicitudes de no contacto.

La cadencia debe optimizar **oportunidades recuperadas y conversiones**, no cantidad de mensajes enviados.
