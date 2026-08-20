# Pruebas del MVP

El archivo `fixtures/e2e-test-input.json` contiene un evento de extremo a extremo para probar el orquestador.

## Prueba manual en n8n

1. Importar `n8n/orchestrator-v1.json`.
2. Ejecutar el workflow en modo manual.
3. Sustituir el payload de prueba por `tests/fixtures/e2e-test-input.json`.
4. Verificar que un mensaje con intención de compra termine en una ruta de intervención humana.
5. Verificar que el evento quede registrado y que no se generen acciones duplicadas si se procesa nuevamente el mismo `event_id`.

## Nota

La validación real depende de ejecutar n8n. GitHub contiene la definición y los fixtures, pero no es el runtime del sistema.
