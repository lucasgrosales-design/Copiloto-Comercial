# Orquestación del Sistema v1

## Flujo unificado

El sistema integra recepción, memoria, inteligencia, pipeline, seguimiento y monitoreo en un ciclo continuo.

```text
Entrada de prospecto/mensaje
        ↓
Normalización
        ↓
Recuperar memoria de oportunidad
        ↓
Interpretar mensaje + contexto
        ↓
Actualizar memoria
        ↓
Actualizar pipeline
        ↓
Evaluar reglas comerciales
        ↓
┌──────────────┬───────────────┬───────────────┐
│ Responder    │ Seguimiento   │ Humano        │
│              │ programado    │ requerido     │
└──────┬───────┴───────┬───────┴───────┬───────┘
       ↓                ↓               ↓
   Registrar        Registrar        Alertar
       └───────────────┴───────────────┘
                       ↓
                 Nueva evaluación
```

## Contrato entre módulos

Cada módulo recibe y devuelve un objeto de oportunidad normalizado. La oportunidad es el hilo conductor; los mensajes son eventos que modifican su estado.

### Eventos principales

- `prospect_created`
- `message_received`
- `message_sent`
- `response_classified`
- `memory_updated`
- `stage_changed`
- `follow_up_due`
- `follow_up_ready`
- `human_required`
- `proposal_sent`
- `won`
- `lost`
- `nurture_scheduled`

## Regla de idempotencia

Un mismo evento no debe generar dos seguimientos ni dos alertas. Cada evento debe tener un identificador único.

## Orden de prioridad

1. solicitudes de no contacto;
2. seguridad y límites de información;
3. intervención humana requerida;
4. señal de compra;
5. respuesta a pregunta/objeción;
6. seguimiento pendiente;
7. nutrición/reactivación;
8. reportes.

## Qué falta para producción

La lógica está definida, pero todavía faltan decisiones de infraestructura que no conviene inventar:

- proveedor de WhatsApp;
- almacenamiento persistente;
- proveedor/modelo de IA;
- autenticación;
- mecanismo de ejecución programada;
- política de consentimiento y tratamiento de datos;
- credenciales de los servicios.

El MVP puede seguir desarrollándose sin esas integraciones usando eventos y payloads simulados.
