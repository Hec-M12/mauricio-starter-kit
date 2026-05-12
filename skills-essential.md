# Skills + Plugins Esenciales para Mauricio

Lista curada. Hector la usa cuando ejecuta `INSTALL.md` paso 7 (copia de skills) y paso 8 (install de plugins).

## Filosofía

- **Día 1**: pocas skills, foco en aprender fundamentals. Solo `superpowers`, `frontend-design`, `code-review`, `skill-creator`.
- **Bloque 5+** (cuando termine fundamentals): se activan las skills de Next.js y Supabase que ya están en su filesystem.
- **Cuando lo necesite**: Mauricio agrega más skills/plugins. NO al inicio.

---

## Skills incluidas en el starter kit (vienen copiadas por `cp -r skills/* ~/.claude/skills/`)

Estas las trajimos del setup de Hector porque son skills directas (no plugin-namespaced). Mauricio las tiene en su filesystem pero NO las usa hasta Bloque 5.

### Next.js (para Bloque 5+)

- `nextjs-app-router-fundamentals` — fundamentos de App Router (Next.js 13+)
- `nextjs-server-client-components` — cuándo usar `'use client'` vs server components (crítico, fácil confundir)
- `nextjs-dynamic-routes-params` — rutas dinámicas con `[id]`
- `nextjs-pathname-id-fetch` — fetch data basado en URL params
- `nextjs-anti-patterns` — evitar errores comunes
- `nextjs-use-search-params-suspense` — pattern de useSearchParams con Suspense
- `nextjs-advanced-routing` — server actions, parallel routes, intercepting routes (no día 1)
- `nextjs-client-cookie-pattern` — server actions desde client components
- `nextjs-server-navigation` — navegación con Link + redirect()

### Supabase

- `supabase-postgres-best-practices` — optimización de queries + schema design

### Vercel AI SDK

- `vercel-ai-sdk` — para Bloque 6 si el MVP integra AI features (probable porque vamos a tener photo extraction como milla 2)

---

## Plugins a instalar vía `/plugin install` (Día 1)

Solo estos 4. NO instales más al inicio. Comandos exactos van en `INSTALL.md` Paso 8.

### 1. `superpowers@claude-plugins-official`

Skills de proceso que Mauricio va a usar todo el tiempo:

- `superpowers:brainstorming` — antes de cualquier feature nueva. Convierte ideas en specs.
- `superpowers:test-driven-development` — escribir test antes que código. TDD desde día 1.
- `superpowers:systematic-debugging` — debugging científico (hipótesis → test → fix).
- `superpowers:verification-before-completion` — verificar antes de decir "listo".
- `superpowers:writing-plans` — specs → planes ejecutables.
- `superpowers:using-superpowers` — meta-skill que enseña a usar los demás.

### 2. `frontend-design@claude-plugins-official`

Skill `frontend-design:frontend-design` — diseñar interfaces production-grade. Sin esto, la UI parece tutorial de YouTube. Con esto, parece app real.

### 3. `code-review@claude-plugins-official`

Skill `code-review:code-review` — para revisar el código que Mauricio escribe antes de commit. Refuerza la regla "explicame antes de aceptar".

### 4. `skill-creator@claude-plugins-official`

Skill `skill-creator:skill-creator` — si Mauricio se traba 2+ veces en el mismo pattern y no hay skill que lo cubra, puede crear una nueva juntos con Hector. No urgente día 1.

---

## NO instalar (estos son específicos de Hector / Oktya)

- ❌ `oktya-*` (suite completa) — agencia de Hector
- ❌ `gsd-*` (suite completa) — framework de planning con overhead innecesario para junior
- ❌ `n8n-*` — Mauricio no construye workflows n8n
- ❌ `oktya-broll-pipeline`, `oktya-editing`, `oktya-portfolio-positioning` — content production de Hector
- ❌ `higgsfield`, `image-generation`, `imagegen-*`, `brandkit`, `stitch-skill`, `taste-skill`, `brutalist-skill`, `minimalist-skill`, `redesign-skill`, `soft-skill`, `gpt-tasteskill` — generación de imágenes + design styles. Tal vez después.
- ❌ `dream`, `dream-review` — memory consolidation de Hector
- ❌ `apply`, `job-search`, `cover-letter`, `tailor-resume`, `network-scan` — job hunting de Hector
- ❌ `claude-api` — solo si llegamos a integrar Claude API en el marketplace, no antes
- ❌ `setup`, `init`, `update-config`, `keybindings-help`, `statusline-setup`, `fewer-permission-prompts` — meta-tools que distraen
- ❌ `loop`, `schedule`, `ralph-overnight`, `gsd-autonomous` — automation, no en mes 1
- ❌ Cualquier `mcp__*` (MCPs) — Higgsfield, computer-use, Canva, Gmail, Notion, Supabase MCP, WhatsApp MCP, Serena, Playwright, etc. Mauricio arranca sin MCPs.

---

## Cuándo agregar más

Reglas de pulgar:

- **Mauricio se traba 2+ veces en lo mismo y no hay skill para eso** → agregar skill existente o crear uno (`skill-creator`)
- **Mauricio pide hacer algo que requiere herramienta nueva** (eg. "quiero ver el browser mientras desarrollo") → MCP de Playwright
- **Mauricio gasta tokens explicando lo mismo cada sesión** → agregar memoria persistente (`feedback_*.md`) en su pool

---

## Validation (después del install)

Mauricio corre los Prompts 1, 2, 3 de `first-prompts.md`. Si los 3 pasan → install OK. Si alguno falla → revisar el paso del INSTALL.md correspondiente.
