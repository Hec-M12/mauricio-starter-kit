# Install — Claude Code en Mac de Mauricio

Sentate al lado de Mauricio. Mauricio ejecuta los comandos, vos supervisás y respondés sus preguntas. **Importante**: que escriba él, no vos. Aprender se hace con las manos.

**Tiempo estimado**: 45-60 minutos.

---

## Pre-flight (chequeá antes de empezar)

- [ ] macOS 12+ (Monterey o más nuevo)
- [ ] Mauricio sabe la contraseña de admin de su Mac (o vos)
- [ ] Conexión internet estable
- [ ] ~2 horas bloqueadas sin interrupciones
- [ ] Editor visual de código instalado o a instalar — sugerencia VS Code: `brew install --cask visual-studio-code` (lo hacemos en Paso 2.5)

---

## Paso 1 — Verificar / instalar Xcode Command Line Tools

Muchos npm packages requieren esto en Mac. Verificar:

```bash
xcode-select -p
```

Si imprime algo tipo `/Library/Developer/CommandLineTools` → ya está. Skip al Paso 2.

Si dice error o nada:

```bash
xcode-select --install
```

Aparece un dialog del OS pidiendo instalar. Aceptar y esperar (5-10 min).

---

## Paso 2 — Instalar Homebrew (si no está)

```bash
which brew
```

Si imprime `/opt/homebrew/bin/brew` o `/usr/local/bin/brew` → ya está. Skip al Paso 2.5.

Si no:

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

Al final, el installer imprime instrucciones para agregar brew al PATH (algo como `echo 'eval "$(/opt/homebrew/bin/brew shellenv)"' >> ~/.zprofile`). Seguirlas exactamente. Cerrar terminal, abrir nueva, verificar con `which brew`.

---

## Paso 2.5 — Instalar Node.js + git + VS Code

```bash
brew install node git
brew install --cask visual-studio-code
```

Verificar:

```bash
node --version    # v20+ esperado
npm --version
git --version
```

---

## Paso 2.6 — Configurar git

Sin esto, los commits fallan. Mauricio usa nombre + email reales (el email puede ser uno que tenga o uno nuevo que cree para el proyecto).

```bash
git config --global user.name "Mauricio"
git config --global user.email "el-email-que-mauricio-elija@gmail.com"
git config --global init.defaultBranch main
git config --global pull.rebase false
```

Verificar:

```bash
git config --global --list
```

Debe imprimir las 4 líneas.

---

## Paso 3 — Instalar Claude Code

```bash
npm install -g @anthropic-ai/claude-code
```

Verificar:

```bash
claude --version
```

Si `claude: command not found`: cerrar terminal, abrir nueva, retry. Si persiste, ejecutar `npm config get prefix` y agregar `<output>/bin` al PATH manualmente.

---

## Paso 4 — Login con tu cuenta Anthropic

```bash
claude
```

Adentro del prompt interactivo:

```
/login
```

Eso abre un browser para OAuth. Login con TU email (el del Max plan).

**Aviso a Mauricio**:
> "Mauricio, esta cuenta tiene mi historial de Oktya. NO uses claude.ai (la web) desde esta Mac sin avisarme primero. Para tu proyecto, usá SOLO `claude` desde la terminal. Si querés ver tu propio historial después, te creo tu propio account."

---

## Paso 5 — Limpiar config viejo si existe

```bash
ls ~/.claude/ 2>/dev/null
```

Si está vacío o no existe → fresh slate, continuar.

Si tiene contenido viejo:

```bash
mv ~/.claude ~/.claude.backup-$(date +%Y%m%d)
mkdir -p ~/.claude
```

---

## Paso 6 — Clonar el starter kit desde GitHub

El repo del kit vive en GitHub. Clonarlo a algún lugar (ejemplo `~/Downloads/`):

```bash
cd ~/Downloads
git clone https://github.com/Hec-M12/mauricio-starter-kit.git
cd mauricio-starter-kit
ls
```

Debe imprimir todos los archivos del kit (README.md, INSTALL.md, settings.example.json, etc.).

---

## Paso 7 — Instalar settings + CLAUDE.md + skills

