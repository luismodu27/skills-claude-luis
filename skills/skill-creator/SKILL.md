---
name: skill-creator
description: >-
  Crea un nuevo Claude Code Skill en este repositorio siguiendo las reglas de
  AGENTS.md. Úsalo cuando el usuario diga que quiere crear, generar, añadir o
  empezar un skill nuevo, o cuando pida "un skill para X". Se encarga de la
  estructura de carpetas, el frontmatter, la plantilla, la validación y el
  registro de correcciones en MEMORY.md.
---

# skill-creator

## Propósito

Guía la creación de un skill nuevo de principio a fin, aplicando las reglas de
`AGENTS.md` y las lecciones de `MEMORY.md`, para que todos los skills del
repositorio sean consistentes y cumplan las buenas prácticas de autoría.

## Cuándo usarlo

- El usuario quiere **crear / generar / añadir / empezar** un skill nuevo.
- El usuario describe una necesidad del tipo "un skill que haga X".
- Hay que convertir una idea suelta en un skill bien estructurado.

## Antes de empezar

Lee siempre estos dos archivos de la raíz del repo y respeta lo que digan:

- `AGENTS.md` — reglas de autoría, estructura, nombres, plantilla y validación.
- `MEMORY.md` — correcciones y preferencias acumuladas del usuario.

Si algo de este skill contradice a esos archivos, **gana `AGENTS.md`/`MEMORY.md`**.

## Cómo funciona

1. **Aclara el objetivo.** Si no está claro qué hace el skill o cuándo debe
   activarse, haz 1–3 preguntas breves antes de escribir nada.
2. **Elige el nombre.** kebab-case en inglés, ≤ 64 chars; la carpeta y el campo
   `name` deben ser idénticos (p. ej. `csv-cleaner`).
3. **Crea la estructura.** `skills/<nombre-skill>/SKILL.md`. Añade
   `references/`, `scripts/` o `assets/` **solo si hacen falta**.
4. **Escribe el `SKILL.md`** a partir de la plantilla de `AGENTS.md`:
   - `description` en **español**, en tercera persona, con **qué hace** +
     **cuándo usarlo** y frases disparadoras concretas que el usuario diría.
   - Cuerpo conciso (< 200 líneas); el detalle pesado va en `references/`.
5. **Aplica divulgación progresiva.** No incrustes tablas ni ejemplos largos
   en el `SKILL.md`; enlázalos desde `references/`.
6. **Valida** con la lista de `AGENTS.md` (frontmatter + prueba real en Claude
   Code). Un skill no está terminado hasta pasar ambas.
7. **Registra aprendizajes.** Si durante el proceso el usuario corrige algo,
   añádelo a `MEMORY.md` antes de cerrar la tarea.
8. **Git.** Un skill por rama/commit, con mensaje descriptivo en español.

## Errores comunes a evitar

- `description` genérica o solo en inglés → no se dispara. Sé específico y usa
  el idioma del usuario.
- Duplicar en el `SKILL.md` reglas que ya están en `AGENTS.md`: enlaza, no copies.
- Dejar carpetas de recursos vacías.
- Cerrar el skill sin probarlo de verdad en una sesión.

## Recursos

- `AGENTS.md` (raíz) — reglas y plantilla oficiales del proyecto.
- `MEMORY.md` (raíz) — correcciones vigentes a aplicar.
