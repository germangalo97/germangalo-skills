# germangalo-skills

3 configuraciones de optimización de tokens para Claude Code. Las mismas que usa @germangalo.ia.

## Skills

| Skill | Qué hace |
|-------|----------|
| `selector-modelo` | Recomienda el modelo óptimo al final de cada respuesta |
| `ultra-conciso` | Elimina relleno verbal sin recortar outputs técnicos |
| `eficiencia-herramientas` | Prioriza Grep/Glob/Read sobre Bash, limita output en búsquedas |

---

## Opción 1 — Instalar con npx (recomendado)

```bash
npx skills add germangalo97/germangalo-skills@selector-modelo -g -y
npx skills add germangalo97/germangalo-skills@ultra-conciso -g -y
npx skills add germangalo97/germangalo-skills@eficiencia-herramientas -g -y
```

Una vez instaladas, activarlas en cualquier conversación con:
```
/selector-modelo
/ultra-conciso
/eficiencia-herramientas
```

Para que estén **siempre activas** (sin tener que invocarlas cada vez), seguí la Opción 2.

---

## Opción 2 — Pegar en tu CLAUDE.md (siempre activo)

Abrí o creá el archivo `CLAUDE.md` en la raíz de tu proyecto (o en `~/.claude/CLAUDE.md` para que aplique globalmente) y pegá esto:

```md
## Skills siempre activos

### selector-modelo
Al final de cada respuesta, cuando el modelo actual no es el óptimo para lo que viene, emitís una línea con recomendación y razón breve:
→ Próximo: Haiku 4.5 — consulta simple
→ Próximo: Sonnet 4.6 — tarea técnica
→ Próximo: Opus 4.6 1M — análisis complejo

Si el modelo actual ya es el óptimo, no aparece nada (sin ruido innecesario).
Cómo usar: Si la recomendación te parece correcta, escribí `/model haiku` (u otro modelo) antes de tu próximo mensaje.

### ultra-conciso
Máxima densidad informativa. La respuesta más corta que responde completamente es la correcta. Sin preambles, sin resúmenes al final, bullets > prosa con múltiples ítems.

---

## Eficiencia de herramientas

Reglas para reducir tokens de contexto sin perder calidad:

- **Grep/Glob/Read > Bash** para buscar y leer — menos overhead, output más limpio
- **head_limit en búsquedas de símbolo/patrón** — usar 50 líneas cuando buscás algo específico; nunca limitar al leer un archivo completo para análisis
- **Subagentes solo para trabajo genuinamente independiente** — no lanzar agente para una búsqueda que podés hacer con Grep en 1 llamada
- **No reinvocar un skill** si su contenido ya está fresco en el contexto de esta conversación
- **Cuando la conversación lleva muchos intercambios** y el contexto acumulado ya no es útil: sugerir `/compact` al usuario antes de continuar con tareas nuevas
```

---

## Por @germangalo.ia
