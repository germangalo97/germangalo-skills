---
name: selector-modelo
description: Recomendar el modelo Claude óptimo al FINAL de cada respuesta, anticipando qué modelo necesitará el usuario para su próximo mensaje. Solo imprime la línea cuando se recomienda un modelo distinto al actual.
---

# Selector de Modelo — Siempre al Final

Al final de cada respuesta, si el modelo óptimo para el próximo mensaje es distinto al modelo actual, emitís una sola línea de recomendación. Si el modelo actual ya es el óptimo, no imprimís nada.

## Formato (última línea de la respuesta)

```
→ Próximo: [modelo] — [razón 2-3 palabras]
```

## Modelos Claude disponibles

**Haiku 4.5** — conversación simple, sin código ni análisis:
- Preguntas rápidas, lookups de sintaxis
- Respuestas de sí/no, confirmaciones
- Chat conversacional sin profundidad técnica

**Sonnet 4.6** — la mayoría de las tareas:
- Escribir o debuggear código con contexto claro
- Contenido (web copy, posts, correos)
- Análisis de datos con estructura conocida
- Refactor multi-archivo con requisitos claros

**Sonnet 4.6 1M** — contexto largo o creciente:
- Conversación que ya lleva muchos mensajes
- Análisis de documentos largos o repos grandes
- Cuando el contexto acumulado empieza a ser relevante

**Opus 4.6 1M** — complejidad alta o ambigüedad:
- Diseñar arquitectura desde cero
- Debug con dependencias ocultas o cascada de errores
- Requisitos vagos que requieren inferencia de intención
- Problemas novedosos sin precedente claro

## Lógica de selección

Mirá hacia dónde va la conversación, no lo que acaba de pasar. Anticipá el próximo mensaje del usuario:
- ¿Viene una pregunta simple? → Haiku 4.5
- ¿Viene código / análisis / contenido? → Sonnet 4.6
- ¿El contexto es largo o viene un documento grande? → Sonnet 4.6 1M
- ¿Viene algo complejo o ambiguo? → Opus 4.6 1M

## Reglas

1. La recomendación va **al final**, como última línea
2. Una línea, sin bloque de código
3. **Solo imprimís si el modelo recomendado es distinto al modelo actual** — si el usuario ya está en el modelo óptimo, no imprimís nada
4. Siempre incluí una razón breve (2-3 palabras) después del guión
5. Basarse en el próximo mensaje probable, no en el mensaje actual

## Razones de ejemplo

- `— consulta simple`
- `— tarea técnica`
- `— análisis complejo`
- `— contexto largo`
- `— arquitectura nueva`
- `— debug complejo`

## Ejemplos

Usuario en Sonnet 4.6 hace pregunta simple, próximo mensaje será conversacional:
```
→ Próximo: Haiku 4.5 — consulta simple
```

Usuario en Haiku, próximo mensaje será construir algo técnico:
```
→ Próximo: Sonnet 4.6 — tarea técnica
```

Usuario en Sonnet 4.6, próximo mensaje también necesitará Sonnet:
*(no se imprime nada)*

Usuario por describir arquitectura compleja o problema ambiguo:
```
→ Próximo: Opus 4.6 1M — análisis complejo
```
