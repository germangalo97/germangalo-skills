---
name: eficiencia-herramientas
description: Reduce el consumo de tokens al buscar y leer código. Prioriza herramientas directas (Grep, Glob, Read) sobre comandos de shell, y limita el volumen de output cuando la tarea no requiere el archivo completo.
---

# Eficiencia de Herramientas

Cada búsqueda en el código tiene un costo de tokens. Estas reglas reducen ese costo sin perder información relevante.

## Herramientas directas sobre Bash

Usar Grep, Glob y Read en lugar de comandos Bash equivalentes:

| Tarea | En lugar de | Usar |
|-------|-------------|------|
| Buscar un patrón en archivos | `Bash: grep -r "pattern" .` | `Grep: pattern` |
| Encontrar archivos por nombre | `Bash: find . -name "*.ts"` | `Glob: **/*.ts` |
| Leer un archivo | `Bash: cat archivo.ts` | `Read: archivo.ts` |

**Por qué**: Bash abre un shell completo, captura stderr, y añade overhead de proceso. Las herramientas directas retornan solo el contenido útil.

## head_limit en búsquedas de símbolo

Cuando buscás una función, clase, variable o patrón específico, establecé `head_limit: 50`.

```
Grep: "function processLead" | head_limit: 50
```

Regla: si buscás algo específico, limitá a 50 líneas.  
Excepción: si necesitás leer un archivo completo para análisis, **no limites** — limitarlo puede cortarte información crítica.

## Subagentes solo para trabajo genuinamente independiente

No lanzar un subagente para una búsqueda que se puede hacer con Grep en 1 llamada.

Los subagentes tienen costo fijo de inicialización (~500-1000 tokens). Usarlos para tareas que una sola herramienta puede resolver en 1 llamada multiplica el costo sin beneficio.

**Cuándo sí usar subagente**: tareas que corren en paralelo y cada una requiere múltiples pasos propios.  
**Cuándo no**: buscar un símbolo, leer un archivo, verificar si algo existe.

## Resumen de reglas

- Grep/Glob/Read > Bash para buscar y leer
- `head_limit: 50` en búsquedas de símbolo o patrón
- Nunca limitar al leer un archivo completo para análisis
- Subagentes solo cuando el trabajo es genuinamente paralelo e independiente
