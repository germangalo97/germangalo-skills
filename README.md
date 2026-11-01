# germangalo-skills

Skills para Claude Code que uso todos los días. Las comparto en mi video
«Mi experiencia con Claude Code en 2026 (no soy programador)», en YouTube: @germangaloia.

| Skill | Qué hace |
|-------|----------|
| `selector-modelo` | Al final de cada respuesta te dice si conviene cambiar de modelo (Haiku, Sonnet, Opus, Opus Plan o Fable) y con qué comando |
| `ultra-conciso` | Respuestas sin relleno, sin recortar el código ni los resultados técnicos |
| `eficiencia-herramientas` | Busca y lee archivos de la forma que gasta menos tokens |

Una skill es una carpeta con un archivo `SKILL.md`: instrucciones que Claude Code lee cuando le sirven para lo que
estás haciendo. Las personales van en la carpeta `.claude/skills` de tu usuario y valen para todos tus proyectos.

---

## Opción 1: pedírselo a Claude Code (la más fácil)

Abre Claude Code y escribe:

```
Instala la skill selector-modelo de https://github.com/germangalo97/germangalo-skills
en mis skills personales (~/.claude/skills/selector-modelo/SKILL.md).
```

Claude Code descarga el archivo y lo pone en su lugar. Revisa lo que te muestra antes de aceptar.

## Opción 2: descargarla a mano

1. Descarga [selector-modelo.zip](https://github.com/germangalo97/germangalo-skills/releases/latest/download/selector-modelo.zip).
2. Descomprímelo. Queda una carpeta `selector-modelo` con un archivo `SKILL.md` adentro.
3. Copia esa carpeta dentro de la carpeta de skills de tu usuario:
   - Windows: `C:\Users\TU-USUARIO\.claude\skills\`
   - Mac y Linux: `~/.claude/skills/`
   (si la carpeta `skills` no existe, créala).
4. Abre una sesión nueva de Claude Code.

## Opción 3: con la terminal

Necesita Node.js 22.20 o más nuevo:

```bash
npx skills add germangalo97/germangalo-skills --skill selector-modelo -g -a claude-code
```

Cambia `selector-modelo` por `ultra-conciso` o `eficiencia-herramientas` para instalar las otras.

---

## Que esté siempre activa

Claude Code usa una skill cuando cree que hace falta, o cuando la llamas con `/selector-modelo`. Si quieres que la
recomendación aparezca siempre, pega esto en tu `CLAUDE.md` (el archivo de instrucciones que Claude Code lee al
empezar cada sesión: `~/.claude/CLAUDE.md` para todos tus proyectos, o `CLAUDE.md` en la carpeta del proyecto):

```md
## Skills siempre activas

### selector-modelo
Al final de cada respuesta, si conviene un modelo distinto del actual para el próximo mensaje, escribe una línea:
→ Próximo: Haiku (/model haiku) — consulta simple
→ Próximo: Sonnet (/model sonnet) — tarea de código
→ Próximo: Opus (/model opus) — sistema nuevo
→ Próximo: Opus Plan (/model opusplan) — trabajo grande
Fable (/model fable) solo para lo excepcional: según el plan, se cobra con créditos de uso.
Si el modelo actual ya es el adecuado, no escribas nada.

### ultra-conciso
La respuesta más corta que responde completamente es la correcta. Sin introducciones ni resúmenes al final;
listas en lugar de párrafos cuando hay varios puntos. El código y los resultados técnicos van siempre completos.
```

---

## Eficiencia de herramientas

Reglas para gastar menos tokens sin perder calidad:

- **Grep, Glob y Read antes que Bash** para buscar y leer: menos texto de más en la respuesta.
- **Limitar las búsquedas de un símbolo** a unas 50 líneas; nunca limitar al leer un archivo entero para analizarlo.
- **Subagentes solo para trabajo que de verdad es independiente**: no lanzar un agente para una búsqueda que sale
  con un Grep.
- **No volver a llamar una skill** si su contenido ya está en la conversación.
- **Cuando la conversación ya es muy larga** y lo anterior no sirve: sugerir `/compact` antes de seguir con algo nuevo.

---

Hecho por Germán Galo · YouTube @germangaloia · Instagram y TikTok @germangalo.ia