Desde dentro de `mauricio-starter-kit/`:

```bash
# Settings (permisos básicos + status bar)
cp settings.example.json ~/.claude/settings.json

# CLAUDE.md global (Mauricio's identity para Claude)
cp mauricio-CLAUDE.md ~/.claude/CLAUDE.md

# Status bar inferior (modelo, task activa, contexto usado, rate limits)
mkdir -p ~/.claude/hooks
cp hooks/gsd-statusline.js ~/.claude/hooks/

# Skills Next.js + Supabase (para Fase 2, cuando empiece a buildear)
mkdir -p ~/.claude/skills
cp -r skills/* ~/.claude/skills/
```

Verificar que skills se copiaron:

```bash
ls ~/.claude/skills/
```

Debe listar las carpetas de skills (nextjs-*, supabase-postgres-best-practices, etc.).

---

## Paso 8 — Instalar plugins esenciales

Lanzar Claude Code interactivo:

```bash
claude
```

Adentro, instalar los plugins Anthropic-oficiales:

```
/plugin marketplace add anthropics/claude-plugins-official
/plugin install superpowers@claude-plugins-official
/plugin install frontend-design@claude-plugins-official
/plugin install code-review@claude-plugins-official
/plugin install skill-creator@claude-plugins-official
```

Salir con `/exit`. Abrir nuevo `claude` para que cargue los plugins.

**NO instalar más plugins ahora**. Ver `skills-essential.md` para la lista completa de qué NO instalar y por qué.

---

## Paso 9 — Sanity check con primer prompt

```bash
mkdir ~/scratch-claude
cd ~/scratch-claude
claude
```

Mauricio escribe el Prompt 1 de `first-prompts.md`:

```
Hola! Soy Mauricio. ¿Sabés algo sobre mí y mi proyecto?
```

**Resultado esperado**: Claude responde con datos correctos sobre Mauricio (12 años, hermano de Hector, marketplace). Si NO los menciona → revisar Paso 7.

---

## Paso 10 — Empezar fundamentals (no marketplace todavía)

Mauricio NO arranca el repo del marketplace hoy. Hoy aprende fundamentals.

Mauricio abre `fundamentals-roadmap.md` y empieza por el Bloque 1 (Terminal). Lo recorre con Claude como tutor. Vos podés sentarte a leer al lado o dejarlo solo si querés.

Una vez complete los Bloques 1-4 del roadmap (terminal, git, JS, HTTP/web básico) → recién ahí brainstormeamos el MVP y arrancamos el repo.

Estimación: 3-7 días según ritmo. NO hay prisa — la ventana del mundial es del 11 jun, faltan ~30 días.

---

## Si algo falla

| Síntoma | Acción |
|---------|--------|
| `brew: command not found` post-install | Cerrar terminal, abrir nueva. Si persiste, revisar instrucciones de PATH del installer. |
| `claude: command not found` post-install | `npm config get prefix` → agregar `<output>/bin` al PATH en `~/.zprofile`. Cerrar y abrir terminal. |
| `/login` falla en browser | Verificar internet. Si insiste, probar `/login` otra vez. |
| `/plugin install` falla | Verificar que estás logueado (al abrir `claude` debe mostrar email en algún lado). Reintentar. |
| Skills no aparecen | Salir Claude (`/exit`), volver a abrir. |
| `cp` falla por path | Verificar que estás dentro de `~/Downloads/mauricio-starter-kit/` (con `pwd`). |
| `git config` settings no toman | Asegurar que escribiste `--global`. Verificar con `git config --global --list`. |
| Mauricio frustrado | Pausá. Salí a tomar agua. No es race — entender > velocidad. |

---

## Después del install

- El repo `mauricio-starter-kit/` puede quedarse en `~/Downloads/` como referencia, no estorba
- Cualquier duda técnica → Mauricio te pregunta primero, no a Claude (al menos primera semana)
- Mauricio empieza `fundamentals-roadmap.md`, no el marketplace
- En 1-2 semanas revisás `~/.claude/CLAUDE.md` de Mauricio para ver cómo evoluciona su setup
