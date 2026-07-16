# AGENTS.md — skills-claude-luis

Guía para cualquier agente (Claude Code) que trabaje en este repositorio.
Léela completa antes de crear o modificar un skill.

## Qué es este proyecto

Es un **laboratorio de aprendizaje** para construir múltiples **Claude Code
Skills**. Cada skill es una carpeta autónoma con un `SKILL.md` que Claude Code
descubre e invoca cuando la tarea del usuario coincide con su descripción.

El objetivo es iterar rápido y aprender, pero escribiendo cada skill con
**calidad de publicación**: podrían compartirse públicamente más adelante.

## Idioma

- **Documentación, cuerpo de los skills y comentarios:** español.
- **Nombres de carpeta, campo `name`, frontmatter y código:** inglés.

## Estructura del repositorio

```
skills-claude-luis/
├── AGENTS.md              # Este archivo
├── README.md
└── skills/
    └── <nombre-skill>/    # Una carpeta por skill (kebab-case en inglés)
        ├── SKILL.md       # Obligatorio: punto de entrada
        ├── references/    # Opcional: detalle extenso, cargado bajo demanda
        ├── scripts/       # Opcional: scripts ejecutables
        └── assets/        # Opcional: plantillas, imágenes, datos
```

- **Una carpeta por skill.** Cada skill es autónomo.
- Crea `references/`, `scripts/` o `assets/` **solo cuando hagan falta**; no
  dejes carpetas vacías.

## Convención de nombres

- Carpeta y campo `name`: **kebab-case en inglés**, iguales entre sí.
  - Ejemplos: `pdf-form-filler`, `git-commit-helper`, `csv-cleaner`.
- `name` ≤ 64 caracteres, solo minúsculas, números y guiones.

## Reglas de autoría (estrictas)

Estas reglas son obligatorias. Siguen las buenas prácticas de Anthropic.

### 1. Divulgación progresiva

- El `SKILL.md` debe ser **conciso** (idealmente < 200 líneas de cuerpo).
- El detalle pesado (referencias largas, tablas, ejemplos extensos) va en
  `references/*.md` y se enlaza desde `SKILL.md`, no se incrusta.
- Claude carga el cuerpo del `SKILL.md` siempre; los `references/` solo cuando
  los necesita. Aprovéchalo para no saturar el contexto.

### 2. La `description` es un disparador

Es el campo más importante: decide **cuándo** se activa el skill.

- Escrita en **tercera persona**.
- Debe responder dos cosas: **qué hace** el skill y **cuándo usarlo**.
- Incluye palabras/frases disparadoras concretas que el usuario usaría.
- ≤ 1024 caracteres. Específica, no genérica.
- ❌ Mal: `"Ayuda con PDFs."`
- ✅ Bien: `"Rellena formularios PDF a partir de un mapa de datos. Úsalo
  cuando el usuario quiera completar campos de un PDF, marcar casillas o
  aplanar un formulario."`

### 3. Cuerpo del `SKILL.md`

- Instrucciones claras, imperativas y accionables para el agente.
- Estructura sugerida: propósito → cuándo usar → pasos/flujo → recursos.
- Evita repetir lo que ya dice la `description`.

## Plantilla base de SKILL.md

Copia esto al crear un skill nuevo:

```markdown
---
name: nombre-del-skill
description: Qué hace el skill y cuándo debe usarse, en tercera persona, con
  frases disparadoras concretas que el usuario diría.
---

# Nombre del skill

## Propósito
Una o dos frases sobre qué resuelve este skill.

## Cuándo usarlo
- Situación disparadora 1
- Situación disparadora 2

## Cómo funciona
1. Paso uno.
2. Paso dos.
3. Paso tres.

## Recursos
- `references/detalle.md` — (opcional) documentación extendida.
- `scripts/tarea.py` — (opcional) script auxiliar.
```

## Validación antes de dar por terminado un skill

Repasa esta lista para cada skill:

- [ ] **Frontmatter válido:** existen `name` y `description`.
- [ ] `name` en kebab-case, ≤ 64 chars, igual al nombre de la carpeta.
- [ ] `description` en tercera persona, con qué-hace + cuándo-usar y
      disparadores; ≤ 1024 chars.
- [ ] El cuerpo es conciso; el detalle pesado está en `references/`.
- [ ] No hay carpetas de recursos vacías.
- [ ] **Prueba real en Claude Code:** se invoca el skill en una sesión y se
      confirma que se activa con los disparadores esperados y funciona.

Un skill no está terminado hasta pasar el frontmatter y la prueba real.

## Flujo de trabajo Git

- **Una rama por skill.** Nómbrala según el skill, p. ej.
  `skill/pdf-form-filler`.
- Commits pequeños y con mensajes descriptivos en español (imperativo):
  p. ej. `Añade skill pdf-form-filler con validación de campos`.
- Haz merge a la rama principal solo cuando el skill pase la validación.
- No mezcles varios skills en la misma rama ni en el mismo commit.

## Al crear un skill nuevo — checklist rápido

1. Crea la carpeta `skills/<nombre-skill>/` y la rama `skill/<nombre-skill>`.
2. Escribe el `SKILL.md` a partir de la plantilla.
3. Añade recursos en `references/`, `scripts/` o `assets/` solo si hacen falta.
4. Ejecuta la lista de validación.
5. Commit descriptivo y merge cuando esté listo.
