# First Prompts — Mauricio's First Day

Prompts sugeridos en orden. Cubren el **Día 1**: install verificado + meet Claude + arrancar Bloque 1 del fundamentals roadmap.

**NO toques el código del marketplace todavía**. El marketplace viene después de los Bloques 1-4 del `fundamentals-roadmap.md`.

---

## Prompt 1 — Sanity check que Claude te conoce

```
Hola! Soy Mauricio. ¿Sabés algo sobre mí y mi proyecto?
```

**Esperado**: Claude lee tu `~/.claude/CLAUDE.md` y responde con datos correctos (12, hermano de Hector, está aprendiendo fundamentals antes del marketplace, etc.).

Si NO los menciona → revisar Paso 7 de `INSTALL.md`. No avancés hasta arreglarlo.

---

## Prompt 2 — Sanity check que las skills cargaron

```
¿Qué skills tienes disponibles? Listame las que sean para Next.js, Supabase, y procesos como brainstorming o testing.
```

**Esperado**: Claude lista varios `nextjs-*`, `supabase-postgres-best-practices`, `superpowers:brainstorming`, `superpowers:test-driven-development`, etc.

Si solo lista 1-2 → revisar Pasos 7 y 8 de `INSTALL.md`.

---

## Prompt 3 — Activar modo tutor

```
Leíste mi CLAUDE.md. Las reglas que más me importan son las de "Cómo trabajar conmigo — REGLAS CRÍTICAS". Confirmá que las entendiste. Después decime cuál es la regla #3 con tus propias palabras.
```

**Esperado**: Claude confirma que va a ser tutor (no doer), responde correctamente sobre la regla #3 ("pedime que te explique antes de aceptar código").

Si Claude obvia las reglas o responde genérico → corrige: "tomá las reglas críticas en serio. Reseteamos."

---

## Prompt 4 — Arrancar Bloque 1 del fundamentals roadmap

```
Quiero arrancar el Bloque 1 del fundamentals roadmap: terminal básica. Soy nuevo. Enseñame los 10 comandos esenciales (cd, ls, mkdir, etc.) uno por uno, con ejemplos que YO escribo en MI terminal mientras vos me explicás. Después de cada comando, hacéme una pregunta para chequear que entendí.
```

**Esperado**: Claude empieza por `pwd` o `cd`, te muestra qué hace, te pide que lo escribas, después pregunta algo tipo "¿qué pasa si escribís `cd` sin argumentos?".

Esta sesión va a tomar 30-60 min. Bueno. Estás aprendiendo.

---

## Si Claude no se comporta como tutor

Patrón que vas a ver: Claude se entusiasma y empieza a "hacer todo por vos". Cortáselo:

```
Pará. Recordá la regla #1 de mi CLAUDE.md — sos tutor, no implementador. No me hagas las cosas, enseñame a hacerlas.
```

Si después de esto sigue overstep → cerrá Claude (`/exit`) y abrí nuevo. Frescas reglas.

---

## Si algo no entendés

Reglas para vos:

1. **No entiendo lo que Claude dijo** → copy-pega esa parte: "explicámelo más simple, soy junior, asumí cero contexto".
2. **No entiendo el código que Claude escribió** → "explica línea por línea, qué hace cada parte y por qué".
3. **Esto se siente complicado** → "esto se siente complicado. ¿Hay forma más simple? Si no, está OK, decime por qué es complicado para entender".
4. **Me trabé 30+ min sin avanzar** → cerrá la terminal, hablale a Hector. No insistas solo.

---

## Anti-patterns — NO hacer

- Aceptar código sin entenderlo. Si no podés explicárselo a Hector → no lo aceptés.
- Dejar que Claude haga 5 cambios de una vez. Pedile UN cambio a la vez.
- Commitear "feat: WIP". Cada commit debe describir QUÉ se logró concretamente.
- Pedirle a Claude "hacé toda la feature". Una task a la vez.
- Saltarse los tests porque "anda más rápido sin".
- **Brincar a buildear el marketplace antes de terminar los Bloques 1-4 del fundamentals roadmap**. Hector y yo acordamos esto. No es opcional.

---

## Goal del Día 1

Que termines el día habiendo:

- [ ] Instalado y autenticado Claude Code
- [ ] Confirmado que las skills esenciales están disponibles
- [ ] Claude entendiendo que es tu tutor (no doer)
- [ ] Bloque 1 (terminal básica) completado parcialmente o entero
- [ ] Primer commit aunque sea de un readme vacío en `~/scratch-claude/`

**No hace falta más**. Si pasaste de Prompt 1 a Prompt 4 con respuestas que entendiste, día épico.

---

## Mañana y siguientes días

Seguí el `fundamentals-roadmap.md` bloque por bloque. Cuando termines Bloque 4 (HTTP/web básico), avisale a Hector. Ahí brainstormeamos juntos el MVP del marketplace y arrancamos a buildear de verdad.
