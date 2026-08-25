# Asignación de oportunidades v1

**Estado:** MVP / regla operativa inicial

## Regla de asignación

La asignación se realiza en este orden:

1. **Responsable explícito:** si el canal o la empresa informa un `owner_id` válido, se conserva.
2. **Regla del cliente:** si el cliente tiene una regla de asignación configurada, se aplica esa regla.
3. **Round robin:** para el MVP, cuando existen varios vendedores habilitados y no hay una regla específica, asignar de forma rotativa entre vendedores elegibles.
4. **Un solo vendedor:** si solo existe un vendedor elegible, asignarlo directamente.
5. **Sin vendedor elegible:** mantener `owner_id = null` y generar una anomalía/alerta para intervención humana. No inventar un responsable.

## Elegibilidad

Un vendedor es elegible si está activo, habilitado para recibir oportunidades y pertenece al equipo configurado para ese cliente.

En MVP no se utilizarán atributos sensibles del contacto para decidir asignación.

## Reasignación

No reasignar automáticamente una oportunidad que ya tiene responsable, salvo que exista una regla explícita de reasignación o intervención humana.

Una oportunidad reabierta después de `closed_lost` debe seguir las reglas de asignación vigentes y conservar su historial.

## Auditoría

Cada asignación o reasignación debe poder registrarse como evento con:

- oportunidad;
- responsable anterior;
- nuevo responsable;
- motivo/regla aplicada;
- fecha/hora;
- origen de la decisión.

## Evolución posterior

Cuando tengamos datos suficientes, podremos evaluar reglas por territorio, producto, carga de trabajo, horario u otras variables comerciales. Esas reglas no forman parte del MVP hasta que exista una necesidad demostrada.
