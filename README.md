# Mauricio Starter Kit — Claude Code Setup

Bundle para configurar Claude Code en la Mac de Mauricio (hermano de Hector, 12, programador junior) y arrancarlo con fundamentals primero, marketplace después.

**Auth**: shared con cuenta Max de Hector (Mauricio login con su mismo account).
**OS**: Mac (familia).
**Project location**: Mauricio decide dónde poner su repo cuando llegue ese paso — no le impongas un path.

## Archivos del bundle

| Archivo | Para qué sirve |
|---------|----------------|
| `README.md` | Este index |
| `INSTALL.md` | Procedural step-by-step para que Hector + Mauricio ejecuten en su Mac |
| `settings.example.json` | Template limpio de `~/.claude/settings.json` (sin tokens Valencia ni MCPs de Hector) |
| `mauricio-CLAUDE.md` | Template de CLAUDE.md global con reglas críticas tutor-mode |
| `skills-essential.md` | Qué plugins instalar + qué skills incluye el bundle + qué NO instalar |
| `fundamentals-roadmap.md` | 6 bloques de aprendizaje. Bloques 1-4 antes de tocar marketplace |
| `first-prompts.md` | Prompts del Día 1 para verificar install + arrancar Bloque 1 |
| `close-session-pattern.md` | Ritual de 5 pasos para cerrar cada sesión bien (update CLAUDE.md, CHANGELOG, memoria, commit) |
| `skills/` | Carpetas de skills (Next.js, Supabase, Vercel AI SDK) que se copian a `~/.claude/skills/` de Mauricio |

## Filosofía

- **Fundamentals primero**: Bloques 1-4 (terminal, git, JS, web) ANTES de buildear el marketplace. NO se salta.
- **Claude como tutor, no doer**: las reglas críticas en `mauricio-CLAUDE.md` instruyen a Claude a enseñar, no a implementar por Mauricio.
- **Filtrado, no idéntico**: NO replicamos los 80+ skills/plugins de Hector. Solo los esenciales.
- **Cero MCPs al inicio**: Higgsfield, computer-use, n8n-mcp, etc. quedan FUERA. Mauricio los agrega después si los necesita.
- **Cero hooks de memoria de Hector**: la pool de memoria de Hector tiene 6 meses de signal. Mauricio arranca fresh.
- **Cero Oktya-specific**: skills `oktya-*` son de la agencia de Hector.

## Cómo se entrega

1. Hector clona este repo (GitHub) en la Mac de Mauricio: `git clone https://github.com/Hec-M12/mauricio-starter-kit.git`
2. Hector + Mauricio leen `INSTALL.md` juntos, Mauricio ejecuta cada comando (no Hector — aprender se hace con las manos)
3. Al final del install, Mauricio corre Prompts 1-4 de `first-prompts.md`
4. Mauricio empieza Bloque 1 del `fundamentals-roadmap.md` (terminal básica)
5. Hector se retira o supervisa. Mauricio avanza a su ritmo
6. Cuando termine Bloque 4, ambos brainstorman el marketplace MVP juntos

## Timeline esperado

- **Día 1**: Install + Prompts 1-4 + arranque Bloque 1 (2-3 hrs activas)
- **Días 2-5**: Bloques 1-4 a ritmo de Mauricio
- **Día 6+**: Brainstorm MVP marketplace → Plan B → build
