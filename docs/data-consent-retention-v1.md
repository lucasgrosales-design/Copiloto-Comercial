# Política de consentimiento y retención de datos v1

**Estado:** Diseño previo a datos reales

> Este documento define requisitos de producto/arquitectura. No sustituye asesoramiento jurídico local para cada país o cliente.

## Objetivo

Definir un mínimo operativo antes de procesar datos reales de contactos de terceros mediante Copiloto Comercial.

## Principios

1. Recopilar solamente los datos necesarios para la operación comercial.
2. Registrar el origen del contacto y del mensaje cuando esté disponible.
3. Respetar las preferencias y solicitudes de no contacto.
4. Mantener separación entre datos de clientes distintos.
5. No utilizar datos de contacto para fines distintos de los autorizados por el cliente y aplicables al canal.
6. No inferir ni almacenar categorías sensibles salvo necesidad legal y producto expresamente justificada.
7. Proteger credenciales, tokens y secretos fuera de los registros de negocio.

## Estado de consentimiento/preferencia

El modelo debe poder distinguir como mínimo:

- `unknown`: no tenemos una preferencia registrada;
- `contact_allowed`: contacto permitido según la configuración y base aplicable;
- `do_not_contact`: no enviar comunicaciones comerciales;
- `restricted`: requiere revisión humana o regla específica.

`do_not_contact` debe detener automáticamente los seguimientos salientes.

## Retención

Para el MVP no se fija todavía un período legal universal, porque depende del país, del cliente, del propósito y de las obligaciones aplicables.

Sí se fija una regla de producto: **no conservar datos indefinidamente por defecto**.

La implementación comercial deberá definir por cliente:

- período de retención de contactos;
- período de retención de conversaciones/eventos;
- criterios de eliminación o anonimización;
- quién puede solicitar eliminación;
- cómo se audita la eliminación.

Hasta definir estos parámetros, los datos reales deben utilizarse en el mínimo entorno necesario y con acceso restringido.

## Acceso y aislamiento

- Cada cliente debe tener separación lógica de sus contactos y oportunidades.
- El personal solo debe acceder a los datos necesarios para su función.
- Los secretos de canales y proveedores no deben almacenarse en campos de negocio.
- Los logs técnicos no deben reproducir innecesariamente el contenido completo de conversaciones.

## Antes de producción

No se considera listo para operar con datos reales de terceros hasta contar con:

1. configuración de consentimiento/preferencias;
2. política de retención por cliente/entorno;
3. mecanismo de no contacto;
4. aislamiento de datos por cliente;
5. control de acceso;
6. revisión legal de los países objetivo cuando corresponda.
