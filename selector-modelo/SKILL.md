---
name: selector-modelo
description: Al final de cada respuesta, recomienda el modelo de Claude que conviene para el próximo mensaje (Haiku, Sonnet, Opus, Opus Plan o Fable) y el comando para cambiarlo. Solo escribe la línea cuando conviene cambiar de modelo.
---

# Selector de modelo

Al final de cada respuesta, piensa qué va a necesitar el próximo mensaje del usuario. Si conviene un modelo distinto
del que está usando ahora, agrega una sola línea con el modelo, el comando para cambiarlo y una razón corta:

→ Próximo: Sonnet (/model sonnet) — tarea de código

Si el modelo actual ya es el adecuado, no escribas nada.

## Qué modelo para qué

Modelos de Claude Code con una suscripción de Claude, a noviembre de 2026. Cada nombre corto apunta siempre a la
última versión de ese modelo.

- **Haiku** (`/model haiku`, hoy Haiku 5.5): preguntas rápidas, confirmaciones, buscar cómo se escribe algo,
  conversación sin código.
- **Sonnet** (`/model sonnet`, hoy Sonnet 5.5): la mayoría de las tareas. Escribir o corregir código con un pedido
  claro, automatizaciones, contenido, análisis de datos con una estructura conocida, cambios en varios archivos con
  requisitos claros.
- **Opus** (`/model opus`, hoy Opus 5.5): lo complejo o ambiguo. Diseñar algo desde cero, errores con causas
  escondidas, pedidos vagos donde hay que adivinar qué se quiere, problemas sin un camino conocido.
- **Opus Plan** (`/model opusplan`): Opus planifica en el modo plan y Sonnet ejecuta. Para trabajos grandes que
  conviene planificar bien y después hacer sin gastar Opus en cada paso.
- **Fable** (`/model fable`, hoy Fable 5.1): las tareas más difíciles y largas. Según el plan, puede cobrarse con
  créditos de uso en lugar de los límites de la suscripción (el menú de `/model` lo avisa con «Requires usage
  credits»). Recomiéndalo solo para algo excepcional y avisa que puede costar créditos.

## Cómo decidir

Mira hacia dónde va la conversación, no lo que acaba de pasar:

- ¿Viene una pregunta simple? → Haiku
- ¿Viene código, una automatización o contenido con un pedido claro? → Sonnet
- ¿Viene algo complejo, ambiguo o un sistema nuevo? → Opus
- ¿Viene un trabajo grande que conviene planificar antes de hacerlo? → Opus Plan
- ¿Viene algo excepcionalmente difícil y largo, y el usuario puede usar Fable? → Fable

Que la conversación sea larga no es motivo para cambiar de modelo: en Claude Code, Haiku 5.5, Sonnet 5.5, Opus 5.5
y Fable 5.1 ya trabajan con un millón de tokens de contexto.

## Reglas

1. Una sola línea, al final de la respuesta, sin bloque de código.
2. Solo cuando el modelo recomendado es distinto del actual.
3. Con el comando `/model` y una razón de 2 a 4 palabras después del guion.
4. Basada en el próximo mensaje probable, no en el actual.

## Ejemplos

En Opus, el usuario hizo una pregunta simple y lo que sigue es conversación:

→ Próximo: Haiku (/model haiku) — consulta simple

En Haiku, lo que sigue es armar una automatización:

→ Próximo: Sonnet (/model sonnet) — automatización

En Sonnet, lo que sigue es diseñar un sistema desde cero sin requisitos claros:

→ Próximo: Opus (/model opus) — sistema nuevo

En Sonnet, lo que sigue también es para Sonnet: no se escribe nada.

---

Hecha por Germán Galo. Más sobre Claude Code en youtube.com/@germangaloia.
