# Resolución de Identidad Comercial v1

## Objetivo

Reconocer que una misma persona/empresa puede aparecer por distintos canales y evitar duplicar oportunidades.

## Identificadores

Prioridad de coincidencia:

1. identificador interno ya conocido;
2. email exacto normalizado;
3. teléfono normalizado en formato internacional;
4. identificador estable entregado por el canal;
5. combinación empresa + nombre + dominio;
6. coincidencia difusa solo como candidata, nunca como fusión automática.

## Regla crítica

Una coincidencia difusa no debe fusionar contactos automáticamente. Si existe ambigüedad, el sistema conserva entidades separadas y marca `identity_review_required=true`.

## Contacto unificado

Un contacto puede tener múltiples identidades de canal:

- WhatsApp ID;
- email;
- Instagram ID;
- Facebook ID;
- LinkedIn ID;
- webchat ID.

Todas apuntan al mismo `contact_id` cuando la identidad está confirmada.

## Oportunidad

La oportunidad comercial pertenece al contacto/empresa, no al canal.

Esto permite:

WhatsApp → oportunidad 123
Email → oportunidad 123
Instagram → oportunidad 123

## Historial

Cada evento conserva su canal original. La unificación no elimina el historial de ningún canal.

## Reglas de seguridad operativa

- Nunca enviar un mensaje a un canal distinto del autorizado solo porque se encontró una coincidencia.
- Respetar preferencias y solicitudes de no contacto.
- No inferir identidad únicamente por nombre.
- Registrar el motivo de cada fusión o vinculación.
- Las fusiones dudosas requieren revisión humana.
