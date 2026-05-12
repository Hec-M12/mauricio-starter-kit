# Fundamentals Roadmap — Mauricio

Ruta de aprendizaje antes de tocar código del marketplace. Cada bloque tiene: qué aprender, prompts sugeridos para Claude, criterio de "listo".

**Cadencia sugerida**: 1 bloque por día. Si necesitás 2 días, perfecto. NO bridges, NO saltarse bloques.

**Total estimado**: 5-7 días para los Bloques 1-4. Después brainstormeamos el MVP.

---

## Bloque 1 — Terminal básica

**Por qué importa**: la terminal es tu interfaz primaria. Cuanto más fluido seas, más rápido aprenderás todo lo demás.

**Conceptos**:
- Filesystem: `/`, `~`, paths absolutos vs relativos
- Comandos esenciales: `pwd`, `cd`, `ls`, `mkdir`, `touch`, `cp`, `mv`, `rm`, `cat`, `echo`
- Tab completion (autocompletar con TAB)
- Historial (flecha arriba)
- Pipes y redirección básica: `|`, `>`, `>>`
- `man` y `--help` (cómo aprender solo)

**Prompt para Claude**:
```
Bloque 1 del fundamentals: terminal básica. Enseñame uno por uno los comandos esenciales. Cada uno: definición corta + 1 ejemplo que YO escribo + 1 pregunta para chequear que entendí. Empezamos por `pwd`. Recordá la regla #1 de mi CLAUDE.md — sos tutor.
```

**Listo cuando**:
- [ ] Podés navegar a cualquier directorio en tu Mac sin pensarlo
- [ ] Podés crear, copiar, mover, borrar archivos y carpetas
- [ ] Podés explicar qué hace `ls -la` línea por línea
- [ ] Podés explicar diferencia entre `cd ..` y `cd /`
- [ ] No te asustás al ver paths largos

---

## Bloque 2 — Git fundamentals

**Por qué importa**: cada cambio que escribas se guarda en git. Sin esto, perdés trabajo o pisás trabajo de otros.

**Conceptos**:
- Qué es un repo, qué es un commit
- `git init`, `git status`, `git add`, `git commit`, `git log`
- `git diff` antes y después de `add`
- Branches: `git branch`, `git checkout -b`, `git merge` (concepto)
- Remotes: qué es origin, `git push`, `git pull`
- `.gitignore`
- **Qué NO hacer**: `git push --force`, `git reset --hard` sin saber qué hacen

**Prompt para Claude**:
```
Bloque 2 del fundamentals: git. Soy nuevo. Quiero hacer un mini-proyecto: crear un repo vacío, hacer 3 commits chiquitos, ver el log, y entender qué pasó. Guíame con `git init` y vamos paso a paso. Yo escribo, vos explicás cada flag. NO me hagas avanzar al siguiente comando hasta que entienda el actual.
```

**Listo cuando**:
- [ ] Podés crear un repo desde cero y hacer commits
- [ ] Entendés qué hace `git add` (staging area) y por qué existe
- [ ] Podés explicar qué muestra `git log` y `git status`
- [ ] Sabés crear una branch y cambiar a ella
- [ ] Sabés qué es un remote y cómo pushear a GitHub
- [ ] Sabés qué hace `.gitignore` y para qué sirve

**Bonus** (opcional pero recomendado):
- [ ] Creaste tu cuenta de GitHub (usar tu email)
- [ ] Creaste un repo público "hello-mauricio" con un README

---

## Bloque 3 — JavaScript básico

**Por qué importa**: el marketplace lo vamos a buildear en JavaScript/TypeScript. Si no podés leer JS, no podés revisar el código que Claude escribe.

**Conceptos**:
- Variables: `const`, `let` (NO usar `var`)
- Tipos: string, number, boolean, null, undefined
- Funciones: declaración, arrow functions, parámetros, return
- Arrays: `[].map`, `.filter`, `.find`, `.forEach`, `.length`
- Objects: keys, values, dot notation vs bracket notation, destructuring
- Conditionals: `if/else`, ternario, `&&` y `||`
- `console.log` para debug
- Async/await (concepto básico, no profundo todavía)

**Prompt para Claude**:
```
Bloque 3 del fundamentals: JavaScript básico. NO lo vamos a leer — lo vamos a escribir. Creemos un archivo `fundamentals.js` y escribamos código sencillo juntos. Vos proponés un ejercicio chiquito, yo lo escribo, lo corro con `node fundamentals.js`, y si falla lo arreglamos juntos. Empezamos por declarar 3 variables (string, number, boolean) e imprimirlas. Recordá: tutor, no doer.
```

