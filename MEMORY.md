# MEMORY.md — Memoria de correcciones

Registro vivo de las correcciones, preferencias y lecciones aprendidas en este
proyecto. Su objetivo es que los skills mejoren **de forma progresiva**: cada
vez que el usuario corrige algo, esa lección queda aquí y no se repite el error.

## Cómo funciona (para el agente)

1. **Léelo siempre** al inicio de cualquier tarea, junto con `AGENTS.md`.
   Las reglas de aquí tienen prioridad sobre los hábitos por defecto.
2. **Actualízalo** cada vez que el usuario te corrija, rechace un enfoque o
   exprese una preferencia nueva. No esperes a que te lo pidan: añadir la
   entrada es parte de aplicar la corrección.
3. **Generaliza** la corrección puntual a una regla reutilizable siempre que
   sea posible, para que aplique a futuros skills y no solo al caso actual.
4. **Consolida:** si una corrección es estable y general, considera moverla o
   reflejarla también en `AGENTS.md` como regla permanente.
5. No borres entradas antiguas salvo que queden obsoletas; en ese caso
   márcalas como `~~obsoleta~~` con una nota, no las elimines sin dejar rastro.

## Formato de cada entrada

Añade las entradas nuevas al principio de la sección "Correcciones" (las más
recientes arriba). Usa esta plantilla:

```markdown
### [YYYY-MM-DD] Título corto de la lección

- **Contexto:** qué estaba haciendo cuando surgió la corrección.
- **Corrección:** qué me indicó el usuario que cambiara o evitara.
- **Regla:** la lección generalizada a aplicar de ahora en adelante.
```

## Correcciones

<!-- Añade aquí las entradas nuevas, las más recientes arriba. -->

### [2026-07-17] Los skills deben ir en `.claude/skills/`, no en `skills/`

- **Contexto:** habíamos colocado los skills en `skills/<nombre>/SKILL.md` en la
  raíz del repo.
- **Corrección:** Claude Code solo descubre skills en `.claude/skills/<nombre>/`;
  una carpeta `skills/` en la raíz no se carga automáticamente.
- **Regla:** todos los skills viven en `.claude/skills/<nombre>/SKILL.md`.
  Reflejado en `AGENTS.md` → "Estructura del repositorio".

### [2026-07-17] La `description` va en español, no en inglés

- **Contexto:** al crear el skill `skill-creator` surgió la duda del idioma del
  frontmatter, que `AGENTS.md` marcaba como inglés.
- **Corrección:** el campo `description` es el disparador y debe coincidir con
  cómo pregunta el usuario (español); en inglés no se activaría.
- **Regla:** `name` y código en inglés, pero `description` (y el cuerpo del
  skill) en español. Reflejado en `AGENTS.md` → sección "Idioma".
