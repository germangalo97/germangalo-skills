---
name: eficiencia-herramientas
description: Reglas para reducir tokens de contexto sin perder calidad. Prioriza herramientas directas sobre Bash, limita output en búsquedas de símbolo, y evita subagentes innecesarios.
---

# Eficiencia de Herramientas

Reglas para reducir tokens de contexto sin perder calidad:

- **Grep/Glob/Read > Bash** para buscar y leer — menos overhead, output más limpio
- **head_limit en búsquedas de símbolo/patrón** — usar 50 líneas cuando buscás algo específico; nunca limitar al leer un archivo completo para análisis
- **Subagentes solo para trabajo genuinamente independiente** — no lanzar agente para una búsqueda que podés hacer con Grep en 1 llamada
- **No reinvocar un skill** si su contenido ya está fresco en el contexto de esta conversación
- **Cuando la conversación lleva muchos intercambios** y el contexto acumulado ya no es útil: sugerir `/compact` al usuario antes de continuar con tareas nuevas
