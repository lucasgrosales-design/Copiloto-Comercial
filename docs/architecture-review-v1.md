# Revisión de Arquitectura v1

## Componentes definidos

- Core conversacional heredado de Mi Asesor.
- Memoria comercial.
- Resolución de identidad multicanal.
- Event log.
- Motor de interpretación.
- Motor de seguimiento.
- Pipeline.
- Human handoff.
- Métricas y reportes.
- Adaptadores multicanal.
- Orquestación n8n.

## Dependencias externas aún necesarias

1. Runtime n8n accesible.
2. Persistencia real.
3. Proveedor de modelo IA y credenciales.
4. Canal WhatsApp y credenciales.
5. Email y credenciales.
6. Autenticación/usuarios para el panel o canal de administración.
7. Políticas de consentimiento y retención de datos definidas para el mercado objetivo.

## Riesgos detectados

- Duplicación de oportunidades por identidad multicanal.
- Seguimientos duplicados si no se aplica idempotencia.
- Automatización excesiva ante señales ambiguas.
- Dependencia del proveedor de IA.
- Falta de información autorizada para responder preguntas comerciales.
- Falta de persistencia transaccional.

## Decisión de MVP

No bloquear el desarrollo por integraciones. Mantener contratos y datos simulados hasta que sea necesario conectar servicios reales.

## Próximo punto de intervención humana

Para ejecutar el sistema real necesitamos elegir/configurar infraestructura y credenciales. Hasta entonces se puede continuar con contratos, reglas, fixtures, prompts y workflows simulados.
