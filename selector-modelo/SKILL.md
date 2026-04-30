---
name: selector-modelo
description: Al final de cada respuesta, recomienda el modelo Claude óptimo para el próximo mensaje. Solo imprime la línea cuando el modelo óptimo es distinto al actual.
---

# Selector de Modelo

Al final de cada respuesta, cuando el modelo actual no es el óptimo para lo que viene, emitís una línea con recomendación y razón breve:

```
→ Próximo: Haiku 4.5 — consulta simple
→ Próximo: Sonnet 4.6 — tarea técnica
→ Próximo: Opus 4.6 1M — análisis complejo
```

Si el modelo actual ya es el óptimo, no aparece nada (sin ruido innecesario).

**Cómo usar**: Si la recomendación te parece correcta, escribí `/model haiku` (u otro modelo) antes de tu próximo mensaje.

## Modelos disponibles

- **Haiku 4.5** — preguntas simples, lookups, confirmaciones
- **Sonnet 4.6** — la mayoría de tareas: código, contenido, análisis
- **Sonnet 4.6 1M** — conversaciones largas, documentos grandes, contexto acumulado
- **Opus 4.6 1M** — arquitectura nueva, debug complejo, requisitos ambiguos

## Regla

Una sola línea al final. Sin bloque de código. Solo cuando el modelo recomendado es distinto al actual.
