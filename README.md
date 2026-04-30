# germangalo-skills

Skills de optimización de tokens para Claude Code. Reducen el costo por conversación sin sacrificar calidad de respuesta.

## Skills disponibles

| Skill | Qué hace |
|-------|----------|
| `selector-modelo` | Recomienda el modelo óptimo al final de cada respuesta |
| `ultra-conciso` | Elimina relleno verbal sin recortar outputs técnicos |
| `eficiencia-herramientas` | Prioriza Grep/Glob/Read sobre Bash y limita output en búsquedas |

## Instalación

```bash
npx skills add germangalo97/germangalo-skills@selector-modelo -g -y
npx skills add germangalo97/germangalo-skills@ultra-conciso -g -y
npx skills add germangalo97/germangalo-skills@eficiencia-herramientas -g -y
```

El flag `-g` instala globalmente (aplica a todos tus proyectos). Omitilo para instalar solo en el proyecto actual.

## Uso

Una vez instaladas, invocá cada skill desde Claude Code:

```
/selector-modelo
/ultra-conciso
/eficiencia-herramientas
```

O activarlas permanentemente en tu `CLAUDE.md`:

```md
## Skills activos
Aplicar siempre las reglas de /ultra-conciso y /eficiencia-herramientas.
Al final de cada respuesta, aplicar /selector-modelo.
```

## Por @germangalo.ia