**Listo cuando**:
- [ ] Podés escribir una función que toma 2 números y retorna su suma
- [ ] Podés escribir un array de 5 strings y filtrarlo (quedarte solo con los que tienen más de 3 letras)
- [ ] Podés explicar qué hace `array.map(x => x * 2)`
- [ ] Podés acceder a una propiedad anidada de un object: `user.address.city`
- [ ] Entendés qué es async/await aunque sea conceptual ("código que espera por algo")
- [ ] Podés leer código JS y guess qué hace antes de ejecutarlo

---

## Bloque 4 — Web básico (HTTP, JSON, APIs)

**Por qué importa**: el marketplace es un web app. Frontend habla con backend vía HTTP. Si no entendés HTTP, no entendés cómo se conectan las cosas.

**Conceptos**:
- Qué es HTTP: request/response
- Métodos: GET, POST, PUT, DELETE (qué hace cada uno conceptualmente)
- Status codes esenciales: 200, 201, 400, 401, 404, 500
- JSON: qué es, cómo se ve, cómo difiere de un object JS
- Qué es una API REST (concepto)
- Hacer un request con `fetch()` desde Node
- Hacer un request con `curl` desde terminal

**Prompt para Claude**:
```
Bloque 4 del fundamentals: web básico. Quiero entender cómo funciona el internet a nivel "qué pasa cuando abro una página". Después quiero hacer mi primer HTTP request a una API pública (tipo jsonplaceholder.typicode.com o similar). Enseñame los conceptos primero con dibujos en texto / diagramas, después hacemos el request juntos con `curl` y con `fetch()`. Tutor, no doer.
```

**Listo cuando**:
- [ ] Podés explicar qué pasa entre escribir una URL en el browser y ver la página (request → server → response → render)
- [ ] Sabés la diferencia entre GET y POST
- [ ] Podés leer un response JSON y extraer un valor específico
- [ ] Hiciste un `curl` exitoso a una API pública
- [ ] Hiciste un `fetch()` exitoso desde Node a una API pública
- [ ] Entendés que el frontend (lo que el user ve) y el backend (donde vive la lógica + DB) son cosas separadas que se hablan vía HTTP

---

## Bloque 5 — Next.js + Supabase intro (DESPUÉS de 1-4)

Una vez los 4 anteriores estén ✓, hablamos con Claude que ya tenés las skills de Next.js + Supabase disponibles. Bloque 5 es:
- Levantar un Next.js skeleton vacío
- Entender estructura: `app/`, `page.tsx`, `layout.tsx`
- Conectar a Supabase, crear una tabla, hacer un read básico
- Server vs Client components (importante, fácil confundir)

**Prompt para Claude**:
```
Bloque 5: arrancamos con Next.js + Supabase. Antes de tocar el marketplace, quiero hacer un mini-proyecto: una página que liste 5 figuritas de prueba desde una tabla de Supabase. Eso me enseña los fundamentals del stack sin la complejidad del marketplace real. Tutor, no doer — quiero entender cada archivo que creamos.
```

---

## Bloque 6 — Brainstorm + build del marketplace

Una vez Bloque 5 ✓ → avisale a Hector. Vos + Mauricio + Claude brainstorman el MVP del marketplace, escriben el spec, y arrancan a buildear con TDD.

Eso es Plan B. No es parte de este roadmap.

---

## Reglas del roadmap

- **NO saltar bloques**. Si te aburrís en el Bloque 1, igual hacelo. Es la base.
- **Bloque listo = todos los checkboxes marcados**. No vale "ya está, sigamos".
- **Si te trabás 2+ días en el mismo bloque** → hablale a Hector. No es prueba de estamina, es mentorship.
- **Anotá lo que aprendiste** en `~/scratch-claude/learnings/`. Un .md por bloque. Va a ser tu portfolio cuando lo necesités después.
- **Si Claude empieza a hacer cosas por vos** en lugar de enseñarte → cortáselo con "tutor, no doer" o cerrá la sesión.

---

## Recursos adicionales (si querés profundizar)

Solo si tenés ganas. NO obligatorio.

- **Terminal**: MDN/freeCodeCamp tienen tutoriales escritos. Pero la mejor forma de aprender terminal es usándola.
- **Git**: [Pro Git book gratis](https://git-scm.com/book/en/v2). Capítulos 1-3.
- **JavaScript**: [JavaScript.info](https://javascript.info/) — el mejor recurso gratis que existe.
- **Web básico**: [MDN: How the Web works](https://developer.mozilla.org/en-US/docs/Learn/Getting_started_with_the_web/How_the_Web_works).
- **Next.js**: Para Bloque 5 — [docs oficiales](https://nextjs.org/docs).

**Importante**: NO empezás leyendo. Empezás escribiendo (con Claude tutor). Los recursos son para cuando un concepto no te queda claro y querés más profundidad.
