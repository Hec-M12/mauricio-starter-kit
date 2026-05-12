# Cerrar Sesión — Pattern Simple

Al final de cada sesión productiva, cerrá bien para que la próxima sesión arranque sin re-explicar todo.

## Por qué importa

Cada vez que abrís `claude`, es una sesión nueva. Claude lee tu `CLAUDE.md` y tus memorias, pero NO recuerda lo que pasó en sesiones anteriores SI no lo guardaste explícitamente.

**Cerrar bien = guardar lo que importa antes de irte**. Sin esto:

- Mañana abrís Claude y le re-explicás dónde estabas
- Perdés contexto de decisiones tomadas hoy
- El historial de tu proyecto vive solo en tu cabeza
- Reincidís en errores que ya resolviste

## Cuándo aplica

- Cuando termines una sesión de trabajo de >30 min
- Cuando vas a apagar la Mac o cerrar la terminal
- Cuando contexto se está llenando (Claude empieza a olvidar cosas del principio de la sesión)
- ANTES de irte a dormir si laburaste

**Cuándo NO aplica**: sesiones de 5 min haciendo algo trivial. No hace falta ritual.

## El ritual — 5 pasos

Cuando estés listo para cerrar, decile a Claude **textualmente**:

```
Cerremos la sesión. Seguí el close-session-pattern de mi kit.
```

Claude debería hacer los 5 pasos siguientes. **Vos verificás que los hizo, no solo que dijo que los hizo**.

### Paso 1 — Update CLAUDE.md del proyecto

El `CLAUDE.md` del proyecto (en la raíz del repo, NO el global de `~/.claude/`) debe reflejar:

- Qué hicimos hoy (1-2 frases)
- Qué decidimos (si hubo decisión importante)
- Qué falta hacer next

Si tu proyecto todavía no tiene `CLAUDE.md` propio, Claude lo crea.

### Paso 2 — Append a CHANGELOG.md del proyecto

Entrada nueva al tope con:

```markdown
## YYYY-MM-DD — [título corto]

- Hice: [qué se completó]
- Decidí: [si hubo decisión]
- Siguiente: [próximo paso concreto]
```

Si tu proyecto todavía no tiene `CHANGELOG.md`, Claude lo crea.

### Paso 3 — Guardar memoria durable (si aplica)

Si en esta sesión aprendiste algo que vale para FUTURAS sesiones (no solo esta), Claude lo guarda en tu memory pool:

- **Preferencia tuya**: "Mauricio prefiere variable names en inglés aunque comentarios en español"
- **Regla de proyecto**: "Marketplace usa UUIDs como IDs, no auto-increment"
- **Lección aprendida**: "Cuidado con Server Components que llaman APIs sin cache — duplican requests"

Si NO aprendiste nada durable hoy → skip este paso. Es OK.

Estas memorias viven en `~/.claude/projects/<tu-pool>/memory/` automáticamente. Claude sabe dónde van.

### Paso 4 — Git commit + push

```bash
git add .
git commit -m "session: <título corto>"
git push  # si tenés remote
```

Claude lo ejecuta. Vos confirmás que el commit aparece en `git log`.

### Paso 5 — Confirmar el cierre

Claude debería responder al final algo tipo:

> "Session closed. CLAUDE.md y CHANGELOG.md actualizados. Memoria guardada: X. Commit hecho."

Si Claude saltea pasos o solo dice "listo" sin detalle → pedile que confirme cada paso uno por uno.

## Ejemplo de sesión cerrada bien

```
Mauricio: Cerremos la sesión. Seguí el close-session-pattern de mi kit.

Claude:
1. Update CLAUDE.md: agregué que terminamos Bloque 3 del fundamentals y
   empezamos Bloque 4 con curl. Next: completar Bloque 4 mañana.
2. Append CHANGELOG.md:
   ## 2026-05-12 — Bloque 3 ✓, Bloque 4 arranque
   - Hice: Completamos Bloque 3 JS básico, primer commit fundamentals.js
   - Decidí: usar `const` por default, `let` solo si reassign
   - Siguiente: Terminar Bloque 4 (HTTP + fetch) mañana
3. Memoria durable: agregué a tu pool una nota sobre que preferís async/await
   sobre .then() después de que lo discutimos hoy
4. git commit -m "session: complete bloque 3, start bloque 4" → done, sha abc123
5. ✓ Session closed
```

## Anti-patterns

- ❌ "Cerrá sesión" sin más → Claude puede saltear pasos. Decí siempre "seguí el close-session-pattern de mi kit".
- ❌ Cerrar sin verificar → siempre leé el CHANGELOG.md entry antes de salir
- ❌ Commits con mensaje "WIP" o "stuff" → el message del commit es parte del historial. Sé específico
- ❌ Skipear este ritual "porque no tengo ganas" → en 2 semanas vas a tener un proyecto con CHANGELOG vacío y memoria de mierda

## Auto-memory — cómo funciona

Claude Code tiene memoria automática built-in. Cada proyecto/carpeta tiene su propio "pool" en `~/.claude/projects/<carpeta-encoded>/memory/`.

Adentro del pool vive:

- `MEMORY.md` — índice de memorias
- Archivos individuales: `feedback_X.md` (correcciones que me diste), `project_X.md` (decisiones de proyecto), `user_X.md` (cosas sobre vos), `reference_X.md` (cómo usar herramientas externas)

**Vos no tenés que escribir estos archivos a mano**. Claude los escribe cuando aprende algo durable durante la sesión (Paso 3 del ritual de cierre).

Para ver qué memorias tenés:

```bash
ls ~/.claude/projects/
# encontrá tu pool (será tu cwd encoded con guiones)
ls ~/.claude/projects/<tu-pool>/memory/
cat ~/.claude/projects/<tu-pool>/memory/MEMORY.md
```

Cuando arranques una sesión nueva en el mismo proyecto, Claude lee `MEMORY.md` y tiene todo el contexto.

## Avanzado (no día 1, pero saber que existe)

Hector usa un sistema más complejo para Oktya con múltiples agentes, inbox compartido entre agents, dream consolidation, etc. Vos NO necesitás eso ahora. Cuando crezca el proyecto y tengas 2-3 sub-projects independientes, hablamos con Hector y vemos qué pieza agregar.

Por ahora: 5 pasos, ritual al final de cada sesión. Suficiente.
