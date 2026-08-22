# Prueba simple del MVP en n8n

Este flujo permite probar Copiloto Comercial sin URLs, WhatsApp ni herramientas externas.

## Cómo usarlo

1. En n8n, elegí **Import from File**.
2. Seleccioná `n8n/copiloto-prueba-simple-mvp.json`.
3. Abrí el bloque del medio, llamado **Escribí el mensaje de prueba acá**.
4. Cambiá únicamente el texto que aparece junto a `text`. Por ejemplo: `Quiero una cotización`.
5. Hacé clic en **Test workflow** o **Execute workflow**.
6. Abrí el último bloque, **Crear oportunidad de prueba**, para ver el resultado.

## Qué significa el resultado

Si ves `Consulta recibida correctamente`, el MVP procesó el mensaje y creó una oportunidad de prueba en etapa `new`.

Nada se envía a WhatsApp y nada queda guardado todavía. Es una prueba segura para entender el flujo antes de conectar servicios reales.
